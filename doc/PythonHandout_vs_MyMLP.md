# 比较 `Python Handout` 和我的 `Markdown文学编程` 的差异

版权所有 © 2024.08.22 林鹏程，保留所有权利。

2024.08.22首发于[我的微博](https://weibo.com/lincpa)

### 用途

- `Python Handout` 库是传统的"文学编程"工具, 主要思想是"文档第一", 用来生成文档的工具, 与编程源代码无关,
  类似Racket语言的scribble文档工具.

- 我的`Markdown文学编程`主要思想是"代码(编程)第一", 是源代码工具, 
  主要是用来放在编程的源代码里, 把源代码的表现方式从文本时代通过`Live Preview`进步到Web时代.

两者在用途上完全不同. ​​​

# 方法

- `Python Handout` 库通过`md+py`达到类似`HTML+js`(或`ASP`)生成动态文档。

- 我的`Markdown文学编程`是在注释区扩展md, 通过`Live Preview`实现源代码网页化的展示，
  让代码更有可读性，更好理解，更有表现力。

# 设计方案

因为用途不同，两者在设计方案上产生了一个最重要的显著差异：

- `Python Handout` 库动态文档部分则是放在正常代码区域，会影响源代码。
  因此handout只能做为文档工具，不能做为语言特性放在源代码里。

- 我的`Markdown文学编程`不管是静态部分还是动态部分都在源代码文件注释区，不影响编程语言语法和编译器，
  可以作为编程语言特性放在源代码里。
