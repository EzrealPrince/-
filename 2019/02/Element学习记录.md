## Message消息提示
- 默认调用方法. **this.$message**,可以接受一个字符串也可以接受一个VNode,使用渲染函数

- 可以显示不同状态下的消息，函数参数传入对象，**message** 表示提示文本，**type** 表示提示类型，也可以直接通过**message**的子方法调用
- **center**属性使文字居中
- 将**dangerouslyUseHTMLString**设置为true，可以将**message**当作HTML片段处理

## MessageBox
美化了系统自带的**alert、confirm和prompt**，只适合展示较为简单的内容，如果需要弹出复杂的内容，使用**Dialog**

