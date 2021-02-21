# Everything is RMDB 

Copyright © 2018 Lin Pengcheng. All rights reserved.

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

I use the R language for data analysis and visualization 
through JRI and DSL(Like hiccup, honeysql) on Clojure, 
use Chrome to view data (format to HTML), 
and use the free image-viewer software to view plot.

I prefer pure clojure hash-map to implement a model similar to Dataframe, 
which, by its characteristics, is more like a super Execl with spec and s expressions.
Clojure manipulation Hash-map is very convenient, hash index performance is also very strong.
Dataframe is similar to DB, It don’t have to keep the order, Therefore, 
It don’t need to use vector, just sort when you need it.
I use “hash-map * hash-map” to map (metaphorically) semantically 
on demand as a database structure for NoSQL and RMDB.

If you're having trouble modeling your data, you can refer to posgtresql how to do it.
- Relational data model, recommended design as the 3NF (third normal form)
- For non-critical information, for simplicity and flexibility, 
  it can be designed as a hash-map (json) type in a small range. 
- Avoid deep nesting of data structures. Generally, the nesting depth is no more than 3 levels, 
  and no more than 5 levels at most.
  - Recursive (or loop) operations can be avoided, 
    and low nesting depth can be easily converted to single-level operations, 
    especially hash-map is more convenient.
  - The data is readable and easy to display and debug.

Finally, I think that RMDB is the most scientific, simplest 
and most reliable in theory and practice, and it has withstood the most rigorous, 
high-pressure, and long-term tests in various critical situations.
  
# 一切都是RMDB

版权所有 © 2018 林鹏程， 保留所有权利。

我的开发思想：

- 一切都是RMDB,
- 发送SQL,
- 获得结果(或副作用),
- 在Clojure和RMDB之间打乒乓球。

我使用R语言通过Clojure上的JRI和DSL（如hiccup，honeysql）进行数据分析和可视化，
使用Chrome查看数据（格式化为HTML），并使用免费的看图软件查看数据可视化结果。

我更喜欢纯粹的clojure hash-map来实现类似于Dataframe的模型，
根据它的特性，它更像是带有spec和s表达式的超级Execl。
Clojure操作Hash-map非常方便，哈希索引的表现也很强。
Dataframe类似于DB，它不需要保持顺序，因此，它不需要使用向量，只需在需要时进行排序。
我使用“hash-map * hash-map”按需在语义上映射（隐喻）作为NoSQL和RMDB的数据库结构。

如果在数据建模时遇到麻烦, 可以参考posgtresql怎么做.
- 关系数据模型，推荐设计为第三范式
- 非关键信息，为简便灵活，小范围地使用的 hash-map(json), 
  如同pgsql一样，只可做调味，不可当饭吃。
- 避免数据结构深度嵌套，一般嵌套深度不超过3层，最多不超过5层。
  - 可避免递归（或循环）操作，低嵌套深度可以很方便变换为单层深度的操作，特别是hash-map更方便。
  - 数据可读性强，方便显示和调试。

最后, 我认为RMDB在理论和实践中是最科学、最简单和最可靠的，
并且它在各种至关重要的关键场景中经受最严格的、高压力的、长期的考验。
