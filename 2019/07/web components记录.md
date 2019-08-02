## 自定义组件
### 注册
window.customElements.difine('my-element',MyElement)
window.customElements.get('my-element')
## 生命周期
connectedCallback()   当元素被插入到DOM树的时候将会触发这个方法
disconnectCallback()   当元素从DOM树中移除的时候将会被调用
adoptedCallback() 还不是很清楚
attributeChangedCallback()