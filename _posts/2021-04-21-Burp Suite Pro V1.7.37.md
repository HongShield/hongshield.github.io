---
layout:     post
title:      Burp Suite Pro V1.7.37
subtitle:   【web安全】 渗透工具
date:       2021-04-09
author:     HongShield
header-img: img/post-bg-resource.jpeg
catalog: true
tags:
    - 渗透
    - WEB安全
    - 工具
    - 破解
music-id:
---
# Burp Suite Pro V1.7.37

## 概述
&emsp;&emsp;Burp Suite 能高效率地与多个工具一起工作，例如：一个中心站点地图是用于汇总收集到的目标应用程序信息，并通过确定的范围来指导单个程序工作。

&emsp;&emsp;在一个工具处理HTTP 请求和响应时，它可以选择调用其他任意的Burp工具。例如：代理记录的请求可被Intruder 用来构造一个自定义的自动攻击的准则，也可被Repeater 用来手动攻击，也可被Scanner 用来分析漏洞，或者被Spider(网络爬虫)用来自动搜索内容。应用程序可以是“被动地”运行，而不是产生大量的自动请求。

&emsp;&emsp;Burp Proxy 把所有通过的请求和响应解析为连接和形式，同时站点地图也相应地更新。由于完全的控制了每一个请求，你就可以以一种非入侵的方式来探测敏感的应用程序。

&emsp;&emsp;当你浏览网页(这取决于定义的目标范围)时，通过自动扫描经过代理的请求就能发现安全漏洞。

&emsp;&emsp;IburpExtender 是用来扩展Burp Suite 和单个工具的功能。一个工具处理的数据结果，可以被其他工具随意的使用，并产生相应的结果。

## 工具箱
&emsp;&emsp;Proxy——是一个拦截HTTP/S的代理服务器，作为一个在浏览器和目标应用程序之间的中间人，允许你拦截，查看，修改在两个方向上的原始数据流。

&emsp;&emsp;Spider——是一个应用智能感应的网络爬虫，它能完整的枚举应用程序的内容和功能。

&emsp;&emsp;Scanner[仅限专业版]——是一个高级的工具，执行后，它能自动地发现web 应用程序的安全漏洞。

&emsp;&emsp;Intruder——是一个定制的高度可配置的工具，对web应用程序进行自动化攻击，如：枚举标识符，收集有用的数据，以及使用

&emsp;&emsp;fuzzing 技术探测常规漏洞。

&emsp;&emsp;Repeater——是一个靠手动操作来补发单独的HTTP 请求，并分析应用程序响应的工具。

&emsp;&emsp;Sequencer——是一个用来分析那些不可预知的应用程序会话令牌和重要数据项的随机性的工具。

&emsp;&emsp;Decoder——是一个进行手动执行或对应用程序数据者智能解码编码的工具。

&emsp;&emsp;Comparer——是一个实用的工具，通常是通过一些相关的请求和响应得到两项数据的一个可视化的“差异”。

## 使用
&emsp;&emsp;当Burp Suite 运行后，Burp Proxy 开启默认的8080 端口作为本地代理接口。通过设置一个web 浏览器使用其代理服务器，所有的网站流量可以被拦截，查看和修改。默认情况下，对非媒体资源的请求将被拦截并显示(可以通过Burp Proxy 选项里的options 选项修改默认值)。对所有通过Burp Proxy 网站流量使用预设的方案进行分析，然后纳入到目标站点地图中，来勾勒出一张包含访问的应用程序的内容和功能的画面。在Burp Suite 专业版中，默认情况下，Burp Scanner是被动地分析所有的请求来确定一系列的安全漏洞。

&emsp;&emsp;在你开始认真的工作之前，你最好为指定工作范围。最简单的方法就是浏览访问目标应用程序，然后找到相关主机或目录的站点地图，并使用上下菜单添加URL 路径范围。通过配置的这个中心范围，能以任意方式控制单个Burp 工具的运行。 

&emsp;&emsp;当你浏览目标应用程序时，你可以手动编辑代理截获的请求和响应，或者把拦截完全关闭。在拦截关闭后，每一个请求，响应和内容的历史记录仍能再站点地图中积累下来。

&emsp;&emsp;和修改代理内截获的消息一样，你可以把这些消息发送到其他Burp 工具执行一些操作：
你可以把请求发送到Repeater,手动微调这些对应用程序的攻击，并重新发送多次的单独请求。

&emsp;&emsp;[专业版]你可以把请求发送到Scanner,执行主动或被动的漏洞扫描。

&emsp;&emsp;你可以把请求发送到Intruder，加载一个自定义的自动攻击方案，进行确定一些常规漏洞。

&emsp;&emsp;如果你看到一个响应，包含不可预知内容的会话令牌或其他标识符，你可以把它发送到Sequencer 来测试它的随机性。

&emsp;&emsp;当请求或响应中包含不透明数据时，可以把它发送到Decoder 进行智能解码和识别一些隐藏的信息。

&emsp;&emsp;[专业版]你可使用一些engagement 工具使你的工作更快更有效。

&emsp;&emsp;你在代理历史记录的项目，单个主机，站点地图里目录和文件，或者请求响应上显示可以使用工具的任意地方上执行任意以上的操作。

&emsp;&emsp;可以通过一个中央日志记录的功能，来记录所单个工具或整个套件发出的请求和响应。

&emsp;&emsp;这些工具可以运行在一个单一的选项卡窗口或者一个被分离的单个窗口。所有的工具和套件的配置信息是可选为通过程序持久性的加载。在Burp Suite 专业版中，你可以保存整个组件工具的设置状态，在下次加载过来恢复你的工具。

## 外部链接

- [官方网站](https://portswigger.net/burp)
- [Burp Suite 支持中心](https://portswigger.net/support)包含大量有关使用 Burp Suite 的文章和社区讨论。
- [Burp 测试方法](https://portswigger.net/support/burp-testing-methodologies)解释了使用 Burp Suite 测试各种 Web 应用程序漏洞的方法。
- [知识库]()包含 Burp Scanner 可以检测到的所有问题的定义。

摘自：[百度百科](https://baike.baidu.com/item/burpsuite/5971741?fr=aladdin)

下载地址：[Burp Suite Pro V1.7.37](https://pan.baidu.com/s/180LDTxv_wGCts4Drw2N83w) 提取码： <kbd>ebig</kbd> 