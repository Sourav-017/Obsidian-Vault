[[Threading]] [[Multi Threading]] [[MUTEX And Race condition]]


It's Clear from the name that the `try_lock_for(time)`  function will try to lock a **timed_mutex** object for a given amount of time
We tell the timeout period
`std::timed_mutex m`
`if(m.try_lock_for(chrono::seconds(1)))` 
{
	
}

**Recursive Mutex:** `std::recursive_mutex m`
can m be recursively locked multiple times but need to unlock it each time.
