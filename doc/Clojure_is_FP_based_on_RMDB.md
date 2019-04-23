# Clojure is a functional programming language based on relational database theory

# Clojure是基于关系式数据库理论的函数式编程语言

Copyright © 2018 Lin Pengcheng. All rights reserved.

版权所有 © 2018 林鹏程， 保留所有权利。

```
               Clojure -> DBMS, Super Foxpro
                   STM -> Transaction，MVCC
Persistent Collections -> db, table, col
              hash-map -> indexed data
                 Watch -> trigger, log
                  Spec -> constraint
              Core API -> SQL, Built-in function
              function -> Stored Procedure
             Meta Data -> System Table
 
```
Note: In the latest spec2, spec is more like RMDB. 
see: [spec-alpha2 wiki: Schema-and-select](https://github.com/clojure/spec-alpha2/wiki/Schema-and-select)

I don’t care about static or dynamic types, nor about FP, LP, or OO. For me, 
they are overly complex, unreliable, and unscientific. I think they are very bad and upset me.

The production methods and business management ideas of large industries are also more mature than FP&OO. 
I have used them as programming ideas.

I think that RMDB is the simplest and most reliable in theory and practice, 
and it is the most rigorous, long-term, high-stress test in critical situations.

Before using clojure, I was a Foxpro programmer. 
I used clojure as a super Foxpro, 
and I also used it successfully in the field of WebApp and R language mixed programming. 
I will continue to apply this routine to the AI field in the future.

The main development goal of clojure is to write the database. 
The development idea is actually from the database, not the FP.

The Clojure system can be treated as a RMDB using the Lisp language, RMDB Schema (Clojure Spec) is a static type, and SQL (LISP) is a dynamic type.

It is an example of the best combination of dynamic and static types.

With reference to the database, as long as I use spec to strictly define (standardization) the core data model, I can ensure the correctness of the system.

I've turned the traditional work of ensuring code correctness from in-code type system validation to data self-validation. Turn the work into verifying the core data model instead of validating the input and output data types of the function.

Similar to industry, verify that all finished products meet the standards before entering the warehouse.
Also similar to databases, verify their compliance before data enters the database.

That is "Data as a service, Warehouse as the core, operates around it".

A system requires only a few core data models, and development is built around the core data model.

Persistent data structures ensure that the modification of the immutable big data model are high performance and memory efficient.

In addition, using my pure function pipeline data stream (https://github.com/linpengcheng/PurefunctionPipelineDataflow) makes debugging, parallelism and extension very simple.


