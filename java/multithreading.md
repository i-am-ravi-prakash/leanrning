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
