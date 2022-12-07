# SOLID design is an acronym for the following five principles:

- **Single** Responsibility Principle.
- **Open-Closed** Principle.
- **Liskov** Substitution Principle.
- **Interface** Segregation Principle.
- **Dependency** Inversion Principle.

## Why to use design patterns?

The aim of **Design Patterns** is to make software design more understandable and maintainable.

> Bad programmers worry about the code, good programmers worry about data structure and their relationship.

# SOLID Principle

## Single Responsibility Principle

- Every single software entity (class or method) should have only a single reason to change.
- If a single class (or method) does multiple operations, then it's advisable to separate into distinct classes (or methods).
- It can be done easily using **Interface**.
- If there are two reasons to change a given class then it's a sign of violation of **Single Responsibility** principle.
- Each class or method handles just a single responsibility.
- This is how we can achieve loosely coupled software components.

| Tight coupling | Loose coupling |
| -------------- | -------------- |
| Classes are highly dependent on each other | Classes are independent of each other |
| This typically happend when classes have too many responsibilities | Interfaces (or Abstractions) can be used to achieve this feature using SOLID principles |



# Singleton Design Pattern

- Singleton pattern is a creational design pattern.
- It ensures that the **class has only one instance** while providing a global access point to that instance.
- It involves a single class.

We're going to create a Database class. Database class have its constructor as private and have a static instance of itself.

Database class provides a static method to get its static instance to outside world. Application, our demo class will use Database class to get a Database object.

```
class Database{
  private static Database instance;
  
  private Database(){
    
  }
  
  public static DatabaseConnector getInstance() {
        if (instance == null) {
            instance = new DatabaseConnector();
        }
        return instance;
   }
  
  public void connect() {
        System.out.println("Connecting to the database...");
    }
    
  public void disconnect() {
      System.out.println("Disconnecting...");
  }
}

class Application{
  public static void main(String[] args) {
        DatabaseConnector.getInstance().connect();
        DatabaseConnector.getInstance().disconnect();
    }
}
```


# Factory Design Pattern
