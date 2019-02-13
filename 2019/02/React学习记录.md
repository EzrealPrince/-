## JSX
1. **JSX**中的表达式，用大括号包裹起来
2. **JSX**是普通的Javascript对象，所以可以将他赋值给变量或者当作参数返回值等
3. **JSX**的属性
- 字符串使用双引号包裹
- 表达式使用大括号包裹
- 默认使用小驼峰命名，**class**变为**className**
4. babel转译器会把**JSX**转换成==React.createElement==
5. JSX类型可以使用点表示法，组件可以存在于对象之中。
6. 用户自定义组件首字母必须大写，小写会被识别为原生HTML标签
7. 运行时选择组件类型，标签名不能是一个表达式，但是可以将其先赋值给一个大写开头的变量
8. 传递字符串常量时，该值为HTML非转义的，特殊符号会被解析
9. 属性值默认为true
10. 支持展开操作符
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
3. 不能使用**return false**来组织默认事件，必须使用**preventDefault()**
4. 类的方法默认不会绑定this，所以需要对时间回调函数绑定this，**this.handle = this.handle.bind(this)**,或者使用其他两种方法代替
- 回调写成箭头函数，在事件绑定里使用**onClick={this.handle}**
- **onclick={(e) => this.handle(e)}**
5.向事件处理程序传递参数
- 通过箭头函数调用的方法 **onclick={(e) => this.handle(id,e)}**
- 通过bind调用的方式**onClick={this.handle(this,id)}**,通过这种方式事件对象隐式传递，而且在所传递参数的后面

## React生命周期方法
1. **render()**
- 必须方法，纯函数，不应该改变组件状态，且不直接和浏览器交互
- **shouuldComponentUpdate**返回false，render函数将不会被调用
2. **constructor()**
- 在装载之前被调用，为了初始化局部状态或者绑定事件处理方法到某个实例
- super(props)需要在所有表达式之前声明
3. **compinentDidMount()**
- 紧跟在组建装载后(被插入到树中)调用，要求DOM节点初始化应该放在这里
- 适合实例化网络请求、建立订阅
4. **componentDidUpdate()**
- 紧跟在更新后调用，对于初次的渲染，该方法并不会调用
- 适合数据改变时发送数据请求
5. **componentWillUnmount()**
- 紧挨着组件被卸载和销毁之前调用，适合解绑定时器，取消网络请求，清理订阅等
- 


