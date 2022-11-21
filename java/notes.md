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

Let's see the example, where downcasting is possible by instanceof operator.

