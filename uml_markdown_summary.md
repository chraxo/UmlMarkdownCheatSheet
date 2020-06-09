# UML & Markdown Summary

[plantUML](http://plantuml.com/)

## Table of Contents

- [UML & Markdown Summary](#uml--markdown-summary)
  - [Table of Contents](#table-of-contents)
    - [General plantUML syntax](#general-plantuml-syntax)
    - [Class Diagram (formerly Entity-Relationship-Diagram)](#class-diagram-formerly-entity-relationship-diagram)
    - [Activity Diagram (Flow Chart)](#activity-diagram-flow-chart)
      - [Connector & Detach](#connector--detach)
      - [Grouping (partitions)](#grouping-partitions)
      - [Detach](#detach)
    - [MindMap Diagram](#mindmap-diagram)
      - [Basic MindMap syntax](#basic-mindmap-syntax)
      - [Headers etc.](#headers-etc)
      - [Markdown compliant](#markdown-compliant)
      - [Symbols](#symbols)



### General plantUML syntax

**Markdown**
```{.md}
@startuml

title Overview about the general plantUML syntax

' This is a one line comment and will be ignored by plantUML

/' This is ...
   ... as multiline comment.
'/

note left
    This is **bold**
    This is //italic//
    This is ""monospaced""
    This is -- stroked--
    This is __underlined__
end note

@enduml
```

**Result**
@startuml

title Overview about the general plantUML syntax

' This is a one line comment and will be ignored by plantUML

/' This is ...
   ... as multiline comment.
'/

note left
    This is **bold**
    This is //italic//
    This is ""monospaced""
    This is -- stroked--
    This is __underlined__
end note

@enduml

### Class Diagram (formerly Entity-Relationship-Diagram)

[plantUML: Class Diagram Syntax](http://plantuml.com/de/class-diagram)

@startuml
title Class Diagram

' ABBREVIATIONS
class "other class" as OC
SomeClass --|> OC
note right
    here 'other class'
    has the abbre-
    viation 'OC'
end note

' CLASS RELATIONS
Class1 <|-- Class2 : Inheritance
note right 
    Class2 inherits
    from Class1
end note

Class3 "1" -- "*" Class4 : Association
note right: Class4

Class03 *-- Class04 : **Composition**\nClass04 is\npart of\nClass03
Class05 o-- Class06 : Aggregation
Class07 .. Class08

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
