### 组件使用

- nav滚动效果实现
- 加载更多轮播实现
- 鼠标hover视频效果

### 踩坑小计

- 注意-webkit-text-stroke属性，其边框渲染是向内的，所以达不到设计稿上的效果，只能如下设置会好一点

  ```
  font-weight: bold;
  text-shadow: 0px 0px 14px rgba(84,39,66,1);
  -webkit-text-stroke: 1px #fff;
  ```

- 想实现nav如下效果，可以设置li为inline元素，这样就可以支撑padding撑开了

  ![1563679387374](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1563679387374.png)

