# Google Flutter is a similar technology I created and eliminated
# Google Flutter是一种我曾经原创并已淘汰的类似技术

Copyright © 2020.02 Lin Pengcheng. All rights reserved.

版权所有 © 2020.02 林鹏程， 保留所有权利。

Google Flutter 是安卓（andriod）手机新一代的界面框架，并开始延伸到PC桌面端和Web端.
Flutter组件采用现代响应式框架构建，这是从React中获得的灵感，中心思想是用组件(widget)构建你的UI。 
[参考:百度百科: Flutter](https://baike.baidu.com/item/Flutter/22498985)

最近看到"有个梨UGlee"的微博说, Flutter的方法是UI=f(state),
我发现居然是我五六年前开发[林鹏程财务分析软件v0.10.2015.6.1](https://github.com/linpengcheng/fa)时,
使用clojure-clr写基于.net winform界面时使用的方法. 

Flutter的第一个版本被称为“Sky”，运行在Android操作系统上。它是在2015年5月3日Dart开发者峰会上亮相的,
但它只是一个概念演示版,根本无法使用.直到2018年2月27日才在2018世界移动大会发布Beta1版.
1.0版本于2018年12月5日(北京时间)发布.

[林鹏程财务分析软件v0.10.2015.6.1](https://github.com/linpengcheng/fa)是2015年6月1日发布, 
但这是一个完整的产品, 而不仅仅是UI概念演示版, 另外, 因为我是个人业余开发, 开发速度很慢,
整个项目用了4年多, 实际上我的UI实现应该早了几年, 在2013年左右,有在QQ群"Clojure"里讲过我的技术实现.
可以另外参见我在2018年4月19日的博文[C#愚蠢到我不能理解，兼论UI构造方法。](./c%23stupid.md)

因为同时期的“Sky”资料找不到, 就和最新的Flutter比较一下差异:

1. 我用clojure-clr动态构造.net winform界面时, 经常使用多线程或异步来构造界面, 比Flutter简单方便强大多了，数据驱动，也更贴近原生。
基于一个包括全部界面组件状态atom数据，所有的界面组件围着atom, 交互运行。 很久以后，我看到"Clojure编程乐趣"这本书上有Alan Perlis
的一句话。 It’s better to have 100 functions operate on one data structure than 10 functions on 10 data structures. 
这与我的解决方案有异曲同工的思想。我的思想是：所有的组件围着一个atom状态交互，比各个组件管理自己的状态好。 大家是不是觉得很相似。
注：Alan Perlis是首位图灵奖得主、Algol语言(C/C++/Pascal等语言的鼻祖)作者。

2. Flutter的UI表达方式更倾向代码化, 更类似OO写法, 代码嵌套比较深, UI与逻辑混杂在一起, 信息密度太低, 阅读代码时, 难快速了解逻辑,
快速修改代码. 我的UI表达方式更倾向纯数据表达并组合, 直接当函数参数调用,UI和逻辑完全分离, 信息密度高, 逻辑简洁清楚独立, 
阅读和维护轻松.

3. Google Flutter的方法UI=f(app-state)和我的UI=f(winform-state)还是有差别的, 我认为app-state范围过大而不必要, 且不能实现UI和逻辑的完美分离. 

4. 按UI=f(state)思想看，最新的Google Flutter只是传统思想与该思想的夹生饭，思维方式没拐过弯的样子，
和我的方法同时期它的最初版本“Sky”估计更糟糕。我的UI as Data 和已淘汰的数据驱动方法更正宗。 

5. 我美工不好, 界面都是原生朴素的界面.

因为五六年前纯函数管道数据流还没有完整的体系化, 
只处于传统方法和[纯函数管道数据流](https://github.com/linpengcheng/PurefunctionPipelineDataflow)方法的中间状态.现在这种方法已淘汰了.

----

[纯函数管道数据流](https://github.com/linpengcheng/PurefunctionPipelineDataflow)善长数据变换，
我也把所有编程的问题归结为数据变换的问题，实现简单性和统一性的完美结合。

现在,我开发财务分析软件使用Web UI, 因为Web UI只是字符串而已, 更简单, 更适合用纯函数管道数据流构造UI. 
用IT流行的表达方式来说：UI即数据（UI as Data）.

我的项目代码是闭源, 但大概的思路还是可以说一下:

- 把UI资源文件用数据结构表达, 用代码操纵, 比UI资源文件更灵活.
- Clojure语言的HTML DSL: [hiccup](https://github.com/weavejester/hiccup)
- Clojure语言的SQL DSL: [honeysql](https://github.com/jkk/honeysql)
- 声明式图形库: [Vega](https://vega.github.io/)
- 数据驱动的图形库: [D3.js](https://d3js.org/)
- 把数据式图形库伪装成面向对象的R语言图形库: [ggplot2](https://ggplot2.tidyverse.org/)
