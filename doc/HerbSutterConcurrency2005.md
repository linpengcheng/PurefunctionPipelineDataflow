# 评：《免费午餐结束：软件开发从根本转向并发编程》

版权所有 © 2021-06-28 林鹏程， 保留所有权利。

ISO C++ 标准委员会主席和Microsoft软件架构师 Herb Sutter
于2005年发表在《Dr. Dobb's Journal》和《C/C++ Users Journal》，
这篇文章主要提出以下观点和问题：

- 从英特尔和 AMD 到 Sparc 和 PowerPC，
  主要的处理器制造商和架构已经耗尽了空间，
  他们转向大规模超线程和多核架构
  
- 缓存是王道， 空间就是速度 
 
- 并发是编写软件方式的下一个重大革命

- 编程语言和系统将越来越被迫处理好并发性。

- 并发性的最大成本是，并发确实很难：编程模型，
  即程序员头脑中的模型，他需要可靠地推理他的程序，
  比连续控制流要困难得多。
  
对于这些问题，我的“纯函数管道数据流和基于原则的仓库/车间模型”
就是最简单、最高效的、最好的并发编程模型，
基于动态树形甘特图算法的动态规划调度器，
避免冲突、竞争，最小化协调、通信等问题，
数据存取效率最高,
成为一个性能、灵活性、扩展性、简单性最佳的系统。

Apple M1 芯片及 MacOS 虽然尚未完全实现“仓库/车间模型”,
但已经成为世界第一了。

我的“仓库/车间模型”解决了困扰 Herb Sutter
和C＋＋几十年的并发编程的最大难题一一并发编程模型，
现在计算机硬件架构和OS都转向或准备转向“仓库/车间模型”，
各语言应紧随历史潮流，把“仓库/车间模型”加语言标准里。
我认为“仓库/车间模型”应进C＋＋标准了。

另外，那个抱着连“所有权和经营使用权”都没搞清楚的、
因错误而复杂的“借贷模型”的Rust语言，
最基本的财务金融概念都没搞清楚，就想自己开银行了，囧。
趁早踢了借贷模型，金融业的花样太多太复杂了，别太勉强了，
改换成简单、实用的“仓库/车间模型”吧。

参考

- [The Free Lunch Is Over, A Fundamental Turn Toward Concurrency in Software](http://www.gotw.ca/publications/concurrency-ddj.htm)

- [Rust: 数学不能救编程，但财务可以](./rust.md)