---
title: C++::THREADS
date: 2022-01-01
tags: [
    "C++",
    "Threads"
] 
categories: [
    "C++"
]
thumbnail:
---

In shared memory multiprocessor architecture, threads can be used to implement parallelism. For UNIX systems, a standardized C language threads programming interface has been specified by the IEEE POSIX 1003.1c standard. Implementations that adhere to this standard are referred to as **POSIX threads**, or **Pthreads**. This post introduces essentials of the POSIX threads and the programming examples in C/C++.


### [POSIX Threads Essentials](#posix-threads-essentials)
##### [&nbsp; &nbsp; &nbsp; 1. PThreads Overview](#pthreads-overview)
##### [&nbsp; &nbsp; &nbsp; 2. Thread Management](#examples)
##### [&nbsp; &nbsp; &nbsp; 3. Mutex Variables](#examples)
##### [&nbsp; &nbsp; &nbsp; 4. Condition Variables](#examples)
##### [&nbsp; &nbsp; &nbsp; 5. Monitoring, Debugging and Performance Analysis](#examples)
### [POSIX Threads Exercise](#hmm)
##### [&nbsp; &nbsp; &nbsp; 1. Exercise #1](#examples)
##### [&nbsp; &nbsp; &nbsp; 2. Exercise #2](#examples)
##### [&nbsp; &nbsp; &nbsp; 3. Exercise #3](#examples)
##### [&nbsp; &nbsp; &nbsp; 4. Exercise #4](#examples)
<!--more-->

# **POSIX Threads Essentials**

## **PThreads Overview**
A programming language consits of a grammar/syntax and execution model.
**POSIX Threads** (known as **pthreads**) is a parallel execution model specifing the behavior of elements of the language.
Pthreads control multiple different flows of work that overlap in time. Each flow of work is reffered to as a thread, and creation and control over these flows is achieved by making calls to the POSIX Thread API.

### **1. Threads and Process**
A **thread** is defined as the smallest independent stream of programmed instructions that can be managed by scheduler, which is typically a part of the operating system. The implementation of threads and processes differs between operating systems, but in most cases a thread is a compnent of process. 

A **Process** is created by the operating system. A process consists of below process control infomration, which is used by OS to manage the process. The information is stored in the **Process Control Block (PCB)**.

Information | Description
-------- | -------
Process scheduling state | The state of the process in terms of "ready", "suspended", etc., and other scheduling information as well, such as priority value, the amount of time elapsed since the process gained control of the CPU or since it was suspended. Also, in case of a suspended process, event identification data must be recorded for the event the process is waiting for.
Process structuring information | the process's children id's, or the id's of other processes related to the current one in some functional way, which may be represented as a queue, a ring or other data structures
Interprocess communication information | flags, signals and messages associated with the communication among independent processes
Process Privileges | allowed/disallowed access to system resources
Process State | new, ready, running, waiting, dead
Process Number (PID) | unique identification number for each process (also known as Process ID)
Program Counter (PC) | A pointer to the address of the next instruction to be executed for this process
CPU Registers | Register set where process needs to be stored for execution for running state
CPU Scheduling Information | information scheduling CPU time
Memory Management Information | page table, memory limits, segment table
Accounting Information | amount of CPU used for process execution, time limits, execution ID etc.
I/O Status Information | list of I/O devices allocated to the process.

Threads use and exist within these process resources, yet are able to be scheduled by the operating system and run as independent entities largely because they duplicate only the bare essential resources that enable them to exist as executable code.

This independent flow of control is accomplished because a thread maintains its own:

- Stack pointer
- Registers
- Scheduling properties (such as policy or priority)
- Set of pending and blocked signals
- Thread specific data.

So, in summary, a thread:

- Exists within a process and uses the process resources
- Has its own independent flow of control as long as its parent process exists and the OS supports it
- Duplicates only the essential resources it needs to be independently schedulable
- May share the process resources with other threads that act equally independently (and dependently)
- Dies if the parent process dies - or something similar
- Is “lightweight” because most of the overhead has already been accomplished through the creation of its process.

Because threads within the same process share resources:

- Changes made by one thread to shared system resources (such as closing a file) will be seen by all other threads.
- Two pointers having the same value point to the same data.
- Reading and writing to the same memory locations is possible, and therefore requires explicit synchronization by the programmer.

### **2. PThreads**
Historically, hardware vendors have implemented their own proprietary versions of threads. These implementations differed substantially from each other making it difficult for programmers to develop portable threaded applications.

In order to take full advantage of the capabilities provided by threads, a standardized programming interface was required. For UNIX systems, this interface has been specified by the IEEE POSIX 1003.1c standard (1995). Implementations which adhere to this standard are referred to as POSIX threads, or Pthreads. Most hardware vendors now offer Pthreads in addition to their proprietary API's.

Pthreads are defined as a set of C language programming types and procedure calls, implemented with a `pthread.h` header/include file and a thread library - though this library may be part of another library, such as `libc`.

There are several drafts of the POSIX threads standard. It is important to be aware of the draft number of a given implementation, because there are differences between drafts that can cause problems.

### **3. Threaded Program Design**

On modern, multi-cpu machines, pthreads are ideally suited for parallel programming, and whatever applies to parallel programming in general, applies to parallel pthreads programs.

There are many considerations for designing parallel programs, such as:
- What type of parallel programming model to use?
- Problem partitioning
- Load balancing
- Communications
- Data dependencies
- Synchronization and race conditions
- Memory issues
- I/O issues
- Program complexity
- Programmer effort/costs/time
- ...
