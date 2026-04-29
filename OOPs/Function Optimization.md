## **Inline Expansion**

- **Definition**: The inline keyword suggests to the compiler that a function's code should be expanded in-line where it's called, to avoid the overhead of a function call.

```
inline int add(int a, int b) {
    return a + b;
}
```