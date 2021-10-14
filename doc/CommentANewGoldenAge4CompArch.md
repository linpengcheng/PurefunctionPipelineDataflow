# 评: 两位图灵奖得主 David Patterson 与 John Hennessey 共同发表的“计算机架构的新黄金十年”

版权所有 © 2021.10.14 林鹏程， 保留所有权利。

> 在 2019 年 2 月的 ACM 通讯上，计算机架构宗师、架构领域“圣经”著作
> 《计算机架构与量化研究方法》的作者 David Patterson 与 
> John Hennessey 共同发表了一篇重磅论文：《计算机架构的新黄金十年》，
> 阐述了他们对未来十年计算体系结构发展的分析和展望。论文指出，
> 以硬件为中心、针对特定领域和用途设计的架构（DSA）将提供
> 显著的性能和能效收益，在摩尔定律走向终结的同时为计算机带来
> 新的活力与发展机遇。

## 评 

- 仅仅是发现目前市场上存在的DSA（Google TPU 等）的优势，
  预测DSA将产生显著的性能和能效收益, 但没有说明应该怎么采用什么架构
  去组织、协调、控制这些 DSA 完成任务， 因为专用的芯片应用范围很有限,
  必须设计一种全新的架构来组合通用CPU与多种DSA,以共同完成任务. 即: 
  没有提出一个新计算机体系结构来解决问题。

- 如果是DSA，那应该引用 Google TPU, ASIC 相关的文献才对.

- 如果是组织这类DSA以新计算机体系结构完成任务, 那应该引用我的
 《大统一编程理论：纯函数管道数据流和基于原则的仓库/车间模型》.

## 结论

这两位图灵奖得主在这篇报告并没有发表出新观点，
也没有给出解决方案，没有觉得有什么创新,
不明白那么多人会引用这篇文章，难道仅仅因为是名人效应。

## 参考

- [为多样性算力软件开发铺就平坦大道：华为北冥融合架构全面解析](https://www.infoq.cn/article/h8yElVd995fv4dCvZiuB)

- [A New Golden Age for Computer Architecture, By John L. Hennessy, David A. Patterson, Communications of the ACM, February 2019, Vol. 62 No. 2, Pages 48-60, 10.1145/3282307](https://cacm.acm.org/magazines/2019/2/234352-a-new-golden-age-for-computer-architecture/fulltext)
