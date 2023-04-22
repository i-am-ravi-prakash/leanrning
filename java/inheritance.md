# Inheritance introduction

Inheritance is an object oriented concept by which any class can inherits all the properties and behaviors of another class.

- It's also called IS-A relationship.
- Its main advantage is code reusability.
- **extends** keyword is used to implement iheritance in Java.

Below are the frequently used terminologies in inheritance:

- **Super class**: The class from which any class inherits the properties and behaviors. It's also called parent class.
- **Sub class**: The class which inherits the properties and behaviors from another class. It's also called child class.
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

## Types of inheritance in Java

1. **Single Inheritance**: A single class inheriting a single class.

```
class A {
    // TO-DO
}

class B extends A {
    // TO-DO
}
```

2. **Multiple Inheritance**: A single class inherating more than one class at a time.

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

**NOTE**: Multiple inheritance is not supported in Java wrt class but it's allowed wrt interface.

3. **Heirarchical inheritance**: When there is a heirarchy of inheritance.

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

4. **Multi-level inheritance**: Multiple classes extending the features of a single class.

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

5. **Cyclic inheritance**: When there is a cycle in inheritance, it's called cyclic inheritance. Cyclic inheritance can occur in the following two ways:

```
class A extends A{
    // TO-DO
}
```

```
class A extends B{
    // TO-DO
}

class B extends A{
    // TO-DO
}
```

**NOTE:** Cyclic inheritance is not allowed in Java or any programming language.


## Important points to 
