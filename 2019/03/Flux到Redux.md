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
