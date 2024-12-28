
# Utility Types in TypeScript

---

## **Objective:**
Learn how to use TypeScript's built-in utility types to manipulate and transform types for better type safety and flexibility.

---

## **1. What are Utility Types?**
- Utility types are predefined types provided by TypeScript to perform common type transformations.
- They help reduce boilerplate code and improve readability.

---

## **2. Commonly Used Utility Types**
### **2.1. `Partial<T>`**
- Makes all properties in a type optional.

**Example:**
```typescript
interface User {
  name: string;
  age: number;
  isAdmin: boolean;
}

let partialUser: Partial<User> = { name: "Alice" };
```

---

### **2.2. `Required<T>`**
- Makes all properties in a type required.

**Example:**
```typescript
interface User {
  name?: string;
  age?: number;
}

let user: Required<User> = { name: "Bob", age: 30 }; // Error if properties are missing
```

---

### **2.3. `Readonly<T>`**
- Makes all properties in a type read-only.

**Example:**
```typescript
interface User {
  name: string;
  age: number;
}

let readonlyUser: Readonly<User> = { name: "Charlie", age: 25 };
// readonlyUser.age = 26; // Error: Cannot assign to 'age' because it is a read-only property
```

---

### **2.4. `Pick<T, K>`**
- Creates a type by picking specific properties from another type.

**Example:**
```typescript
interface User {
  name: string;
  age: number;
  email: string;
}

let pickedUser: Pick<User, "name" | "email"> = { name: "David", email: "david@example.com" };
```

---

### **2.5. `Omit<T, K>`**
- Creates a type by omitting specific properties from another type.

**Example:**
```typescript
interface User {
  name: string;
  age: number;
  email: string;
}

let omittedUser: Omit<User, "age"> = { name: "Eve", email: "eve@example.com" };
```

---

### **2.6. `Record<K, T>`**
- Creates an object type with keys of type `K` and values of type `T`.

**Example:**
```typescript
let userRoles: Record<string, string> = {
  admin: "Alice",
  editor: "Bob",
};
```

---

### **2.7. `Exclude<T, U>`**
- Excludes properties of `U` from `T`.

**Example:**
```typescript
type AvailableRoles = "admin" | "editor" | "guest";
type NonGuestRoles = Exclude<AvailableRoles, "guest">; // "admin" | "editor"
```

---

### **2.8. `Extract<T, U>`**
- Extracts properties of `U` that are assignable to `T`.

**Example:**
```typescript
type Roles = "admin" | "editor" | "guest";
type AdminRoles = Extract<Roles, "admin" | "guest">; // "admin" | "guest"
```

---

### **2.9. `NonNullable<T>`**
- Removes `null` and `undefined` from a type.

**Example:**
```typescript
type Name = string | null | undefined;
type ValidName = NonNullable<Name>; // string
```

---

### **2.10. `ReturnType<T>`**
- Extracts the return type of a function.

**Example:**
```typescript
function getUser() {
  return { name: "Alice", age: 30 };
}

type User = ReturnType<typeof getUser>; // { name: string; age: number }
```

---

### **2.11. `InstanceType<T>`**
- Extracts the type of an instance of a class.

**Example:**
```typescript
class User {
  constructor(public name: string, public age: number) {}
}

type UserInstance = InstanceType<typeof User>; // User
```

---

### **2.12. `Awaited<T>`**
- Unwraps the return type of a Promise.

**Example:**
```typescript
type FetchData = Promise<string>;
type ResolvedData = Awaited<FetchData>; // string
```

---

## **3. Combining Utility Types**
- Utility types can be combined for advanced use cases.

**Example:**
```typescript
interface User {
  name: string;
  age: number;
  email: string;
}

type PartialReadonlyUser = Readonly<Partial<User>>;
let user: PartialReadonlyUser = { name: "Alice" };
// user.name = "Bob"; // Error: Cannot assign to 'name' because it is a read-only property
```

---

## **4. Practice Exercises**
1. Create a `Partial` version of a `Product` type and add a few properties.
2. Use `Pick` to create a type that includes only the `title` and `price` properties from a `Book` interface.
3. Write a function that accepts a `Readonly` type of a `Car` object and attempts to modify a property (observe the error).
4. Combine `Omit` and `Record` to create a map of users excluding sensitive properties like `password`.

---

Utility types are essential tools in TypeScript that simplify type manipulation, reduce boilerplate, and make your code more expressive and maintainable.
