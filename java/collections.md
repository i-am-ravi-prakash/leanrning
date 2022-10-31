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

