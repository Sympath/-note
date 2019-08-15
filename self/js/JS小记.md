### 基础知识点
- 选中html对象 domcument.documentElement
- 选中body或同级元素，直接用documentElement.body(或其他标签名就好)




- 事件参数对象 event
    - 方法
        - stopPropagation()：阻止事件冒泡
        - stopImmediatePropagation()：取消事件添加效果，使第一个事件之外添加的所有事件失效  
        - preventDefault()：阻止事件默认行为
    - 属性
        - target：  点击的对象
        - currentTarget: 事件绑定的对象
```
e.currentTarget=====事件绑定的对象,e.target=====点击的对象（简单来说，就是如果事件绑定的对象内部还有子元素，点击该子元素也会触发事件，此时target指的就是子元素，而currentTarget则是事件绑定对象本身（ps：个人理解））
```

- 做题小记
1. 进行算术运算时会做，+号，数字隐式转换成字符串。其余的运算符号是字符串隐式转换成数字。
2. 一元加操作符，一元加操作符相当于Number()函数

### 共有
- Element
    - 方法
        - getBoundingClientRect()   用于获取某个元素相对于视窗的位置集合。集合中有top, right, bottom, left等属性
    - 属性
        - dataset   用于获取元素上data-xxx属性值   eg： data-original   通过 dataset.original 获取
- e 
    - 方法
    - 属性
- window
    - 方法
        - requestAnimationFrame(fn)     一秒60幁进行屏幕刷新
    - 属性

##### 一些事件
- 入口事件
    1. document.DOMContentLoad    在dom树加载完毕后执行
    2. window.onload   在页面资源全部加载完毕后执行
- 浏览器
    1. onscroll事件    在scroll滚动触发事件    document.addEventListener('scroll',lazyload);

### ES6
- 变量
    - 声明关键字
        - var的缺点
            1. 重复声明不报错
            2. 无法限制修改
            3. 没有块级作用域
        - 对应ES6的声明方式let const
            1. 支持块级作用域
            2. 重复声明会报错
            3. 省略闭包
    - 声明方式
        - 解构赋值
            - 实现前提
                1. 左右结构必须一致
                2. 右侧格式必须符合规范
                3. 必须声明同时进行初始化

- 函数
    - 箭头函数 () => {}
        1. 在只有一个参数时可以省略()：e=> {}
        2. 在函数体只有一个return时可以省略{}：()=>return;
        3. 箭头函数中的this在创建时就会固定，而不会再出现一定指向调用对象的现象
    - 函数参数
        1. 参数扩展：
            1. 参数收集：...args
            2. 数组展开：...arr
        2. 默认参数
            1. es6支持在函数定义时可以以给形参初始化的方式进行参数默认，若函数调用时未传入该参数，则依照默认值进行函数调用
- 数组
    - map  映射 一对一
        - 传入一个函数，返回数组内每个元素操作后组成的新数组
    - reduce 汇总 多对一 
        - 四个形参 
            - temp 中间值(累计器)--即上一次计算的结果值，第一次的值因为没有计算，所有值等于数组的第一个元素
            - item 项值 从数组第二项开始
            - index 项索引 从1开始
            - arr  源数组
        - 返回一个总值 
    - filter 过滤器
        - 通过return 布尔值进行决定数组是否保留
        - 返回一个数组
    - find  返回通过测试（函数内判断）的数组的第一个元素的值
         function(currentValue, index, arr) 回调函数可以接受三个参数，依次为当前的值、当前的位置和原数组
    - splice(index,num)   index  要刪除的元素的索引   num 删除多少位
- 字符串
    - 方法
        - startsWith(str)：首子字符串匹配 返回boolean
        - endsWith(str)：尾子字符串匹配
        - 字符串截取的api区分

||slice()|substr()|substring()|
|---|---|---|---|
|参数||第二位参数代表截取字符位数||
|特性||非标准化ECMA的API|第二位参数为负数则只截取一位|
|数组|存在(buffer也存在)|不存在|不存在|

​                     


    - 字符串模板
        - 引入``定义str的方式，仿用数据库，存在${}占位符的写法
        ```
        eg:
        let addStr = `c`;
        let str = `ab${addStr}d`;
        console.log(str);//abcd
        ```

- ES6的面向对象        
    - 新增class关键字
        - 内部定义
            - constructor方法（构造器）
            - 普通方法
        - 意义
            - 将构造器和类分开了
            - 方法可内部定义，避免了原型情况的向外暴露
    - 新增extends关键字
        - super方法指向父类

#### 一些特殊数据

- Number

  ```
  Infinity   数值无穷大
  NaN        非数字
  ```

  

##### 一些对象

- json
    - JSON对象
    - json简写
        1. key-value相同时可以只写一个；
        2. 内部存在方法可以省略: function部分；
    - 方法
        - JSON.stringify(json); json对象串行化，即转化成字符串
        - JSON.parse(); json类型字符串转换成json对象
        - encodeURIComponent(json类型的字符串)
    - json标准写法：
        1. key必须用""包裹
        2. 只能使用双引号

##### 一些API
- 对象
    - 距离
        1. offset系列     距父级的距离
- window



### 获取元素样式



```javascript
function getStyle(element, attr) {
      if(attr){
​                if (ele.currentStyle) {
​                    return ele.currentStyle[attr];
​                } else {
​                    return getComputedStyle(ele, false)[attr];
​                }
​            }else {
​                if (ele.currentStyle) {
​                    return ele.currentStyle;
​                } else {
​                    return getComputedStyle(ele, false);
​                }
​            }}
```



- 大牛和牛书
1. 司徒正美    js框架设计
2. 张鑫旭   css世界
3. 