- yarn

  npm install -g yarn

  - yarn默认安装源地址使用以下命令查看（https://registry.yarnpkg.com）

    yarn config get registry

  - 切换yarn安装源为淘宝

    yarn config set registry 'https://registry.npm.taobao.org'

- npm 

  - 命令

    ```
查看所有全局安装的模块 npm ls -g
    
    ```

查看npm默认设置（部分） npm config ls
    
  查看npm默认设置（全部） npm config ls -l
    
    修改npm全局安装路径 npm config set prefix "path"
    修改npm缓存  npm config set cache "path"
    ```


​    
​    
  - 报错  
  
    ![å¨è¿éæå¥å¾çæè¿°](https://img-blog.csdn.net/2018101000153851?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQ3MDc5MQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
  
    给npm降级或者升级
  
    - 降级 ： npm install -g npm@5.4.0
    - 升级 ： npm install -g npm ` 升级到最新版`
  
  - 一些知识
  
    ```
    1. C:\Users\Administrator\AppData\Roaming\npm，一般安装时，没修改 node 安装路径，默认的 npm 全局安装路径就在这里(可以在环境变量中的用户路径更改配置)
    ```
  
    

