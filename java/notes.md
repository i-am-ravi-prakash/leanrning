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
