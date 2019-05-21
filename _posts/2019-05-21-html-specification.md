---
layout: post
title: HTML 规范
subtitle:
date: 2019-05-21
tags: ['note']
---
# HTML 规范
# HTML 部分
---
## * 基础
### 1. THML
* 块级元素
* 行级元素

### 2. 规则
`内联元素可以嵌套内联元素，块级元素可以嵌套部分块级元素也能嵌套内联元素，但是内联元素不能嵌套块级元素,块级元素为block,内联元素为inline,拥有“inline”特性的同时又拥有“block”的特性称为replace元素。`

### 3. 开发中遇到的问题
`在<p>元素中嵌套了两个<span>元素，它们按照浏览器的渲染正常显示。但当在<p>元素中嵌套两个 <div>元素时，我们会发现，<div>分别在一行显示，而此时"p元素的开始"与"p元素的结束"也在不同的一行显示，与我们想要的（这两段文字在一行显示）相反。它们也均在不同行显示。这是什么原因呢？`
### 4. 原理
> 原来,在<p>元素中是不能嵌套<div>元素的，在<p>标签还没结束时，遇到下一个块级元素就会自动结束
>
> 内联元素的img 与 input比较特殊，他们有内联元素没有的宽高，w3c定义为replace元素，将元素设置为display:inline-block，模拟的就是replace元素。
> p元素中是不能嵌套块级元素的。


* 块级元素：元素的 display 为 block、list-item、table 时，该元素将成为块级元素。

    一个块级元素会被格式化成一个 **块**，默认按照垂直方向依次排列。
    > 这就是为什么块级元素表现为一个水平流上只能单独显示一个元素，多个块级元素则换行显示。

* 行内级元素：display 为 inline、inline-block、inline-table 的元素称为行内级元素。

    一个行内级元素不会被格式化成一个 **块**。

### 5. HTML4/XHTML的嵌套规则:
(1)内联元素不能嵌套块元素
(2)<p>元素和<h1~6>元素不能嵌套块元素。
关于块级元素和内联元素。
块级元素一般是都是从新的行开始,内联元素在一行内显示。我们可以通过css的display的属性来改变元素是内联元素或者是块级元素,当然这是css对于元素的分类。显然用"display"的属性值来对html元素进行分类是不严谨的。

### 6. HTML5的元素嵌套规则:
> 

W3C在最新的HTML5规范中对元素的分类方式:
元素的分类不再是块元素或内联元素这样来分类（其实从来就没有这样分），而是按照如下分类来分：Flow（流式元素）、Heading（标题元素）、Sectioning（章节元素）、Phrasing（段落元素）、Embedded（嵌入元素）、Interactive（交互元素）、Metadata（元数据元素）。

> Flow（流式元素）
> a， abbr， address， area（如果它是map元素的后裔）， article， aside， audio， b， bdi， bdo， 
blockquote， br， button， canvas， cite， code， command， datalist， del， details， dfn， div， 
dl，em， embed， fieldset， figure， footer， form， h1， h2， h3， h4， h5， h6， header， hgroup， 
hr， i， iframe， img， input， ins， kbd， keygen， label， map， mark， math， menu， meter，nav， 
noscript， object， ol， output， p， pre， progress， q， ruby， s， samp， script， section， select， 
small， span， strong， style（如果该元素设置了scoped属性）， sub， sup， svg， table，textarea， time， 
u， ul， var， video， wbr， text
> Heading（标题元素）:
> h1， h2， h3， h4， h5， h6， hgroup
> Sectioning（章节元素）:
> article， aside， nav， section
> Phrasing（段落元素）:
> a（如果其只包含段落式元素）， abbr， area（如果它是map元素的后裔）， audio， b， bdi， 
bdo， br， button， canvas， cite， code， command， datalist， del（如果其只包含段落式元素）， 
dfn， em， embed， i，iframe， img， input， ins（如果其只包含段落式元素）， kbd， keygen， label， 
map（如果其只包含段落式元素）， mark， math， meter， noscript， object， output， progress， q， 
ruby， s， samp， script，select， small， span， strong， sub， sup， svg， textarea，
time， u， var， video， wbr， text
> Embedded（嵌入元素）:
> audio， canvas， embed， iframe， img， math， object， svg， video
> Interactive（交互元素）:
> a， audio（如果设置了controls属性）， button， details， embed， iframe， img（如果设置了usemap属性）， 
input（如果type属性不为hidden状态）， keygen， label， menu（如果type属性为toolbar状态），
object（如果设置了usemap属性）， select， textarea， video（如果设置了controls属性）
> Metadata（元数据元素）:
> base，command，link，meta，noscript，script，style，title

