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

In addition, using my pure function pipeline data flow (https://github.com/linpengcheng/PurefunctionPipelineDataflow) makes debugging, parallelism and extension very simple.


----

I think developers must fully understand the data model and be able to manipulate any data element, data transformation, and collection operations as they wish.

The data model is the most important. It should be designed before programming and adjusted as the development progresses to ensure that the data model can be easily and smoothly manipulated.

If you only need a pure relational database, I will choose postgresql, h2, honeysql.

The main purpose of my approach is to implement data modeling best practices using pure clojure core data types. The hash-map data model is designed with reference to the relational data model to:

- Like Collection operations of relational data models.

- Manipulate data elements with the powerful core functions of the hash-map in clojure.

Clojure has many facilities similar to RMDB, but lacks a relational data model. I designed this model and sql-like function. Filled in this defect. So we can call clojure an RMDB.

I did not design a complete SQL clause, because in the pure function pipeline data flow, only need to add a reduce-kv (filter, map , etc.) in series to achieve the clause function.

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

Rmdb is not only manipulated with SQL, The original DML of postgresql and foxpro is not SQL.

Duck Typing: If it looks like a duck and quacks like a duck, it must be a duck.

**If clojure's data model like a RMDB, clojure's facilities like a RMDB and clojure's data manipulation like a RMDB, clojure must be a RMDB.**

----

If Clojure is the sea, programming is to sail on the sea, I use the relational model as a lighthouse and route, as a reference model for simple programming, because the relationship theory is simple and scientific.

I had implemented a DataFrame with hash-map, which implements relational operations. A relational operation is just a function. The advantage of hash-map is that key-chain can be used as a pointer, and processing data elements is simple and efficient. Therefore, DataFrame has advantages of RMDB and NoSQL.

A strict relational model will lose the flexibility of data element operations.

Clojure is a multi-paradigm, general-purpose functional programming language.

The postgresql development team is also this view, so postgresql is not only RMDB (relational modeling), but also supports OO and json (NoSQL). But postgresql default data modeling is relational modeling

My point of view is mainly to emphasize the best practices of data modeling and programming.

In general, I think:

1. arbitrary layering and deep nesting are not good engineering practices.

2. I prefer to use hash-map as the table with the primary key hash index, with key as the primary key and val(colname-colval-hashmap) as the row content.

```clojure

(def db {:table01 {:t1-pk1 {:t1-pk   :t1-pk1
                            :name01  "t1-r1"
                            :manager :m1}
                   :t1-pk2 {:t1-pk   :t1-pk2
                            :name01  "t1-r2"
                            :manager :m2}
                   :t1-pk3 {:t1-pk   :t1-pk3
                            :name01  "t1-r3"
                            :manager :m3}
                   :t1-pk4 {:t1-pk   :t1-pk4
                            :name01  "t1-r4"
                            :manager :m2}}
         ; generate a "derived index" based on the "primary key hash index".
         :t1-manager-index {:m1 #{:t1-pk1}
                            :m2 #{:t1-pk2 
                                  :t1-pk4}
                            :m3 #{:t1-pk3}}                 
         :table02 {:t2-pk1 {:t2-pk   :t2-pk1
                            :t1-pk   :t1-pk1
                            :name02  "t2-r1"
                            :client  :client1}
                   :t2-pk2 {:t2-pk   :t2-pk2
                            :t1-pk   :t1-pk2
                            :name02  "t2-r2"
                            :client  :client2}
                   :t2-pk3 {:t2-pk   :t2-pk3
                            :t1-pk   :t1-pk3
                            :name02  "t2-r3"
                            :client  :client3}
                   :t2-pk4 {:t2-pk   :t2-pk4
                            :t1-pk   :t1-pk4
                            :name02  "t2-r4"
                            :client  :client2}}})

;try to row (or col) operations as much as possible, 
;and join all data only when necessary(reduce the row-join).
        
(let [{:keys [table01 table02]} db]
  (->> table02
       :t2-pk1
       :t1-pk
       table01
       :name01))
;=>
;"t1-r1"

(let [{:keys [table01 table02]} db
      x (table02 :t2-pk1)]
  (->> x  
       :t1-pk
       table01
       (merge x ,)))
 
;=>
; {:t2-pk   :t2-pk1, 
;  :t1-pk   :t1-pk1, 
;  :name02  "t2-r1", 
;  :client  :client1          
;  :manager :m1, 
;  :name01  "t1-r1"} 

(let [{:keys [table01 table02]} db
      f #(let [x (table02 %2)]
          (->> x 
               :t1-pk
               table01
               (merge x ,)
               (assoc %1 %2 ,)))]
  (->> table02  
       keys
       (reduce f {} ,)
       doall))      
;=>
; {:t2-pk1 {:t2-pk :t2-pk1, 
          ; :t1-pk :t1-pk1, 
          ; :name02 "t2-r1",
          ; :client  :client1          
          ; :manager :m1, 
          ; :name01 "t1-r1"},  
 ; :t2-pk2 {:t2-pk :t2-pk2, 
          ; :t1-pk :t1-pk2, 
          ; :name02 "t2-r2", 
          ; :client  :client2          
          ; :manager :m2, 
          ; :name01 "t1-r2"}, 
 ; :t2-pk3 {:t2-pk :t2-pk3, 
          ; :t1-pk :t1-pk3, 
          ; :name02 "t2-r3", 
          ; :client  :client3          
          ; :manager :m3, 
          ; :name01 "t1-r3"}, 
 ; :t2-pk4 {:t2-pk :t2-pk4, 
          ; :t1-pk :t1-pk4, 
          ; :name02 "t2-r4", 
          ; :client  :client2          
          ; :manager :m2, 
          ; :name01 "t1-r4"}}       

(defn gen-index [index-name db table col]
  (let [f (fn [m k v]
            (let [x (v col)
                  y (m x)
                  y (if y y #{})] 
              (->> (conj y k)
                   (assoc m x ,))))]
    (->> db
         table 
         (reduce-kv f {} ,)
         (assoc db index-name ,)))) 
    
(gen-index :t1-manager-index db :table01 :manager)

(let [{:keys [table01 t1-manager-index]} db]
  (->> :m2
       t1-manager-index
       (select-keys table01 ,)))
  
; =>
; {:t1-pk4 {:t1-pk :t1-pk4, :name01 "t1-r4", :manager :m2}, 
 ; :t1-pk2 {:t1-pk :t1-pk2, :name01 "t1-r2", :manager :m2}}
 
(let [{:keys [table01 t1-manager-index]} db]
  (->> [:m2 :m3]
       (select-keys t1-manager-index ,)
       vals
       (apply clojure.set/union ,)
       (select-keys table01 ,))) 
 
; =>
; {:t1-pk3 {:t1-pk :t1-pk3, :name01 "t1-r3", :manager :m3}, 
 ; :t1-pk4 {:t1-pk :t1-pk4, :name01 "t1-r4", :manager :m2}, 
 ; :t1-pk2 {:t1-pk :t1-pk2, :name01 "t1-r2", :manager :m2}}          
            
```

I don't think relational algebra operations must be implemented in the form of RMDB and SQL. It can also be implemented very elegantly with clojure.core. using hash-map operation is simpler, clearer, smoother and high performance.

There are many ways to implement relational algebra. The thinking is not limited by the "information structure" displayed by the traditional RMDB interface. In clojure, the hash-map(NoSQL) is the underlying physical model, and the relational model is the upper logical model.clojure core function acts as a data manipulation language, I named this architecture SuperSQL or SuperRMDB.

In fact, the original data manipulation language of posgresql and foxpro is not SQL. Clojure core function is closer to foxpro's commands (DML).

3. set, vector, list is generally not a good default data container, only used when needed. if you use the them as container, it's difficult to operate data (table, row, column, value).

In summary, I think: programming is the process of designing a data model that is simple and fluent in manipulation. To have open thinking, not to be restricted by traditional thinking, to be flexible, adapt to local conditions, and design as needed.
