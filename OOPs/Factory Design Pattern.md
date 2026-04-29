The **Factory Method Pattern** defines an interface for creating an object, but lets **subclasses decide which class to instantiate**.

It shifts object creation from direct construction (`new`) to a **polymorphic method**.

---

### Core Idea

Instead of:

```
Product* p = new ConcreteProduct();
```

You do:

- Ask a “creator” class
- Let subclasses decide what to return

---

### Structure

- **Product** → common interface
- **ConcreteProduct** → actual implementations
- **Creator (abstract)** → declares factory method
- **ConcreteCreator** → overrides factory method

---

### C++ Example

```
#include <iostream>  
using namespace std;  
  
class Product {  
public:  
    virtual void use() = 0;  
    virtual ~Product() {}  
};  
  
class ConcreteProductA : public Product {  
public:  
    void use() override {  
        cout << "Using Product A\n";  
    }  
};  
  
class ConcreteProductB : public Product {  
public:  
    void use() override {  
        cout << "Using Product B\n";  
    }  
};
```

### Creator

```
class Creator {  
`public:  
    virtual Product* factoryMethod() = 0;  
  
    void operation() {  
        Product* p = factoryMethod();  
        p->use();  
        delete p;  
    }  
  
    virtual ~Creator() {}  
};`
```

### Concrete Creators

```
class CreatorA : public Creator {  
public:  
    Product* factoryMethod() override {  
        return new ConcreteProductA();  
    }  
};  
  
class CreatorB : public Creator {  
public:  
    Product* factoryMethod() override {  
        return new ConcreteProductB();  
    }  
};
```

### Usage

```
int main() {  
    Creator* c = new CreatorA();  
    c->operation();  
  
    delete c;  
}
```

---

### What is happening?

- Client calls `operation()`
- `operation()` calls `factoryMethod()`
- Subclass decides which object is created

This is **runtime object creation polymorphism**.

---

### Why not just use `new` directly?

Bad design:

```
if (type == "A") new A();  
else new B();
```

Problems:

- Violates Open/Closed Principle
- Hard to extend
- Tight coupling to concrete classes

Factory Method fixes this.

---

### When to use

- Object creation logic is **uncertain or variable**
- You want to **decouple creation from usage**
- You expect new product types in future