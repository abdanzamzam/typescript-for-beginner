
# Union and Intersection Types in TypeScript

---

## **Objective:**
Understand and use `Union` and `Intersection` types in TypeScript to create flexible and composable type structures.

---

## **1. What are Union Types?**
- A union type allows a variable to hold one of several defined types.
- Syntax: `type1 | type2 | ...`

**Example:**
```typescript
let id: string | number;
id = "abc123"; // Valid
id = 123;      // Valid
// id = true;  // Error: Type 'boolean' is not assignable to type 'string | number'
```

---

## **2. Key Features of Union Types**
### **2.1. Narrowing with Type Guards**
- Use type guards to determine the exact type of a variable at runtime.

**Example:**
```typescript
function display(value: string | number): void {
  if (typeof value === "string") {
    console.log(`String: ${value.toUpperCase()}`);
  } else {
    console.log(`Number: ${value.toFixed(2)}`);
  }
}
```

### **2.2. Union Types in Functions**
- Define parameters or return values that accept multiple types.

**Example:**
```typescript
function calculateArea(shape: "circle" | "square", size: number): number {
  if (shape === "circle") {
    return Math.PI * size * size;
  } else {
    return size * size;
  }
}
```

### **2.3. Union Types in Arrays**
- Define arrays with elements of multiple types.

**Example:**
```typescript
let mixedArray: (string | number)[] = [1, "hello", 42];
```

---

## **3. What are Intersection Types?**
- An intersection type combines multiple types into one, requiring a value to satisfy all included types.
- Syntax: `type1 & type2 & ...`

**Example:**
```typescript
type HasName = { name: string };
type HasAge = { age: number };

type Person = HasName & HasAge;

let john: Person = { name: "John", age: 30 };
```

---

## **4. Key Features of Intersection Types**
### **4.1. Combining Object Types**
- Merge multiple object types into a single structure.

**Example:**
```typescript
type Address = { street: string; city: string };
type Contact = { email: string; phone: string };

type Employee = Address & Contact;

let employee: Employee = {
  street: "123 Main St",
  city: "New York",
  email: "john.doe@example.com",
  phone: "123-456-7890",
};
```

### **4.2. Extending Interfaces with Intersection Types**
- Combine interfaces and other types using intersections.

**Example:**
```typescript
interface User {
  username: string;
}

type Admin = User & { privileges: string[] };

let admin: Admin = { username: "adminUser", privileges: ["manage-users", "edit-content"] };
```

### **4.3. Intersection of Primitive and Object Types**
- Use intersections to enforce constraints.

**Example:**
```typescript
type ID = string & { length: 10 };

let validID: ID = "1234567890"; // Must have exactly 10 characters
```

---

## **5. Combining Union and Intersection Types**
- Create complex types by mixing unions and intersections.

**Example:**
```typescript
type SuccessResponse = { status: "success"; data: any };
type ErrorResponse = { status: "error"; message: string };

type APIResponse = SuccessResponse | ErrorResponse;

function handleResponse(response: APIResponse): void {
  if (response.status === "success") {
    console.log("Data:", response.data);
  } else {
    console.error("Error:", response.message);
  }
}
```

---

## **6. When to Use Union vs. Intersection**
| Scenario                         | Use Union (`|`)                   | Use Intersection (`&`)               |
|----------------------------------|-----------------------------------|---------------------------------------|
| Allowing multiple options        | When a value can be one of many   | When a value must satisfy all types   |
| Combining object properties      | Not applicable                   | To merge multiple object structures   |
| Function parameters or return types | Accepting different value types   | Enforcing combined behavior           |

---

## **7. Practical Applications**
### **7.1. API Response Handling**
- Use union types to handle multiple response formats.

**Example:**
```typescript
type APIResult = { data: any } | { error: string };

let result: APIResult = { data: "Sample data" };
```

### **7.2. Form Validation**
- Use intersection types to combine validation rules.

**Example:**
```typescript
type RequiredFields = { username: string; password: string };
type OptionalFields = { rememberMe?: boolean };

type LoginForm = RequiredFields & OptionalFields;

let form: LoginForm = { username: "user123", password: "pass", rememberMe: true };
```

---

## **8. Practice Exercises**
1. Create a union type for a variable that can hold either a string or an array of strings.
2. Define an intersection type for a `Product` that includes properties for `name` (string), `price` (number), and `inStock` (boolean).
3. Write a function that accepts a union type of `number` or `boolean` and performs different operations based on the type.
4. Use an intersection type to define a `Student` with properties from both `Person` and `SchoolRecord`.

---

Mastering `Union` and `Intersection` types allows you to create flexible and powerful type definitions that adapt to a variety of use cases in TypeScript.
