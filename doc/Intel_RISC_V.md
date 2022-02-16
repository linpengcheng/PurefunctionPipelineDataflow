# Prediction: Intel will use "RISC-V plus x86 compatibility layer" or "RISC-V plus x86 heterogeneous computing architecture" to develop a new generation of "warehouse/workshop model" CPU

Copyright © 2021.06.14 Lin Pengcheng. All rights reserved.

Prediction: Intel will use RISC-V plus x86 compatibility layer to develop a new generation of "warehouse/workshop model" CPU. 
It will not only reverse the competitive situation with Apple M1, but also open up the market for IoT CPUs.

If developing the x86 compatibility layer is too troublesome, there is a quick solution, 
because my "warehouse/workshop model" naturally supports heterogeneous computing and can 
provide 1 or 2 x86 cores in the CPU to execute x86 instructions specifically to provide compatibility.

Intel has been in a lot of trouble recently. There is an Apple M1 chip using my warehouse/workshop model on the front, 
which not only greatly beats Intel’s CPU in performance, but also maintains a greater energy-saving advantage. 
In addition, as I said in the blog post, M1 also There is a lot of space for optimization. 
The new M2 is said to be coming out soon, and AMD is catching up. Intel is in a hurry to change its CEO.

Intel’s original technology accumulation and development route can be said to be useless. 
If it is useful, it has been put into the market long ago, and now it can only be completely updated..

Now the only architecture that fully surpasses the "von Neumann architecture" is my "warehouse/workshop model". 
I think Intel has no choice but to "warehouse/workshop model".

If ARM and RISC-V manufacturers join the "warehouse/workshop model" CPU competition, it will pose a serious threat to Intel. 
I have not seen any news in this regard, but at least one or two major manufacturers should join the competition,
The market has entered a stage of fierce competition. In addition, Microsoft's support is very important, 
especially Microsoft and Qualcomm have a close cooperative relationship to jointly develop the "Windows/ARM PC".

The huge x86 stock market will still give Intel a period of funding and buffer space, 
and the future Internet of Things market will be even broader. 
About news of "Intel Offers $2 Billion for RISC-V Chip Startup SiFive",
RISC-V is open source and can be extended proprietary. 
It is the best choice for Intel with excellent CPU design talents, 
and it is also the best choice for Intel to strive for market leadership. 

Danger and opportunity coexist. This is the moment that determines the life and death of Intel, 
just like the phoenix nirvana, or rebirth from ashes, or burned to death.

Intel CEO Pat Gelsinger's recent announcement that the company would begin licensing its own x86 processor designs 
to other firms as part of its new IDM 2.0 initiative was surprising. 
In view of Intel's previous licensing policy, I think this is Intel's preparation to abandon x86.
Intel’s x86 processor design license is likely to target Chinese companies.
I think x86 is an outdated design that is about to be phased out.
Chinese companies should not bid too high.

postscript:

- 2022.2.14 News: "Intel's plan to license x86 cores for chips with Arm, RISC-V and more inside"

  I think Intel should use my solution, 
  Because if Intel wants to implement this solution it has to use my "Warehouse/Workshop Model",
  Because Intel's 10nm process is not as precise as the Apple M1's 5nm process, 
  So it can't integrate as much memory as the Apple M1, ie: can't use the standard warehouse/workshop model, 
  can only use variant "dispatch center (virtual global unified warehouse, 
  integration layer or platform, the parent company of the enterprise group)" model, 
  and improve the shortcomings of not integrating large memory by increasing the cache, 
  This seems to implement a large repository as a two-level repository: 
  a small integrated warehouse (cache) and a large external warehouse (memory).

Reference: 

