## 原始数据类型
### 布尔值
`
let isDone: boolean = false
let createdByBoolean: boolean = Boolean(1);
let createdByNewBoolean: Boolean = new Boolean(1); //编译报错，使用构造函数创造的对象不是布尔值
`
### 数值类型
`
let decLiteral: number = 6
let hexLiteral: number = 0xf00d
let binaryLiteral: number = 0b1010
`
可以直接使用二进制表示法或者八进制表示
会被编译为10进制

### 字符串
`
let myName: string = 'Tom'
`
支持模板字符串

### 空值
可以定义一个 **void** 类型的函数表示该函数没有返回值

### Null和Undefined
`
let u: undefined = undefined;
let n: null = null;
`
1. undefined和null是所有类型的子类型，所以可以赋值给任意类型的变量
2. void类型的变量不能赋值给其他类型

## 任意值
**any**
`
let myFavoriteNumber: any = 'seven';
myFavoriteNumber = 7;
`
对任意值进行的任何操作，返回的内容类型也为任意值

如果定义变量时未声明类型，且未赋值，则默认被识别为任意值类型

## 类型推论
在没有明确指定类型时定义一个变量并赋值，ts会进行类型推论，给该变量推测处

