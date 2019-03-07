
# HTML学习记录
## 文字标签集合
**\<p>** &nbsp;&nbsp;&nbsp;段落表示

**\<h>**&nbsp;&nbsp;&nbsp;h1 - h7

**\<em> \<i>** &nbsp;&nbsp;&nbsp;强调，倾斜，类似于
**font-style:** italic/oblique

**\<strong> \<b>** 强调，加粗 类似于 **font-weight:**
bold/bolder/lighter

**\<u> \<del>**&nbsp;&nbsp;&nbsp;添加下划线，删除线。应避免，使用样式来表达

**\<big> \<small>**&nbsp;&nbsp;&nbsp;大号和小号字

**\<sub> \<sup>**&nbsp;&nbsp;&nbsp;定义下标和上标字

**\<abbr> \<acronym>**&nbsp;&nbsp;&nbsp;定义缩略语 光标移动到此可以出现提示，title属性。首字母缩写

**\<br>** 换行

**\<hr>** 段落之间的横线分割符

**\<pre>** 保留文本格式

**\<address>** 定义包含联系信息的一个章节。
## 超链接
**\<a href=“网址/相对路径”>**&nbsp;&nbsp;&nbsp;超链接，**title**属性可以添加鼠标悬停标识，**target="_blank"**
属性会打开新页面，可以包含块级元素，挑转到当前页面的name属性所在标签的位置

## 图片
**\<img>**&nbsp;&nbsp;&nbsp; 图像标签，**src属性**为图片资源地址，**alt属性**为加载图像失败的替换文本，**align属性**设置对齐，浮动，bottom为默认对齐方式，height和width属性

## 表格

**\<ul> \<li> \<ol>** &nbsp;&nbsp;&nbsp;有序列表和无序列表，可以嵌套混合使用，ul的type属性可以改变无序的序号标志，disc、circle、square

**\<table>\<tr>\<td>\<th>**&nbsp;&nbsp;&nbsp;表格，border属性，表格边框，其中
**\<th>** 会默认加粗文本。**\<caption>** 表格标题，**\<cellpaddin>** 单元格边距，
**\<cellspacing>** 单元格间距，
**\<align>** 单元格文本对齐方式

**\<dl>\<dt>\<dd>** 定义列表

**\<div>\<span>** 无含义块级属性和无含义内联元素

## HTML表单

**\<form>** 表单标签
- 可以给元素添加伪类&nbsp;&nbsp;**:valid** 和 **:invalid** 来判断输入是否通过验证
- 该标签包括所有全局属性。
- **accept-charset** 规定服务器用哪种字符集处理表单数据。
- **action** 处理这个form的url，可以被
**\<button>** 或者 **\<input>** 的**formaction** 属性重载
- **method**
   - **post**，表单数据会包含在表单体内然后发送给服务器.
   - **get** 表单数据会附加在 action 属性的URI中，并以 '?' 作为分隔符, 然后这样得到的 URI 再发送给服务器.
- **name** form的标识

**\<label>** 提示标签
- **\<for>** 标记着form相关元素的ID
**\<fieldset>** 表示控件组，默认带一个黑边框样式
**\<legend>** 表示控件组标题
**\<input>** 输入控件
- **type**属性
   - **button** **onclick** 指向点击处理事件，**value** 表示按钮内容
   - **checkbox** 复选框，必须使用value属性
   - **color** 拾色器
   - **date** 年月日选择器
   - **month** 年月选择器
   - **email** 可以用
   **:valid**和
   **:invalid**进行检测进行样式修改
   - **file** 进行文件选择
   - **hidden** 不显示页面控件，但会将其值提交到服务器
   - **number** 输入浮点数，仅输入数字有效
   - **password** 输入密码 将输入的明文变得不可见，并且可以使用**maxlength** 指定最大长度
   - **radio** 单选按钮，指定相同的**name**属性以及设置**value**属性，可以设置缺省选择 **checked**
   `
   <input type="radio" name="sex" value="female" checked>Female
   <input type="radio" name="sex" value="male">male
   `
   - **range** 滑动选择器，默认设置了属性 
     - min：0
     - max：100 
     - step：1 
     - value：min + (max-min)/2，或当 max 小于 min 时使用 min

   - **search** 用于输入搜索字符串的单行文本，换行输入文本会被清除，并且控件带有一个删除按钮
   - **reset** 用于将表单所有内容设置为缺省值
   - **tel** ，用于输入电话号码，可以使用**pattern**和**maxlength**进行约束 ，可以用
   **:valid**和
   **:invalid**进行检测进行样式修改

   - **url** 用于输入url，换行会自动被移除，可以使用**pattern**和**maxlength**进行约束 ，可以用
   **:valid**和   **:invalid**进行检测进行样式修改

   - **week** 选择某年的第多少周
