---
layout: post
title: "Model View Controller"
description: ""
category: 
tags: [Computer Science, Modeling, Architecture, Design]
---
{% include JB/setup %}

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

## [Concerns][15]
A concern is a particular set of information that has an effect on the
code. A concern can be as general as the details of a database
interaction, or as specific as performing a primitive calculation.


### [Separation of Concerns][3]
Separation of Concerns (SoC) is a design principle for separating a
computer program into distinct sections, such that each section
addresses a separate concern. This leads to modular program design. 

### [Cross-Cutting Concerns][4]
Cross-cutting concerns are aspects of a program that affect other
concerns, and often are not able to be cleanly decomposed from the rest
of the system. They can often cause problems in design and
implementation, including scattering (code duplication), tangling
(significant dependencies), or both.


## Paradigms Addressing Concerns

### [Model View Controller (MVC)][1]
Model view controller (MVC) is a software architecture patter which
separates the representation of information from the user's interaction
with it. 

1. __Model:__ Consist of data, rules, logic, and function. Used to store
   and manipulate state.
1. __View:__ Any output representation. The user interface bits. 
1. __Controller:__ The brain, mediates input converting it into commands.

Component interactions:

1. The __controller__ can send commands to its associated view to change the
   view's presentation of the model. It can also send commands the
   model to update the model's state. 
1. The __model__ notifies its associated views and controllers when there
   has been a change in its state. This notification allows the views to
   produce updated output, and th controllers to change the available
   set of commands. 
1. A __view__ requests from the model the information that it needs to
   generate an output representation to the user. 

![Model View Controller][13]

#### [Further explanation][14]
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
and Strategy Patterns. 


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

## [Common Layers in an Information System Logical Architecture][7]
The following four layers are the most common layers in  logical
multilayer architecture for an information system with an OO design. A
layer is a group of classes that have the same set of link-time module
dependencies to other modules. In other words, a layer is a group of
components that are reusable in similar circumstances. This is often
expressed in terms of import dependencies

1. __Presnetation Layer:__ 
1. __Application Layer:__
1. __Business Layer:__
1. __Infrastructure Layer:__ or data access layer (DAL), provides access to
   data stored in persistent storage. It hides the complexity of the
   underlying data store from the external world. Here, all calls to the
   database are centralized. 

## [Data Access Object (DAO)][8]
A data access object is an object that provides an abstract interface to
some type of database or other persistence mechanism. DAOs provide some
specific data operations without exposing details of the database.

## [Observer Pattern][9]
The observer pattern is a software design patter in which an object,
called the subject, maintains a list of its dependents, called
observers, and notifies them automatically of any stat changes, usually
by calling one of their methods.

## [Presnetation-Abstraction-Control (PAC)][10]
Presentation-abstration-control is an interaction-oriented software
architecture, and is similar to MVC. It separates the interactive system
into three types of componenets responsible for specific aspects of the
application;s functionality. 

1. __Abstraction:__ Retrieves and processes the data.
1. __Presentation:__ Formats the visual and audio presentation of data.
1. __Control:__ Handles things such as the flow of control and
   communication between the other two components. 

## [Multitier Architechture][11]
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


### Comparison with MVC Architecture
The fundamental difference is that the presentation tier never
communicates with the data tier. Conceptually, the three-tier
architecture is linear, where the MVC architecture is triangular. 



## [Database Normalization][5]
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

## [Domain Model][16]
A domain model is a conceptual model of all the topics related to a
specific problem. It describes the various entities, their attributes,
roles, and relationships, plus the constraints the govern the problem
domain. The model is created to represent the vocabulary and key
concepts of the problem domain. It identifies the relationships among
all entities within the scope of the problem domain, and commonly
identifies their attributes and methods. 

