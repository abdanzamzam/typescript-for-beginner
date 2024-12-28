
# Literal Types and Enum in TypeScript

---

## **Objective:**
Learn how to use Literal Types and Enums in TypeScript to define fixed sets of values for variables, enhancing type safety and code clarity.

---

## **1. What are Literal Types?**
- Literal types allow you to specify exact values a variable can have.
- They are used to define a fixed set of allowable values for a type.

**Example:**
```typescript
let direction: "up" | "down" | "left" | "right";
direction = "up"; // Valid
// direction = "forward"; // Error: Type '"forward"' is not assignable to type '"up" | "down" | "left" | "right"'
```

---

## **2. Key Features of Literal Types**
### **2.1. String Literal Types**
- Restrict a variable to specific string values.

**Example:**
```typescript
type Status = "success" | "error" | "pending";

let responseStatus: Status = "success";
// responseStatus = "failure"; // Error
```

### **2.2. Numeric Literal Types**
- Restrict a variable to specific numeric values.

**Example:**
```typescript
type DiceRoll = 1 | 2 | 3 | 4 | 5 | 6;

let roll: DiceRoll = 4;
// roll = 7; // Error
```

### **2.3. Combining Literal Types with Union**
- Combine literals for flexible and safe types.

**Example:**
```typescript
type Alignment = "left" | "center" | "right";
type Size = "small" | "medium" | "large";

let textAlignment: Alignment = "center";
let buttonSize: Size = "medium";
```

---

## **3. What is an Enum?**
- An `enum` is a way to define a named set of constants, either as numbers or strings.
- It is useful for representing fixed value sets with meaningful names.

---

## **4. Numeric Enums**
- By default, enums are numeric and start at `0`. You can override the starting value.

**Example:**
```typescript
enum Direction {
  Up,    // 0
  Down,  // 1
  Left,  // 2
  Right, // 3
}

let move: Direction = Direction.Up;
console.log(move); // 0
```

### **4.1. Custom Numeric Values**
- Define specific numeric values for enum members.

**Example:**
```typescript
enum Status {
  Success = 200,
  NotFound = 404,
  InternalError = 500,
}

console.log(Status.NotFound); // 404
```

---

## **5. String Enums**
- Enums can also hold string values.

**Example:**
```typescript
enum Color {
  Red = "RED",
  Green = "GREEN",
  Blue = "BLUE",
}

let favoriteColor: Color = Color.Blue;
console.log(favoriteColor); // "BLUE"
```

---

## **6. Const Enums**
- Use `const enum` for optimized and inline values.

**Example:**
```typescript
const enum Sizes {
  Small = "SMALL",
  Medium = "MEDIUM",
  Large = "LARGE",
}

let tshirtSize: Sizes = Sizes.Medium;
```

- Compiles to:
```javascript
let tshirtSize = "MEDIUM";
```

---

## **7. Enum Use Cases**
### **7.1. Flags and Options**
- Use numeric enums for bitwise operations.

**Example:**
```typescript
enum Permissions {
  Read = 1,
  Write = 2,
  Execute = 4,
}

let userPermissions = Permissions.Read | Permissions.Write;
console.log(userPermissions); // 3
```

### **7.2. Status Codes**
- Use string enums for descriptive constants.

**Example:**
```typescript
enum HttpStatus {
  OK = "200 OK",
  NotFound = "404 Not Found",
  InternalError = "500 Internal Server Error",
}

console.log(HttpStatus.OK); // "200 OK"
```

---

## **8. Combining Literal Types and Enums**
- Use literal types and enums together for advanced type definitions.

**Example:**
```typescript
enum LogLevel {
  Info = "INFO",
  Warning = "WARNING",
  Error = "ERROR",
}

type LogMessage = {
  level: LogLevel;
  message: string;
};

let log: LogMessage = { level: LogLevel.Info, message: "System is running smoothly." };
```

---

## **9. When to Use Literal Types vs. Enum**
| Scenario                              | Use Literal Types                  | Use Enums                        |
|---------------------------------------|------------------------------------|----------------------------------|
| Fixed small set of string values      | Yes                                | No                               |
| Meaningful names for constants        | No                                 | Yes                              |
| Optimized runtime code                | No                                 | Use Const Enum                   |
| Need for numeric values               | No                                 | Yes                              |

---

## **10. Practice Exercises**
1. Create a string literal type for `days` of the week and assign one to a variable.
2. Define a numeric enum for RGB color values (`Red = 255`, `Green = 128`, `Blue = 64`).
3. Write a function that accepts an enum value (e.g., `Status`) and returns a message.
4. Use a string enum to represent HTTP status codes and log one to the console.

---

Literal types and enums are powerful tools in TypeScript that help create predictable, readable, and type-safe code. Use them to define fixed value sets for variables and constants effectively.
