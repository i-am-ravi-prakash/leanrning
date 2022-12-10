# Object Oriented Programming

# Java Source File Structure

- In a java program file, there can be n numbers of classes.
- In a java programe file, there can be at most one public class. If we try to make two classes public in the same java program file, we will get compile time error.
- If there is no public class in the java program then we can give any file name to that program but if there exists any public class in the program then compulsory we should give filename as public class name. Let's say there are three classes A, B and C in a java program and class A is public class then java program file name should be A.java.
- When we compile any java program, then for every class present in the program one separate .class file will be generated.
- When we run any class which doesn't have any main method, we will get compile time error saying main method not found in class class_name.

```
class A{
    public static void main(String[] args){
        System.out.println("A class main method");
    }
}

class B{
    public static void main(String[] args){
        System.out.println("B class main method");
    }
}

class C{
    public static void main(String[] args){
        System.out.println("C class main method");
    }
}

class D{

}
```

# Import statement

There are two ways to use any outside class in a java program:

- Fully qualified class name
- Using import statement

Let's say in a java file we have to use ArrayList. We can use any of the below approaches:

**First approach: fully qualified class name**
```
public class Test {
    public static void main(String[] args) {
        java.util.ArrayList arrayList = new java.util.ArrayList();
        
        System.out.println("Compiled successfully");
    }
}
```

**Second approach: using import statement**
```
import java.util.ArrayList;

public class Test {
    public static void main(String[] args) {
        ArrayList arrayList = new ArrayList();
        
        System.out.println("Compiled successfully");
    }
}
```

There are two types of import:

1. Explicit import: When we mention the complete class name in the import statement it's class explicit import.
    e.g. import java.util.ArrayList;
2. Implicit import: When we don't mention the class name explicitly in the import statement.
    e.g. import java.util.*;
    
**Important**:
- We don't need to import classes present in the current working directory or package.
- We don't need to import **java.lang** package. All classes and interfaces present inside java.lang package are available in every java program by default.
- If we are importing any package, then all classes and interfaces present in that package will be available but not sub-package classes or interfaces. If we have to use any sub-package class or interface then we have to write import statement till sub-package level.
- In any java source file, at most one package is allowed.
- In java program, package statement should be the first statement.

# Class Level Modifier

Below modifiers are available for top level classes:
1. public: if a class is public, then it can be accessed from anywhere or any package.
2. default: default classes can be accessed only from the current package, not from other package.
3. abstract
4. final
5. strictfp

Below modifiers are available for inner classes:
1. public
2. default
3. abstract
4. final
5. strictfp
6. private
7. static
8. protected


# Abstraction

Abstraction is a process of hiding the implementation details and showing only functionality to the user.

Another way, it shows only essential things to the user and hides the internal details, for example, sending SMS where you type the text and send the message. You don't know the internal processing about the message delivery. Abstraction lets you focus on what the object does instead of how it does it.

## Abstract Method

- Abstract keyword is applicable only for methods and classes.
- Abstract method has declaration only not the implementation.
- Abstract methods should end with ";" not "{ }".
- Child class inheriting abstract class is responsible for providing abstract method implementation.
- If a class contains at least one abstract method, then the class must be declared as abstract class.

## Abstract Class

- A class which is declared with the abstract keyword is known as an abstract class in Java.
- It can have abstract and non-abstract methods (method with the body).
- It cannot be instantiated.
- It can have constructors and static methods also.
- It can have final methods which will force the subclass not to change the body of the method.
- Abstract class can have zero abstract methods also.


```
abstract class Bike {
    // constructor
    Bike() {
        System.out.println("bike is created");
    }
    
    // abstract method
    abstract void run();
    
    // non-abstract method
    void changeGear() {
        System.out.println("gear changed");
    }
}

class Honda extends Bike {
    
    void run() {
        System.out.println("running safely..");
    }
}

public class TestAbstraction {
    
    public static void main(String args[]) {
        
        Bike obj = new Honda();
        obj.run();
        obj.changeGear();
    }
}
```

Output:
```
bike is created
running safely..
gear changed
```

**NOTE**: If you are extending an abstract class that has an abstract method, you must either provide the implementation of the method or make this class abstract.


# Members Modifiers

It defines the access type of methods or variables i.e. from where we can access these in our Java application. In Java, we have four types of access modifiers:

- **public**: Accessible in all classes in your application.
- **protected**: Accessible within the package in which it is defined and in its child classes.
- **private**: Accessible only within the class in which it is defined.
- **default** (declared/defined without using any modifier): Accessible within the same class or same package within which its class is defined.

## Protected

- Protected members/methods can be accessed only in the same package classes and if we want to access protected members/methods outside of current package, then it will be accessible only in child classes.
- Outside the current package, protected members/methods are accessible only with child class reference not with parent class reference. See the below example to understand this.


