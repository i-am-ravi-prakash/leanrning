# Object Oriented Programming

Object Oriented Programming is a paradigm where we use objects to represent or write complex softwares. It aims to implement real world entities like hiding, inheritance, polymorphism, etc.


### Access Modifier

It defines the access type of methods or variables i.e. from where we can access these in our Java application. In Java, we have four types of access modifiers:

- **public**: Accessible in all classes in your application.
- **protected**: Accessible within the package in which it is defined and in its subclass(es) (including subclasses declared outside the package).
- **private**: Accessible only within the class in which it is defined.
- **default** (declared/defined without using any modifier): Accessible within the same class and package within which its class is defined.


### Message Passing

Objects communicate with each other by sending or receiving information to each other. A message for an object is a request for execution of a procedure and therefore will invoke a function in the receiving object that generates the desired results.

Message passing involves specifying the name of the object, the name of the function and the information to be sent.

![Object-Oriented-Programming-Concepts](https://user-images.githubusercontent.com/84272788/201808279-bad17345-c1d1-4de9-b82a-5ef4a1055e15.jpg)


## Class

A class in Java is a blueprint or prototype from which we create objects. It represnets set of properties or behaviours which are common to all objects of one type. Using classes, we can create multiple objects with same behaviours instead of witing their code multiple times. In general, class declarations can include these components in order:

- Modifiers: A class can be public or have default access.
- Class name: The class name should begin with the initial letter capitalized by convention.
- Superclass (if any): The name of the class’s parent (superclass), if any, preceded by the keyword **extends**. A class can only extend (subclass) one parent.
- Interfaces (if any): A comma-separated list of interfaces implemented by the class, if any, preceded by the keyword **implements**. A class can implement more than one interface.
- Body: The class body is surrounded by braces, { }.


## Object

An object is a basic unit of Object-Oriented Programming that represents real-life entities. A typical Java program creates many objects, which as you know, interact by invoking methods. The objects are what perform your code, they are the part of your code visible to the viewer/user. An object mainly consists of:

- **State**: It's represented by the attributes of an objects. It also reflects properties of an object.
- **Behaviour**: It's represented by the methods of an object. It also reflects response of an object to another.
- **Identity**: It'a unique name given to any object which enables it to interact with other objects.


## Method

It's a collection of statements or instructions that performs some specific tasks and returns the response to the caller. A method can perform some specific task even without returning anything (return type void). Methods allow us to reuse the code without retyping it, which is why they are considered time savers. In Java, every method must be part of some class, which is different from languages like C, C++, and Python.


Let us now discuss the 4 pillars of OOPs:

## Abstraction

Abstraction is the property by virtue of which only essential functionalities are shown to the users hiding the implementations. The trivial or non-essential units are not shown to the users.

Data abstraction may also be defined as the process of identifying only the required characteristics of an object, ignoring the irrelevant details. In Java, abstraction is achieved by using abstract class and interfaces. Lets see the below example to understand abstraction process:

Let's say I am withdrawing money from ATM. After I inserted the card in the machine one popup will display on the screen asking to select any option. I will select Withdraw Money option and put the required details like amount to be withdrawn and my ATM pin. After processing all the details, ATM will give me the money.

If we observe this example carefully, we can see that ATM machine is only displaying the functionality. We don't know what was the internal internal implementation of withdrawing the money from ATM.


## Encapsulation

It's defined as wrapping the data and code together as a single unit. It's a mechanism that binds together the code and data it manipulates.
- Technically, in encapsulation data and variables in a class are hidden from any other classes and can only be access through any member methods of the class in which they are declared.
- In encapsulation, data in a class is hidden from any other classes which is similar to what **data-hiding** does. So, the terms “encapsulation” and “data-hiding” are used interchangeably.
- Encapsulation can be achieved by declaring all the variables in a class as private and writing public methods in the class to set and get the values of the variables.
