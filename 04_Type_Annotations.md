
# Type Annotations in TypeScript

---

## **Objective:**
Learn how to use type annotations in TypeScript to specify variable types, function parameters, and return values to create more reliable and maintainable code.

---

## **1. What are Type Annotations?**
- Type annotations explicitly specify the type of a variable, function parameter, or return value.
- They help catch errors during development and improve code readability.

**Example:**
```typescript
let age: number = 25;
```

---

## **2. Adding Type Annotations to Variables**
- Type annotations are added using the colon (`:`) followed by the type.

**Examples:**
```typescript
let name: string = "Alice";
let isStudent: boolean = true;
let grades: number[] = [90, 85, 88];
```

---

## **3. Type Annotations in Functions**
### **3.1. Function Parameters**
- Use type annotations to specify the types of function parameters.

**Example:**
```typescript
function greet(name: string): void {
  console.log(`Hello, ${name}!`);
}
```

### **3.2. Function Return Types**
- Specify the return type of a function after the parameter list.

**Example:**
```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

### **3.3. Optional Parameters**
- Mark a parameter as optional by adding a `?` after its name.

**Example:**
```typescript
function displayMessage(message: string, sender?: string): void {
  if (sender) {
    console.log(`${sender}: ${message}`);
  } else {
    console.log(message);
  }
}
```

### **3.4. Default Parameters**
- Assign a default value to a parameter.

**Example:**
```typescript
function multiply(a: number, b: number = 1): number {
  return a * b;
}
```

---

## **4. Type Annotations in Arrays and Objects**
### **4.1. Arrays**
- Annotate arrays using `type[]` or `Array<type>`.

**Example:**
```typescript
let fruits: string[] = ["apple", "banana", "cherry"];
let numbers: Array<number> = [1, 2, 3];
```

### **4.2. Objects**
- Use inline type annotations or interfaces to annotate objects.

**Example (Inline):**
```typescript
let user: { name: string; age: number } = { name: "John", age: 30 };
```

**Example (Interface):**
```typescript
interface User {
  name: string;
  age: number;
}

let admin: User = { name: "Alice", age: 25 };
```

---

## **5. Using Type Annotations with Complex Data**
### **5.1. Union Types**
- Allow variables to hold values of multiple types.

**Example:**
```typescript
let id: string | number = "123";
id = 456; // Also valid
```

### **5.2. Literal Types**
- Specify exact values that a variable can hold.

**Example:**
```typescript
let direction: "up" | "down" | "left" | "right" = "up";
```

---

## **6. Type Assertions**
- Convert a variable to a specific type when TypeScript cannot infer it.

**Example:**
```typescript
let input: any = "This is a string";
let length: number = (input as string).length;
```

---

## **7. Type Annotations in Practice**
### **7.1. Function Overloading**
- Define multiple function signatures with different parameter types.

**Example:**
```typescript
function format(input: string): string;
function format(input: number): string;
function format(input: string | number): string {
  return input.toString();
}
```

### **7.2. API Response Handling**
- Use type annotations to define the structure of API responses.

**Example:**
```typescript
interface ApiResponse {
  success: boolean;
  data: { id: number; name: string };
}

let response: ApiResponse = {
  success: true,
  data: { id: 1, name: "John" },
};
```

---

## **Practice Exercises**
1. Write a function that takes a name (`string`) and age (`number`) as parameters and returns a greeting message.
2. Create an array of objects representing students with properties: `name` (string) and `grade` (number).
3. Define a union type for a variable that can either hold a `string` or a `boolean`.
4. Use type annotations to write a function that calculates the area of a rectangle, with optional height parameter.

---

Type annotations make your code predictable, easier to debug, and more maintainable. Use them extensively for variables, functions, and data structures to unleash TypeScript's full potential.
