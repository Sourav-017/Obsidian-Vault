**Dependency Inversion Principle:** Depend on abstractions, not on concrete implementations.4
``Stopping high-level logic from breaking every time low-level implementation changes.
==High-level logic should not be rewritten when low-level implementation changes.==

```
class IService {
public:
    virtual void serve() = 0;
};

class Service : public IService {
public:
    void serve() override { std::cout << "Service" << std::endl; }
};

class Client {
    IService* service;
public:
    Client(IService* srv) : service(srv) {}
    void doWork() { service->serve(); }
};


```
#### Real-world scenario: switching database logic

Imagine `serve()` is actually:

```
class Database {  
public:  
    virtual void query() = 0;  
};
```

#### MySQL version

```
class MySQL : public Database {  
public:  
    void query() override {  
        std::cout << "Querying MySQL\n";  
    }  
};
```

#### MongoDB version

```
class MongoDB : public Database {  
public:  
    void query() override {  
        std::cout << "Querying MongoDB\n";  
    }  
};
```

#### Business logic

```
class ReportService {  
    Database& db;  
public:  
    ReportService(Database& db) : db(db) {}  
  
    void generateReport() {  
        db.query();  
    }  
};
```

---

### Without DIP 

```
class ReportService {  
    MySQL db;  // hardcoded dependency  
};
```

Now change DB → you must rewrite ReportService.