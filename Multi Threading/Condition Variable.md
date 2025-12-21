[[Multi Threading]]

A **condition variable** (`std::condition_variable`) is a synchronization primitive in C++ that allows one thread to **wait** until another thread **signals** that some condition has become true.

It works together with a **mutex**.

---

# **Why We Need Condition Variables**

Busy waiting is bad:

`while (!ready) {     // waste CPU }`

A condition variable allows the thread to sleep efficiently until something changes.

---

# **Basic Components**

A condition variable is used with:

- a **mutex**
    
- a **predicate** (shared condition)
    
- `wait()`, `notify_one()`, `notify_all()`
    

---

# 🧩 Minimal Example

## Thread 1 — waits:

`std::mutex m; std::condition_variable cv;`
`bool ready = false;  `
`void waiting_thread() {`
`std::unique_lock<std::mutex> lk(m);`
`cv.wait(lk, [] {`
` return ready;`
` });`
`  // sleeps until ready == true      // After waking up, ready is true `
`std::cout << "Proceeding...\n"; `
`}`

## Thread 2 — signals:

`void signaling_thread() { `    
`{`
`    std::lock_guard<std::mutex> lk(m);`
`    ready = true; // change the condition`
`}  `
`cv.notify_one();  // wake up one waiting thread ``}`

---

# 🧠 **How `wait` works internally**

`cv.wait(lk)` does:

1. **Unlocks the mutex automatically**
    
2. **Puts the thread to sleep (no CPU used)**
    
3. When notified, wakes up
    
4. **Re-locks the mutex**
    
5. Returns to your code
    

---

# 🟨 Why do we pass a predicate (`wait(lk, predicate)`)?

Because of **spurious wake-ups** — a thread may wake up even without a notification.

Example:

`cv.wait(lk, []{ return ready; });`

This ensures:

- If wakes up wrongly → checks predicate → goes back to waiting
    
- If `ready == true` → continues
    

If you use the simple `wait(lk)` form, you must write:

`while (!ready)     cv.wait(lk);`

---

# 🟦 `notify_one` vs `notify_all`

### `notify_one()`

Wakes only **one** waiting thread.

### `notify_all()`

Wakes **all** waiting threads.

---

# 🛠️ Real Example: Producer–Consumer

## Producer

`void producer() {     std::unique_lock<std::mutex> lk(m);     data = 42;     ready = true;     lk.unlock();     cv.notify_one(); }`

## Consumer

`void consumer() {     std::unique_lock<std::mutex> lk(m);     cv.wait(lk, []{ return ready; });     std::cout << data << std::endl; }`

---

# 🎯 Summary (easy to remember)

- Condition variable lets threads **wait without busy looping**
    
- Used with a mutex and a predicate
    
- `wait()` unlocks → sleeps → re-locks
    
- Always check condition in a loop or use the predicate version
    
- Use `notify_one()` or `notify_all()` to wake waiting threads