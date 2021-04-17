---
layout:     post
title:      前端-H5+C3-3
subtitle:   纯html5+css3实现SuNing首页
date:       2020-05-24
author:     HongShield
header-img: img/post-bg-h5c3.jpg
catalog: true
tags:
    - HTML5
    - CSS3
---
#  四、推荐栏（recommend）的制作
接下来的这一块区域，是整个网页中最醒目的一块，是官方的强力推荐区域。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200524190857438.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
## 1.结构分析
我将这块内容分为左中右三块内容，左边就是一个列表（一级菜单嵌套二级菜单，同样我们只做一级菜单），中间可分为两块，大图，和底部的列表，右边分为3块，上面的登录，中间的热门，底部的快捷区域。
## 2.先进行center的制作。
我个人喜欢由中间向两边制作，所以我先进行中间的制作。
我们先将图片插入，并令图片居中

```html
 <div class="banner_center">
        <a href="#" class="dynamic"><img src="./img/159006488916851510.jpg" alt=""></a>
```
设置center区域，在进行排版的时候可以加上1px的边框。
```css
.recommend .recommend_banner .banner_center {
  width: 830px;
  height: 482px;
  margin: 0 0 0 190px;
  position: relative;
}
```
将图片进行定位，在定位时需要给父容器添加相对定位，给自己绝对定位
```css
.recommend .recommend_banner .banner_center .dynamic img {
  width: 830px;
  height: 482px;
  position: absolute;
  top: 0;
}
```
接下来制作center_bottom，这一块其实是一个列表，只不过是列表中又嵌套了两个p标签以及一个图片
```html

        <div class="center_bottom">
          <ul>
            <li>
              <p class="title" style="color:#EF4124">生活家电</p>
              <p class="desc">两件8.5折</p>
              <img src="./img/0000000000000000010953819451.jpg" alt="">
            </li>
            <li>
              <p class="title" style="color:#9837EE">电视家影</p>
              <p class="desc">至高24期免息</p>
              <img src="./img/0000000000000000000735494281.jpg" alt="">
            </li>
            <li>
              <p class="title" style="color:#28AF2E">厨卫精选</p>
              <p class="desc">24期分期免息</p>
              <img src="./img/0000000000000000000143172624.jpg" alt="">
            </li>
            <li>
              <p class="title" style="color:#2482EF">集成家电</p>
              <p class="desc">抢千元红包</p>
              <img src="./img/0000000000000000000187616206.jpg" alt="">
            </li>
          </ul>
        </div>
      </div>
```
添加CSS样式，可以固定4个li的大小，将图片定位到li的右下角
```css
.recommend .recommend_banner .banner_center .center_bottom li img {
  width: 80px;
  height: 80px;
  position: absolute;
  right: 0;
  bottom: 0;
}
```
观察到4个li中的title颜色不同,但是大小相同,相对位置也相同,可以将相同的部分提取出来,颜色的设置,直接在HTML标签上面进行style的设置
```css
.recommend .recommend_banner .banner_center .center_bottom li .title {
  font-size: 17px;
  margin: 10px 0 0 12px;
  font-weight: bold;
}
.recommend .recommend_banner .banner_center .center_bottom li .desc {
  color: #666666;
  font-size: 14px;
  margin: 1px 0 0 12px;
}

```
这个列表在导航栏的底部,必须将其定位,定位之后设置li的大小,背景色.最后再根据设计稿进行微调
```css
.recommend .recommend_banner .banner_center .center_bottom ul {
  position: absolute;
  bottom: 0;
}
.recommend .recommend_banner .banner_center .center_bottom li {
  float: left;
  width: 202px;
  height: 122px;
  background-color: #ffffff;
  margin-left: 3px;
  position: relative;
}
```
下面进行选择图标的添加,这个是通过雪碧图进行添加的
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020052420351481.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
图中用红色框选住的地方就是接下来要添加的.具体产生作用是要和js进行配合,在这里我们只是做出来一个样式.此处要注意:图片两端的箭头是当你的鼠标移动到图片的时候才是显示出来,进一步当你的鼠标移动到箭头上到的时候,会产生一个变色效果.由于水平有限未能实现图片的一个hover效果. 箭头的变色效果同样是通过添加雪碧图实现的.
以下是HTML框架
```html
        <div class="nav">
          <div class="bottom">
            <a href=""></a>
            <a href=""></a>
            <a href=""></a>
            <a href=""></a>
            <a href=""></a>
            <a href=""></a>
            <a href=""></a>
            <a href=""></a>
          </div>
          <a href="" class="left"></a>
          <a href="" class="right"></a>
        </div>

```
下面进行css样式的添加
对8个选择图标的整体设计,其实就是一个ul列表.对其进行定位,长度,宽度的设置.
```css
.recommend .recommend_banner .banner_center .nav {
  position: relative;
  width: 100%;
  height: 20px;
  position: absolute;
  bottom: 134px;
}

.recommend .recommend_banner .banner_center .nav .bottom {
  height: 20px;
  width: 224px;
  margin: 0 auto;
}
```
下面是选择图标的引入,对于a标签我通常会转化成块来进行处理,因为内联标签是不允许设置长和宽的,这对背景图的引入来说是非常不友好的.用雪碧图进行图标的引入需要设置引入图标的大小及其在雪碧图中的位置
```css
.recommend .recommend_banner .banner_center .nav .bottom a {
  display: block;
  float: left;
  width: 20px;
  height: 20px;
  background-image: url(../img/index.png);
  background-position: -26px -100px;
  opacity: 0.8;
  margin-left: 8px;
}
```
选择图标在鼠标选中的时候,有一个hover效果,这个就是通过引用雪碧图中的配套图标达到相应效果的.opacity 是目前第一次接触,他控制这标签的透明度,从 0 - 1 透明度以此减小.
```css
.recommend .recommend_banner .banner_center .nav .bottom a:hover {
  width: 20px;
  height: 20px;
  background-image: url(../img/index.png);
  background-position: 0 -100px;
  opacity: 0.8;
}
```
下面设置轮播图左右变化的箭头,因为左右原理相同,所以只拷贝左侧的代码,同样是进行雪碧图的引用,定位.
```css
.recommend .recommend_banner .banner_center .nav .left {
  display: block;
  width: 30px;
  height: 64px;
  background-image: url(../img/index.png);
  background-position: -82px -145px;
  position: absolute;
  left: 0;
  bottom: 108px;
}
.recommend .recommend_banner .banner_center .nav .left:hover {
  display: block;
  width: 30px;
  height: 64px;
  background-image: url(../img/index.png);
  background-position: -161px -145px;
  position: absolute;
  left: 0;
  bottom: 108px;
}

```
设置完这些以后,center就做完了,
## 3.下面进行left的制作
 left正是有前面 结构分析是所提到的,有两级菜单,我们只进行一级菜单的制作.一级菜单由li列表组成的,li标签在嵌套了一些a标签
