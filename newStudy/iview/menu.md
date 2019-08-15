```
<Menu active-name="">
        <MenuItem  name="home" to="/home">home</MenuItem>
        <MenuItem name="about" to="/about">about</MenuItem>
 </Menu>
```

- MENU
  - active-name   高亮菜单项





### 实战

- 根据路由高亮对应菜单项

  - 高亮项根据active-name进行判断匹配的MenuItem的name属性
  - 获取路由参数  *this*.$route.path        类似 /home
  - 监听$route动态改变Menu上的active-name属性

  ```
  <!--Menu  -->
  <template>
    <div id="app">
      <div id="nav">
        <Menu :active-name="act_name">
          <MenuItem name="/home" to="/home">home</MenuItem>
          <MenuItem name="/about" to="/about">about</MenuItem>
        </Menu>
      </div>
    </div>
  </template>
  
  <script>
    export default {
      components: {},
      data() {
        return {
          act_name: this.$route.path
        };
      },
      computed: {},
      watch: {
        "$route"(){
          this.act_name = this.$route.path
        }
      },
      methods: {
      },
    }
  </script>
  <style lang='scss' scoped>
  </style>
  ```

  