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

1. beforeCreate：初始化事件，进行数据的观测，methods和data读取不到
2. created：vue实例化创建，完成了数据观测、属性和方法的运算，watch回调，$el属性不可见，因为还没有渲染，此时dom还没有挂在，允许进行http请求
3. beforeMount：将HTML解析生成AST节点，再根据AST节点动态生成渲染函数，render函数首次调用
4. mounted：vue实例对象添加$el成员，并且替换掉之前的dom元素，挂载到页面
5. beforeUpdate：当vue发现data数据发生变化，会触发对应组件的重新渲染，当数据改变后调用
6. updated：当改变的数据渲染完成之后调用
7. beforeDestroy：在实例化销毁前调用，此时实例化任然可以使用，清空定时器在此时
8. destroyed：在vue实例化销毁之后调用，调用后，vue实例指示的东西全部解绑，所有事件监听器移除，挂载的子组件实例也会被销毁

### 初始化ajax请求

初始化请求一般在created之中完成，因为只是后data与methods实例化完成，可以更快获取到服务器的数据，ssr不支持 beforeMount 、mounted 钩子函数。

放在mounted之后的话在页面初次渲染完成了，先读取默认数据，在根据ajax返回值再次改变页面视图，进行了二次渲染，

## vue中data为什么是一个方法

当定义成对象时，所有的组件共享一个data，导致一个组件修改值，其他组件的引用也会发生变化。当定义成一个函数时，数据是函数的返回值，每个函数都会定义一个新的空间，各自维护各自的数据，不会造成混乱。

## $nextTick()作用

因为vue渲染dom是异步的，当修改了data的值时，马上获取dom的数据是获取不到更新后的值的，所以使用$nextTick()回调，让你的操作在dom渲染完成之后执行。

## 常用指令

v-model;v-if;v-show;v-html;v-bind;v-on;v-for

## slot插槽

一个组件放置的内容不确定是什么类型，组件，文本或者其他时，这个位置就可以防止一个插槽。

1. 默认插槽：设置插槽的默认值，不使用的时候渲染默认值，使用的时候代替掉
2. 具名插槽：插槽添加name属性，使插槽具有唯一性，
3. 带参数的插槽：插槽定义时，绑定数据，使使用插槽时可以使用绑定在插槽上的数据

## MVVM是什么

M:  model
V:  view
VM:  viewmodel

MVVM不同于MVC的层层控制，去除了C的控制层，使用VM代替，VM时V和M的映射，操作数据来操作试图进而操作dom，借助于MVVM无需直接操作dom

关注Model的变化，让MVVM框架去自动更新DOM的状态，从而把开发者从操作DOM的繁琐步骤中解脱出来

## vue双向绑定的原理

## diff算法

1. 使用了虚拟dom来代替真实的dom
2. 新旧虚拟dom比较，如果有差异则以新的为准，然后再插入真实的dom重新渲染
3. 先比较同级，如果有变化则直接替换，没有变化进入下级检测
4. v-for必须绑定key，是一个唯一标识，可以更有效的利用虚拟dom的diff算法，找到正确的位置重新插入新的节点。但是不推荐使用index，因为每次重新赋值list，index是变化的，每一个项即使没变，key也可能发生变化，从而出发了diff算法，重新渲染，浪费内存

## vue-router

### 动态路由

使用addRouter添加。

### 导航钩子函数

1. 全局路由守卫：router.beforeEach
2. 组件内的钩子函数
3. 单独路由独享组件

### 路由懒加载

1. vue异步组件技术
2. 使用component直接调用import，不在文件头部定义
3. webpack配置

### params传参和query传参区别

1. params传参必须要用路由的name，传参不可见，url地址不显示，
2. query传参需要用路由的path，传参可见，url地址会显示，

## vuex

vue的黄台管理工具，在main中引入store，然后注入。单页面应用中组件之间的状态，

**state** 存放基本数据  
**getters**  读取state的值，类似于computed，具有缓存   
**mutations**  修改state里面的值，所有修改state的操作必须在这里的方法里完成，同步的  
**actions**  异步的，一般是调用ajax，然后掉哦那个mutations的方法以修改state的值  
**modules**  模块化vuex

## vue与其他框架的对比
