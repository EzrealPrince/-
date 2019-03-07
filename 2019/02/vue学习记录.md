# Vue学习心得
## 1、模板语法
- 插值
    - 文本  **v-once** 只渲染一次
    - 原始HTML  **v-html**
    - 特性 **v-bind** 值必须为true
    - 使用JavaScript表达式 只能是一句表达式
- 指令
    - **v-if**  条件渲染
    - **v-bind** 参数接收 简写 :
    - **v-on** 事件监听 简写@
    - 修饰符
## 2、计算属性和侦听器
- 计算属性 **computed**
    - 为属性设置getter函数
    - 示例
    ```javascript
    var vm = new Vue({
      el: '#example',
      data: {
        message: 'Hello'
      },
      computed: {
        // 计算属性的 getter
        reversedMessage: function () {
          // `this` 指向 vm 实例
          return this.message.split('').reverse().join('')
        }
      }
    })
    ```
    - 基于依赖缓存，只有依赖发生改变时他们才会重新求值
- 侦听属性 **watch**
    - 依赖的属性发生改变则重新计算
    - 当需要在数据变化时**异步执行**或开销较大的操作时，常用watch
    - 也可以使用命令式的 **vm.$watch API**
## 3、Class与Style绑定
- 绑定HTML Class
    - 对象语法 动态切换class，可以绑定一个对象
    - 数组语法 将一个数组传给class，应用一个class列表，数组语法可以和对象语法嵌套使用
    - 示例
    ```javascript
    <div v-bind:class="classObject"></div>
    <div v-bind:class="[activeClass, errorClass]"></div>
    <div v-bind:class="[{ active: isActive }, errorClass]"></div>
    data: {
      activeClass: 'active',
      errorClass: 'text-danger'，
      isActive: true,
      hasError: false，
      classObject: {
        active: true,
        'text-danger': false
      }
    }
    ```
    - 组件使用时添加的class不会覆盖原有class
- 绑定内联样式
    - 对象语法 改变style
    - 数组语法
    - 自动添加浏览器引擎前缀
## 条件渲染
- **v-if**
- **v-else**  必须紧跟在 **v-if** 或者 **v-else-if** 后面
- **v-else-if**  限制同上
- 当想要条件渲染多个元素时可以用 **template** 包裹起来
-  用 **key** 管理可复用的元素
-  **v-show** 渲染的元素始终保留在DOM中，只是切换元素的 **display** 属性，不支持 **template** 元素
- 当 **v-if** 和 **v-for** 同时使用时，后者拥有更高的优先级

## 列表渲染
- **v-for** 在其块中，拥有对父作用域属性的完全访问权限，支持一个可选的第二个参数指向当前项的索引
- 可以用of代替in，可以迭代一个对象的属性，并且可以提供第二个参数为键名，第三个参数为索引。使用的是 **Object.keys()**
- 应该提供一个动态值key
- 示例
```javascript
v-for="item in items"
v-for="(item, index) in items"
v-for="item of items"
v-for="value in object"
v-for="(value, key) in object"
v-for="(value, key, index) in object"
```
- 关于数组修改的监听
    - 可以监听到通过方法改变数组本身的API
    - 无法监听到用索引直接修改，可以用 
    ```javascript
    Vue.set(vm.items, indexOfItem, newValue) 
    ```
    ```javascript
    vm.items.splice(indexOfItem, 1, newValue)
    ```
- 关于对象的检测
    - Vue不能检测对象属性的添加和删除，对于已经创建的实例，只能用过 **Vue.set(object, key, value)** 来进行对象的响应式属性添加。**vm.$set** 同理
    - 使用 **Object.assign** 时应创建一个新对象
    - 显示过滤或者排序结果时可以创建一个 **计算属性** 
- v-for可以取整数，表示重复渲染模板n次
  ` v-for="n in 10">`

## 事件处理
- **v-on**
    - 监听DOM事件并触发时运行一些js代码
    - 可以选择一个事件处理方法
    - 可以直接内联到js语句中调用方法，可以传入特殊变量 **$event** 用来访问原生DMO事件
    - 事件修饰符，修饰符可以串联
        - ==**.stop**== 等效于 **event.stopPropagation()** 停止冒泡
        - **==.prevent==** 等效于 **event.preventDefault()** 阻止默认事件
        - **==.capture==** 使用事件捕获模式
        - **==.self==** 当在 **event.target** 是当前元素自身时触发处理函数
        - **==.once==** 触发一次
        - **==.passive==** 提升移动端的性能，不会阻止浏览器默认行为
    - 按键别名

