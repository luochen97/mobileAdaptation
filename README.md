> 规则就是：文字流式，控件弹性，图片等比缩放
> 视口：浏览器中用于显示网页的区域。在移动端，绝大多数情况下 viewport 都大于浏览器可视区，保证 PC 页面在移动浏览器上面的可视性。
```
<meta name='viewport' content='width=device-width,initial-scale=1,user-scale=no' />
```
# 百分比
> 百分比类型定制规则
```
width:取父元素宽度
height:取父元素高度
margin，padding均取父元素宽度
border不可用百分比
```
# media（媒体查询）
> 可以根据不同的媒体类型，不同的屏幕尺寸，定制不同的样式。
```
@media mediatype and|not|only (media feature) {
    CSS-Code;
}
<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="mystylesheet.css">
```
# Flex 弹性布局
* 教程  http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html
> 主要思想是父元素能够调节子元素的宽高，排列顺序，从而能够最优
## Flex布局和传统的其他布局有什么优点？
传统布局，基于盒模型，依赖 display属性 、position属性 、float属性<br/>
Flex布局,提升了盒模型的灵活性，可以响应式的实现页面布局
## 使用场景
```
1.单列宽度均等分
2.某列宽度固定，其他宽度自适应
3.宽度固定，间距始终均等分
4.垂直居中布局（不定宽高）
5.网格布局
6.圣杯布局
7.固定底部和顶部，中间自适应布局
8.流式布局
```
## 基础知识
> 父元素设置了flex属性，他的子元素自动成为flex项目。flex布局分俩个轴：主轴和垂直于主轴的交叉轴
### 容器属性
#### flex-direction
> 该属性决定了主轴的方向
```
row :主轴在水平轴，起点在左端
column: 主轴在垂直轴，起点在上侧
row-reverse: 主轴在水平轴，起点在右端
column-reverse: 主轴在垂直轴，起点在下侧
```
#### flex-wrap
> 该属性决定了一行显示不下，如何换行
```
nowrap :不换行
wrap: 第一行在上面
wrap-reverse: 第一行在下面
```
#### justify-content
> 项目在主轴上的排列顺序
```
// 假设主轴是水平
flex-start :左对齐
flex-end: 右对齐
center: 居中对齐
space-between: 两端对齐，间距均等分
space-around: 每个项目间距均等分
```
#### align-items
> 项目在交叉轴上的排列顺序
```
// 假设主轴是水平，即交叉轴是自上而下
flex-start :上对齐
flex-end: 下对齐
center: 居中对齐
baseline: 文字基线对齐
strech:若项目未设置高度或高度为auto,项目高度将铺满整个容器高度
```
#### align-content
> 多条轴线情况下，项目在主轴上的排列顺序
```
// 假设主轴是水平
flex-start :左对齐
flex-end: 右对齐
center: 居中对齐
space-between: 两端对齐，间距均等分
space-around: 每个项目间距均等分
strech:轴线占满整个交叉轴
```
### 项目属性
#### order 定义项目的排列顺序。数值越小，越靠前。默认值为零
#### flex-grow 定义项目的放大比例
#### flex-shrink 定义项目的缩小比例
#### flex-basis 定义在分配多余空间之前，项目占据的主轴空间
#### align-self 允许单个项目优于其他项目不一样的对齐方式
```
// 假设主轴是水平
flex-start :上对齐
flex-end: 下对齐
center: 居中对齐
baseline: 文字基线对齐
strech:轴线占满整个交叉轴
```
# rem
> rem是一个相对于根节点html->font-size属性值的css3单位，可以设置高度和宽度，边框，字体，padding，margin。
> 移动端是根据屏幕的clientWidth属性，动态给html添加font-szie属性
```
var cw=document.documentElement.clientWidth || document.body.clientWidth;//获取设备宽度
  var html=document.getElementsBytagName('html')[0];<=>document.querySelector('html');
  //获取html元素
  html.style.fontSize=cw/10 +'px';//html设置font-size
```
> 这样相当于1rem = cw/10+'px';我们可以根据设计稿的依赖，一般设计稿是iphone6 =>750px;即：1rem= 75px; 设计稿上某个盒子的宽度为200px;我们可以设置width:200/75+'rem',
```
// 巧妙利用scss 
$rem:75;//声明对象-> 设计稿对应的iphone尺寸的根节点font-size的值
@function function-name($args) { 
   //定义函数
  @return $args/$rem; 
}
// 调用时
width: function-name(500rem);
```
# vw
> 1vw等于1%屏幕的宽度

