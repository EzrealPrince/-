## Message消息提示
- 默认调用方法. **this.$message**,可以接受一个字符串也可以接受一个VNode,使用渲染函数

- 可以显示不同状态下的消息，函数参数传入对象，**message** 表示提示文本，**type** 表示提示类型，也可以直接通过**message**的子方法调用
- **center**属性使文字居中
- 将**dangerouslyUseHTMLString**设置为true，可以将**message**当作HTML片段处理

## MessageBox
美化了系统自带的**alert、confirm和prompt**，只适合展示较为简单的内容，如果需要弹出复杂的内容，使用**Dialog**
方法与参数
- this.$alert  
- this.$confirm  
- this.$prompt
- 都返回promise
- confirmButtonText **String** 确定按钮文本
- cancelButtonText **String** 取消按钮文本
- type 类型 **String** info、warning、error、success
- inputPattern 正则 **regexp**匹配prompt中输入格式
- inputErrorMessage **String**
 匹配失败提示
- 也可以通过渲染函数传入自定义模板
- dangerouslyUseHTML **String**设置为true，文本默认解析为HTML
- showClose **boolean** 是否显示关闭按钮

## Notification通知
- this.$notify
- title **String** 标题
- message **String | renderFunction** 正文
- type **String** 类型
- position **String** 弹出位置，默认为 **top-right**
- duration **Number** 显示时间，为0时永不关闭
- offset **Number** 偏移量
- showClose **Boolean** 关闭按钮显示控制
- dangerouslyUseHTML **String**设置为true，文本默认解析为HTML
- onClick 点击时的回调函数

## Loading加载
- 指令方式
	- v-loading 指令，绑定布尔类型变量
	- element-loading-text 加载文案
	- element-loading-spinner 加载图标类名
	- element-loading-background 背景色
	- 覆盖全屏 指令修饰符 fullscreen
	- 锁定页面滚动 修饰符lock
	- v-loading.fullscreen.lock
- 服务方式
	- this.$loading
	- 参数为options，默认全屏
	- lock **boolean** 锁定滚动
	- spinner **String** 图标内容
	- text **String** 加载文案
	- background **rgba** 背景色
	- target **DOM对象 | String** 若传入字符串，则默认调用document.querySelector获取到对应DOM
	- loading.close 关闭加载