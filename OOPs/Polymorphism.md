### 1. **What is Function Overloading?**

**Solution:** Function overloading allows multiple functions with the same name but different parameters in the same scope.

```
class Printer {
public:
    void print(int i) { std::cout << "Printing int: " << i << std::endl; }
    void print(double d) { std::cout << "Printing double: " << d << std::endl; }
};
```

### 2. **What is Operator Overloading and provide an example**

**Solution:** Operator overloading allows custom behavior for C++ operators in user-defined classes.

```
class Complex {
    int real, imag;
public:
    Complex(int r, int i) : real(r), imag(i) {}
    Complex operator+(const Complex& other) {
        return Complex(real + other.real, imag + other.imag);
    }
};
```

**Explanation:** Overloading the `+` operator allows adding two `Complex` objects, enhancing readability.
### 3. **What is the difference between Function Overloading and Overriding?**

**Solution:**

- **Overloading:** Same function name with different parameters in the same class.
- **Overriding:** Derived class provides a specific implementation of a function already defined in the base class.

### 4. **How does C++ achieve Run-Time Polymorphism?**

**Solution:** Run-time polymorphism is achieved using **virtual functions** and **pointers or references** to base classes.

```
class Animal {
public:
    virtual void sound() { std::cout << "Animal sound" << std::endl; }
};
class Cat : public Animal {
public:
    void sound() override { std::cout << "Cat meows" << std::endl; }
};
Animal* animal = new Cat();
animal->sound();  // Output: Cat meows
```

**Explanation:** Here, `sound()` is resolved at runtime based on the actual object type, enabling run-time polymorphism.
#### Without `virtual`

- Decision is made at **compile time**
- Based on pointer type (`Animal*`)
- This is **static binding**
#### With `virtual`

- Decision is made at **runtime**
- Based on actual object (`Cat`)
- This is **dynamic dispatch**
### 5. **What is the `final` keyword in C++?**
 The `final` keyword prevents further inheritance or function overriding.

```
class Base {
public:
    virtual void show() final { std::cout << "Base show" << std::endl; }
};
class Derived final : public Base {
	cant override show(){
	}
};  // Cannot inherit from Derived
```

**Explanation:** Marking classes or methods as `final` enforces immutability in design, making the code easier to understand and safer from unintended modifications.
### 6. **Can you access a Private member of a class outside the class in C++? How?**

**Solution:** While private members are inaccessible directly, they can be accessed using:

1. **Friend Functions:** Functions declared as `friend` inside the class.
2. **Access Functions (Getters/Setters):** Public methods that provide controlled access.

Example with a friend function:

```
class Box {
private:
    int width;
    friend void printWidth(Box&);  // Friend function
};
void printWidth(Box& b) {
    std::cout << "Width: " << b.width << std::endl;
}
```