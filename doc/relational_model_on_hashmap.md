# Implement relational data model and programming based on hash-map (NoSQL)

# 在hash-map(NoSQL)的基础上实现关系式数据模型和编程

Copyright © 2018 Lin Pengcheng. All rights reserved.

版权所有 © 2018 林鹏程， 保留所有权利。

If programming is to sail on the sea, 
I use the relational model as a lighthouse and route, 
as a reference model for simple programming, 
because the relationship theory is simple and scientific.

The advantage of hash-map is that it is good for data element operations. 
You can use key-chain as a pointer, 
and processing data elements is simple and efficient. 
In addition, using hash-map implementation, 
you can take full advantage of Clojure's powerful core functions.

The advantage of the relational data model is 
that it is a good collection operation, 
and it does not have deep nesting, 
expression is clear, easy to view, and simple operation logic.
By simply wrapping the Clojure core functions, 
you can implement SQL-like functions.
[Clojure is a FP based on RMDB](doc/Clojure_is_FP_based_on_RMDB.md),
it has many RMDB facilities.

Therefore, it has the advantages of RMDB and NoSQL.

This method is actually an inverse implementation of PostgreSQL.
PostgreSQL Implements NoSQL support on relational models 
by supporting json types and extending SQL.

Postgresql uses SQL to manipulate data,
and my method uses a more powerful clojure core function.

Therefore, I don't want to implement the relational data model on clojure 
as the following RMDB-like data representation:

```clojure
;I don't like this RMDB-like implementation:

(def table01
    #rel [{name "t1-r1", manager :m1}
          {name "t1-r2", manager :m2}
          {name "t1-r3", manager :m3}
          {name "t1-r4", manager :m2}])

(select table01 (= manager :m2))

; => #rel [{name "t1-r2", manager :m2}
;          {name "t1-r4", manager :m2}] 

(select table01 (or (= manager :m2) (= manager :m3)))

; => #rel [{name "t1-r2", manager :m2}
;          {name "t1-r3", manager :m3}
;          {name "t1-r4", manager :m2] 
```

My implementation is as follows:

```clojure
;My method: Implement relational model and programming based on hash-map (NoSQL)

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
                            
;=======SQL-Like===========    

(defn join [db main_table join_table join_col]
  (let [f #(let [x (-> db main_table %2)]
              (->> x
		   join_col
		   (get (db join_table) ,)
		   (merge x ,)
		   (assoc %1 %2 ,)))]
  (->> db
       main_table  
       keys
       (reduce f {} ,)
       doall)))  
	   
(join db :table02 :table01 :t1-pk)

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
          
(defn index [index-name db table col]
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
    
(index :t1-manager-index db :table01 :manager)

(use 'clojure.set)

(defn select-by-index [index-name index-keys db table]
  (->> index-keys
       (select-keys (get db index-name) ,)
       vals
       (apply clojure.set/union ,)
       (select-keys (get db table) ,)))  
	   
(select-by-index :t1-manager-index 
                 [:m2 :m3] 
		 db 
		 :table01)
; =>
; {:t1-pk3 {:t1-pk :t1-pk3, :name01 "t1-r3", :manager :m3}, 
 ; :t1-pk4 {:t1-pk :t1-pk4, :name01 "t1-r4", :manager :m2}, 
 ; :t1-pk2 {:t1-pk :t1-pk2, :name01 "t1-r2", :manager :m2}}   

;=======hash-map(NoSQL): clojure core fn ======
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



(let [{:keys [table01 t1-manager-index]} db]
  (->> :m2
       t1-manager-index
       (select-keys table01 ,)))
  
; =>
; {:t1-pk4 {:t1-pk :t1-pk4, :name01 "t1-r4", :manager :m2}, 
 ; :t1-pk2 {:t1-pk :t1-pk2, :name01 "t1-r2", :manager :m2}}
 
```
----

I think developers must fully understand the data model and be able to manipulate any data element, data transformation, and collection operations as they wish.

The data model is the most important. It should be designed before programming and adjusted as the development progresses to ensure that the data model can be easily and smoothly manipulated.

If you only need a pure relational database, I will choose postgresql, h2, honeysql.

The main purpose of my approach is to implement data modeling best practices using pure clojure core data types. The hash-map data model is designed with reference to the relational data model to:

- Like Collection operations of relational data models.

- Manipulate data elements with the powerful core functions of the hash-map in clojure.

Clojure has many facilities similar to RMDB, but lacks a relational data model. I designed this model and sql-like function. Filled in this defect. So we can call clojure an RMDB.

I did not design a complete SQL clause, because in the pure function pipeline data flow, only need to insert a reduce-kv (filter, map , etc.) in series to achieve the clause function.

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

If clojure's data model like a RMDB, clojure's facilities like a RMDB and clojure's data manipulation like a RMDB, clojure must be a RMDB.

----
