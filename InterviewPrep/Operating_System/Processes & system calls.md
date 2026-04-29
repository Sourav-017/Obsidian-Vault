
**Q1.** What is the return value of `fork()` in the parent, in the child, and on failure?

**Ans**: val < 0 on failure, 0 on child, childs pid on parent.

**Q2.** You call `fork()` then `exec()` in the child. Does the child's PID change after `exec()`?
**Ans**: No.
1. If `fork()` **copies** a process, `execvp()` **replaces** it.
2. `wait()` does two things:

	**Blocks the parent** until a child process finishes
	**Cleans up the zombie** — removes the child's entry from the process table and lets the parent collect the child's exit status

	So without `wait()`, finished children pile up as zombies eating process table space. `wait()` is basically the parent saying _"okay I acknowledge my child is done, clean it up."_

**Q3.** What happens to a child process if the parent exits without calling `wait()`?
**Ans**: The process becomes a orphan process and Run as a child of init process.


**Q4.** In xv6, every system call goes through a trap. What is the specific instruction a user program executes to trigger a system call on RISC-V xv6?


**Q5.** `fork()` returns twice. But `exec()` — how many times does it return on success?
**Ans**: **`exec()` does not return at all on success.** There's nothing to return to — the entire code/stack/data of the calling program is wiped and replaced. A return value only exists on **failure** (returns -1).