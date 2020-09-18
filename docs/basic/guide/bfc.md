---
title: 格式化上下文
---

### 什么是 BFC

BFC 全称为块级格式化上下文 (Block Formatting Context) 。BFC 是 W3C CSS 2.1 规范中的一个概念，它决定了元素如何对其内容进行定位以及与其他元素的关系和相互作用，当涉及到可视化布局的时候，Block Formatting Context 提供了一个环境，HTML 元素在这个环境中按照一定规则进行布局。一个环境中的元素不会影响到其它环境中的布局。比如浮动元素会形成 BFC，浮动元素内部子元素的主要受该浮动元素影响，两个浮动元素之间是互不影响的。这里有点类似一个 BFC 就是一个独立的行政单位的意思。可以说 BFC 就是一个作用范围，把它理解成是一个独立的容器，并且这个容器里 box 的布局与这个容器外的 box 毫不相干。

### 触发 BFC 的条件

- 根元素或其它包含它的元素
- 浮动元素 (元素的 float 不是 none)
- 绝对定位元素 (元素具有 position 为 absolute 或 fixed)
- 内联块 (元素具有 display: inline-block)
- 表格单元格 (元素具有 display: table-cell，HTML 表格单元格默认属性)
- 表格标题 (元素具有 display: table-caption, HTML 表格标题默认属性)
- 具有 overflow 且值不是 visible 的块元素
- 弹性盒（flex 或 inline-flex）
- display: flow-root
- column-span: all

---

- `<html>`根元素;
- float 的值不为 none;
- overflow 的值为 auto、scroll 或 hidden;
- display 的值为 table-cell、table-caption 和 inline-block 中的任何一个;
- position 的值不为 relative 和 static。

### BFC 的约束规则

- 内部的盒会在垂直方向一个接一个排列（可以看作 BFC 中有一个的常规流）
- 处于同一个 BFC 中的元素相互影响，可能会发生外边距重叠
- 每个元素的 margin box 的左边，与容器块 border box 的左边相接触(对于从左往右的格式化，否则相反)，即使存在浮动也是如此
- BFC 就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然
- 计算 BFC 的高度时，考虑 BFC 所包含的所有元素，连浮动元素也参与计算
- 浮动盒区域不叠加到 BFC 上

### BFC 可以解决的问题

- 垂直外边距重叠问题
- 去除浮动
- 自适用两列布局（float + overflow）
