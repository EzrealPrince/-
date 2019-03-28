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
可以定义一个** void **