- **autofocus** 指定的表单控件在页面加载时自动获取焦点。
- **checked** 在**radio和checkbox**中可以指定默认选择
- **disabled** 表示控件不可用，click事件也将不会被分发，提交表单时也不会被提交
- **height** 如果**type**属性的值是**image**，这个属性定义了按钮图片的高度
- **max** 定义了这个输入的最大值(数字或者日期时间)，且不得小于其最小值(**min**属性)。
- **min** 相对**max**
- **maxlength** 定义了输入的最多字符数
- **multiple** 指示用户可以输入多个值，仅在**type**属性为**email或file**
- **name** 控件的名称，与表单数据一起提交
- **pattern** 检查输入的正则表达式，要求**type**属性需为**text，search，tel，url，email**时，否则被忽略
- **placeholder** 提示用户输入框，提示文本不包含回车或者换行，要求**type**属性需为**text，search，tel，url，email**时，否则被忽略
- **readonly** 布尔属性，表示用户无法修改控件的值
- **required** 表示提交表单必须为该元素填值，当**type**属性为**hidden，image，submit，reset，button**时不可使用，使用 **:required,:optional**伪元素来为组件添加样式。
- **size** 控件的初始大小，像素为单位。此属性仅适用于当 **type** 属性为 **text, search, tel, url, email, password**时有效。
- **src** **image**的必要属性，表示资源地址。
- **width** **image**属性的图片宽度。
- **step** 增量，任意字符串或者正浮点数。
- **value** 控件的初始值，可选属性，**type**为**radio，checkbox** 时为必选属性。
- **list** 配合\<datalist>以及\<option>标签使用
<input list="name">
<datalist id="name">
   <option value="Ezreal">
   <option value="Hana">
   <option value="Pike">
</datalist> 

**\<select>** 下拉选择框，可创建选项菜单。菜单内的选项为 **\<option>** , 可以由 **\<optgroup>** 元素分组。**selected** 属性可以使选项可以被用户预先选择。 

<select name="select">
  <option value="value1">Value 1</option> 
  <option value="value2" selected>Value 2</option>
  <option value="value3">Value 3</option>
</select>

**\<progress>** 进度条显示 
<progress value="70" max="100">70 %</progress>

**\<output>** 表示用户计算结果显示
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" name="b" value="50" /> +
    <input type="number" name="a" value="10" /> =
    <output name="result"></output>
</form>

### HTML全局属性
- **accesskey** 生成键盘快捷键
- **class** 设置元素类名
- **id** 设置元素id名，唯一
- **style** 行内样式
- **lang** 语言设置
- **title** 有关元素的额外信息
- **hidden** 隐藏属性
- **contenteditable** 可编辑，布尔类型，默认为false
- **data-\*** 设置元素所带参数，使用**getAttribute("")** 接口来获得
- **dir** 文本方向，取值有**ltr，rtl，auto**
- **draggable，daopzone** 关于元素是否可以被拖动，以及移动后的行为表示
### HTML事件属性
放到javascript中学习
## HTML5新特性
### 新的语义元素
- **布局语义**
   - **\<main>** 定义文档的主内容。
   - **\<header>** 	定义文档或节的页眉。
   - **\<nav>**  导航栏
   - **\<aside>** 定义页面内容之外的内容。
   - **\<article>** 定义文档内的文章。
   - **\<section>**
   - **\<details>** 	定义用户可查看或隐藏的详细信息。
   - **\<summary>**  代表**details**标签的标题，摘要等，在 **\<details>** 内部使用
   - **\<mark>** 黄色高亮，强调
   - **\<footer>** 定义文档
或节的页脚。
### 离线&存储
- ***window.localStorage***  存储没有截止日期的数据
- ***window.sessionStorage*** - 针对一个 session 来存储数据（当关闭浏览器标签页时数据会丢失）
### 多媒体
**\<audio>** 和 **\<video>** 元素嵌入和允许操作新的多媒体内容。

**\<source>** 

`<source src="test.mp3" type="audio/mp3">`
### 绘图canvas


