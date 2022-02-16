# The future OS kernel will be a data-oriented scheduler (with Computer hardware and software integration architecture diagram)

---- In the future, OS will be a DB-like, and Clojure will be the best DML

Copyright © 2021.11.15 Lin Pengcheng, all rights reserved.

In the future, OS will face the following challenges:

- More and more computers with a `Warehouse/Workshop Model` as a hardware architecture, 
  from SOC (e.g. Apple M1 chip) to supercomputers, from PC to cloud computing, 
  need to support a very large number and variety of computing units (e.g. CPU, GPU, ASIC, etc.).

- In the age of the Internet of Things, computers will connect more and more hardware.

- Massive applications & Service software.

This development trend necessitates the improvement of the OS algorithm:

- If a factory (computer system) has only one workshop (CPU), 
  then it is more efficient for the workshop (CPU) to manage the raw materials (data) by itself.

- If a factory (computer system) has many and different types of workshops (CPU, GPU, ASICs, applications & Service software), 
  then it is easier and more efficient to manage raw materials (data) 
  by a dedicated management department (warehouse, database). 
  The method can perform heterogeneous parallel computing more simply, 
  more convenient for the scheduler to perform global optimization, 
  more efficient data exchange, and improve overall resource efficiency. 
  The benefits outweigh the cost of data management.
  
How should OS evolve to adapt to this new theory and new computer architecture? 
It must use the following `Warehouse/Workshop Model`:  

