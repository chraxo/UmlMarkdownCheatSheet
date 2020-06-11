# UML & Markdown

<!-- Hint: use Visual Studio Code with packages *plantUML* and *Markdown PDF*  -->

## Table of Contents

- [UML & Markdown](#uml--markdown)
  - [Table of Contents](#table-of-contents)
  - [Links & Sources](#links--sources)
  - [plantUML Introduction](#plantuml-introduction)
    - [Available Diagrams](#available-diagrams)
    - [Usage](#usage)
      - [Inheritance ("arrow syntax")](#inheritance-arrow-syntax)
      - [Realization (Interface inheritance)](#realization-interface-inheritance)
      - [Association](#association)
      - [Association with *association class*](#association-with-association-class)
      - [Composition](#composition)
      - [Aggregation](#aggregation)
      - [Komposition](#komposition)
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

* [OOSE UML Notationsübersicht](https://www.oose.de/wp-content/uploads/2012/05/UML-Notations%C3%BCbersicht-2.5.pdf)
* [CommonMark: Markdown Syntax](https://commonmark.org/help/)
* [plantUML Website](https://plantuml.com/en/)

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
left to right direction

class "class2" as c2
class1 "line start" -- "line end" c2 : line middle
@enduml

```{.md}
' optional switch to set the diagram orientation:
left to right direction

' "as" sets an alias name, here "c2" for "class2"
class "class2" as c2

class1 "line start" -- "line end" c2 : line middle
```

#### Inheritance ("arrow syntax")

```{.md}
class1 <|-- class2
```

@startuml
left to right direction
class1 <|-- class2
note right 
    class2 extends class 1
    (or: class 2 inherits from class1)
end note
@enduml

#### Inheritance ("extends" syntax)

```{.md}
class class2 extends class1
```

@startuml
left to right direction
class class2 extends class1
@enduml

#### Realization (Interface inheritance)

```{.md}
interface1 <|.. class2
```

@startuml
left to right direction
interface1 <|.. class2
note right 
    class2 realizes (implements 
    / "inherits from") interface1
end note
@enduml

#### Realization (2)

```{.md}
class class2 implements interface1
```

@startuml
left to right direction
class class2 implements interface1
@enduml

#### Association

```
class1 "1" -- "*" class2
```

@startuml
left to right direction
class1 "1" -- "*" class2
note right 
    class1 and class 2 are associated
end note
@enduml

#### Association with *association class*

```
class1 "1" -- "*" class2
(class1, class2) .. "AssociationClass"
```

@startuml
class1 "1" -- "*" class2
(class1, class2) .. "AssociationClass"
@enduml


```
class1 "1" -- "*" class2
(class1, class2) . "AssociationClass"
```

@startuml
class1 "1" -- "*" class2
(class1, class2) . "AssociationClass"
@enduml

#### Composition
@startuml
left to right direction
class1 *-- class2
note right 
    Composition
end note
@enduml

#### Aggregation

```
left to right direction
class1 o-- class2
```

@startuml
left to right direction
class1 o-- class2
@enduml

#### Komposition

```
left to right direction
class1 *-- class2
```

@startuml
left to right direction
class1 *-- class2
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
