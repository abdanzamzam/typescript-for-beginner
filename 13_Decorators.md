

# Decorators in TypeScript

---

## **Objective:**
Understand how to use decorators in TypeScript to add metadata, modify behavior, and extend functionality of classes, methods, properties, and parameters.

---

## **1. What are Decorators?**
- A decorator is a special kind of declaration that can be attached to a class, method, accessor, property, or parameter.
- They allow you to modify or annotate the behavior of the element they are attached to.
- Syntax: `@decoratorName`

**Example:**
```typescript
function Log(target: any, propertyName: string): void {
  console.log(`${propertyName} was accessed`);
}

class Example {
  @Log
  property: string;

  constructor(property: string) {
    this.property = property;
  }
}
```

---

## **2. Enabling Experimental Decorators**
- To use decorators, enable the `experimentalDecorators` option in `tsconfig.json`.

**Example (tsconfig.json):**
```json
{
  "compilerOptions": {
    "experimentalDecorators": true
  }
}
```

---

## **3. Types of Decorators**
### **3.1. Class Decorators**
- Applied to a class and receive the class constructor as an argument.

**Example:**
```typescript
function Component(target: Function): void {
  target.prototype.componentType = "UI Component";
}

@Component
class Button {
  click(): void {
    console.log("Button clicked!");
  }
}

let button = new Button();
console.log((button as any).componentType); // "UI Component"
```

---

### **3.2. Method Decorators**
- Applied to a method and receive the target, method name, and descriptor.

**Example:**
```typescript
function LogMethod(target: any, methodName: string, descriptor: PropertyDescriptor): void {
  const originalMethod = descriptor.value;

  descriptor.value = function (...args: any[]) {
    console.log(`Calling ${methodName} with`, args);
    return originalMethod.apply(this, args);
  };
}

class Calculator {
  @LogMethod
  add(a: number, b: number): number {
    return a + b;
  }
}

let calc = new Calculator();
console.log(calc.add(2, 3)); // Logs: "Calling add with [2, 3]" and then returns 5
```

---

### **3.3. Accessor Decorators**
- Applied to a getter or setter and receive the target, name, and descriptor.

**Example:**
```typescript
function ReadOnly(target: any, propertyName: string, descriptor: PropertyDescriptor): void {
  descriptor.writable = false;
}

class User {
  private _name: string;

  constructor(name: string) {
    this._name = name;
  }

  @ReadOnly
  get name(): string {
    return this._name;
  }
}

let user = new User("Alice");
// user.name = "Bob"; // Error: Cannot assign to read only property
console.log(user.name); // "Alice"
```

---

### **3.4. Property Decorators**
- Applied to a class property and receive the target and property name.

**Example:**
```typescript
function DefaultValue(value: any) {
  return function (target: any, propertyName: string): void {
    Object.defineProperty(target, propertyName, {
      value,
      writable: true,
    });
  };
}

class Settings {
  @DefaultValue("dark")
  theme: string;
}

let settings = new Settings();
console.log(settings.theme); // "dark"
```

---

### **3.5. Parameter Decorators**
- Applied to parameters of a method and receive the target, method name, and parameter index.

**Example:**
```typescript
function LogParameter(target: any, methodName: string, parameterIndex: number): void {
  console.log(`Parameter in position ${parameterIndex} in method ${methodName} was accessed`);
}

class Service {
  greet(@LogParameter message: string): void {
    console.log(message);
  }
}

let service = new Service();
service.greet("Hello!"); // Logs: "Parameter in position 0 in method greet was accessed"
```

---

## **4. Chaining Decorators**
- Multiple decorators can be applied and are executed in reverse order of their declaration.

**Example:**
```typescript
function First() {
  return function (target: any, methodName: string): void {
    console.log("First decorator");
  };
}

function Second() {
  return function (target: any, methodName: string): void {
    console.log("Second decorator");
  };
}

class Example {
  @First()
  @Second()
  method(): void {}
}

// Logs: "Second decorator" and then "First decorator"
```

---

## **5. Use Cases for Decorators**
1. **Logging**: Track method calls, parameters, and return values.
2. **Validation**: Validate input data in methods.
3. **Dependency Injection**: Automatically inject dependencies.
4. **Framework Development**: Used in frameworks like Angular for annotations.

---

## **6. Practice Exercises**
1. Create a class decorator that adds a timestamp property to the class.
2. Write a method decorator that logs the execution time of a method.
3. Implement a property decorator that sets a default value for a property.
4. Use a parameter decorator to log all method parameter values during method execution.

---

Decorators are powerful tools in TypeScript that allow you to modify the behavior of your code at runtime. Mastering them enables you to write clean, modular, and reusable code.
