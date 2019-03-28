# Flux
单向数据流 始祖

# Redux
基本思想： 
1.组件从store获取状态
2.通过dispatch action进行状态的更新
3.监听store，store发生变化进行组件内值的更新
4.组件被删除时移除监听
## Action
## Store
- createStore()
- getState()
- subscribe()
- unsubscribe()
- 
## Reducer

## 容器组件和傻瓜组件
容器组件负责和Redux Store进行交互，处于外层
傻瓜组件只根据当前props进行渲染用户界面，目的是使傻瓜组件没有状态

## React-Redux
- Provider  提供包含store的context
- connect  连接傻瓜组件和容器组件
	- 是一个返回一个高阶组件的函数
	- 参数为mapStateToProps和mapDispatchToProps，两个函数，获取所有state数据的映射和返回所有的dispatch
# 模块化React和Redux
## 代码文件的组织方式
- 按功能组织，提供模块接口index.js
- 导出方式应该统一  export 或者  export default
## 状态树的设计
- 一个模块控制一个状态节点
- 避免冗余数据
- 树形解构扁平

# React组件的性能优化
