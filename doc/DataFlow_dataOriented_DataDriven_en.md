# The difference between Data-oriented, Data-driven, The Pure Function Pipeline Data Flow with Principle-based Warehouse/Workshop Model

Copyright © 2021.02.22 Lin Pengcheng. All rights reserved.

## Data-driven programming

- Eric Steven Raymond, The Art of Unix Programming

  > [Chapter9.Generation: Data-Driven Programming](https://homepage.cs.uri.edu/~thenry/resources/unix_art/ch09s01.html)
  > 
  > Data-driven programming one clearly distinguishes code 
  > from the data structures on which it acts, and designs both 
  > so that one can **make changes to the logic of the program 
  > by editing not the code but the data structure**.

- [Wikipedia: Data-driven programming](https://en.wikipedia.org/wiki/Data-driven_programming)

  > In computer programming, data-driven programming is 
  > a programming paradigm in which the program statements 
  > describe the data to be matched and the processing required 
  > rather than defining a sequence of steps to be taken.

- Core features

   - make changes to the logic of the program 
     by editing not the code but the data structure
  
   - Separation of code and data structure

## Data-Oriented design (programming)

- [Wikipedia: Data-oriented design(programming)](https://en.wikipedia.org/wiki/Data-oriented_design)

  > In computing, data-oriented design is 
  > a program optimization approach motivated 
  > by efficient usage of the CPU cache, 
  > used in video game development.
  > The approach is to focus on the data layout, 
  > separating and sorting fields according to 
  > when they are needed, and to think about 
  > transformations of data. 
  
- [Noel, Data-Oriented Design (Or Why You Might Be Shooting Yourself in The Foot With OOP)](https://gamesfromwithin.com/data-oriented-design)

  > Data-oriented design shifts the perspective of 
  > programming from objects to the data itself: 
  > The type of the data, how it is laid out in memory, 
  > and how it will be read and processed in the game.
  > 
  > Programming, by definition, is about transforming data: 
  > It’s the act of creating a sequence of machine instructions 
  > describing how to process the input data and 
  > create some specific output data. 
  
- Richard Fabian, Data-Oriented Design

  > [1.1 It's all about the data](https://www.dataorienteddesign.com/dodbook/node2.html#SECTION00210000000000000000)
  > 
  > In essence, data-oriented design is the practice 
  > of designing software by developing transformations 
  > for well-formed data where the criteria for well-formed 
  > is guided by the target hardware and the patterns 
  > and types of transforms that need to operate on it. 
  
## Difference 

- Data-driven programming
  - make changes to the logic of the program 
    by editing not the code but the data structure
  - clearly distinguishes code from 
    the data structures on which it acts
  
- Data-Oriented design (programming)
  - It is a program optimization approach
  - motivation: efficient usage of the CPU cache
  - approach: focus on the data layout, 
    separating and sorting fields according to 
    when they are needed, and to think about 
    transformations of data.
  
- The Pure Function Pipeline Data Flow with 
  Principle-based Warehouse/Workshop Model
  
  - It is a system theory, including a series of 
    complete, simple and unified theories including 
    architecture, programming, principles, quality control, 
    and aesthetics. It is highly unified with the theory of manufacturing, 
    integrated circuits, and computer hardware architecture.
    The other two methods lack this complete, 
    simple and unified system theory.
    
  - optimization approach
  
    - The scheduling function dynamically plans 
      the order of completion of tasks according to 
      the Gantt chart algorithm, and calls the workshop 
      to complete the assigned tasks. This approach is the most efficient, 
      and there is no resource competition and transaction conflict. 
      
    - System continuity: Software is a factory that produces data. 
      By designing an excellent product (data) standard specification, 
      the software is designed into a simple, efficient, reliable, 
      and smooth data manufacturing production line. 
      It pays attention to the continuity of the data flow of the entire system,
      The entire runtime system is a continual flow of the river system, 
      or a running integrated circuit system, in the system, 
      the data flow (water flow, current) continues to flow smoothly. 
      It is essentially a continuous running tree Gantt chart.
      
    - Warehouse/workshop model is conducive to global optimization
      
    - `Data-Oriented design (programming)`: 
      focus on the data layout, separating and sorting fields according to 
      when they are needed, and to think about transformations of data. 
    
    - `Data-driven programming`: There is no such content.
    
  - It can be compatible with and absorb `Data-Oriented design (programming)` 
    and `Data-driven programming` as a technical means.
    
  - It is strongly related to RMDB, MVCC, and its goal is similar to Clojure's early concept STM, 
    but unfortunately, STM does not seem to be popular in the clojure community now.

  - Like lisp, it pursues simplicity and unity, but it seems that it has only become the publicity slogan 
    for macros and S expressions in the lisp community.
    
  - It is derived from Clojure's data-oriented programming ideas and pipeline functions (->>, ->), 
    but unfortunately, some people in the Clojure community do not like to use the two together.
    When it published related topics in the Clojure community, it was often complained, 
    so that it was hidden and deleted.