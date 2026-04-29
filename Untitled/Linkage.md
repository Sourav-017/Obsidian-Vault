# Internal vs External Linkage

| Feature                 | Internal Linkage                                  | External Linkage                        |
| ----------------------- | ------------------------------------------------- | --------------------------------------- |
| **Visibility**          | Only inside one `.cpp` file (translation unit)    | Visible across multiple `.cpp` files    |
| **Scope across files**  | Not accessible from other files                   | Accessible from other files via linking |
| **Default for globals** | Only if marked `static` or in anonymous namespace | Default for global variables/functions  |
| **How to declare**      | `static`, or `namespace {}`                       | Default, or `extern` for declaration    |
| **Linker behavior**     | Symbol is private to that file                    | Symbol is shared and resolved by linker |
| **Use case**            | Hide implementation details per file              | Share variables/functions across files  |
| **Risk of collision**   | None (isolated per file)                          | Possible ODR/linker errors if misused   |
| **Example**             | `static int x;`                                   | `int x;` + `extern int x;`              |

## Code illustration

### Internal linkage

```
// file1.cpp  
static int x = 10;  // only inside file1.cpp  
  
namespace {  
    void helper() {}  
}
```
### External linkage

```
// file1.cpp  
int x = 10;  // shared symbol  
  
void show() {}

// file2.cpp  
extern int x;  
  
int main() {  
    std::cout << x;  
}
```