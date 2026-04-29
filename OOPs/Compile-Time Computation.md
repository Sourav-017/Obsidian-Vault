### `constexpr`

Means: _“evaluate at compile time if possible”_

```
constexpr int square(int x) {  
    return x * x;  
}

Usage:

constexpr int a = square(5); // compile-time  
int x;  
cin >> x;  
int b = square(x);          // runtime
```

### Key idea:

- Not guaranteed compile-time always
- Just _eligible for compile-time evaluation_