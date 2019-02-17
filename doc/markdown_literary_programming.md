## Markdown Literary programming for compatible codes

Copyright © 2018 Lin Pengcheng. All rights reserved.

Just add a custom line comment character before each line of Markdown.

When previewing or converting a format, you only need to simply preprocess: replace the `\r\n\;` with `\r\n`

Note: line comment character of Clojure(Lisp) is `;`

## example:

```
;# Markdown literary programming
;## example01:
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

## Screenshot

![](#./markdown_literary_programming.png)
