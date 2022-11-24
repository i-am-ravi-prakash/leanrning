# instanceof operator

The java **instanceof** operator is used to test whether the object is an instance of the specified type (class or subclass or interface). The instanceof in java is also known as type comparison operator because it compares the instance with type. It returns either true or false.

```
public class InstanceOfTest {
    public static void main(String[] args) {
        InstanceOfTest instanceOfTest = new InstanceOfTest();
        System.out.print(instanceOfTest instanceof InstanceOfTest);
    }
}
```

Output:
```
true
```

An object of subclass type is also a type of parent class. For example, if InstanceOfTest class extends ParentInstanceOfTest then object of ParentInstanceOfTest can be referred by either ParentInstanceOfTest or ParentParentInstanceOfTest class.

```
class ParentInstanceOfTest{
    
}

public class InstanceOfTest extends ParentInstanceOfTest{
    public static void main(String[] args) {
        InstanceOfTest instanceOfTest = new InstanceOfTest();
        System.out.print(instanceOfTest instanceof ParentInstanceOfTest);
    }
}
```

Output:
```
true
```

If we apply instanceof operator with a variable that have null value, it returns false.

```
public class InstanceOfTest{
    public static void main(String[] args) {
        InstanceOfTest instanceOfTest = null;
        System.out.print(instanceOfTest instanceof InstanceOfTest);
    }
}
```

Output:
```
false
```

When Subclass type refers to the object of Parent class, it is known as downcasting. If we perform it directly, compiler gives Compilation error. If you perform it by typecasting, ClassCastException is thrown at runtime.

```
public class InstanceOfTest extends ParentInstanceOfTest{
    public static void main(String[] args) {
        InstanceOfTest instanceOfTest = new ParentInstanceOfTest(); // compile time error
        InstanceOfTest instanceOfTest = (InstanceOfTest) new ParentInstanceOfTest(); // compiled successfuly but ClassCastException is thrown at runtime
        System.out.print(instanceOfTest instanceof InstanceOfTest);
    }
}
```


# Copy Constructor in Java

In object-oriented programming, object copying is creating a copy of an existing object. The resulting object is called an object copy or simply copy of the original object. There are several ways to copy an object, most commonly used is **copy constructor**.

```
public class Complex {
    private double re;
    private double im;
    
    public Complex(double _re, double _im) {
        this.re = _re;
        this.im = _im;
    }
    
    public Complex(Complex _complex) {
        re = _complex.re;
        im = _complex.im;
    }
    
    @Override
    public String toString() {
        return "(" + re + " + " + im + "i)";
    }
}


public class Main {
    public static void main(String[] args) {
        Complex obj1 = new Complex(10, 15);
        Complex obj2 = new Complex(obj1);
        
        System.out.println(obj2);
    }
}
```

Output:

```
(10.0 + 15.0i)
```


# Clone() method in Java

Object cloning refers to the creation of an exact copy of an object. It creates a new instance of the class of the current object and initializes all its fields with exactly the contents of the corresponding fields of this object.

**Using Assignment Operator to create a copy of the reference variable**

```

public class Test {
    
    int x;
    int y;
    
    public Test() {
        x = 10;
        y = 20;
    }
}

public class Main {
    public static void main(String[] args) {
        Test obj1 = new Test();
        System.out.println("x = " + obj1.x + " y = " + obj1.y);
        
        Test obj2 = obj1;
        
        obj2.x = 15;
        // Any change made in obj2 will be reflected in obj1
        
        System.out.println("x = " + obj1.x + " y = " + obj1.y);
        System.out.println("x = " + obj2.x + " y = " + obj2.y);
    }
}
```

Output:

```
x = 10 y = 20
x = 15 y = 20
x = 15 y = 20
```

**Creating a copy using the clone() method**


# Shallow Copy

When we do a copy of some entity to create two or more than two entities such that changes in one entity are reflected in the other entities as well, then that's called **shallow copy**. In shallow copy, new memory allocation never happens for the other entities, and the only reference is copied to the other entities. The following example demonstrates the same.


```

public class Test {
    
    int x;
    int y;
    
    public Test() {
        x = 10;
        y = 20;
    }
}

public class Main {
    public static void main(String[] args) {
        Test obj1 = new Test();
        System.out.println("x = " + obj1.x + " y = " + obj1.y);
        
        Test obj2 = obj1;
        
        obj2.x = 15;
        System.out.println("x = " + obj1.x + " y = " + obj1.y);
        System.out.println("x = " + obj2.x + " y = " + obj2.y);
    }
}
```

Output:
```
x = 10 y = 20
x = 15 y = 20
x = 15 y = 20
```

**Explaination**:

In the above example obj1 and obj2 are pointing to the same memory location or object. Therefore, whatever update we do use the reference variable obj2, the same changes will be reflected using the reference variable obj1.


# Deep Copy

When we do a copy of some entity to create two or more than two entities such that changes in one entity are not reflected in the other entities, then we can say we have done a deep copy. In the deep copy, a new memory allocation happens for the other entities, and reference is not copied to the other entities. Each entity has its own independent reference. The following example demonstrates the same.


```
public class DeepCopy {
    int x;
    int y;
    
    public DeepCopy() {
        x = 10;
        y = 20;
    }
}

public class Main {
    public static void main(String[] args) {
        DeepCopy obj1 = new DeepCopy();
        System.out.println("x = " + obj1.x + " y = " + obj1.y);
        
        DeepCopy obj2 = new DeepCopy();
        
        obj2.x = 15;
        System.out.println("x = " + obj1.x + " y = " + obj1.y);
        System.out.println("x = " + obj2.x + " y = " + obj2.y);
    }
}

```

Output:
```
x = 10 y = 20
x = 10 y = 20
x = 15 y = 20
```

**Differences Between Shallow Copy and Deep Copy**

| Shallow Copy | Deep Copy |
| ------------ | --------- |
| It is fast as no new memory is allocated. | It is slow as new memory is allocated. |
| Changes in one entity is reflected in other entity. | Changes in one entity are not reflected in changes in another identity. |
| The default version of the clone() method supports shallow copy. | In order to make the clone() method support the deep copy, one has to override the clone() method. |
| A shallow copy is less expensive. | Deep copy is highly expensive. |
