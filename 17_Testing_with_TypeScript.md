
# Testing with TypeScript

---

## **Objective:**
Learn how to write and run tests in TypeScript using popular testing frameworks like Jest and Mocha, ensuring your code is reliable and bug-free.

---

## **1. Why Test TypeScript Code?**
- **Catch Bugs Early:** Detect issues before they reach production.
- **Maintain Code Quality:** Ensure new changes don't break existing functionality.
- **Improve Confidence:** Safeguard against unexpected behaviors in your application.

---

## **2. Setting Up Testing Frameworks**
### **2.1. Using Jest**
#### Installing Jest and TypeScript Support
```bash
npm install jest ts-jest @types/jest --save-dev
npx ts-jest config:init
```

#### Configuring Jest
- Update `jest.config.js`:
```javascript
module.exports = {
  preset: "ts-jest",
  testEnvironment: "node",
};
```

---

### **2.2. Using Mocha with Chai**
#### Installing Mocha, Chai, and TypeScript Support
```bash
npm install mocha chai ts-node @types/mocha @types/chai --save-dev
```

#### Configuring Mocha
- Add a `mocha` script to `package.json`:
```json
"scripts": {
  "test": "mocha -r ts-node/register 'tests/**/*.ts'"
}
```

---

## **3. Writing Tests in TypeScript**
### **3.1. Example Test with Jest**
#### File: `mathUtils.ts`
```typescript
export function add(a: number, b: number): number {
  return a + b;
}
```

#### File: `mathUtils.test.ts`
```typescript
import { add } from "./mathUtils";

test("adds two numbers", () => {
  expect(add(2, 3)).toBe(5);
});
```

- Run the test:
```bash
npm test
```

---

### **3.2. Example Test with Mocha and Chai**
#### File: `mathUtils.ts`
```typescript
export function subtract(a: number, b: number): number {
  return a - b;
}
```

#### File: `tests/mathUtils.test.ts`
```typescript
import { expect } from "chai";
import { subtract } from "../mathUtils";

describe("MathUtils", () => {
  it("should subtract two numbers", () => {
    expect(subtract(5, 3)).to.equal(2);
  });
});
```

- Run the test:
```bash
npm test
```

---

## **4. Advanced Testing Techniques**
### **4.1. Mocking**
- Mock external dependencies to isolate units under test.
- Example using Jest:
```typescript
import axios from "axios";
import { fetchData } from "./api";

jest.mock("axios");
const mockedAxios = axios as jest.Mocked<typeof axios>;

test("fetches data successfully", async () => {
  mockedAxios.get.mockResolvedValue({ data: { message: "Hello" } });

  const data = await fetchData();
  expect(data.message).toBe("Hello");
});
```

---

### **4.2. Testing Asynchronous Code**
- Use `async/await` for testing promises.
```typescript
test("resolves with correct data", async () => {
  const data = await asyncFunction();
  expect(data).toBe("Success");
});
```

---

### **4.3. Code Coverage**
- Use Jest to generate code coverage:
```bash
jest --coverage
```

- View coverage report in the `coverage` directory.

---

## **5. Integrating Tests in CI/CD**
- Add testing to CI/CD pipelines (e.g., GitHub Actions, Travis CI):
```yaml
steps:
  - name: Install Dependencies
    run: npm install
  - name: Run Tests
    run: npm test
```

---

## **6. Practice Exercises**
1. Write unit tests for a `multiply` function using Jest.
2. Implement a function to fetch user data from an API and mock it in a Jest test.
3. Create a `Rectangle` class with `area` and `perimeter` methods, and test it using Mocha and Chai.
4. Configure code coverage for your Jest tests and verify the report.

---

Testing with TypeScript ensures your code is robust, maintainable, and error-free. Mastering these tools and techniques will make you a more confident and effective developer.
