### 项目目录

```
│  index.html
│  index.tsx
│  
└─css
        site.css
```

### 依赖安装

```
# ts依赖
yarn add typescript awesome-typescript-loader -D
# react依赖
yarn add react-router-dom react react-router react-dom
yarn add @types/react @types/react-router @types/react-router-dom @types/react-dom -D
# webpack依赖
yarn add webpack webpack-cli webpack-dev-server babel-core babel-cli babel-loader babel-preset-env css-loader style-loader url-loader file-loader -D
# webpack plugin依赖
yarn add html-webpack-plugin mini-css-extract-plugin -D
# 项目本身依赖
yarn add bootstrap
```

### 配置文件

1. webpack.config.js

   ```
   var path = require('path');
   
   var HtmlWebpackPlugin = require('html-webpack-plugin');
   
   let MiniCssExtractPlugin = require('mini-css-extract-plugin');
   
   var webpack = require('webpack');
   
   
   
   var basePath = __dirname;
   
   
   
   module.exports = {
   
       context: path.join(basePath, 'src'),
   
       resolve: {
   
           extensions: ['.js', '.ts', '.tsx']
   
       },
   
       entry: {
   
           app: './index.tsx',
   
           appStyles: './css/site.css',
   
           vendor: [
   
               'react',
   
               'react-dom',
   
               'react-router-dom',
   
           ],
   
           vendorStyles: [
   
               '../node_modules/bootstrap/dist/css/bootstrap.css',
   
           ],
   
       },
   
       output: {
   
           path: path.join(basePath, 'dist'),
   
           filename: '[name].js',
   
       },
   
       module: {
   
           rules: [
   
               {
   
                   test: /\.tsx?$/,
   
                   exclude: /node_modules/,
   
                   loader: 'awesome-typescript-loader',
   
                   options: {
   
                       useBabel: true,
   
                   },
   
               },
   
               {
   
                   test: /\.css$/,
   
                   use: [
   
                       MiniCssExtractPlugin.loader, "css-loader"
                   ],
               },
               // Loading glyphicons => https://github.com/gowravshekar/bootstrap-webpack
               // Using here url-loader and file-loader
               {
                   test: /\.(png|jpg|gif|svg)$/,
                   loader: 'file-loader',
                   options: {
                       name: 'assets/img/[name].[ext]?[hash]'
                   }
               },
           ],
       },
       // For development https://webpack.js.org/configuration/devtool/#for-development
       devtool: 'inline-source-map',
       devServer: {
           port: 8080,
           noInfo: true,
       },
       plugins: [
           //Generate index.html in /dist => https://github.com/ampedandwired/html-webpack-plugin
           new HtmlWebpackPlugin({
               filename: 'index.html', //Name of file in ./dist/
               template: 'index.html', //Name of template in ./src
               hash: true,
           }),
           new MiniCssExtractPlugin({
               filename: "[name].css",
               chunkFilename: "[id].css"
           }),
       ],
   };
   
   ```

2. tsconfig.json

   ```
   {
   
       "compilerOptions": {
   
           "target": "es6",
   
           "module": "es6",
   
           "moduleResolution": "node",
   
           "declaration": false,
   
           "noImplicitAny": false,
   
           "sourceMap": true,
   
           "jsx": "react",
   
           "noLib": false,
   
           "suppressImplicitAnyIndexErrors": true
   
       },
   
       "compileOnSave": false,
   
       "exclude": [
   
           "node_modules"
   
       ]
   
   }
   ```

3. .babelrc

   ```
   {
       "presets": [
           [
               "env",
               {
                   "modules": false
               }
           ]
       ]
   }
   ```

   