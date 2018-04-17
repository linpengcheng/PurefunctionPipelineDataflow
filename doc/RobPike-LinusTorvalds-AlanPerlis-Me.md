# 英雄所见略同：Rob Pike，Linus Torvalds，Alan Perlis 和我

Copyright © 2018 Lin Pengcheng. All rights reserved.

版权所有 © 2018 林鹏程， 保留所有权利。

2018.04.11晚，在 https://www.reddit.com/r/Clojure/ 上新文章的链接 https://github.com/walkable-server/walkable 
看到 Rob Pike (unix,utf8,plan9,go的作者) 和 Linus Torvalds (Linux和git的作者) 的语录，
发现与我自创的纯函数管道数据流的观点是一致的，
首位图灵奖得主, Algol语言(C/C++/Pascal等语言的鼻祖)作者Alan Perlis也有类似观点，
真是英雄所见略同啊, 哈哈！

Rob Pike: Data dominates. If you’ve chosen the right data structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming.

Linus Torvalds: Bad programmers worry about the code. Good programmers worry about data structures and their relationships.

Alan Perlis: It’s better to have 100 functions operate on one data structure than 10 functions on 10 data structures.

100个人围着一个核心干活，核心设计好，100个全都干活轻松，设计不好，那就要命了.

FP的思想与此完全背道而驰，FP学术派和OO咨询派终归不如UNIX工程派靠谱。低调的Unix派撑起了整个IT的软件世界，真个厚德载物。
整天挖空心思耍花枪的FP和OO派，很流行，流行感冒，是IT界流行的娱乐明星。
