
# API Integration in TypeScript

---

## **Objective:**
Learn how to perform API integration in TypeScript by making HTTP requests, handling responses, and defining type-safe models.

---

## **1. Why Use TypeScript for API Integration?**
- **Type Safety:** Ensures correct data structures for requests and responses.
- **Improved Debugging:** Catches type-related errors at compile time.
- **Readability and Maintenance:** Makes code easier to understand and maintain.

---

## **2. Setting Up HTTP Libraries**
### **2.1. Using Axios**
- Install Axios and its TypeScript types:
```bash
npm install axios
npm install @types/axios --save-dev
```

---

## **3. Making HTTP Requests**
### **3.1. GET Request**
#### File: `api.ts`
```typescript
import axios from "axios";

export interface User {
  id: number;
  name: string;
  email: string;
}

export async function fetchUsers(): Promise<User[]> {
  const response = await axios.get<User[]>("https://jsonplaceholder.typicode.com/users");
  return response.data;
}
```

#### File: `main.ts`
```typescript
import { fetchUsers } from "./api";

fetchUsers().then((users) => {
  console.log(users);
});
```

---

### **3.2. POST Request**
#### File: `api.ts`
```typescript
import axios from "axios";

export interface NewUser {
  name: string;
  email: string;
}

export async function createUser(user: NewUser): Promise<NewUser> {
  const response = await axios.post<NewUser>("https://jsonplaceholder.typicode.com/users", user);
  return response.data;
}
```

#### File: `main.ts`
```typescript
import { createUser } from "./api";

createUser({ name: "Alice", email: "alice@example.com" }).then((user) => {
  console.log(user);
});
```

---

## **4. Advanced Techniques**
### **4.1. Using Generics for Dynamic Responses**
```typescript
import axios from "axios";

export async function fetchData<T>(url: string): Promise<T> {
  const response = await axios.get<T>(url);
  return response.data;
}

fetchData<{ id: number; title: string }[]>("https://jsonplaceholder.typicode.com/posts").then((posts) => {
  console.log(posts);
});
```

---

### **4.2. Handling Errors**
- Use `try-catch` blocks to handle API errors.

**Example:**
```typescript
import axios from "axios";

export async function fetchPosts() {
  try {
    const response = await axios.get("https://jsonplaceholder.typicode.com/posts");
    return response.data;
  } catch (error) {
    if (axios.isAxiosError(error)) {
      console.error("Axios error:", error.message);
    } else {
      console.error("Unexpected error:", error);
    }
  }
}
```

---

### **4.3. Interceptors**
- Use Axios interceptors for common tasks like adding headers or logging.

**Example:**
```typescript
import axios from "axios";

axios.interceptors.request.use((config) => {
  console.log("Request made:", config.url);
  return config;
});

axios.interceptors.response.use(
  (response) => {
    console.log("Response received:", response.status);
    return response;
  },
  (error) => {
    console.error("Error occurred:", error.message);
    return Promise.reject(error);
  }
);
```

---

## **5. Defining Type-Safe API Responses**
- Define interfaces or types for responses to ensure type safety.

**Example:**
```typescript
export interface ApiResponse<T> {
  data: T;
  status: string;
}

export async function fetchUsers(): Promise<ApiResponse<User[]>> {
  const response = await axios.get("https://jsonplaceholder.typicode.com/users");
  return { data: response.data, status: "success" };
}
```

---

## **6. Practice Exercises**
1. Write a function to fetch a list of posts from an API and log their titles.
2. Create a POST request to submit a new comment and log the response.
3. Implement a generic function to handle API responses for both `GET` and `POST` methods.
4. Add error handling and logging to your API integration code.

---

TypeScript's strong typing capabilities make API integration safer and more predictable, ensuring that your application handles data correctly and consistently.
