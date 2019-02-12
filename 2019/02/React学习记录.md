## JSX
1. **JSX**中的表达式，用大括号包裹起来
2. **JSX**是普通的Javascript对象，所以可以将他赋值给变量或者当作参数返回值等
3. **JSX**的属性
- 字符串使用双引号包裹
- 表达式使用大括号包裹
- 默认使用小驼峰命名，**class**变为**className**
4. babel转译器会把**JSX**转换成==React.createElement==

## state和生命周期
1. **正确的使用状态**
- 要更新组件状态不能直接修改，必须使用**setState**函数
- 构造函数是唯一能够初始化**this.state**的地方
- 单项数据流
- 组件可以使用函数或者类来构造，**state**只存在类声明结构，**props**都可以
2. 生命周期钩子
- componentDidMount() 
- componentWillUnmount()

## 事件处理
1. 事件绑定属性命名使用驼峰式
2. 应该传入函数名称
3. 