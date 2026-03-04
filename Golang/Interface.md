[[GOLANG]]

A set of method signatures
```
type Shape interface {
    Area() float64
    Perimeter() float64
}

```
```
type Circle struct {
    Radius float64
}

func (c Circle) Area() float64 {
    return 3.14 * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
    return 2 * 3.14 * c.Radius
}

var s Shape = Circle{Radius: 5}  // Circle satisfies Shape interface
fmt.Println(s.Area())             // works
```
