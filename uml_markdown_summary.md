# UML & Markdown

<!-- Hint: use Visual Studio Code with packages *plantUML* and *Markdown PDF*  -->

## Table of Contents

- [UML & Markdown](#uml--markdown)
  - [Table of Contents](#table-of-contents)
  - [Links & Sources](#links--sources)
  - [plantUML Introduction](#plantuml-introduction)
    - [Available Diagrams](#available-diagrams)
    - [Usage](#usage)
      - [Inheritance](#inheritance)
      - [Realization (Interface inheritance)](#realization-interface-inheritance)
      - [Association](#association)
      - [Composition](#composition)
      - [Aggregation](#aggregation)
    - [Activity Diagram (Flow Chart)](#activity-diagram-flow-chart)
      - [Connector & Detach](#connector--detach)
      - [Grouping (partitions)](#grouping-partitions)
      - [Detach](#detach)
    - [MindMap Diagram](#mindmap-diagram)
      - [Basic MindMap syntax](#basic-mindmap-syntax)
      - [Headers etc.](#headers-etc)
      - [Markdown compliant](#markdown-compliant)
      - [Symbols](#symbols)

## Links & Sources

* [UML Diagrams: Wikipedia](https://en.wikipedia.org/wiki/Unified_Modeling_Language#Diagrams)
* [UML Diagrams: uml-diagrams.org](https://www.uml-diagrams.org/class-diagrams-overview.html)
* [UML Basic Notations: tutorialspoint.com](https://www.tutorialspoint.com/uml/uml_basic_notations.htm)
* [UML Quick Reference: nomagic.com](https://www.nomagic.com/support/quick-reference-guides)
* [UML Notation Overview (German): oose.de](https://www.oose.de/wp-content/uploads/2012/05/UML-Notations%C3%BCbersicht-2.5.pdf)
* [Markdown Syntax: commonmark.org](https://commonmark.org/help/)
* [plantUML: plantuml.com](https://plantuml.com/en/)

## plantUML Introduction

### Available Diagrams

@startuml
title Sequence Diagram
class1 -> class2 : DoSomething()
@enduml

@startuml
left to right direction

title Use Case Diagram
Actor1 --> (Use Case)
@enduml

TODO: ... to be continued... 

### Usage

Within a markdown document a plantUML section is marked with the tags  `@startuml` and `@enduml`.

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

### Formatting

* See also [https://plantuml.com/de/creole](https://plantuml.com/de/creole)

@startuml

title Formatting + General purpose syntax

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
@startuml

title Formatting + General purpose syntax

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
```

@startuml

title Notes

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
@startuml

title Notes

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
```

### Class Diagrams (former name *"Entity-Relationship-Diagram"*)

* [Class Diagram Syntax @plantuml.com](http://plantuml.com/de/class-diagram)
* [Class Diagram (Wikipedia)](https://en.wikipedia.org/wiki/Class_diagram)

@startuml
    title Class Diagram: General Syntax
    
    ' optional switch to set the diagram orientation:
    left to right direction

    ' optional:
    hide empty members

    ' "as" sets an alias name, here "c2" for "class2"
    class "class2" as c2

    class1 "line start" -- "line end" c2 : line middle
@enduml

```{.md}
    ' optional switch to set the diagram orientation:
    left to right direction

    ' optional:
    hide empty members

    ' "as" sets an alias name, here "c2" for "class2"
    class "class2" as c2
    
    class1 "line start" -- "line end" c2 : line middle
```

#### Inheritance

@startuml
    left to right direction
    skinparam noteFontName Consolas
    hide empty members

    class1 <|-- class2

    note right of class2
        plantUML: 
           class1 <|-- class2
        or:
           class class2 extends class1
    end note
@enduml

* "class 2 inherits from class1"
* or: "class2 extends class 1"

#### Realization (Interface inheritance)

@startuml
    left to right direction
    skinparam noteFontName Consolas
    hide empty members

    interface interface1
    interface1 <|.. class2

    note right 
        plantUML:
           interface interface1
           interface1 <|.. class2
        or:
           class class1 implements interface1
    end note
@enduml

* "class2 implements interface1"
* or: "class2 realizes interface1"
* or: "class2 inherits from interface1"

#### Association

@startuml
    left to right direction
    skinparam noteFontName Consolas
    hide empty members

    title Association

    class1 "1" -- "*" class2

    note right 
        plantUML:
           class1 "1" -- "*" class2
    end note
@enduml

* "class1 and class 2 are associated"

@startuml
    left to right direction
    skinparam noteFontName Consolas
    hide empty members

    title Association with *association class*

    class1 "1" -- "*" class2
    (class1, class2) .. "AssociationClass"
        
    note right of class2
        plantUML:
           class1 "1" -- "*" class2
           (class1, class2) .. "AssociationClass"
    end note
@enduml

#### Composition
@startuml
    left to right direction
    skinparam noteFontName Consolas
    hide empty members
    
    class1 *-- class2 : Composition

    note right
        class2 can *not* exist without class1.
        plantUML:
           class1 *-- class2 : Composition
    end note
@enduml

#### Aggregation
@startuml
    left to right direction
    skinparam noteFontName Consolas
    hide empty members
    
    class1 o-- class2 : Aggregation

    note right
        class2 can exist independent of class1.
        plantUML:
           class1 o-- class2 : Aggregation
    end note
@enduml









### Activity Diagram (Flow Chart)

[plantUML: NEW Activity Diagram Syntax](http://plantuml.com/activity-diagram-beta)

@startuml
title: Activity Diagram / Flow Chart

start

note right: Some note

:Step01
Second line;

if (Some condition) then (yes)
    :StepA;
else (no)
    :StepB;
endif

:Step02;

while (WHILE LOOP: CONDITION)
    :Step03;
    :Step04;
endwhile

repeat
    :Step05;
    :Step06;
repeat while (REPEAT WHILE: CONDITION)

stop

@enduml

#### Connector & Detach

@startuml
title: Activity Diagram / Flow Chart (2)

start
:Step01;
(A)
detach
note right: Connector

(A)
:Step02;
stop
@enduml

#### Grouping (partitions)

@startuml
title Grouping
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

#### Detach

@startuml
title DETACH

:start;
fork
    :foo1;
    :foo2;
fork again
    :foo3;
    detach
endfork

if (foo4) then
    :foo5;
    detach
endif

:foo6;

detach
:foo7;
stop

@enduml

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
