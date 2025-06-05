# OS-Practical-Day_22-02-06-2025-

01.
 This C program demonstrates interprocess communication (IPC) between a parent and child process using shared memory created via mmap() with the MAP_SHARED | MAP_ANONYMOUS flags.

 Key Operations:
        mmap() is used to allocate a shared memory region that is accessible by both the parent and child processes.
        The child process writes a message ("Hello from child!") to the shared memory.
        The parent process, after waiting for the child to finish (wait(NULL)), reads the message from the shared memory and prints it.

Concepts Demonstrated:
      Shared memory using memory mapping (mmap)
      Process creation using fork()
      Synchronization using wait() to ensure the parent reads only after the child writes

02.
/*There are parent process, shared memory and child process... The parent process should read the input (n,r). after reading the value the parent process should send the value through shared memory to child Process.. 
The child process should print the factorial only... It should return the factorial value to shared memory... 
And the shared memory send it to the parent process , after getting the factorial the parent process should print nCr and nPr*/

This C program demonstrates Inter-Process Communication (IPC) using System V shared memory to compute nCr and nPr using factorials.

Program Flow Overview:
Parent Process:
      Accepts input values n and r from the user.
      Writes these values to a shared memory segment.
Child Process:
    Reads n and r from shared memory.
    Calculates:
        n!, r!, and (n-r)! using a custom factorial function.
        Stores the factorial results back in the shared memory.
        Prints the factorial values.
Parent Process (After Wait):
Retrieves the factorial values from shared memory.
Calculates:
      nCr = n! / (r!(n−r)!)
      nPr = n! / (n−r)!

Prints the results.
Detaches and removes the shared memory.

Key Concepts Demonstrated:
Use of ftok, shmget, shmat, shmdt, and shmctl for shared memory management.
fork() for process creation.
Parent-child synchronization using wait(NULL).
Modular design: logic split between main and child function.
Factorial-based combinatorics in IPC context.

03.
This pair of C programs demonstrates Inter-Process Communication (IPC) using System V shared memory for a simple writer-reader model:
      The writer process (process_01) creates a shared memory segment and writes user input into it.
      The reader process attaches to the same shared memory segment, reads the content, displays it, and then removes the shared memory.
This approach effectively illustrates one-way communication between processes using shared memory, suitable for transferring string data. It also reinforces the importance of memory cleanup using shmdt() and shmctl().


![output1](https://github.com/user-attachments/assets/cd3ef49d-08bf-4b47-b1c6-ae3cacd3d77d)
