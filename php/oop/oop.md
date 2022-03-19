What is OOPs?

    Object Oriented is an approach to software development that models application around real 
    world objects such as employees, cars, bank accounts, etc. A class define the properties 
    and methods of a real world object. An object is an occurrence of a class.

What are the three basic components of object orientation?

    The three basic components of object orientation are;
    - Object oriented analysis – functionality of the system
    - Object oriented designing – architecture of the system
    - Object oriented programming – implementation of the application

What are the three features of OOP?

    The three major principles of OOP are;

    - Encapsulation – this is concerned with hiding the implementation details and only exposing the methods. The main purpose of encapsulation is to;
    Reduce software development complexity – by hiding the implementation details and only exposing the operations, using a class becomes easy.
    Protect the internal state of an object – access to the class variables is via methods such as get and set, this makes the class flexible and easy to maintain.
    The internal implementation of the class can be changed without worrying about breaking the code that uses the class.
    - Inheritance – this is concerned with the relationship between classes. The relationship takes the form of a parent and child. The child uses the methods defined in the parent class. The main purpose of inheritance is;
        - Re-usability – a number of children, can inherit from the same parent. This is very useful when we have to provide common functionality such as adding, updating and deleting data from the database.
    Polymorphism – this is concerned with having a single form but many different implementation ways. The main purpose of polymorphism is;
        - Simplify maintaining applications and making them more extendable.

OOPs Concepts in PHP

    PHP is an object oriented scripting language; it supports all of the above principles. The above principles are achieved via;
    
    Encapsulation – via the use of “get” and “set” methods etc.
    Inheritance – via the use of extends keyword
    Polymorphism – via the use of implements keyword

    Now that we have the basic knowledge of OOP and how it is supported in PHP, let us look at examples that implement the above principles

What is UML?

    Unified Modeling Language UML is a technique used to design and document object oriented systems.
    
    UML produces a number of documents, but we will look at the class diagram which is very important to object oriented php programming.

Class Diagram Example?

![class diagram example](/php/oop/employee_class_diagram.png)

Class Diagram Key

    - The Upper box contains the class name
    - The middle box contains the class variables
    - The lower box contains the class methods
    - The minus (-) sign means private scope
    - The plus (+) sign means public scope
    - The hash (#) sign means protected scope
