# UML & Markdown Summary

<!-- 
    Hint for editing: Use *Visual Studio Code* together with the plugins
    *plantUML*,
    *Markdown All in One* and
    *Markdown PDF*
-->

## Table of Contents

- [UML & Markdown Summary](#uml--markdown-summary)
  - [Table of Contents](#table-of-contents)
  - [Links & Sources](#links--sources)
  - [Markdown Syntax](#markdown-syntax)
      - [Page break](#page-break)
  - [plantUML Introduction](#plantuml-introduction)
    - [Usage of plantUML within a Markdown document](#usage-of-plantuml-within-a-markdown-document)
    - [Basic Syntax](#basic-syntax)
    - [Available Diagrams](#available-diagrams)
  - [UML Diagrams](#uml-diagrams)
    - [Sequence Diagram](#sequence-diagram)
    - [Usecase Diagram](#usecase-diagram)
    - [Class Diagram](#class-diagram)
      - [Class Notation](#class-notation)
      - [Association](#association)
      - [Dependency](#dependency)
      - [Aggregation](#aggregation)
      - [Composition](#composition)
      - [Inheritance](#inheritance)
      - [Interface Realization (Interface Inheritance)](#interface-realization-interface-inheritance)
    - [Activity Diagram (Flow Chart)](#activity-diagram-flow-chart)
    - [Component Diagram](#component-diagram)
    - [State Diagram](#state-diagram)
    - [Object Diagram](#object-diagram)
    - [Deployment Diagram](#deployment-diagram)
    - [Timing Diagram](#timing-diagram)
    - [plantUML formatting / styles](#plantuml-formatting--styles)
      - [Border around the diagrams](#border-around-the-diagrams)
      - [Black White diagrams](#black-white-diagrams)
    - [UML compliant appearance](#uml-compliant-appearance)
    - [together](#together)
  - [Non-UML Diagrams](#non-uml-diagrams)
    - [MindMap Diagram](#mindmap-diagram)
      - [Basic MindMap syntax](#basic-mindmap-syntax)
      - [Headers etc.](#headers-etc)
      - [Markdown compliant](#markdown-compliant)
      - [Symbols](#symbols)

<div style="page-break-after: always;" />

## Links & Sources

* [UML Diagrams: Wikipedia](https://en.wikipedia.org/wiki/Unified_Modeling_Language#Diagrams)
* [UML Diagrams: uml-diagrams.org](https://www.uml-diagrams.org/class-diagrams-overview.html)
* [UML Basic Notations: tutorialspoint.com](https://www.tutorialspoint.com/uml/uml_basic_notations.htm)
* [UML Quick Reference: nomagic.com](https://www.nomagic.com/support/quick-reference-guides)
* [UML Notation Overview (German): oose.de](https://www.oose.de/wp-content/uploads/2012/05/UML-Notations%C3%BCbersicht-2.5.pdf)
* [Markdown Syntax: commonmark.org](https://commonmark.org/help/)
* [plantUML.com](https://plantuml.com/en/)
* [plantUML Reference Guide: deepu.js.org](https://deepu.js.org/svg-seq-diagram/Reference_Guide.pdf)
* [Hyperlinks in plantUML](https://plantuml.com/de/link))

## Markdown Syntax

Special:

#### Page break
```
<div style="page-break-after: always;" />
```

## plantUML Introduction

### Usage of plantUML within a Markdown document

Within a markdown document a plantUML section is marked with the tags `@startuml` and `@enduml`.

Example:

```{.md}
@startuml
Class1 <|-- Class2 : Inheritance
@enduml
```

Result:

@startuml
Class1 <|-- Class2 : Inheritance
@enduml

<div style="page-break-after: always;" />

### Basic Syntax

* See also [https://plantuml.com/de/creole](https://plantuml.com/de/creole)

@startuml
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2

    title This is a diagram title

    ' This is a (one line) comment. This line will be ignored by plantUML.

    /' This is ...
       ... a multiline comment.
    '/

    note left
        This is **bold**
        This is //italic//
        This is ""monospaced""
        This is --stroked--
        This is __underlined__
    end note
@enduml

```{.md}
title This is a diagram title

' This is a (one line) comment. This line will be ignored by plantUML.

/' This is ...
   ... a multiline comment.
'/

note left
        This is **bold**
        This is //italic//
        This is ""monospaced""
        This is --stroked--
        This is __underlined__
end note
```

@startuml
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2

    note left
        note at the left side
    end note

    note right
        note at the right side
    end note

    note bottom
        note at the bottom
    end note

    note top
        note at the top
    end note
@enduml

```{.md}
note left
    note at the left side
end note

note right
    note at the right side
end note

note bottom
    note at the bottom
end note

note top
    note at the top
end note
```

<div style="page-break-after: always;" />

### Available Diagrams

UML Diagrams:

* [Sequence diagram](https://plantuml.com/en/sequence-diagram)
* [Usecase diagram]()
* [Class diagram]()
* [Activity diagram](https://plantuml.com/en/activity-diagram-beta)
* [Component diagram](https://plantuml.com/en/component-diagram)
* [State diagram](https://plantuml.com/en/state-diagram)
* [Object diagram](https://plantuml.com/en/object-diagram)
* [Deployment diagram](https://plantuml.com/en/deployment-diagram)
* [Timing diagram](https://plantuml.com/en/timing-diagram)

Non-UML Diagrams:

* [Wireframe GUI]()
* [Archimate diagram]()
* [SDL - Specification and Description Language]()
* [Ditaa diagram]()
* [Gantt diagram]()
* [MindMap]()
* [Work Breakdown Structure diagram]()
* [Entity Relationship diagram]()

## UML Diagrams

* The standard plantUML style does not perfectly comply with the UML standard. To be more compliant use `skinparam style strictuml`.
* To get a non-colored diagram `skinparam monochrome true` can be used.

### Sequence Diagram

@startuml
    skinparam legendFontName Consolas
    skinparam noteFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    title Sequence Diagram

    class1 -> class2 : DoSomething()

    legend
        plantUML:
            //class1 -> class2 : DoSomething()//
    end legend
@enduml

### Usecase Diagram

@startuml
    skinparam legendFontName Consolas
    skinparam noteFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    left to right direction

    title Use Case Diagram
    
    Actor --> (Use Case)
    legend
        plantUML:
            //Actor --> (Use Case)//
    end legend
@enduml

### Class Diagram

See also:
* [Class Diagrams Overview: uml-diagrams.org](https://www.uml-diagrams.org/class-diagrams-overview.html)
* [Class Diagram: plantuml.com](https://plantuml.com/en/class-diagram)

#### Class Notation
@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    skinparam classFontName Consolas    
    skinparam classAttributeFontName Consolas
    'hide empty members
    'left to right direction

    class ClassName
    {
        ' {field} is used to explicitely mark a field, that contains () braces,
        ' so that it is not interpreted as a method.

        field1 : Type = DefaultValue
        {field} -private_field   : Type   //(private)//
        {field} #protected_field : Int32  //(protected)//
        ~internalMethod() : ReturnType //(internal)//
        +publicMethod()    : string    //(public)//
    }

    note right
        plantUML:
           class ClassName
           {
               field1 : Type = DefaultValue
               -private_field    : Type
               #protected_field  : Int32
               ~internalMethod() : ReturnType
               +publicMethod()    : string
           }
    end note

@enduml

#### Association

@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    skinparam classFontName Consolas    
    skinparam classAttributeFontName Consolas
    
    hide empty members
    left to right direction

    class1 "1" -- "*" class2

    note right 
        **__Association__**
            - "class1 and class2 are associated"
            - "The relation consists of 1 object of class1 
               and any number of objects (0 .. ∞) of class2"
        plantUML:
           //class1 "1" -- "*" class2//
    end note
@enduml

@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction

    Book "1..*" -- "1..*" Author: < wrote
    note right
        **__Association: Example__**
        
        plantUML:
            //Book "1..*" -- "1..*" Author: < wrote//
    end note
@enduml

@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction

    class1 "1" -- "*" class2
    (class1, class2) .. "AssociationClass"
        
    note right of class2
        **__Attributed Association__**
        plantUML:
           //class1 "1" -- "*" class2//
           //(class1, class2) .. "AssociationClass"//
    end note
@enduml

#### Dependency
@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction

    class1 ..> class2 : uses >
    
    note bottom of class1
        Dependend
    end note

    note bottom of class2
        Independend
    end note

    note right of class2
        **__Dependency__**
        plantUML:
           //class1 ..> class2 : uses >//
    end note
@enduml

#### Aggregation
@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction
    
    class1 --o class2 : < has

    note right
        **__Aggregation__**
            - class1 is part of class2.
            - class1 can exist independent of class2.
        plantUML:
           //class1 --o class2 : < has//
    end note
@enduml

#### Composition
@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction
    
    class1 --* class2 : < owns

    note right
        **__Composition__**
            - class1 is part of class2.
            - class1 can //not// exist without class2.
        plantUML:
           //class1 *-- class2 : < owns//
    end note
@enduml


#### Inheritance

@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction

    class1 <|-- class2

    note right
        **__Inheritance__**
          - "class2 inherits from class1"
          - "class2 extends class1"
        
        plantUML: 
           //class1 <|-- class2//
        or:
           //class class2 extends class1//
    end note
    
@enduml

#### Interface Realization (Interface Inheritance)
@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction

    interface interface1
    interface1 <|.. class2

    note right 
        **__Interface Realization__**
            **__(Interface Inheritance)__**
            - "class2 implements interface1"
            - "class2 realizes interface1"
            - "class2 inherits from interface1"
        
        plantUML: 
           //interface interface1//
           //interface1 <|.. class2//
        or:
           //class class1 implements interface1//
    end note
@enduml

<div style="page-break-after: always;" />

### Activity Diagram (Flow Chart)

[plantUML: NEW Activity Diagram Syntax](http://plantuml.com/activity-diagram-beta)

@startuml
    skinparam legendFontName Consolas
    skinparam noteFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    title Activity Diagram

    start
    :step 1;
    if (Check) then (success)
        :step 2a;
    else (fail)
        :step 2b;
    endif
    stop

    legend
        plantUML:
            //start//
            //:step 1;//
            //if (Check) then (success)//
                //:step 2a;//
            //else (fail)//
                //:step 2b;//
            //endif//
            //stop//
    end legend
@enduml

@startuml
    skinparam legendFontName Consolas
    skinparam noteFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    'skinparam style strictuml
    'skinparam monochrome true

    'hide empty members
    'left to right direction

    start
    note right
        //plantUML://
            start
    end note

    :Step01;
    note right
        //plantUML://
            :Step01;
    end note

    if (CONDITION) then (yes)
        :StepA;
    else (no)
        :StepB;
    endif
    note right
        //plantUML://
            if (CONDITION) then (yes)
                :StepA;
            else (no)
                :StepB;
            endif
    end note

    :Step02
    Second line;
    note right
        //plantUML://
           :Step02
           Second line;
    end note

    while (CONDITION)
        note right
            //plantUML://
                while (CONDITION)
                    :Step03;
                    :Step04;
                endwhile
        end note
        :Step03;
        :Step04;
    endwhile
    
    repeat
        note
            //plantUML://
                repeat
                    :Step05;
                    :Step06;
                repeat while (CONDITION)
        end note
        
        :Step05;
        :Step06;
    repeat while (CONDITION)
    
    stop
    note right
        //plantUML://
            stop
    end note
@enduml

<div style="page-break-after: always;" />


@startuml

title Connector & Detach

start
:Step01;
(A)
detach
note right: Connector

(A)
:Step02;
stop
@enduml

@startuml

title Grouping (partitions)

start
partition Group1{
    :Step01;
    :Step02;
}
partition Group2{
    :Step03;
    :Step04;
}
stop
@enduml

@startuml

title Fork

:start;
fork
    :foo1;
    :foo2;
fork again
    :foo3;
    detach
endfork

stop

@enduml

### Component Diagram

@startuml
    skinparam legendFontName Consolas
    skinparam noteFontName Consolas
    'skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    title Component Diagram

    interface "Interface1 \n(provided \n interface)" as Interface1

    interface "Interface2 \n(Used\nInterface)" as Interface2

    Interface1 - [Component] : provide
    [Component] ..> Interface2 : use
    
    [Component]
    legend
        plantUML:
            //interface Interface1//
            //interface Interface2//
            //[Component]//

            //Interface1 - [Component] : provide//
            //[Component] ..> Interface2 : use//
    end legend
@enduml

### State Diagram

@startuml
    skinparam legendFontName Consolas
    skinparam noteFontName Consolas
    'skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    title State Diagram

    [*] -> State1

    State1: **entry** action
    State1: **do** action
    State1: **exit** action

    State1 -> State2
    State2 -> State1
    State2 -> [*]

    legend
        plantUML:
            [*] -> State1
            State1 -> State2
            State2 -> State1
            State2 -> [*]

            State1: **entry** action
            State1: **do** action
            State1: **exit** action
    end legend
@enduml

### Object Diagram

@startuml
    skinparam legendFontName Consolas
    skinparam noteFontName Consolas
    'skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    title Object Diagram

    hide empty members

    object __Object__ {
        field1 = 5
        field2 = "abc"
    }

    class Class1

    legend
        plantUML:
            //object __Object__ {//
                //field1 = 5//
                //field2 = "abc"//
            //}//

            //class Class1//
    end legend
@enduml

### Deployment Diagram

<div style="page-break-after: always;" />
### Timing Diagram

@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    'skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    skinparam legendBorderColor white
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    'skinparam LegendFontSize 12

    title Timing Diagram

    clock clk with period 1

    binary "Binary" as B
    @0
    B is low
    @1
    B is high
    @2
    B is low

    robust "Robust" as R
    @0
    R is state1
    @1
    R is state2
    @2
    R is state3
    @3
    R is state1

    concise "Concise" as C
    @0
    C is state1
    @1
    C is state2
    @2
    C is state3

    @1
    R -> B@2 : message1

    legend
        plantUML:
            //clock clk with period 1//

            //binary "Binary" as B//
            //@0//
            //B is low//
            //@1//
            //B is high//
            //@2//
            //B is low//

            //robust "Robust" as R//
            //@0//
            //R is state1//
            //@1//
            //R is state2//
            //@2//
            //R is state3//
            //@3//
            //R is state1//

            //concise "Concise" as C//
            //@0//
            //C is state1//
            //@1//
            //C is state2//
            //@2//
            //C is state3//

            //@1//
            //R -> B@2 : message1//
    end legend
  
@enduml

<div style="page-break-after: always;" />

### plantUML formatting / styles

#### Border around the diagrams

```
@plantuml
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    ...
```

#### Black White diagrams

```
@plantuml
    skinparam monochrome true
    ...
```

@startuml
    skinparam monochrome true
    class Class1
@enduml

### UML compliant appearance

The default style of plantUML does not completely match the official UML definition. To change the style to comply as far as possible with the official UML defintion, set the `strictuml` style.

@startuml
    class Class1
    note right
        plantUML:
            //class Class1//
    end note
@enduml

@startuml
    skinparam style strictuml
    class Class1
    note right
        plantUML:
            //skinparam style strictuml//
            //class Class1//
    end note
@enduml

@startuml
    skinparam style strictuml
    hide empty members
    class Class1
    note right
        plantUML:
            //skinparam style strictuml//
            //**hide empty members**//
            //class Class1//
    end note
@enduml

### together

To influence how multiple classes are arranged in large diagrams, the ´Together{}´ keyword can be used:

```
Together{
    class A
    class B
}
```

<div style="page-break-after: always;" />

## Non-UML Diagrams

### MindMap Diagram

#### Basic MindMap syntax

@startmindmap

* Root node
'* A second root node is not allowed
** Node
*** Subsubnode
**_ Node without box

left side

** left side node
** second

@endmindmap

@startmindmap

+ Root Node
++ Alternative notation with ++
-- '--' Chooses the left side
---_ Subnode
---_ Subnode
-- <s>Strike through</s>
@endmindmap

#### Headers etc.

@startmindmap

header My Header
title My Title

* one
** two
** three

legend right
    My
    Legend
end legend

caption My Caption
center footer My Footer
@endmindmap

#### Markdown compliant

@startmindmap

* **Markdown syntax**
	* indented by **TAB**
	* intention by space\n is currently not possible
		* one
		* two
	* three
@endmindmap

#### Symbols

@startmindmap

* Symbols
	* <&flag> <&flag >
	* <&globe> <&globe >
	* <&graph> <&graph >
	* <&pulse> <&pulse >
	* <&people> <&people >
	* <&star> <&star >

@endmindmap
