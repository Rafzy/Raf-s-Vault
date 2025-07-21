#Letsgochat

# Session 1

## Software

Software -> entire set of programs, data, and related documentations
Software != program (Similar but not the same, software includes programs)

**Related terms**
- Hardware -> The physical machines (The physical components)
- Program -> Set of instructions in code that controls the operation or functions of a computer (Countable unlike software)

**Information system and software**
Sort of mechanism to process, store, and exchange information (Constructed by humans, machines, and computers)
Information processing system -> Included in information system (Computers that process information)

![[image-85.png]]

**Embedded system**
Computer system which is embedded in apparatuses
The hardware is also specifically developed for a specific system

**Characteristics of software**
- Present everywhere
- Software has variety
	- Target domains
	- Running environment
	- Development style
	- Users

**Scale of software**
The scale of a software is often described by lines of code
Roughly:
- 100 lines : Exercise of programming
- 1,000 lines : Compact
- 10,000 lines : small
- 100,000 lines : Mid size
- 1,000,000 lines : Large


## Software engineering

**Software engineering**
Study about how to develop software
Standard definition:
The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software

**Birth software engineering**
Came from *1968 NATO Software Engineering conference*

**Background of the origin**
There was a software crisis in the late 1960s
- Many problems occurred regarding software productivity & quality
- Not enough productivity in software code production
- Chang of scale brought the change of quality

**Brook's law**
> Adding more people to a late project only makes it more delayed

Number of people and development time are not interchangable

- Brook: Father of IBM system, "Mythical man month"

**Developers/month and productivity**
It's shown that the number of developers per month decreases the productivity

![[image-86.png|401x186]]


**How to develop a software**

We need the lifecycle of software devleopment:
- Requirements analysis: understand problems, acquire and order user's requirement
- Specification: Decide the software to be built
- Design: Decide the structure of software
- Coding: Write the program itself
- Test: Check that the software follows the design, specification, and requirements decided before
- Operation & Maintenance: Operate the software, and keep it up and running, because software WILL have to be maintained

**What causes errors?**

![[image-87.png|577x317]]

![[image-88.png|587x346]]


To avoid this,

