
# Basic Data Types in TypeScript

---

## **Objective:**
Understand and use TypeScript's basic data types to declare variables, enhance code reliability, and prevent runtime errors.

---

## **1. Primitive Data Types**
### **1.1. `string`**
- Represents text data.
- Declared with single (`'`) or double (`"`) quotes or backticks (`` ` ``).

**Example:**
```typescript
let firstName: string = "John";
let greeting: string = `Hello, ${firstName}`;
```

### **1.2. `number`**
- Represents numeric values (integers, floats, hex, binary, or octal).

**Example:**
```typescript
let age: number = 30;
let hex: number = 0xf00d; // hexadecimal
let binary: number = 0b1010; // binary
```

### **1.3. `boolean`**
- Represents a true or false value.

**Example:**
```typescript
let isActive: boolean = true;
let hasAccess: boolean = false;
```

### **1.4. `null` and `undefined`**
- `null`: Represents the intentional absence of value.
- `undefined`: Represents a variable that has been declared but not yet assigned a value.

**Example:**
```typescript
let value: null = null;
let notAssigned: undefined = undefined;
```

---

## **2. Complex Data Types**
### **2.1. `array`**
- Represents a collection of elements of the same type.
- Declared using `type[]` or `Array<type>` syntax.

**Example:**
```typescript
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];
```

### **2.2. `tuple`**
- Represents a fixed-length array with specific types for each element.

**Example:**
```typescript
let person: [string, number] = ["John", 30]; // [string, number]
```

### **2.3. `enum`**
- Represents a set of named constants, often used for fixed options.

**Example:**
```typescript
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT"
}

let move: Direction = Direction.Up;
```

---

## **3. Special Types**
### **3.1. `any`**
- Disables type checking, allowing any value to be assigned.
- Use sparingly to avoid losing type safety.

**Example:**
```typescript
let randomValue: any = "Hello";
randomValue = 42; // Valid
```

### **3.2. `unknown`**
- Represents a variable whose type is not known.
- Safer than `any` as it requires type checking before usage.

**Example:**
```typescript
let input: unknown = "A string";
if (typeof input === "string") {
  console.log(input.toUpperCase());
}
```

---

## **4. Using Basic Data Types in Functions**
- Type annotations can be used for function parameters and return types.

**Example:**
```typescript
function add(a: number, b: number): number {
  return a + b;
}

let result: number = add(5, 10); // Valid
```

---

## **5. Type Inference**
- TypeScript can infer the type of a variable based on its initial value.

**Example:**
```typescript
let inferredString = "TypeScript"; // Type inferred as string
let inferredNumber = 42; // Type inferred as number
```

---

## **Practice Exercises**
1. Declare variables using each basic data type (`string`, `number`, `boolean`, etc.).
2. Create an `enum` for the days of the week and assign it to a variable.
3. Write a function that accepts an array of numbers and returns the sum.
4. Use `tuple` to represent a book with title (string), pages (number), and isPublished (boolean).

---

Mastering these basic data types is the foundation for leveraging TypeScript's type system to write reliable, maintainable, and scalable code.
