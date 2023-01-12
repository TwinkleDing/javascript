## 基础类型

### 元组 Tuple

元组类型允许表示一个已知元素数量和类型的数组

```ts
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error
```

### 枚举 enum

枚举是对 js 标准数据类型的补充，使用枚举类型可以为一组数组赋予有好的名字

```ts
emun Color1 {REd, Green ,Blue}
let c:Color1 = Color1.Green;
//
enum Color2 {Red = 1, Green, Blue}
let colorName: string = Color2[2];

console.log(colorName);  // 显示'Green'因为上面代码里它的值是2
```

### void

表示没有任何类型。当一个函数没有返回值时，返回值类型通常是 void

```ts
function warnUser(): void {
	console.log("This is my warning message");
}
```

### Object 表示非原始类型，

```ts
declare function create(o: object | null): void;

create({ prop: 0 }); // OK
create(null); // OK

create(42); // Error
create("string"); // Error
create(false); // Error
create(undefined); // Error
```

### 类型断言

有时候你会遇到这样的情况，你会比 TypeScript 更了解某个值的详细信息。 通常这会发生在你清楚地知道一个实体具有比它现有类型更确切的类型。

```ts
// <>语法
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;
// as语法
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
// 上面两种形式是等价的。但是在jsx时，只有as语法是被允许的
```

## 接口

```ts
interface Label {
	lable: string;
	color?: string; // 可选属性。有时使用必须要判断非空，不然会报错
	readonly x: number; //只读属性
}
```

### 函数类型

```ts
interface SearchFunc {
	(source: string, subString: string): boolean;
}
let mySearch: SearchFunc;
// 对于函数类型的类型检查来说，函数的参数名不需要与接口里定义的名字相匹配。
// 同样 使用了函数类型的函数的变量不需要再次定义类型
mySearch = function (src, str) {
	let result = src.search(str);
	return result > -1;
};
```

## 函数

```ts
let myAdd: (x: number, y: number) => number = function (x: number, y: number): number {
	return x + y;
};
```

## 泛型

```ts
function identity<T>(arg: T): T {
	return arg;
}
```

## type 和 interface

-   type 类型别名；
    1. 可以生命任何类型
    2. 定义俩个同名的 type 会报异常
    3. type 可以使用交叉类型进行合并
-   interface 接口，主要用于类型检查；
    1. 只能定义对象类型
    2. 定义俩个同名的会合并
    3. interface 可以使用 extends，implements 进行扩展
