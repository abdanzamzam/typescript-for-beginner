
# Generics in TypeScript

---

## **Objective:**
Understand how to use Generics in TypeScript to write reusable and type-safe functions, classes, and interfaces that work with a variety of types.

---

## **1. What are Generics?**
- Generics allow you to create reusable components that can work with a variety of types while maintaining type safety.
- Syntax: `<T>` (where `T` is a placeholder for a type).

**Example:**
```typescript
function identity<T>(value: T): T {
  return value;
}

let num = identity<number>(5); // Explicitly specifying type
let str = identity("Hello"); // Type inferred
```

---

## **2. Generic Functions**
- Use generics to create flexible functions.

**Example:**
```typescript
function reverseArray<T>(items: T[]): T[] {
  return items.reverse();
}

let numbers = reverseArray<number>([1, 2, 3]);
let strings = reverseArray<string>(["a", "b", "c"]);
```

---

## **3. Generic Classes**
- Use generics in classes to create flexible and reusable types.

**Example:**
```typescript
class Box<T> {
  private contents: T;

  constructor(contents: T) {
    this.contents = contents;
  }

  getContents(): T {
    return this.contents;
  }
}

let stringBox = new Box<string>("Hello");
console.log(stringBox.getContents()); // "Hello"

let numberBox = new Box<number>(123);
console.log(numberBox.getContents()); // 123
```

---

## **4. Generic Interfaces**
- Use generics in interfaces to enforce a structure while keeping flexibility.

**Example:**
```typescript
interface KeyValuePair<K, V> {
  key: K;
  value: V;
}

let pair: KeyValuePair<string, number> = { key: "age", value: 30 };
```

---

## **5. Constraints on Generics**
- Use `extends` to constrain the type of a generic parameter.

**Example:**
```typescript
function getLength<T extends { length: number }>(item: T): number {
  return item.length;
}

console.log(getLength("Hello")); // 5
console.log(getLength([1, 2, 3])); // 3
// console.log(getLength(123)); // Error: Type 'number' has no property 'length'
```

---

## **6. Default Values for Generics**
- Assign default types to generics.

**Example:**
```typescript
function createArray<T = string>(length: number, value: T): T[] {
  return Array(length).fill(value);
}

let numbers = createArray<number>(3, 42); // [42, 42, 42]
let strings = createArray(3, "Hi"); // ["Hi", "Hi", "Hi"]
```

---

## **7. Generic Utility Types**
- TypeScript provides built-in generic types for common use cases, such as `Array<T>` and `Promise<T>`.

**Example:**
```typescript
let list: Array<number> = [1, 2, 3];
let fetchData: Promise<string> = new Promise((resolve) => resolve("Success"));
```

---

## **8. Combining Generics**
- Combine multiple generic types for more complex scenarios.

**Example:**
```typescript
function mapObject<K extends string, V>(obj: Record<K, V>, callback: (key: K, value: V) => V): Record<K, V> {
  const result: Record<K, V> = {} as Record<K, V>;
  for (let key in obj) {
    result[key] = callback(key, obj[key]);
  }
  return result;
}

let transformed = mapObject({ a: 1, b: 2 }, (key, value) => value * 2);
console.log(transformed); // { a: 2, b: 4 }
```

---

## **9. Practical Applications of Generics**
### **9.1. Type-Safe Data Structures**
- Create reusable and type-safe data structures.

**Example:**
```typescript
class Stack<T> {
  private items: T[] = [];

  push(item: T): void {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }
}

let numberStack = new Stack<number>();
numberStack.push(10);
numberStack.push(20);
console.log(numberStack.pop()); // 20
```

### **9.2. API Responses**
- Define generic interfaces for consistent API response handling.

**Example:**
```typescript
interface ApiResponse<T> {
  data: T;
  success: boolean;
  error?: string;
}

let response: ApiResponse<string> = {
  data: "Hello, world!",
  success: true,
};
```

---

## **10. Practice Exercises**
1. Write a generic function to return the first element of an array.
2. Create a generic class for a queue data structure.
3. Define a generic interface for a pair of values, and create an instance of it.
4. Implement a generic function with constraints to filter objects with a `length` property greater than a given value.

---

Generics allow you to write flexible, reusable, and type-safe code in TypeScript. Mastering them is essential for advanced programming and library development.
