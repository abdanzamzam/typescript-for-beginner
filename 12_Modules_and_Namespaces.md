
# Modules and Namespaces in TypeScript

---

## **Objective:**
Understand how to use TypeScript modules and namespaces to organize and manage code across multiple files while avoiding naming conflicts.

---

## **1. What are Modules?**
- Modules are files containing code that can be imported or exported.
- They help organize code into reusable and maintainable units.
- Syntax: `import` and `export`

---

## **2. Exporting and Importing**
### **2.1. Named Exports**
- Export specific members from a module.

**Example (mathUtils.ts):**
```typescript
export function add(a: number, b: number): number {
  return a + b;
}

export function subtract(a: number, b: number): number {
  return a - b;
}
```

**Example (main.ts):**
```typescript
import { add, subtract } from "./mathUtils";

console.log(add(10, 5)); // 15
console.log(subtract(10, 5)); // 5
```

### **2.2. Default Exports**
- Export a single default member.

**Example (logger.ts):**
```typescript
export default function log(message: string): void {
  console.log(message);
}
```

**Example (main.ts):**
```typescript
import log from "./logger";

log("Hello, world!"); // "Hello, world!"
```

### **2.3. Export All**
- Re-export all members from another module.

**Example (utilities.ts):**
```typescript
export * from "./mathUtils";
export * from "./logger";
```

**Example (main.ts):**
```typescript
import { add, subtract } from "./utilities";
console.log(add(5, 3)); // 8
```

---

## **3. Aliases**
- Use aliases to rename imports and exports.

**Example:**
```typescript
import { add as addition } from "./mathUtils";

console.log(addition(2, 3)); // 5
```

---

## **4. What are Namespaces?**
- Namespaces group related code together to prevent naming conflicts.
- Syntax: `namespace` and `export`

**Example:**
```typescript
namespace Geometry {
  export function calculateArea(radius: number): number {
    return Math.PI * radius ** 2;
  }

  export function calculateCircumference(radius: number): number {
    return 2 * Math.PI * radius;
  }
}

console.log(Geometry.calculateArea(5)); // 78.53981633974483
console.log(Geometry.calculateCircumference(5)); // 31.41592653589793
```

---

## **5. Differences Between Modules and Namespaces**
| Feature             | Modules                        | Namespaces                  |
|---------------------|---------------------------------|-----------------------------|
| Scope               | File-based                     | Global (within the namespace) |
| Usage               | Better for modern applications | Legacy code or large projects |
| Dependency Handling | Uses `import` and `export`     | Not dependent on file imports |

---

## **6. Combining Modules and Namespaces**
- Use namespaces within modules for better organization.

**Example:**
```typescript
// geometry.ts
export namespace Geometry {
  export function calculateArea(radius: number): number {
    return Math.PI * radius ** 2;
  }
}

// main.ts
import { Geometry } from "./geometry";

console.log(Geometry.calculateArea(5)); // 78.53981633974483
```

---

## **7. Practical Use Cases**
### **7.1. Modularizing Code**
- Split utilities into separate modules for reuse.

**Example:**
```typescript
// mathUtils.ts
export function square(num: number): number {
  return num * num;
}

// main.ts
import { square } from "./mathUtils";
console.log(square(4)); // 16
```

### **7.2. Using Namespaces for Large Libraries**
- Group related functionalities in a namespace.

**Example:**
```typescript
namespace Utils {
  export function isEven(num: number): boolean {
    return num % 2 === 0;
  }

  export function isOdd(num: number): boolean {
    return !isEven(num);
  }
}

console.log(Utils.isEven(4)); // true
console.log(Utils.isOdd(5)); // true
```

---

## **8. Practice Exercises**
1. Create a `mathOperations` module with `add`, `subtract`, `multiply`, and `divide` functions. Import them in a `main` file and use them.
2. Define a `Shapes` namespace with functions to calculate the area of a circle and a rectangle.
3. Combine namespaces and modules to create an organized project structure.
4. Re-export all utilities from two different modules (`mathUtils` and `stringUtils`) into a single `utilities` module.

---

Modules and namespaces are powerful tools in TypeScript for organizing code and managing dependencies. Use modules for modern applications and namespaces for specific legacy or large project scenarios.
