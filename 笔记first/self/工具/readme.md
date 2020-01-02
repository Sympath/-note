### nvm是一款node版本管理工具，安装步骤如下

1. 下载对应安装包，但下载好了先别启动安装程序

2. 先清空node环境，即删掉当初下载的node（官网推荐），一般默认会在C:\Program Files\node

3. 在某一盘符路径下（注意不要有中文和空格）新建两个文件夹（nvm和nodejs）用以保存nvm和正在使用的node环境（其实这是一个快捷方式，指向nvm内的node，个人理解原理是nvm的一个指针指向nvm管理的node），本人配置

![1561515405890](C:\Users\wzy\AppData\Roaming\Typora\typora-user-images\1561515405890.png)

4. 双击启动安装包，点击下一步，注意有两处更改路径

   ![1561531841589](C:\Users\wzy\AppData\Roaming\Typora\typora-user-images\1561531841589.png)

![1561531907716](C:\Users\wzy\AppData\Roaming\Typora\typora-user-images\1561531907716.png)

5. 修改setting.txt文件

   安装好后目录结构如下

   ![1561537067229](C:\Users\wzy\AppData\Roaming\Typora\typora-user-images\1561537067229.png)

   修改setting文件，在文件末尾添加(即添加镜像，加速使用中的下载)

```
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/6。 
```

6. 大功告成，附上nvm常用命令（在cmd中用nvm -v验证下有没有成功安装）

   - 下载node某些版本  nvm install v8.14.0

     ```
      使用nvm install <version> [<arch>]命令下载需要的版本。arch参数表示系统位数，默认是64位，如果是32位操作系统，需要执行命令：nvm install 6.9.0 32
     ```

   - 更换node版本    nvm use v8.14.0

   - 查看所有管理的node  nvm list

### 注意

1. nvm的环境变量是会在下载时默认配置好的，可以再安装后自行验证下有没有问题

   ![1561537507188](C:\Users\wzy\AppData\Roaming\Typora\typora-user-images\1561537507188.png)

2. 重装node后，可能出现npm全局安装位置更改问题，这时最好把npm包的位置也自己配置一下，毕竟一切尽在掌握为佳，这也补充了一个知识点，我们平时全局安装的依赖，其实是存放在某个位置的，而我们平时直接使用必然是有默认配置环境变量的，计算机没有魔法，只有巧妙，npm全局默认安装在C:\Users\Administrator\AppData\Roaming\npm，此时我们需要两个操作

   1. 在node方面，更改npm全局依赖指向，建议在nodejs文件夹下新建node_global文件夹，然后path即node_global的路径

      ```
      修改npm全局安装路径 npm config set prefix "path"  
      ```

   2. 计算机方面，配置环境变量，在用户变量的path中找到C:\Users\Administrator\AppData\Roaming\npm，更改为path，本人配置如下

      ![1561538228393](C:\Users\wzy\AppData\Roaming\Typora\typora-user-images\1561538228393.png)

3. 如果一切顺利，恭喜。。你得所有的全局包重装了，不过一时麻烦总比一直糊涂要好，完美收官，诸君顺利