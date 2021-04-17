---
layout:     post
title:      前端-H5+C3-2
subtitle:   纯html5+css3实现SuNing首页
date:       2020-05-21
author:     HongShield
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - HTML5
    - CSS3
---
# 三、主体内容顶部的制作
接下来我们要制作的就是包含logo，搜索框，以及下面菜单的这一块内容
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200521122744149.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
## 1.框架分析
这块内容可以划分为5块，苏宁logo，搜索框，全部商品分类，右边的图片以及中间的菜单。我们又可以将logo和搜索框划分为一块（这一块我起名为body_head），剩下的3部分为一块（可以起名为body_menu）.
## 2.body_head 制作
### 1.具体分析（排版）
1.我们给body_head容器一个固定大小，一般就是版心的大小，然后将搜索框在容器中居中，再用定位将logo定位到容器左端。
2.这里有一个小技巧，在确定容器大小之后，可以给容器先添加边框，以便于我们对每一块的调整。等到CSS样式添加完成之后，将添加的边框去掉。如果边框去掉后出现了一些问题再根据问题进行微调。
3.虽然我们没有设计稿，但是我们可以直接在官网打开控制台，直接查看元素的宽高，颜色，字体大小等。没有必要自己去测量，这样可以节省很多时间。关键的是一个思路，以及语法的细节。
### 2.CSS样式添加
#### 1.搜索框的制作
1.我们先给搜索框一个容器大小，添加一个边框便于我们的调整。利用margin 0 auto； 进行居中。

```css
.body_head .body_head_search {
  width: 600px;
  height: 100px;
  margin: 0 auto;
  position: relative;
  border :1px solid red;
}
```

2.接下来我们将本块分为三部分，一个是搜索框input，一个是搜索按钮 button，另一块就是紧挨搜索框的菜单。先进行input的制作，先给这一块加一个边框，这个边框加在了search_body的上面。

```html
<div class="search_body">
        <span class="iconfont icon-sousuo"></span>
        <input type="text" placeholder="输入关键字搜索商品/品牌/店铺">
      </div>
```
3. 接下来，我们通过定位将div定位，上下一定是居中，左右就要通过一些计算，定位的时候，要给父容添加相对定位，给自身添加绝对定位。一定要找准父容器。
调整好位置之后，由于这个区域本身是有边框的，我们直接修改边框的大小，颜色，注意，搜索框没有右边框。

```css
.body_head .body_head_search .search_body {
  position: absolute;
  top: 30px;
  width: 420px;
  height: 40px;
  border: 2px solid #fa0;
  border-right: none;
  margin: 30px 120px 30px 60px;
  position: relative;
}
```
4.我们进行区域内部样式的添加，要清楚input 是有默认样式的，不仅仅是边框，而且当你鼠标点击的时候，还会有一个边框，这时候就需要用 outline:none;来取消默认样式。input左边的“放大镜”可以通过添加矢量图标进行添加。改变input输入框的大小，让它的大小和父容器相匹配。同时，我们可以看到，输入框中当我们没有输入的时候，默认会有一些输入内容，这时候我们就可以用input属性placeholder来添加。

矢量图标的调整：
```css
.body_head .body_head_search .search_body span {
  font-size: 18px;
  line-height: 40px;
  color: #cccccc;
  padding-left: 5px;
}
```
input输入框的调整：
```css
.body_head .body_head_search .search_body input {
  width: 390px;
  height: 40px;
  font-size: 12px;
  border: 0px;
  outline: none;
  position: absolute;
  top: 0;
}
```
5.input输入框的右边，有一个搜索按钮。有两种方法来实现，第一种方法，我们取消按钮的默认样式，并调整合适的大小，将按钮定位到input右边，同时引入图片将图片定位到同一位置实现覆盖。
第二种方法就是通过修改按钮的样式来达到同样的效果。会有一个手型的变化
```css
.body_head .body_head_search button {
  width: 120px;
  height: 44px;
  position: absolute; //手型的添加
  right: 4px;
  top: 30px;
  border: none;
  background: #ff9900;
  font-size: 18px;
  color: #ffffff;
  font-weight: bold;
  outline: none;
}
```

我们可以观察到，当鼠标移动上去的时候背景也会发生变化。我们通过添加hover来实现。

```css
.body_head .body_head_search button:hover {
  background: #ff8800;
  cursor: pointer;
}
```


