客户端默认会在第二次请求时带上请求头Cookie字段，值为k1=v1;k2=v2格式









### 一些知识

- httponly：禁止js通过document.cookie对cookie进行操作===为了避免类似CSRS（即通过注入脚本或url引导用户发送自己的cookie）的网络攻击
- cookie默认在浏览器关闭时销毁