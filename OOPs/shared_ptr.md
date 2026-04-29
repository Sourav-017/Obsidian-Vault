# `std::shared_ptr` — **shared ownership**

### Core idea

> Multiple pointers can own the same resource.

### Properties

- Uses **reference counting**
- Object deleted when count becomes 0

### Example

std::shared_ptr<int> p1 = std::make_shared<int>(10);  
std::shared_ptr<int> p2 = p1;  // count = 2

### Internal model

- Control block stores:
    - reference count
    - pointer to object

### Use when

- Multiple owners exist
- Lifetime is shared