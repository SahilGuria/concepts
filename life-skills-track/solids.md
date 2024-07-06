
# SOLID Principles in Object-Oriented Design

The SOLID principles are the kind of morals to achieve a good code in terms of extensible, Maintainable, Readable, Reusable, Modular.

1. **Single Responsibility Principle (SRP)**
2. **Open/Closed Principle (OCP)**
3. **Liskov Substitution Principle (LSP)**
4. **Interface Segregation Principle (ISP)**
5. **Dependency Inversion Principle (DIP)**

## 1. Single Responsibility Principle (SRP)

**Definition:**
Single Responsibility Principle says every code unit (Class, Method, Interface) should have a single responsibility.

**Explanation**
The Single Responsibility Principle is like, a class should only have one job. Yeah, you heard that right! A class should only be responsible for one thing. This helps us avoid the "God object" anti-pattern, where one class is trying to do too many things.

### How to identify violation:-
1. Too many if else conditions -> If if else conditions are part of logic algorithm then it is okay. 
2. Monster Method -> Method which has code that does more than what its name suggest.

**Example:**

```java
// Bad Example
class User {
    void getUserData() { ... }
    void saveUserData() { ... }
    void printUserData() { ... }
}

// Good Example
class UserData {
    void getUserData() { ... }
    void saveUserData() { ... }
}

class UserPrinter {
    void printUserData() { ... }
}
```

## 2. Open/Closed Principle (OCP)

**Definition:**
Our Codebase should be open for Extension closed for modification.

The Open/Closed Principle encourages developers to design software that can be extended without modifying existing code. This principle helps prevent breaking existing functionality when adding new features, leading to more stable and flexible systems.

**Explanation**
The Open-Closed Principle states that a class should be open for extension but closed for modification. This means that you should be able to add new functionality to a class without modifying its existing code.

**Example:**

```java
// Violation of OCP
class Rectangle {
    public double length;
    public double width;
}

class AreaCalculator {
    public double calculateArea(Rectangle rectangle) {
        return rectangle.length * rectangle.width;
    }
}

// Adhering to OCP
interface Shape {
    double calculateArea();
}

class Rectangle implements Shape {
    public double length;
    public double width;
    
    @Override
    public double calculateArea() {
        return length * width;
    }
}

class Circle implements Shape {
    public double radius;
    
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

class AreaCalculator {
    public double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}
```

## 3. Liskov Substitution Principle (LSP)

**Definition:**
Object of any child class should be as it is substituable in a variable of parent class reference without making any extra code changes or we can say no special to treatment to any child class.

**Explanation**
The Liskov Substitution Principle ensures that subclasses can stand in for their base classes without altering the desirable properties of a program. This principle promotes the correct use of inheritance and polymorphism, ensuring that derived classes extend base classes without changing their behavior.

```java
// Violation of LSP
class Bird {
    public void fly() {
        // Logic for flying
    }
}

class Ostrich extends Bird {
    @Override
    public void fly() {
        throw new UnsupportedOperationException("Ostriches can't fly");
    }
}

// Adhering to LSP
class Bird {
    public void move() {
        // Logic for general movement
    }
}

class FlyingBird extends Bird {
    public void fly() {
        // Logic for flying
    }
}

class Ostrich extends Bird {
    @Override
    public void move() {
        // Logic for walking
    }
}
```


## 4. Interface Segregation Principle (ISP)

**Definition:**
Interface Segregation Principle says ideally each interface should have a single method. Interfaces should be as light as possible. Clients should not be forced to depend on interfaces they do not use.

**Explanation**
The Interface Segregation Principle is like, clients shouldn't have to depend on interfaces they don't use. Yeah, it's like, if you have an interface with a bunch of methods, but a client only needs one or two of them, that's bad design.

**Example:**

```java
// Violation of ISP
interface Worker {
    void work();
    void eat();
}

class HumanWorker implements Worker {
    @Override
    public void work() {
        // Human working
    }

    @Override
    public void eat() {
        // Human eating
    }
}

class RobotWorker implements Worker {
    @Override
    public void work() {
        // Robot working
    }

    @Override
    public void eat() {
        // Robots don't eat, this method is unnecessary
    }
}

// Adhering to ISP
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class HumanWorker implements Workable, Eatable {
    @Override
    public void work() {
        // Human working
    }

    @Override
    public void eat() {
        // Human eating
    }
}

class RobotWorker implements Workable {
    @Override
    public void work() {
        // Robot working
    }
}

```


## 5. Dependency Inversion Principle (DIP)

**Definition:**
Dependency Inversion Principle says no two concrete classes should depend on each other directly they should depend on each other via an Interface.

**Explanation**
The Dependency Inversion Principle aims to reduce the coupling between high-level and low-level modules by introducing abstractions. By depending on abstractions, rather than concrete implementations, systems become more modular and easier to maintain and extend.

**Example:**

```java
// Violation of DIP
class LightBulb {
    public void turnOn() {
        // Logic to turn on the light bulb
    }

    public void turnOff() {
        // Logic to turn off the light bulb
    }
}

class Switch {
    private LightBulb lightBulb;

    public Switch(LightBulb lightBulb) {
        this.lightBulb = lightBulb;
    }

    public void operate() {
        // Logic to operate the switch
    }
}

// Adhering to DIP
interface Switchable {
    void turnOn();
    void turnOff();
}

class LightBulb implements Switchable {
    @Override
    public void turnOn() {
        // Logic to turn on the light bulb
    }

    @Override
    public void turnOff() {
        // Logic to turn off the light bulb
    }
}

class Switch {
    private Switchable device;

    public Switch(Switchable device) {
        this.device = device;
    }

    public void operate() {
        // Logic to operate the switch
    }
}

```



