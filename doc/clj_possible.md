# A possible roadmap for clojure

Copyright © 2020 Lin Pengcheng. All rights reserved.

I think babashka  (clojure native) can become an IDE for database (analysis) applications, 
such as Foxpro (the former king of desktop database developers), Racket(all in one), 
Janet(clojure-like, stdlib: db, webapp, ui), python Jupyter,etc.

- If built-in H2 database (and its Web console), http-kit, then babashka has all 
  Foxpro components (database engine, database management, GUI(Web), programming language),
  and clojure is good at manipulating data, becoming departmental or small Enterprise's 
  WebApp database development solution.

- If you add data visualization libraries such as oz, or call an external command line visualization engine,
  It will be a good data display platform.

- Babashka is not suitable for big data analysis, but if fastmath & core.logic is integrated, it can become
  a lightweight `expert system` type data analysis platform.


# clojure的一种可能的路线图

版权所有 © 2020 林鹏程， 保留所有权利。

我认为 babashka (clojure native)可以成为一个数据库（分析）应用的集成开发环境，类似：Foxpro(曾经的桌面数据库开发王者)， 
Racket，Janet(clojure-like, stdlib: db, webapp, ui), Jupyter等.

- 如果内置H2 database(及其Web控制台)，http-kit,那么babashka就具备Foxpro的部件(数据库引挚，数据库管理，WebGUI, 编程语言)，
  且clojure善长操作数据，成为部门级或小企业的WebApp数据库开发解决方案.

- 如果再加上oz, darkstar等数据可视化库，或调用外部命令行可视化引挚, 它将是一个很好的数据展示平台。

- babashka不适合作大数据分析，但如果集成fastmath，core.logic可以做轻量级的`专家系统`型的数据分析平台。