![无hover](https://img-blog.csdnimg.cn/20200521132458907.png)

6.接下来进行search_foot,也就是紧挨输入框的菜单,菜单中的九个选项都是a链接,我们可以直接在div中嵌套9个a链接.然后通过调整选项之间的间距等,给div添加绝对定位,调整位置.可以看到每一个选项之间看到一条灰色的竖线.有两种方法添加,一种是"手动添加",在每两个a链接之间通过 i 标签 添加一条竖线 " | ",这种无疑是比较low的,我采用第二种方法,直接给a链接添加一个左边框.
定位菜单的位置
```css
.body_head .body_head_search .search_foot {
  position: absolute;
  left: 53px;
  bottom: 3px;
}
```
菜单选项a链接的设置
```css
.body_head .body_head_search .search_foot a {
  font-size: 12px;
  color: #999999;
  padding: 0 7px 0 8px;
  border-left: 1px solid #dddddd;
}
```
7.这时看到“电风扇”的左边也有了边框，实际上是没有的，所有我们使用:nth-child() 伪类选择器来进行调整。

```css
.body_head .body_head_search .search_foot a:nth-child(1) {
  border: none;
}
```
8.有两个选项的颜色与其他的不同，我们同样通过伪类选择器进行选择添加。

```css
.body_head .body_head_search .search_foot a:nth-child(2) {
  color: #ff6600;
}
.body_head .body_head_search .search_foot a:nth-child(4) {
  color: #ff6600;
}
```

9.a链接在选中的时候还会变色，我们再添加一个hover，

```css
.body_head .body_head_search .search_foot a:hover {
  color: #ff6600;
}
```
至此，搜索框的制作就完成了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200521141319727.png)
#### 2.body_head_logo的添加
这块内容就很简单了，把logo定位到对应位置之后，调整大小就ok

```html
<div class="body_head_logo">
      <img src="./img/logo.png" alt="苏宁易购">
    </div>
```

```css
.body_head .body_head_logo img {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 190px;
  height: 90px;
}
```
#### 3,接下来进行下一大块的制作
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200521141923735.png)
1.这一块内容分为了三块，左边的a链接，中间的menu，右边的图片(图片中也是有链接的)

```html
<div class="body_head_foot">

      <a href="#" class="body_head_foot_left">
        <span class="iconfont icon-liebiao"></span>
        全部商品分类
      </a>

      <div class="body_head_foot_menu">
        <a href="#">天天低价</a>
        <a href="#">红孩子</a>
        <a href="#">苏宁超市
          !-- <img src="./img/index.png" alt=""> 
        </a>
        <a href="#">电器城</a>
        <a href="#">生活家电</a>
        <a href="#">时尚服饰</a>
        <a href="#">苏宁国际</a>
        <a href="#">苏宁Outlets</a>
        <a href="#">金融</a>
      </div>
		<a href="#">
        <img src="./img/156810604991255454.png" alt="">
     	</a>
```
2.接下来一块一块的调整，左边调整，先将a链接转成块，否则a的大小由内容的大小决定，自定义的大小是无效的，为了便于调整，给“全部商品分类”添加了 i 标签，注意一点：i 标签默认是斜体，必须通过 font-style:normal 来调整成为正常字体.为了使字体居中,可以设置行高等于容器的高度.

```css
.body_head_foot .body_head_foot_left {
  display: block;
  width: 190px;
  height: 38px;
  line-height: 38px;
  color: #ffffff;
  background: #ff9900;
}
.body_head_foot .body_head_foot_left span {
  font-size: 13px;
  padding-left: 4px;
}
.body_head_foot .body_head_foot_left i {
  font-size: 13px;
  font-style: normal;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200521155915755.png)
此外,还有一个hover效果

```css
.body_head .body_head_foot.body_head_foot .body_head_foot_left:hover {
  background: #ff6600;
}
```
3.进行menu和right 的定位

```css
.body_head .body_head_foot .body_head_foot_menu {
  padding-left: 10px;
  position: absolute;
  left: 190px;
  bottom: 0;
}

.body_head .body_head_foot .body_head_foot_right {
  position: absolute;
  right: 0;
  top: 0;
}
```
4.下来我们先进行right的定位,

```css
.body_head .body_head_foot .body_head_foot_right {
  position: absolute;
  right: 0;
  top: 0;
}
.body_head .body_head_foot .body_head_foot_right img {
  width: 170px;
  height: 38px;
}
```

5.下面对menu进行处理
对menu进行CSS样式的添加,很简单,调整字体大小,设置margin或者padding调整选项的距离.需要注意的地方是:苏宁超市后面有一个小图标,那个是通过 雪碧图 来进行引用,就是下面这张图.
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200521162555784.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
5.先进行menu其他样式的添加先把a链接模块化,之后就是正常的浮动,padding等

```css
.body_head .body_head_foot .body_head_foot_menu {
  padding-left: 10px;
  position: absolute;
  left: 190px;
  bottom: 12px;
}
.body_head .body_head_foot .body_head_foot_menu a {
  float: left;
  display: block;
  padding: 0 14px 0 11px;
  font-size: 15px;
  font-weight: bold;
  line-height: 38px;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200521183318101.png)
6.menu在选择时有变色效果,添加hover

```css
.body_head .body_head_foot .body_head_foot_menu a:hover {
  color: rgb(255, 102, 0);
}
```
7.最后我们来进行雪碧图的添加.添加雪碧图首先需要绝对定位position,通过背景图 backgrou-image:url();来引用,然后用 background-position 来定位.然后设置所引用区域的大小.

```css
.body_head .body_head_foot .body_head_foot_menu .hot {
  position: absolute;
  width: 14px;
  height: 17px;
  background-image: url(../img/index.png);
  background-position: -345px -213px;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200521184032124.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)


*[雪碧图]:  许多小的图标放在了一张图里,目的是减少访问服务次的次数