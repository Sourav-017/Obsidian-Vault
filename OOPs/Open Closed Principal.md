**Open/Closed Principle:** Classes should be open for extension, but closed for modification.  
    Example using inheritance:
    
    ```
    class Shape {
    public:
        virtual double area() const = 0;
    };
    
    class Circle : public Shape {
        double radius;
    public:
        Circle(double r) : radius(r) {}
        double area() const override { return 3.14 * radius * radius; }
    };
    ```