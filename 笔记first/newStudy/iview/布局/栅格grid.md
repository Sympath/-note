### 组件

#### 核心组件

- Row
  - 属性
    - type
      - flex
    - justify
      - center   在type为flex时将主轴项目排布设为居中
    - align
      - middle  在type为flex时将侧轴项目排布设为居中
- Col   （注意如果col标签内容为空，则会不占据文档流，可能造成初次进入页面，页面闪动，可以放一个空div，设置样式为height：1px解决）
  - 属性
    - span    24列栅格系统所占列数
    - offset   向右偏移列数     用于实现一列内容空出一块


#### 功能性组件

- Avatar  头像
  - 属性
    - src   头像图片链接
- Icon
  - 属性
    - type
      - ios-checkmark  √
    - color     颜色
    - size      大小

### 实战

- 图文居中

  ```
  <template>
    <div id="app">
      <Row type="flex" justify="center" align="middle">
        <i-col span="4">
          <Avatar src="https://n.sinaimg.cn/front/94/w560h334/20190114/_IE3-hrpcmqw4458934.jpg">
  
          </Avatar>
        </i-col>
        <i-col span="18">
          <div>少年听雨歌楼上，红烛昏罗帐。壮年听雨客舟中，江阔云低、断雁叫西风。
            而今听雨僧庐下，鬓已星星也。悲欢离合总无情，一任阶前、点滴到天明。</div>
          <div>少年听雨歌楼上，红烛昏罗帐。壮年听雨客舟中，江阔云低、断雁叫西风。
            而今听雨僧庐下，鬓已星星也。悲欢离合总无情，一任阶前、点滴到天明。</div>
          <div>少年听雨歌楼上，红烛昏罗帐。壮年听雨客舟中，江阔云低、断雁叫西风。
            而今听雨僧庐下，鬓已星星也。悲欢离合总无情，一任阶前、点滴到天明。</div>
        </i-col>
        <i-col span="2">
          <Icon type="ios-checkmark" color="#2d8cf0" size="28" ></Icon>
        </i-col>
      </Row>
    </div>
  </template>
  
  <style>
    body {
      height: 5600px;
      background: #f8f8f9 !important;
    }
  </style>
  ```

  