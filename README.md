# Tutorial 10 - Timer

![img](/img/image.png)

The first line, “Ilham's Komputer: hey hey”, is printed from the main thread immediately after execution starts. Then, an asynchronous task is spawned, which quickly prints “Ilham's Komputer: howdy!” before hitting an await on a custom TimerFuture that pauses the task for 2 seconds using a separate thread. Once the timer completes, it wakes the task, allowing it to resume and print “Ilham's Komputer: done!”. After all tasks finish and the spawner is dropped (signaling no more tasks will be added), the executor exits cleanly and returns control to the terminal.







