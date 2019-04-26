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
Also similar to databases, verify their compliance before data enters the database.;unctionPipelineDataflow) makes debugging, parallelism and extension very simple.

----

In general, I think:
1. arbitrary layering and deep nesting are not good engineering practices.

2. I prefer to use hash-map as the table with the primary key hash index, with key as the primary key and val(colname-colval-hashmap) as the row content.

```clojure

{:table01 {:row01 {:col-array [0 1 2]
                   :col-json  "{\"a\": \"Hello\"}"
                   :col-text  "abc"}
           :row02 {}}
 :table02 {:row01 {}
           :row02 {}}}
            
(def a {:a-id-01 {:a-name "a1"}
        :a-id-02 {:a-name "a2"}})
(def b {:b-id-01 {:a-id :a-id-01 :b-name "b2"}
        :b-id-02 {:a-id :a-id-02 :b-name "b2"}})

;try to row (or col) operations as much as possible, 
;and join all data only when necessary(reduce the row-join).
        
(->> b
     :b-id-01
     :a-id
     a
     :a-name)
;=>
;"a1"

(let [x (b :b-id-01)]
  (->> x  
       :a-id
       a
       (merge x ,)))
;=>
;{:a-id   :a-id-01,
; :b-name "b2",
; :a-name "a1"}            
            
```

I don't think relational algebra operations must be implemented in the form of RMDB and SQL. It can also be implemented very elegantly with clojure.core. using hash-map operation is simpler, clearer, smoother and high performance.

There are many ways to implement relational algebra. The thinking is not limited by the "information structure" displayed by the traditional RMDB interface. In clojure, the hash-map(NoSQL) is the underlying physical model, and the relational model is the upper logical model.clojure core function acts as a data manipulation language, I named this architecture SuperSQL or SuperRMDB.

In fact, the original data manipulation language of posgresql and foxpro is not SQL. Clojure core function is closer to foxpro's commands (DML).

3. set, vector, list is generally not a good default data container, only used when needed. you use the set as container, it's difficult to operate data (table, row, column, value).

4. In summary, I think: programming is the process of designing a data model that is simple and fluent in manipulation. To have open thinking, not to be restricted by traditional thinking, to be flexible, adapt to local conditions, and design as needed.
