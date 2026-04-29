1. **Encapsulation**: Encapsulation bundles data and methods into a single unit, usually a class, restricting access to its internal data and allowing controlled interaction.
	```
	class Car {
	private:
	int speed;  // Encapsulated data
	public:
	void setSpeed(int s) { speed = s; }
	int getSpeed() const { return speed; }
	};
	```
2. **Abstraction**: Abstraction hides complex details and shows only the essential parts of an object to simplify usage.
```
class Car {
public:
virtual void start() = 0;  // Abstract method
};
```
3. [[Inheritence]]:  Inheritance allows a new class to acquire properties and behavior from an existing class, forming an "is-a" relationship.
	```
	class Vehicle {};
	class Car : public Vehicle {};
	```

4. [[Polymorphism]]: Polymorphism enables a single interface to represent different types achieved through function overloading and overriding.
```
class Animal {
public:
    virtual void makeSound() { std::cout << "Animal sound" << std::endl; }
};
class Dog : public Animal {
public:
    void makeSound() override { std::cout << "Dog barks" << std::endl; }
};
```
