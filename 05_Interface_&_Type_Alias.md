
# Interface & Type Alias in TypeScript

---

## **Objective:**
Understand how to use `interface` and `type` in TypeScript to define the shape of objects, enforce structure, and build flexible data models.

---

## **1. What is an Interface?**
- An `interface` in TypeScript defines the shape of an object.
- It is used to describe properties and methods an object must have.

**Example:**
```typescript
interface User {
  name: string;
  age: number;
  isAdmin: boolean;
}

let user: User = {
  name: "Alice",
  age: 25,
  isAdmin: true,
};
```

---

## **2. What is a Type Alias?**
- A `type` defines a custom name for any type, including primitive types, unions, or more complex structures.

**Example:**
```typescript
type Point = {
  x: number;
  y: number;
};

let coordinates: Point = { x: 10, y: 20 };
```

---

## **3. Key Differences Between Interface and Type**
| Feature               | Interface                         | Type Alias                   |
|-----------------------|------------------------------------|-----------------------------|
| Object Shape          | Defines object structure.         | Defines object structure.   |
| Extensibility         | Can be extended or implemented.   | Cannot be extended.         |
| Union Types           | Not supported.                   | Supported.                  |
| Declaration Merging   | Supported.                        | Not supported.              |

---

## **4. Advanced Usage of Interface**
### **4.1. Optional Properties**
- Use `?` to define optional properties.

**Example:**
```typescript
interface Car {
  brand: string;
  model?: string; // Optional
}

let myCar: Car = { brand: "Toyota" };
```

### **4.2. Readonly Properties**
- Use `readonly` to make a property immutable.

**Example:**
```typescript
interface Book {
  readonly title: string;
  pages: number;
}

let myBook: Book = { title: "1984", pages: 328 };
// myBook.title = "New Title"; // Error
```

### **4.3. Extending Interfaces**
- Extend existing interfaces to add more properties.

**Example:**
```typescript
interface Person {
  name: string;
}

interface Employee extends Person {
  employeeId: number;
}

let emp: Employee = { name: "John", employeeId: 123 };
```

### **4.4. Interfaces with Methods**
- Define methods inside an interface.

**Example:**
```typescript
interface Greeter {
  greet(): string;
}

let greeter: Greeter = {
  greet: () => "Hello, world!",
};
```

---

## **5. Advanced Usage of Type Alias**
### **5.1. Union and Intersection Types**
- Use `type` to define unions or intersections.

**Example (Union):**
```typescript
type ID = string | number;

let userId: ID = 101; // Can be string or number
```

**Example (Intersection):**
```typescript
type Position = { x: number; y: number };
type Size = { width: number; height: number };

type Rectangle = Position & Size;

let rect: Rectangle = { x: 10, y: 20, width: 30, height: 40 };
```

### **5.2. Using Type for Function Signatures**
- Define reusable function types.

**Example:**
```typescript
type Add = (a: number, b: number) => number;

let addNumbers: Add = (a, b) => a + b;
```

### **5.3. Using Type for Tuples**
- Create fixed-length arrays with specific types.

**Example:**
```typescript
type Point = [number, number];

let point: Point = [10, 20];
```

---

## **6. When to Use Interface or Type Alias**
- **Use `interface`** when defining objects, especially when extending or merging is needed.
- **Use `type`** for complex structures like unions, intersections, or custom function signatures.

---

## **7. Combining Interface and Type Alias**
- You can use both together for different use cases.

**Example:**
```typescript
interface Shape {
  color: string;
}

type Dimensions = {
  width: number;
  height: number;
};

type Rectangle = Shape & Dimensions;

let box: Rectangle = { color: "blue", width: 20, height: 15 };
```

---

## **Practice Exercises**
1. Define an `interface` for a `Student` object with properties: `name` (string), `age` (number), and `isGraduated` (boolean).
2. Create a `type` for a `Coordinate` object with `x` and `y` properties.
3. Extend an `interface` for an `Employee` to include an optional `department` (string).
4. Use `type` to create a union of `string` and `number` and use it to define an `ID` type.

---

Understanding and mastering `interface` and `type alias` enables you to build flexible, reusable, and type-safe structures in TypeScript.
