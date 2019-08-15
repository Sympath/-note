### html

除非子组件模板包含至少一个 <slot> 插口，否则父组件的内容将会被丢弃。当子组件模板只有一个没有属性的插槽时，父组件传入的整个内容片段将插入到插槽所在的 DOM 位置，并替换掉插槽标签本身。

###### 插槽slot

- 匿名插槽

  - my-component 组件

    ```
    <div>
      <h2>我是子组件的标题</h2>
      <slot>
        只有在没有要分发的内容时才会显示。
      </slot>
    </div>
    ```

  - 父组件

    ```
    <div>
      <h1>我是父组件的标题</h1>
      <my-component>
        <p>这是一些初始内容</p>
        <p>这是更多的初始内容</p>
      </my-component>
    </div>
    ```

  - 渲染结构结果

    ```
    <div>
      <h1>我是父组件的标题</h1>
      <div>
        <h2>我是子组件的标题</h2>
        <p>这是一些初始内容</p>
        <p>这是更多的初始内容</p>
      </div>
    </div>
    ```

- 具名插槽

  `<slot>` 元素可以用一个特殊的特性 name 来进一步配置如何分发内容。多个插槽可以有不同的名字。具名插槽将匹配内容片段中有对应 slot 特性的元素。

  仍然可以有一个匿名插槽，它是默认插槽，作为找不到匹配的内容片段的备用插槽。如果没有默认插槽，这些找不到匹配的内容片段将被抛弃。

  -  app-layout 组件

    ```
    <div class="container">
      <header>
        <slot name="header"></slot>
      </header>
      <main>
        <slot></slot>
      </main>
      <footer>
        <slot name="footer"></slot>
      </footer>
    </div>
    ```

  - 父组件

    ```
    <app-layout>
      <h1 slot="header">这里可能是一个页面标题</h1>
    
      <p>主要内容的一个段落。</p>
      <p>另一个主要段落。</p>
    
      <p slot="footer">这里有一些联系信息</p>
    </app-layout>
    ```

  - 渲染结构结果

    ```
    <div class="container">
      <header>
        <h1>这里可能是一个页面标题</h1>
      </header>
      <main>
        <p>主要内容的一个段落。</p>
        <p>另一个主要段落。</p>
      </main>
      <footer>
        <p>这里有一些联系信息</p>
      </footer>
     </div>
    ```

  