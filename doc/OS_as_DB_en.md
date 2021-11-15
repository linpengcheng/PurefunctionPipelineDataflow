# In the future, OS will be a DB, and Clojure will be the best DML

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
  - DML: Just let Clojure integrate JDBC and SQL, 
    and let all core APIs natively support JDBC and OSDB, 
    and Clojure can instantly become the best DML.
    
- Workshop

  - Hardware: CPU, GPU, ASIC, various peripherals, etc
  - Software: Various applications & Service software
  
![OS-Star-WWM](./image/OS-Star-WWM.svg)
