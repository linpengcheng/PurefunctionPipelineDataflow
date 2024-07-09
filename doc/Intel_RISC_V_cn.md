# 预测: Intel将用“RISC-V加x86兼容层”或“RISC-V加x86异构计算架构”开发新一代"仓库/车间模型"的CPU

版权所有 © 2021.06.14 林鹏程， 保留所有权利。

Intel应该是准备以RISC-V为核心，加x86兼容层，对标Apple M1开发新一代"仓库/车间模型"的CPU，同时还能开拓占领物联网CPU的市场。

如果开发x86兼容层太麻烦，有一个快速解决方案，因为我的“仓库/车间模型”对天然支持异构计算，可以在CPU内提供1~2个x86核心专门执行x86指令，提供兼容能力。

Intel最近麻烦挺大，前有Apple采用我的仓库/车间模型的M1芯片，不仅在性能大胜Intel的CPU,而且还保持更大的节能优势，
另外，我以前在博文上讲过，M1还有很大的优化空间，新的M2据说也快出来了，后有AMD赶超，可谓前有虎后有狼，Intel都急得临阵换帅（CEO）了。

Intel这个牙膏厂，它的原有的技术积累和开发路线可以说是不顶用了，如果有早就推出来了，当下只能大动作更新换代了，
现在唯一表现出全面超越"冯·诺依曼体系结构"的架构只有我的“仓库/车间模型”了，我想它除了“仓库/车间模型”之外，别无选择了。

最近有消息Intel 准备花 20 亿美元收购RISC-V的初创公司SiFive， 难道它准备以“RISC-V加x86兼容层”或“RISC-V加x86异构计算架构”，
对标M1开发新一代"仓库/车间模型"的CPU，同时还能开拓占领物联网CPU的市场。

如果ARM和RISC-V生产商加入“仓库/车间模型”CPU的竞争，将对Intel产生严重威胁，
目前我没有看到这方面的消息，但应该至少会有1~2家主要生产商加入竞争，市场进入激烈竞争阶段。
另外，微软的支持至关重要，特别是微软与高通有密切合作关系，联合开发了“Windows/ARM PC”。

巨大的x86存量市场仍然会给予Intel带来一段时间的资金来源和缓冲空间，未来的物联网市场更为广阔。RISC-V是开源的，
并且可以进行专有扩展，它是拥有优秀CPU设计人才的Intel的最好选择，也是Intel争取市场领导地位的最好选择。
危险与机遇并存，这是决定Intel生死存亡的时刻，如同凤凰涅槃，或浴火重生，或烧成死灰。

Intel CEO Pat Gelsinger最近宣布，该公司将开始向其他公司发放自己的x86处理器设计许可，作为其新的IDM 2.0计划的一部分。
鉴于Intel以前的严苛的许可政策，我认为这是Intel准备放弃x86. Intel发放的x86处理器设计许可的目标对象很可能是中国公司，
我认为x86是一种过时的即将被淘汰的设计，中国公司不应出价太高，避免成为冤大头。

后记:

- 2022.2.14新闻:《Intel计划将x86内核授权用于内置Arm，RISC-V等的芯片》

  我想Intel应该是使用我的方案, 
  因为实现这个方案须使用我的"仓库/车间模型", 因为Intel的10nm制程没有Apple M1的5nm制程精密, 
  所以没办法象 Apple M1 那样集成大内存, 使用标准的仓库/车间模型, 
  只能使用没有集成大内存的变种"调度中心（虚拟的全局统一仓库, 集成层或平台, 企业集团的母公司）"模式, 
  并通过加大缓存改善没有集成大内存的缺点, ，这相当于实现了把大型仓库分解为两级仓库：
  小型集成仓库（缓存）和大型外部仓库（内存）。

- 2023.10.25高通推出对标Apple的M系列SoC的骁龙 X Elite

