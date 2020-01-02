- express   require得到的是一个函数，调用返回一个server对象
    -  属性
        1. 
    -  方法
        1. get(url,(req,res,next)=>{})
            - req
                - 属性
                    1. query        get下返回一个json对象，包含请求数据
                - 方法
        2. post(url,(req,res,next)=>{})
            - req
                - 属性
                    1. body         返回post数据对象 在server.use(body.urlencoded({extended:false})); 执行后才存在
                - 方法

        3. use(arg)  arg分类如下
            1. url,(req,res,next)=>{}   任意类型请求
            2. express.static(文件夹path)   返回文件夹下对应请求的文件   

   - 中间件
        1. body-parser   普通post
            - 初始化方法
                urlencoded({extended:false})
            - req
                - 属性
                    1. body 接收到的数据键值对
                
            - res
                - 属性
                - 方法
                    1. 

        2. multer        文件上传
            - 初始化方法
                any({})
                    dest:'上传文件放置位置      
            - req
                - 属性
                    1. files  返回接收到的文件数组
                
            - res
                - 属性
                - 方法
                    1. 

        3. cookieParser   
            - 初始化方法
                本身即是一个函数，初始化时调用本身即可，初始化时可以传递一个字符串参数作为签名密钥
            - req
                - 属性
                    1. cookie  读取未签名cookie数据信息，返回一个k-v对象
                    2. signedCookies  读取签名cookie
                
            - res
                - 属性
                - 方法
                    1. cookie(key,value,{});   设置返回cookie 第三个参数可以添加一些其他数据
                        httpOnly  :  boolean   为true时对前台不可见  
                        maxAge    :   time      失效时间
                        secure    :   boolean   只接受https
                        signed    :   boolean   为true表示签名  
        4. cookie-session
            - 初始化方法  cookiesession({keys:[]})
                本身即是一个函数，初始化时调用本身即可，初始化时传递一个对象，存在属性keys存放秘钥数组生成签名
            - req
                - 属性
                    session    返回一个对象，可以往里面存储内容
                
            - res
                - 属性
                - 方法
