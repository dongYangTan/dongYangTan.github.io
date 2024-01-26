<!--
 * @Date: 2024-01-16 14:36:46
 * @LastEditors: tandongyang =
 * @LastEditTime: 2024-01-26 11:11:47
 * @FilePath: /dongYangTan.github.io/docs/web/html_css/README.md
-->

## transform
transform 属性：transform 属性允许你对元素进行各种变换操作，如旋转、缩放、倾斜和扭曲等。 
* rotate(angle)：旋转元素，angle 表示旋转的角度，可以使用度数或弧度。
* scale(x, y)：缩放元素，x 和 y 分别表示水平和垂直方向的缩放比例。
* skew(x-angle, y-angle)：倾斜元素，x-angle 和 y-angle 分别表示水平和垂直方向的倾斜角度。
* translate(x, y)：平移元素，x 和 y 分别表示水平和垂直方向的平移距离。  
translate 函数：translate 函数是 transform 属性中的一个具体变换函数，用于实现元素的平移效果。它接受两个参数，表示水平和垂直方向的平移距离。  

***transform 对行内元素无效***    
***行内元素（除可替换元素比如img input内容都不是通过在标签内添加文本，而是通过某个属性）不能设置宽 高 margin上下 ,padding会生效 但对其上下的元素无影响***

## transition 过渡
transition: width 1s ease-in-out

## animation

```
@keyframes animationName {
  0% {
    /* 初始样式 */
  }
  50% {
    /* 中间样式 */
  }
  100% {
    /* 结束样式 */
  }
}
动画持续时间为3秒，时间函数为 ease-in-out，延迟时间为 1 秒，infinite 表示动画无限循环，alternate 表示在每个循环中反向播放动画。
.element {
  animation: animationName 3s ease-in-out 1s infinite alternate;
}
 
```  
动画-若存在一张10个动作的连续图，利用background-position的偏移量 并配合animation：name 1s steps(10) infinite  实现动画
> 动画 (animation) 和过渡 (transition)   

区别如下：  
1) 实现方式：动画使用 @keyframes 规则定义关键帧，并使用 animation 属性将动画应用于元素；而过渡使用 transition 属性来指定元素在不同状态之间的平滑过渡效果。
2) 操作对象：动画通常用于实现元素的复杂动态效果，可以在关键帧中定义多个样式变化；而过渡主要用于实现元素在某个状态改变时的平滑过渡，只能在两个状态之间进行简单的样式变化。
3) 触发方式：动画通常需要通过 JavaScript 或者 CSS 伪类（如 :hover）等方式来触发或控制；而过渡可以通过 CSS 伪类（如 :hover）或者添加/移除类名等方式来触发或控制。
4) 时间控制：动画可以指定动画的持续时间、时间函数、延迟时间以及是否循环等参数，可以实现更精确的时间控制；而过渡只需指定过渡的持续时间和时间函数，不支持循环和延迟。  
5) 复杂度：动画可以实现复杂的动态效果，可以定义多个关键帧和多个样式变化；而过渡相对简单，只能在两个状态之间进行平滑过渡。

## vertical-align
vertical-align的作用对象是 inline-level element，也就是内联级元素。 即： ***inline  inline-block !!!***  
vertical-align的作用其实是控制元素的垂直对齐方式，而不是绝对的解决垂直居中的方案。因为有时候当你使用它的时候，你会发现，nothing happened。而神奇的是，它附近的元素发生了改变。（以行内高的元素为准）  
```
'vertical-align'
Value:      baseline | top | middle | bottom 
Initial:    baseline

```
[vertical-align MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/vertical-align)

单独img标签，由于默认是基线对齐，下面如果有块元素，会有段空白间隙。原因：基线标准x的底部 预留超出类似j等字母超出x底部长度。解决：img转化block 或者改变img的vertical-align: 使用middle等；  
可以说基线是 'x' 字母的底部。但需要注意的是，基线并不是严格定义为 'x' 字母的底部，而是一个相对的参考线，用于对齐其他字母和行内元素。    

vertical-align 控制了img span组件和父容器内以及默认文字的基线对齐，如果要文字+图片垂直居中 需要让父容器fontsize：0 子span和img的vertical-align middle  个人理解 不知道对不对  还有行内元素行内块元素彼此之间换行会被浏览器解析成空白，可以去掉回车直接连着写，还可以父组件font-size 0，子元素再单独设置字体  ，或者中间使用注释  

