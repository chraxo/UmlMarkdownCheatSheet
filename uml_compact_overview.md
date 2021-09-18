# UML Compact Overview

<!-- 
    Hint for editing: Use *Visual Studio Code* together with the plugins
    *plantUML*,
    *Markdown All in One* and
    *Markdown PDF*
-->

## Class Diagram

### Class Details

@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    ' skinparam legendBorderColor white
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
           //class ClassName//
           //{//
               //field1 : Type = DefaultValue//
               //-private_field    : Type//
               //#protected_field  : Int32//
               //~internalMethod() : ReturnType//
               //+publicMethod()    : string//
           //}//
    end note

@enduml

## Class Relations

@startuml
    skinparam noteFontName Consolas
    skinparam legendFontName Consolas
    skinparam noteBackgroundColor white
    skinparam legendBackgroundColor white
    ' skinparam legendBorderColor white
    'skinparam DiagramBorderColor black
    'skinparam DiagramBorderThickness 2
    skinparam style strictuml
    'skinparam monochrome true

    hide empty members
    left to right direction

    class "interface1" as realInterface1
    class "class2" as realClass2

    class "class1" as inhClass1
    class "class2" as inhClass2

    class "class1" as compClass1
    class "class2" as compClass2

    class "class1" as aggClass1
    class "class2" as aggClass2
    
    class "class1" as depClass1
    class "class2" as depClass2

    class "Book" as assBook
    class "Author" as assAuthor
    
    ' ##### Association #####
    assBook "1..*" -- "1..*" assAuthor: < wrote
    note right
        **Association**
    end note

    ' ##### Dependency #####
    depClass1 ..> depClass2 : uses >    
   '  note bottom of depClass1
    '     Dependent
    ' end note
    ' note bottom of depClass2
   '      Independent
    ' end note
    note right of depClass2
        **Dependency**
    end note

    ' ##### Aggregation #####
    aggClass1 --o aggClass2 : < has
    note right
        **Aggregation**
    end note

    ' ##### Composition #####
    compClass1 --* compClass2 : < owns
    note right
        **Composition**
    end note

    ' ##### Inheritance #####
    inhClass1 <|-- inhClass2 :  < extends
    note right
        **Inheritance**
        (class2 inherits from class1)
    end note

    ' ##### Interface Realization (Interface Inheritance) #####
    realInterface1 <|.. realClass2 :  < implements
    note right 
        **Interface Realization**
        (also **"Interface Inheritance"**)
    end note

@enduml