因为结构相同,只拷贝了  第一列的HTML 结构
```html
<ul>
          <li>
            <a href="">手机</a>
            <em></em>
            <a href="">运营商</a>
            <em></em>
            <a href="">智能数码</a>
          </li>
</ul>
```
先设置recommend_left的大小,背景颜色,令left浮动在左边

```css
.recommend .recommend_banner .banner_left {
  width: 190px;
  background-color: #252221;
  float: left;
}
```
下面设置菜单额每一行,其实就一每一列的高度,行高,字体大小等

```css
.recommend .recommend_banner .banner_left li {
  height: 32px;
  font-size: 13px;
  line-height: 32px;
  padding: 0 8px 0 10px;
}
```
当鼠标移动到每一列的时候,会产生hover效果,这个效果是字体颜色变黑,背景颜色变白这两种效果同时发生作用.
在此同时,鼠标移到选项上面的时候,字体颜色再一次发生变化,变成了橘黄色 .我们会在后面再次设置字体颜色的hover效果,对前面的黑色字体颜色的覆盖

```css
.recommend .recommend_banner .banner_left li:hover {
  background-color: #ffffff;
}
.recommend .recommend_banner .banner_left li:hover a {
  color: #333333;
}
```

如果单纯的对  li:hover 是无法对字体颜色产生效果的,必须在hover下对a标签进行选择,在设置字体颜色.(这也是我本期制作最大的收获).

设置当没有hove时字体的颜色-白色

```css
.recommend .recommend_banner .banner_left li a {
  color: #ffffff;
}
```
下面设置字体颜色-橘黄色 hover效果

```css
.recommend .recommend_banner .banner_left li a:hover {
  color: #ff6600;
}
```
最后,我们可以看得到a标签之间有一条灰色的竖线,我的第一想法通过添加左右边框来实现这个效果,然而水平有限,没能搞出来.我看了一下官方的做法是在a标签之间添加一个em标签,通过设置em标签的背景颜色,大小,宽度来实现这个效果.

