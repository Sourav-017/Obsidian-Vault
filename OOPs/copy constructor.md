### **Deep vs. Shallow Copy in C++**

- **Shallow Copy:** Only copies pointers, not actual data.
- **Deep Copy:** Allocates new memory for copies of all objects.

```
class MyClass {
    int* data;
public:
    MyClass(int value) { data = new int(value); }
    MyClass(const MyClass& other) { data = new int(*other.data); } // Deep Copy
};
```