# CSS

❓ 介绍一下 position

🤔&emsp;position 属性用于指定一个元素在文档中的定位方式，通过top、right、bottom、left属性决定该元素的最终位置。
它的值可以是static、relative、absolute、fixed、sticky、inherit、initial

* static：正常布局行为，元素在文档流中，此时top、right、bottom、left和z-index无效
* relative（相对定位）：元素在文档流中，在不改变文档流的前提下可以调整四个方位的位置属性
* absolute（绝对定位）：元素脱离文档流，相对于最近的非static定位的父级元素偏移
* fixed（固定定位）：元素脱离文档流，一般情况下相对于屏幕适口（viewport）偏移。
当有父级元素的transform、perspective、filter属性非none时，相对于该父级元素偏移
* sticky（粘性布局）：元素在文档流中，相对于最近的滚动父级元素进行偏移

---

❓ 介绍一下行内元素/块状元素

🤔&emsp;行内元素，规范称为内联级元素（inline-level elements）。从定义来看 inline、inline-block、inline-table 等都是；从表现来看，就是可以和文字在一行显示

块状元素，规范称为块级元素（block-level elements）。基本特征是一个水平流只能单独显示一个元素，多个块级元素则换行显示。

---

⭐ flex

❓ 介绍一下 flex 布局

🤔&emsp;flex 是 flexible box 的缩写，意为弹性布局。块级元素和内联级元素（inline-flex）都可以使用。  
使用 flex 布局的元素成为容器（flex container），容器的子元素成为子项（flex item）。  
flex 布局的容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。  
容器属性有：
* flex-direction: 决定主轴的方向。默认值为 `row`。可选值有 `row-reverse`、`column` 和 `column-reverse`
* flex-wrap: 决定子项是否换行排列。默认值为 `nowrap`。可选值有 `wrap` 和 `wrap-reverse`（换行，第一行在下方）
* flex-flow: flex-direction 和 flex-wrap 的缩写。默认值为 `row nowrap`。
* justify-content: 决定子项在主轴的对齐方式。默认值为 `flex-start`。可选值有：
  * `flex-end`（右对齐，实际上是主轴的结尾对齐）
  * `center`
  * `space-between`（子项间距相等）
  * `space-around`（子项间距相等，首尾子项距离容器是子项间间距的一半，即每个子项的左右间距一样）
  * `space-evenly`（子项间距相等，包括首尾子项距离容器的距离）

![space-between](https://saas-base.cdnjtzy.com/sns/20210928/d7dcb46652b64808a761f5ebdb25a0fa.png)

![space-around](https://saas-base.cdnjtzy.com/sns/20210928/4b508f69429178eeb3cddbf988c1fbd6.png)

![space-evenly](https://saas-base.cdnjtzy.com/sns/20210928/2df4cd15037378798558ed8901981324.png)

* align-items: 决定子项在交叉轴的对齐方式。默认值为 `stretch`（占据容器的整个高度）。可选值有 `flex-start`、`flex-end`、`center` 和 `baseline`
* align-content: 决定子项在多根交叉轴（flex-wrap 不为 `nowrap`）情况下的对齐方式。默认值为 `stretch`。可选值和 justify-content 一致，只多了 `stretch`

子项的属性有：
* order: 决定子项的排列顺序，从小到大。默认值为 `0`。支持正负整数
* flex-grow: 决定子项的放大比例。默认值为 `0`。不支持负值，即使有多余空间也不会放大。若所有子项值都为 1，则均分剩余空间；若有一个子项为 2，其分到剩余空间的比例是其余值为 1 的子项的两倍
* flex-shrink: 决定子项的缩小比例。默认值为 `1`。不支持负值，没有空间子项会缩小。当值为 0 时，即使空间不足时也不缩小
* flex-basis: 决定子项在分配剩余空间前占据主轴的空间大小。默认值为 `auto`
* flex: flex-grow、flex-shrink 和 flex-basis 的缩写。默认值为 `0 1 auto`
* align-self: 定义子项本身在交叉轴的对齐方式，可覆盖 align-items。默认值为 `auto`。可选值和 align-items 一致，多了 `auto`，等同于 `stretch`

❓ 如何使用 flex 实现九宫格布局

🤔&emsp;通过设置容器的 justify-content、align-items 属性和子项的 align-self 属性。设置子项的情况是九宫格没有满九个子项（如绘制骰子的点数等）

❓ flex: 1 指的是什么，flex 属性默认值是什么

🤔&emsp;`flex: 1` 即 `flex: 1 1 0%`，适合等分布局。flex 默认值是 `0 1 auto`。比较常见的还有 `flex: none` 即 `flex: 0 0 auto`，适用于不换行的内容固定或者较少的小控件元素上，如按钮

❓ 分别介绍一下 flex-shrink 和 flex-basis 属性

🤔&emsp;flex-shrink 决定子项的缩小比例。默认值为 `1`。不支持负值，没有空间子项会缩小。当值为 0 时，即使空间不足时也不缩小；flex-basis 决定子项在分配剩余空间前占据主轴的空间大小。默认值为 `auto`

❓ 介绍一下 grid 布局

---

⭐ 自适应

❓ 移动端 1px 问题

🤔&emsp;推荐使用方法：

* viewport + rem + media dpr（device pixel ratio）  
缺点：通过 JS 对文档进行 viewport 修改

* 伪元素 + transform scale + media dpr

* svg 实现

能解决的方法：

* 0.5px + media dpr  
缺点：安卓待兼容；支持 ios8+（无所谓）

* border-image  
缺点：更换麻烦

* box-shadow  
缺点：边框有阴影，颜色浅；Safari 不支持 1px 以下

❓ 解释一下 rem 方案和 vw 方案，分别有什么优点和缺点

❓ rem 方案的 font-size 是挂在哪的

❓ rem 方案的移动端字体是怎么处理的

---

⭐ 重绘回流

❓ 介绍一下重绘和回流

❓ 如何避免重绘和回流

---

❓ 居中/常见布局

---

❓ 层叠上下文，说一下 z-index

---

❓ 介绍一下 SASS/LESS