### 7. 各分类会有交叉或重叠的现象，这说明在html5中，元素可能属于上述所有分类中的一个或多个

通过上面的示例我们发现在<p>元素里嵌套<div>元素或者<a>元素里<a>元素会导致所有的浏览器都解析错误，这其实是W3C规范的严格嵌套约束，严格嵌套约束要求必须去遵守，不然就会导致所有浏览器的解析错误。
严格嵌套约束规则:
（1）.a元素里不可以嵌套交互式元素(<a>、<button>、<select>等)。
（2）.<p>里面不可以嵌套<div>、<h1>~<h6>、<p>、<ul>/<ol>/<li>、<dl>/<dt>/<dd>、<form>等。
  每个元素基本都有自己的嵌套规则（即父元素可以是什么，子元素可以是什么），除了严格嵌套约束之外的一些规则就是语义嵌套约束，对于语义嵌套约束，如果不遵守，页面可能正常，但也可能解析错误，尽量要遵守，不过也要遵循最佳实践，比如导航菜单经常就会有<ul>元素作为<li>的子元素。
### 8. http://www.softwhy.com/article-33-1.html
盒子有多种类型：

* 块级盒子： block-level box

  由块级元素生成。一个块级元素至少会生成一个块级盒子（主块级盒子 principal block-level box），但也有可能生成多个（例如列表项元素，会生成额外的盒子来放置项目符号，学名“标记盒子” marker box）。

  * 每个块级盒子都会参与 `块格式化上下文` 的创建
  * 主块级盒子包含由后代元素生成的盒子以及内容，同时它也会参与定位方案。

* 块容器盒子：block container box 或 block containing box

  要么只包含其它块级盒子，要么只包含行内盒子并同时创建一个行内格式化上下文（inline formatting context）。

  > 为什么要再弄个 块容器盒子 出来呢：
  > 
  > 这里搬出张鑫旭大佬的解释：
 > 张鑫旭大佬在《CSS世界》中提到：每个元素都有两个盒子：**容器盒子+外在盒子**
 >
 > 外在盒子：确定元素是可以一行显示还是只能换行显示
 >
 > 容器盒子：负责元素宽高、内容呈现等
 * display:block; 块级盒子+块级盒子
 * display:inline-block; 内联盒子+块级盒子
 * display:table; 块级盒子+表格盒子

* 块盒子：block box，如果一个块级盒子同时也是一个块容器盒子，则称其为块盒子。

* 匿名块盒子：Anonymous block box
   块包含盒子可能只包含行内级盒子，也可能只包含块级盒子，但通常的文档都会同时包含两者，在这种情况下，就会在相邻的行内级盒子外创建匿名块盒子。

   另一种会创建匿名块盒子的情况是一个行内盒子中包含一或多个块盒子。此时，包含块盒子的盒子会拆分为两个行内盒子，分别位于块盒子的前面和后面。块盒子前面的所有行内盒子会被一个匿名块盒子包裹，块盒子后面的行内盒子也是一样。因此，块盒子将成为这两个匿名块盒子的兄弟盒子。如果有多个块盒子，而它们中间又没有行内元素，则会在这些盒子的前面和后面创建两个匿名块盒子。
   
   CSS选择器不能作用于匿名盒子(anonymous boxes)，所以它不能被样式表赋予样式。也就是说，此时所有可继承的 CSS 属性值都为 inherit ，而所有不可继承的 CSS 属性值都为 initial。

> 块容器盒子侧重于当前盒子作为“容器”的这一角色，它不参与当前块的布局和定位，它所描述的仅仅是当前盒子与其后代之间的关系。换句话说，块容器盒子主要用于确定其子元素的定位、布局等。有些块级盒子并不是块容器盒子，比如表格；而有些块容器盒子也不是块级盒子，比如非替换行内块和非替换表格单元格。

> 我个人目前的理解是张鑫旭大佬可能只是为了通俗解释，实际情况是只生成了 块级盒子或者块容器盒子或块盒子，用哪种盒子主要看是否作为容器角色和是否参与布局定位。
> 
> 但感觉还是有些问题（主要疑惑是：块盒子、块容器盒子是和块级盒子同级的概念还是块级盒子的特例，一个元素是不是会同时生成这些盒子），有空抠一下规范：

 ---