```css
.recommend .recommend_banner .banner_left em {
  height: 12px;
  width: 1px;
  background-color: #d8d8d8;
  margin: 0 5px -2px 3px;
  display: inline-block;
  opacity: 0.4;
}
```
左边就制作完了,接下来进行right的制作
## 4.下面进行right的制作
right分为三部分,前面已经分析过了.
先对整体进行设置,宽度,背景色,圆角等

```css
.recommend .recommend_banner .banner_right {
  width: 170px;
  height: 482px;
  position: absolute;
  top: 0;
  right: 0;
  background-color: #ffffff;
  border-radius: 4px;
}
```

第一部分又可以细分为三部分,上面的头像,一句话,中间的两个a链接,区别是一个内嵌p标签,一个是图标,下面是两个类似的图标.
设置第一部分的大小,边框,另文本居中

```css
.recommend .recommend_banner .banner_right .signin {
  width: 170px;
  height: 155px;
  padding: 11px 0 2px 0;
  border-bottom: 1px solid #f2f2f2;
  text-align: center;
}
```
下面进行登录部分的制作

```html
 <a href="" class="headportrait"></a>
          <p>Hi,你好</p>
```
a链接引入图标,

```css
.recommend .recommend_banner .banner_right .signin .headportrait {
  display: inline-block;
  background-image: url(../img/index.png);
  background-position: -93px -24px;
  width: 52px;
  height: 52px;
}
```
设置p标签的大小以及位置
```css
.recommend .recommend_banner .banner_right .signin p {
  margin: 8px auto 0;
  font-size: 12px;
}
```
第一部分接下来的两块都是div标签嵌套两个a标签,进行雪碧图的引用,较为简单就不多说了.
中间的这一部分,他其实是有一个js效果,就是区域中间的三句话不停的变换.我们用纯HTML和CSS3的话只能实现这个静态效果.不停变换的这些内容其实已经写在了页面之中,不过是因为添加了溢出隐藏,导致我们前端只能看到想让你看到的内容,而在控制台就可以看到全部的内容.
我们只做出来静态效果就ok
设置区域的大小,让溢出隐藏

```css
.recommend .recommend_banner .banner_right .hot {
  width: 150px;
  height: 145px;
  margin: 11px 10px 11px 10px;
  overflow: hidden;
}
```
设置每句话所占的区域大小,同样溢出隐藏

```css
.recommend .recommend_banner .banner_right .hot li {
  font-size: 12px;
  width: 150px;
  height: 48px;
}
.recommend .recommend_banner .banner_right .hot li p {
  width: 150px;
  height: 40px;
  overflow: hidden;
  word-break: break-all;
}
```
注意到每一句话前面都有一个 [热门] 并且颜色是橘黄色的,只要添加一个span标签就可以,很简单,不多说了.而且当鼠标选中这些话的时候有变色效果,添加一个hover就行,也很简单

我们进行最后一部分的制作.这一块是由一个列表构成的,li中右包含了一个矢量图标和一个p标签.

```html
<li>
              <a href="">
                <span class="iconfont icon-huafei"></span>
                <p>话费</p>
              </a>
            </li>
```
我们先设置li的大小,并且为了使列表能够排列成两排,我们添加了浮动.给li添加边框我们只添加了一面,这么做的好处是是的每一区域的边框都是1px宽

```css
.recommend .recommend_banner .banner_right .kuaijie li {
  float: left;
  width: 55px;
  height: 72px;
  border-width: 0 1px 1px 0;
  border-style: solid;
  border-color: #f2f2f2;
}
```
接下来就对li中的内容进行,位置,大小的调整

```css
.recommend .recommend_banner .banner_right .kuaijie li a {
  display: block;
  width: 55px;
  height: 72px;
  line-height: 24px;
  text-align: center;
  margin: 10px 0 0 0;
}
.recommend .recommend_banner .banner_right .kuaijie li a span {
  font-size: 24px;
  color: #ff6600;
}
.recommend .recommend_banner .banner_right .kuaijie li a p {
  font-size: 12px;
}
```
同样的p标签同样有一个hover效果,不过这个效果不仅仅是鼠标移动到文字上面才有的,而是当鼠标移动到li区域中就已经产生了.所以我们将a的设置的和li相同大小.
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200524220637466.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L014X3pI,size_16,color_FFFFFF,t_70)
这块区域的制作就到这里了
