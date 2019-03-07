## DOM及其操作
### 节点关系
  - 节点类型：Node.ELEMENT_NODE(1)  元素类型  Node.TEXT_NODE(3)  文本类型
  - 每个节点都有一个childNodes属性，其中保存着一个NodeList对象，像array但不是array，动态变化
    通过访问下标，item()，来访问，将NodeList对象转化为数组：
    - Array.prototype.slice.call(nodes,0);
    - 循环push

### 选择节点
  - getElementById()
  - getElementByTagName()
  - getElementByClassName() 传入类名，返回所有同类元素
  - querySelector() 传入css选择器，返回第一个元素
  - querySelectorAll() 传入css选择器，返回一个NodeList对象
  - matchesSelector() 判断元素是否存在

### 节点属性
  - childElementCount   返回子元素的个数，不包括文本节点和注释
  - firstElementChild   返回第一个子元素
  - lastElementChild    返回最后一个子元素
  - previousElementSibling   指向前一个同辈元素
  - nextElementSibling   指向后一个同辈元素
  - children
  - classList  保存元素类名集合
    - add(value)   增加新字符串到该列表中
    - contains(value)  判断列表中是否存在
    - remove(value)  从列表中删除给定字符串
    - toggle(value)  如果列表中有，删除。如果没有，添加
  - innerHTML
  - outerHTML
  - innerText

### 操作节点
  - appendChild()   向childNodes列表的末尾添加一个节点，返回值为新增的节点
  - insertBefore()   向childNodes列表指定位置添加一个同胞节点
  - replaceChild(newNode，someNode)   替换节点和被替换节点，返回值为被替换的节点   
  - removeChild() 移除特定的节点，归文档所有，只不过没有了自己的位置
  - cloneNode()  复制某个节点，参数为布尔类型，表示是否需要深拷贝
  - normalize()  针对文本节点，删除空文本节点，合并相邻文本节点
  - insertAdjacentHTML() 
  - contains() 判断后代元素是否包含给定节点
  - setAttribute("name","value")   为元素设置相应属性

### 对象属性
  - 数据属性
    - [[Value]] 包含这个属性的数据值
    - [[Writable]]  可写  如果该值为 false，则该属性的 [[Value]] 特性 不能被改变。
    - [[Enumerable]]  可枚举  如果该值为 true，则该属性可以用 for...in 循环来枚举。
    - [[Configurable]]  可修改 如果该值为 false，则该属性不能被删除，并且 除了 [[Value]] 和 [[Writable]] 以外的特性都不能被改变。
    - 修改数据属性时只能使用 Object.defineProperty()  接受三个参数，对象，属性，数据属性枚举
  - 访问器属性
    get和set，旧的方法为：__defineGetter__("name",function() {})   __defineSetter__("name",function() {})

### js对象
  - 反射  reflection
    - hasOwnProperty("name") 不会查找原型链
    - 使用typeof来排除函数
  -  for in遍历对象所有属性  乱序
  - delete删除对象的属性

### 函数
  - 函数对象 函数对象连接到function.prototype(连接在object.prototype)，拥有一个prototype属性，该属性拥有一个constructor的属性
  - 闭包  返回一个或多个子函数，更长的生命周期且内部变量私有
  - 函数调用   不同的调用方式初始化的this不同
    - 方法调用 this指向拥有该方法的对象
    - 函数调用  this为全局对象，内部函数不能范围外部函数的this以及arguments
    - 构造器调用  当作构造函数来使用,通常用大写开始命名
    - apply调用 call，bind
  - 参数
    arguments参数数组
  - 返回值 没有指定则为undefined，new的时候返回新this
  - 扩充类型功能 Number.prototype.test = function () {}
  - 回调
  - 模块 提供接口但隐藏状态与实现
  - 级联
  - 柯里化 把函数和参数结合，产生一个新的函数
  - 记忆


  - ES6
    - 默认参数
    - 默认参数对arguments对象的影响，严格模式下参数的改变会影响arguments，带默认参数arguments行为会像严格模式一样，默认参数值可以用表达式获取
    - 不定参数 每个函数最多只能有一个不定参数而且必须放到所有参数末尾
    - 展开运算符

### 继承
  - var newObject = Object.create(object)，将object绑定到newObject的原型链上

