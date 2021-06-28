＃　评：《免费午餐结束：软件并发的根本转变》

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
成为一个性能、灵活性、扩展性、简单性最佳的系统。

Apple M1 芯片及 MacOS 虽然尚未完全实现“仓库/车间模型”,
但已经成为世界第一了。

参考

- [The Free Lunch Is Over, A Fundamental Turn Toward Concurrency in Software](http://www.gotw.ca/publications/concurrency-ddj.htm)
