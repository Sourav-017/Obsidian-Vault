- **Inheritance:** Defines an "is-a" relationship.
    
    ```
    class Vehicle {};
    class Car : public Vehicle {};
    ```
    
- **Composition:** Defines a "has-a" relationship.
    
    ```
    class Engine {};
    class Car {
        Engine engine; // Composition
    };
    ```
    