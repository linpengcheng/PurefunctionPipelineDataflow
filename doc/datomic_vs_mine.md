# `Datomic` vs. `my relational data model based on hash-map`

Copyright © 2021.11.06 Lin Pengcheng. All rights reserved.

## Data model

- Datomic: The schema consists of an entity primary key, 
  a data column name, a data column value, and time.
  
  - It is equivalent to an RMDB table with only one data column, 
    turning a wide table into a narrow table.
  - It is equivalent to a NoSQL (a hash-map) persisted on the RMDB, 
    and a schema instance is equivalent to a key-value pair of a data column.
  - Advantages: Unified query method (datalog), 
    suitable for constructing complex queries, 
    with a complete system.
  - Disadvantages: more redundant data
  - Datomic = DB-atomic ? Persist Clojure atom to PostgreSQL (RMDB) ? :-)
   
- Mine: Relational data model based on hash-map

  - Advantages: Simple, no redundant data, 
    Clojure's native data types and data manipulation methods.
  - Disadvantages: Users are required to construct 
    query functions and derived indexes 
    on a custom data model.
    
## DML

- Datomic: datalog, Clojure

- Mine 
  - Simple and necessary SQL subset implemented with Clojure
  - Clojure core API
  
## Transaction, parallel, concurrency

  - Datomic: MVCC
  
  - Mine: The scheduling function dynamically plans 
    the order of completion of tasks according to 
    the Gantt chart algorithm, and calls the workshop 
    to complete the assigned tasks. 
    This approach is the most efficient, 
    and there is no resource competition 
    and transaction conflict. 
    
----

# `Datomic` vs. `我的基于hash-map之上的关系数据模型`

版权所有 © 2021.11.06 林鹏程， 保留所有权利。

## data model
- Datomic: schema由实体主键,一个数据列名,一个数据列值,时间组成.
  - 它相当于只有一个数据列的RMDB表，把宽表变成窄表。
  - 它相当于一个持久化在RMDB之上的NoSQL(一个hash-map), 一个schema实例相当于一个数据列的键值对
  - 优点: 统一查询方式（datalog）, 适合构造复杂查询, 有一个完整的系统．
  - 缺点: 冗余数据多
  - Datomic = DB-atomic ? 把Clojure atom持久化到PostgreSQL(RMDB) :-)
  
- 我的: 基于hash-map之上的关系数据模型

  - 优点: 简单, 没有冗余数据, Clojure的原生数据类型和数据操纵方式.

  - 缺点: 需要用户在自定义的数据模型上构造查询函数和派生索引.
    
## DML

- Datomic: datalog, Clojure

- 我的: 用Clojure实现的简单和必要的SQL子集, Clojure core API
  
## 事务,并行,并发

- Datomic: MVCC
  
- 我的: 调度函数根据甘特图算法动态规划任务的完成顺序，并调用车间完成分配的任务。 这种方式效率最高，不存在资源竞争和事务冲突。
      
