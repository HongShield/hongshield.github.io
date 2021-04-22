---
layout:     post
title:      SuNing Index Creat -1
subtitle:   HTML5 + CSS3
date:       2020-05-20
author:     HongShield
header-img: img/post-bg-h5c3.jpg
catalog: true
tags:
    - HTML5
    - CSS3
---
# 前言
&emsp;&emsp;最近处于一个特殊的时期，由于一个偶然的机会学习了前端，在很短的时间内学完了HTML5+CSS3，进入了JS的学习，感觉到学习速度太快对我来说不是一件好事，于是我暂停了JS的学习，打算完成一到两个项目实战。第一个项目就是用纯H5+C3实现苏宁易购官网的页面制作。
# 一、准备工作
## 1、结构分析
&emsp;&emsp;我将整个页面分为了7大块，导航栏，中间的5块内容，以及页面底部。当然这并不是绝对的，在我们需要的时候随时会进行调整。

## 2、图片素材
 - 将苏宁首页进行截图保存，将来用ps进行测量，切片等。
 - 将苏宁网页上的一些图片扒下来。
 - 在[阿里巴巴矢量图标库](https://www.iconfont.cn/)中寻找一些需要的矢量图标。
 （没有设计搞真难啊）
 # 二、导航栏制作
 ## 1、框架分析
 - 首先分析结构，可以分为两个区域左边和右边
![导航栏](https://img-blog.csdnimg.cn/20200518205107832.png#pic_center)
 - 因此我们可以将这两个区域放在一个容器之内。先编写HTML框架，之后再编写CSS样式。HTML相当于我们建筑的四梁八柱，人体的骨架，是主题结构，CSS相当于装饰品，血肉。
 - 导航栏分为两级菜单，我们只做一级菜单，也就是鼠标没有移动上去的时候所看到的内容
 - 对于一些选项来说，当鼠标移动上去的时候，会显示一个下拉菜单，所以我又在**li**标签内嵌套了div标签。为了不使代码冗余，我只拷贝了一部分代码。
```html
<div class="nav">
    <div class="nav_left">
      <ul>
        <li>
          <div>
            <a href="#">网站导航
            </a>
          </div>
        </li>
      </ul>
      </div>
      <div class="nav_right">
      	<ul>
	        <li>
	          <a href="#">企业采购
	          </a>
	        </li>
		</ul>
    </div>
  </div>
```
- 未添加任何css样式时候的导航栏左面区域
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200518212311404.png )
## 2.接下来我们消除一些标签的默认样式，同时通过添加样式来达到我们想要的效果。
### 1. 消除标签的默认样式

```css
*{margin: 0;padding: 0;}
ul{list-style: none;}
img{display: block;}
h1,h2,h3{font-size: 16px;font-weight: normal;} 
a{text-decoration: none;color: #333333;} //链接的样式
body{font-family: Arial;} // 字体设置

.l{float: left;}		//左浮动
.r{float: right;}		//右浮动
.clear::after{content: "";display: block;clear: both;} // 清除浮动
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519123035952.png)
### 2. 为每一个区域起一个名字，方便选择器进行选择。
### 3. 添加CSS样式
#### 1）首先我要让选项横向排列，采用左浮动

```css
.nav .nav_left ul li {
  float: left;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051912445499.png)
#### 2)容器的制作
&emsp;&emsp;用PS测量出容器高度，宽度我们设置成自适应，添加好背景色后，添加下边框，1px，

```css
.container_fluid {
  width: 100%;
  background: #f5f5f5;
  border-bottom: 1px #eeeeee solid;
}
```

#### 3）令菜单水平
&emsp;&emsp;菜单分为左右两块，左div设置左浮动，li设置左浮动，右div设置右浮动，li设置左浮动（如果此处设置右浮动，第一个li标签在最右边）。

#### 4）使菜单的每一项之间保持相应的距离
&emsp;&emsp;可以通过测量或者感觉来进行调整，比如margin，padding。左菜单我给每一个li设置了固定宽度，另li中的div进行居中。而右菜单设置了根据div内容自适应，为了不使div紧挨在一块，我添加了padding。

```css
#head .nav .nav_left ul li {
  float: left;
  width: 104px;
  height: 33px;
  font-size: 14px;
}

#head .nav .nav_left ul li div {
  text-align: center;
}
```
#### 5）调整字体大小，颜色
根据“设计稿”进行字体大小，颜色的调整。

```css
#head .nav span {
  font-size: 10px;
  color: #cfcad8;
}
```
#### 6）添加矢量图标
&emsp;&emsp;下载好矢量图标以后，进行引用，一定要注意路径。矢量图标是一种字体，因此可以用font-size ，color 进行大小颜色的调整

通过给span标签添加选择器进行引入。

```css
<li>
            <div>
              <a href="#">网站导航
                <span class="iconfont icon-ai-arrow-down"></span></a>
            </div>
          </li>
```
#### 7）设置 hover 属性。
&emsp;&emsp;菜单的选项，当我们把鼠标移动上去的时候，字体会变色，并且背景会变化成白色，并出现一个二级菜单。我们只做一个字体，背景变色效果。

```css
#head .nav .nav_left ul li:hover {
  background-color: white;
}
#head .nav .nav_left ul li a:hover {
  color: #ff6600;
}
```
&emsp;&emsp;这么设置之后，我们发现所有的选项，当hover的时候背景都发生了变化，而没有二级菜单的选项的背景色并没有变化，我们可以再次添加hover，设置为原来的背景色对当前的hover覆盖，已达到我们想要的效果。

```css
#head .nav .nav_right ul .no_hover:hover {
  background-color: #f5f5f5;
}
```
&emsp;&emsp;或者也可以通过伪类选择器达到这一效果，（不过我对选择器的使用不熟悉）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200520150220824.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200520150125258.png)
 
## 3、小结
&emsp;&emsp;1.在导航栏的制作过程中，出现了许多的小问题，例如div标签的重叠问题。我的解决方式就是删除div标签的固定宽度，设置为自适应，给他的父容器li标签加上了宽度，另div居中。还有一些语法的使用细节。

&emsp;&emsp;2.在添加样式的过程中，选择器的使用方式是多样的，给不同的标签添加选择器都可以起到同样的效果。但是由于选择器使用的不熟练，将一些样式直接加在了标签中，这是非常不合格的。在真正的开发过程当中，CSS和HTML一定是分开写的，这样便于代码的维护。

&emsp;&emsp;3.在制作导航栏的过程中应该设置手性的，但是添加了a链接之后默认出现了手性。

&emsp;&emsp;4.导航栏的制作就告一段落了。我只制作了一级菜单，二级菜单的制作将会等到正在页面制作完成之后在进行制作。

*[hover]: 鼠标移动上去后产生的变化
