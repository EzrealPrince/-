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
l