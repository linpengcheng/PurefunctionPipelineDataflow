# Defects and improvement measures of Microsoft `Azure DataFactory/DataPipelines Architecture` ---- The difference between `Warehouse/Workshop Model` and Microsoft `Azure DataFactory/DataPipelines Architecture`

Copyright © 2021-04-27 Lin Pengcheng. All rights reserved.

## Difference

### Workshop vs DataPipeline

- Workshop

  - It is a larger execution unit than a data pipeline 
    and consists of a series of data pipelines.
  - There is no interaction between the workshops, 
    and each workshop is only uniformly scheduled by the warehouse.
    - the warehouse scheduler and the workshop are **1: n relationship**
  - It is the atomic unit when dividing independent tasks, 
    corresponding to a bar of the Gantt chart.
  - It can have no warehouse, at this time it is just a microservice 
    (service industry).

- Azure DataPipeline

  - Execute Pipeline Execute: Pipeline activity allows 
    a Data Factory pipeline to invoke another pipeline.
  - Scheduling pipelines  [new feature in current version (2019-11-19)]
    - Pipelines & triggers have an **n:m relationship**.
  - It does not comply with the following principles
    - Single Leader and Unified Scheduling
    - Order

### Warehouse vs DataFactory

- Warehouse

  - It is a special pipeline, a container for all resources 
    (status, data, and functions are also data). 
    It has two special side-effect pipelines (I/O) 
    that are connected to the outside world.
  
  - It has a scheduler, the warehouse scheduler and 
    the workshop are **1: n relationship**, 
    the warehouse scheduler uses Gantt chart algorithm 
    dynamic planning for global optimization.
    
  - It may not have an ordinary workshop, 
    at this time it is just a data center 
    (warehousing industry).
  
- Azure DataFactory

  - Azure Data Factory is the cloud-based ETL and data integration service，
  - Scheduling pipelines  [new feature in current version (2019-11-19)]
    - Pipelines & triggers have an **n:m relationship**.
    - According to the activity dependency scheduling 
      used in traditional concurrent systems, 
      it is not scheduled in an optimized order.
  - It does not comply with the following principles
      - Single Leader and Unified Scheduling
      - Order
      - Definiteness

## Defects and improvement measures of Microsoft `Azure DataFactory/DataPipelines Architecture`

From the comparison of the above differences, 
Microsoft `Azure DataFactory/DataPipelines Architecture` 
has the following shortcomings:

- Because
  - Execute Pipeline Execute: Pipeline activity allows 
    a Data Factory pipeline to invoke another pipeline.
  - Pipelines & triggers have an **n:m relationship**.
- So
  - Since it has no workshop encapsulation,
    multiple data pipelines call each other, 
    intertwined into a complex and chaotic network.
  - It is like a factory without workshops, 
    all machines (data pipelines) are connected together 
    in an open field, There is no unified scheduler, 
    they are in a chaotic, unorganized state.
  - It is not a strict star system and fractal system.
  - It does not comply with the following principles
    - Single Leader and Unified Scheduling
    - Order
    - Definiteness
  
The improvement measure is to use my `Warehouse/Workshop Model`.

## Reference

- [Pipelines and activities in Azure Data Factory (current version 2019-11-19) at docs.microsoft.com](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities)
