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
在没有明确指定类型时定义一个变量并赋值，ts会进行类型推论，给该变量推测出一个类型

## 联合类型
表示取值可以为多种类型中的一种
`
let numberString: string | number
numberString = '1111'
numberString = 1111
`
访问联合类型的属性或方法不确定一个联合类型的变量到底是哪个类型的时候只能访问联合类型的所有类型里共有的属性或者方法

联合类型的变量在赋值的时候，会根据类型推论规则推断出一个类型

## 对象的类型 接口

使用接口（interfaces）来定义对象的类型

接口是对类的一部分行为进行抽象，同事也用于描述对象的形状

接口一般首字母大写，定义的变量比接口少了一些属性或者多一些属性都是不允许的

`
interface Person {
    name: string;
    age: number;
}

let tom: Person = {
    name: 'Tom',
    age: 25
};
`
**可选属性**
可选属性用一下方法来表示

`
age?: number
`
**任意属性**
`
[propName: string]: any
`
一旦定义了任意属性，那么确定属性和可选属性的类型都必须是它的类型的子集

**只读属性**
要求对象中的某些字段只能在创建的时候被赋值，那么用**readonly** 字段来标识
`
interface Person {
    readonly id: number
}
`
只读属性的约束是在第一次给对象赋值的时候，而不是第一次给只读属性赋值的时候

## 数组的类型

最简单的方法是使用 **[类型 + 方括号]** 来定义数组

数组的项中不允许出现其他的类型

**数组泛型**
`
let numbers: Array<number> = [1,2,3,4]
`

**用接口表示数组**
`
interface NumberArray {
    [index: number]: number;
}
let fibonacci: NumberArray = [1, 1, 2, 3, 5];
`
**any在数组中的应用**
表示数组中允许出现任意类型

## 函数的类型
### 函数声明
函数声明和函数表达式
函数必须被约束，需要把输入输出都考虑到，输入多余的或者少于要求的参数是不被允许的
`
let mySum: (x: number, y: number) => number = function (x: number, y: number): number {
    return x + y;
};
`

### 用接口来定义函数的形状
约束参数和返回值类型

### 可选参数
可以使用 ？ 来表示可选的参数
可选参数后不允许出现参数

### 参数默认值
TypeScript会将添加了默认值的参数识别为可选参数

### 剩余参数

...rest 是一个数组，所以可以使用数组的类型来定义
rest参数只能是最后一个参数
`
function push(array: any[], ...items: any[]) {
    items.forEach(function(item) {
        array.push(item);
    });
}
`
### 函数重载

## 类型断言
类型断言（Typpe Assertion）可以用来手动指定一个值的类型
`
<类型> 值
`
或者
`
值 as 类型
`
在tsx语法中必须使用后一种

用于在联合类型中书写代码防止出错而存在的

类断言不是类型转换，断言成一个联合类型中不存在的类型是不允许的

## 声明文件
使用第三方库时需要引用它的声明文件，才能获得对应的代码补全

语法：
`
declare var jQuery: (selector: string) => any;
`
声明文件后缀 .d.ts

可以直接使用@types统一管理第三方库的声明文件

- declare var 声明全局变量
- declare function 声明全局方法
- declare class 声明全局类
- declare enum 声明全局枚举类型
- declare namespace 声明全局对象（含有子属性）
- interface 和 type 声明全局类型

## 内置对象

## 类型别名
给一个类型起个新名字

## 字符串字面量类型
约束用来取值只能时某几个字符串中的一个
`
type EventNames = 'click' | 'scroll' | 'mousemove';
`
## 元组（Tuple）






