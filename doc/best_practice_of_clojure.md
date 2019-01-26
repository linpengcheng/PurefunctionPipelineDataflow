# The Best Practice of Clojure
# Clojure最佳实践

---- from the largest personal Clojure project (Lin Pengcheng Financial Analyser )

Copyright © 2018 Lin Pengcheng. All rights reserved.

版权所有 © 2018 林鹏程， 保留所有权利。

- IDE: Notepad++ (ClojureBoxNpp)
- Version Control: 7z.exe
- Programming ideas (PurefunctionPipelineDataflow)simulate the following list:
  - Imaginative programming： Everything is an algorithm, at your fingertips.
  - The most valuable chapter of "Code Complete" : Chapter 2 Metaphors for a Richer Understanding of Software Development
  - Business management thinking
  - Pipeline technology for large industrial production
  - Business process reengineering
  - Enterprise organization, system, process design thinking
  - Accounting
  - Integrated circuit diagram
  - Urban water network
  - Boeing aircraft pulse production line technology
  - Confluence technology of rivers from the source to the sea
- Data-centric, dataflow, designing a data model that is simple and fluent in manipulation. 
The line between the two points is the shortest, and the data is directly manipulated 
from the initial state to the final state.
- Pure Clojure.
- Don't use OO, FP, AOP. They are overly complex hand-workshop-level technologies.
- Don't write middleware, macros, loop. They are hard to read, difficult to debug and observe.
- repl drive development.
- Try to design a pure function (pipe function) of a single hash-map parameter.
- Minimize front-end code.
- Side effects can only appear at the end of the pipe.
- Try to use thread macros.
- Code linearization, schematicization, simplification. What You See Is What You Get.
- Use namespaces to achieve good code structure.
- Normalize data.
- Data verification only appears at the beginning of the pipeline.
- Use the clojure.core API to manipulate data, enhance data model design capabilities. 
Don't use like specter lib etc.
- Use and design "simple DSL", like hiccup, honeysql etc. DSL usage is code conversion,
Using data style representation is better than using function style representation. 
A series of pipeline functions are concatenated to form a compiler 
for converting DSL data into target code and then evaluating it.
- The best abstraction is: data and logic are strictly separated, 
data-flow is current-flow, function is chip, thread macro (->>, -> etc.) is a wire, 
and the entire system is an integrated circuit that is energized.

