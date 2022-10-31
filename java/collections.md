# Collection frameworks

An array is an indexed collection of fixed number of homegeneous daya elements. It is preferable when we have to store a lot of data let's say roll numbers of student in a class. We can create and access an array to store roll numbers of let's say 100 students in a class like below:

```int[] rollNumber = new int[100];
int len = rollNumber.length;
for(int i = 0; i < len; i++){
  System.out.println(rollNumber[i]);
}
```

But array comes with some limitation which are as follows:

- Array is fixed in size.
- Array can contain homogeneous data types.
- There is no underlying data structure for arrays.
