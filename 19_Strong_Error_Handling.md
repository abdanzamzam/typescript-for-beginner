
# Strong Error Handling in TypeScript

---

## **Objective:**
Learn how to implement robust error handling in TypeScript to manage exceptions effectively and create resilient applications.

---

## **1. Why Strong Error Handling?**
- **Prevent Crashes:** Avoid application crashes due to unhandled exceptions.
- **Improve User Experience:** Provide meaningful error messages and fallback mechanisms.
- **Enhance Debugging:** Simplify troubleshooting with structured error logging.

---

## **2. Basic Error Handling**
### **2.1. Using `try-catch` Blocks**
- Handle runtime errors gracefully.

**Example:**
```typescript
function parseJSON(jsonString: string): any {
  try {
    return JSON.parse(jsonString);
  } catch (error) {
    console.error("Invalid JSON:", error.message);
    return null;
  }
}

const result = parseJSON('{"key": "value"}');
console.log(result); // { key: "value" }
```

---

### **2.2. Throwing Errors**
- Use `throw` to generate custom errors.

**Example:**
```typescript
function divide(a: number, b: number): number {
  if (b === 0) {
    throw new Error("Division by zero is not allowed.");
  }
  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (error) {
  console.error(error.message);
}
```

---

## **3. Typed Error Handling**
### **3.1. Custom Error Classes**
- Create custom error classes for specific scenarios.

**Example:**
```typescript
class ValidationError extends Error {
  constructor(message: string) {
    super(message);
    this.name = "ValidationError";
  }
}

function validateInput(input: string): void {
  if (input.trim() === "") {
    throw new ValidationError("Input cannot be empty.");
  }
}

try {
  validateInput("");
} catch (error) {
  if (error instanceof ValidationError) {
    console.error("Validation Error:", error.message);
  }
}
```

---

### **3.2. Using Type Guards**
- Check the type of an error to handle it appropriately.

**Example:**
```typescript
function handleError(error: unknown): void {
  if (error instanceof Error) {
    console.error("Error:", error.message);
  } else {
    console.error("Unexpected error:", error);
  }
}

try {
  throw new Error("Something went wrong");
} catch (error) {
  handleError(error);
}
```

---

## **4. Error Handling with Async/Await**
- Use `try-catch` for errors in asynchronous code.

**Example:**
```typescript
async function fetchData(url: string): Promise<void> {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Fetch error:", error.message);
  }
}

fetchData("https://jsonplaceholder.typicode.com/posts");
```

---

## **5. Centralized Error Handling**
- Use centralized handlers for consistent error management.

**Example:**
```typescript
function errorHandler(error: Error): void {
  console.error(`[Error] ${error.name}: ${error.message}`);
}

try {
  throw new Error("A critical error occurred!");
} catch (error) {
  errorHandler(error);
}
```

---

## **6. Error Logging**
- Log errors for monitoring and debugging.

**Example:**
```typescript
function logError(error: Error): void {
  console.log(`[${new Date().toISOString()}] ${error.name}: ${error.message}`);
}

try {
  throw new Error("An unexpected issue!");
} catch (error) {
  logError(error);
}
```

---

## **7. Using Utility Libraries**
- Use libraries like `winston` or `pino` for advanced logging.
- Example with `winston`:
```typescript
import winston from "winston";

const logger = winston.createLogger({
  transports: [new winston.transports.Console()],
});

try {
  throw new Error("An error occurred");
} catch (error) {
  logger.error(error.message);
}
```

---

## **8. Best Practices for Strong Error Handling**
1. **Always Handle Errors:** Never leave errors unhandled.
2. **Use Custom Error Types:** Create specific error classes for clear identification.
3. **Log Errors:** Ensure all errors are logged for debugging and auditing.
4. **Provide User-Friendly Messages:** Show meaningful messages to users.
5. **Validate Inputs:** Prevent errors by validating inputs before processing.

---

## **9. Practice Exercises**
1. Create a custom error class for API errors and handle it in a function.
2. Write an asynchronous function that fetches data from an API and handles errors gracefully.
3. Implement a centralized error handling mechanism in a small TypeScript project.
4. Use a logging library to log errors with timestamps and severity levels.

---

Strong error handling is crucial for building reliable, user-friendly applications. Implementing these strategies ensures your TypeScript applications are robust and maintainable.
