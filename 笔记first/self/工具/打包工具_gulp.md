#### gulp  返回对象
- 属性
    1. 
- 方法
    1. task(path,()=>{
        return gulp.
    })
    2. src([...paths])   压缩文件路径
    3. dest(path)    压缩后输出文件夹路径
    4. 流式操作  gulp.src([]).pipe(souermaps.init())
        .pipe(babel({presets: [@babel/env]}))
        .pipe(concat('汇总文件名'))
        .pipe(uglify())
        .pipe(sourcemaps.write())
        .pipe(rename({suffix: "min"}))
        .pipe(gulp.dest(''))
    5. 默认任务  gulp.task('defualt',['taskname'...])

##### 包安装
1. 启动器  npm i gulp -g
2. 本地核心包 npm i gulp




##### 工具包 基本返回一个函数，调用json传参
1. gulp-uglify
2. gulp-concat   合并文件
3. gulp-rename   更改压缩后的名字 
    {}
        1. suffix: '后缀'  
4. gulp-babel   适配器
    - @babel/core @babel/preset-env     babel核心库
    {}
        1. presets:[@babel/env]

5. gulp-sourcemaps  保留源码信息，便于调试              返回一个对象
    - 属性
    - 方法
        1. init()   在压缩前调用
        2. write()   在压缩后调用
6. gulp-cssmin    压缩css

7. gulp-imagemin  压缩image
    []
        imagemin.gifsicale({interlaced:true})   隔行加载
        imagemin.jpegtran({propressive: true})
        imagemin.optipng({optimizationLevel: 5})   



