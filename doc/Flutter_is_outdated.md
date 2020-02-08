# Google Flutter is a technology I created and eliminated
# Google Flutter是一种我原创并已淘汰的技术

Copyright © 2020.02 Lin Pengcheng. All rights reserved.

版权所有 © 2020.02 林鹏程， 保留所有权利。

Google Flutter 是安卓（andriod）手机新一代的界面框架，并开始延伸到PC桌面端和Web端.

最近看到"有个梨UGlee"的微博说, Flutter的方法是UI=f(state),
我发现居然是我五六年前开发[林鹏程财务分析软件v0.10.2015.6.1](https://github.com/linpengcheng/fa)时,
使用clojure-clr写基于.net winform界面时使用的方法. 

我用clojure-clr动态构造.net winform界面时, 经常使用多线程或异步来构造界面, 
比Flutter简单方便强大多了，数据驱动，也更贴近原生。

不过我美工不好, 界面都是原生朴素的界面. 

因为五六年前纯函数管道数据流还没有完整的体系化, 
只处于传统方法和[纯函数管道数据流](https://github.com/linpengcheng/PurefunctionPipelineDataflow)方法的中间状态.现在这种方法已淘汰了.

另外, Google Flutter的方法UI=f(app-state)和我的UI=f(winform-state)还是有差别的,
我认为app-state范围过大而不必要, 且不能实现UI和逻辑的完美分离.

----

[纯函数管道数据流](https://github.com/linpengcheng/PurefunctionPipelineDataflow)善长数据变换，
我也把所有编程的问题归结为数据变换的问题，实现简单性和统一性的完美结合。

现在,我开发财务分析软件使用Web UI, 因为Web UI只是字符串而已, 更简单, 更适合用纯函数管道数据流构造UI. 
用IT流行的表达方式来说：UI即数据（UI as Data）.

----

"有个梨UGlee"的微博说Google剽窃, 如果Google没有声明"自主创新", 也没把这技术申请为自家专利, 不能说它剽窃, 但完全没有提及过原创作者就不厚道了.
另注: 美国专利法是发明时间优先，而不是申请时间优先。

和中科院木兰编程语言之流的项目比,好一点,也只好了一点.
不能对国内科研项目的评价高标准，对国外项目低标准，双标做法可不行.
两者都一起批了.
