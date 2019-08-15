### koa使用

- 后端声明

  ```
  const ejs = require('koa-ejs');
  ejs(server, {
      root: pathLib.resolve('view'),
      layout: false,
      viewExt: '.ejs',
      cache: false,
      debug: false
  })
  或者
  const view = require('koa-views');
  server.use(view(
      pathLib.join(__dirname, './view'), {
          extension: 'ejs'
      }
  ))
  结合session使用
router.get('/user',async ctx=>{    
     if (!ctx.session.count){
      ctx.session.count = 0
     }
     ctx.session.count++;
     await ctx.render('user', {
         count: ctx.session.count
     })
  })
  ```
  
  - 前端使用
    - 小标签
      - html  include <%- include(path)%>
      - 变量      <%= %>
      - js          <%%>