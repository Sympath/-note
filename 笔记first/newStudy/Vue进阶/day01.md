### 父子通讯

1. 同步数据

   1. .sync

      ![1565612100646](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565612100646.png)

   2. v-model

      ![1565612306207](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565612306207.png)

   3. ref







### 多层级

 - 层层传递（很麻烦）

 - $parent

    - 触发事件必须用$emit

    - $dispatch（eventName,args)   向上传递

      ![1565613232422](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565613232422.png)

   - $boradcast    向下传递

     ![1565613345518](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565613345518.png)

- $attrs

  - inhertAttrs    默认为true     即会挂载到dom上
  - v-bind="$attrs"







#### this属性

- $listeners   所有父组件传递的方法    v-on="$listeners"    一次绑定所有方法    

- $attrs      属性的集合                    v-bind="$attrs"       一次性绑定所有属性

  ​	 简单来说就是利用如果传递的是对象，会解构然后将所有的都传递

- $refs     

### 配置属性

- provide(){}      inject:[]



##### EventBus

- Vue原型上绑定一个vue实例   然后通过$on 以及 $emit实现通讯；得注意顺序问题   可以用this.$nextTick

#### 插槽传参

scopeslot

![1565617059595](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565617059595.png)

- 普通插槽在父组件中执行    作用域插槽在子组件中执行

- 函数的methods已经bind过了
- 表单DOM元素原生存在focus()方法，调用则获取焦点