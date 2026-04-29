- **lvalue** → has identity (persistent object, addressable)
- **rvalue** → temporary value (no stable identity)
`&&` defines an **rvalue reference**.
---

## Fast classification rule

Ask:

> Can I take its address or assign to it?

- Yes → **lvalue**
- No → **rvalue**

---

## Basic examples

```
int x = 5;x        // lvalue
(x)      // lvalue
x + 1    // rvalue
5        // rvalue
```

---

## Assignment behavior

```
x = 10;        // OK
(x + 1) = 10;  // ❌ rvalue
(x = 10);      // lvalue
(x = 10) = 20; // valid
```

---

## References

```
int x = 5;
int& a = x;   // OK (lvalue ref)
int& b = 10;  // ❌
int&& c = 10; // OK (rvalue ref) && means rvalue reference
int&& d = x;  // ❌
```

---

## Functions

### Function name

```
foo        // lvalue
```

### Function call

```
int foo();        // returns value → rvalue
int& bar(int&);  // returns reference → lvalue
foo()   // rvaluebar(x)  // lvalue
```

---

## Operators returning lvalues

```
v[i]        // lvalue 
(if returns T&)*ptr        // lvalue
x = y       // lvalue
++x         // lvalue
```

---

## Operators returning rvalues

```
x + y       // rvalue
x++         // rvalue
foo()       // rvalue 
(if return by value)
```

---

## Move semantics (key idea)

```
std::move(x)
```

- Casts **lvalue → rvalue**
- Enables move instead of copy
- Does NOT move anything by itself