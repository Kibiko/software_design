# Software Design Methodologies

## Contents

- [Design Strategies](#design-strategies)
    * [Structured Design](#structured-design)
    * [Function Oriented Design](#function-oriented-design)
    * [Object Oriented Design](#object-oriented-design)
- [Tasks](#task)

## Design Strategies

There are three principle design strategies used in software engineering:

- Structured design
- Function oriented design
- Object oriented design

## Structured Design

- Problem is broken down into several well-organised elements of solution
- Concerned with solution design and how the problem is being solved
- Divide and conquer strategy - each small problem is individually solved until whole problem is solved
- These are done through solution modules
- These modules are arranged in a hierachy that communicate with each other

**Rules for communication among multiple modules**

- **Cohesion** - grouping of all functionally related elements to fufill a single, well-defined purpose
- **Coupling** - communication between different modules, where high coupling means modules are closely connected and changes in one module may affect others

A good structured design has low coupling arrangements and high cohesion.

## Function Oriented Design

- Focuses on the function of the program
- The system is comprised of many smaller sub-systems known as functions
- Functions can change the state of the program 
- Works well when system state does not matter and the program works on the input rather than state
- Therefore it uses immutable data and follows a declarative programming model which allows for parallel programming
- This is used when there are a few things with more operations therefore good for fixed set of things and new operations needed
- Top Down Design

**Design Process** -
* How data flows in the system 
* Data Flow Diagram depicts how functions changes data and state of entire system
* System is broken down into smaller modules known as functions
* Each function is described at large

## Object Oriented Design

- Design is focused on the entities and their characteristics instead of functions involved in the software system
- Good for fixed set of operations and new objects are added instead
- Bottom Up Design

**OOP Concepts**

- Objects - entities of the system e.g. person, bank, company, customer. Objects have properties and methods
- Classes - blueprint for an object. Objects are instances of a class
- Encapsulation - properties and methods are bundled together and also restricts access of the data and methods *(information hiding)*
- Inheritance - enables stacking in hierarchical manner with subclasses able to import properties and methods
- Polymorphism - methods can perform similar tasks but vary in arguments

**Design Process**
* Solution design is created from requirements through a UML
* Objets are idenfitifed and grouped in classes based on similar properties
* Class hierarchy and relation is defined
* Application framework is defined

## Software Design Approaches

### Top Down Design

- This takes the whole system and decomposes it to many sub-systems. This is further decomposed until the lowest level of system is achieved in a hierarchy. 
- When all components are composed, the whole system comes into play
- More suitable for undefined systems
- C, Fortran
- Has high ratio of redundancy as size of project increases

### Bottom Up Design

- Starts with most basic components and proceeds with composing higher level components
- More suitable when a system needs to be created from some existing system
- Minimum data redundancy and focuses of re-usability
- C++, Java

## Task

In this exercise you will be required to research the design strategies listed above and answer some questions about them. Your answers should be in a markdown (`.md`) file and uploaded to GitHub, then the link submitted using the lab submission form. There is no MVP/extension split for this task - you should attempt to answer every question. You can collaborate with others in the cohort on the research part of the task but everyone should submit their own answers.


***1. What do we mean by **coupling** and **cohesion** when discussing structured design?***

Coupling is the level at which different classes/modules in a system interact with each other. Cohesion on the other hand is how connected the functions or elements are in a class/module. 

Low coupling means that changing a class/module would have little to no affect on other classes/modules. Highly coupled classes makes it difficult to maintain code as more would have to be changed. Low coupling is key.

Low cohesion would mean that the class/module does a large variety of actions and has a lot of functions while high cohesion means that the class/module is focused on what it should be doing. High cohesion is the aim.

***2. What is the difference between **top-down** and **bottom-up** design? Which best describes a function oriented design?***

A top down design breaks down the problem into smaller sub problems until a base is reached. Organised in a hierarchy, the coding only starts when the entire design is made and the solution as a whole is complete when all parts are completed. This design is best for systems which require a lot of functions or methods.

Bottom up design starts from the smallest parts and then pieces them together to build the entire system. This is preferred when there are many objects to track and smaller amount of methods so that there is a lot more reusability in methods and functions.

In Function Oriented Design, the aim is to focus on the function of the program and tries to avoid changing state of the program and mutable data. The important parts of function oriented is the input and how the data flows through the program. A Top Down design describes Function Oriented Design the best.

***3. In which design methodology would a **class diagram** be most useful?***

Class digrams would be most useful in Object Oriented Design as it is a useful way of keeping track of the classes, objects, methods and how they all connect to one another. Changes to classes or interfaces during the implementation would also be easier to monitor on a class diagram. 

***4. What are the **four pillars of object oriented programming**? Give a single-sentence description of each.***

- **Abstraction** - Hiding away the implementation details of something to keep things simple and showing important parts only. E.g. Creating an abstract class for all cars while subclasses focuses on how each vehicle brand and how they vary.
- **Encapsulation** - Limiting pieces of your code that can be directly accessed by making data and/or implementation private and only passing values. E.g. getters and setters rather than directly accessing and modifying properties
- **Inheritance** - Allows classes to gain properties and methods of another class. E.g. Subclasses of vehicle brands inherits engine property and methods associated with starting and stopping an engine from parent class Car. 
- **Polymorphism** -

***5. What is the **strategy pattern**? How would its implementation differ between a functional and object oriented system?***

![strategy pattern](/images/strategy_pattern.png)

A way to vary a family of encapsulated algorithms that enable a class behaviour or it's algorithm to change during run time. The components include,

- Algorithm - a method or function
- Strategy - common interface with methods that are implemented by other classes
- Context - a run time environment or parent process which uses the Strategy interface given a certain condition

A good example on how the implementations may differ is a calculator for a coffee shop that depends on a walk-in customer or online,

* In OOD, we would have an interface that holds a method of getTotalPrice and then the classes that represent a walk in customer or online customer that implements the method will have it's own way of calculating it. In the Context we could implement a switch case for whichever customer has bought the coffee and then use the getTotalPrice method which calls the algorithm based on what class the new customer has been initilised as

* In Function Oriented Design, we could implement this final pricing through defining a function which takes in other functions as a parameter. Implementation of the smaller functions will be needed first. In our example, a function for walk in pricing and online pricing are the base. Then we define the getTotalPrice function that takes in the pricing strategy and customer type for both walk in and online. Lastly we can write the switch case to define the parameters that the getTotalPrice function takes in before finally calling the function at the end to get the price. 

***6. Imagine you're creating a new online payment system. In order to gain maximum market share it can't be tied to a particular sector - it needs to work just as well when ordering a takeaway as when buying a new coat. Which design methodology would you suggest following? Give some justification for your decision.***

I would implement the Object Oriented Design for this new online payment system. Since the system is not tied to a particular sector and should work just as well as ordering a takeaway, there would be a lot of common methods that both situations can use. These may include checking stock, pricing items, processing an order online, saving delivery info etc. This would make OOD much more suitable than FOD since in FOD there are a lot of tightly coupled modules if we wish to change the online payment system for a different sector. In OOD we can focus on common methods in interfaces and can more easily switch classes that implement them.