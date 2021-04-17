---
layout:     post
title:      SuNing Index Creat -4
subtitle:   HTML5 + CSS3
date:       2020-05-28
author:     HongShield
header-img: img/post-bg-h5c3.png
catalog: true
tags:
    - HTML5
    - CSS3
---
# 五、剩余区域presale和main-first的制作
接下来我们进行剩下部分的制作，这一块区域背景色是灰色的，不再是纯白#ffffff色的。先制作前两块块区域。顺便把左边的悬浮导航制作一下。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528184636234.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
## 1.presale的制作
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528185255807.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
### ①结构分析
1.这一块我原以为只有图片的上半部分是图片，下半部分红色区域是css实现的，结果在网页扒图的时候发现，这两部分是一个整体，是一张图片。
2.只需要往其中添加一个ul列表，定位到合适的位置就行。这么一来就简单多了。
### ②html结构搭建
1.这个背景图是一张大图，同时还有一张上半部分的图，便于添加ul列表，撑开内容。
2.我们发现这整个区域都是插入了链接，包括图片的上半部分。显然链接不能添加到整块背景图上。所以分开进行链接的添加。
```html
<img src="./img/159013915800672132.png" alt="" class="back">

      <a href="#" class="top">
        <img src="./img/159013929674557432.png" alt="" class="tupian">
      </a>
```
下来就是图片底部ul列表的添加。因为li内容大同小异，我们只拷贝了一块代码，li 是由一张图片两行字组成的，分别给图片和文字添加了链接
```html
<div class="bottom">
        <ul>
          <li>
            <a href="" class="tupian">
              <img src="./img/0000000000000000010217696270.jpg" alt="">
            </a>
            <a href="" class="text">
              <p class="title">清凉风扇</p>
              <p class="desc">低至7折起</p>
            </a>
          </li>
       </ul>
</div>
```
### ③CSS样式添加
先确定presale的大小，进行定位

```css
.presale {
  width: 1190px;
  margin: 0 auto;
  position: relative;
  height: 364px;
  overflow: hidden;
}
```
然后就是分区域进行设置调整，先将背景图添加好。通过绝对定位的方法定位到页面中间。

```css
.presale .back {
  position: absolute;
  top: 0;
  left: -365px;
}
```
小图片的插入，宽度设置100%，就是宽度继承父容器的宽度。

```css
.presale .top {
  width: 100%;
  height: 150px;
}
```
ul列表区域大小的设定，将其定位到背景图的底部，并且另文本居中。
```css
.presale .bottom {
  width: 1190px;
  height: 213px;
  overflow: hidden;
  position: absolute;
  text-align: center;
}
```
列表的每一项li大小，利用浮动让li排列在一行

```css
.presale .bottom ul li {
  width: 228px;
  height: 213px;
  margin: 0 0 10px 10px;
  float: left;
}
```
li中的小图片的设置
```css
.presale .bottom ul li .tupian img {
  width: 120px;
  height: 120px;
  margin: 10px auto 0;
}
```
两行文字的设置，大小，颜色等直接扒网站的就可以，可以节省一点时间。
```css
.presale .bottom ul li .text .title {
  font-size: 20px;
  line-height: 28px;
  width: 210px;
  height: 28px;
  margin: 15px auto 6px;
  color: #ffffff;
}
.presale .bottom ul li .text .desc {
  height: 22px;
  margin-top: 6px;
  line-height: 22px;
  font-size: 16px;
  color: #ff353f;
}
```
## 2.first以及悬浮导航的制作
因为代码繁多，我只将结构进行分析，对一些比较有难度的css样式进行一个叙述，对于简单的就不进行叙述了，减少篇幅。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528192122931.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
### ①结构分析
这块区域大致分为左右两块，左边分为一个top和下面的ul列表，右边同样分为两块上面和下面。
### ②html结构搭建
left-top的结构，这一块可细分为四块，一个图片，两段文字，以及最右边的两段文字。

```html
        <div class="top">
          <img src="./img/天天低价.png" alt="">
          <p class="text ">距离下场</p>
          <p class="time ">
            <span class="hour-node">02</span>
            <i>&nbsp;</i>
            <span class="minute-node">53</span>
            <i>&nbsp;</i>
            <span class="second-node">47</span>
          </p>
          <div class="right">
            <ul>
              <li><i>10:00</i>场-正在疯抢</li>
              <li><i>13:00</i>场-即将开抢</li>
            </ul>
          </div>
        </div>
```
left-bottom的结构制作，这一块区域是一个ul列表，li中还是比较复杂的，可以分为4块内容，图片，标题，价格，进度条。同样li大同小异，只拷贝其中一个li

