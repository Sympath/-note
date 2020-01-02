### 基础知识点
##### 属性
    - transform
        1. tranform-origin()：旋转基点，当该属性对象进行旋转时围绕此旋转
        2. rotate()： 英文释义：旋转 即是该对象按基点旋转角度
        3. scale()：压缩
        4. screw(): 扭曲


    - border
        1. radius
    
    - 伪元素before/after
        - 特点
            1. 内联元素
            2. 虚拟    
            3. 必须存着content属性
    - calc 实现属性值计算
    
    - box-sizing: border-box;   使得盒模型
    
    - 文字
        1. 文字不换行   white-space:nowrap;
        2. word-break : normal | break-all | keep-all    单词断句规范   break-all===允许单词断开分行显示   keep-all===整个单词不断开，分行显示
    
        - 操作
            1. 文字省略号
                text-overflow: ellipsis   显示省略符号来代表被修剪的文本
                overflow hidden
                white-space: nowrap     超出不换行
    
    - 语义化
        1. 文档结构更清晰
        2. SEO更加具有解析权重
##### 选择器
    1.   排除存在目标类样式的容器  :not()
    2.    已被访问的容器   :visited           
### 实际操作
    - 边线处理
        - 采用伪元素进行实现
        - 关键：
            - 定位脱标；
            - 伪元素不影响父盒子模型；


### 经典布局
    - 弹性布局（display：flex）
        - align-items: center 内部子元素侧轴对齐居中 
        - justify-content 横轴居中
        - flex 
            - 不受块级约束，自成一体，是父子元素一起的布局，若flex:1设置在某一个子元素上，则该元素成为主元素，在其余子元素填充自身的盒子模型完成后的所有余下的父级内容都交给主元素；
            - flex具有继承性，即如果想要子元素平分空间，可以给父元素添加flex:1;
        - 注意：
            1. 子元素的float、clear和vertical-align属性将失效
        - 弹性盒对象属性
            1. flex-direction 属性规定灵活项目的方向 




### 居中

||垂直|水平|整体居中|
|---|---|---|---|
|块级||margin:0 auto;|top: 50%;left: 50%;<br/>transform: translate(-50%,-50%);<br/>|
|行内块/行内|vertical-align: middle;（兄弟节点之间）|text-align: center;|
|弹性布局|align-items: center|justify-content|

### 新属性（移动端开发必加）
- -webkit-overflow-scrolling: touch;   #提升用户滑动体验
- text-rendering: optimizeLegibility;  抗锯齿  高清手机上文字边缘不出现锯齿
- text-size-adjust: 100%               禁止浏览器调整字体大小
- filter
    1. contrast() 对比度  传纯数字
    2. blur() 模糊度   传px
    3. grayscale()  灰色度缩放

- mix-blend-mode: screen


### 深度考点
    - 1px 边框问题
        - css 像素 1px 在手机里 硬件物理像素 retina 2px 3倍retina 3px
        - 解决方法 transform：scaleY(0.5);配合transform-origin:基点 压缩使得满足用户体验（苹果）            
        - 注意点：浏览器不会处理小数点像素，若小数浏览器会自然转为整数进行处理
        - 升级问题   如果是一个包裹，即四边均有1px问题
            1. 设置本身内容宽高为200%
            2. 怪异盒模型
            3. 整体scale(.5)
            
    - BFC
        1. 样式特点
            1. 官网：所有毗邻的两个或更多盒元素的margin将会合并为一个margin共享之。毗邻的定义为：同级或者嵌套的盒元素，并且它们之间没有非空内容、Padding或Border分隔。
            2. BFC容器不会与浮动容器重叠


        2. 触发条件

## 其他知识点
@media  媒体查询
- 横屏竖屏
    - 
      


### 布局常用词汇
- 上中下
    1. hd bd ft

- 左右
    1. main  aside

- 评论
    1. feed item 

- PC端  ==== 优先float
- 移动端  ===== 优先flex布局
