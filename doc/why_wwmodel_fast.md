# 为什么我的"仓库/车间模型"能做到高性能低功耗(以Apple, Intel, 高通为例)

版权所有 © 2021-07-28 林鹏程， 保留所有权利。

## 综述

"仓库/车间模型"源自制造工业的大工业生产,最适合大批大量高负载的大规模计算场景. 虽然它应用在 Apple M1 芯片时, 
M1 不仅成为世界上最快的芯片,而且保持极低的功耗. 但实际上它的最佳应用场景是超级计算机或云计算, 
Apple M1 芯片的小身板不能发挥出它的优越性, 只是开席前的小菜一碟。 

为什么"仓库/车间模型"能做到高性能低功耗呢?这就是在大工业规模生产和任务分工的优点在计算机领域的展现.
另外以仓库为中心统一调度，全局统筹优化效果好，且数据存取和交换性能高。

如果一项任务独立作为一个车间后, 它产生的规模效益超过开设它的成本, 那么应该把它设立为一个车间, 
注意: 在超过一定生产规模(计算量),专业车间的生产成本(功耗)较低且生产效率(性能)更高.


对于计算机SOC芯片，它的空间很有限，不象软件项目那样增加车间的成本很低，
很有必要把车间分为内部（集成）车间和外部车间，只要所增加的专用核心（ASIC,专业车间）足够常用,
产生的整体效益超过把这部分空间用来做通用核心(CPU,通用车间)的效益时,
可以把该专用核心（ASIC,专业车间）加入SOC芯片，成为内部车间.
ASIC具有体积更小、功耗更低、可靠性更高、性能更高、保密性更强、成本更低等优点。

从仓库车间模型讲, 一般必须包括三大组件:

- 仓库: 内存
- 车间
  - CPU
  - GPU

## Apple M1

Apple M1 还配备了如下ASIC:

- 用于机器学习任务的神经引擎，如语音识别和相机处理
- 用于视频文件的内置视频解码器/编码器
- 用于处理加密的Secure Enclave
- 用于处理解压音乐文件等数学密集型功能的数字信号处理器
- 用于加快图像处理应用完成任务的图像处理单元

从使用效果上看, Apple M1 加入的这些ASIC是合适的.

## Intel

Linux的作者 Linus 认为 Intel 为了提高 CPU 的性能跑分，强行在 CPU 中塞入了像 AVX-512 这样的东西，
导致 CPU 内核臃肿，为了提升少数特定使用场景下的运算性能而影响了大部分普通用户的使用体验。

AVX-512 的主要场景为图像/音视频处理、数据分析、科学计算、数据加密和压缩和深度学习等大规模运算,
这部分任务用GPU来做更合适, 完全没必要放在CPU, 目的仅仅为了跑分，实现是太浪费了。

对于这些场景，Apple M1 把它们独立出来, 做为专业内部车间, 使用更专业的ASIC达到更高性能和低功耗的目标。

## 高通

《Qualcomm plans to design an M1 competitor for PCs—sans ARM》，
高通新任CEO Amon表示，
该公司在生产笔记本电脑芯片以直接与苹果M1竞争方面没有问题，
这主要是因为高通现在雇佣了苹果高度宣传的突破背后的一些关键人才.
另外, 高通要把它的5G芯片和Nuvia CPU核心都作为车间塞进整个芯片里。

我认为：

- 如果芯片是用在手机等小型设备, 功耗, 体积, 成本很重要时, 且5G使用量高时, 把5G芯片集成到SOC芯片是合理的。

- 如果芯片是用在笔记本电脑， 这时性能很重要，且5G使用量不那么高，这时把5G芯片集成到SOC芯片是不合理的，应作为外部芯片（车间）。

## 参考

- [Developer Delves Into Reasons Why Apple's M1 Chip is So Fast](https://www.macrumors.com/2020/11/30/m1-chip-speed-explanation-developer/)

- [Linus Torvalds: I hope Intel's AVX-512 'dies a painful death'](https://www.zdnet.com/article/linus-torvalds-i-hope-intels-avx-512-dies-a-painful-death/)

- [Intel defends AVX-512 against critics who wish it to die a 'painful death'](https://www.pcworld.com/article/3571956/intel-defends-avx-512-against-critics-who-wish-it-to-die-a-painful-death.html)

- [Qualcomm plans to design an M1 competitor for PCs—sans ARM](
https://arstechnica.com/gadgets/2021/07/qualcomm-ceo-we-can-beat-apple-because-we-poached-talent-from-them/)

- [Qualcomm's new CEO eyes dominance in the laptop markets](https://www.reuters.com/technology/qualcomms-new-ceo-eyes-dominance-laptop-markets-2021-07-01/)
