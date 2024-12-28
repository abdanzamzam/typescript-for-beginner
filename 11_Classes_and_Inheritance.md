
# Classes and Inheritance in TypeScript

---

## **Objective:**
Learn how to use TypeScript classes to define objects with properties and methods, and understand how to implement inheritance for code reuse and polymorphism.

---

## **1. What is a Class?**
- A class is a blueprint for creating objects with properties and methods.
- Syntax: `class ClassName { }`

**Example:**
```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): string {
    return `Hello, my name is ${this.name}`;
  }
}

let person = new Person("Alice", 30);
console.log(person.greet()); // "Hello, my name is Alice"
```

---

## **2. Class Properties**
- Class properties can have type annotations.
- Properties can be public, private, or protected.

### **2.1. Public Properties**
- Accessible from anywhere.

**Example:**
```typescript
class Car {
  public brand: string;

  constructor(brand: string) {
    this.brand = brand;
  }
}

let car = new Car("Toyota");
console.log(car.brand); // "Toyota"
```

### **2.2. Private Properties**
- Accessible only within the class.

**Example:**
```typescript
class BankAccount {
  private balance: number;

  constructor(balance: number) {
    this.balance = balance;
  }

  getBalance(): number {
    return this.balance;
  }
}

let account = new BankAccount(1000);
console.log(account.getBalance()); // 1000
// console.log(account.balance); // Error: Property 'balance' is private
```

### **2.3. Protected Properties**
- Accessible within the class and its subclasses.

**Example:**
```typescript
class Animal {
  protected species: string;

  constructor(species: string) {
    this.species = species;
  }

  getSpecies(): string {
    return this.species;
  }
}

class Dog extends Animal {
  constructor() {
    super("Dog");
  }

  bark(): string {
    return `The ${this.species} barks!`;
  }
}

let dog = new Dog();
console.log(dog.bark()); // "The Dog barks!"
```

---

## **3. Inheritance**
- A class can extend another class to inherit its properties and methods.

**Example:**
```typescript
class Vehicle {
  brand: string;

  constructor(brand: string) {
    this.brand = brand;
  }

  move(): string {
    return `${this.brand} is moving`;
  }
}

class Car extends Vehicle {
  wheels: number;

  constructor(brand: string, wheels: number) {
    super(brand); // Call the parent class constructor
    this.wheels = wheels;
  }

  drive(): string {
    return `${this.brand} with ${this.wheels} wheels is driving`;
  }
}

let car = new Car("Toyota", 4);
console.log(car.drive()); // "Toyota with 4 wheels is driving"
```

---

## **4. Method Overriding**
- Subclasses can override methods from the parent class.

**Example:**
```typescript
class Animal {
  sound(): string {
    return "Some generic sound";
  }
}

class Cat extends Animal {
  sound(): string {
    return "Meow";
  }
}

let cat = new Cat();
console.log(cat.sound()); // "Meow"
```

---

## **5. Static Properties and Methods**
- Static members belong to the class itself, not instances.

**Example:**
```typescript
class MathUtils {
  static PI = 3.14;

  static calculateCircleArea(radius: number): number {
    return this.PI * radius * radius;
  }
}

console.log(MathUtils.PI); // 3.14
console.log(MathUtils.calculateCircleArea(10)); // 314
```

---

## **6. Abstract Classes**
- Abstract classes define a base class that cannot be instantiated directly.
- They can include abstract methods that must be implemented in subclasses.

**Example:**
```typescript
abstract class Shape {
  abstract getArea(): number;

  describe(): string {
    return "This is a shape";
  }
}

class Circle extends Shape {
  radius: number;

  constructor(radius: number) {
    super();
    this.radius = radius;
  }

  getArea(): number {
    return Math.PI * this.radius ** 2;
  }
}

let circle = new Circle(10);
console.log(circle.getArea()); // 314.1592653589793
```

---

## **7. Polymorphism**
- Subclasses can provide specific implementations for methods, allowing dynamic behavior.

**Example:**
```typescript
class Bird {
  fly(): string {
    return "The bird is flying";
  }
}

class Penguin extends Bird {
  fly(): string {
    return "Penguins can't fly!";
  }
}

let bird: Bird = new Bird();
let penguin: Bird = new Penguin();

console.log(bird.fly()); // "The bird is flying"
console.log(penguin.fly()); // "Penguins can't fly!"
```

---

## **8. Practice Exercises**
1. Create a `Student` class with `name` and `grade` properties. Add a method to display a student's details.
2. Extend the `Student` class to create a `GraduateStudent` class with an additional property, `thesisTitle`.
3. Implement a `Vehicle` class with `start()` and `stop()` methods. Extend it to create a `Motorcycle` class with an additional method `revEngine()`.
4. Write an abstract class `Appliance` with an abstract method `turnOn()` and a concrete method `getPowerSource()`.

---

TypeScript's classes and inheritance provide robust tools for object-oriented programming. They help you structure your code in a maintainable and reusable way.
