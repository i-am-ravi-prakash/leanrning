# Multithreading in Java

## Contents

- Introduction
- Process, Thread, Multitasking, Multithreading, Multiprocessing
- Creating and starting thread(s) in Java
- Life Cycle of thread
- Thread operations
- Daemon thread
- Producer and consumer problem


## Introduction

Threads are basically the lightweight and smallest unit of processing that can be managed independently by a scheduler. It is considered the simplest way to take advantage of multiple CPUs available in a machine. They share the common address space and are independent of each other.

- Multithreading in Java is a process of executing multiple threads simultaneously.
- A thread is a lightweight sub-process, the smallest unit of processing.

<img width="803" alt="Screenshot 2022-11-06 at 10 11 23 AM" src="https://user-images.githubusercontent.com/84272788/200154586-ad3cf93e-61f3-4d15-8099-b64a050d8389.png">

If multiple processes are being executed simulatneously, it's called multi-processing.

Let's say, I am working on my computer. I am playing my favourite song on it, and also working on some file. And alongwith these works, my computer is also downloading some files from internet. This is an example of multi-processing because multiple processes (playing song, editing file, downloading files) are being executed simultaneously.

If multiple threads are running to complete one process, it's called multi-threading.

Let's say IDM (Internet Download Manager) software is downloading three files from the internet simultaneously. As we know thread is the smallest unit of processing so here thread will come into picture. There will be one thread downloading one file My_Fav_Song.mp4, one separate thread will be downloading one file Reports.pdf and another thread is downloading Employee.xls from internet. Here we can see, in a single process (downloading of file(s) from internet) there are multiple threads working. This is an example of multi-threading.

**Benefits of multithreading**

- Allow the program to run continuously even if a part of it is blocked.
- Allows to write effective programs that utilize maximum CPU time.
- Increase use of CPU resources and reduce costs of maintenance.
- If an exception occurs in a single thread, it will not affect other threads as threads are independent.

**Difference between thread and process**

**Process**: It simply refers to a program that is in execution i.e., an active program. A process can be handled using PCB (Process Control Block).

**Thread**: It simply refers to the smallest units of the particular process. It has the ability to execute different parts (referred to as thread) of the program at the same time.

| Thread | Process |
| ------ | ------- |
| It is a subset of a subunit of a process. | It is a program in execution containing multiple threads. |
| In this, inter-thread communication is faster, less expensive, easy and efficient because threads share the same memory address of the process they belong to.| In this, inter-process communication is slower, expensive, and complex because each process has different memory space or address. |
| It requires less time for creation, termination, and context switching. | It requires more time for creation, termination, and context switching. |
| Processes with multiple threads use fewer resources. | Processes without threads use more resources. |
| There is a need for synchronization in threads to avoid unexpected scenarios or problems. | There is no need for synchronization in each process. |
| Threads are parts of a process, so they are dependent on each other but each thread executes independently. | Processes are independent of each other. |


## Creating threads in Java

There are two ways to create threads in Java:
1. Implementing Runnable interface
2. Extending Thread class

### Thread creation by implementing Runnable interface

```
public class MyThreadI implements Runnable{

    public static void main(String[] args) {
        MyThreadI myThreadI = new MyThreadI();
        Thread threadI = new Thread(myThreadI);
        threadI.start();
    }

	@Override
    public void run() {
        for (int i = 0; i <= 10; i++) {
            System.out.println("Downloading reports.ppt. Progress ... " + (i * 10) + "%");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println("" + e.getMessage());
            }
        }
        System.out.println("Download completed");
    }

}
```

### Thread creation by extending Thread class

```
public class MyThreadC extends Thread{
    
    public static void main(String[] args) {
        MyThreadC myThreadC = new MyThreadC();
        myThreadC.start();
    }
    
    public void run() {
        for (int i = 0; i <= 10; i++) {
            System.out.println("Downloading song.mp3. Progress... " + (i * 10) + "%");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println("" + e.getMessage());
            }
        }
    }
}
```

**NOTE**: There is always one main thread which is created by the JVM


## Life cycle of Thread

<img width="1205" alt="Screenshot 2022-11-04 at 2 46 42 PM" src="https://user-images.githubusercontent.com/84272788/200106617-ae1a63ac-798f-4697-bd45-3e3ba81b33d0.png">

When we create the thread and call the start() method it'll go in Runnable state. Runnable state means waiting state. Once thread scheduler pick the newly created thread, it's in Running state. While in running state, if the thread encounters sleep(), wait() or has to wait for any I/O it goes in Non Runnable (Blocked) state. Once sleep(), wait() or I/O is completed, the thread again goes back to Runnable state and from there it'll be picked by thread scheduler. After finishing the operation or calling stop() on the thread, it's finally terminated.


## Thread Operations

