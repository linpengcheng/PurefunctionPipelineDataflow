# 一学就会，一用就废！评论DBOS：一个面向数据库的操作系统（兼论：如何预防应用我的理论时出现偏差呢?）
———— 评《80岁Postgres创始人、数据库领域“祖师爷”想颠覆数据库设计：不推翻下当前技术，不足以谈人生》

版权所有 © 2023.12.27 林鹏程，保留所有权利。
（2023.12.27首发于微博）

根据[DBOS的博客](https://dbos-project.github.io/), 
他的第一篇论文[《TabulaROSA: Tabular Operating System Architecture for Massively Parallel Heterogeneous Compute Engines (HPEC 2018.09.25)》](https://ieeexplore.ieee.org/document/8547577)
和我的仓库/车间模型(2018)相差比较大.

第二篇论文[《DBOS: A Proposal for a Data-Centric Operating System (arXiv 2020.07.21)》](https://arxiv.org/abs/2007.11112)
和我的仓库/车间模型(2018)论述一致,我认为他应该是参考了我的理论.

> Stonebraker 与 Zaharia 等人共同撰写的论文对此做出具体解释，“
> 
> - 仓库: 所有操作系统状态都应统一表示为数据库表，
> - 车间: 并应通过来自其他无状态任务的查询对该状态进行操作。
>
> 这样的设计能够让操作系统拥有更灵活的扩展和开发空间。无需对整个操作系统进行重构、
> 无需检查和调度系统状态、也无需停机即可升级组件；
> 
> - 调度器: 同时配合机器学习来管理决策，并实现复杂的安全功能。”

我认为他在调度器方面投机取巧了, 我的理论所用的动态树形甘特图基于运筹学, 
实现起来比较困难但更高效.

DBOS在抽象层使用仓库/车间模型, 但从他的2022.09.03的博客
《DBOS: A Database-Oriented Operating System》上看, 
他的实现偏离了仓库/车间模型及其原则, 究其原因, 
应该是对仓库/车间模型理解不够透彻, 
不自觉地滑向贯用的传统DB和OS系统构造方法.

上一个犯同样错误案例是Apple从抄作业的M1扩展到M1 Ultra所犯的错误!

为什么会有这种 **“一学就会，一用就废”** 的现象? 原因很简单，基础不牢固，
没有把最简单、最乏味的纯函数管道数据流的5个基本组件练成本能，形成正确的思维方式。
这就是俗话所说的：练拳不练功，到老一场空；看人挑担很轻松，自己挑担压断腰；一学就会，一用就废！

如何预防应用我的理论时出现偏差呢?
我的理论简单统一，浑然一体,由下面七个部份组成：

1. 数学原型: 简单经典的"水池进/排水"模型
2. 编程: 纯函数管道数据流, 5个基本的纯函数管道数据流组件
3. 架构: 仓库/车间模型
4. 原则: 基于原则的方法学, 10个原则
5. 质控: 简单的山峦图或等高线图、纯函数比例
6. 美学: 简单、统一、有序、对称、明确
7. 道家仙派科研方法学

本理论的每个组成部分都完美地应用和演示了其他组成部分， 是一个实用的、完整的、系统的理论体系。
把工作成果与这七个部份互相印证, 可以预防出现偏差!

我认为他应该再努力理解我的理论, 主要多阅读下面的文章:

- 2018.03.18, [The Math-based Grand Unified Programming Theory: The Pure Function Pipeline Data Flow with Principle-based Warehouse/Workshop Model](https://github.com/linpengcheng/PurefunctionPipelineDataflow)

- 2021.11.15, [OS kernel as Hardware: The future OS kernel will be a data-oriented scheduler (with Computer hardware and software integration architecture diagram)](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/OS_as_DB_en.md)

- 2021.07.28, [Why my "warehouse/workshop model" can achieve high performance and low power consumption (take Apple M1 chip, Intel AVX-512, Qualcomm as examples)](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/why_wwmodel_fast_en.md)

- [Microsoft's AI computing platform Singularity's architecture has plagiarized my Warehouse/Workshop Model](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/Follower_MS_Singularity_Architecture_en.md)

- [Apple M1 Ultra is a mistake](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/SuccessStory.md#M1-Ultra-is-a-mistake)

- [Traditional IT theory (OO, FP and hardware architecture, etc.) VS. Warehouse/Workshop Model](https://github.com/linpengcheng/PurefunctionPipelineDataflow#Traditional-OO-and-FP-architecture-VS-Warehouse-Workshop-Model)

- [Success Story](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/SuccessStory.md)

```
Traditional IT theory (OO, FP and hardware architecture, etc.) 
are pseudoscience. they belong to what physicist Wolfgang 
Pauli said "Not Even Wrong".

It is the perfect theory if a theory is based on mathematics 
and meets the five basic principles of "Simplicity, Unity, 
Order, Symmetry and Definiteness" in science, industry 
and aesthetics.  

Keep it Simple and Unified.

Computer science is essentially a management science, 
and vice versa.

Software and hardware are factories that manufacture data, 
so they have the same "warehouse/workshop model" and 
management methods as the manufacturing industry.

        ---- Lin Pengcheng
```
