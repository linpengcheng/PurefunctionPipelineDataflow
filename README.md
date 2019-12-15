# The Pure Function Pipeline Data Flow v2.0
# 纯函数管道数据流  v2.0

Copyright © 2018 Lin Pengcheng. All rights reserved.

版权所有 © 2018 林鹏程， 保留所有权利。

## Table of Contents
- [My and Other People's Related Views](#My-and-Other-Peoples-Related-Views-我的和其他人的相关观点)
- [Summary](#Summary-概述)
- [Classical Model](#Classical-Model-经典模型)
  - [Warehouse/Workshop Model](#Warehouse-Workshop-Model-仓库车间模型)
- [Disadvantages of FP and OO](#Disadvantages-of-FP-and-OO-函数式编程和面向对象编程的缺点)
- [The difference between it and middleware](#The-difference-between-it-and-middleware-它和中间件的区别)
- [The difference between it and Rx](#The-difference-between-it-and-Rx-它和Rx的区别)
- [The difference between it and traditional unix-like pipe operator in FP language](#The-difference-between-it-and-traditional-unix-like-pipe-operator-in-FP-language-它和传统FP语言里的类unix管道操作符的区别)
- [Basic quality control](#Basic-quality-control-基本质量控制)
- [Code Example](#Code-example-代码范例)
- [Basic construction method](#Basic-construction-method-基本构造方法)
  - [1. Pipeline Component](#Pipeline-Component-管道组件)
  - [2. Branch](#Branch-分支)
  - [3. Feedback circuit (reflow, whirlpool, recursive)](#Feedback-Circuit-反馈电路)
  - [4. shunt (concurrent, parallel)](#Shunt-分流)
  - [5. Confluence(reduce)](#Confluence-合流)
- [Tao](#Tao-道)
- [Great Historical Significance](#Great-Historical-Significance-重大历史意义)
- [Postscript](#Postscript-后记)
- Appendix:
  - [(Chinese) Simplicity and Unity ---- Grand Unified Theory, Lisp(Clojure) and Pure Function Pipeline Dataflow](doc/Simplicity_and_Unity.md)
  - [Clojure is a FP based on RMDB.](doc/Clojure_is_FP_based_on_RMDB.md)
  - [Everything is RMDB.](doc/Everything_is_RMDB.md)
  - [Implement relational data model and programming based on hash-map (NoSQL)](doc/relational_model_on_hashmap.md)
  - [Markdown Literary Programming that don't break the syntax of any programming language](doc/markdown_literary_programming.md)
  - [Other Articles Table of Contents](#Other-Articles-Table-of-Contents-其他文章目录)

----

## 目录
- [我的和其他人的相关观点](#My-and-Other-Peoples-Related-Views-我的和其他人的相关观点)
- [概述](#Summary-概述)
- [经典模型](#Classical-Model-经典模型)
  - [仓库/车间模型](#Warehouse-Workshop-Model-仓库车间模型)
- [函数式编程和面向对象编程的缺点](#Disadvantages-of-FP-and-OO-函数式编程和面向对象编程的缺点)
- [它和中间件的区别](#The-difference-between-it-and-middleware-它和中间件的区别)
- [它和Rx的区别](#The-difference-between-it-and-Rx-它和Rx的区别)
- [它和传统FP语言里的类unix管道操作符的区别](#The-difference-between-it-and-traditional-unix-like-pipe-operator-in-FP-language-它和传统FP语言里的类unix管道操作符的区别)
- [基本质量控制](#Basic-quality-control-基本质量控制)
- [代码范例](#Code-example-代码范例)
- [基本构造方法](#Basic-construction-method-基本构造方法)
  - [1. 管道组件](#Pipeline-Component-管道组件)
  - [2. 分支](#Branch-分支)
  - [3. 反馈电路（回流, 漩涡, 递归）](#Feedback-Circuit-反馈电路)
  - [4. 分流(并发, 并行)](#Shunt-分流)
  - [5. 合流, 合一](#Confluence-合流)
- [道](#Tao-道)
- [重大历史意义](#Great-Historical-Significance-重大历史意义)
- [后记](#Postscript-后记)
- 附录:
  - [简单性和统一性----大统一理论, Lisp(Clojure) 与纯函数管道数据流](doc/Simplicity_and_Unity.md)
  - [Clojure是基于关系式数据库理论的函数式编程语言](doc/Clojure_is_FP_based_on_RMDB.md)
  - [一切都是RMDB](doc/Everything_is_RMDB.md)
  - [在hash-map(NoSQL)的基础上实现关系式数据模型和编程](doc/relational_model_on_hashmap.md)
  - [不破坏编程语言语法的Markdown文学编程](doc/markdown_literary_programming.md)
  - [其他文章目录](#Other-Articles-Table-of-Contents-其他文章目录)

----
  
## My and Other Peoples Related Views 我的和其他人的相关观点

```
Keep it Simple and Unified.
        ---- Lin Pengcheng

NASA’s 10 rules for writing mission-critical code: 
1.Restrict all code to very simple control flow constructs.
        ---- Gerard J. Holzmann, NASA JPL lead scientist.
        
Minimize control flow complexity and "area under ifs", 
favoring consistent execution paths and times over "optimally" avoiding unnecessary work.
        ---- John Carmack

Clojure Aphorism: A tangled web of mutation means any change to 
your code potentially occurs in the large. 
        ---- The Joy of Clojure (2nd Edition, Chapter 10)
        
Bad programmers worry about the code. 
Good programmers worry about data structures and their relationships.
        ---- Linus Torvalds
        
Data dominates. If you’ve chosen the right data structures and organized things well, 
the algorithms will almost always be self-evident. 
Data structures, not algorithms, are central to programming. 
        ---- Rob Pike
        
It’s better to have 100 functions operate on one data structure 
than 10 functions on 10 data structures.        
        ---- Alan Perlis

Even the simplest procedural logic is hard for humans to verify, 
but quite complex data structures are fairly easy to model and reason about. 
...
Data is more tractable than program logic. It follows that where you see a choice 
between complexity in data structures and complexity in code, choose the former. 
More: in evolving a design, you should actively seek ways to shift complexity from code to data.
        ---- Eric Steven Raymond, The Art of Unix Programming, Basics of the Unix Philosophy
        
Metaphors for a Richer Understanding of Software Development.
        ---- The most valuable chapter of "Code Complete": Chapter 2
        
Principles-based are better than rules-based.
        ----International Accounting Standards        

大道至简，万法归宗。
        ---- 林鹏程

NASA的10大编程规则：第一条：用非常简单的控制流结构体来编写程序。
        ---- NASA 喷气推进实验室（JPL）的首席科学家 Gerard J. Holzmann
       
最小化控制流复杂性和“ifs下的区域”，倾向于一致的执行路径和时间, 
而不是 "最优化", 以避免不必要的工作。。
       ---- 约翰 卡马克       

Clojure格言：交织的变化网意味着，代码的任何变化都可能会在更大层面上产生影响。
        ---- Clojure编程乐趣(第2版)第10章
        
糟糕的程序员关注代码。优秀的程序员关注数据结构及其关系。
       ---- Linus Torvalds

数据占主导地位。如果您选择了正确的数据结构并组织好了，那么算法几乎总是不言自明的。
数据结构才是编程的核心, 而不是算法。
        ---- Rob Pike

围绕一个数据结构开发100个函数, 比设计10个带10个函数的数据结构更好.
       ---- Alan Perlis

即使是最简单的程序逻辑对于人类来说也难以验证，但非常复杂的数据结构却相当容易建模和推理。
...
数据比程序逻辑更容易处理。接下来，您可以选择数据结构的复杂性和代码的复杂性，选择前者。
更多：在设计的演变过程中，您应该积极寻求将复杂性从代码转移到数据的方法。
        ---- Eric Steven Raymond, Unix编程的艺术, Unix哲学的基础知识

善于在软件开发中运用比喻。
       ---- "代码大全"最有价值章节(第二章)
       
基于原则比基于规则更好。
       ----国际会计准则
``` 

## Summary 概述

Using the input and output characteristics of pure functions, pure functions are used as pipelines.
Dataflow is formed by a series of pure functions in series.
A dataflow code block as a function, equivalent to an integrated circuit element (or board)。
A complete integrated system is formed by serial or parallel dataflow.

利用纯函数的输入输出特性当作管道（导线）使用。
数据经过一系列串联的纯函数形成数据流。
一个数据流代码块作为一个函数，相当于一个集成电路元件（或板）。
通过串联或并联数据流，形成一个完整的集成系统。

Can also be said, Data and logic are strictly separated, 
Element level separation of data and logic, data stream processing.

也可以换种说法，数据和逻辑严格分离，数据和逻辑的元素级分离，数据流处理。

```clojure
(defn f [[evens odds total amax amin] x]
  (let [[evens odds] (cond 
                       (even? x) [(inc evens ) odds]
                       (odd? x)  [evens (inc odds)]
                       :else     [evens odds])
        total (+ total x)
        amax  (max amax x)
        amin  (min amin x)]   
     [evens odds total amax amin]))

(reduce f [0 0 0 ##-Inf ##Inf] [5 6 8 -3 -9 11 156 6 7])

;;[4 5 187 156 -9]
```

For me, programming is the process of designing a data model that is simple and fluent in manipulation. 
More than 80% functions of my project is `->>` threading macro code block, 
each step is simple, verifiable, replaceable, testable, pluggable, extensible,
and easy to implement multithreading. 
The clojure threading macro provides language-level support for PurefunctionPipeline&Dataflow.

对我来说，编程就是设计一个操纵简单流畅的数据模型的过程，
在我的项目里，80%以上的函数是由`->>`这类数据流线程宏代码块组成。
每一步都是很简单、可验证、可测试、可替换、可插入、可扩展，
而且容易实现多线程处理。
Clojure的提供的很多种类线程宏，还有极简单流畅的数据操作函数，
对纯函数管道数据流提供了语言级的支持。

The sea sails by the helmsman and the programming moves toward the data. Initial state, final state, the shortest linear distance between two points. Simplicity is the root of fast, stable and reliable. 

大海航行靠舵手，编程朝着数据走。初始状态，最终状态，两点间直线距离最短。简单直接是快速稳定可靠的根本。

## Classical Model 经典模型

This is a typical application of the philosophy of the `Tao` and the `Grand Unified Theory`.

- data-flow is current-flow, function is chip, thread macro (->>, -> etc.) is a wire, and the entire system is an integrated circuit that is energized.
- Data (flow) is raw material (flow), pure function is machine, the thread macro (->>, -> etc.) is the conveyor belt, and the entire system is a large industrial pipeline.
- Communication modes, data signals and control signals (annotations or metadata) flow through the pipeline.
- The compiler is essentially a data transformation, starting with the source code, through a series of pure function pipeline transformation optimization, up to the machine code. It's very easy to insert enhanced optimizations or features, and parallel compilation is also very simple.
- Urban water network
- Management is the best and most vivid treasure trove of computer science
  (algorithm, architecture, asynchronous, parallel, distributed and etc.).
  My programming approach is a fusion of “functional programming” and “enterprise management”. 
  It has an added benefit，It is very helpful for the communication 
  between the information technology department and the management of the company.
  - The **Gantt chart** in management, with the timeline as the main axis, multiple data flows running in parallel. 
    It is also a good data flow , parallel and asynchronous programming tool. 
  - Parallel: Large industrial pipelines can be expanded linearly in parallel.
  - Distributed: group company model, total branch model, parent-subsidiary model, holding company model, etc.
  - Architecture (Organizational Structure): 
    - Pyramid: Classic top-down modular design
    - Flat: The Pure Function Pipeline Data Flow
    - Matrix: AOP (Aspect-Oriented Programming)
    - Chaos P2P (peer to peer): OOP (Object-Oriented Programming)
  - OS or Resource Management: ERP
  - Type system: Industrial standard system (ISO standard, national standard, industry standard, enterprise standard), 
    The Pure Function Pipeline Data Flow is suitable for the implementation of product specification (data specification) 
    industry standard system, Just like the computer hardware interface standard specification, Hardware is a function, 
    interface is a data standard specification. Data is transferred between hardware (functions).
  - Storage Management(buffers, caches, databases, etc.): Inventory management
  - In a large business, `process first thinking` is based on the credential(evidence). This credential is data.
    Credentials (data) flow through the nodes in the process to form a dataflow.
    Every node in the process is a pipe-function (pure function).
    This is the `Pure Function Pipeline Data Flow`.
  - Boeing aircraft pulse production line technology, just like confluence technology of rivers from the source to the sea. 
    It's also a variant of the **Gantt Chart**.
    
    
![Gantt chart](./doc/image/GanttChart.jpeg) 

![River](./doc/image/river.jpeg) 

这是`道`和`大统一理论`的哲学的典型应用:

- 数据流是电流，函数是芯片，线程宏（->>, -> etc.）是导线，整个系统就是通电工作的集成电路。
- 数据(流)是原料(流), 纯函数是机器, 线程宏（->>, -> etc.）是传送带, 整个系统是大工业流水线.
- 通信模式, 数据信号和控制信号(注解或元数据)在管道里流转.
- 编译器本质上就是数据变换，从源码开始，经过一系列纯函数管道的变换优化，直至机器码.非常容易插入增强优化或特性, 实现并行编译也很简单.
- 城市的自来水网
- 管理学是最好的,最生动的计算机科学的宝库(算法、架构、异步、并行和分布式等等). 
  我的编程方法是“函数式编程”和“企业管理”的融合。它有一个额外的好处，
  它对信息技术部门和公司管理层之间的沟通非常有帮助。
  - 管理学里的**甘特图**, 以时间线为主轴, 多个数据流并行前进. 它也是很好的数据流、并行、异步编程工具.
  - 并行: 大工业流水线可以线性并行扩展.
  - 分布式: 集团公司模型, 总分公司模式,母子公司模式, 控股公司模型等.
  - 组织架构: 
    - 金字塔式: 经典的自顶向下模块化设计:
    - 扁平式: 纯函数管道数据流
    - 矩阵式: 面向切面编程(AOP)
    - 混乱的P2P (点对点对等网络): 面向对象编程(OOP)
  - 操作系统或资源管理: ERP
  - 类型系统: 工业标准体系(ISO标准,国家标准，行业标准，企业标准)，纯函数管道数据流适合产品规范(数据规范)工业标准体系的实施,
    就象计算机硬件接口标准规范一样, 硬件是函数, 接口是数据标准规范 在硬件(函数)间传输数据.。
  - 存储管理(缓冲区, 缓存, 数据库, 等等)：库存管理.
  - 在大型企业中, 流程第一思想, 是建立在凭据(证据)的基础上的, 这个凭据就是数据, 凭据(数据)在流程中各节点流转, 形成数据流. 
    流程中的每一个节点就是管道函数(纯函数), 这就是`纯函数管道数据流`.
  - 波音公司的脉动生产线技术, 就象长江从源头出发, 沿途汇流, 百川东到海. 它也是**甘特图**的一个变种.

### Warehouse Workshop Model 仓库车间模型

![Warehouse Workshop Model](./doc/Warehouse-Workshop-Model.svg)

Metaphor:

- Information System Integration Model: 

  Many large enterprises have independent information systems produced 
  by different manufacturers and need to integrate and integrate.
  
  - Workshop: individual subsystems  
  - Warehouse: The information system integration layer acts as a individual system.
    - A unified abstraction layer (virtual database, virtual data warehouse) 
      of enterprise global data, external data requests of any subsystem 
      are requested from this system without knowing from that subsystem.
      Achieve the unity of the global system.
    - The middle layer and data routing of system interconnection.
    - Isolation change: When one subsystem changes, 
      it does not cause chain changes of other subsystems.
    - Putting the complexity in one place is better than 
      putting it in all places.
    - The subsystems are guaranteed independence, 
      and the simplicity of each subsystem is realized.
    - Ultimately, the simplicity and unity of the global system is achieved.
  - Extended case
    - The OS provides a large number of APIs for developers to use, 
      but if the OS API changes may be more frequent, 
      such as adding methods or variables, but previously developed 
      applications are likely to use the old OS API. 
      Solution: Develop directly a version compatibility layer independently, 
      and freely develop the OS.
      - Warehouse: individual version compatibility layer
      - Workshop: OS, applications, programming languages, etc.
    - Intel's CPU starts with Pentium, the kernel switches to RISC, 
      and the external CISC compatibility layer
    - Microsoft's Windows 95/NT system also supports DOS and Windows 3.1 
      applications with a separate compatibility layer.
    - Apple's Mac OS X uses an independent compatibility layer to 
      support legacy applications of System OS.
    
- Computer model: 
  
  The model uses memory as the core, not the CPU.
  
  - Warehouse: Memory
  - Workshop: CPU, graphics card, sound card, etc.
  - Standardized data: data transmitted between hardware 
    that conforms to industry standard interfaces
  - Acceptance: Motherboard with standardized interfaces
    such as PCI, SATA, USB, etc.
  - External standardized data: hard disk, flash drive, etc.
  
- Integrated circuit system
  - Warehouse: Battery
  - Workshop: Integrated Circuit Components (Chip, Board), Electrical Equipment
  - Standardized data: current
  - External standardized data: power plants
  
- Programming language platform

  Like julia, a lisp is built into the internal core or internal representation, 
  and the popular grammar is used externally. Therefore, 
  the grammar is not a problem at all, and the compiler and the grammar 
  can evolve independently, go hand in hand, freely, efficiently, and flexibly. 
  You can do several languages at the same time, 
  such as Julia native support for julia and lisp syntax, 
  and third-party implementation of clojure syntax, 
  performance equivalent to native grammar. 
  Converting clojure grammar to lisp grammar is simpler than 
  native julia grammar conversion. Implementing a language on a platform 
  represented by a lisp is very simple, such as Racket. 
  Regardless of which one of the developers likes swift, python, ruby, 
  scala, f`#` and java, all of them are implemented separately, 
  all of them are satisfied.
  
  - Warehouse 
    - Standard library
    - Library represented by internal lisp that 
      compiled from Code written in various external languages.
    - Native compiler compiled libraries and applications
    
  - Workshop
    - Native compiler: Get the lisp intermediate code from the repository, 
      compile and output to the repository.
    - Internal lisp core: Write code in lisp, 
      or compile output intermediate code in other languages.
    - External languages: Compile and output each language code to the warehouse. 
      Each language does not have to interact with each other. 
      Just interact with the repository. Multi-language on the racket language 
      is the mechanism.

- Other models 

  - Warehouse
    - Standardized data model
    - RMDB
  - Workshop
    - The Pure Function Pipeline Data Flow
    - Industrial production line
    - Watertight compartment of the vessel
  - Standardized data
    - Industry standard products
      - Raw material
      - Semi finished product
      - Finished product
  - Acceptance
    - Quality control department
    - customs
  - External standardized data
    - Purchasing department
    - supply chain
  
Before entering the warehouse, 
all data must be acceptance-checked first.

The input and output of the workshop 
can only be standardized data, 
the input-data comes from the warehouse, 
the output-data is acceptance-checked 
and sent to the warehouse.

Therefore, there will be no 
abnormal/error/Illegal data inside the workshop, 
no need to check data.

The code in the workshop is a pure function pipeline data flow,
it's simple, reliable, high-performance, 
Easy to debug, easy to observe, easy to maintain, easy to expand.

The workshop and the workshop are independent, 
non-interactive, Like a Lego module or 
a ship's watertight compartment, 
internal changes or abnormalities 
in any one workshop do not affect other workshops.  

比喻:

- 信息系统集成模型：很多大企业有不同厂家生产的独立信息系统，需要整合集成。
  - 车间：各个独立的系统  
  - 仓库：信息系统集成层作为独立系统。
    - 企业全局数据统一的抽象层（虚拟数据库，虚拟数据仓库），
      任一系统的外部数据请求皆向此系统求，而无需知道来自那个系统，实现全局系统的统一性。
    - 系统互联与数据路由的中间层。
    - 隔离变化：当一个系统变动时，不会导致其他系统的连锁变动。
    - 把复杂性集中在一个地方，比在所有地方束手束脚，按了葫芦起了瓢好。
    - 使各系统保证独立性，进而实现各系统的简单性。
    - 最终达到全局系统的简单性和统一性。
  - 扩展案例
    - OS提供了大量的编程接口给开发者使用，但如果os接口变更可能比较频繁，如添加方法或者变量等，
      但以前开发的应用很可能使用OS老版本的API。方案：直接独立开发一个版本兼容层，放开手脚干OS
      - 仓库：独立的版本兼容层
      - 车间：OS, 应用, 编程语言等
    - Intel的CPU从奔腾开始, 内核改用RISC, 外用CISC兼容层也是类似方法。
    - Microsoft的Windows95/nt系统也是以独立兼容层支持DOS和Windows3.1的应用
    - Apple的Mac OS X也是以以独立兼容层支持老产品System OS的应用
    
- 计算机模型：模型以内存作为核心，而不是CPU。
  - 仓库：内存
  - 车间：CPU, 显卡，声卡等。
  - 标准化的数据：在符合工业标准接口的硬件间传输的数据
  - 验收：主板(带有PCI, SATA, USB等标准化接口)
  - 外部的标准化数据：硬盘，闪存盘等
  
- 集成电路系统
  - 仓库：电池
  - 车间：集成电路元件(芯片,板), 电气设备
  - 标准化的数据：电流 
  - 外部的标准化数据：发电厂
  
- 语言平台: 
  象julia一样搞个lisp为内部核心或内部表示，外用流行语法，这么一来语法特牲完全不是问题，随便增改,
  编译器和语法可以独立演进，齐头并进，自由高效灵活。 可以同时搞几个语言,
  如Julia原生支持julia和lisp语法，还有第三方实现了clojure语法，性能等同原生语法。
  把clojure语法转换成lisp语法，比原生julia语法转换还简单，在一个lisp内部表示的平台上实现一个语言，是很简单的,如Racket.
  不管是喜欢swift,py,ruby,scala,java,f#的哪一种, 统统分别实现一个，统统满足.
  - 仓库: 
    - 标准库
    - 外部各种语言编写的编译后以内部lisp表示的库.
    - 本地编译器编译后的库和应用
  - 车间: 
    - 本地编译器: 从仓库获取lisp中间代码, 编译输出到仓库.
    - 内部lisp核心: 用lisp编写代码, 或其他语言编译输出的中间代码.
    - 外部各种语言: 把各语言代码编译输出到仓库, 各语言不必互相交互, 只要与仓库交互即可. racket语言上的多语言即是如此机制.

- 其他模型：  
  - 仓库
    - 标准化的数据模型
    - 关系式数据库
  - 车间
    - 纯函数管道数据流
    - 工业生产流水线
    - 船只的水密隔舱
  - 标准化的数据
    - 符合工业标准的产品
      - 原材料
      - 半成品
      - 产成品
  - 验收
    - 质量控制部门
    - 海关
  - 外部的标准化数据
    - 采购部门
    - 供应链
  
进入仓库前, 所有的数据必须先经过验收.

车间的输入输出只能是标准化数据,
输入的数据来自仓库,输出的数据经过验收后送到仓库.
因此车间内部不会存在异常/错误/非法数据,
无须检测数据.

车间的代码是纯函数管道数据流,
代码简单,可靠,高性能,
易调试,易观测,易维护,易扩展.

车间与车间之间是并行且独立的,不交互,
就象是乐高组件或船只的水密隔舱,
任何一个车间的内部变动或异常不会影响其他车间.

## Disadvantages of FP and OO 函数式编程和面向对象编程的缺点

FP and OO are overly complicated, and it is not feasible in large industries. It is also a kind of production method that emphasizes personal technology in hand workshops. Personal technology greatly affects product quality and extremely unreliable production methods.FP and OO are actually taking a detour, highly embellished and ineffectual, and produce all kinds of fail.

FP和OO过度复杂了，在大工业上是行不通的，还是属于手工作坊那种强调个人技术的生产方式, 个人技术极大影响了产品质量，极不可靠的生产方式。FP和OO其实全是在走弯路, 花拳秀腿,花样作死。

Excessive application of OO and FP design patterns, in addition to increasing complexity 
and error probability, reduce performance, without any benefit. 
Complex networks of relationships between objects in the OO system are also difficult to maintain..

过多的应用OO和FP的各种模式, 除了增加复杂性和出错概率,降低性能, 没有任何好处,
OO系统中对象之间复杂的关系网也是难以维护的.

I tend to construct systems with the simplest concepts and the most basic techniques, syntax, and functions. Used to implement my mind, The Pure Function Pipeline Data Flow is the simplest, stable, reliable and readable.. There is a great poet Bai Juyi in China. even illiteracy understands and appreciates his poetry. I hope that my code can be understood by the junior programmer even in the most complicated system.

我倾向于用最简单的概念和最基本的技术、语法和函数构建系统，用来实现我的思想，纯函数管道数据流是最简单、稳定、可靠、可读性强. 在中国有一位伟大的诗人白居易，甚至文盲也理解和欣赏他的诗歌。 我希望即使在最复杂的系统中，初级程序员也能理解我的代码。

## The difference between it and middleware 它和中间件的区别

The code looks similar, but the idea is essentially different.

- The input and output of the middleware's function is a function, 
the flow is a layer-packed function. It like concentric circles, 
and middleware debugging is very troublesome.

- The input and output of the PureFunctionPipelineDataflow's function is data, flow is data, 
it is linear series and parallel. It like a line.

I can't agree with the idea of middleware,
It is in conflict with the idea of integrated circuits. 
In the circuit, the component (board) cannot be circulated, 
only the data (current) can flow, which is the essential difference.

代码外形看起来相似，但理念是本质上的差别。

- 中间件函数的输入输出是函数，流转的是层层打包的函数，是同心圆，middleware调试是很麻烦的。

- 纯函数管道数据流输入输出是数据，流转的是数据，是线性的串并联。

我不能认同中间件的理念，和集成电路思想是冲突的。电路里，元件（电路板）是无法流转的，
只有数据（电流）才能流转，这是本质的区别。

## The difference between it and Rx 它和Rx的区别

It is essentially different between it and [Rx](http://reactivex.io/):

- The essential difference between programming methods is the inherent thoughts and models. The idea and model of pure function pipeline data flow are highly consistent with integrated circuits.

- `The Pure Function Pipeline Data Flow` emphasizes the data flow, Rx emphasizes the asynchronous event flow, and does not mention or emphasize the data flow.

- `The Pure Function Pipeline Data Flow` is composed of only 5 components, and the model is much simpler than Rx.

- `The Pure Function Pipeline Data Flow` emphasizes the sequential structure (series of pipeline components), and the maintenance (code reading, expansion, debugging, etc.) is simpler.

- The asynchronous event flow of `The Pure Function Pipeline Data Flow` is simpler than Rx. I wrote an asynchronous event flow in my project, it is just a queue processing, It's too simple, so there's no need to mention it specifically.

- The Clojure language doesn't require [RxClojure](https://github.com/ReactiveX/RxClojure) at all.

它与[Rx](http://reactivex.io/)本质上是不同的：

- 编程方法之间的本质区别在于内在的思想和模型。 纯函数流水线数据流的思想和模型与集成电路高度一致。

- 纯函数管道数据流强调数据流，Rx强调异步事件流，没有提及或强调数据流。

- 纯函数流水线数据流仅由5个组件组成，模型比Rx简单得多。

- 纯函数流水线数据流强调顺序结构（管道组件的串联），维护（代码读取，扩展，调试等）更简单。

- 纯函数管道数据流的异步事件流比Rx简单。 我在我的项目中编写了一个异步事件流，它只是一个队列处理，简单到没有必要特别提及它。

- Clojure语言根本不需要[RxClojure](https://github.com/ReactiveX/RxClojure)。

## The difference between it and traditional unix-like pipe operator in FP language 它和传统FP语言里的类unix管道操作符的区别

- Traditional unix-like pipe operator in FP language

  - Just simply  simulate a water pipe.
  
  - Just as a tip in a code snippet.

- Pure function pipeline data flow

  - Systematic simulation of integrated circuit systems and large industrial production lines.
  
  - Covers all aspects of system architecture, data modeling, data manipulation, data application, etc.

- 传统FP语言里的类unix管道操作符

  - 只是简单地模仿自来水管.
  
  - 只作为一个代码片段里的小技巧.

- 纯函数管道数据流

  - 系统性地模拟了集成电路系统和大工业生产流水线.
  
  - 涵盖了系统架构, 数据建模, 数据操纵, 数据应用等一切层面.
  

   

## Basic quality control 基本质量控制

Basic quality control of pure function pipeline data flow. The code must meet the following three basic quality requirements before you can talk about other things. These simple and reliable evaluation criteria are enough to eliminate most unqualified codes.
- **Function evaluation:** Just look at the shape of the code (pipeline structure weight), and whether the function is a pure function.
- **Dataflow evaluation:** A data flow has at most one side effect and can only be placed at the end.
- **System evaluation:** Just look at the circuit diagram, you can treat the function as a black box like an electronic component.
- **Clojure Code Quality Visualization:** S expression is contour graph, can be very simple transformation into contour map, or 3D mountain map, if the height of the mountains is not high, and the altitude value is similar, it means that the quality of the code is good.

纯函数管道数据流的基本质量控制, 只有代码达到下面三条基本质量要求, 才可以继续谈其他.
这些简单可靠的评价标准, 足以淘汰绝大多数不合格代码:
- **函数  评价:** 只需要看代码的外形(管道结构比重), 以及函数是不是纯函数.
- **数据流评价:** 最多只有一个副作用,且只能放在末端.
- **系统  评价:** 只看线路图即可, 可以把函数象电子元件一样当黑盒处理.
- **Clojure代码质量可视化:** S表达式就是等高线图,可以很简单的变换成等高线图,或3D山峦图.
如果山峦高度不高,且海拔高度值相近,意味着代码质量是好的.

## Code example 代码范例

### Code example 01

```clojure
;Traditional expression, chaotic logic, unreadable.
(if (and (> x1 x2)
         (or (< x3 x4) 
             (and (or (> y1 y2) 
                      (< y3 y4))
                  (not= x5 x6)))
         (keyword? x7)) 
  :t
  :f)

;Pure Function Pipeline Dataflow
;Unrestricted expression, just read in order. 
;Closer to the order of execution of the machine.
(->  (> y1 y2)
     (or  , (< y3 y4))
     (and , (not= x5 x6))
     (or  , (< x3 x4))
     (and , (> x1 x2))
     (and , (keyword? x7))       
     (if  , :t :f))
```

### Code example 02

```clojure
(def data
  {:a [[:b :c :d]
       [:e :f :g]
       [:h :i :j]]
   :k [[:l :m :n]
       [:o :p :q]
       [:r :s :t]]})

(defn f1 [[k v]]
  (let [[h & t] v
        f   (fn [x] (mapv #(vector :td %) x))
        tds (map #(->> % f (into [:tr] ,)) t)]
     (->> (f h)
          (into [:tr [:td {:rowspan (count v)} k]] ,)
          (conj tds ,))))

(->> data
     (reduce #(->> %2 f1 (into %1 ,)) [:tbody] ,)
     (conj [:table] ,)
     hiccup/html)

```

<table>
    <tbody>
       <tr><td rowspan=3>a</td>
           <td>b</td>
           <td>c</td>
           <td>d</td></tr>
       <tr><td>e</td>
           <td>f</td>
           <td>g</td></tr>
       <tr><td>h</td>
           <td>i</td>
           <td>j</td></tr>
       <tr><td rowspan=3>k</td>
            <td>l</td>
            <td>m</td>
            <td>n</td></tr>
       <tr><td>o</td>
            <td>p</td>
            <td>q</td></tr>
       <tr><td>r</td>
            <td>s</td>
            <td>t</td></tr>
    </tbody>
</table>


## Basic construction method 基本构造方法

### Pipeline Component 管道组件

A ->> block function is equivalent to an integrated circuit component (or board).
A series of functions in a ->> block can only have one function with side effects 
and can only be at the end. 
In addition, we must pay attention to the data standardization work, 
verify the data at the entrance and exit, 
and run at full speed in the middle, 
which is simple, smooth, stable and efficient.

一个->>块函数相当于一个集成电路元件（或板）,
一个->>块里面的一系列函数，最多只能有一个带副作用的函数且只能处于末尾。
另外，要注意做好数据标准化工作，在出入口检查，中间就可以极限裸奔，
这样做简洁、流畅、稳定、高效。

In the clojure language, it is recommended that the function be designed as 
a single-parameter function with a hash-map type. 
Like most functions in the R language, you can design many named parameters with default values, 
which are highly scalable. 
In addition, clojure has many core functions for operating hash-map, it's easy to operate,
not only it may don't write parentheses when using ->> macro, 
it can be integrated that parameter formation, verification, transformation and serial pipeline functions, 
It is also convenient to deconstruct in clojure. 
which is as convenient as multi-parameter functions.

在clojure语言里，建议函数尽量设计成参数为hash-map类型的单参数函数，
象R语言大多数函数那样，可以设计很多带默认值的命名参数，有很强的可扩展性。
另外，clojure操作hash-map的核心函数很多，操作方便，不仅在使用->>宏时可以不用写括号，
而且参数的形成，校验，变换与函数调用一体化、一条龙数据流处理。
还有clojure解构方便，在使用上与多参数函数是一样方便的。

```clojure
(defn f [x]
  (->> x
       f1
       f2))
```

```clojure
(defn f [{:keys [x y] :as m}]
  (->> x
       (f1 y ,)
       f2))
```

### Branch 分支

A (cond) or (if) block as a function.

一个(cond)或(if)块作为一个函数。

```clojure
(defn f [x]
  (cond
    (= x 1) (f1)
    (= x 2) (f2)
    :else   (f3)))
```
```clojure
(defn f2 [x y]
  (-> (> x 2)
      (and , (< y 6))
      (if , 25 30)))
```
```clojure
(defn path-combine [s1 s2]
  (cond
    (string/starts-with? s2 "/") 
      s2
    (not (string/ends-with? s1 "/"))
      (-> (string/split s1 #"[\\/]")
          butlast
          (#(string/join "/" %))
          (str , "/")
          (path-combine , s2)) 
    :else  
      (-> (string/join "/" [s1 s2])
          (string/replace ,  #"[\\/]+" "/")))) 
```

### Feedback Circuit 反馈电路

Feedback circuit (reflow, whirlpool, recursive): 
A tail recursive function is equivalent to a feedback circuit. 

Note: The map is batch processing. it can be regarded as similar to a queue of tourists. 
Repeating the ticket checking action at the entrance is a forward action, 
not feedback or reflow.

反馈电路（回流, 漩涡, 递归）:
一个尾递归函数相当于一个反馈电路。

备注：map是批处理，可以看成类似对一个游客队列，在入口重复进行验票动作，
是一个前进动作，不是反馈或回流。

```clojure
(defn f [i]
  (if-not (zero? i)
    (f1)
    (-> i dec recur)))
```

### Shunt 分流

Shunt（concurrent，parallel）,
For example: data partitioning, parallel processing

分流（并发，并行）,例如：对数据进行分块，并行处理

```clojure
(->> data
     (partition n ,)
     (pmap f ,))
```
```clojure
(->> [pipe-f1 pipe-f2 pipe-f3]
     (pmap #(% data) ,))
```

### Confluence 合流

Confluence（reduce）: reduce the result of the shunt

合流，合一: 对分流的结果进行reduce： 

```clojure
(->> data
     (partition n ,)
     (pmap f1 ,)
     (reduce f2 ,))   
```

## Tao 道

According to Taoism, water flow is the perfect substance. The water flow is always able to assume any shape as needed, sequential processing, until the mission is completed, reaching the end. The pure function pipeline data flow is like a water flow, almost the Tao.

上善若水, 水能按需呈现任何形状, 随心所欲, 千变万化, 顺序前进, 直到完成使命, 到达终点. 
纯函数管道数据流就象水流一样, 近乎于道.

Clojure just adds four persistent collections and some core functions to the JVM, and expresses the code with four persistent collections. It has no syntax, It can change as needed, like water flow, almost the Tao.

Clojure只是向JVM添加了四个持久集合和一些核心函数，并用四个持久集合表示代码。
它没有语法, 它可以象水流那样, 随需变化, 近乎于道。

![TaoTaiji](./doc/TaoTaiji.gif)

Tao is simplicity, Tao is the law of nature, Tao is algorithm, Tao is everything.
Therefore, Integrated Circuit Technology, Industrial Assembly Line Production Technology, 
Accounting, Management, Architecture etc. 
everything can be used as Algorithms and Software Engineering Methods.
They can transform each other.


大道至简, 道法自然, 道是算法, 道无处不在。
所以, 集成电路技术、工业流水线生产技术、会计学、管理学、建筑学等,
一切都可当成算法和软件工程方法使用, 它们可以互相转化.

## Great Historical Significance 重大历史意义

The Pure Function Pipeline Data Flow, 
based on the philosophy of Taoism and the Great Unification Theory, 
In the computer field, for the first time, 
it was realized that the unification of hardware engineering and software engineering on the logical model.
It has been extended from `Lisp language-level code and data unification` 
to `system engineering-level software and hardware unification`. 
Whether it is the appearance of the code or the runtime mechanism, 
it is highly consistent with the integrated circuit system. 
It has also been widely unified with other disciplines 
(such as management, large industrial assembly lines, water conservancy projects, power engineering, etc.). 
It's also very simple and clear, and the support for concurrency, parallelism, 
and distribution is simple and natural.

There are only five basic components:

1. Pipeline (pure function)

2. Branch

3. Reflow (feedback, whirlpool, recursion)

4. Shunt (concurrent, parallel)

5. Confluence.

The whole system consists of five basic components. 
It perfectly achieves unity and simplicity.
It must be the ultimate programming methodology.

This method has been applied to 100,000 lines of code-level pure clojure project, 
which can prove the practicability of this method.

In addition, the IT industry is still a very young and immature discipline.
The current software engineering is still at the level of manual workshops. 
`Pure function pipeline data flow` brings large industrial production theory 
and methods to software engineering. It incorporates IT industry into 
modern large industrial production systems, This is an epoch-making innovative 
theory and method. 

The modern society is an information society, IT controls everything, 
penetrates everything. In my opinion, the development of IT is exactly 
the same as the development of modern large-scale industrial production 
systems. With the development of the IT industry, 
With the development of the IT industry, data standard systems will be 
widely established, improved and interconnected at the international, 
national, industrial and enterprise levels, It will be precisely standardized 
to every smallest part. `pure function pipeline data flow` will become 
the basic theory and Methods have become increasingly important, 
and have become the ultimate standard method for entering textbooks and industry.

The key to the industrialization of the IT industry is to 
establish a complete standard system like the traditional industry. 
From the perspective of large industrial production theory, 
standardizing the output products (data) has the following advantages:

- Fairness
- Neutrality
- Fungibility
- Standard
- Interconnectedness
- Combination, Data combination is better than code (function) combination.
- Simplicity.
- reliability
- Unity
- Easy to expand
- Easy to parallel, Can linearly scale up production (performance).
- Observable, easy to debug, and verifiable.
- Clarity, non-IT practitioners can understand.
- It can refer to the theory of integrated circuits, business management and other disciplines.

The role of the standard system can be seen from 
the great progress of social productivity after 
the traditional industry has entered the era of 
large industrial production from the era of manual workshops.

纯函数管道数据流，基于道家和大统一理论的哲学，
在计算机领域，首次实现了硬件工程与软件工程在逻辑模型上的统一。
它已从“Lisp语言级代码和数据统一”扩展到“系统工程级软件和硬件统一”。
无论是代码的外观还是运行时机制，它都与集成电路系统高度一致。
它还与其他学科（如管理，大型工业流水线，水利工程，电力工程等）广泛统一。
它也非常简单明了，对并发，并行和分布式的支持简单而自然。

只有五个基本组成部分：

1. 管道（纯函数）

2. 分支

3. 回流（反馈，漩涡，递归）

4. 分流（并发，并行）

5. 合流

整个系统由五个基本组成部分组成。它完美地实现了统一性和简单性。它一定会成为终极编程方法学。

该方法已应用于10万行代码级的纯Clojure项目，足以证明该方法的实用性。

另外,IT业作为一门学科，还很年轻，不够成熟， 目前的软件工程还停留在手工作坊水平， 
"纯函数管道数据流"方法的出现，为软件工程带来了大工业生产理论和方法，
把IT业纳入现代大工业生产体系，这是一个划时代的创新的理论和方法。

现代社会是信息社会，IT控制一切, 渗透一切, 我认为，
IT的发展历程与现代大工业生产体系的发展历程是一模一样的。
随着IT业的发展，如国际级、国家级、行业级、企业级的数据标准体系的广泛建立、细化和互联，
"纯函数管道数据流"将成为IT业大工业化生产的基础理论和方法而发挥越来越重要的地位，
并成为终极的标准性的方法进入教科书和工业界。

IT界大工业生产化的关键在于建立象传统工业界的完整的标准体系，如ISO,国标，行标，企标等.
从大工业生产理论来讲，对输出的产品(数据)做标准规范，具有如下优点:
- 公平性, 中立性
- 可替代性
- 标准性
- 互联性
- 组合性, 数据组合优于代码(函数)组合.
- 简单性
- 可靠性
- 统一性
- 易扩展
- 易并行, 可以线性扩大生产规模(性能).
- 可观测,易调试,可验证
- 清晰性, 非IT从业人员也可理解.
- 可以参考集成电路, 企业管理等学科的理论.

标准体系的作用,从传统工业界从手工作坊时代进入大工业生产时代后, 社会生产力的巨大进步可以看出来.
这也是中国历史上著名的"车同轨,书同文"的作用.


## Postscript 后记

Similar to The most valuable chapter of “Code Complete”----Chapter 2 Metaphors for a Richer Understanding of Software Development, I tend to inspire readers to discover useful patterns from life, work and personal interests, which are then used as solutions for development, rather than to apply mechanically other people’s cases.

In this way there will be endless cases, there will always be endless ways to solve the problem. This is "Tao ".

类似于“代码大全”中最有价值的章节--第2章对软件开发有更深入理解的隐喻，我倾向于激发读者从生活，工作和个人兴趣中发现有用的模式，然后将其作为开发的解决方案，而不是机械地应用其他人的案件。

通过这种方式，将会有无穷无尽的参考案例、无穷无尽的方法来解决问题。这就是“道”。

老子曰：“吾言甚易知甚易行，天下莫能知莫能行。”
即：大道至简，易学难精。
另外，就是要养成并保持良好的开发习惯，
做一件好事很容易，但一辈子做好事很难，
写一个管道纯函数很容易，坚持写纯管道系统不容易。
对本法有兴趣的人，可以坚持多应用，熟能生巧，功到自然成。

I was asked why I didn't create several pipeline dataflow design patterns like OO and FP, and I thought, in Chinese Classic Myth Fiction "The Journey to the West", Bodhi  asked the monkey if he wanted to learn `Tiangang 36 change patterns` or `Disha 72 change patterns`, when the monkey chose `Disha 72 change patterns`, his failure has become a foregone conclusion, Bodhi who is the Taoist great God must understand the nature of the Tao, learn the laws of nature, The ever-changing truth, whether the monkey chose `Tiangang 36 change patterns`, or `Disha 72 change patterns`, his thoughts from then on stifled shackles, put on the invisible Tight curse, from then on can not approach  "Tao ", this is not teaching, but playing monkey. :-)

有人问我为什么不象OO和FP一样，搞几个管道流的设计模式，我不禁想到《西游记》中菩提祖师问猴子要学天罡36变，还是地煞72变，
当猴子选择72变时，他的失败已成定局，作为道家大能的菩提祖师，不会不懂道法自然，千变万化的道理，
不管猴子选36变，还是72变，他的思想从此受到窒梏，戴上无形的紧㧜咒，从此无缘大道，这不是教学，而是耍猴。:-)

当然, 事情也可以从另一个角度来讲，子曰： “不愤不启，不悱不发，举一隅不以三隅反，则不复也。”老子曰：“道可道，非常道。”
因为猴子优秀的身体资质，被菩提祖师收入门墙，因为道只可意会，不可言传，因此给了猴子72次机会，以72变为例启发猴子悟道，
可惜，猴子悟性太差，只是一台完美的复印机，没有任何创新能力，不能举一反三，始终不能悟道，
最终菩提祖师绝望了，明白了猴子不能悟道继承他的衣钵，达不到做他弟子的标准，
就把猴子逐出门墙，不许猴子称他为师傅，即猴子是肆业，甚至是不光彩地被劝退，而不是毕业。

I spend my spare time developing a financial analysis expert system. 
Although my writing time is very limited, but I will gradually improve it. 
compared to the content when I first set up the blog, 
it has been rich and improved a lot.

我利用业余时间开发财务分析专家系统。虽然我写作时间有限，但我会逐步改进它，
相比我第一次设置博客时的内容，它已经丰富和改进了很多。

## Other Articles Table of Contents 其他文章目录

### English + Chinese

- [Markdown Literary Programming that don't break the syntax of any programming language 不破坏编程语言语法的Markdown文学编程](doc/markdown_literary_programming.md)

- [~~Introduction： Basic Methods (Old version) 引论: 基本构造方法(老版本)~~](doc/IntroductionBasicMethods.md)

- [Annotation is an unnecessary technique 注解是不必要的技术](doc/annotation_is_unnecessary.md)

- [Clojure is a FP based on RMDB. clojure是基于关系式数据库理论的函数式编程语言](doc/Clojure_is_FP_based_on_RMDB.md)

- [Everything is RMDB. 一切都是RMDB](doc/Everything_is_RMDB.md)

- [Mathathematical and AI 数学与《天龙八部》小无相功：从AI的角度看，所有的专业都是穿着马甲的数学。](doc/math-xiaoyao.md)

- [Why Clojure (Lisp) almost the Tao? 为什么 Clojure (Lisp) 近乎于道?](doc/why_clojure_almost_the_Tao.md)

- [The Best Practice of Clojure. Clojure最佳实践](doc/best_practice_of_clojure.md)

- [Interaction of Static and Dynamic (Taiji and Table Tennis) 动静态交互(太极与乒乓球)](doc/interaction_of_static_and_dynamic.md)

- [Rust: Mathematics can't save programming, but finance can do. Rust: 数学不能救编程，但财务可以](doc/rust.md)

- [React is terrible. React很糟糕](doc/react_is_terrible.md)

### Chinese

- [简单性和统一性----大统一理论, Lisp(Clojure) 与纯函数管道数据流](doc/Simplicity_and_Unity.md)

- [儒家大统一之道--学科融合(国际疾病分类、AI、数学、会计与纯函数管道数据流)](doc/Tao_ICD.md)

- [论“立德、立功、立言”三不朽](doc/immortal.md)

- [Office是数据库服务](doc/office_is_db.md)

- [数据模型是全局的、战略的，而函数实现只是局部的、战术的](doc/datamodel-vs-function.md)

- [英雄所见略同：Rob Pike，Linus Torvalds，Alan Perlis 和我](doc/RobPike-LinusTorvalds-AlanPerlis-Me.md)

- [纯函数管道数据流串并联集成系统法](doc/DataflowIC.md)

- [论纯函数管道数据流方法，兼评：左耳朵耗子 《什么是函数式编程？》](doc/AboutDataflow.md)

- [函数式编程学套路还是学无限法？](doc/infinite.md)

- [代码也是头等公民](doc/code-is-first-class.md)

- [《代码大全》与“想像力编程”](doc/CodeComplete.md)

- [《计算机编程的艺术》与想象力编程](doc/TAOCP.md)

- [神话编程：生死簿、轮回、地狱](doc/LifecycleManagement.md)

- [半自动步枪、批处理和Lazy](doc/lazy.md)

- [如来神掌与tree-seq](doc/tree-seq-and-The-Hand-of-God.md)

- [C#愚蠢到我不能理解，兼论UI构造方法](doc/c%23stupid.md)

- [例解：抽象、多态、变态](doc/Ii-abstract.md)

- [我的项目技术架构：AI、统计、杀毒软件](doc/TechnicalFramework.md)

