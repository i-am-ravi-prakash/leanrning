# Collection frameworks

An array is an indexed collection of fixed number of homegeneous daya elements. It is preferable when we have to store a lot of data let's say roll numbers of student in a class. We can create and access an array to store roll numbers of let's say 100 students in a class like below:

```
int[] rollNumber = new int[100];
int len = rollNumber.length;
for(int i = 0; i < len; i++){
  System.out.println(rollNumber[i]);
}
```

But array comes with some limitation which are as follows:

- Array is fixed in size.
- Array can contain homogeneous data types.
- There is no underlying data structure for arrays.

To overcome the above problems of array, collections were introduced. Below are the advantages of the collection framework:

- Collections are growable in nature. At runtime size can incease or decrease.
- Collections can hold homogeneous or heterogenous data elements.
- Every collection class has been implenented on some standard data structure.

**NOTE**: If number of elements is known, it's a good choise to go with array instead of collection.

Let's say we have an array arr of size 10. And the array is full. We will get error while executing the below line of code:

```
arr[10] = 10;
```

This is because the array size is fixed to be 10. And it can't be changed at the runtime. Let's take the same example with ArrayList. If we create an arrayList, internally one list is created with some size which we don't know. Let's say the list is full and we are trying to add one more element to that list. Internally, one new list will be created with size greater than the previous one and all the data of the previous list will be copied in the newly create one and reference will be changed from previous list to the new one and garbage collector will destroy the previous list. So, we can see using collection is a costly operation. that's why it's recommended to use array if the size is already known to us.

## Differences between arrays and collections:

| Array | Collection |
| ----- | ---------- |
| Array is fixed in size.| Collection is growable in nature.|
| Array is not recommended memory wise. | Collection is recommended memory wise. |
| WRT preformance array is not a good choice. | WRT preformance collection is recommended. |
| It can hold only homogeneous data. | It can hold both homogeneous and heterogeneous data. |
| There is no underlying data structure for array. | Collections have been imoplemented on standard data structure. |
| Array can hold both primitive data types and objects. | Collections can hold only object data types. |


**When we want to represent a group of individual objects as a single entity, we should go for Collection. Collection framework defines several Classes and interfaces which is used to represent Collection. **

## 9 key interfaces of Collection framework

## 1. Collection interface

- If we want to represent a group of individual objects as a single entity then we should go for Collection.
- Collection interface defines most commonly used methods which are applicable to any Collection object.
- In general, Collection interface is considered as the root interface of Collection framework.

**NOTE**: There is no concrete class which implements Collection interface directly.

**Differences between Collection and Collections**:

- Collection is an interface which is used to represent a group of individual objects as a single entity.
- Collections is an utility class present in java.util package which defines several method like sorting, searching, etc. for various Collection objects.


## 2. List interface

- List is a child interface of Collection.
- List is an interface which is used to represent a group of individual objects as a single entity where duplicates are allowed and order of elements must be maintained.
- Belows are the implementation classes of List interface:
  - ArrayList
  - LinkedList
  - Vector
  - Stack


## 3. Set interface

- It is child interface of Collection.
- It is used to represent a group of individual object as a single entity where duolicates are not allowed and order of elements doesn't not need to be maintained.

**NOTE**: HashSet is the implementation class of Set interface. LikedHashSet is child class of HashSet.

Differeneces between List and Set interfaces:

| List | Set |
| ---- | --- |
| Duplocates are allowed.| Duplicates are not allowed. |
| Order of elements is maintained. | Order of elements are not maintained. |

## 4. SortedSet interface

- SortedSet is child interface of Set.
- It is used to represent a group of individual object as a single entity where duolicates are not allowed and all the elements must be inserted in sorted manner.


## 5. NavigableSet interface

- It is a child interface of SortedSet. It defines variuos methods for navigation purposes.
- TreeSet is implementation class of NavigableSet interface.


## 6. Queue interface

- It is a child interface of Collection.
- If we want to represent a group of individual objects prior to processing then we should go for Queue.
- Two implementation classes of Queue interface are PriorityQueue and BlockingQueue.
- LinkedBlockingQueue and PrioriryBlockingQueue are the two child class of BlockingQueue.

**If we want to represent a group as key value pair then we should go for Map interface.**


## 7. Map interface

- Map is not a child interface of Collection.
- If we want to represent a group of key-value pairs, then we should go for Map interface.
- Both key and value are objects.
- Duplicate keys are not allowed however we can have duplicate value.


Below are the implementation classes of Map interface:
1. HashMap
2. WeakHashMap
3. IdentityHashMap
4. Hashtable

- LinkedHashMap is child class of HashMap.
- Hashtable is child class of Dictionary.
- Properties is the child class of hashtable.


## 8. Sortedmap interface

- It is a child interface of Map.
- If we want to represent a group of key value pair in some sorting order of keys, then we should go for SortedMap.


## 9. NavigableMap interface

- It is a child interface of SortedMap.
- It defines several utility methods for navigation purposes.
- TreeMap is the implementation class of NavigableMap interface.
