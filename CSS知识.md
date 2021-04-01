## css上下左右居中方法：
0. display:flex;justify-content:center;align-items:center
1. position:absolute;margin:auto;top:0;left:0;bottom:0;right:0
2. position:relative;left:50%;top:50%;transform:translate(-50%,-50%)
3. float:left;height:50%; clear:both;

## 重绘和回流

### 重绘在dom节点不发生几何属性及位置等变化改变元素的大小，位置等为重绘

### 回流

1. 添加或删除dom元素
2. 元素位置改变
3. 元素尺寸改变
4. 内容改变：文本或图片大小改变引起重新计算元素高度和宽度
5. 页面初始化渲染
6. 浏览器窗口尺寸发生改变

重绘不一定会引起回流，回流一定会引起重绘。