```
<span>内容1</span><!--
--><span>内容2</span>
```
还有直接在不设置高度div中写个img img下会有空白，这个也是基线对齐导致的，可设置 img的vertical-align: middle等非默认;  也可以直接设置父div font-size：0 ，因为出现这个原因就是由于字导致的。

## 4种方法实现html 页面内锚点定位
1) 最简单的方法是锚点用标签，在href属性中写入div的id。


```javascript
<style>  
    div {  
        height: 800px;  
        width: 400px;  
        border: 2px solid black;  
    }  
    h2 {  
        position: fixed;  
        margin:50px 500px;  
    }  
</style>  
  
  
<h2>  
    <a href="#div1">to div1</a>  
    <a href="#div2">to div2</a>  
    <a href="#div3">to div3</a>  
</h2>  
    <div id="div1">div1</div>  
    <div id="div2">div2</div>  
    <div id="div3">div3</div>  

```


2) 在js事件中通过  



```
 window.location.hash="divId"
```
跳转，但地址也会发生变化，感觉跟第一种方法没区别，甚至更麻烦。


3)  animate属性，当点击锚点后，页面滚动到相应的div。


```
$(document).ready(function() {
    $("#div1Link").click(function() {
        $("html, body").animate({
            scrollTop: $("#div1").offset().top }, {duration: 500,easing: "swing"});
            return false;
    });
    $("#div2Link").click(function() {
        $("html, body").animate({
        scrollTop: $("#div2").offset().top }, {duration: 500,easing: "swing"});
        return false;
    });
    $("#div3Link").click(function() {
        $("html, body").animate({
        scrollTop: $("#div3").offset().top }, {duration: 500,easing: "swing"});
        return false;
    });
});


```
4) 用js的srollIntoView方法，直接用:

```
document.getElementById("divId").scrollIntoView();

比如：

document.querySelector("#roll1").onclick = function(){
      document.querySelector("#roll1_top").scrollIntoView(true);
}  

```
这里就是点击id是#roll1的元素可以滚动到id是#roll1_top的地方，这里的#roll1和#roll1_top最好是一一对应的， 这种方法的好处，是URL不会变，同时能够响应相应的scroll事件，不需要算法什么的。代码如下：

```
<html>
    <head>
        <title>HTML5_ScrollInToView方法</title>
        <meta  charset="utf-8">
        <style type="text/css">
            #myDiv{
                height:900px;
                background-color:gray;

            }
            #roll_top{
                height:900px;
                background-color:green;
                color:#FFF;
                font-size:50px;
                position:relative;
            }
            #bottom{
                position:absolute;
                display:block;
                left:0;
                bottom:0;
            }
        </style>
    </head>
    <body>
        <button id="roll1">scrollIntoView(false)</button>
        <button id="roll2">scrollIntoView(true)</button>
        <div id="myDiv"></div>
        <div id="roll_top">
            scrollIntoView(ture)元素上边框与视窗顶部齐平
            <span id="bottom">scrollIntoView(false)元素下边框与视窗底部齐平</span>
        </div> 
    </body>
</html>

```
javascript部分
```
window.onload = function(){
    /*
        如果滚动页面也是DOM没有解决的一个问题。为了解决这个问题，浏览器实现了一下方法，
    以方便开发人员如何更好的控制页面的滚动。在各种专有方法中，HTML5选择了scrollIntoView()
    作为标准方法。
        scrollIntoView()可以在所有的HTML元素上调用，通过滚动浏览器窗口或某个容器元素，
    调用元素就可以出现在视窗中。如果给该方法传入true作为参数，或者不传入任何参数，那么
    窗口滚动之后会让调动元素顶部和视窗顶部尽可能齐平。如果传入false作为参数，调用元素
    会尽可能全部出现在视口中（可能的话，调用元素的底部会与视口的顶部齐平。）不过顶部
    不一定齐平，例如：
    //让元素可见
    document.forms[0].scrollIntoView();
    当页面发生变化时，一般会用这个方法来吸引用户注意力。实际上，为某个元素设置焦点也
    会导致浏览器滚动显示获得焦点的元素。
        支持该方法的浏览器有 IE、Firefox、Safari和Opera。
    */

    document.querySelector("#roll1").onclick = function(){
        document.querySelector("#roll_top").scrollIntoView(false);
    }
    document.querySelector("#roll2").onclick = function(){
        document.querySelector("#roll_top").scrollIntoView(true);
    }
}

```
 

 ## 选择器 
 ```
 在 CSS 中，逗号（,）用于将多个选择器组合在一起，表示“或者”的关系。
 h1, p {
  color: red;
}

选择同时满足多个条件的元素（即“并”的关系），你可以将类名链接在一起，形成一个类名链。 
.box.red.large {
  /* CSS */
}

后代选择器
 div p {
  /* CSS */
}

CSS 中的子代选择器用 > 符号表示
div > p {
  /* CSS */
}

兄弟选择器用 + 符号表示  
h2 + p {
  /* CSS */
}上述规则中的 + 符号表示选择紧接在 <h2> 元素之后的同级 <p> 元素。（如果<p> 不在 <h2>下紧紧相邻 那么<p>样式无效）
h2 ~ p 这个选择器时，它会选择所有紧跟在 <h2> 元素之后的同级 <p> 元素，无论它们是否紧邻。

属性存在选择器 [title]：选择具有指定属性的元素。
[title] {
border: 1px solid red;
}它会选择具有 title 属性的所有元素
[title='a'] {
border: 1px solid red;
}它会选择具有 title 属性 并且值为a的所有元素
[title^='a'] {
border: 1px solid red;
}它会选择具有 title 属性 并且值以a开头的所有元素
[title$='a'] {
border: 1px solid red;
}它会选择具有 title 属性 并且值以a结尾的所有元素
[title*='a'] {
border: 1px solid red;
}它会选择具有 title 属性 并且值包含a的所有元素


```

