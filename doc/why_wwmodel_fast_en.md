# Why "warehouse/workshop model" high performance and low power consumption (take Apple, Intel, Qualcomm as examples)

Copyright © 2021-07-28 Lin Pengcheng, all rights reserved.

## Summary

The "Warehouse/Workshop Model" is derived from the large-scale industrial production of the manufacturing industry, and is most suitable for large-scale and high-load computing scenarios. Although when it is used in Apple M1 chip, Apple M1 chip not only becomes the fastest chip in the world, but also maintains an extremely low Power consumption. But in fact, its best application scenarios are supercomputers or cloud computing. Consumer-grade chips such as the Apple M1 chip cannot reach its potential.

Why can the "warehouse/workshop model" achieve high performance and low power consumption? This is the demonstration of large-scale industrial-scale production and task division in the computer field.

If a task is independently used as a workshop, and its scale benefit exceeds the cost of opening it, then it should be set up as a workshop, paying attention to exceeding a certain production scale (computing amount). Professional workshops have lower production costs (power consumption) and higher production efficiency (performance).

For computer SOC chips, its space is very limited. Unlike software projects, the added cost is very low. It is necessary to divide the workshop into internal (integrated) workshops and external workshops. Only the added dedicated core (ASIC, professional workshop) is enough Commonly used, when the overall benefit exceeds the benefit of using this part of the space as a general-purpose core (CPU, general workshop), the dedicated core (ASIC, professional workshop) can be added to the SOC chip to become an internal workshop.

From the warehouse workshop model, generally must include three components:

- Warehouse: memory
- Workshop
  - CPU
  - GPU

## Apple M1

> In addition to the CPU (with high-performance and high-efficiency cores) and GPU, the ‌M1‌ has a Neural Engine for machine learning tasks like voice recognition and camera processing, a built-in video decoder/encoder for power-efficient conversion of video files, the Secure Enclave to handle encryption, the Digital Signal Processor for handling mathematically intensive functions like decompressing music files, and the Image Processing Unit that speeds up tasks done by image processing apps.

From the perspective of use effect, these ASICs added by Apple M1 are suitable.


## Intel

> Linus (Linux author): I hope AVX-512 dies a painful death, and that Intel starts fixing real problems instead of trying to create magic instructions to then create benchmarks that they can look good on ... I think they are largely a complete waste of transistors and effort, and I think the amount of time spent on them – both by hardware people and by software people trying to use them – has been largely time wasted

Linux author Linus believes that in order to improve CPU performance evaluation scores, Intel forcibly stuffed things like AVX-512 into the CPU, which caused the CPU core to be bloated. In order to improve the computing performance in a few specific usage scenarios, most of the ordinary ones were affected. User experience. And this part of the task is more suitable to be done with GPU, it is not necessary to put it on the CPU, the purpose is only to run the score, the realization is too wasteful.

  The application scenarios of AVX-512 are mainly large-scale operations such as image/audio and video processing, data analysis, scientific computing, data encryption and compression, and deep learning. Apple M1 uses ASIC to specifically higher performance and lower power consumption.
  
## Qualcomm

《Qualcomm plans to design an M1 competitor for PCs—sans ARM》，
> Qualcomm's new CEO, Cristiano Amon, says the company will have no problem producing laptop chips to compete directly with Apple's M1—mainly because Qualcomm now employs some of the key minds behind Apple's highly publicized breakthrough.

> This SoC would include a 5G modem as well as a CPU.

I think：

- If the chip is used in small devices such as mobile phones, when power consumption, size, and cost are important, and 5G usage is high, it is reasonable to integrate the 5G chip into the SOC chip.

- If the chip is used in a notebook computer, performance is very important at this time, and the 5G usage is not so high. At this time, it is unreasonable to integrate the 5G chip into the SOC chip, and it should be used as an external chip (workshop).

## Reference

- [Developer Delves Into Reasons Why Apple's M1 Chip is So Fast](https://www.macrumors.com/2020/11/30/m1-chip-speed-explanation-developer/)

- [Linus Torvalds: I hope Intel's AVX-512 'dies a painful death'](https://www.zdnet.com/article/linus-torvalds-i-hope-intels-avx-512-dies-a-painful-death/)

- [Intel defends AVX-512 against critics who wish it to die a 'painful death'](https://www.pcworld.com/article/3571956/intel-defends-avx-512-against-critics-who-wish-it-to-die-a-painful-death.html)

- [Qualcomm plans to design an M1 competitor for PCs—sans ARM](
https://arstechnica.com/gadgets/2021/07/qualcomm-ceo-we-can-beat-apple-because-we-poached-talent-from-them/)

- [Qualcomm's new CEO eyes dominance in the laptop markets](https://www.reuters.com/technology/qualcomms-new-ceo-eyes-dominance-laptop-markets-2021-07-01/)
