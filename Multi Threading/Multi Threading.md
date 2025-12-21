[[HPC]]
### What is a Thread?
A thread is the smallest unit of execution inside a process.
- A process can have multiple threads.
- Threads share the same code and global data but have their own registers and local variables (stack).
- Think of a thread as a lightweight subprocess.

![[Pasted image 20251106225751.png]]
***Join :** Joins threads or waits for threads to finish their work in the main function.
Thread th1 = new Thread( either object or a runnable function) eg.  // **Java** Specific