```
package pack1;

class Parent{
    protected method(){
        System.out.println("Parent class protected method");
    }
}

package pack2;

public class Test{
    public static void main(String[] args){
        Parent parent = new Parent();
        parent.method();    //  gives compile time error
        
        Test test = new Test();
        test.method();
        
        Parent parent1 = new Test();
        parent1.method();    //  gives compile time error
    }
}
```


**NOTE**: Outside the current package, only child class reference can be used to access protected members/methods.


| Visibility | public | protected | default | private |
| ---------- | ------ | --------- | ------- | ------- |
| Within the same class | Yes| Yes | Yes | Yes |
| Child class of same package | Yes| Yes | Yes | No |
| Non-child class of same package | Yes| Yes | Yes | No |
| Child class of outside package | Yes| Yes | No (only with child reference) | No |
| Non-child class of outside package | Yes| No | No | No |


# Interface

- Every method present inside the interface must be public and abstract (method with no body).
- While providing method implementation, we can't reduce access visibility of methods. It means in the implementation class also we must declare interface method as public only.
- The class implementing the interface must provide method implementation for all the method present inside interface.
- If the class providing method implementation of interface is not able to provide implementation for all methods then that class must be declared abstract.
- In case any abstract class implementing the interface is not able to provide method implementation of all methods then it's responsibility of child class of that abstract class to provide implementation for rest of the methods.


```
interface TestInterface{
    public void m1();
    
    public void m1();
}

public class Test implements TestInterface{
    @Override
    public void m1() {
        
    }

    @Override
    public void m2() {
        
    }
}
```

```
interface Interface{
    public void m1();
    
    public void m1();
}

abstract class ServiceProvider implements TestInterface{
    @Override
    public void m1() {
        
    }
}

class SubServiceProvider extends ServiceProvider{
    @Override
    public void m2() {
        
    }
}
```


# Data Hiding

- External entities can't access the internal application data directly.
- For implementing data hiding, it's recommended to declare variables as private.
- The biggest advantage of data hiding is security


# Encapsulation

It's defined as wrapping the data members (variables) and data behaviours (methods) together as a single unit. It's a mechanism that binds together the code and data it manipulates.
- Technically, in encapsulation methods and variables in a class are hidden from any other classes and can only be access through any member methods of the class in which they are declared.
- In encapsulation, data in a class is hidden from any other classes which is similar to what **data-hiding** does. So, the terms “encapsulation” and “data-hiding” are used interchangeably.
- Encapsulation can be achieved by declaring all the variables in a class as private and writing public methods in the class to set and get the values of the variables.
- Encapsulation = Data hiding + Abstraction


```
class Account{
    private double balance;
    
    public doubleGetbalance(){
        accountValidation();
        return balance;
    }
    
    public void setBalance(double amount){
        accountValidation();
        this.balance = this.balance + amount;
    }
}
```


## Tightly Encapsulated Class

- A class is said to be tightly encapsulated if and only if all the variables inside that class are private.
- If the parent class is not tightly encapsulated then child class also can't be tightly encapsulated class.


```
class Account{
    private double balance;
    private String accountNumber;
    
    public double getBalance(){
        return balance;
    }
}
```


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


# Inheritance

Inheritance is a very important concept in OOP. It allows one class to use features (methods and fields) of another class. 

- It's also called IS-A relationship.
- Its main advantage is code reusability.
- **extends** keyword is used to implement inheritance.

Below are the frequently used terminologies in inheritance:

- **Superclass**: The class whose features are inherited by some other class. It's also called base class or parent class.
- **Subclass**: It's the class which inherits the features of another class. It's also called child class.
- **Reusability**: Inheritance supports the concept of “reusability”, i.e. when we want to create a new class and there is already a class that includes some of the code that we want, we can derive our new class from the existing class. By doing this, we are reusing the fields and methods of the existing class.

**NOTE**: Every class in Java extends java.lang.Object class by default.

- All the members (variables and methods) of parent class are available to child class by default.
- Parent class reference can't be used to call child specific methods or access child class specific variables.
- Child class reference can be used to call both child specific methods as well as parent specific methods and variables.
- Parent class reference can be used to hold child class object but still that parent class reference can't be used to call or access child class members (methods or variables).
- Child class reference can't be used to hold parent class objects.


```
class Parent {
    public void m1(){
        System.out.println("Parent");
    }
}

class Child extends Parent {
    public void m2(){
        System.out.println("Parent");
    }
}

class Test {
    public static void main(String[] args){
        Parent p = new Parent();
        p.m1();
        p.m2();    // compile time error because parent reference can't be used to call child specific methods
        
        Child c = new Child();
        c.m1();
        c.m2();
        
        Parent p = new Child();
        p.m1();
        p.m2();    // compile time error because although parent class reference can be used to 
                   // hold child objects but still that parent reference can be used to call child specific methods
        
        Child c = new Parent();    // compile time error: Incompatible type. Parent can't be connverted to Child
                                   // because child class reference can never be used to hold parent class objects
    }
}
```


**Type of inheritance**

1. **Single inheritance**: A single class inheriting a single class.

