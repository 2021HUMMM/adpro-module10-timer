# Tutorial 10 - Timer

## SECOND COMMIT
![img](/img/image1.png)

The first line, “Ilham's Komputer: hey hey”, is printed from the main thread immediately after execution starts. Then, an asynchronous task is spawned, which quickly prints “Ilham's Komputer: howdy!” before hitting an await on a custom TimerFuture that pauses the task for 2 seconds using a separate thread. Once the timer completes, it wakes the task, allowing it to resume and print “Ilham's Komputer: done!”. After all tasks finish and the spawner is dropped (signaling no more tasks will be added), the executor exits cleanly and returns control to the terminal.

## THIRD COMMIT

### 1. ![img](/img/image_drop_spawner.png)
### 2. ![img](/img/image_no_drop_spawner.png)
</br>
The difference between the two outputs lies in whether drop(spawner); is called in the main.rs file. When drop(spawner); is uncommented, as seen in the first image, it explicitly informs the custom executor that no more tasks will be submitted. As a result, after all three asynchronous tasks complete their execution and print their respective messages (“howdy!”, “howdy2!”, “howdy3!”, followed by “done!”, “done2!”, and “done3!” after a delay), the executor exits cleanly and the program returns control to the terminal. However, in the second image, drop(spawner); is commented out, meaning the executor continues waiting for new tasks because the task channel remains open. Even though all tasks finish and their output appears, the program doesn’t terminate, and the terminal hangs indefinitely. This demonstrates the importance of dropping the spawner to signal task completion and allow the executor to shut down gracefully.