- 2024年6月，Intel开始推出仓库/车间模型SoC: Lunar Lake

  2024年6月，Intel开始推出仓库/车间模型SoC，至此，两大主流CPU（ARM和x86）均已加入，
  宣告CPU/SoC全面进入我创造的仓库/车间模型时代，统一硬件领域。

  三年前，我预言Intel必然要推出仓库/车间模型SoC，x86 CPU实现不佳，过于复杂臃肿，功耗大，发热大，
  最好使用RISC-V加x86兼容层(或x86 CPU), 在技术革新的同时进军PC和物联网，一举三得，
  Intel也准备花20亿美元收购高性能RISC-V的领先厂商SiFive，可惜SiFive不想卖。
  Intel自行从头开始设计RISC-V太费时间了，会贻失商机，只好硬着头皮改造x86 CPU。

  仓库/车间模型SoC需要精密制程，Intel拼命花高价和Apple一起获得台积电3nm制程的优先制造权，
  可惜x86 CPU实现不佳，过于复杂臃肿，功耗大，使用3nm制程制造出来的仓库/车间模型SoC，
  竟然不如5nm制程制造出来的Apple M1，而且功耗大，发热大，体积大，只能推出桌面PC版，
  无法推出笔记本电脑所需要的低功耗版。要解决Intel目前的难题，其实也很简单，
  有好多个方案可以选择，我已解决了主要的方向性、系统性、架构性、原则性问题，
  这些小问题我就不讲了，算做课后作业吧！:-)

  目前，Apple(ARM)、高通(ARM)、Intel(x86)三大CPU厂商已推出仓库/车间模型SoC，
  第四大厂商AMD别无选择，不跟随只有死路一条。事实上AMD也于2024年6月推出不包含内存的SoC Ryzen AI 300，
  应该是没有抢到3nm精密制程优先制造权和研发进度的问题，后续一定会推出仓库/车间模型SoC。
  至此CPU/SoC全面进入我创造的仓库/车间模型时代，统一硬件领域。

  主要的PC配件厂商好象只有nvidia我还没有批评过, 以前看过一篇H100的架构文章, 本想批评一下,
  因为太忙拖到H200出来了也没写, 过时的老产品就不想写了, 虽然H100好象还是卡脖子产品,
  我写文章一向比较随性, 没有特别去找H200架构的资料, 因为现在IT界软硬件架构都没有数学模型支持,
  不科学, 找问题太容易!

  在IT领域，底层硬件技术决定上层软件技术，软件领域必然也要进入我创造的仓库/车间模型时代，
  统一整个IT领域。

  我宣称以我的基于数学模型的仓库/车间模型理论为核心统一了多个行业理论体系，为什么我只抓着IT行业打？
  道理很简单，在街头流氓斗殴时，都是钉着带头的、跳得最欢的那个打，把他打服了，其他人也就服了，
  这个道理也适用于科学领域，目前IT业号称高科技的当红炸子鸡，渗透到各行各业，流行度、知名度、应用度最高，
  最崇尚数学偏又核心底层软硬件系统构造方法学没有数学模型支持，而这是我的理论的最大优势，
  以我的理论最强优点攻击最强行业的最大弱点，高举数学旗帜，降维打击，如摧枯拉朽，一击即溃，攻击效果最大、
  效率最高、速度最快、震憾力最强。最强行业被击败了，其他行业自然顺服，万国来朝，学术界第一个理论帝国成立，
  天可汗、学术界始皇帝、大成就悟道者、道家科学派创始人、科学仙帝、科学道祖林鹏程的千秋伟业大功告成，
  千秋万载，一统学界！

  ```
  所有真理都经历三个阶段：
  1. 它被嘲笑。
  2. 它被强烈反对。
  3. 它被认为是不言而喻的真理。
      ---- 叔本华
  ```
  
  显然，我的理论已经达到第3阶段了。

  我发现最近这几年，我公开发布的已实现的预言或断言100%正确，口含天宪，金口玉言，“言出法随”大神通大成了！

参考文献

