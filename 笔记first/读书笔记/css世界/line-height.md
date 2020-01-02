### line-herght作用范围

1. 内联元素
   1. 值即为元素高度，存在line-height = 行距 + content area，而content area近似字体大小（在字体为宋体的情况下完全相同，简单来说即content area受fontsize以及fontfamily的影响）
2. 替换元素
   1. 对替换元素不会有任何作用，但注意替换元素会存在行框盒子，于是会有幽灵空白节点存在，所以lh作用的是这个节点产生作用
3. 块级元素
   1. 不会有任何作用，块级元素的高度跟着变化实际上是通过改变块级元素里面内联级别元素占据的高度实现的

### 应用

1. 小图标居中

   ![1567668179047](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567668179047.png)

   ```
   .icon-arrow {
       display: inline-block;
       width: 20px;
       height: 1ex;//关键
       background: url(/images/5/arrow.png) no-repeat center;
   }
   ```

2. 多行文本垂直居中

   ![1567668278459](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567668278459.png)

   ```
   <div class="box">
       <div class="content">基于行高实现的...</div>
   </div>
   .box {
       width: 280px;
       line-height: 120px;
       background-color: #f0f3f9;
       margin: auto;
   }
   .content {
       display: inline-block;
       line-height: 20px;
       margin: 0 20px;
       text-align: left;
       vertical-align: middle;
   }
   ```

   