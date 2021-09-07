# CSS

❓ 介绍一下position

🤔 position 属性用于指定一个元素在文档中的定位方式，通过top、right、bottom、left属性决定该元素的最终位置。
它的值可以是static、relative、absolute、fixed、sticky、inherit、initial

* static：正常布局行为，元素在文档流中，此时top、right、bottom、left和z-index无效
* relative（相对定位）：元素在文档流中，在不改变文档流的前提下可以调整四个方位的位置属性
* absolute（绝对定位）：元素脱离文档流，相对于最近的非static定位的父级元素偏移
* fixed（固定定位）：元素脱离文档流，一般情况下相对于屏幕适口（viewport）偏移。
当有父级元素的transform、perspective、filter属性非none时，相对于该父级元素偏移
* sticky（粘性布局）：元素在文档流中，相对于最近的滚动父级元素进行偏移

---

❓ 介绍一下行内元素/块状元素

---

⭐ flex

❓ 介绍一下flex布局

❓ 如何使用flex实现九宫格布局

❓ flex:1指的是什么，flex属性默认值是什么

❓ 分别介绍一下flex-shrink和flex-basis属性

❓ 介绍一下grid布局

---

⭐ 自适应

❓ 移动端1px问题

❓ 解释一下rem方案和vw方案，分别有什么优点和缺点

❓ rem方案的font-size是挂在哪的

❓ rem方案的移动端字体是怎么处理的

---

⭐ 重绘回流

❓ 介绍一下重绘和回流

❓ 如何避免重绘和回流

---

❓ 居中/常见布局

---

❓ 层叠上下文，说一下z-index

---

❓ 介绍一下SASS/LESS
