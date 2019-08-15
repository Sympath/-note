### gulp && grunt

后者先问世，但是属于读写处理，即每次完成任务都得文件读取和写入；而前者属于流式操作，即多任务一次读写，效率有显著提升。

### CSS模块化

- 设计原则

  - 可复用能继承要完整
  - 周期性迭代

- 设计方法

  - 先整体后部分再颗粒化

    布局=》页面=》功能=》业务

### JS组件设计

- 设计原则
  - 高内聚低耦合
  - 周期性迭代
- 设计方法
  - 先整体后部分再颗粒化

### 自适应

```
  <meta name=viewport content="width=device-width,initial-scale=1,maximum-scale=1,minimum-scale=1,user-scalable=no,minimal-ui">
```

- viewport
  - layout viewport
  - visual viewport
  - ideal viewport