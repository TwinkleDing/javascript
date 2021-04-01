# VUE

## v-show和v-if区别

作用：控制元素的显示和隐藏

### 不同点：

1. v-show: 使用css的diaplay:none来控制隐藏，初始化会加载一次，
2. v-if: 控制dom节点的删除和添加赖控制显隐，设置为false不会加载，初始渲染开销较小。频繁使用会不停销毁和创建dom，消耗性能。
3. 总结：频繁操作使用v-show，不频繁使用v-if，

## 父子组件传值

1. 父传子：props属性；子传父：$emit方法
2. 子组件添加ref属性在父组件操作，
3. 使用$parent和$children操作父子组件
4. 使用vuex进行父子传值
5. 使用$eventbus进行传值

## vue的生命周期

1. beforeCreate：
2. created
3. beforeMount
4. mounted
5. beforeUpdate
6. updated
7. beforeDestroy
8. destroy

## vue中data为什么是一个方法

## $nextTick()作用

## 常用指令

## slot插槽

## MVVM是什么

## vue双向绑定的原理

## diff算法

## vue相比其他框架好处

## vue-router

## vuex

