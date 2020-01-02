### 属性操作变量

 - computed     将计算处理后返回的内容作为变量返回

   ```
   computed: {
                   sum: {
                       get() {
                           return this.count * this.price
                       },
                       s et(newVal) {
                           this.count = newVal / this.price;
                       }
                   }
               }
   ```

   

 - watch  监听变量的改变 

   ```
   watch: {
                   wendu(newVal,oldVal){
                       console.log("温度改变：", newVal, oldVal);            
                   }
   ```
   
   

- extends    将vue之外的方法拉至内部使用 注意如果与methods重名则方法不生效，但与生命周期同名则会生效