
# 1. `std::unique_ptr` — **exclusive ownership**

### Core idea

> Exactly **one owner** of a resource.

### Properties

- Cannot be copied
- Can be moved
- Deletes object when it goes out of scope

### Example

```
std::unique_ptr<int> p1 = std::make_unique<int>(10);  
  
// std::unique_ptr<int> p2 = p1; ❌ error (no copy)  
  
std::unique_ptr<int> p2 = std::move(p1); // ownership transferred
```

### Use when

- You want strict ownership
- No sharing allowed
- Fastest (no overhead)