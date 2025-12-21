[[Multi Threading]]

`%% std::lock_guard<mutex> lock(m) %%`
`std::mutex m;`

`void func() {`
    `std::lock_guard<std::mutex> lg(m); // lock happens here`
    `// critical section`
`} // lg goes out of scope → unlock happens here automatically`


`std::unique_lock` is a **mutex wrapper** provided by the C++ standard library (`<mutex>`).  
It manages the **ownership and locking** of a `std::mutex` — similar to how `std::unique_ptr` manages a pointer.

It’s called _unique_ because only **one unique_lock** can own a given mutex at a time.

`#include <iostream>`
`#include <thread>`
`#include <mutex>`
`using namespace std;`

`mutex m;`

`void print_message(const string& msg) {`
    `unique_lock<mutex> lock(m);  // 🔒 locks m automatically`
    `cout << msg << endl;`
`}  // 🔓 unlocks m automatically here (when 'lock' goes out of scope)`

`int main() {`
    `thread t1(print_message, "Hello");`
    `thread t2(print_message, "World");`
    `t1.join();`
    `t2.join();`
`}`

**Unique Lock**: unique_lock<mutex> lock(m);

|Feature|`std::lock_guard`|`std::unique_lock`|
|---|---|---|
|**Locks immediately** on creation|✅ Yes|✅ By default (but optional)|
|**Can unlock/relock manually**|❌ No|✅ Yes|
|**Can be moved (transferred)**|❌ No|✅ Yes|
|**Can be constructed with no lock (defer_lock)**|❌ No|✅ Yes|
|**Can use `std::condition_variable`**|❌ No|✅ Yes|
|**Performance overhead**|Slightly faster|Slightly slower|
|**Use case**|Simple, strict locking|Complex, conditional, or delayed locking|

![[Pasted image 20251112225547.png]]

To transfer lock ownership:

`std::unique_lock<std::mutex> a(m); `
 `std::unique_lock<std::mutex> b = std::move(a);`

After this:

- `b` owns the lock
    
- `a` becomes empty (a.safe but uninitialized object)