### 数组
  - 将下标转成字符串并作为其属性
  - 方法
    - push 末尾添加元素
    - pop 移除最后一个并返回，如果为empty则返回undefined
    - shift 移除第一个元素，如果为empty则返回undefined
    - unshift 从开始插入一个元素
    - sort 排序，默认对按字符串排序
    - foreach
    - map
    - indexOf
    - lastIndexOf
    - splice 移除数组中一个或者多个元素，并用新的元素替换，改变原数组
    - slice 对数组的一段进行浅复制，不改变原数组
    - concat 产生一个新数组，包含一份array的浅复制，不修改原数组
    - find
    - reduce
    - reduceRight
    - filter
    - some
    - every
    - fill
    - includes
    - reverse 反转array里的数组，并且将原数组修改
    - join 将数组添加分隔符并且构造成一个字符串
    - entires
    - keys

### 方法
  - 函数
    - bind
    - apply
    - call
  - Number
    - toExponential 将number转成一个指数形式的字符串，可选参数表示小数点个数
    - toFixed 转换成一个十进制的字符串，可选参数表示小数点个数
    - toString 转成字符串 可选参数表示进制 
  - Object
    - constructor 返回创建实例对象的 Object 构造函数的引用 
    - hasOwnProperty 判断该对象是否包含属于自己的某个属性
    - defineProperty 修改属性的属性特性
    - defineProperties 定义多个属性及其特性
    - getOvnPropertyDescriptor 取得给定属性的特性 参数为 (对象，属性名)
    - Object.assign() 用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。
    - Object.create() 创建一个新对象，使用现有的对象来提供新创建的对象的__proto__。 
    - Object.entries() 返回一个给定对象自身可枚举属性的键值对数组，其排列与使用 for...in 循环遍历该对象时返回的顺序一致（区别在于 for-in 循环也枚举原型链中的属性）。
    - Object.freeze() 可以冻结一个对象，冻结指的是不能向这个对象添加新的属性，不能修改其已有属性的值，不能删除已有属性，以及不能修改该对象已有属性的可枚举性、可配置性、可写性。该方法返回被冻结的对象。(浅冻结)
  - String
    - fromCharCode(65)  将ASCII码转成字符串
    - charAt(2)  获取字符串指定索引处的值
    - charCodeAt(2)  返回字符串指定索引处的值的ASCII
    - concat('abc','def') 连接字符串 不改变原有字符串 建议用 + 来代替
    - endWith('end',5)  判断从指定索引处开始给定字符串是否是目标字符串的结尾，索引默认值为0
    - startsWith('start',5)  判断从指定索引处开始给定字符串是否是目标字符串的开始，索引默认值为0
    - includes('hello',4)  判断给定字符串从目标索引处开始是否为目标字符串的子串
    - indexOf('hello',4)和lastIndexOf('test',5)   返回给定字符串从目标字符串的指定索引处第一次出现和最后一次出现的索引
    - match(Regexp) 
    - padEnd(10,'hello')  用指定字符串填充目标字符串直到目标字符串长度为给定值，在结尾添加
    - padStart(10,'hello')  用指定字符串填充目标字符串到指定长度，从开始添加
    - repeat(3)  构造并返回一个新字符串，该字符串包含被连接在一起的指定数量的字符串的副本。
    - replace(old,new)  用给定的新字符串替换目标字符串中给定的原字符串，
    - slice(start,end) 提取一个字符串的一部分，并返回一新的字符串。索引可以为负值
    - split(' ')  将目标字符串用给定字符分割成数组
    - substring()
    - toLowerCase() toUpperCase() 将目标字符串转成大写或者小写 
    - trim() trimRight() trimLeft()从字符串两端开始删除空字符

