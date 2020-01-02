#### node意义
1. 中间层
2. 提高安全性，避免核心服务器暴露
3. 优化性能



#### 协议
HTTP1.0
HTTP1.1    支持持久连接
HTTPS      安全协议 签名和非对称加密
HTTP2.0    加密、头部压缩、多路复用 

###### 报文
头Head   ======  32KB
体Body   ======  2G   


##### 包管理器
- npm
- cnpm      阿里镜像
- yarn     facebook出品
- bower    前端包管理

##### 一些命令
- 安装cnpm  npm install -g cnpm --registry=https://registry.npm.taobao.org

##### 一些文件
- package.json   工程文件   通过npm init -y 自动生成
    1. script   相当于命令别名
    2. devDependencies   开发依赖管理   其中^代表该版本往上兼容的最高版本
- package-lock.json   npm安装报错时出现的文件，相当于日志    

##### 一些工具
- forever   启动器
    - 一些命令
        1. forever start xxx.js
        2. forever restart xxx.js
        3. forever stop xxx.js
        4. forever stopall
        5. forever list
    - 一些参数
        1. -l 'path'  日志输出路径
        2. -e 'path'    错误输出路径
        3. -a       



##### 一些对象
- Buffer
    - 方法
        1. indexof(new buffer(str))      指定子串下标
        2. slice(a,b)  
        3. (static)Buffer.concat(list[Buffer])   合并缓冲区返回一个新的buffer    
    - 属性
- Error
    - 属性
        1. message  表示异常详细信息字符串
        2. name 表示异常的类型
    - 特性
        js预定义了六种常见的Error子类
        1. EvalError   //当不正确使用eval函数时，会抛出EvalError类的一个实例

        2. RangeError   //当数值超出JavaScript中合法的数值范围时，会抛出RangeError类的一个实例

        3. ReferenceError  //当读取一个不存在的变量的值时，会抛出ReferenceError类的一个实例

        4. SyntaxError   //当JavaScript中出现语法错误时，会抛出SyntaxError类的一个实例

        5. TypeError   //当JavaScript中类型不符合要求时，会抛出TypeError类的一个实例

        6. URIError    //当字符串不符合编码或解码要求时，会抛出URIError类的一个实例    



#### 原生系统库
1. http
    - 方法
        1. creatServer((req, res)=>{})    创建服务器对象server， server.listen(端口) 实现监听，服务器长久运行
            1. req
                - 属性
                    1. url 请求相对路径
                    2. headers 请求头信息  json对象
                        1. host  域名+端口
                        2. origin  域名
                        3. connection 连接类型

                - 方法
                    1. on('事件名',()=>{})     post提交时
                        1. data    callback参数buffer（是Buffer类型数据）       数据传输时出发点事件
                        2. end     数据传输完成时触发的时间

            2. res
                - 属性

                - 方法
                    1. writeHeader(status,{key,value})  可以输出状态码 向请求的客户端发送响应头 
                        - key                 value
                            1. "Content-Type"  : "text/html;charset=utf-8"  编码格式
                            2. "Content-encoding"  指定返回内容格式
                                1. "gzip"      文件格式==压缩文件声明，避免浏览器下载
                                2. "deflate"   buffer流
                                3. ""          字符串
                    2. write()     返回字符串   原生http   koa中是用send()  代替write和end
                    3. end()       结束响应    

2. fs    文件处理
    - 方法
        1. readFile(path,(err,buffer)=>{})   读
        2. createReadStream(path)      创建读取流  返回一个流对象
            - 方法
                1. pipe()
                2. statSync(path)   获取对应路径下的文件（文件夹）状态 返回一个对象
                    Stats {
                        dev: 1342755101,
                        mode: 33206,
                        nlink: 1,
                        uid: 0,
                        gid: 0,
                        rdev: 0,
                        blksize: undefined,
                        ino: 844424930231171,
                        size: 0,
                        blocks: undefined,
                        atimeMs: 1555483304277.7886,
                        mtimeMs: 1555483405669.6567,
                        ctimeMs: 1555483405669.6567,
                        birthtimeMs: 1555483304277.7886,
                        atime: 2019-04-17T06:41:44.278Z,
                        mtime: 2019-04-17T06:43:25.670Z,
                        ctime: 2019-04-17T06:43:25.670Z,
                        birthtime: 2019-04-17T06:41:44.278Z 
                        }
                        - 方法
                            1. isFile()
                            2. isDirectory() 
            - 事件
                1. on('error',err=>{})  必须保留，避免读写文件报错抛出异常导致服务器崩溃 
        3. createWriteStream(path)      创建写入流 返回一个流对象
            - 事件
                1. on('fini',()=>{})  
3. zlib   文件压缩
    - 方法
        1. createGzip()   创建一个压缩流对象，作为熟读写入流的中间层


4. querystring   请求参数解析
    - 方法
        1. parse(str)   str是k=v&k1=v1...格式字符串    返回k-v对象 存储参数
        2. stringify(json)  返回k=v&k1=v1...格式字符串    

5. url          处理解析请求数据
    - 方法
        1. parse((req.url, true)=>{})   callback中第二个参数true是指连query一起解析   返回一个Url对象  一般我们只用pathname,query

            - Url {
                    protocol: null,
                    slashes: null,
                    auth: null,
                    host: null,
                    port: null,
                    hostname: null,
                    hash: null,
                    search: null,
                    query: [Object: null prototype] {},
                    pathname: '/',
                    path: '/',
                    href: '/' 
                }


​       
6. path     路径处理
    - 方法
        - dirname(str)  返回路径
        - extname(str)  返回文件扩展名
        - basename(str)  返回文件名
        - resolve(path,...relPath)   路径解析   eg:   path.resolve(__dirname,'xxx') ==>当前目录/xxx   
    - 属性

7. assert     断言
    - 特性
        - 本身是一个函数，可以直接被调用，assert(boolean, msg)   如果boolean为false 则抛出异常并提醒msg
    - 方法
        - deepEqual(变量,预期值,msg);
        - deepStrictEqual(变量,预期值,msg);
    - 属性

8. net     网络通信   （本质是对TCP协议的实现）  质量高速度慢

9. process  系统进程信息
    - 属性
        1. env     系统环境信息  返回一个对象
            - 属性
                1. OS   系统类型
    - 方法
    
10. util node后端实现promise格式调用api

    ```
    const fs = require('fs');
    const util = require('util');
    const readFile = util.promisify(fs.readFile);
    readFile('./index.html',{encoding: 'utf-8'})
    .then(res=>{
        console.log(res);
        
    })
    ```

    
##### 系统依赖包
- 表单
1. multiparty
    - 特性
    - 属性

    - 方法
        - Form({})     构造，创建form实例 传参{}配置
            - 属性
            - 方法
              
                - parse(req)
            - 事件
                - on('field',(name, value)=>{})    字段数据    name == 表单name  value == 表单value
                - on('file',(name, file)=>{})    文件数据      name == 表单name  file == 文件对象
                - on('close',()=>{})             表单解析完成触发 
                
                


##### 注意点
1. 表单提交不受跨域请求限制    因为表单提交时用户主动且明确提出的，所以不存在安全问题
2. post数据是异步的 且是分批发送的，因为数据量大
3. http 是基于文本进行传输的协议 所以会导致出现很多无效的数据传输，且转换耗费性能，所以性能偏低

#### 一些错误
- crypto 加密模块
    - Digest already called    digest()调用时一个实例只能调用一次，如果调用多次则报此错   crypto.createHash('md5').update(data).digest('hex')