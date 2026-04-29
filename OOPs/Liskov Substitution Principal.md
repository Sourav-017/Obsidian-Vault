1. **Liskov Substitution Principle:** Objects of a derived class should behave like their base class.
```
class Bird {
public:
    virtual void fly() { std::cout << "Flying" << std::endl; }
};
class Sparrow : public Bird {};
Bird* bird = new Sparrow();
bird->fly();  // Correct behavior
```