### 事件
  - 捕获和冒泡
    - 事件捕获  事件由最上层沿dom树依次向下传递直到事件的实际目标
    - 冒泡  事件由实际目标元素向外传递知道document
  - 先捕获再到实际目标元素再冒泡
  - DOM0级事件处理程序
    - 先获取到目标元素，el.onlick = function () {}
    当el.onlick = null时即清除该元素点击事件
  - DOM2级事件处理程序   可以对同一个事件添加多个处理程序，按顺序执行
    - addEventListener("事件名",回调函数,布尔值)  布尔值为true表示在捕获时处理，为false表示在冒泡时处理，默认为false
    - removeEventListener("事件名",函数名)   传入的函必须和添加时的函数指向相同，即为同一个函数
    - IE事件处理程序
      - attachEvent("事件名",回调函数)，作用域为全局作用域
      - detachEvent  传入参数应该与添加时完全相同
  - 事件对象 触发某个事件时，会产生一个event，包含许多信息，事件元素、事件类型、鼠标位置等
    - target 只读 事件的目标
    - type 只读 事件类型
    - bubbles 只读 表示事件是否冒泡 布尔类型
    - cancelable 只读 表示是否可以取消默认事件 布尔类型
    - currentTarget 表示事件处理程序正在处理事件的那个元素
    - preventDefault() 方法 只读 取消事件的默认行为，如果cancelable为true，则可以使用此方法
    - stopPropagation() 方法 只读 取消事件的进一步捕获或者冒泡，如果bubbles为true，则可以使用此方法
    - stopImmediatePropagation() 方法 只读 取消事件的进一步捕获或者冒泡，且同时阻止任何事件处理程序被调用(DOM3级事件新增)
    - eventPhase 只读 整形 表示调用事件处理程序的阶段 1、捕获 2、目标元素 3、冒泡

### JQuery
  - HTML 元素选取
    - 支持元素、Id、类、:first、:first-child、[属性]、even(偶数位置)、odd(奇数位置)
  - HTML 元素操作
    - text() 设置或返回所选元素的文本内容
    - html() 设置或返回所选元素的内容（包括 HTML 标记）
    - val() 设置或返回表单字段的值
    - attr() 获取属性值
    - append() 在被选元素的结尾插入内容
    - prepend() 在被选元素的开头插入内容
    - after() 在被选元素之后插入内容
    - before() 在被选元素之前插入内容
    - remove() 删除被选元素，可以接收参数对被删元素进行过滤
    - empty() 从被选元素中删除子元素
  - CSS 操作
    - addClass() 向被选元素添加一个或多个类
    - removeClass() 从被选元素删除一个或多个类
    - toggleClass() 对被选元素进行添加/删除类的切换操作
    - css() 设置或返回样式属性，`$("p").css("background-color")`返回所有p元素的background-color属性值。`$("p").css("background-color","yellow");`设置元素属性值。`$("p").css({"background-color":"yellow","font-size":"200%"});`设置多个元素属性值
  - HTML 事件函数
    - click(回调) 单击
    - dbclick() 双击
    - mouseenter() 鼠标移入
    - mouseleave() 鼠标移出
    - keypress() 键盘按下
    - keydown() 键盘按下，不包含无意义的键，例如shift
    - keyup() 键盘松开
    - hover() 
    - submit() 表单提交
    - change() 表单修改
    - focus() 获得焦点
    - blur() 失去焦点
    - load() 将文件内容直接加载到指定的元素中
    - resize() 页面重置大小
    - scroll() 页面滚动
    - unload() 
    - $(document).ready() 页面加载完成
  - JavaScript 特效和动画
    - hide() 和 show() 隐藏和显示元素
    - fadeIn() fadeOut() fadeToggle() fadeTo() 渐隐渐显，fadeTo可以添加目标透明度
    - slideDown() slideUp() slideToggle() 滑动效果
    - $(selector).animate({params},speed,callback); 动画效果
    - 停止动画stop() 
    - 链式方法，按序执行
  - 尺寸集合
    - width() 元素content宽度
    - height()
    - innerWidth()  包含元素padding
    - innerHeight()
    - outerWidth() 包含元素border
    - outerHeight()
    - outerWidth(true) 包含元素margin
    - outerHeight(true) 
  - HTML DOM 遍历和修改
    - parent() 返回被选元素的直接父元素
    - parentsUntil('div') 返回被选元素介于给定元素之间的所有祖先元素
    - parents() 返回被选元素的所有祖先元素
  - AJAX
    - $.get()
    - $.getJSON()
    - $.param()
    - $.post()
    - serialize() 编码表单元素集为字符串以便提交



    - each(callback) 以每一个匹配的元素作为上下文来执行一个函数。
    - length 属性，表示对象元素个数
    - data(key,value)和removeData(name || list)   数据缓存，在元素上添加私有数据
    - jQuery.fn.extend()   扩展jquery对象   
    - jQuery.extend()   扩展jquery本身

    