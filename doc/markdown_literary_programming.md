# Markdown Literary programming that don't break the syntax of any programming language

Copyright © 2018 Lin Pengcheng. All rights reserved.

## Table of Contents 目录
- [Comment Area Markup Method](#Comment-Area-Markup-Method)
- [Live Preview Panel of editor do the following work](#Live-Preview-Panel-of-editor-do-the-following-work)
- [Advantages](#Advantages)
- [Example](#Example)
- [Live Preview Effects](#Live-Preview-Effects)

## Comment Area Markup Method

Literary Programming, Programming was the first, Literary was the second.

the main purpose of the Code comment area markup method is 
to live Preview directly in the Code Editor Preview panel 
without exporting or any preprocessing.

*Just add a line comment character of the programming language 
before each line of Markdown.*

In the comments of code, you can draw flowcharts, tasklist, 
display data visualizations, etc.

When previewing or converting a format,
you only need to simply preprocess: 
delete line comment characters with regular expressions, 
example: `sed 's/^;//'  x.clj`

Note: 

- line comment character of Clojure(Lisp) is `;`
- line breaks and line comment characters of the current file 
  can be obtained from the editor's API.

when we edit the code, we can preview the effect in real time. 
Editing literary code has a live preview panel like most markdown editors.

## Live Preview Panel of editor do the following work

```clojure
(cond
  (or (= file-extension-name ".md")
      (= file-extension-name ".markdown"))
       parse+view as a normal markdown file
  (empty? line-comment-characters-of-the-current-document-type)
       parse+view as a normal text file 
  :else
       (do 0.get line breaks and line comment characters of the current document
           1. get the current text
           2. delete line comment characters with regular expressions to get markdwon string
           3. live Preview markdown string
           4. Easily export directly to PDF or HTML))
```

## Advantages

- fast, live, simple, no interference.

- It don't break the syntax of any programming language, you can compile directly. 
  comment area markup method can be applied to any programming language and any markup 
  (including Org,rst, asciidoc, etc.), which is the greatest advantage.

- you only need a single line code to delete line comment characters with regular expressions, 
  then you can use any Markdown parse or converter.

- Support any code editor that supports Markdwon Live preview, 
  allowing the source code of any programming language to become rich text in real time. 
  In the code's comment area, You can use the markdown to draw flowcharts, tables, task lists, 
  and display images on the live preview panel, enhance the readability of your code.

- If you extend the Markdwon tag, you can implement the eval code, print result, display 
  data visualization and other instruction tags, to achieve live programming, live test.

- When writing (reading or refactoring) code files, It can modify and live preview directly 
  in the editor without exporting or any preprocessing.

- Reliable. Maximum code accuracy is guaranteed, and markup language errors do not affect the code.

- It hasn't interfere anyone to read the code.
  Markdown is simple, so if it doesn’t have syntax highlighting, 
  it doesn’t have much effect on writing and reading.
  And having a gray comment area doesn’t affect reading code, 
  especially for people who don’t understand the markup language.
  Strict distinction between markdown and code, 
  and gray comment area can reduce the amount of information in the source code file, 
  conducive to reading code.

## Example

```clojure
;### Markdown literary programming
;#### example01:
;![Warehouse Workshop Model](./Warehouse-Workshop-Model.svg)
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

## Live Preview Effects

> 
> ### Markdown literary programming
> #### example01:
> ![Warehouse Workshop Model](./Warehouse-Workshop-Model.svg)
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
