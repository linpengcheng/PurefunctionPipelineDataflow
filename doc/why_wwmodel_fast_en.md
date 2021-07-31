# Why my "warehouse/workshop model" can achieve high performance and low power consumption (take Apple, Intel, Qualcomm as examples)

Copyright © 2021-07-28 Lin Pengcheng, all rights reserved.

## Summary

The "Warehouse/Workshop Model" is derived from the large-scale industrial production of the manufacturing industry, 
and is most suitable for large-scale and high-load heterogeneous parallel computing scenarios. Although when it is used in Apple M1 chip, 
Apple M1 chip not only becomes the fastest chip in the world, but also maintains an extremely low Power consumption. 
But in fact, its best application scenarios are supercomputers or cloud computing. 
Consumer-grade chips such as the Apple M1 chip cannot reach its potential.

Why my "warehouse/workshop model" can achieve high performance and low power consumption? 
This is the display of the advantages of large-scale production and task division in the computer field. 
In addition, the warehouse is the center and the workshop is uniformly scheduled. 
The overall optimization effect is good, and the data access and exchange performance is high.

If a task is independently used as a workshop, and its scale benefit exceeds the cost of opening it, 
then it should be set up as a workshop, paying attention to exceeding a certain production scale (computing amount). 
Professional workshops have lower production costs (power consumption) and higher production efficiency (performance).

For computer SOC chips, its space is very limited. 
Unlike software projects, the cost of increasing the workshop is very low.
It is necessary to divide the workshop into internal (integrated) workshops and external workshops. 
As long as the added ASIC (Application Specific　Integrated Workshop) is frequently used enough, 
and the overall benefit generated exceeds the benefit of using this part of the space as a general-purpose core (CPU, general workshop), 
the ASIC (Application Specific　Integrated Workshop) can be used Join the SOC chip and become an internal workshop. 
ASIC has the advantages of smaller size, lower power consumption, higher reliability, 
higher performance, stronger confidentiality, and lower cost.

From the warehouse workshop model, generally must include three components:

- Warehouse: memory
- Workshop
  - CPU
  - GPU

## Apple M1

2020-11-30, [Developer Delves Into Reasons Why Apple's M1 Chip is So Fast](https://www.macrumors.com/2020/11/30/m1-chip-speed-explanation-developer/):

> In addition to the CPU (with high-performance and high-efficiency cores) and GPU, 
> the M1 has a Neural Engine for machine learning tasks like voice recognition and camera processing, 
> a built-in video decoder/encoder for power-efficient conversion of video files, 
> the Secure Enclave to handle encryption, 
> the Digital Signal Processor for handling mathematically intensive functions like decompressing music files, 
> and the Image Processing Unit that speeds up tasks done by image processing apps.

> there's also a new unified memory architecture that lets the CPU, GPU, 
> and other cores exchange information between one another, and with unified memory, 
> the CPU and GPU can access memory simultaneously rather than copying data between one area and another. 
> Accessing the same pool of memory without the need for copying speeds up information exchange for faster overall performance.

From the perspective of use effect, these ASICs added by Apple M1 are suitable.

## Intel

2020-7-13, [Linus Torvalds: I hope Intel's AVX-512 'dies a painful death'](https://www.zdnet.com/article/linus-torvalds-i-hope-intels-avx-512-dies-a-painful-death/):

> Linus (Linux author): I hope AVX-512 dies a painful death, 
> and that Intel starts fixing real problems instead of trying to create magic instructions 
> to then create benchmarks that they can look good on 

> I think they are largely a complete waste of transistors and effort, 
> and I think the amount of time spent on them 
> – both by hardware people and by software people trying to use them – 
> has been largely time wasted

The main scenarios of AVX-512 are image/audio and video processing, data analysis, 
scientific computing, data encryption and compression, and deep learning. 
It can do better with the existing GPU，
If this is only used as a component to obtain higher benchmarks scores, 
it would be too wasteful.

For these scenarios, Apple M1 separates them as a Application Specific　Integrated Workshop, 
using ASICs to achieve higher performance and low power consumption.
  
## Qualcomm

2021-7-3, [Qualcomm plans to design an M1 competitor for PCs—sans ARM](https://arstechnica.com/gadgets/2021/07/qualcomm-ceo-we-can-beat-apple-because-we-poached-talent-from-them/):

> Qualcomm's new CEO, Cristiano Amon, says the company will have no problem producing laptop chips 
> to compete directly with Apple's M1—mainly because Qualcomm now employs some of 
> the key minds behind Apple's highly publicized breakthrough.

> This SoC would include a 5G modem as well as a CPU.

I think：

- If the chip is used in small devices such as mobile phones, 
  when power consumption, size, and cost are important, and 5G usage is high, 
  it is reasonable to integrate the 5G chip into the SOC chip.

- If the chip is used in a notebook computer, performance is very important at this time, 
  and the 5G usage is not so high. At this time, it is unreasonable to integrate the 5G chip into the SOC chip, 
  and it should be used as an external chip (workshop).

## Reference

- 2018-2-13, [The Grand Unified Programming Theory: The Pure Function Pipeline Data Flow with Principle-based Warehouse/Workshop Model](https://github.com/linpengcheng/PurefunctionPipelineDataflow)

- 2020-11-30, [Developer Delves Into Reasons Why Apple's M1 Chip is So Fast](https://www.macrumors.com/2020/11/30/m1-chip-speed-explanation-developer/)

- 2020-7-13, [Linus Torvalds: I hope Intel's AVX-512 'dies a painful death'](https://www.zdnet.com/article/linus-torvalds-i-hope-intels-avx-512-dies-a-painful-death/)

- 2020-8-20, [Intel defends AVX-512 against critics who wish it to die a 'painful death'](https://www.pcworld.com/article/3571956/intel-defends-avx-512-against-critics-who-wish-it-to-die-a-painful-death.html)

- 2021-7-3, [Qualcomm plans to design an M1 competitor for PCs—sans ARM](https://arstechnica.com/gadgets/2021/07/qualcomm-ceo-we-can-beat-apple-because-we-poached-talent-from-them/)

- 2021-7-1, [Qualcomm's new CEO eyes dominance in the laptop markets](https://www.reuters.com/technology/qualcomms-new-ceo-eyes-dominance-laptop-markets-2021-07-01/)
