### Definition

A **mixin** is a small class designed to **add reusable behavior** to other classes via inheritance, without representing a standalone “is-a” type.

It is used to **inject functionality**, not define identity.

---

### Core Idea

- Base class → defines _what the object is_
- Mixin → defines _what the object can do_

Mixins are meant to be **combined**, not used alone.

---

### C++ Example

```
class LoggerMixin {  
public:  
    void log(const string& msg) {  
        cout << "[LOG] " << msg << endl;  
    }  
};  
  
class File {  
public:  
    void open() {  
        cout << "File opened\n";  
    }  
};  
  
class FileWithLogging : public File, public LoggerMixin {};

Usage:

FileWithLogging f;  
f.open();  
f.log("operation done");
```

---

### Why Mixins Exist

Without mixins:
```
LoggedFile  
LoggedSocket  
LoggedDatabase
```

→ duplicated logging logic everywhere

With mixins:
```
File + LoggerMixin  
Socket + LoggerMixin  
Database + LoggerMixin
```

→ reusable behavior

---

### Key Properties

- Small and focused responsibility
- Not meant to be instantiated alone
- Adds capability, not identity
- Used via **multiple inheritance**
- No strong dependency on derived class state (ideally)