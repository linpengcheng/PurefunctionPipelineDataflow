# Markdown Literary programming that don't break the syntax of any programming language

Copyright © 2018 Lin Pengcheng. All rights reserved.

## comment area markup method:

Just add a custom line comment character before each line of Markdown.

In the comments of code, you can draw flowcharts, tasklist, display data visualizations, etc.

When previewing or converting a format, you only need to simply preprocess: replace the `\r\n\;` with `\r\n`

Note: 

- line comment character of Clojure(Lisp) is `;`
- line breaks and line comment  characters of the current file can be obtained from the editor's API.

when we edit the code, we can preview the effect in real time. 
Editing literary code has a live preview panel like most markdown editors.

## The editor has a Live Preview panel to do the following work:

1. Get the current text 

2. replace the `\r\n\;` with `\r\n`

3. live Preview markdown string

4. Easily export directly to PDF or HTML.

## Its advantages:

1. It don't break the syntax of any programming language, you can compile directly. comment area markup method can be applied to any programming language and any markup (including Org,rst, asciidoc, etc.), which is the greatest advantage.

2. you only need a single line of regular replacement preprocessing, then you can use any Markdown parse or converter.

3. Support any code editor that supports Markdwon Live preview, allowing the source code of any programming language to become rich text in real time. In the code's comment area, You can use the markdown to draw flowcharts, tables, task lists, and display images on the live preview panel, enhance the readability of your code.

4. If you extend the Markdwon tag, you can implement the eval code, print result, display data visualization and other instruction tags, to achieve live programming, live test.

the main purpose of the Code comment area markup method is to live Preview directly in the Code Editor Preview panel without exporting or any preprocessing.

I think:

- Literary Programming, Programming was the first, Literary was the second.

- The entire file is compliant with the programming language syntax and can be compiled directly.

- When writing (reading or refactoring) code files, I can modify and live preview directly in the editor without exporting or any preprocessing.

- Do not interfere with people who do not understand the markup language to read the code.

- Reliable. Maximum code accuracy is guaranteed, and markup language errors do not affect the code.

## example:

```clojure
;### Markdown literary programming
;#### example01:
;![Warehouse Workshop Model](./doc/Warehouse-Workshop-Model.svg)
;#### example02:
;```clojure
(defn f [[evens odds total amax amin] x]
  (let [[evens odds] (cond 
                       (even? x) [(inc evens ) odds]
                       (odd? x)  [evens (inc odds)]
                       :else     [evens odds])
        total (+ total x)
        amax  (max amax x)
        amin  (min amin x)]   
     [evens odds total amax amin]))
;;The comment of the code requires at least two line comment characters
(reduce f [0 0 0 ##-Inf ##Inf] [5 6 8 -3 -9 11 156 6 7])
;```
;return`[4 5 187 156 -9]`

```

## Live Preview Effects:

> 
> ### Markdown literary programming
> #### example01:
> ![Warehouse Workshop Model](./doc/Warehouse-Workshop-Model.svg)
> #### example02:
> ```clojure
> (defn f [[evens odds total amax amin] x]
>   (let [[evens odds] (cond 
>                        (even? x) [(inc evens ) odds]
>                        (odd? x)  [evens (inc odds)]
>                        :else     [evens odds])
>         total (+ total x)
>         amax  (max amax x)
>         amin  (min amin x)]   
>      [evens odds total amax amin]))
> ;The comment of the code requires at least two line comment characters
> (reduce f [0 0 0 ##-Inf ##Inf] [5 6 8 -3 -9 11 156 6 7])
> ```
> return`[4 5 187 156 -9]`
> 
