# Markdown Literary programming that don't break the syntax of any programming language

Copyright © 2018 Lin Pengcheng. All rights reserved.

## Table of Contents 目录
- [Comment Area Markup Method](#Comment-Area-Markup-Method)
- [Live Preview Panel of editor do the following work](#Live-Preview-Panel-of-editor-do-the-following-work)
- [Advantages](#Advantages)
- [Notepad++ Solutions](#NotepadPlusPlus-Solutions)
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

The method is to add extension instructions 
in any programming language comment area:
- markdown
- manual eval code, live eval code, print result, 
  display data visualization and other directives

When previewing or converting a format,
you only need to simply preprocess: 
delete line comment characters with regular expressions, 
example: `sed 's/^;//'  x.clj`

Note: 

- line comment character of Clojure(Lisp) is `;`
- line comment characters of the current file type
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
       (do 0. get line-comment-characters-of-the-current-document-type
           1. get full-text-of-the-current-document
           2. delete line comment characters with regular expressions to get markdwon string
           3. live Preview markdown string
           4. Can easily export directly to PDF or HTML))
```

## Advantages

- fast, live, simple, no interference.

- It don't break the syntax of any programming language, you can compile directly. 
  comment area markup method can be applied to any programming language and any markup 
  (including Org,rst, asciidoc, etc.), which is the greatest advantage.

- you only need a single line code to delete line comment characters using regular expressions, 
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
  
## NotepadPlusPlus Solutions

### Create MLP_Clojure.bat

put to `$(NPP_DIRECTORY)\MarkdownLiteraryProgramming`

```batch

@echo off
cd /d "%~dp0"
echo "start Markdown Literary Programming converter ..."
sed\sed 's/^;//' %2 > tmp\%1.tmp.md
copy MLP_common_head.md + tmp\%1.tmp.md tmp\%1.md
..\notepad++ tmp\%1.md
del  tmp\%1.tmp.md
echo "finish Markdown Literary Programming task!"

rem %1 $(FILE_NAME)
rem %2 $(FULL_CURRENT_PATH)
REM -----------------------
rem MLP out path:
rem It can be modify to project's MLP dir,
rem default: $(NPP_DIRECTORY)\MarkdownLiteraryProgramming\tmp
REM -----------------------
rem sed: 
rem line comment characters can be modified 
rem to adopt other programming language.
rem default to Clojure `;`

```

### Add the following XML entry to Shortcuts.xml

```xml

<Command name="view Clojure Markdown Literary Programming">CMD /K $(NPP_DIRECTORY)\MarkdownLiteraryProgramming\MLP_Clojure.bat $(FILE_NAME) &quot;$(FULL_CURRENT_PATH)&quot;</Command>

```

### Common Resource

common resource (js, image, ClojureMLP.bat, etc.) 
put to `$(NPP_DIRECTORY)\MarkdownLiteraryProgramming` Directory.

### Install

- install MarkdownViewer++ plugin, Select:

```

  MarkdownViewer++ 
  Options
  HTML
  Open HTML after export
  
``` 

- install NppExec plugin, 
  - create Execute clean script: 
    `cmd /c del /F /S /Q $(NPP_DIRECTORY)\MarkdownLiteraryProgramming\tmp\*.*`
  - set Advanced Options,
    when Notepad++ exit, NppExec run clean script.
    to delete all files of output directory 
    `$(NPP_DIRECTORY)\MarkdownLiteraryProgramming\tmp`.

- Set Chrome as the default browser,
  because IE don't suport Mermaid.js of 
  HTML file exported MarkdownViewer++.

### click menu 

`run -> view Clojure Markdown Literary Programming`

### export as html

Automatically opens with chrome 
when MarkdownViewer++ viewer exports html files.

### Note:
- syntax highlighting
  - MarkdownViewer++ viewer don't support 
    syntax highlighting.
  - MarkdownViewer++ export as html, 
    chrome displaying syntax highlighting is ok.

- Mermaid charts
  - pandoc conver md to html, chrome displaying chart is failed.
  - MarkdownViewer++ export as html, chrome displaying chart is ok.
  - MarkdownViewer++ viewer only displaying Mermaid text.
  - MarkdownViewer++ viewer don't support js.
 
- Image
  - MarkdownViewer++ viewer don't support displaying image.
  - MarkdownViewer++ export as html, chrome displaying image is ok.
    

## Example

- MLP_common_head.md:

```html

<link rel="stylesheet" href="../js/prismjs/prism.css"/>
<script src="../js/prismjs/prism.js"></script>

<link rel="stylesheet" href="../js/mermaidjs/mermaid.css"/>
<script src="../js/mermaidjs/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>

```

- Clojure Source Code:

```clojure

;### Markdown literary programming Example

;#### example01: Code with syntax highlighting.

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

;return `[4 5 187 156 -9]`

;#### example02: Mermaid flow chart

;<div class="mermaid">
;graph LR
;      A-->B
;      B-->C
;      C-->A
;      D-->C
;</div>

;#### example03: Image

;![cowplot](../image/cowplot.png)

```

## Live Preview Effects

![](../image/mlp01.png)
![](../image/mlp02.png)
