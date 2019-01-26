# Everything is RMDB 
# 一切都是RMDB

Copyright © 2018 Lin Pengcheng. All rights reserved.

版权所有 © 2018 林鹏程， 保留所有权利。

```
              R System -> RMDB     <- Chrome, X-Server
   JRI/RServe/Rsession -> JDBC     <- ring,   X-Protocol
            R Language -> SQL      <- HTML,   X-Client(KDE,GNOME,Aqua)
                  RDSL -> HoneySQL <- hiccup, code+rc(QML,qrc,XUL,XAML)
--------------------------------------------------
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

My idea of development: 

- Everything is RMDB. 
- Send SQL, 
- Get Results ( or side effects).
- Playing table tennis between Clojure and RMDB.

我的开发思想：

- 一切都是RMDB,
- 发送SQL,
- 获得结果(或副作用),
- 在Clojure和RMDB之间打乒乓球。

I use the R language for data analysis and visualization 
through JRI and DSL(Like hiccup, honeysql) on Clojure, 
use Chrome to view data (format to HTML), 
and use the free image-viewer software to view plot.

我使用R语言通过Clojure上的JRI和DSL（如hiccup，honeysql）进行数据分析和可视化，
使用Chrome查看数据（格式化为HTML），并使用免费的看图软件查看数据可视化结果。

I prefer pure clojure hash-map to implement a model similar to Dataframe, 
which, by its characteristics, is more like a super Execl with spec and s expressions.
Clojure manipulation Hash-map is very convenient, hash index performance is also very strong.
Dataframe is similar to DB, It don’t have to keep the order, Therefore, 
It don’t need to use vector, just sort when you need it.
I use “hash-map * hash-map” to map (metaphorically) semantically 
on demand as a database structure for NoSQL and RMDB.

我更喜欢纯粹的clojure hash-map来实现类似于Dataframe的模型，
根据它的特性，它更像是带有spec和s表达式的超级Execl。
Clojure操作Hash-map非常方便，哈希索引的表现也很强。
Dataframe类似于DB，它不需要保持顺序，因此，它不需要使用向量，只需在需要时进行排序。
我使用“hash-map * hash-map”按需在语义上映射（隐喻）作为NoSQL和RMDB的数据库结构。

Finally, I think that RMDB is the simplest and most reliable in theory and practice, 
and it is the most rigorous, long-term, high-stress test in critical situations. 
if you're having trouble modeling your data, you can refer to posgtresql how to do it.

最后, 我认为RMDB在理论和实践中是最简单和最可靠的，
并且它是在危急情况下最严格，长期，高压力的测试。
如果在数据建模时遇到麻烦, 可以参考posgtresql怎么做.