```html
<li><a>
  <img src="./img/first_1.jpg" alt="">
  <p class="title">维生素E乳V身体乳补水保湿滋润全身秋冬香体润肤露护肤面霜男女士新品 100g</p>
  <p class="price">
    <span class="gbprice"><i>￥</i><em>5.8</em></span><span class="newprice"><i>￥</i><em>19.9</em></span>
  </p>
  <p class="line">
    <span style="width: 94px;"></span>
  </p>
  <p class="precent">
     已抢<i>94</i>%
  </p>
</a></li>
```
right的制作和left类似。特别需要注意的一点就是大图的中间又嵌套了一个div标签
悬浮导航的制作，主体由ul构成。再添加图标到导航的顶部就可以，也是比较简单的。
### ③CSS样式添加
确定first区域的大小，另其居中
```css
.first {
  width: 1190px;
  margin: 20px auto;
  position: relative;
}
```
设置左区域的大小，背景色。border-radius是给区域添加圆角，一般是写像素大小。50%就是一个圆区域。
```css
.first .left {
  position: relative;
  width: 790px;
  min-width: 790px;
  height: 330px;
  background: #fff;
  border-radius: 4px;
}
```
top的下面有一条类似下边框的横线，注意：这一条横线并不是下边框，如果是下边框的话，这条横线的长度是整个top区域的宽度，而不是我们所看到的长度较短的横线。
那么这个横线是怎么制作的呢？是通过::after 伪类选择器，是通过content添加的页面中的，

```css
.first .left .top::after {
  content: "";
  width: 755px;
  height: 1px;
  position: absolute;
  top: 46px;
  left: 18px;
  background-color: #ededed;
}
```
在top的右边，文字有一个背景色，这个背景色不是通过添加背景图实现，而是通过css样式的颜色渐变实现的。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528210321903.png)
这个渐变是横向渐变的。llinear-gardient 渐变默认是纵向渐变。我们可以添加一个角度 90 deg，至于具体的渐变过程，在开发过程中，在设计稿中应该可以找到。例如蓝湖等平台。
```css
.first .left .top .right li:hover {
  background-image: linear-gradient(90deg, #f60 7%, #f22 97%);
  border-radius: 31px;
  color: #fff;
}
```
如果遇到超长的文本，不想超出标签设定区域，可以添加溢出隐藏，word-break是针对文本折行。break-all 可以在文本的任意位置进行折行。
```css
.first .left .main ul li .title {
  width: 170px;
  height: 20px;
  margin: 0 0 0 20px;
  color: #333;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  word-break: break-all;
}
```
下面我们说一下进度条的实现
首先呢进度条分为两块，颜色亮暗不同，给父容器添加一个暗的进度条，设置长度为100，给子容器添加亮的进度条，长度我们根据需求进行设置，例如想要达到56%的效果，我们就设置长度为56px，为了方便，我将长度直接添加在了标签上面。

```css
.first .left .main ul li .line {
  background-image: url(../img/index.png);
  background-position: 0 -332px;
  height: 4px;
  width: 100px;
  float: left;
  margin: 9px 0 0 20px;
}

.first .left .main ul li .line span {
  float: left;
  height: 4px;
  background-image: url(../img/index.png);
  background-position: -104px -332px;
}
```
右边有一块有意思的区域，div嵌套在了图片之中，并且div区域还有外边框，他是通过给父容器添加一个边框设置圆角，子容器区域设置圆角，实现了这一功能。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528213850538.png)
```css
.first .right .union .center .small {
  position: absolute;
  left: 12px;
  top: 39px;
  width: 158px;
  height: 98px;
  border: 1px solid #fff;
  border-radius: 10px 24px 10px 24px;
}
.first .right .union .center .small .warp {
  width: 152px;
  height: 92px;
  background: #fff;
  border-radius: 8px 22px 8px 22px;
  margin: 3px;
  overflow: hidden;
}
```

```
我们直接跳到悬浮导航的制作，唯一的难点就是让导航悬浮起来，其他的很简单，至于实现悬浮，是通过 position:fixed; 实现的，fixed 使得内容相对于页面，就是显示器进行定位，这样定位让内容不再随着页面的上下的移动而改变自己的位置，而是固定在了屏幕的某一位置。

```css
.main .floatbar {
  position: relative;
  width: 68px;
  padding-top: 9px;
  border: 1px solid #ddd;
  background: #f8f8f8;
  position: fixed;
  top: 40%;
  left: 6%;
  font-size: 12px;
}
```
