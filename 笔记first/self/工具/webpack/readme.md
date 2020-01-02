- webpack-dev-server 中   不配置、 --inline 以及 --inline --hot   的区别
   -  // 当资源发生改变，以下三种方式都会生成新的bundle，但是又有区别：

      1. 不会刷新浏览器
         $ webpack-dev-server
      2. 刷新浏览器
         $ webpack-dev-server --inline
      3. 重新加载改变的部分，HRM败则刷新页面
         $ webpack-dev-server  --inline --hot

```
关于热更新
--watch（原生webpack配置）
	虽然 webpack 提供了 webpack --watch 的命令来动态监听文件的改变并实时打包，输出新 bundle.js 文件，这样文件多了之后打包速度会很慢，此外这样的打包的方式不能做到 hot replace ，即每次 webpack 编译之后，你还需要手动刷新浏览器。
webpack-dev-server
webpack-dev-server 主要是启动了一个使用 express 的 Http服务器 。它的作用 主要是用来伺服资源文件 。此外这个 Http服务器 和 client 使用了 websocket 通讯协议，原始文件作出改动后， webpack-dev-server 会实时的编译，但是最后的编译的文件并没有输出到目标文件夹，注意：你启动webpack-dev-server后，你在目标文件夹中是看不到编译后的文件的,实时编译后的文件都保存到了内存当中。
```