## 伪类选择器
伪类选择器是CSS中一种用于选择元素的状态或特定位置的方法。它们以冒号（:）开头
 ```
链接伪类选择器 :link 和 :visited：分别选择未访问过和已访问过的链接元素。
a:link {
  color: blue;
}
a:visited {
  color: purple;
}
鼠标状态伪类选择器 :hover 和 :active：分别选择鼠标悬停和被点击的元素。
button:hover {
  background-color: yellow;
}
button:active {
  background-color: green;
}
焦点伪类选择器 :focus：选择当前获取焦点的元素。
input:focus {
  border: 2px solid blue;
}
子元素伪类选择器 :first-child 和 :last-child：选择父元素中的第一个和最后一个子元素。
ul li:first-child {
  font-weight: bold;
}
ul li:last-child {
  color: red;
}

选择第 n 个子元素：
ul li:nth-child(3) {
  color: red;
}
选择偶数或奇数位置的子元素
ul li:nth-child(even) {
  background-color: lightgray;
}
ul li:nth-child(odd) {
  background-color: lightblue;
}
选择周期性重复的子元素：
ul li:nth-child(3n+1) {
  font-weight: bold;
}

选择与给定类型匹配的元素中的第一个出现的元素。
div p:first-of-type {
  color: red;
}
div p:last-of-type {
  color: red;
}

选择与给定类型匹配的同类型元素中的第n个出现的元素。
div p:nth-of-type(n) {
  color: red;
}
 
:only-child 选择器选择在其父元素中作为唯一子元素的元素
:only-of-type 选择器选择在其父元素中作为特定类型的唯一子元素的元素
:root 是一个伪类选择器，用于选择文档的根元素，通常指的是 <html> 元素 
:not 是一个伪类选择器，用于选择不符合指定条件的元素。它允许你排除某些元素，而选择其他的元素。


 ```


## 伪元素选择器
::before：在元素内容之前插入生成的内容。  
::after：在元素内容之后插入生成的内容。    
::first-line：选择元素中的第一行文本。  
::first-letter：选择元素中的第一个字母。  
::selection：选择用户选择的文本部分。  

***伪类选择器用于选择符合特定状态或条件的元素，伪元素选择器用于向元素的特定部分添加额外的内容或样式***  
`！important > 行内 > ID选择器 > 类选择器 > 元素选择器 > * > 继承样式`

 ## font-weight 
 lighter 细 、normal 正常、bold 粗、bolder 很粗（多字体不支持）   
 100～300 等价 lighter     
 400～500 等价 normal    
 600及以上 等价 bold    

