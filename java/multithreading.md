# Multithreading in Java

### Contents

- Introduction
- Process, Thread, Multitasking, Multithreading, Multiprocessing
- Creating and starting thread(s) in Java
- Life Cycle of thread
- Thread operations
- Daemon thread
- Producer and consumer problem


## Introduction

- Multithreading in Java is a process of executing multiple threads simultaneously.
- A thread is a lightweight sub-process, the smallest unit of processing.

If multiple processes are being executed simulatneously, it's called multi-processing.

Let's say, I am working on my computer. I am playing my favourite song on it, and also working on some file. And alongwith these works, my computer is also downloading some files from internet. This is an example of multi-processing because multiple processes (playing song, editing file, downloading files) are being executed simultaneously.

If multiple threads are running to complete one process, it's called multi-threading.

Let's say IDM (Internet Download Manager) software is downloading three files from the internet simultaneously. As we know thread is the smallest unit of processing so here thread will come into picture. There will be one thread downloading one file My_Fav_Song.mp4, one separate thread will be downloading one file Reports.pdf and another thread is downloading Employee.xls from internet. Here we can see, in a single process (downloading of file(s) from internet) there are multiple threads working. This is an example of multi-threading.


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
	- **public void run()**: contains the task of thread
	- **public void start()**: start thread by allocating resources
	- **public long getId()**: returns id of thread
	- **setPriority(p)**: set the priority of any thread
	- **getPriority()**: get the priority of any thread
	- **sleep(), wait(), join(), interrupt(), resume(), stop()**



## Daemon thread

- Daemon thread in Java is service provider thread which provides service to user defined threads.
- **setDaemon(Boolean)**: set any thread to daemon thread
- **public boolean isDaemon()**: returns true if the thread is daemon thread, false otherwise
- Garbage collector is the best example of Daemon thread.
