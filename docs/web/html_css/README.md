<!--
 * @Date: 2024-01-16 14:36:46
 * @LastEditors: tandongyang =
 * @LastEditTime: 2024-01-22 18:10:35
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
***行内元素（除可替换元素比如img input内容都不是通过在标签内添加文本，而是通过某个属性）不能设置宽 高 margin ,padding上下会生效 但对其上下的元素无影响***


## vertical-align
vertical-align的作用对象是 inline-level element，也就是内联级元素。 即： ***inline  inline-block !!!***  
vertical-align的作用其实是控制元素的垂直对齐方式，而不是绝对的解决垂直居中的方案。因为有时候当你使用它的时候，你会发现，nothing happened。而神奇的是，它附近的元素发生了改变。
```
'vertical-align'
Value:      baseline | top | middle | bottom 
Initial:    baseline

```
[vertical-align MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/vertical-align)

单独img标签，由于默认是基线对齐，下面如果有块元素，会有段空白间隙。原因：基线标准x的底部 预留超出类似j等字母超出x底部长度。解决：img转化block 或者改变img的vertical-align: 使用middle等；  
可以说基线是 'x' 字母的底部。但需要注意的是，基线并不是严格定义为 'x' 字母的底部，而是一个相对的参考线，用于对齐其他字母和行内元素。  

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

