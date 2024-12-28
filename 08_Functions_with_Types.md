
# Functions with Types in TypeScript

---

## **Objective:**
Learn how to add type annotations to functions, define optional and default parameters, and implement function overloading for better type safety and maintainability in TypeScript.

---

## **1. Adding Type Annotations to Functions**
- Type annotations can be added to function parameters and return types.
- Syntax: `(parameterName: type) => returnType`

**Example:**
```typescript
function add(a: number, b: number): number {
  return a + b;
}

let result: number = add(5, 10); // Valid
// add(5, "10"); // Error: Argument of type 'string' is not assignable to parameter of type 'number'
```

---

## **2. Functions with Optional Parameters**
- Use `?` to mark a parameter as optional.
- Optional parameters default to `undefined` if not provided.

**Example:**
```typescript
function greet(name: string, age?: number): string {
  return age
    ? `Hello, ${name}. You are ${age} years old.`
    : `Hello, ${name}.`;
}

console.log(greet("Alice")); // "Hello, Alice."
console.log(greet("Bob", 30)); // "Hello, Bob. You are 30 years old."
```

---

## **3. Functions with Default Parameters**
- Assign a default value to a parameter.
- Default parameters are used when no value or `undefined` is passed.

**Example:**
```typescript
function multiply(a: number, b: number = 1): number {
  return a * b;
}

console.log(multiply(5)); // 5 (uses default value for b)
console.log(multiply(5, 3)); // 15
```

---

## **4. Void and Never Return Types**
### **4.1. Void**
- Indicates that a function does not return a value.

**Example:**
```typescript
function logMessage(message: string): void {
  console.log(message);
}
```

### **4.2. Never**
- Indicates a function that never returns (e.g., it throws an error or enters an infinite loop).

**Example:**
```typescript
function throwError(message: string): never {
  throw new Error(message);
}
```

---

## **5. Function Overloading**
- Define multiple function signatures with different parameter types.
- A single implementation handles all cases.

**Example:**
```typescript
function format(input: string): string;
function format(input: number): string;
function format(input: string | number): string {
  return input.toString();
}

console.log(format("Hello")); // "Hello"
console.log(format(123)); // "123"
```

---

## **6. Functions with Rest Parameters**
- Use the rest parameter syntax (`...args`) to handle multiple arguments.

**Example:**
```typescript
function sum(...numbers: number[]): number {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4)); // 10
```

---

## **7. Arrow Functions with Types**
- Use arrow functions with type annotations for concise syntax.

**Example:**
```typescript
const subtract = (a: number, b: number): number => a - b;

console.log(subtract(10, 5)); // 5
```

---

## **8. Callback Functions**
- Type annotations can be applied to callback functions.

**Example:**
```typescript
function processNumbers(
  numbers: number[],
  callback: (num: number) => number
): number[] {
  return numbers.map(callback);
}

const doubled = processNumbers([1, 2, 3], (num) => num * 2);
console.log(doubled); // [2, 4, 6]
```

---

## **Practice Exercises**
1. Write a function that accepts two numbers and returns their difference. Add appropriate type annotations.
2. Create a function with a default parameter for greeting someone in a specific language (e.g., "Hello" by default).
3. Implement a function that uses `rest parameters` to calculate the average of multiple numbers.
4. Write a function with overloading to format a `Date` object or a timestamp (number) as a string.

---

Understanding how to use functions with types in TypeScript helps you write safer, more predictable, and reusable code.
