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

如果说编程是在海上航行，我使用关系模型作为灯塔和路线，
作为简单编程的参考模型，因为关系理论简单而科学。

hash-map的优点是善长数据元素操作, 可以把key-chain作为指针，处理数据元素简单而有效。
另外用hash-map实现,可以充分利用Clojure丰富强大的核心函数。

关系模型的优点是善长集合操作, 通过对Clojure核心函数的简单包装,可以实现SQL类的函数。
另外,关系模型不会有深度嵌套, 表达清晰, 查看方便, 操作逻辑简单.

因此，它具有RMDB和NoSQL的优点。

这种编程方法事实上是PostgreSQL的逆实现,
PostgreSQL:通过支持json类型和扩展SQL，实现在关系式模型上的NoSQL支持.

因此, 我不希望把clojure上的关系模型实现成类似RMDB的数据表示, 
