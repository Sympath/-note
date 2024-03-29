### CSP是什么
CSP指的是内容安全策略，为了缓解很大一部分潜在的跨站脚本问题，浏览器的扩展程序系统引入了内容安全策略（CSP）的一般概念。这将引入一些相当严格的策略，会使扩展程序在默认情况下更加安全，开发者可以创建并强制应用一些规则，管理网站允许加载的内容。简单来说，就是我们能够规定，我们的网站只接受我们指定的请求资源。

### CSP的意义

防XSS等攻击的利器。CSP 的实质就是白名单制度，开发者明确告诉客户端，哪些外部资源可以加载和执行，等同于提供白名单。它的实现和执行全部由浏览器完成，开发者只需提供配置。CSP 大大增强了网页的安全性。攻击者即使发现了漏洞，也没法注入脚本，除非还控制了一台列入了白名单的可信主机。

### CSP的分类

- Content-Security-Policy 
  配置好并启用后，不符合 CSP 的外部资源就会被阻止加载。 

- Content-Security-Policy-Report-Only 

  表示不执行限制选项，只是记录违反限制的行为。它必须与report-uri选项配合使用。

### CSP的使用

- 在HTTP Header上使用（首选）

  ```
  "Content-Security-Policy:" 策略
  "Content-Security-Policy-Report-Only:" 策略
  ```

  