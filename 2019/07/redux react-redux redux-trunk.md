## redux
### action
- action是view变化时发出的通知，用来提示state
- action一般时一个对象，至少需要一个type属性
- action creator 用来生成action的函数
### reducer
- store收到action时需要返回一个新的state，这样view才会重新渲染
- reducer是一个函数，他接受action和state作为参数，返回一个新的state
- 一般情况下在生成store时将reducer传入createStore即可在接收到action时自动执行
- 必须是一个纯函数
- 
### store
- 保存数据的地方，整个应用的数据容器
- 使用createStore()这个函数来生成store
- store.dispatch（）时view发出action的唯一方法
### state
- 某个时点的数据即可成为state，当前时刻的state可以通过store.getState()获得


### reducer的拆分
- combineReducers
