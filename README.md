## Threads and Synchronization

This lab illustrates the problem of synchronization when many threads are operating on a shared object.  The general issue is called "thread safety", and it is a major cause of errors in computer software.

## Assignment

To the problems on the lab sheet and record your answers here.

1. Record average run times.
2. Write your explanation of the results.  Use good English and proper grammar.  Also use good Markdown formatting.

## ThreadCount run times

These are the average runtime using 3 or more runs of the application.
The Counter class is the object being shared by the threads.
The threads use the counter to add and subtract values.

| Counter class           | Limit              | Runtime (sec)   |
|:------------------------|:-------------------|-----------------|
| Unsynchronized counter  |      10,000,000    |    0.023007     |
| Using ReentrantLock     |      10,000,000    |    1.116937     |
| Syncronized method      |      10,000,000    |    1.097928     |
| AtomicLong for total    |      10,000,000    |    0.421863     |

## 1. Using unsynchronized counter object
1.1 The total should be zero.Total change in every time.

1.2 0.0260696667

1.3 The 2 thread add and subtract that run in a parallel sometime add set the counter before substract get the counter that make the total sometime not a zero in sometime.


## 2. Implications for Multi-threaded Applications
How might this affect real applications?  

The application work not correctly when we use counter in application.

For example

Deposit : 1000 --> counter 1000 ---> Withdraw 700 and Deposit 500 in the same time when counter is 1000 and 2 thread use counter 1000 so it make the application work not correctly.

## 3. Counter with ReentrantLock


3.1 Total always zero.Average is zero.

3.2 The result is always zero because in the counter with lock it separate the thread by the lock method that when one of thread is running the other thread can't run in the same time.

3.3 ReentrantLock make the other thread can't run when the previous thread is still running.We should use it in the program because it make the application run in the correctly and we use it when we have many thread to run.

3.4 Use to lock to permission the other thread run.


## 4. Counter with synchronized method

4.1 It is always zero.

4.2 When the previous thread is executing a synchronized method is block the other thread.

4.3 Synchronized methods enable a simple strategy for preventing thread interference and memory consistency errors. 


## 5. Counter with AtomicLong

5.1 Java provides AtomicLong which can be used without any synchronization.


5.2 You would use AtomicLong when you have guarantee that have value can be used in concurrent environment and don't need the wrapper class.Using AtomicLong because Long does not allow for thread interoperability

## 6. Analysis of Results

6.1 Unsynchronized counter is the fastest,ReentrantLock is the slowest.

6.2 I think the best solution can be applied to the broadest range of problem is using AtomicCounter because it will work completely by itself without any synchronization.

## 7. Using Many Threads (optional)