## 表单输入绑定
- 基础用法  **v-model** 数据的双向绑定
- 修饰符
    - **==.lazy==** 在change时触发同步
    - **==.number==** 将用户的输入值转换为数值类型
    - **==.trim==** 自动过滤用户输入的首尾空白字符

## 组件基础
- 组件声明方式
```javascript
Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  props: ['title'],
  template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
})
```
- 引用的任意组件都将创建一个相关的新实例，并且组件的 **data** 必须是一个函数
- 全局注册和局部注册
- 通过**Prop**向子组件传递数据，调用的时候用**v-bind**，在组件的**props**捕获
- 通过实践向父级组件发送消息,使用 **$emit** 方法并传入事件的名字，需要在父级组件监听这个事件，可以添加第二个参数来传参，父级用 **$event** 捕获，如果为方法的话直接可以通过形参获取 
- 插槽 **solt** 向组件传递内容
- 动态组件 可以通过 Vue 的 **component** 元素加一个特殊的 **is** 特性
```HTML
<!-- 组件会在 `currentTabComponent` 改变时改变 -->
<component v-bind:is="currentTabComponent"></component>
```

## 组建注册
- 名称推荐用横杠链接
- 全局注册，可以用在任何新创建的 Vue 根实例的模板中
- 局部注册 
- 模块

## Prop
- 在DOM模板中引用 **props** 属性时只能使用短横线分割命名法
- Prop类型 ，字符串数组、对象形式，值为其类型
- 静态和动态Prop，使用v-bind为动态，不适用则为静态
- 单项数据流 子组件不能直接修改父级附件状态，对于引用数据类型，子组件中改变会影响父组件的状态
- prop验证 
    - 单个类型
    - 多个类型  数组
    - 必填字符串 required
    - 默认值 default
    - 自定义验证函数

## 自定义事件
- .native
- .sync

## 插槽
- 具名插槽  **<slot>** 元素有一个特殊的特性：**name** 。这个特性可以用来定义额外的插槽，在向具名插槽提供内容的时候，我们可以在一个父组件的    **<template>** 元素上使用 slot 特性，也可以直接用在普通元素上。   
- 插槽默认内容     
- 作用域插槽  

## 动态组件和异步组件
- **v-bind:is** 特性，不会缓存，切换组件会创建一个新实例
- **keep-alive**  要求被切换到的组件都有自己的名字，可以将该组件的状态保存
- 异步组件 
 
## 访问元素和组件
- 尽量不要去操作另外一个组件实例内部或者手动操作DOM元素
- 访问根实例 **this.$root** 可以当作一个全局store，针对小型的项目，大型项目还是推荐vuex
- 访问父级组件实例  **this.$parent**  
- 访问子组件实例或者子元素  可以通过 **ref** 特性为该子组件赋予一个ID引用，可以直接通过 **this.$refs.idName** 调用，refs只会在组建渲染完成后才生效，而且不是响应式的。所以应该尽量在模板或者计算属性中访问该属性。
- 依赖注入  **provide** 和 **inject**， 提供的数据不是响应式的。
- 程序化的时间侦听器 
    - **$on(eventName,handler)**
    - **&once(eventName,handler)**
    - **$off(eventName,handler)**
- 循环引用
    - 递归组件，根据name选项，Vue.component全局注册一个组件时，这个全局的ID会自动设置为该组件的 **name** 选项。递归应该有推迟条件。
    - 组件之间的循环引用
- 模板定义的替代品 
    - 内联模板 


## 过渡和动画

## 可复用性和组合
- **mixins** 混入
- 自定义指令
    - 全局自定义指令。使用全局Api，**Vue.directice** 
    - 局部指令。 **directives:{}**
    - 实例
    ```javascript
    Vue.directive('focus', {
      // 当被绑定的元素插入到 DOM 中时……
      inserted: function (el) {
        // 聚焦元素
        el.focus()
      }
    })
    //局部指令
    directives: {
      focus: {
        // 指令的定义
        inserted: function (el) {
          el.focus()
        }
      }
    }
    ```
- 钩子函数
# 全局API
## Vue.extent()
# 特殊特性
## key
- 作用
    - 强制替换组件，重新渲染
    - 完整的触发组件的生命周期钩子
    - 触发过渡

