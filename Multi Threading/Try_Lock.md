[[Multi Threading]] [[Threading]]

So far I came across 2 types of try_lock().There are others obviously.
First mutex::try_lock() and other one is std::try_lock(m1, m2, m3, ..... mn)[Mainly Try to lock all possible mutex objects]
What try_lock() does is check if its possible to lock the object.If not possible return false instantly. Carefully follow the word instantly because in mutex::lock() cpu blocks the thread if not lockable and the thread waits for some time.

 std::try_lock(m1, m2, m3, ..... mn) if it fails to lock any mutex it'll release all the previously locked mutex and return the index of the mutex which is not lockable. Otherwise this function returns -1. 
`#include <iostream>`
`#include <thread>`
`#include <mutex>`
`#include <chrono>`

`using namespace std;`

`int X = 0, Y = 0;`
`std::mutex m1, m2;`

`void dosom(int sec)`
`{`
    `this_thread::sleep_for(chrono::seconds(sec));`
`}`

`void incr(int &val, mutex& m,  char desc)`
`{`
    `for(int i = 0; i < 5; i++)`
    `{`
        `m.lock();`
        `++val;`
        `cout << desc << " " << val << endl;`
        `m.unlock();`
        `dosom(1);`
    `}`
`}`
`void consumeXY()`
`{`
    `int cnt = 5;`
    `while(cnt)`
    `{`
        `if(try_lock(m1, m2) == -1)`
        `{`
	            // operations
		        $m1.unlock();$
			    $m2.unlock();$
        `}`
    `}`
`}`
`int32_t main()`
`{`
    `ios_base::sync_with_stdio(false);`
    `cin.tie(NULL);`
    `thread t1(incr, ref(X), ref(m1), 'X');`
    `thread t2(incr, ref(Y), ref(m2), 'Y');`
    `t1.join();`
    `t2.join();`
`}`