```
class A {
    // TO-DO
}

class B extends A {
    // TO-DO
}
```

2. **Multiple inheritance**: A single class extending more that one class at a time.

```
class A {
    // TO-Do
}

class B {
    // TO-DO
}

class C extends A, B {
    // TO-DO
}
```

**NOTE**: Multiple inheritance is not supported by Java.

3. **Multi-level inheritance**: When there is a heirarchy of inheritance, it's called multi-level inheritance.

```
class A {
    // TO-DO
}

class B extends A {
    // TO-DO
}

class C extends B {
    // TO-DO
}
```

4. **Heirarchical inheritance**: Multiple classes extending the features of a single class.

```
class A {
    // TO-DO
}

class B extends A {
    // TO-DO
}

class C extends A {
    // TO-DO
}

class D extends A {
    // TO-DO
}
```


# static keyword

The static keyword in Java is used for memory management mainly. We can apply static keyword with variables, methods, blocks and nested classes. The static keyword belongs to the class than an instance of the class.

The static can be:

1. variables
2. methods
3. blocks
4. nested class


## static variables

- If we declare any variable as static, it's known as static variable.
- Static variables get memory only once in the class area at the time of class loading.
- Static variales can be used to refer the common property of all objects. e.g. Company name of all employess of a company


## static methods

- If you apply static keyword with any method, it is known as static method.
- A static method belongs to the class rather than the object of a class.
- A static method can be invoked without the need for creating an instance of a class.
- A static method can access static data member and can change the value of it.

In addition to the above points, there are certain limitations to static methods which are as follows:

- Static methods cannot use non-static members or call non-static methods directly.
- **this** and **super** cannot be used in static context.


**Why is the Java main method static?**
- Object is not required to call any static method. If the main method is not static then everytime JVM needs to create an object to call main method and it'll lead to the problem of extra memory allocation.


## static block

- It is used to initialize the static data member.
- It is executed before the **main** method at the time of classloading.

```
class Test {
    static {
        System.out.println("Static block is invoked");
    }
    
    public static void main(String[] args) {
        System.out.println("main method is invoked");
    }
}
```

Output:
```
Static block is invoked
main method is invoked
```


# this keyword

**this** is a reference variable which refers to the current object.

## Usage of Java this keyword

1. **this** can be used to refer current class instance variable.

```
class Users {
    private String name;
    private int age;
    
    public Users(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public void display() {
        System.out.println("Name: " + name + " Age: " + age);
    }
}

class Test {
    public static void main(String[] args) {
        Student student1 = new Student("Ravi", 24);
        Student student2 = new Student("Suraj", 19);
        
        student1.display();
        student2.display();
    }
}
```

Output:
```
Name: Ravi Age: 24
Name: Suraj Age: 19
```

2. **this** can be used to invoke the current class method

You may invoke the method of the current class by using the **this** keyword. If you don't use the this keyword, compiler automatically adds this keyword while invoking the method.

```
public class Test {
    public static void main(String[] args) {
        Test test = new Test();
        test.m();
    }
    
    public void m() {
        System.out.println("m() method invoked");
        this.n();
    }
    
    public void n() {
        System.out.println("n() method invoked");
    }
}
```

Output:
```
m() method invoked
n() method invoked
```

3. **this()** can be used to invoke current class parameter

```
public class Test {
    
    public static void main(String[] args) {
        App obj = new App(10);
    }
}


class App {
    
    App() {
        System.out.println("Constructor invoked");
    }
    
    App(int _num) {
        this();
        System.out.println(_num);
    }
}
```

Output:
```
Constructor invoked
10
```

**Real usage of this() constructor call**

The this() constructor call should be used to reuse the constructor from the constructor. It maintains the chain between the constructors i.e. it is used for constructor chaining.

```
public class Test {
    
    public static void main(String[] args) {
        Student s1 = new Student(111, "ankit", "java");
        Student s2 = new Student(112, "sumit", "java", 6000f);
        s1.display();
        s2.display();
    }
}


class Student {
    
    private int rollno;
    private String name;
    private String course;
    private float fee;
    
    Student(int rollno, String name, String course) {
        this.rollno = rollno;
        this.name = name;
        this.course = course;
    }
    
    Student(int rollno, String name, String course, float fee) {
        this(rollno, name, course);// reusing constructor
        this.fee = fee;
    }
    
    void display() {
        System.out.println(rollno + " " + name + " " + course + " " + fee);
    }
}
```

Output:
```
111 ankit java 0.0
112 sumit java 6000.0
```

**NOTE**: Call to **this()** must be the first statement in constructor.

4. **this** can be passed as an arguement in the method

```
public class Test {
    
    public static void main(String[] args) {
        Test test = new Test();
        test.method1();
    }
    
    public void method1() {
        method2(this);
    }
    
    public void method2(Test obj) {
        System.out.println("Method is invoked");
    }
}
```

Output:
```
Method is invoked
```

5. **this** can be passed as argument in the constructor call

6. **this** keyword can be used to return current class instance

