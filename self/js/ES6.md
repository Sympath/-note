#### Promise

- 极度简单的promise

  ```-
  //构造
  function Promise(excutor) {
    let self = this
    self.status = 'pending'
    self.value = null
    self.reason = null
    function resolve(value) {
      if (self.status === 'pending') {
        self.value = value
        self.status = 'fulfilled'
      }
    }
    function reject(reason) {
      if (self.status === 'pending') {
        self.reason = reason
        self.status = 'rejected'
      }
    }
    try {
      excutor(resolve, reject)
    } catch (err) {
      reject(err)
    }
  }
  //原型链
  Promise.prototype.then = function (onFulfilled, onRejected) {
    let self = this
    if (self.status === 'fulfilled') {
      onFulfilled(self.value)
    }
    if (self.status === 'rejected') {
      onRejected(self.reason)
    }
  }
  ```

  逻辑：

  1. 调用`then`方法，将想要在`Promise`异步操作成功时执行的回调放入`callbacks`队列，其实也就是注册回调函数，可以向观察者模式方向思考；
  2. 创建`Promise`实例时传入的函数会被赋予一个函数类型的参数，即`resolve`，它接收一个参数value，代表异步操作返回的结果，当一步操作执行成功后，用户会调用`resolve`方法，这时候其实真正执行的操作是将`callbacks`队列中的回调一一执行；