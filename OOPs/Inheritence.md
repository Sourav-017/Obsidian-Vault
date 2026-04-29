==**Inheritence**==:  Inheritance allows a new class to acquire properties and behavior from an existing class, forming an "is-a" relationship.
	
	```
	class Vehicle {};
	class Car : public Vehicle {};
	```
	
**Multiple Inheritence:** ```
class C : public A, public B {};  // Multiple Inheritance```

**Diamond Problem in Multiple Inheritence:** **:** The diamond problem occurs when a class inherits from two classes that have a common base class, causing ambiguity

**Example**:
```
class A {
public:
    void f() { cout << "A\n"; }
};

class B : public A {
public:
    void f() { cout << "B\n"; }
};

class C : public A {
public:
    void f() { cout << "C\n"; }
};

class D : public B, public C {};

D d;
d.f(); // ERROR: ambiguous
```
**Solution**:  
Explicit Call:
```
d.B::f();  // prints B
d.C::f();  // prints C
```
**Way2:```
```**class A {
public:
    void show() { std::cout << "Class A" << std::endl; }
};
class B : virtual public A {};
class C : virtual public A {};
class D : public B, public C {};  // Diamond Problem solved with virtual inheritance
```