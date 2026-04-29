**Interface Segregation Principle:** Don’t force clients to implement unnecessary methods.

 **Bad design (violates ISP)**
```
class Worker {  
public:  
    virtual void work() = 0;  
    virtual void eat() = 0;  
};

// Now every worker must implement both:

class Robot : public Worker {  
public:  
    void work() override { /* ok */ }  
  
    void eat() override {  // nonsense  
        throw "Robots don't eat";  
    }  
};
```

This is bad design:

- Robot is forced to implement irrelevant behavior
- leads to dummy code or exceptions

**Correct design (ISP applied)**

Split interfaces:

```
class Workable {  
public:  
    virtual void work() = 0;  
};  
  
class Eatable {  
public:  
    virtual void eat() = 0;  
};
```

Now:
```
class Human : public Workable, public Eatable {  
public:  
    void work() override {}  
    void eat() override {}  
};  
  
class Robot : public Workable {  
public:  
    void work() override {}  
};
```
