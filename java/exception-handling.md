# Exception Handling

## Contents

- What is exception?
- What is exception handling?
- Why to handle exception?
- How to handle exception?
- try-catch practical example.
- Creating and using our own exception.


## What is exception?

Dictionary meaning of exception is any abnormal condition.

In Java, exception is an event that disrupts the normal flow of program.

When we compile any .java file, Java compiler looks for any syntax error in the .java file which is also called source code. If there are no syntax error in the source code then .class file will be generated which is also calles byte code and if there are any syntax error in the source code then we get compile time error. There might be some cases where we don't have any syntax error in the source code and it's compiled well but at the runtime we get the error. There are various runtime error which we may encounter like division by zero, file not found exception, null pointer exception, etc. These runtime errors are called exceptions.


## What is exception handling?

Exception Handling is a mechanism to handle runtime errors such as ClassNotFoundException, IOException, SQLException, RemoteException, etc.


## Why to handle exception?

Let's say there is one class file and there are 1
