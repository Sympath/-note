### 版本

- 安装最新版本

  ```
  npm install -g @vue/cli 或 yarn global add @vue/cli
  ```

  

### 基础语法

##### 事件修饰符

- stop        禁止冒泡
- once        单次事件
- prevent     阻止默认事件
- native      原生事件（组件）
- keycode|name   筛选按键

### 组件

##### 父传子

- 父组件内定义

  ```
  <template>
    <div class="container">
        <child :message="message"></child>
    </div>
  </template>
  
  <script type="text/ecmascript-6">
  import child from "./child";
  export default {
    name: "demo1",
    data() {
      return {
          message: '最好的时光'
      };
    },
    components: {
        child
    }
  };
  </script>
  
  ```

- 子组件接收props

  ```
  props: ['message']
  ```

##### 子传父

- 子组件发送事件且传参

```
 <button @click="$emit('sendMsg',{
        msg:message
      })">ok</button>
```

- 父组件接收事件及参数

```
<child @sendMsg='getMsg'></child>
js中
   getMsg(e){
      console.log(e.msg);
    }
```



### 生命周期

### vue中类dom操作

- $ref

  ```
  设置：	
  <input type="text" ref="info">
  获取：
  this.$refs.info.value
  ```

- $event 事件对象 

  ```
  传递：
  <button @click="Event($event)">事件对象</button>
  获取：
  Event(e){console.log(e)}
  注意：
  1.不使用圆括号，event被自动当作实参传入
  2.使用圆括号，必须显式的传入event对象，如果不传入可能最终找到的是全局的window .event
  ```

- $nextTick(()=>{})  保证操作在dom渲染完成后进行

### 插件

#### axios

- 拦截器

![1560589027961](C:\Users\wzy\AppData\Roaming\Typora\typora-user-images\1560589027961.png)