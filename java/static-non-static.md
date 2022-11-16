All static fields (variables or methods) are accessible at class level whereas non-static fields are accessible at object level. We don't need to create objects to access static fields but to access non-static fields we need to create objects.

static fields are common for the entire class. Let's take an example of banking system. Balance or loan amount may be different for different users (objects) but the interest rates are same for alll the users. In this example, interest rate is static variable for this banking system.

## static blocks

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
**Output**:
Static Block 1
Static Block 2
Hello World
```
