### auto

对于默认值auto，height在标准中有明确规范：

```
如果包含块的高度没有显式指定（即高度由内容决定），并且该元素不是绝对定位，则计算值为 auto。
### 所以如果内部子节点设置高度为百分比，则得出auto*n% = NAN  于是无效
```

​	这也就解释了为什么我们设置html和body的时候经常设置如下代码

```
html,body {
	height:100%;
}
```

​	因为可以这么理解：html原始结构是：浏览器可视区包裹html包裹body；可视区是有高度的，但html和body均为默认auto，于是按标准所说，高度由内容决定；此时我们写代码如果最外层直接用百分值或者只设置body不设置html，则导致父级无显式高度，百分值计算值为NAN，无效；

而对于宽度，

```
如果包含块的宽度取决于该元素的宽度,那么产生的布局在 CSS 2.1 中是未定义的；
### 即是属于未定义行为，由浏览器自行定义，好在对于这个行为各大浏览器比较统一：就按照包含块真实的计算值作为百分比计算的基数；
```

而由此衍生出一个知识面 ，width在不同盒子下auto展示的不同特形

- 充分利用可用空间。<div>、<p>这些元素的宽度默认是 100%于父级容器的。这种充分利用可用空间的行为还有个专有名字，叫作 fill-available。

- 收缩与包裹。典型代表就是浮动、绝对定位、inline-block元素或table元素。

- 收缩到最小。该情况很容易出现在table-layout为auto的表格中，如下图所示。最左边单元格收缩导致一柱擎天效果


  ![img](https://upload-images.jianshu.io/upload_images/2917105-ace53d0bda42ec08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/282/format/webp)

- 超出容器限制。除非有明确的width相关设置，否则不会超过父级容器宽度。单页存在一些特殊情况，如内容很长的连续的英文和数字、内联元素被设置了white-space:nowrap。

在第一种充分利用空间的情况下，即是我们常用的块级元素auto情况，于是最外层容器有了可视区的宽度，那么假设它内部有个子div，宽度设为100%，margin-left100px，会是怎样呢？

```
 <div class="container">
        <div class="content"></div>
    </div>
    <style>
        .container {
            background-color: #000;
        }
        .content {
            width: 100%;
            margin: auto 100px;
            background-color: #ccc;
            height: 10px;
        }
            </style>
    </style>
```

![1565923277187](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565923277187.png)

喜提惊喜：

	1. 出现横向滚动条 （即content容器溢出）
 	2. margin-right失效

#### 第一点解释：

​	由于dom树由上至下执行渲染，所以解释了为什么父容器不会被撑开的问题（注意与height的auto区分开），再者看看标准对width设置为百分比的定义

```
定义基于包含块（父元素）宽度的百分比宽度。
```

于是我们得出此时content容器的width的值为container宽度（可视区宽度），但重点来了，注意盒子模型，在标准盒子模型下，width仅仅代表content的宽度，于是当我们设置margin/border/padding时就会出现溢出情况；

![img](https://images2017.cnblogs.com/blog/1265396/201711/1265396-20171119143703656-1332857321.png)

我们可以更改content样式代码为

```
.content {
    width: 100%;
    padding: 0 100px;
    background-color: #ccc;
    height: 10px;
    background-clip: content-box; ### 注意设置背景颜色的展示区间为content-box，不然padding区域也会有背景颜色，此属性自查详情
    }
```

![1565924784103](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565924784103.png)

上面是原理介绍，总结而言就是

#### width: auto或不设置宽度

> - 子元素（包括content+padding+border+margin）撑满整个父元素的content区域。
> - 子元素有margin、border、padding时，会减去子元素content区域相对应的width值
> - 父元素的content = 子元素（content + padding + border + margin )

#### width: 100%

> - 强制将子元素的content区域 撑满 父元素的content区域
> - 子元素有margin、border、padding时，不改变子元素content区域的width，而是溢出父盒子，保持原有值
> - 父元素的content = 子元素的content

#### 简单来说，就是子元素width：auto；时父元素的content=子元素的content+margin，border之类的，即设置margin之类属性有效，而设置width：100%；则会强制性的撑满父元素的空间。

#### 第二点解释：

![img](https://img-blog.csdn.net/20180312235037474)

![img](https://img-blog.csdn.net/20180312235112809)

[http://blog.cssforest.org/2017/06/21/margin-right%E5%8F%B3%E8%BE%B9%E8%B7%9D%E5%A4%B1%E6%95%88.html](http://blog.cssforest.org/2017/06/21/margin-right右边距失效.html)   margin-right的原文链接