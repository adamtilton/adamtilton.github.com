---
layout: post
title: "Notes on Design Concerns"
description: ""
category: 
tags: [notes, python, design, computer science, architecture]
---

[1]:  http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
[2]:  http://en.wikipedia.org/wiki/Aspect-oriented_programming
[3]:  http://en.wikipedia.org/wiki/Separation_of_concerns
[4]:  http://en.wikipedia.org/wiki/Cross-cutting_concern
[5]:  http://en.wikipedia.org/wiki/Database_normalization
[6]:  http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter
[7]:  http://en.wikipedia.org/wiki/Common_layers_in_an_information_system_logical_architecture
[8]:  http://en.wikipedia.org/wiki/Data_Access_Object
[9]:  http://en.wikipedia.org/wiki/Observer_pattern
[10]: http://en.wikipedia.org/wiki/Presentation%E2%80%93abstraction%E2%80%93control
[11]: http://en.wikipedia.org/wiki/Multitier_architecture#Three-tier_architecture
[12]: http://upload.wikimedia.org/wikipedia/commons/thumb/5/51/Overview_of_a_three-tier_application_vectorVersion.svg/400px-Overview_of_a_three-tier_application_vectorVersion.svg.png
[13]: http://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/MVC-Process.png/200px-MVC-Process.png
[14]: http://en.wikipedia.org/wiki/Design_Patterns
[15]: http://en.wikipedia.org/wiki/Concern_(computer_science)
[16]: http://en.wikipedia.org/wiki/Domain_model
[17]: http://en.wikipedia.org/wiki/Entity-relationship_model
[18]: http://upload.wikimedia.org/wikipedia/commons/thumb/7/72/ER_Diagram_MMORPG.png/450px-ER_Diagram_MMORPG.png
[19]: http://en.wikipedia.org/wiki/Three_schema_approach

## Introduction 
The goal is to develop an software architecture that separates the
concerns into modules. A [concern][15] is a particular set of
information that has an effect on the code. It can be as general as the
details of a database interaction, or as specific as performing a
primitive calculation. [Separation of concern][3] is a design principle
for separating a computer program into distinct sections, such that each
section addresses separate concerns. 

Separation of concerns is not always possible. [Cross-cutting
concerns][4] are aspects of a program that affect other concerns, and
often these are not able to be cleanly decomposed from the rest of the
system. These concerns can cause problems in design and implementation,
including scattering (code duplication), tangling (significant
dependencies), or both. 

This article discusses details of the software architecture design. The
software architecture will need three main layers: computations, data
management, and user interaction. Below are described potential design
paradigms that provide patterns for achieving this. 

## Potential Design Paradigms

### [Model View Controller (MVC)][1]
Model view controller (MVC) is a software architecture pattern which
separates the representation of information from the user's interaction
with it. There are three main componenets:

1. __Model:__ Consists of data, rules, logic, and functions. This layer
   controls manipulation of the state, and storing of the data.
1. __View:__ Any output representation, e.g. the GUI.
1. __Controller:__ The brain, which mediates converting input from the user
   into commands.

Component interactions:

1. The __controller:__
    1. send commands to its associated view to change the view's presentation
       of the model; and
    1. it can also send commands the model to update the model's state. 
1. The __model:__ 
    1. notifies it's associated views to produce update output; and
    1. notifies it's controllers controllers to change the available set of commands. 
1. A __view:__ 
    1. requests from the model the information that it needs to generate an
       output representation to the user. 

![Model View Controller][13]

MVC decouples views and models by establishing a subscribe/notify
protocol between them. A view must ensure that its appearance reflects
the state of the model. Whenever the model's data changes,the model
notifies views that depend on it. In response, each view gets an
opportunity to update itself. 

This design pattern was originally created to decouple views from
models, but the design is applicable to a more general problem:
decoupling objects so that changes to one can affect any number of
others without requiring the changed object to know details of the
others. 

The main relationships in MVC are described by the Observer, Composite,
and Strategy Patterns. See [Design Pattens][14]

### [Model-View-Presenter][6]
Model-view-presenter (MVP) is a derivative of the MVC patter. It is
mostly used for building user interfaces. 

The MVP presenter assumes the functionality of the controller.
Eventually, the model becomes strictly a domain model. 