**Software design is the key**
Because the complexity and size of software keeps increasing, we need good software design (It's important basically).


# Session 2

## Overview of modeling

**What is software modeling**

> Task of abstracting an information system an information system and its related things and expressing them in a formal notation

Targets of software modeling
- Real world related to an information system
- Specification of an information processing system
- Anything related to software design
- Anything related to software implementation

Software modeling != designing software, but it is part of it, and very important

**Why is it useful?**
First of all, it provides basic viewpoints and description methods, even though there are many artifacts of software development (Programs, specification, design, etc), there are patterns or common types of viewpoints and description methods used

It helps lighten the scale & complexity of software, by modeling, we can describe specific aspects of software and make them easy to understand.

It also provides an accurate way to describe software, which is important with ever growing and ever complex software

**UML**
Unified Modeling Language

![[image-89.png]]


## Class and object diagram

**Class & Object**
Class -> Abstraction of similar entities (We can imagine classes as blueprints)
Object -> Construct of a class (An implementation of a class blueprint)
These two are concepts of Object oriented programming
We can use these concepts to describe the structure of our description target

**Class diagram & Object diagram**
Class diagram -> Describes the target using classes
Object diagram -> Describes the structure of the target using objects.

## Notation of class and object diagram

**Class**
Class notation uses a box with three compartments:
- Class name
- Attributes
- Operations

![[image-90.png]]

**Attribute & Operation**
- Attribute -> Data that every object of the modeling target a class has (Usually data types)
- Operation -> A service that the class provides to the outside (Usually functions)

**Object**
Concrete example of class
- Instance of class
- Shows concrete example of data structure

![[image-91.png]]

**Notation option**
- Class name -> Mandatory
- Object name -> May be omitted
- Attributes and operations -> May be omitted

**Attribute syntax**
\[Visibility] name \[multiplicity] \[:type] \[=initial-value] \[{property-string}]
- Visibility: public '+', protected '#', private '-'
- name: (Use CamelCase)
- Multiplicity: number, range, or sequence of number or ranges
- type: built in type or user-defined class
- initial-value: Constant and user-defined object
- property-string: changeable, addOnly, frozen

**Operation syntax**
\[visibility] name \[(parameter-list)]\[:return-type]\[{property-string}]
- visibility : public '+', protected '#', or private '-'
- name : (verb or verb phase, capitalize every word except first)
- parameter-list: list of parameters
- return-type: primitive type or user defined type
- property-string: isQuery, sequential, guarded, concurrent

**Visibility**
- refers to whether an element of the class is visible from outside the class
- Typically, attributes are hidden, operations are visible

**Association**
Classes can be associated with other classes
- Line between classes describe "association"
- Association -> Structural relationship that specifies that objects of class may be **connected** to objects of another class 

![[image-92.png]]

**Association notation**
Described by a direct line
- Has label
- Multiplicity
- Association end names

![[image-93.png]]


**Label (on association)**
Indicates the association name
Optional but recommended 


**Multiplicity (on association)**
Indicates how many objects may be related to an object of the class on the other end

![[image-94.png]]


**Association end name**
Can name both association ends
Used to describe the role that objects play on the association

![[image-95.png]]


**Association & link**
Association -> Structural relationship between classes
Link -> Instance of an association (Between objects)

![[image-96.png|495x294]]


**Association class**
Association that has a set of features of it's own
Both an association & class

![[image-97.png|502x229]]


**Aggregation**
It's a special kind of association, means "part of", "has a" relation.

![[image-98.png|504x219]]


**Generalization**
Generalization describes the relationship between generalized elements and more specific elements
The triangle is on the side of the general class

![[image-99.png]]



# Session 3

## Activity Diagram (Flow)

**Activity & Action**
- Processes information and data, we need fixed steps or the order to execute the processing
- Activity diagrams show such flow of processing
- Activity: Behavior of information systems described by a sequence of actions
- Action: Lower level behavior

**Activity diagram**
- The purpose of activity diagram is to describe one activity
- Shows what kinds of action collaborate to realize the activity
Activity may be:
- A work in the real world
- Process executed on a computer
Similar to flowchart, but the principal difference is that an activity diagram supports parallel behavior

## Basic Notations of activity diagram

**Basic elements**
- Action -> One step of an activity (rounded rectangle)
- Flow -> Flow between actions (Arrows)

![[image-100.png]]

**Two types of flows**
In activity diagram, flows may show one of the two:
- Control flow: (Shows the sequence in which actions are executed)
- Data flow: Flow of data, (shows a sequence in which data are transformed)

**Detailed notation of data flow**
Two types of detailed descriptions

![[image-101.png]]

**Start and end of the flow**
- Initial node: Dot
	![[image-102.png]]
- Final node: Dot with outer circle
	![[image-103.png]]

**Conditional behavior**
Shown by "decision" and "merge" nodes
Both are shows by diamond notations

![[image-104.png]]

- Decision -> One incoming flow, and several guarded outbound flows (Only one outbound flow can be taken according to the guard)
- Merge -> Multiple input flows and single output (Marks the end of the conditional behavior)


**Parallel behavior**
Shown by "Fork" and "Join"
Fork -> Splits flow into multiple concurrent flows
Join -> Synchronizes multiple flows

![[image-105.png]]


**Partition**
Activity diagram can use partitions to describe "who" does what. To do this, we use swim lanes

![[image-106.png]]



## Sequence Diagram (Message interaction)

**Interaction**
A system is composed of multiple elements (objects), and these elements interact with each other to realize the whole behavior of the system

**Sequence diagram**
Shows interactions of objects -> Described by sets of messages passed between objects, ordered chronologically
Message -> Communication from sender to receiver
Shows only **One example** of behavior

![[image-107.png]]


![[image-108.png|351x218]]


**Execution specification**
Shows when the participant is active in the interaction
(Optional)

![[image-109.png]]

**When to use this**
- Good at showing **collaborations among the objects**
- But not good at precise definition of a behavior

## Advanced usage of sequence diagram

**Extensions**
Sometimes we want to describe the communication of objects more generally. We want to show another example by reusing existing sequences. To do this:
- Reuse by *frame*
- Branching by *combined fragment*

**Frame & Combined fragment**
![[image-110.png]]


**Time constraint**
![[image-111.png]]

## Communication Diagram

Interaction diagram, emphasizes links between objects

![[image-112.png]]


**Which one to use?**
Communication diagrams and sequence diagrams both show the same information

If understanding the sequence of messages is important -> Sequence diagram
If understanding the links between objects is important -> Communication diagram


# Session 4

## State Machine Diagram

**Definition and example**
- Static modeling (Modeling of structure)
	- Definition: Class diagram
	- Example: Object diagram
- Dynamic modeling (Modeling of behavior)
	- Definition: ?
	- Example: Sequence diagram, communication diagram

**State Machine diagram**
Describes the behavior of a target entity as a **finite state machine** (Finite states and transitions between them)

**State & Transition**
State -> Condition that an entity meets at runtime, or status that the entity may be in it's timeline
Transition -> Movement from one state to another 

Transition may be triggered by the occurrence of an event just called "Event" formally. An event triggering a transition is called "trigger"
The next state is determined by the combination of the current state and the triggering event

**Notation**

![[image-113.png]]

**Transition label**
Three parts:
- Trigger -> Single event that triggers a potential transition
- Guard -> Bool expression, only when it's true does the transition happen
- Behavior expression -> Behavior that is executed if and when the transition fires

**Special states**
- Initial pseudostate -> Indicates the point where the behavior starts (Required)
  ![[image-114.png]]
- Final state -> Indicates that the behavior described by the state machine is completed (optional)
  ![[image-115.png|44x43]]


**Action, activity, state**
A state may have actions and activities
![[image-116.png]]

Entry action -> Optional behavior that is executed whenever this state is entered regardless the transition it took
Exit action -> Optional behavior that is executed whenever this state is exited, regardless of the transition it will take
Do-Activity -> Optional behavior that is executed while in the state, the execution starts when the state is entered, and stops either by itself, or when the state exits
Internal action -> Optional behavior that is executed when the event shown as a label occurs

**Composite state**
Contains state transitions in of itself
Contains one region or is decomposed into two or more orthogonal regions

![[image-117.png]]

Composite state with one region
![[image-118.png|428x210]]

Composite state with multiple regions
![[image-119.png|433x285]]

**When to use this diagram**
State machine diagrams are good at describing the behavior of an object in several different situations (Define the behavior of an object)
Not very good at describing that involves a number of **objects collaborating**

# Session 5

## Modeling of service ~ Use case

 **Use case**
 Shows how a system is used
 Users of the system use it's function that is observable from outside the system

It describes an interaction between a user and a system
![[image-120.png]]

Set of scenarios tied together by a common user goal
It's a service performed by the system

**Use case diagram**
Shows use cases of a system.
The purpose is **Not** to show all specific functions in detail, but to capture roughly what kind of usages exist

- Subject : A system currently under focus
- Actor : A role that a user plays with respect to the subject (Doesn't have to be human, it can be any outside entity that interacts with the system.)

**Notation**

![[image-121.png]]

- Use case : 
  ![[image-122.png]]

- Actor:
  ![[image-123.png]]
  
**Relationships in use case diagram**
- Association : Shows that the actor carries out the use case
- A use case is related to at least one actor
- A use case may be related to two or more actors
- An actor is related to at least one use case
- An actor may be related to two or more use cases

Three types of relationships between use cases
- Extension: Inserts other use case at the extension point
- Inclusion: Includes other use cases (Used when there are common prats of the behavior of two or more use cases)
- Generalization: Shows generalization of use cases
![[image-124.png]]

Use cases are well known, but the UML doesn't prescribe how to describe the content of the use case

**Templates of use case in this class**
- Actors
- Objective : Brief description of the goal of the use case
- Precondition (If any) : One or more conditions that must be true at the start of the use case
**- Postcondition (If any) : Conditions that is always true at the end of the use case
- Description of the main sequence: Narrative description of the main sequence of the use case.
- Description of alternative sequences (If any): Narrative description of alternative branches off the main sequence
- Remarks

**Use case and actors**
If a use case is related to two or more actors, then al actors must participate to the use case

**When to utilize use case**
- To analyze the essential usage of the system
- To define the services the system performs
- To understand the system in the viewpoint of users


## Common notations of UML diagrams

**Package**
Used to group elements, and provided namespace for the grouped elements
It allow the use of names to refer to package members from other namespaces

![[image-125.png]]

**Stereotype**
Classifies type elements? Whatever that means
![[image-126.png]]

# Session 6

## Requirements Definition

**Requirements definition**
When we want to develop software, we must clarify what we want to build
First step of software development

**Requirement**
Condition or capability needed by a user to solve a problem or reach an objetive
Condition or capability that must be met or pocessed by a system

**Types of requirements**
- *Functional* Requirements 
- *Non-functional* requirements

**Functional requirements**
Requirements related to the services the software must provide.
(How the system should react to particular inputs etc)
Ex: The payment result shall be outputted properly when the order and credit information has been inputted

**Non-functional requirements**
Requirements other than the functional requirements

**NFRs**
Include:
- Quality requirements
- Constraints on design and development

NFRs often conflict each other.

**Stakeholders**
Person, group or organization that is affected by the system or affects the system. May be: A person, a developer, a salesperson, a maintainer, etc

**Quality requirements**
Requirements on software quality
Quality model -> Definitions of set of characteristics and their relationships that provide the basis for quality requirements

*ISO/IEC 25000 series* standardizes various software qualities.

**Quality model of ISO/IEC 25010**
- Quality in use model:
	Composed of five characteristics that is related to the outcome of interaction when a product is used
- Product quality model
	Composed of eight characteristics that relate to the static properties of software and dynamic properties of the computer system

## Requirements definition

**Requirements definition**
Activity to make clear requirements for target software.
Outcome: "Requirements specification" -> Explicit description of the requirements of the software

**Process of requirements definition**
- Requirements elicitation: Elicit hidden requirements of users
- Requirements analysis
- Specifying requirements: Specify requirements and make specifications document
- Requirements verification, validation, and evaluation: Make sure requirements are complete and consistent
- Requirements management: Manage the change of requirements


**Techniques for requirement elicitation**
- Interview
- Questionnaire
- Workshop
- Observation

**Idea making support**
Support making ideas, useful for requirements elicitation and analysis
Techniques:
- Brainstorming
- KJ method
- Mind mapping
- prototyping

**Techniques for requirements analysis**
- Consensus building:
	Unraveling conflicts and building consensus among stakeholders
	Techniques:
	- Delfhi method
	- Analytic Hierarchy process
	- Win-win approach
- Goal analysis:
	- Goal: Intention about how the real world or the system should be


## Goal analysis

**Goal model**
Goal are decomposed into sub goals
Two types of decomposition:
- AND decomposition: All sub goals must be satisfied
- OR decomposition: satisfying one of the sub goal is sufficient

A model describing the hierarchy of goals and dependency/conflicts between goals
Tree structure is used

![[image-127.png]]

**Hard goal and soft goal**
Hard goal -> Achievement can be clearly determined
Soft goal -> Achievement cannot be clearly determined

**Goal oriented requirements analysis**
Method of acquiring, evaluating, consensus building, refining, documenting, analyzing, and evolving requirements by utilizing goals

## Scenario and use case

**Scenario**
Series of events that occur sequentially or in parallel, described by one in time series.
Concrete description of how to use the system
Various scenarios exist for one system
Scenarios are used in the requirements definition

**Scenario description**
Various ways to describe scenario
- Narrative scenario: Using a natural language
- Structured scenario: using bullet points
- Using models:
	- Sequence diagram
	- Activity diagram

**Requirements and use case**
Use case -> Grouped scenarios
Use cases can be used for requirements analysis, specifically in requirements elicitation and requirements specification. Use cases cannot describe non-functional requirements

**Scenario and use case**
Use case -> Middle between scenarios as concrete, straightforward examples and abstract, general requirements specifications

## Requirements specification

**Structure of requirements specification**
Templates of requirements specification (IEEE std. 830) defines a generic structure for a requirements document that must be instantiated for each system.


**Check of requirements specification**
- Requirements verification
  Check that requirements specification satisfies the required properties and that the description or structure is not defective
- Requirements validation
  Check the requirements specification satisfies the stakeholders expectations
- Requirements evaluation
  Evaluate how good the requirements specification is

**Techniques of check**
- Walk through, inspection
- Checklist
- Prototyping

# Session 8

## Software design

Activity to decide software structure, necessary components, their relationship, and properties
Result of the activities we've done before.
Design is based on software requirements, the design must satisfy the requirements
When the design is translated into executable program -> Implementation

**Design activities**
- External design: Decision of external interface
- Internal design: Decision of internal structure (Define internal components and the relationships between them)
- Decision on realization technologies (Hardware, technologies we use)
- Verification of design

**Requirements definition and design**
Requirements definition -> "What"
Design -> "How"
Requirements specification is an input to design

## Module

**Structured programming**
Computers used to have many "goto" statements, until structured programming was introduced, separating control units and making their relations simple. 

**Modularization**
Module -> Composing element of software, building blocks of software
Modularization -> The act of defining modules necessary to construct software and their relationships

**Dilemma of modularization**
If numbers of modules are small, easy to understand, but number of relationship increases, difficult to understand the impact of other modules relative to one
If modules are large, the number of relationship decreases, but each module can be hard to understand and too complex

**Module cohesion and coupling**
Good modularization -> software is constructed so that change is localized, module cohesion and coupling are conceptual metrics of module independence

Module cohesion: Strength of ties within a module (Good)
Module coupling: Ties between modules (Bad)

**Information hiding**
Hide details of the internal structure from the outside, to allow the outside to only use the operations published, and increase independence. Important concept to weaken module coupling
Example: stack
![[image-128.png]]

**Encapsulation**
Separate functions and data of the system from other parts and to define the specification of those functions and data
One of the mechanisms to ensure information hiding

Example: Class
![[image-129.png]]

**Data abstraction**
Focuses on the operation that can be done on data, don't care on how it does it.
Abstract data type is a data type defined as a set of operations
Evolved to the object-oriented programming


## Viewpoint of software design

**Basic viewpoints of design**
How can we find and design modules to realize good modularization?
We can choose basic viewpoints
![[image-130.png]]

**Overview of structured method**
Method to structure software
Focus on functions of software


**Functional decomposition**
Modules in structured methods are to realize functions called as processes. Each function is a transformation of input to output.
In structured method, a system is considered as one function, and decomposed into necessary sub functions -> Functional decomposition

**Data flow diagram**
![[image-131.png]]

![[image-132.png|378x269]]

**Structured chart**
Shows program structure 
In structured method, each process becomes a module, and data flow becomes a relationship between modules

**Data oriented approach**
The structure of information and data is clarified before the design of functionality
The structure of information and data -> Database design

**Design focused on state**
Many embedded systems are reactive systems.
In reactive systems, each response is determined by combination of an event and the internal state
Design focused on state is necessary to design such reactive systems

**Description of state transitions**
- State machine diagrams
	Describe possible states and transitions between them graphically
	easy to follow state transitions
- State transition table
	Describes states in a table
	- row: State name
	- column: event name
	- cell: name of a next state on the top, activities on the transitions on the bottom


# Session 9

## Data Oriented approach

Structure of information and data is clarified before the design of functionality
Structure of information and data -> database design

![[image-133.png]]

**Process of data modeling**
Conceptual design: Real world -> conceptual model
logical design: conceptual model -> logical world

**Entity relationship model**
Basic concepts:
- Entity: Description of a thing or an object existing in the real world
- Relationship: model element specifying a relationship between entities

**Entity relationship diagram**
graphical expression of entity relationship model
Notations of basic elements:
- Entity set: rectangle
- Relationship set: diamond shape
- Attribute: ellipse

example:
![[image-134.png]]


## Object-oriented design

Advanced method of the basic viewpoint of design

**Characteristics of object oriented design**
Object-oriented design is the design method in which a class and an object is a unit of modularization
Characteristics:
- Inheritance
- Polymorphism
- Delegation

**Inheritance**
Good for independence of object 
Localize effect of changes

![[image-135.png]]

**Polymorphism**
Different classes may have the same operation name
Specification of the operation is identical for each class, but each class can implement the operation differently
Useful for achieving a highly independent module structure

Example:
Client has to know that each subclass of figure has a method named "move()"
at run time, the appropriate implementation of move() is executed
If pentagon is added as a subclass of figure, no change to client is needed

![[image-136.png]]

**Delegation**
A class passes a request received to other classes and let them handle it

![[image-137.png]]

**How to find appropriate classes?**
In object-oriented design, a class is the unit of modularization. Focus on the role that classes play in the system

**CRC**
Class-Responsibility-Collaborator
A method for examining class roles using CRC cards
- CRC cards has three areas:
	- Class name
	- responsibilities (methods)
	- Collaborators (another classes that a class interacts wth to fulfill it's responsibilities)

**Design by contract (DBC)**
Method describing the interface of a class in a specification called a contract.
Contract -> Conditions that must be met between the class that provide the method and the class that use the method
Precondition -> Conditions that must be satisfied before calling a method
Postcondition -> Conditions that should be satisfied after calling a method

Contract and class responsibility
Caller of the method must guarantee preconditions
Provider of the methods must guarantee postconditions

**Design guideline**
Principles of achieving the desired module structure
- Single responsibility principle (SRP)
- Open closed principle (OCP)
- Liskov substitution principle 
- Dependency inversion principle (DIP)
- Interface segregation principle (ISP)


**Single Responsibility principle**
A class should only have one reason to change
Changing a class is necessary when the role the class plays changes
One class should not have more than one role

**Open Closed Principle (OCP)**
A class should be able to extend it's behavior without modifying it
"Open" for extension
"Closed" for modification

**Liskov substitution Principle (LSP)**
The derived class must be replaceable with the original class
A subclass "is a" parent class, it must behave as it's parent class

**Dependency Inversion Principle**
Should not depend on concrete classes (implementation), but on the abstractions (interface)
Increase independence through intervening interfaces rather than relying directly on lower layers 

**Interface segregation principle**
A fine grained interface should be provided for each client. 
One interface for a set of methods needed by different clients exposes unnecessary methods and introduces the risk of unnecessary coupling.

**OO design and UML**
Before designing, develop a *use case diagram*. for requirements definition
To consider data structure, we may use *class diagrams* instead of entity relationship diagrams
Using CRC cards or other methods, we find class candidates, and based on these candidates, design the static structure of the software using *class diagrams*.
To consider collaboration between classes in developing class diagram, we may use *sequence diagram*
To design the behavior of the class, we may use *state machine diagrams*, especially for embedded software development

# Verification & Validation

## Verification & Validation

**Checking artifacts**
Artifacts are programs, data, documents, others that are developed in the software development process.

We need to check all these artifacts (Verification & Validation)

**Verification**
Assess whether the artifacts developed during a phase meet the condition and constraints imposed at the start of that phase
"Are we building the product right?"

**Validation**
Confirm that the requirements for the intended use and purpose have been achieved based on objective evidence
"Are we building the right product?"

**V&V**
To check the artifact, both of verification, and validation are needed and important.
We cannot confirm the software is developed completely "right"

**Typical methods**
- Software testing
	System is executed with test data and it's operational behavior is observed
- Review
	Discuss the evaluation of outputs from each phase, and whether we can accept outputs from the previous phase
- Static analysis
	Analyzes artifacts without executing them, using tools
- Formal verification
	Verify software using formal and mathematical methods

## Testing

