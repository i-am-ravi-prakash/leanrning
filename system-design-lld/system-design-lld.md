# Low Level System Design

## Introduction to Objects

**What is an Object?**

Generally, an object is anything that occupies space in the universe.

For example: The room you are sitting in contains several objects. The laptop you are working on is an object, the table you have kept your laptop on is an object. The chair on which you are sitting is also an object.

**Classes & Objects**

A class can be defined as a blueprint or description of objects that can be created from it. We have also observed the following properties of a class:

- NOT REAL: Class is not a REAL THING; it’s just a concept, actually the objects created from a class are real.
- A single class can be used to create any number of instances or objects.


## Software Development Process

**Problem Solving Process**

Let us discuss the steps that are followed in general to solve any problem.

- First, we focus on the requirements of the problem.
- Next, on the basis of understanding of requirements, we develop a design or prototype of the solution.
- Finally, we convert the prototype to the real implementation and deliver it to the customer.

<img width="542" alt="Screenshot 2023-01-01 at 9 00 01 PM" src="https://user-images.githubusercontent.com/84272788/210176240-342461d9-0ac1-4167-807b-1d4ad2f51227.png">

**Software Development Process**

We saw the general problem-solving process which consist of 4 steps:
- Requirement Analysis
- Design
- Implementation
- Delivery


The same set of steps is followed to develop any software. The only difference is that here implementation is the coding phase.

<img width="451" alt="Screenshot 2023-01-01 at 9 02 56 PM" src="https://user-images.githubusercontent.com/84272788/210176323-eab9aa55-7cd0-475d-b1fb-747c7509efa8.png">

## Introduction to UML (Unified Modelling Language)

**Why UML?**

Suppose there are two designers Alice and Bob creating designs of different parts of the software.
Now if Alice follows some conventions and Bob follows other conventions, then it becomes very difficult for Tom, the developer, to code these designs correctly.

There should be some standard that must be followed by Alice and Bob, so that their designs are uniform, and seems unambiguous to TOM.

Here comes to the rescue, the UML i.e., Unified Modelling Language.

The Unified Modeling Language (UML) is a standard graphical language for modeling object-oriented software.
It was developed by three software engineers, James Rumbaugh, Grady Booch, and Ivar Jacobson.

**UML Diagrams**

As UML is a graphical language, it supports two types of diagrams that can be classified as Structural and Behavioral.

The structural Diagrams are used to create a static model of the software. That is, it gives an idea about what all components build up the system.

The Behavioral Diagrams are used to create a dynamic model of the software. It tells how the different components or modules interact with each other.

<img width="556" alt="Screenshot 2023-01-01 at 10 42 42 PM" src="https://user-images.githubusercontent.com/84272788/210179256-05f6e849-7f32-4fcd-bc3d-fef1e8aeffbd.png">

## Class Diagram and Object Diagram

**Class Diagrams**

In the real world, if you observe, you can see that all the objects have some properties as well as functionalities.

For example: a fan has properties such as color, type, no_of_blades, and made. With these attributes it also has some functionalities such as start(), stop(), increase_speed(), decrease_speed().

**A class diagram in the Unified Modeling Language (UML) is a type of structural diagram that describes the structure of a system by showing the System's Classes, their Attributes, Operations (or methods), and the relationships among objects.**

In a class diagram a class is represented with the help of a rectangular box having three partitions:
- The first partition contains the class name.
- The second partition contains all the attributes of the class.
- The third partition contains all the functionalities of the class.


<img width="566" alt="Screenshot 2023-01-02 at 9 14 29 AM" src="https://user-images.githubusercontent.com/84272788/210193656-017e68a5-d257-4f1d-851e-67facd4f5dfe.png">


**Relationships**

The connection between the two classes in a class diagram is called a Relationship. A class may be involved in one or more relationships with other classes.

<img width="547" alt="Screenshot 2023-01-03 at 9 22 59 PM" src="https://user-images.githubusercontent.com/84272788/210392932-8b57b39c-b0f5-4122-909e-d817272a5ad2.png">

In the class diagram, the classes can be related to each other through Association, Generalization, Aggregation, or Composition.

<img width="568" alt="Screenshot 2023-01-03 at 9 28 50 PM" src="https://user-images.githubusercontent.com/84272788/210393940-37eeb795-64f9-4513-bbd9-4968f95035cb.png">


**Associations**

In class diagrams, we can connect two classes with a solid line. This relationship is known as Association and shows that one class is associated with other classes.

<img width="506" alt="Screenshot 2023-01-03 at 9 32 37 PM" src="https://user-images.githubusercontent.com/84272788/210394667-3afd05d9-2892-4751-9495-b24f212455f8.png">

**Multiplicity**

Multiplicity of Association tells us: how many objects of each class can take part in the relationship.

**Aggregation**

Let's understand Aggregation with the help of shown class diagram:

Here we can see that two classes are connected with a solid line having an unfilled diamond at one end.

<img width="546" alt="Screenshot 2023-01-03 at 9 47 01 PM" src="https://user-images.githubusercontent.com/84272788/210397005-97aed4af-ee74-4caf-b651-f5ba974ce25f.png">

We can read this as Bank has a part locker. Or inversely we can say locker is a part of Bank

This relationship is like a **whole-part relationship**, where class at the diamond end is the WHOLE thing or the Aggregate, whereas the class at the other end is a PART of the WHOLE thing.

So whenever we need to represent any class that is a part of another class, we can use aggregation.
Another example may be:

<img width="570" alt="Screenshot 2023-01-03 at 9 49 22 PM" src="https://user-images.githubusercontent.com/84272788/210397446-0c8f6785-8327-4344-9157-9b26f1e4282a.png">

**Composition**

In the case of aggregation, we saw that two classes had a part-whole relationship i.e. one class was part of another class.

Let’s see the previous example of bank and locker, here the locker is a part of the bank, but a locker has its own existence, i.e. locker can exist even if there is no bank.

So, we can summarize that in the case of aggregation, the part can exist without the whole class also.

Let's take another example.

Just think of any bank account, the account always has a transaction history associated with it. So if we consider Bank account and transaction history as two different entities, we can say that transaction history is part of the Bank account.

But if the bank account doesn’t exist, there will be no transaction history so this can not be represented with aggregation.

Actually this is an example of composition. The composition is a stronger form of aggregation in which if the aggregate is destroyed, the parts are destroyed as well. We represent this with the help of a filled diamond as shown.

<img width="626" alt="Screenshot 2023-01-03 at 9 58 24 PM" src="https://user-images.githubusercontent.com/84272788/210398958-f64402a9-724a-4888-8e1f-914f7022e2ab.png">
