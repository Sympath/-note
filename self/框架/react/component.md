- 组件定义

  ```
  import React from "react";
  export default class Child1 extends React.Component {
      render (){
          return (
              <div>
              </div>
          )
      }
  }
  ```

- 组件引用

  ```
  import Context from "./Context";
  <Context data={data}>msg</Context>
  ```

  #### 父传子

  - html  slot 

    子组件接收msg

    ```
     {this.props.children}
    ```

  - data props

    ```
     {this.props.data}
    ```

  #### 子传父

  - 回调实现