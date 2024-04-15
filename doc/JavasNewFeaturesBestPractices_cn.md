# Java的新特性系统性最佳实践: Java弃暗投明，投奔我的理论!

版权所有 © 2024.04.15 林鹏程， 保留所有权利。

从Java 8开始，Java开始改变其笨重缓慢的形象，努力增加新特性，提高性能，
但由于Java的主要应用领域是企业级应用，更新编程语言的策略比较保守，
大多还守着Java 8，应用众多新特性的企业或个人得不多，只单独新特性的介绍，
没有系统性最佳实践指南之类的文章，人们还不知道Java已弃暗投明，放弃OOP，投奔我的理论——
[《基于数学的大统一编程理论：纯函数管道数据流和基于原则的仓库/车间模型》](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/Readme_Chinese.md) ！

- 车间: Stream (JDK 8～9)，Stream Gatherers(JDK 22)
  
  Stream是对象风格的管道操作，
  用来构造 **“车间”** 生产数据的流水线。
  
- 仓库: Records (JDK 14～16)

  - Record是不可变数据类型，被当作数据载体，
    主要用于存储、保存数据，并且没有其它额外自定义行为的场景下。
    它很适合用来作为 **“仓库”** ，当然如果有特殊需求，
    其他Java类更适合的话，也可以适用，我的理论有极强的兼容性。
  - 类：在我的理论中类主要作为命名空间组织代码，
  　或兼容OOP的概念，以使用传统Java代码。
  - 对象：在我的理论中不需要对象，这用于兼容OOP的概念，
  　以使用传统Java代码。
  
- 调度器: 虚拟线程 (JDK 19～21)，结构化并发 (JDK 19～22)

　- 结构化并发: 用来构造 **“调度器”** 算法：动态树形甘特图（运筹学）。
　- 虚拟线程: 在给车间分配任务后，用来运行任务。

- JEP 467: Markdown 文档注释

  该特性使用我2019-02-17的原创方法[《Markdown Literary Programming that don't break the syntax of any programming language》 ](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/markdown_literary_programming.md) ,
  我的方法更简单、灵活、可视化、可扩展，适用所有编程语言和标记语言。
  
  Demo: [preview in Notepad++](https://github.com/linpengcheng/ClojureBoxNpp)

- 其他新特性

  主要是本机编译、本机代码交互、语法增强、工具增强，
  这些与编程范式没关系，不讨论。

综上所述，Java新特性的发展表明，Java已弃暗投明，放弃`OOP`，
投奔我的理论——[《基于数学的大统一编程理论：纯函数管道数据流和基于原则的仓库/车间模型》](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/Readme_Chinese.md) ！
再结合Java大力发展本机编译、本机代码交互，Java初创时的核心理念`OOP`和`虚拟机`已经被抛弃了。

为什么Java弃暗投明，投奔我的理论? 原因如下:

- Java的主要应用领域是企业级应用软件，从参考模型上看，
  我的仓库/车间模型与企业级应用软件天然直接对应，简单清晰，
  比当前主流的 OO、FP、命令式编程优越多了。
  
- 我的文章[《传统IT理论(OO&FP&硬件等IT系统构造方法学)与仓库/车间模型的比较》](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/Readme_Chinese.md#Traditional-OO-and-FP-architecture-VS-Warehouse-Workshop-Model-CN) 
  指出我的仓库/车间模型基于数学模型，对当前主流的
  OO、FP、命令式编程这类 **伪科学** 来说，那是降维打击。

- 我的仓库/车间模型以数据为中心，这思想与数据库的思想是一致的，
  因此，数据库厂商就是我的理论的天然盟友，Java 背后的老板 Oracle
  是最大的数据库厂商，让Java转向我的理论发展，那是很自然的选择.
  
- 我在文章[《我的理论估计全世界有10万个高水平的关注者（兼论：最权威的同行评审）》](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/estimated_100k_high_level_followers.md)
  指出我的仓库/车间模型已在最底层的CPU/SoC芯片和计算机硬件架构
  取得绝对胜利，在IT领域，最底层技术决定上层技术，因此，我的理论在
  在IT领域中OS，DB，编程语言，应用软件开发等所有层次取得绝对胜利
  只是时间问题，这是必然的，Java语言的改变只是一个开始。
