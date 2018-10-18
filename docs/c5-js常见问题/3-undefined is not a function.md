#### undefined is not a function 
出现'undefined is not a funcation'错误通常是某个方法没有调用。而有些情况在PC机的浏览器中是正常的，转到移动端出现这种错误(通常难以查找)。
这种错误的原因有多种，以下列出几种可能的原因

**原因**: 
1. 使用了es6中的findIndex等一些新API。部分安卓机不支持
    如果我们没有配置一些规则，Babel 默认只转换新的 JavaScript 句法（syntax），而不转换新的 API，比如 Iterator、Generator、Set、Maps、Proxy、Reflect、Symbol、Promise 等全局对象，以及一些定义在全局对象上的方法（比如 Array.findIndex、Object.assign 等）都不会转码。


**解决**：
1. 使用babel-polyfill，为当前环境提供一个垫片。

**相关链接**:
[babel-polyfill使用与性能优化](https://www.cnblogs.com/chyingp/p/understanding-babel-polyfill.html)
