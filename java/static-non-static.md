# Static Members


All static fields (variables or methods) are accessible at class level whereas non-static fields are accessible at object level. We don't need to create objects to access static fields but to access non-static fields we need to create objects.

static fields are common for the entire class. Let's take an example of banking system. Balance or loan amount may be different for different users (objects) but the interest rates are same for alll the users. In this example, interest rate is static variable for this banking system.

## Static blocks

We can exeucte some of the codes or block of codes just after class loading i.e. before **main()** method execution. We can put those lines of codes in a static block like below:

```
static{
  // write your code here
}
```

**NOTE**: static block is executed before main() method execution.

```
public class TestApp {
    
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
    
    static {
        System.out.println("Static Block");
    }
}
```

```
Output: 
Static Block
Hello World
```

We can create multiple static blocks in our code. The order of execution in case of multiple static blocks will depend on the order of static blocks in the code. Check the below code and output:

```
public class TestApp {
    
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
    
    static {
        System.out.println("Static Block 1");
    }
    static {
        System.out.println("Static Block 2");
    }
}
```

```
Output:
Static Block 1
Static Block 2
Hello World
```


# Non-Static Members


Below are the non-static members:

- Non static variables
- Non static blocks
- Non static user defined methods
- Constructors

**NOTE**: We need to create objects to access non-static members in the class.

Below is the exmaple code for non static members:

```
public class NonStaticMembersDemo {
    int num;
    
    NonStaticMembersDemo() {
        System.out.println("Inside constructor");
    }
    
    public static void main(String[] args) {
        System.out.println("Inside main method");
        new NonStaticMembersDemo();
    }
    
    {
        System.out.println("Inside non static block");
    }
}
```

```
Output:
Inside main method
Inside non static block
Inside constructor
```

**NOTE**: 
- Non static blocks are executed before constructor.
- The key difference between static and non static blocks is that static block is executed only once when class is loaded, but non static blocks are executed as many times we create an object of the class.
- If there is no user defined constructor, then Java compiler provides a default constructor.
- Constructors don't have any return type. They return the memory addrress of the object created.


### Static vs Non Static

| Static Members | Non Static Members|
| -------------- | ----------------- |
| Static members belong to class. | Non static members belong to objects. |
| Accessed using class name. | Accessed using object name. |
| Static blocks are executed during class loading. | Non static blocks are executed during object creation. |
| Memory is allocated and variables are initialized during class loading. | Memory is allocated and variables are initialized during object creation. |
