# Spring

Spring is a depenedency injection framaework to make java applications loosely coupled. Spring framework make development of Java EE applications easy.

Dependency Injection is a kind of design pattern which is used to make loosely coupled Java applications. Let's say there is one service BalanceEnquiry. This BalanceEnquiry service will depend on User and Wallet service/class to fetch balance for any user.

```
class User {
  
  public void method1(){
    // TO-DO
  }
}
  
class Wallet {

  public void method1(){
    // TO-DO
  }
  
  public void method2(){
    // TO-DO
  }
  
}

public class BalanceEnquiry {
  User user = new User();
  Wallet wallet = new Wallet();
  
  user.method1();
  wallet.method2();
}
```

In this example, BalanceEnquiry service is dependent on User and Wallet class/service. Here, we are creating object of User and Wallet class manually. In case of Spring framework we don't need to bother about creating objects of different required classes. Spring creates required objects and injects all the required dependency. This whole process of injecting the dependency is called Inversion of Control (IoC).


Below is an example to show the flow of how to create objects of different classes and use it in the required classes to complete the task.

<img width="585" alt="Screenshot 2022-11-23 at 12 11 45 AM" src="https://user-images.githubusercontent.com/84272788/203395533-c85a9f42-86fa-4c74-9bdb-fc81973ff907.png">


Below is an illustration of how Spring handle objects creation and injecting it into required class.

<img width="702" alt="Screenshot 2022-11-23 at 12 13 00 AM" src="https://user-images.githubusercontent.com/84272788/203395735-c8cd24f3-11d2-4ff4-b020-a508b092e636.png">


## Spring Modules

<img width="588" alt="Screenshot 2022-11-23 at 12 26 06 AM" src="https://user-images.githubusercontent.com/84272788/203398170-70f0cadb-a675-41a9-bb88-2a4a1b381952.png">


## Spring IoC Container

Sprinng IoC container is a predefined program which is respondible for object creation and injecting them in the required object.

ApplicationContext is an interface which represents IoC container. There are multiple containers provided by Spring. Some of them are as follows:

- **AnnotationConfigApplicationContext**: It accepts classes annotated with @Configuration, @Component, and JSR-330 compliant classes.
  ```
  ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class, AppConfig1.class);
  ```
- **AnnotationConfigWebApplicationContext**
- **XmlWebApplicationContext**
- **FileSystemXmlApplicationContext**
- **ClassPathXmlApplicationContext**


Dependency injection can be done in two ways:

1. Setter injection
2. Constructor injection


## Setter Injection

For this type of injection, IoC uses setter methods to inject objects (dependency). Below is an exapmle to illustrate the same:

```
class Address {
    String street;
    String city;
    String state;
    String country;
    
    setStreet(String _street);
    setCity(String _city);
    setState(String _state);
    setCountry(String _country);
}

class Student {
    int id;
    String name;
    Address address;
    
    setId(int _id);
    setName(String _name);
    setAddress(Adress _address);
}
```

## Constructor Injection

Dependency injection can also be done through constructors like below:

```
class Address {
    String street;
    String city;
    String state;
    String country;
    
    Address(String _street, String _city, String _state, String _country){
        // TO-DO
    }
}

class Student {
    int id;
    String name;
    Address address;
    
    Student(int _id, String _name, Address _address){
        // TO-DO
    }
}
```

**NOTE**: Configuration file is an XML file where we declare our beans and dependencies.


### Data Types (Dependencies)

1. Primitive Data Types
  - byte, short, int long, char, float, double, boolean
2. Collections Types
  - List, Map, Set, Properties
3. Reference Type
  - Other class object
