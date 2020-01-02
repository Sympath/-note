- css

  - 采用stylus，

    - 先安装

    ```
    npm i stylus stylus-loader -D
    ```

    - 再打开隐藏配置

      ```
      yarn eject
      ```

    - 最后配置webpack.config.js(注意位置放在sass-loader下面)

      ```
      {
                    test: /\.styl$/,
                    use: ["style-loader", "css-loader", "stylus-loader"]
                  },
      ```

      

  - 数据请求jsonp

    - 中文乱码

      ```
      encodeURIComponent
      ```

      