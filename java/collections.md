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



# Collection Interface

- If we want to represent a group of individual objects as a single entity then we should go for Collection.
- Collection interface defines most commonly used methods which are applicable to any Collection object.
- In general, Collection interface is considered as the root interface of Collection framework.

Below are the important methods of Collection interface:

- **boolean add(Object o)**  It adds an object into collection
- **boolean addAll(Collection c)** It add a group of objects into collection
- **boolean remove(Object o)** It removes the given object from collection
- **boolean removeAll(Collection c)**  It removes a group of objects from collection
- **boolean retailAll(Collection c)**  It removes all objects from the collectoin except for the given one
- **void clear()** It clears the Collection
- **boolean contains(Object o)** It checks whether the given object is present in the Collection or not
- **boolean containsAll(Collection c)**  It checks if the list of given object is present or not in the Collection
- **boolean isEmpty()**  It checks if the Collection is empty
- **int size()**  It returns the size of the Collection
- **Object[] toArray()**  It converts the Collection to the object array
- **Iterator iterator()** It iterates through the objects present in the Collection one by one.

**NOTE**: Collection interface doesn't contain any method to retrieve objects as there is not concrete class which implements Collection interface directaly.



# List Interface

- List is a child interface of Collection.
- List is an interface which is used to represent a group of individual objects as a single entity where duplicates are allowed and order of elements must be maintained.
- We can differentiate duplicates by using index, and we can maintain the insertion order by using index. Hence, index plays a very important role in List interface.

**NOTE**: All the methods defined in the Collection interface are available in List interface. There are some List interface specific methods which are as follows:

- **void add(int index, Object o)** It adds the object into the list at the given index.
- **boolean addAll(int index, Collection c)** It adds the collection at the given index.
- **Object get(int index)** It returns the object present at the given index, returns null if anything is not present the given index.
- **Object set(int index, Object newObj)**  It updates the value of object present at the given index with the new object and returns the old object.
- **int indexOf(Object o)** It return the index of first occurence of object.
- **int lastIndexOf(Object o)** It returns the last index of occurence of the object.
- **Iterator iterator()** It is used to to iterate through the list.

There are three implementation classes of List interface:
1. ArrayList
2. LinkedList
3. Vector

Stack is the child class of Vector.



# ArrayList

This is the implementation class of List interface.

- The underlying data structure of ArrayList is resizable or growable array.
- Duplicates are allowed.
- Insertion order is maintained.
- Heteregeneous objects are allowed.
- Null insertion is possible.

**NOTE**: Heterogeneous objects are allowed in all Collections except TreeMap and TreeSet. In TreeMap and TreeSet, objects are stored in sorted order and for storing in sorted order, objects will be compared which possible only when objects are homogeneous.


**Different constructors used in ArrayList**:

1. ArrayList al = new ArrayList();

It creates an empty ArrayList with default initial capacity of 10. Once ArrayList reaches its max capacity and we try to insert more data into it, a new ArrayList will be created with the below new capacity:

new capacity = (current capacity * 3/2) + 1

2. ArrayList al = new ArrayList(int size)

It'll create an empty ArrayList of the given size.

3. ArrayList al = new ArrayList(Collections c)

It'll create an ArrayList as any given vector or LinkedList.

**NOTE**: Usually we use Collections to hold and transfer objects from one place to another. To provide support for this requirement every Collection already implements Serializable and Cloneable interface.

Only ArrayList and Vector implements RandomAccess interface so that we can access any random elements with the same speed. RandomAccess interface is available in java.util package.
RandomAccess interface doesn't contain any methods and it's a marker interface.

- ArrayList is the best choise if the frequent operation is retrieval of elements because ArrayList implements RandomAccess interface.
- ArrayList is the worst choise if the frequent operation is insertion or deletion in middle or any random place because of shifting of rest of the elements.


### Difference between Arraylist and Vector

| ArrayList | Vector |
| --------- | ------ |
| Every method available in ArrayList is non-synchronized. | Most of the methods available in Vector are synchronized. |
| Multiple threads are allowed to operate on ArrayList at a time and that's why ArrayList is not thread safe. | Only one thread is allowed to operate on Vector at a time. And so Vector is thread safe.|
| Threads don't need to operate on ArrayList, that's why relative performance of ArrayList is high. | Threads are required to wait to operate on Vector and hence the relative performance is low. |
| Introduced in 1.2 version. | Introduced in 1.0 version. |

**How to get synchronized version of Arraylist?**

By default, ArrayList objects are non-synchronized. But we can get synchronized version of ArrayList by using synchronizedList() method of Collections class.
```
ArrayList arrayList = new ArrayList();
```
It'll create a non-synchronized arraylist object.
```
List list = Collections.synchronizedList(arrayList);
```
It'll take the reference of non-synchronized arraylist and create one synchronized list.

```
public static List synchronizedList(List list);
```

Similarly we can get the synchronized versions of Set and Map objects by using following methods of Collections class:

```
public static Set synchronizedSet(Set set);

public static Map synchronizedMap(Map map);
```


# LinkedList

This is the implementation class of List interface.

- The underlying data structure of LinkedList is doubly LinkedList.
- Duplicates are allowed.
- Insertion order is maintained.
- Heteregeneous objects are allowed.
- Null insertion is possible.
- LinkedList implements Serializable and Cloneable interface but not RandomAccess interface. RandomAccess interface is only implemented by ArrayList and Vector.
- LinkedList is the best choise if the frequent operation is insertion and deletion from any random index.
- LinkedList is the worst choise if the frequent operation is retrieval because retrieval of data starts from 0th index in case of LinkedList.

We can use LinkedList to implement Stack and Queue. To provide support for this requirement, LinkedList provide below methods:

```
void addFirst(Object obj);
void addLast(Object obj);
Object getFirst();
Object getLast();
Object removeFirst();
Object removeLast();
```

**NOTE**: The above mentioned methods are only available for LinkedList class.

**Various constructors available in LinkedList**

```
LinkedList ll = new LinkedList();
```
This will create a linkedlist.

```
LinkedList ll = new LinkedList(Collection c);
```
This will create an equivalent linkedlist for any given collection.