## ref
- 作用  用来给元素或者组件注册引用信息。将会注册到父组件的 **$refs** 对象 
- 特点
    - 当使用 **v-for** 时，引用信息将会是一个数组
    - ref本身是作为渲染结果被创建的，所以在初始渲染的时候不能访问，**$refs** 不是响应式的

## slot
- 作用 用于具名插槽中，需要和模板中
# 实例属性

## $data
- 类型： Object | Function
- 限制： 组件的定义只接受function，如果为纯粹的对象的话，则该组件所有的实例指向同一个引用。
- 实例创建后，可以通过 **vm.$data** 访问原始对象，并且Vue实例也代理了data对象上所有的属性，**不代理以 ==_== 和 ==$== 开头的属性**，但是可以通过 **vm.$data._property** 访问。

## $props
- 类型： Array<string> | Object
- 详细： 用于接收来自父组件的数据，可以为数组或者对象，而且对象允许配置高级选项，如类型检测、自定义校验和默认值设置。

## $el
- 类型：HTMLElement
- 限制：只读
- 详细：Vue实例使用的根DOM元素

## $root
- 类型： Vue instance
- 限制：只读
- 详细：根元素

## $parent
- 类型： Vue instance
- 限制：只读
- 详细：父实例

## $children
- 类型： Array<Vue instance>
- 限制：只读
- 详细：当前实例的直接子组件，不保证顺序，也不是响应式的。

## $slots
- 类型： { [name: string]: ?Array<VNode> }
- 限制：只读
- 详细：访问插槽分发的内容，每个具名插槽具有其相应的属性。 **default** 包括了所有没有被包含在具名插槽中的节点。**常常用来和render函数配合使用** 
- 示例
```html
<blog-post>
  <h1 slot="header">
    About Me
  </h1>

  <p>Here's some page content, which will be included in vm.$slots.default, because it's not inside a named slot.</p>

  <p slot="footer">
    Copyright 2016 Evan You
  </p>

  <p>If I have some content down here, it will also be included in vm.$slots.default.</p>.
</blog-post>
```
```javascript
Vue.component('blog-post', {
  render: function (createElement) {
    var header = this.$slots.header
    var body   = this.$slots.default
    var footer = this.$slots.footer
    return createElement('div', [
      createElement('header', header),
      createElement('main', body),
      createElement('footer', footer)
    ])
  }
})
```

## $scopedSlots ？
- 类型： **{ [name: string]: props => VNode | Array<VNode> }**
- 限制：只读
- 详细：访问作用域插槽

## $refs
- 类型： Object
- 限制：只读
- 详细：一个对象，持有注册过 **ref** 特性的所有DOM元素和组件实例。

## $attrs ？
- 类型： { [key: string]: string }
- 限制：只读
- 详细：包含了父作用域中不作为prop被识别的特性集合（class和style除外）

## listeners ？

# 实例方法
## vm.$watch() ？
- 参数：
- 用法：观察Vue实例变化的一个表达式或计算属性函数。回调函数得到的参数为新值和旧值

## vm.$set()
- 参数：
    - target {Object | Array}
    - key {string | number}
    - value {any}
- 返回值：设置的value
- 用法：全局**Vue.set()**的别名，向响应式对象中添加一个属性，并确保这个新属性同样是响应式的，且触发视图更新。
- 限制：对象不能是Vue实例，或者Vue实例的根数据对象。

## vm.$delete()
- 参数：
    - target {Object | Array}
    - key {string | number}
- 用法： 全局**Vue.delete()**的别名。删除对象的属性。如果对象是响应式的，确保删除能触发更新视图。

## vm.$on()
- 参数：
    - event {string | Array<string>}
    - callback Function
- 用法：添加当前实例上的自定义事件，可以由 **$emit** 触发

## vm.$once()
和on用法一样，但是只会触发一次
## vm.$off()
取消监听事件
## vm.$emit()
用来触发父组件的监听，附加参数都会传给监听器回调。
## vm.$nextTick()
将回调延迟到下次 DOM 更新循环之后执行。在修改数据之后立即使用它，然后等待 DOM 更新。它跟全局方法 Vue.nextTick 一样，不同的是回调的 this 自动绑定到调用它的实例上。
## vm.$destroy()
完全销毁一个实例。清理它与其它实例的连接，解绑它的全部指令及事件监听器。

    