- Warehouse

  - Memory: Store data, control information for various resources.
  
  - OS: Scheduler, memory management, equivalent to DB engine.
  
    - At present, the CPU is used to boot into the OS, 
      and then the OS obtains the full scheduling capability (including the CPU), 
      and the scheduling capability of the OS requires the CPU to execute.

    - In the future, it would be better to have an ASIC to replace the CPU to cooperate with the OS, 
      because this workshop is highly used and important, 
      and it is necessary to become an `independent internal workshop`.
      This ASIC is mainly responsible for scheduling and memory management (The OS kernel has only these features), 
      all internal (integrated) workshops are directly linked to memory. The workshop is independent of each other.
      Unimportant, infrequently used, slow external workshops can use bus. But the workshop should still not be interconnected.
      [see also: Why my "warehouse/workshop model" can achieve high performance and low power consumption (take Apple M1 chip, Intel AVX-512, Qualcomm as examples)](./why_wwmodel_fast_en.md)

  - DML: Just let Clojure integrate JDBC and SQL, 
    and let all core APIs natively support JDBC and OSDB, 
    and Clojure can instantly become the best DML.
    - At the application layer and script layer, Clojure is sufficient.
    - At the system layer, Clojure has a rust implementation: [ClojuRust](https://github.com/clojurust/clojurust). 
      If necessary, implementing a native compiler for a programming language is not a problem at all. 
      In addition, the JVM has GraalVM to support native compilation.
    
- Workshop

  - Hardware: CPU, GPU, ASIC, various peripherals, etc
  - Software: Various applications & Service software

Note

- The interconnection between workshops is too complex and confusing. 
  I've written [an article criticizing this kind of technology  (AMD Infinity Fabric Architecture)](./Intel_RISC_V.md) before,
  From the schematic diagram of the article, AMD is centered on the Infinity Fabric bus. 
  Realize the task transition between CPU-CPU, and plan to realize the task transition between GPU-GPU 
  and CPU-GPU in the future. That is, the interconnection between workshops. In the manufacturing industry, 
  I have not seen this kind of architecture for arbitrary interconnection of workshops. 
  This is a network structure, very chaotic and complicated, with poor scalability, poor flexibility, 
  and poor data utilization efficiency. I think it’s relatively easy to transfer tasks between similar processors, 
  Task transfer between different types of processors is complicated and difficult, and the effect is not very good. 
  I think it is far inferior to my warehouse/workshop model which is simple, reliable, flexible and extensible. 
  With warehouse (data) as the center, data access efficiency is high, which is roughly similar to 
  [the Comparison of Microsoft Data Factory/Pipeline Architecture and Warehouse/Workshop Model](./diff_WWModel_AzureDataFactoryPipe.md). 
  In fact, although Apple M1 [unified memory architecture](https://www.macrumors.com/2020/11/30/m1-chip-speed-explanation-developer/) 
  has not yet fully realized the warehouse/workshop model, the Apple M1 is already No. 1.
      
- In [Why my "warehouse/workshop model" can achieve high performance and low power consumption (take Apple M1 chip, Intel AVX-512, Qualcomm as examples)](./why_wwmodel_fast_en.md), 
  The "Warehouse/Workshop Model" is derived from the large-scale industrial production of the manufacturing industry, 
  and is most suitable for large-scale and high-load heterogeneous parallel computing scenarios. 
  Although when it is used in Apple M1 chip, Apple M1 chip not only becomes the fastest chip in the world, 
  but also maintains an extremely low Power consumption. But in fact, 
  its best application scenarios are supercomputers or cloud computing. 
  Consumer-grade chips such as the Apple M1 chip cannot reach its potential.

  Why my "warehouse/workshop model" can achieve high performance and low power consumption? 
  This is the display of the advantages of large-scale   production and task division in the computer field. 
  In addition, the warehouse is the center and the workshop is uniformly scheduled. 
  The overall optimization effect is good, and the data access and exchange performance is high.

  If a task is independently used as a workshop, and its scale benefit exceeds the cost of opening it, 
  then it should be set up as a workshop, paying attention to exceeding a certain production scale (computing amount). 
  Professional workshops have lower production costs (power consumption) and higher production efficiency (performance).

  For computer SOC chips, its space is very limited. Unlike software projects, the cost of increasing the workshop is very low. 
  It is necessary to divide the workshop into internal (integrated) workshops and external workshops. 
  As long as the added ASIC (Application Specific　Integrated Workshop) is frequently used enough, 
  and the overall benefit generated exceeds the benefit of using this part of the space as a general-purpose core (CPU, general workshop), 
  the ASIC (Application Specific　Integrated Workshop) can be used Join the SOC chip and become an internal workshop. 
  ASIC has the advantages of smaller size, lower power consumption, higher reliability, higher performance, 
  stronger confidentiality, and lower cost.
       
- Apple M1 unified memory architecture(published on November 11, 2020.) is 
  my "warehouse/workshop model"(hardware architecture section published on February 06, 2019), 
  It is an architecture supported by mathematical models, unlike "von Neumann architecture". 

Reference

- [A good discussion on reddit r/programming](https://www.reddit.com/r/programming/comments/quk3xq/in_the_future_os_will_be_a_db_and_clojure_will_be/)

- [The Math-based Grand Unified Programming Theory: The Pure Function Pipeline Data Flow with Principle-based Warehouse/Workshop Model](https://github.com/linpengcheng/PurefunctionPipelineDataflow)

  Its mathematical prototype is the simple, classic, vivid, and widely used in social production practice, 
  elementary school mathematics "water input/output of the pool". 
  My theory rebuilt the theoretical foundation of the IT industry, 
  It makes the computer theory system fully & perfectly related to mathematics in a simple and unified way: 
  from hardware integrated circuits and computer architecture, 
  to software programming methodology, architecture, programming language and so on. 
  It solve the most fundamental and core major problems in the IT industry: 
  The foundation and core of the IT theory lack mathematical support.

- [Implement relational data model and programming based on hash-map (NoSQL)](./relational_model_on_hashmap.md)

- [Everything is RMDB](./Everything_is_RMDB.md)

- [Clojure is a FP based on RMDB](./Clojure_is_FP_based_on_RMDB.md)

- [Foxpro Database-oriented programming paradigm is the development direction of the future programming language](./Mummy4Foxpro.md)

- [Why my "warehouse/workshop model" can achieve high performance and low power consumption (take Apple M1 chip, Intel AVX-512, Qualcomm as examples)](./why_wwmodel_fast_en.md)

- [The difference between it and Microsoft Azure DataFactory/DataPipelines Architecture](./diff_WWModel_AzureDataFactoryPipe.md)

- [Comment: Intel, RISC-V, and AMD Infinity Fabric Architecture](./Intel_RISC_V.md)
  
![OS-Star-WWM](./image/OS-Star-WWM.svg)