## css长度单位
* 像素（px）：像素是最常用的单位，表示屏幕上的一个物理像素点。
* 百分比（%）：百分比是相对于父元素的长度或宽度的比例。例如，设置一个元素的宽度为50%，表示它的宽度将是父元素宽度的一半。
* em（em）：em 是相对于元素自身的字体大小的单位。例如，设置一个元素的宽度为2em，表示它的宽度将是其字体大小的两倍。
* rem（rem）：rem 也是相对于根元素（即 <html> 元素）的字体大小的单位。与 em 不同，rem 不会受到父元素字体大小的影响。
* 视窗单位（vw、vh、vmin、vmax）：视窗单位是相对于浏览器窗口的尺寸进行计算的单位。vw 表示视窗宽度的百分比，vh 表示视窗高度的百分比，vmin 表示视窗宽度和高度中较小的那个的百分比，vmax 表示视窗宽度和高度中较大的那个的百分比。
* 厘米（cm）、毫米（mm）、英寸（in）、点（pt）、派卡（pc）：这些单位用于指定具体的物理尺寸，如厘米、毫米、英寸、点和派卡。


## 外边距塌陷的原因可以归结为CSS盒模型的规范中定义的特定行为
* 相邻兄弟元素：当相邻的两个块级元素（兄弟元素）之间没有边框、内边距、行内内容或清除浮动，并且它们的上下外边距相遇时，它们的外边距会合并成一个外边距，取其中较大的那个值。这种合并现象称为兄弟元素的外边距塌陷。    
* 父元素与第一个/最后一个子元素：当父元素的上下外边距与其第一个子元素的上外边距或最后一个子元素的下外边距相遇时，它们的外边距会合并成一个外边距，取其中较大的那个值。这种合并现象称为父元素与第一个/最后一个子元素的外边距塌陷    
* `父容器添加边框时，可以阻止外边距塌陷的发生，` 边框可以防止父容器的外边距与子元素的外边距相遇并合并。    
* `使用内边距（padding）：`给父容器添加适当的内边距可以阻止外边距的合并  
* `使用溢出（overflow）：`将父容器的溢出属性设置为非默认值（例如，overflow: hidden;）可以创建一个新的块级格式上下文，从而阻止外边距的合并。这是因为块级格式上下文会隔离元素的外边距，使其不会与其他元素的外边距发生塌陷。  
* `使用浮动（float）：`将父容器或子元素设置为浮动状态，也可以防止外边距塌陷。浮动元素会创建一个新的块级格式上下文，从而隔离其外边距，阻止与其他元素的外边距合并。  
* `使用定位（positioning）：`将父容器或子元素设置为相对定位（position: relative;）或绝对定位（position: absolute;），也可以避免外边距塌陷。定位元素会形成一个新的块级格式上下文，从而分隔外边距，使其不会发生塌陷。


## 隐藏CSS组件
* display属性设置为"none"，可以完全隐藏组件
* visibility属性设置为"hidden"，可以隐藏组件但仍占用空间。这样做将使组件在页面上不可见，但它仍会保留其占用的空间
* opacity属性设置为0，可以使组件透明并隐藏。这样做将使组件在页面上不可见，但它仍将占用其正常的空间

 

## 定位
>Relative（相对定位）：通过设置position: relative;，元素相对于其正常位置进行偏移。    
>Absolute（绝对定位）：通过设置position: absolute;，元素相对于其最近的非静态父元素进行定位。如果没有非静态父元素，那么元素会相对于文档根元素进行定位。  
>Fixed（固定定位）：通过设置position: fixed;，元素相对于浏览器窗口进行定位，即使页面滚动，元素也会保持在固定位置。  
>Sticky（粘性定位）：通过设置position: sticky;，元素在滚动到特定位置时会变为固定定位，否则按照正常文档流布局。  
`span元素的position属性设置为"absolute fixed"可以使用width和height属性来定义元素的尺寸，relative不行 相对定位相对自己 还是之前的显示模式`  

## 定位的层级z-index
定位的层级要高于普通元素    
元素必须具有定位属性position 属性  
> 让定位元素左右充满其父容器

```
.parent {
  position: relative;
}

.child {
  position: absolute;
  left: 0;
  right: 0;
}
```  

> 虽然可以flex（子元素margin：auto或者justify-content align-items：center），但是使用绝对定位将元素水平垂直居中 


```
.element {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
}

```

## background复合属性

```
div {
颜色 背景 背景图重复 位置/大小 背景图片固定在视口中，不随滚动而滚动。  起始位置以容器的内边距框为准 裁剪区域为容器的边框框
  background: #f00 url('image.jpg') no-repeat top right / cover fixed padding-box border-box;
}
```

## outline外轮廓不参与盒子运算


