## 语法
- 可以带{或者不带
- 变量声明与使用
	- $+变量名+: +变量值
	- 普通变量和默认变量，默认变量需要在后加 !default
	- 局部变量和全局变量，元素里声明为局部变量，元素外为全局
- 选择器嵌套 & 表示当前路径上的选择器
- 属性嵌套，例如font，border等
- 混合 mixin
	- 声明 @mixin mixinName { 属性 }
	- 调用 @include mixinName
	- 可以传输参数，参数可以拥有默认值
- 样式继承 @extend 选择器名
- %占位符，如果没被@extend继承则不参与编译
- 加减乘除运算
