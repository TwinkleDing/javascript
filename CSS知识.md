## css 上下左右居中方法：

1. display:flex;justify-content:center;align-items:center
2. position:absolute;margin:auto;top:0;left:0;bottom:0;right:0
3. position:relative;left:50%;top:50%;transform:translate(-50%,-50%)
4. float:left;height:50%; clear:both;

## 重绘和回流

### 重绘在 dom 节点不发生几何属性及位置等变化改变元素的大小，位置等为重绘

### 回流

1. 添加或删除 dom 元素
2. 元素位置改变
3. 元素尺寸改变
4. 内容改变：文本或图片大小改变引起重新计算元素高度和宽度
5. 页面初始化渲染
6. 浏览器窗口尺寸发生改变

重绘不一定会引起回流，回流一定会引起重绘。

## 网页渲染原理

1. 拿到所有html结构，渲染dom树
2. 拿到所有样式结构，渲染cssom树
3. dom树和cssom树附和生成渲染树
4. 计算元素在页面上的位置和大小等（回流）
5. 绘制元素颜色等其他信息（重绘）

