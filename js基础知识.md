## this指向
this永远指向一个对象  
this的只想完全取决于函数调用的位置
1. 默认指向window
2. 指向调用函数的位置
3. 在构造函数内指向该构造函数
4. (call(obj,多个参数)、apply(obj,[参数list]))函数立即执行和bind不立即执行可改变this指向
5. 箭头函数内部没有this。箭头函数内的this是定义该函数时所在的作用域指向的对象，而不是使用时所在的作用域指向的对象

## 闭包
闭包的3个特性  
1. 函数嵌套函数
2. 函数内部可以引用函数外部的参数和变量
3. 参数和变量不会被垃圾回收机制回收

好处  
1. 保护函数内的变量安全，实现封装，防止变量流入其他环境发生命名冲突
2. 在内存中维持一个变量，可以做缓存（但是用多了同样也是缺点，消耗内存）
3. 匿名函数自执行可以减少内存消耗

坏处
1. 引用的私有变量无法销毁，增大了内存消耗，造成内存泄露，解决方法是在使用完变量之后手动复制为null
2. 闭包设计跨域访问，所以会导致内存损失，可以通过把跨作用域变量存储在局部变量中，然后直接访问局部变量，来减轻对执行速度的影响

## 作用域和作用域链
1. 全局作用域：最外层函数定义的变量拥有全局作用域，即对任何内部函数来说都是可以访问的
3. 局部作用域：一般只有在固定代码片段可以访问，而对于函数外部是无法访问的

只要函数内定义了一个变量，函数会在解析的时候将这个变量‘提前声明’  
块级作用域：1，在一个函数内部，2，在一个代码块内（一对花括号）

作用域链：在当前作用域没有定义的变量，在调用时会一层一层向上寻找，直到找到位置，找到最外层找不到就报错，

## 构造函数new操作符做了什么
一共经历了4个阶段  
````js
1. 创建一个空对象
var obj = new Object() 
2. 设置原型链
obj.__proto__ = Func.prototype
3. 让Func的this指向obj，并执行Func的函数体
var result = Func.call(obj)
4. 判断Func的返回类型，如果是值类型，返回obj，如果是引用类型，就返回引用类型的这个对象
if(typeof(result) === 'object'){
  func = result
} else {
  func = obj
}
````

## 原型和原型链
### prototype
prototype是一个属性，每个函数都有一个这样的属性，它默认指向一个空对象，prototype中包含函数实例共享的方法和属性，即实例一旦创建，就会自动引用prototype对象的属性和方法。
### 构造器constructor
原型对象中还有一个属性constructor，其保存了指向该函数的一个引用

### 隐式原型__protot__
每个函数都有一个prototype，即显式原型。  
每个实例对象都有__oroto__。即隐式原型。  
**对象的隐式原型的值指向对应构造函数的显示原型的值**
````js
function Star(uname, age) { // 函数
    this.uname = uname;
    this.age = age;
    this.sing = function() {
      console.log('I can sing！');
    }
  }
var ldh = new Star('刘德华', 18);  // 实例
console.log(ldh.__proto__ === Star.prototype); // true  说明对象的隐式原型的值指向对应构造函数的显示原型的值
console.log(Star.prototype.constructor);  
console.log(Star.prototype.constructor === Star); // 结果为 true，说明Star原型对象的constructor指向Star本身
console.log(ldh.constructor);
console.log(ldh.constructor === Star); // 结果为true，说明Star的实例对象的constructor也指向构造函数Star本身
````

### 原型链
原型链就是根据prototype和__proto__连接起来的一个原型链条。  
**通过原型链访问一个对象的属性的方法：**  
先在自身属性中查找，找到则返回，如果没有，再沿着__proto__这个链向上查找，找到则返回，没有则继续沿着__proto__这个链向上查找，如果最终找到Object的原型对象还是没有找到，则返回undefined。

## 原型的继承

## 什么是面向对象，类和实例

## class类与继承