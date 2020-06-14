# UML & Markdown

<!-- Hint: use Visual Studio Code with packages *plantUML* and *Markdown PDF*  -->

## Table of Contents

- [UML & Markdown](#uml--markdown)
  - [Table of Contents](#table-of-contents)
  - [Links & Sources](#links--sources)
  - [TODO](#todo)
  - [plantUML Introduction](#plantuml-introduction)
    - [Available Diagrams](#available-diagrams)
    - [Use plantUML within a Markdown document](#use-plantuml-within-a-markdown-document)
  - [UML Diagrams (UML 2.5)](#uml-diagrams-uml-25)
    - [Class Diagram](#class-diagram)
      - [Class Notation](#class-notation)
      - [Association](#association)
      - [Dependency](#dependency)
      - [Aggregation](#aggregation)
      - [Composition](#composition)
      - [Inheritance](#inheritance)
      - [Interface Realization (Interface Inheritance)](#interface-realization-interface-inheritance)
    - [Activity Diagram (Flow Chart)](#activity-diagram-flow-chart)
      - [Connector & Detach](#connector--detach)
      - [Grouping (partitions)](#grouping-partitions)
      - [Detach](#detach)
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
* [plantUML: plantuml.com](https://plantuml.com/en/)
* [plantUML Reference Guide: deepu.js.org](https://deepu.js.org/svg-seq-diagram/Reference_Guide.pdf)

## TODO

Notes:
```
' Helps sorting the classes:
Together{
    class A
    class B
}
```

## plantUML Introduction

### Available Diagrams

@startuml
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2

    skinparam style strictuml

    title Sequence Diagram

    class1 -> class2 : DoSomething()
@enduml

@startuml
    skinparam DiagramBorderColor black
    skinparam DiagramBorderThickness 2
    skinparam Shadowing false

    skinparam style strictuml

    left to right direction

    title Use Case Diagram
    
    Actor1 --> (Use Case)
@enduml

TODO: ... to be continued... 

### Use plantUML within a Markdown document

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

### Formatting

* See also [https://plantuml.com/de/creole](https://plantuml.com/de/creole)

@startuml

    ' Choose the "strictuml" style to more comply with the UML specification
    skinparam style strictuml

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

    ' Choose the "strictuml" style to more comply with the UML specification
    skinparam style strictuml

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

<div style="page-break-after: always;" />

## UML Diagrams (UML 2.5)

* The standard plantUML style does not perfectly comply with the UML standard. To be more compliant use `skinparam style strictuml`.
* To get non-colored diagram the setting `skinparam monochrome true` can be used.

### Class Diagram

See also:
* [Class Diagrams Overview: uml-diagrams.org](https://www.uml-diagrams.org/class-diagrams-overview.html)
* [Class Diagram: plantuml.com](https://plantuml.com/en/class-diagram)

#### Class Notation
@startuml
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    'hide empty members
    'left to right direction
    skinparam style strictuml

    class ClassName
    {
        field1 : Type = DefaultValue
        {field} -field2 : Type     //(private)//
        {field} #field3 : Int32    //(protected)//
        ~method1() : ReturnType  //(internal)//
        +method2() : string      //(public)//
    }

    note right
        plantUML:
           class ClassName
           {
               field1 : Type = DefaultValue
               {field} -field2 : Type     //(private)//
               {field} #field3 : Int32    //(protected)//
               ~method1() : ReturnType  //(internal)//
               +method2() : string      //(public)//
           }

        hint: {field} is used to mark attributes, 
              which contain () braces.
    end note

@enduml

#### Association

@startuml
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    hide empty members
    left to right direction
    skinparam style strictuml

    class1 "1" -- "*" class2

    note right 
        **__Association__**
            - "class1 and class2 are associated"
            - "The relation consists of **1** object of class1 
               and * objects of class2"
        plantUML:
           //class1 "1" -- "*" class2//
    end note
@enduml

@startuml
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    hide empty members
    left to right direction
    skinparam style strictuml

    Book "1..*" -- "1..*" Author: < wrote
    note right
        Example for an association
    end note
@enduml

@startuml
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    hide empty members
    left to right direction
    skinparam style strictuml

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
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    hide empty members
    left to right direction
    skinparam style strictuml

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
           //class1 ..> class2 : depends on >//
    end note
@enduml

#### Aggregation
@startuml
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    hide empty members
    left to right direction
    skinparam style strictuml
    
    class1 --o class2 : < has

    note right
        **__Aggregation__**
            - class1 is part of class2.
            - class1 can exist independent of class2.
        plantUML:
           //class1 --o class2 : Aggregation//
    end note
@enduml

#### Composition
@startuml
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    hide empty members
    left to right direction
    skinparam style strictuml
    
    class1 --* class2 : < owns

    note right
        **__Composition__**
            - class1 is part of class2.
            - class1 can //not// exist without class2.
        plantUML:
           //class1 *-- class2 : Composition//
    end note
@enduml


#### Inheritance
@startuml
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    'hide empty members
    'left to right direction
    skinparam style strictuml

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
    skinparam classFontName Consolas
    skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    'hide empty members
    'left to right direction
    skinparam style strictuml

    interface interface1
    interface1 <|.. class2

    note right 
        **__Interface Realization__**
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
    'skinparam classFontName Consolas
    'skinparam classAttributeFontName Consolas
    skinparam noteFontName Consolas

    'hide empty members
    'left to right direction
    'skinparam style strictuml

    title: Activity Diagram / Flow Chart

    start
    note right
        //plantUML://
            start
    end note

    :Step01
    Second line;
    note right
        //plantUML://
            :Step01
            Second line;
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

    :Step02;
    note right
        //plantUML://
           :Step02;
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

<div style="page-break-after: always;" />

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
