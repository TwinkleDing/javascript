## 双向数据绑定原理

使用 es6 的 proxy 方式进行双向监听，优点：

1. 直接监听对象而非属性
2. 直接监听数组的变化
3. 拦截的方式有很多种
4. proxy 返回一个新对象，可以操作新对象达到目的

### vue2 使用 object.defineProperty 的缺点：

1. 因为 es5 的 object.defineProperty 无法监听对象属性的删除和添加
2. 不能监听数组的变化，除了 push/pop/shift/unshift/splice/spObject.definert/reverse，其他都不行
3. Object.defineProperty 只能便利对象属性直接修改（需要深拷贝进行修改）
