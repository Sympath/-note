- 配置doucker

  - 下載安裝doucker http://c.biancheng.net/view/3121.html

  - 報錯參考 https://www.jianshu.com/p/09d53c822cf8

- 配置下拉gitlab項目

  ```
  注意：gitlab上也需要配置本机的git公玥才能clone项目
  ```

- 下拉local-dev-env 即本地doucker鏡像，配置yml文件，配置好後執行如下操作

  1. 登陸docuker

     ```
     賬號密碼及操作：http://lqbyun.com/devops/local-dev-env/snippets/2
     ```

  2. 根據配置景象下拉資源啓動docuker服務

     ```
     docker-compose up -d
     ```

- npm i  && npm run watch



### 注意

1.docker-compose exec container_name bash

2.docker-compose run container_name bash

```
exec回直接进入容器，而run则是在当前容器基础上新建一个一摸一样的容器，相当于clone一个吧。所以exec以后，作修改就是对原来容器的修改，而run的修改则与原来的无关。
注意！！！
这两个命令需要在右compose-up.yml配置文件的目录下执行，否则报错
```



3. 在下班時需要把docuker關掉，這樣就可以避免第二天要restart了

