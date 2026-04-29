Observer
# `std::weak_ptr` — **non-owning observer**

### Core idea

> Observes a `shared_ptr` without increasing reference count.

### Properties

- Does NOT keep object alive
- Must be converted to `shared_ptr` using `lock()`

### Example

```
std::shared_ptr<int> sp = std::make_shared<int>(10);  
std::weak_ptr<int> wp = sp;  
  
if (auto temp = wp.lock()) {  
    std::cout << *temp;  
}
```

---

# 4. Why `weak_ptr` exists (critical concept)

### Problem: cyclic reference

```
struct A;  
struct B;  
  
struct A {  
    std::shared_ptr<B> b;  
};  
  
struct B {  
    std::shared_ptr<A> a;  
};
```
- A owns B
- B owns A  
    → reference count never becomes 0  
    → **memory leak**

### Fix

```
struct B {  
    std::weak_ptr<A> a;  // breaks cycle  
};
```