### 路由

- 路由表定义

  ```
   import Goods from '@/components/goods/goods'
   {
        path: '/goods',
        name: 'goods',
        component: Goods,
        children:[
          {
              path:'router1',
              component:Router1
          },
          {
              path:'router2',
              component:Router2
          }
      ]
      }
  ```

- 动态路由

  ```
   <router-link to="/goods/:id">商品</router-link>
   this.$route.params.id
  ```

- 函数式路由

  ```
  this.$router.push({
        name:goods,
        params:{id:1}
        })
   this.$route.params.id
  ```

- 路由嵌套

  ```
  <li><router-link to="/goods/router1">路由1</router-link></li>
  <li><router-link to="/goods/router2">路由2</router-link></li>
  <router-view></router-view>
  ```

- 命名路由

  ```
   <router-link :to="{name:goods,params:{id:1}}">商品</router-link>
    this.$route.params.id
  ```
- 路由传参

  ```
  传递
  占位符：  路径上:id
  函数式路由中的params
  获取
  {{$route.params.id}}
  ```

- 路由重定向

  ```
    {
        path: '/detail',
        redirect: '/'
      }
  ```