- Thread class provides several methods to perform operations with threads.
- Thread class is available in java.lang package so we don't need to import this.
- Followings are some of the importants methods provided for thread oprations:
	- **public String getName()**: returns the name of thread
	- **public void setname(String name)**: sets the thread name
	- **public void run()**: the run() method is used to start or begin the execution of the same thread. When the run() method is called, no new thread is created as in the case of the start() method. This method is executed by the current thread. One can call the run() method multiple times.
	- **public void start()**: In simple words, the start() method is used to start or begin the execution of a newly created thread. When the start() method is called, a new thread is created and this newly created thread executes the task that is kept in the run() method. One can call the start() method only once.
	- **public long getId()**: returns id of thread
	- **setPriority(p)**: set the priority of any thread
	- **getPriority()**: get the priority of any thread
	- **wait()**: As the name suggests, it is a non-static method that causes the current thread to wait and go to sleep until some other threads call the notify () or notifyAll() method for the object’s monitor (lock). Mostly used for inter-thread communication.
	- **sleep()**:  As the name suggests, it is a static method that pauses or stops the execution of the current thread for some specified period.
	- **notify()**: It sends a notification and wakes up only a single thread instead of multiple threads that are waiting on the object’s monitor.
	- **notifyAll()**: It sends notifications and wakes up all threads and allows them to compete for the object's monitor instead of a single thread.
	- **join()**: This method is generally used to pause the execution of a current thread unless and until the specified thread on which join is called is dead or completed.



## Daemon thread

- Daemon thread in Java is service provider thread which provides service to user defined threads.
- **setDaemon(Boolean)**: set any thread to daemon thread
- **public boolean isDaemon()**: returns true if the thread is daemon thread, false otherwise
- Garbage collector is the best example of Daemon thread.

**What's the difference between User thread and Daemon thread?**

User and Daemon are basically two types of thread used in Java by using a ‘Thread Class’.  

**User Thread (Non-Daemon Thread):** In Java, user threads have a specific life cycle and its life is independent of any other thread. JVM (Java Virtual Machine) waits for any of the user threads to complete its tasks before terminating it. When user threads are finished, JVM terminates the whole program along with associated daemon threads. 

**Daemon Thread:** In Java, daemon threads are basically referred to as a service provider that provides services and support to user threads. There are basically two methods available in thread class for daemon thread: setDaemon() and isDaemon().

| User Thread | Daemon Thread |
| ----------- | ------------- |
| These threads are normally created by the user for executing tasks concurrently. | These threads are normally created by JVM. |
| They are used for critical tasks or core work of an application. | They are not used for any critical tasks but to do some supporting tasks. |
| These threads are referred to as high-priority tasks, therefore are required for running in the foreground. | These threads are referred to as low priority threads, therefore are especially required for supporting background tasks like garbage collection, releasing memory of unused objects, etc. |
| JVM waits for user threads to finish their tasks before termination. | JVM does not wait for daemon threads to finish their tasks before termination. |


**How can we create daemon threads?**

We can create daemon threads in java using the thread class method **setDaemon(true)**. It is used to mark the current thread as daemon thread or user thread. **isDaemon()** method is generally used to check whether the current thread is daemon or not. If the thread is a daemon, it will return true otherwise it returns false.

**Program to illustrate the use of setDaemon() and isDaemon() method.**

```
/**
 * @author raviprakash
 *
 */
public class DaemonThread extends Thread{
    
    public DaemonThread(String name) {
        super(name);
    }
    
    public void run() {
        if (Thread.currentThread().isDaemon()) {
            System.out.println(getName() + " is Daemon thread");
        } else {
            System.out.println(getName() + " user thread");
        }
    }
    
    public static void main(String[] args) {
        DaemonThread t1 = new DaemonThread("t1");
        DaemonThread t2 = new DaemonThread("t2");
        DaemonThread t3 = new DaemonThread("t3");
        
        t1.setDaemon(true);
        t1.start();
        t2.start();
        t3.setDaemon(true);
        t3.start();
    }
}
```

Output:
```
t1 is Daemon thread 
t3 is Daemon thread 
t2 is User thread
```

**NOTE**: But we can only call the setDaemon() method before start() method otherwise it will definitely throw IllegalThreadStateException.

## Producer Consumer Problem

The producer-consumer problem is an example of a multi-process synchronization problem. The problem describes two processes, the producer and the consumer that shares a common fixed-size buffer use it as a queue.

- The producer’s job is to generate data, put it into the buffer, and start again.
- At the same time, the consumer is consuming the data (i.e., removing it from the buffer), one piece at a time.

**Problem**

Given the common fixed-size buffer, the task is to make sure that the producer can’t add data into the buffer when it is full and the consumer can’t remove data from an empty buffer.

