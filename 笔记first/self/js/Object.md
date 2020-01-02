- Object
  - 属性
  - 方法
    
    - assert(a,b,..c)  对象的合并，将所有第二个开始的参数对象的属性合并至第一个参数对象并返回合并后的对象
    
    - defineProperty(obj,name,{})
    
      ```
       function watch(obj,name,fn) {
                  let value = obj[name];
                   Object.defineProperty(obj, name,{
                      get: function () {
                          console.log('獲取', value);
                          return value
                      },
                      set: function (val) {
                          fn(val)
                          value = val;
                      }
                  })  
              }
      ```
    
      {}		均默认为false
    
      - 属性
        - value  	设置值 相当于set简写
        - enumerable       可遍历的
        - writable    可修改的
        - configurable     可删除的
    
      - 方法
    
        - get
    
          ```
           function () {
                              console.log('獲取', value);
                              return value
                          }
          ```
    
        - set
    
          ```
           function (val) {
                              fn(val)
                              value = val;
                          }
          ```
    
          