* 行内级盒子：inline-level box

   如果行内级元素生成的盒子参与行内格式化上下文的创建，则该盒子为一个行内级盒子。

* 行内盒子：inline box

   如果一个行内级盒子的内容不参与行内格式化上下文的创建，则称其为行内盒子。与块盒子类似，行内盒子也分为具名行内盒子和匿名行内盒子（anonymous inline box）两种。

   > 比如所有具有 display:inline 样式的非替换盒子，可以被拆分为多个盒子。

* 原子行内级盒子：atomic inline-level box，不参与行内格式化上下文创建的行内级盒子。**原子行内级盒子的内容不会拆分成多行显示**。

* 匿名行内盒子

   一种常见的情况是CSS引擎会自动为直接包含在块盒子中的文本创建一个行内格式化上下文，在这种情况下，这些文本会被一个足够大的匿名行内盒子所包含。但是如果仅包含空格则有可能不会生成匿名行内盒子，因为空格有可能会由于 white-space 的设置而被移除，从而导致最终的实际内容为空。
  
   ---

* 行盒子

   行盒子由行内格式化上下文创建，用来显示一行文本。在块盒子内部，行盒子总是占据整个块盒子的宽度。当有浮动元素时，行盒子会从向左浮动的元素的右边缘延伸到向右浮动的元素的左边缘。

  > Each line box starts with a zero-width inline box with the element’s font and line height properties. We call that imaginary box a “strut”.


## * 块格式化上下文（Block Formatting Context，BFC）
[https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)

是Web页面的可视化CSS渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。

块格式化上下文包含创建它的元素内部的所有内容.

块格式化上下文对浮动定位（参见 float）与清除浮动（参见 clear）都很重要。浮动定位和清除浮动时只会应用于同一个BFC内的元素。浮动不会影响其它BFC中元素的布局，而清除浮动只能清除同一BFC中在它前面的元素的浮动。外边距折叠（Margin collapsing）也只会发生在属于同一BFC的块级元素之间。


## * box-sizing
`box-sizing`: >=IE8，指定 width/height 作用于哪个区域

`box-sizing` 默认为 `content-box`，内容区域的大小可明确地通过 width、min-width、max-width、height、min-height，和 max-height 控制。

支持情况：
```
.box1 { box-sizing: content-box; } /* 默认值 */
.box2 { box-sizing: padding-box; } /* Firefox曾经支持*/
.box3 { box-sizing: border-box; } /* 全线支持 */
.box4 { box-sizing: margin-box; } /* 从未支持过 */
```

## * 确定包含块
确定一个元素的包含块的过程完全依赖于这个元素的 position 属性：

* 如果 position 属性为 static 或 relative ，包含块就是由它的最近的祖先块元素（比如说inline-block, block 或 list-item元素）或格式化上下文(比如说 a table container, flex container, grid container, or the block container itself)的内容区的边缘组成的。

* 如果 position 属性为 absolute ，包含块就是由它的最近的 position 的值不是 static （也就是值为fixed, absolute, relative 或 sticky）的祖先元素的内边距区的边缘组成。

* 如果 position 属性是 fixed，包含块就是由 viewport (in the case of continuous media) 或是组成的。

* 如果 position 属性是 absolute 或 fixed，包含块也可能是由满足以下条件的最近父级元素的内边距区的边缘组成的：
 * A transform or perspective value other than none
 *A will-change value of transform or perspective
A filter value other than none or a will-change value of filter (only works on Firefox).
## * float
在浮动定位中，浮动盒子会浮动到当前行的开始或尾部位置。这会导致普通流中的文本及其他内容会“流”到浮动盒子的边缘处，除非元素(块级元素)通过 clear 清除了前面的浮动。

一个盒子的 float 值不为 none，并且其 position 为 static 或 relative 时，该盒子为浮动定位。如果将 float 设置为 left，浮动盒子会定位到当前行盒子的开始位置（左侧），如果设置为 right，浮动盒子会定位到当前行盒子的尾部位置（右侧）。不管是左浮动还是右浮动，行盒子都会伸缩以适应浮动盒子的大小。

清除浮动
```
.clear::after {
  content: ' ';
  display: table | block | list-item; 只要是 块级元素 即可
  list-style: none;  针对 list-item，IE <=11不支持
  clear: both;
}
```