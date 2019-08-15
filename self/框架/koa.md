- koa   返回一个构造函数，实例化返回一个server对象
  
    - ctx
      
        - 交互
        
            - 设置响应头：
        
                ctx.set('Content-Type', 'application/zip') 自定义响应头一般以X开头
        
            - 添加请求头：
        
                ctx.append('userName','111111');
        
        - 属性
        
          - cookies
        
            ```
            const Koa=require('koa');
            let app = new Koa();
             
            app.use( async ( ctx ) => {
              if ( ctx.url === '/index' ) {
                ctx.cookies.set(
                  'cid', 
                  'ddddd',    //可替换为token
                  {
                    domain: 'localhost',  // 写cookie所在的域名
                    path: '/',       // 写cookie所在的路径
                    maxAge: 10 * 60 * 1000, // cookie有效时长
                    expires: new Date('2017-02-15'),  // cookie失效时间
                    httpOnly: false,  // 是否只用于http请求中获取
                    overwrite: false  // 是否允许重写
                  }
                )
                ctx.body = 'cookie is ok'
              } else {
              	console.log(ctx.cookies.get("cid"));
                ctx.body = '非index' 
              }
             
            })
            app.listen(3000)
            ```
        
            
        
    - 框架常用包
        cnpm i koa koa-static koa-router koa-ejs koa-session koa-better-body mysql co-mysql -D
    
    - 属性
    
        1. context      ctx的原型
    
    - 方法
    
        1. use(router.routes())      添加路由
    
    - 中间件
        - koa-router   返回一个构造  实例返回一个router对象  server.use(router.routes())
          
            ```
            router.post('/upload',ctx=>{
                ctx.response.body = '上传成功'
            })
    server.use(router.routes())
            ```
            
            - 方法
                1. get(path,ctx=>{})  
                2. use(path,router.routes())   添加路由
            1. all(path,ctx=>{})        不区分请求方式进行拦截
            - 属性
            
            - ctx
                - 属性
                    1. params    获得路径上参数，返回一个k-v对象
                    2. body      设置返回内容并会在执行最后自动end()  区别send在于可以多次设置
                    3. request
                    4. response
                    5. method
                    6. url
                    7. path
            8. query   get数据
                    9. ip      客户端ip
                    10. headers 请求头
                    11. state  状态码
                    12. cookies  返回cookies对象
                        1. set(key,value,{})
                    2. get(key,{})
                    13. session  返回session对象，  需要中间件koa-session支持
            
                - 方法  
                    1. throw(status,msg)    抛出异常状态码及信息并退出
                    2. assert(条件boolean,status,msg)             断言测试 
                    3. redirect(path)   重定向，原请求会返回302  
                    4. attachment(path)   返回文件给客户端
            
            
            
        - koa-static-cache 返回一个函数  server.use(static(path),{
            maxage:   文件缓存时间 
            index:    默认访问文件
        });  path  ==  静态文件文件夹
            
            ```
            server.use(static(pathlib.resolve('./www')))
            ```
            
        - koa-better-body    返回一个函数  server.use(body{uploadDir: path})  上传文件存放  文件夹位置
          
            ```
            server.use(body({
                uploadDir: pathlib.resolve('./upload/')
            }))
            ```
            
            - ctx
                - 属性
                    - req
                        1. fields    返回一个对象，结构为
                        {   user: '王志远',
                            f1:
                            [ File {
                                _events: [Object: null prototype] {},
                                    _eventsCount: 0,
                                    _maxListeners: undefined,
                                    size: 1006365,
                                    path: 'static\\upload\\upload_3b285bc66779119a59fe50cacc858ef8',
                                    name: '风吹猫.jpg',
                                    type: 'image/jpeg',
                                hash: null,
                                    lastModifiedDate: 2019-04-14T14:26:08.442Z,
                                    _writeStream: [WriteStream] 
                                    } 
                            ] 
                        }
                - 方法
            
        - koa-session  强制要求加密
        
            ```
            server.keys = ['dasdasda','daasda'];
            server.use(session({},server));
              if (!ctx.session.count){
                ctx.session.count = 0
               }
            ```
        
            
        
        - koa-ejs 返回一个函数，
          
            ```
            ejs(server, {
              root: pathlib.resolve('./template/'),
              layout: false,
              viewExt: '.ejs',
              cache: false,
          debug: false
            })
            await ctx.render('filename', {
                   data:data
               })
          ```
          
        - koa-views
        
            ```
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
        
            
        
        - 传参两个
          
            1. server
            2. {}
                1. root
                2. layout
                3. viewExt
            4. cache
            5. debug
            
            
    
- 渲染
    - 服务端渲染
        - pug  返回pug对象
            - 属性

            - 方法
                1. renderFile(path,{

                },(error,data)=>{})  path == 渲染的文件的路径
            - 传递变量
              
                1. 在rend方法里的对象中进行配置，在渲染的文件里用=使用
        - ejs
    
            - 类似jsp  <%=变量%> <%js语句%> <% include path %>
        
    - 客户端渲染    


    - 一些数据结构
        - req
            1. files
                [ { fieldname: 'f1',
                    originalname: '黑人微笑.jpg',
                    encoding: '7bit',
                    mimetype: 'image/jpeg',
                    destination: './static/upload',
                    filename: 'd342dbd8ed9ca8f4c9240aa549d72c22',
                    path: 'static\\upload\\d342dbd8ed9ca8f4c9240aa549d72c22',
                    size: 7972 } ]