- 2021-06-11, Paul Alcorn, [Intel Offers $2 Billion for RISC-V Chip Startup SiFive: Bloomberg](https://www.tomshardware.com/news/intel-offers-dollar2-billion-for-risc-v-startup-sifive-bloomberg)
  
- 2021.10.22, Anton Shilov, [Intel's Attempt to Acquire SiFive for $2 Billion Fell Apart, Report Claims](https://www.tomshardware.com/news/intel-failed-to-buy-sifive)

- 2022-02-14, Agam Shah, [Intel's plan to license x86 cores for chips with Arm, RISC-V and more inside](https://www.theregister.com/2022/02/14/intel_x86_licensing/)

- [为什么我的"仓库/车间模型"能做到高性能低功耗(以Apple, Intel, 高通为例)](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/why_wwmodel_fast.md)

- [未来的OS内核将是一个面向数据的调度器（带有计算机硬件和软件集成架构图）](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/OS_as_DB_cn.md)

- 2024.06.03, Gavin Bonshor, [Intel Unveils Lunar Lake Architecture: New P and E cores, Xe2-LPG Graphics, New NPU 4 Brings More AI Performance](https://www.anandtech.com/show/21425/intel-lunar-lake-architecture-deep-dive-lion-cove-xe2-and-npu4)

- 2024.06.10, PChome, [PC鲜辣报：AMD双平台新U齐发 英特尔展示Lunar Lake](https://www.msn.cn/zh-cn/news/other/pc%E9%B2%9C%E8%BE%A3%E6%8A%A5-amd%E5%8F%8C%E5%B9%B3%E5%8F%B0%E6%96%B0u%E9%BD%90%E5%8F%91-%E8%8B%B1%E7%89%B9%E5%B0%94%E5%B1%95%E7%A4%BAlunar-lake/ar-BB1nVqrQ?ocid=BingNewsSerp)

- 2024.06.12, 电脑报, [科普+八卦: “退回”8核8线程的Lunar Lake表现如何？英特尔颠覆式变革目的何在？](https://new.qq.com/rain/a/20240612A02DFW00)

- 2024.06.13, RICH WOODS, [Arm says it wants all Snapdragon X Elite laptops destroyed, The legal battle between Arm and Qualcomm continues](https://www.xda-developers.com/arm-says-it-wants-all-snapdragon-x-elite-laptops-destroyed/)

- 2021-06-14, 首发在新浪微博.
- 2021-06-15, 发布在 github, twitter, reddit/programming.
- 在reddit r/programming有一个很好的讨论。[链接](https://www.reddit.com/r/programming/comments/o0gxy3/prediction_intel_will_use_riscv_plus_x86/)

----

# 预测: Intel和Microsoft都在向“仓库/车间模型”过渡(2021-06-22)

从[《测试：Windows 11 提升了 big.LITTLE x86 CPU 的性能》(2021-06-21)](https://os.51cto.com/art/202106/667326.htm)
这篇文章看，Intel即将推出类似ARM big.LITTLE设计的x86 CPU，
AMD也有类似计划。
我认为是这是Intel向Apple M1（ARM）“仓库/车间模型”CPU过渡，
同时，微软泄露的 Windows 11 也改进调度设计，以支持Intel和AMD。

我认为Intel本来CPU在性能和节能都输给了Apple M1，
这时再搞大小核，恐怕性能与Apple M1的差距越来越大，
缩小一点节能差距没有什么大意义，
再说Apple 都准备推出 M2了，M1虽然尚未完全实现“仓库/车间模型”，就已经是No. 1了，M2将继续扩大优势。 
只能解释Intel这个新CPU仅是用来先模仿Apple M1的ARM设计，
再继续演化为“仓库/车间模型”CPU的过渡产品。

在除Apple M1外的其他ARM和RISC-V的仓库/车间模型CPU出现前,
MS与Intel和AMD一荣俱荣一损俱损，只能死撑，
在 Windows 11 中继续给予支持，
反正“仓库/车间模型”也是早晚要支持的，
顺手为，也不费事。

如果Intel、AMD和其它ARM和RISC-V生产商不生产“仓库/车间模型”CPU，
MS就算学Apple自己上阵开发CPU，也不可能跑去跪求Apple让M1运行Windows,
就算去了Apple也不答应. 最终导致windows失败。

当可运行Windows的ARM和RISC-V的“仓库/车间模型”CPU出现后，
微软就随时可以甩开Intel和AMD，
因为Apple用M1仿真运行以前的x86应用也非常好，
证明了从x86移到“仓库/车间模型”CPU很容易。
以前MS Windows运行在x86主要是因为x86比其他CPU性能好，
高通这个ARM生产商不给力，合作多年，Windows on ARM 一直表现不佳。
但现在这个障碍不存在了，而且x86明显过时了，
Intel硬生生地在一个RISC内核上再加一层x86马甲完全是画蛇添足，
该淘汰时就淘汰，留来留去留成绞索带。

intel都准备开放x86许可，以前可是严封死守的，
看来是真的是放弃了，准备回收点残余价值。

微软Windows 11的DirectStorage技术使系统更加向“仓库/车间模型”演进，
CPU和GPU更加向独立不交互的车间定义演进，更加以内存（仓库）为中心。

再加上神秘的新调度器，铺天盖地的Windows11宣传，往往只描述外在的UI和功能，
但最重要的系统发动机----调度器，却只在Intel即将推出的大小核CPU宣传中一笔带过，
专为支持Intel新的大小核CPU开发, 
我认为Windows11新调度器和Intel新的大小核CPU都是再类似Apple M1的“仓库/车间模型”演进中的过渡产品。

注：Apple M1是一个由下列组件构成， 和我的“仓库/车间模型”的星形图表现形式一模一样。

1. 8 核 CPU
2. 8 核 GPU
3. 统一内存
4. SSD 控制器
5. 机器学习任务的神经引擎，例如语音识别和相机处理
6. 内置视频解码器/编码器，用于节能转换视频文件
7. 用于处理加密的 Secure Enclave
8. 用于处理数学密集型功能（如解压缩音乐文件）的数字信号处理器
9. 用于加速图像处理应用程序完成任务的图像处理单元

以统一内存为中心仓库，让 CPU、GPU 和其他内核相互交换信息，且可同时访问内存，无需复制即可访问相同的内存池，可加快信息交换速度，从而提高整体性能。

最后，IT业真正的现代工业化新时代即将来临，
想学“仓库/车间模型”要趁早，落后是要被淘汰的。

----

# 预测："高通"将使用我的"仓库/车间模型"，以对标Apple M1 (2021-07-03)

2021年7月3日
《Qualcomm's new CEO eyes dominance in the laptop markets》，
从内容上看, 对标的是Apple M1, 

《Qualcomm plans to design an M1 competitor for PCs—sans ARM》，
高通新任CEO Amon表示，
该公司在生产笔记本电脑芯片以直接与苹果M1竞争方面没有问题，
这主要是因为高通现在雇佣了苹果高度宣传的突破背后的一些关键人才.

今年，高通以14亿美元收购了初创公司Nuvia。
Nuvia 是由前苹果员工创立的，
他们在 M1 推出之前曾参与过苹果硅的转型。

另外, 《Samsung and AMD will reportedly take on Apple’s M1 SoC later this year》，
三星将采用AMD GPU + ARM CPU也来凑热闹, 
但它自家的ARM CPU水平不够. 

评论

我想"高通"眼红Apple M1的成就, 这个拖微软后腿的队友, 
终于开始动弹一下了, 看样子, 也是会使用我的"仓库/车间模型", 从文章上看,至少可以确定的是, 
高通要把它的5G芯片和Nuvia CPU核心都作为车间塞进整个芯片里。

如果Intel和AMD如果不加快"仓库/车间模型"的开发速度, 
微软真要转向高通了, 这时就真没这哥俩什么事了! 

参考

- [高通首个采用 Nuvia 架构设计笔记本芯片有望明年发布](https://www.cnbeta.com/articles/tech/1148359.htm)

- [Qualcomm plans to design an M1 competitor for PCs—sans ARM](
https://arstechnica.com/gadgets/2021/07/qualcomm-ceo-we-can-beat-apple-because-we-poached-talent-from-them/)

- [Qualcomm's new CEO eyes dominance in the laptop markets](https://www.reuters.com/technology/qualcomms-new-ceo-eyes-dominance-laptop-markets-2021-07-01/)

- [Samsung and AMD will reportedly take on Apple’s M1 SoC later this year](https://arstechnica.com/gadgets/2021/05/report-the-samsung-amd-exynos-soc-will-be-out-for-laptops-this-year/?itm_source=parsely-api)

----

# 评论：Intel的XPU和oneAPI （2021-06-26）

2020-11-11, Intel宣布XPU和oneAPI计划, 和Apple M1同一天发布。
我发现XPU计划对未来异构计算需求的表述和我的“仓库/车间模型”是一致的，
但是Intel的架构设计并没有“仓库（及其调度器）”这个中心，
只是把这些XPU简单排列在一起，并把相关的API打包在一起，
叫做oneAPI。

我一开始以为Intel已经准备象Apple M1一样使用我的“仓库/车间模型”,
没想到只是一个Intel对API的微改良计划。
XPU和oneAPI计划只标准化了调用车间的接口（相当于供调度器使用的接口），
因为缺乏仓库定义，却没有对车间的输入输出，协作，管理，调度做出定义。
违反了如下原则：单一领导和统一调度，集中与分散，等级链，明确，有序，标准化。
因此，从软硬件架构上看，在全局统筹优化调度和数据存取效率等方面都比不上我的“仓库/车间模型”。


Intel oneAPI号称为“一个跨行业、开放、基于标准的统一编程模型”，
开发人员可以自由选择最佳架构以满足其工作量/应用程序需求，
同时在多个架构中使用单个代码库。
这使得开发人员能够最大限度地提高跨架构性能并最大限度地降低开发成本，
同时允许他们自由地在不同的 XPU 架构中展示和利用尖端功能。
通过用 OneAPI 抽象硬件异质性。

其实，总结起来，Intel的方案和以前的异构计算没有什么不同，
只是把不同API重构，尽量让各类不同的API看起来相似，
然后象大杂烩一样，把API打包在一起而已。
大概类似于R语言的tidyverse系列包而已。

参考：

- [(2020-11-11) Intel Executing toward XPU Vision with oneAPI and Intel Server GPU](https://www.intel.com/content/www/us/en/newsroom/news/xpu-vision-oneapi-server-gpu.html#gs.4t5vlr)

- [(2021-4-12) The evolution of XPU and the critical role of software](https://medium.com/intel-tech/the-evolution-of-xpu-and-the-critical-role-of-software-c46970dfcbe9)

<table>
<tr>
<td width="40%">Intel XPU and oneAPI</td>
<td>Warehouse/Workshop Model</td>
</tr>
<tr>
<td width="40%"><img src=./image/Intel_XPU_oneAPI.png></td>
<td><img src=./Computer-Hardware-Star-WWM.svg></td>
</tr>
</table>

----

# 评：AMD Infinity Fabric 架构

x86+RISC-V异构计算架构是我的创新，2021年6月14日发表在微博，
我2021年6月15日在github的博客发表，隔几天发现这篇AMD专利申请文章了。
由`Joel Hruska`于2021年6月15日写的
[《AMD Is Working on Its Own Hybrid x86 CPU: Patent Filing》](https://www.extremetech.com/computing/323713-amd-is-working-on-its-own-hybrid-x86-cpu-patent-filing)
这篇文章的最早评论2021-06-16，这篇是根据以前的旧文章修改的，
以前的旧文章只是类似于ARM的`big.Little`核，专利的内容是在big核与Little核之间的任务转移方法。
该文仅在开头和结尾增加一小段`Hybrid x86 CPU`表述，非常突兀和不协调。


这篇文章提到了AMD的[“METHOD OF TASK TRANSITION BETWEEN HETEROGENOUS PROCESSORS”](https://www.freepatentsonline.com/y2021/0173715.html)
专利，它的内容是在big核与Little核之间的任务转移方法，
依据我的“仓库/车间模型”的10原则，AMD的这项专利技术是毫无必要的，
违反了任务分工原则、有序原则、明确原则。

从文章示意图上看，AMD以Infinity Fabric总线为中心，
实现CPU-CPU之间的任务转移，未来打算实现GPU-GPU，CPU-GPU之间的任务转移，
即车间之间的互联，我在制造工业内，还未见到过这种车间任意互联的架构。
这是个网状结构，非常混乱和复杂，扩展性差，灵活性差，数据利用效率差。
我认为它在同类处理器之间的任务转移相对容易，
在不同类处理器之间的任务转移是复杂和困难的，效果也不会太好。
我认为它远远不如我的仓库/车间模型简单、可靠、灵活、扩展性强，
以仓库（数据）为中心，数据存取效率高，大致类似我以前发的[微软数据工厂/管道架构和仓库/车间模型的比较](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/diff_WWModel_AzureDataFactoryPipe_cn.md)
实际上,尽管Apple M1尚未完全实现仓库/车间模型，但它已经是第一名了。

<table>
<tr>
<td>AMD fabric 1</td>
<td>AMD fabric 2</td>  
<td>Warehouse/Workshop Model</td>
</tr>
<tr>
<td><img src=./image/AMD_fabric.jpg></td>
<td><img src=./image/AMD_fabric2.jpg></td>  
<td><img src=./Computer-Hardware-Star-WWM.svg></td>
</tr>
</table>

----

# RISC-V VS. ARM

RISC-V的可扩展架构非常出色。它相当于ARM的可扩展版本（例如Apple M1芯片）。
只要扩展的标准化工作做得好，前景就相当不错。

其他ARM制造商也想复制Apple M1的成功，但我还没有听说他们有任何标准工作，
这将导致基于ARM的soc系统的碎片化。这种局面不改变的话, 
最终将导致它输给RISC-V，RISC-V正在努力使扩展标准化。

后记：

从2022-11-01文章[《2024年后，ARM芯片只能用公版？高通被禁用自研GPU》](https://www.51cto.com/article/721715.html)上看：

> ARM 不打算在基于 ARM 架构 SoC 中允许外部 GPU、NPU 或 ISP 存在，
> 包括高通的 Adreno，三星与 AMD 合作使用的 GPU，
> 所有人都需要改回 ARM 的「公版」。

ARM采用了我在一年前（2021-12-06）的看法，只是这会使用ARM的各路诸侯王很不满，
ARM的做法是对的，应趁着垄断地位还在的时侯标准化其SoC架构，
否则如果基于ARM的SoC碎片化必败。
