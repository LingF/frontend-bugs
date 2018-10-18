#### cookie发送不成功
ajax发送请求，cookie发送不成功  

**原因**:  
1. [跨域问题](https://yq.aliyun.com/articles/610080)  
2. 代码使用了请求模拟, 如mockjs  

**解决方法**：  
方法一：  
网页端中，对于跨域的 XMLHttpRequest 请求，需要设置withCredentials 属性为 true。  
同时服务端的响应中必须携带 Access-Control-Allow-Credentials: true 首部。如果服务端的响应中未携带Access-Control-Allow-Credentials: true 首部，浏览器将不会把响应的内容返回给发送者。  

要想设置和获取跨域 Cookie，上面提到的两点缺一不可。另外有一点需要注意的是：规范中提到，如果 XMLHttpRequest 请求设置了withCredentials 属性，那么服务器不得设置 Access-Control-Allow-Origin的值为* ，否则浏览器将会抛出The value of the 'Access-Control-Allow-Origin' header in the response must not be the wildcard '*' 错误。

方法二：  [Nginx反向代理解决前后端联调跨域问题](https://segmentfault.com/a/1190000010197683)

[更多方法：](https://juejin.im/post/5b5787e1f265da0f6263804d)