1. __Model:__ an interface defining the data to be displayed or
   otherwise acted upon in the user interface. 
1. __View:__ a passive interface that displays data (the model) and
   routes user commands to the presenter to act upon the data.
1. __Presenter:__ acts upon the model and the view. It retrieves data
   from repositories (the model), and formates it for display in the
   view.

### [Presnetation-Abstraction-Control (PAC)][10]
Presentation-abstraction-control is an interaction-oriented software
architecture, and is similar to MVC. It separates the interactive system
into three types of components responsible for specific aspects of the
application's functionality. 

1. __Abstraction:__ Retrieves and processes the data.
1. __Presentation:__ Formats the visual and audio presentation of data.
1. __Control:__ Handles things such as the flow of control and
   communication between the other two components. 

### [Multitier Architechture][11]
Multi-tier architecture is a pattern in which presentation, application
processing, and data management functions are logically separated. The
most common use is three-tier architecture, which has the following
three tiers:

1. __Presentation Tier:__ Top most level of the application, a GUI.
1. __Logic Tier:__ Controls the applications functionality by performing
   detailed processing. 
1. __Data Tier:__ Consists of database servers. Here information is
   stored and retrieved. 

![Three-tier example][12]


The fundamental difference between three-tier and MVC is that the presentation
tier never communicates with the data tier. Conceptually, the three-tier
architecture is linear, where the MVC architecture is triangular. 



## The Domain Model
A [domain model][16] is a conceptual model of all the topics related to
a specific problem. It describes the various entities, their attributes,
roles, and relationships, plus the constraints that govern the problem
domain. The model is created to represent the vocabulary and key
concepts of the problem domain. 

Our domain model should be developed to describe the general filtering
problem. The three components of a filtering problem include:

1. __Signal:__ The variable intended to be estimated;
1. __Measurements:__ The observations made on the signal; and 
1. __Filters:__ The algorithms used to reconstruct the signal from the
   measurements.

### Signal
The signal is a state vector comprised of all the states of the signal.
It can be constructed from multiple targets, each of which has its own
state-vector. For instance, consider the situation where there are two
targets, each with a two state vector: $\[ X_j, Y_j \]$.

## More Notes
### [Data Access Object (DAO)][8]
A data access object is an object that provides an abstract interface to
some type of database or other persistence mechanism. DAOs provide some
specific data operations without exposing details of the database.

### [Observer Pattern][9]
The observer pattern is a software design patter in which an object,
called the subject, maintains a list of its dependents, called
observers, and notifies them automatically of any stat changes, usually
by calling one of their methods.

### [Database Normalization][5]
Database normalization is the process of organizing the fields and
tables of a relational database to minimize redundancy and dependency.
The objective is to isolate data so that additions, deletions, and
modifications of a field can be made in just one table and the
propagated thought the rest of the database using the defined
relationships. 

### [Aspect-Oriented Programmping (AOP)][2]
Aspect-oriented Programming (AOP) is a paradigm to increase modularity
by allowing the separation of cross-cutting concerns. It entails
breaking down program logic into distinct parts (so called concerns).
Cross-cutting concerns cut across multiple abstractions in a program.


## Database Design Paradigms
### [Entity-Relationship (ER) Model][17]
An entity-relationship (ER) model is a data model for describing a database in
an abstract way. In the case of a relational database, which stores data
in tables, some of the data in these tables point to data in other
tables. Diagrams created to design these entities and relationships are
called entity-relationship diagrams.

![Entity-Relationship Diagram][18]

#### [Three Schema Approach][19]
There are three levels of ER models that may be developed

1. __Conceptual Data Model:__ This is the highest level ER that contains
   the least level of granularity. It establishes the overall scope of
   what is to be included within the model. The purpose of the
   conceptual model is to establish the structural metadata commonality
   for the master data entities between the set of logical ER models. 
1. __Logical Data Model:__ A logical ER model contains more detail than
   the conceptual ER model. In addition to master data entities,
   operational and transactional data entities are defined. The details
   of each data entity are developed, and the entity relationships
   between these data are established. It is developed, however,
   independent of technology. 
1. __Physical Model:__ The physical ER model is normally developed to be
   instantiated as a database. Therefore, each physical ER model must
   contain enough detail to produce a database and each physical ER
   model is technology dependant. 