- 2021-06-11,  Paul Alcorn, [Intel Offers $2 Billion for RISC-V Chip Startup SiFive: Bloomberg](https://www.tomshardware.com/news/intel-offers-dollar2-billion-for-risc-v-startup-sifive-bloomberg)
- 2022-02-14, Agam Shah, [Intel's plan to license x86 cores for chips with Arm, RISC-V and more inside](https://www.theregister.com/2022/02/14/intel_x86_licensing/)
- [The future OS kernel will be a data-oriented scheduler (with Computer hardware and software integration architecture diagram)](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/OS_as_DB_en.md)
- [Why my "warehouse/workshop model" can achieve high performance and low power consumption (take Apple M1 chip, Intel AVX-512, Qualcomm as examples)](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/why_wwmodel_fast_en.md)

- 2021-06-14, I published it on Chinese Sina Weibo.
- 2021-06-15, I published it on github, twitter, reddit/programming.
- There is a good discussion in reddit r/programming. [Link](https://www.reddit.com/r/programming/comments/o0gxy3/prediction_intel_will_use_riscv_plus_x86/)

----

Attachment: Comment: AMD Infinity Fabric Architecture

x86+RISC-V heterogeneous computing architecture 
is my innovation, published on Chinese Weibo on June 14, 2021,
I published it on the github blog on June 15, 2021, 
and found this article a few days later,
Written by `Joel Hruska` on June 15, 2021
[《AMD Is Working on Its Own Hybrid x86 CPU: Patent Filing》](https://www.extremetech.com/computing/323713-amd-is-working-on-its-own-hybrid-x86-cpu-patent-filing)
The earliest comment of this article is 2021-06-16, 
this article is modified based on the previous old article,
The previous old article is just similar to ARM's `big.Little` core,
The content of the patent is ["METHOD OF TASK TRANSITION BETWEEN HETEROGENOUS PROCESSORS"](https://www.freepatentsonline.com/y2021/0173715.html).
it is a task transition between the big core 
and the little core. The article only adds a short 
paragraph of `Hybrid x86 CPU` expression 
at the beginning and end, 
which is very abrupt and inconsistent.

This article mentions AMD’s ["METHOD OF TASK TRANSITION BETWEEN HETEROGENOUS PROCESSORS"](https://www.freepatentsonline.com/y2021/0173715.html)
Patent, its content is the task transition between 
the big core and the little core,
According to my 10 principles of "Warehouse/Workshop Model", 
AMD’s patented technology is unnecessary.
Violated the principles: Division of tasks, 
Order, and Definiteness.

From the schematic diagram of the article, 
AMD is centered on the Infinity Fabric bus.
Realize the task transition between CPU-CPU, 
and plan to realize the task transition 
between GPU-GPU and CPU-GPU in the future.
That is, the interconnection between workshops. 
In the manufacturing industry, I have not seen 
this kind of architecture for arbitrary 
interconnection of workshops.
This is a network structure, very chaotic 
and complicated, with poor scalability, 
poor flexibility, and poor data utilization efficiency.
I think it’s relatively easy to transfer tasks between 
similar processors, Task transfer between different 
types of processors is complicated and difficult, 
and the effect is not very good.
I think it is far inferior to my `warehouse/workshop model` 
which is simple, reliable, flexible and extensible.
With warehouse (data) as the center, 
data access efficiency is high, 
which is roughly similar to the 
[Comparison of Microsoft Data Factory/Pipeline Architecture and Warehouse/Workshop Model](https://github.com/linpengcheng/PurefunctionPipelineDataflow/blob/master/doc/diff_WWModel_AzureDataFactoryPipe.md)
In fact, although Apple M1 has not yet fully realized 
the `warehouse/workshop model`, the Apple M1 is already No. 1.

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

Attachment: RISC-V VS. ARM (by 2021.12.06)

I think the expandable architecture of RISC-V is excellent. 
It is equivalent to an expandable version of ARM (e.g. Apple M1 chip).
As long as the extended standardization work is done well, 
the prospects are quite good.

I think other ARM manufacturers also want to replicate the success of Apple M1 chip, 
but I have not heard that they have any standard work, 
which will lead to fragmentation of ARM-based SOC systems. 
In the end, it will lose to RISC-V, which worked hard to standardize the extension.

