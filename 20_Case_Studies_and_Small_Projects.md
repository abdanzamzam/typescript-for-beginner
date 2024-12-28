
# Case Studies and Small Projects in TypeScript

---

## **Objective:**
Gain practical experience with TypeScript by working on small projects and case studies, focusing on real-world applications and best practices.

---

## **1. Project: Migrating JavaScript to TypeScript**
### **Overview**
- Convert a small JavaScript project to TypeScript to learn type annotations and project setup.

### **Steps**
1. **Set Up TypeScript**:
   - Install TypeScript and initialize a configuration file:
   ```bash
   npm install typescript --save-dev
   npx tsc --init
   ```

2. **Refactor Code**:
   - Rename `.js` files to `.ts`.
   - Add type annotations to variables, functions, and classes.

3. **Example Code**:
   **JavaScript (Before):**
   ```javascript
   function add(a, b) {
     return a + b;
   }
   console.log(add(2, 3));
   ```

   **TypeScript (After):**
   ```typescript
   function add(a: number, b: number): number {
     return a + b;
   }
   console.log(add(2, 3));
   ```

---

## **2. Project: Building a Simple REST API**
### **Overview**
- Create a basic REST API using TypeScript and Express.

### **Steps**
1. **Install Dependencies**:
   ```bash
   npm install express @types/express typescript ts-node --save-dev
   npx tsc --init
   ```

2. **Write API Code**:
   **File: `server.ts`**
   ```typescript
   import express, { Request, Response } from "express";

   const app = express();
   app.use(express.json());

   app.get("/api/users", (req: Request, res: Response) => {
     res.json([{ id: 1, name: "Alice" }, { id: 2, name: "Bob" }]);
   });

   app.post("/api/users", (req: Request, res: Response) => {
     const user = req.body;
     res.status(201).json(user);
   });

   app.listen(3000, () => console.log("Server running on port 3000"));
   ```

---

## **3. Project: React App with TypeScript**
### **Overview**
- Build a small React application using TypeScript for type safety.

### **Steps**
1. **Create Project**:
   ```bash
   npx create-react-app my-app --template typescript
   ```

2. **Write a Component**:
   **File: `UserList.tsx`**
   ```typescript
   interface User {
     id: number;
     name: string;
   }

   const UserList: React.FC<{ users: User[] }> = ({ users }) => {
     return (
       <ul>
         {users.map((user) => (
           <li key={user.id}>{user.name}</li>
         ))}
       </ul>
     );
   };

   export default UserList;
   ```

3. **Use the Component**:
   **File: `App.tsx`**
   ```typescript
   import React from "react";
   import UserList from "./UserList";

   const App: React.FC = () => {
     const users = [{ id: 1, name: "Alice" }, { id: 2, name: "Bob" }];

     return (
       <div>
         <h1>User List</h1>
         <UserList users={users} />
       </div>
     );
   };

   export default App;
   ```

---

## **4. Case Study: Data Validation with TypeScript**
### **Scenario**
- Validate user input data in a TypeScript application.

### **Steps**
1. **Define an Interface**:
   ```typescript
   interface User {
     name: string;
     email: string;
     age: number;
   }
   ```

2. **Write a Validation Function**:
   ```typescript
   function validateUser(user: User): string[] {
     const errors: string[] = [];
     if (!user.name) errors.push("Name is required.");
     if (!user.email.includes("@")) errors.push("Invalid email.");
     if (user.age < 0 || user.age > 120) errors.push("Invalid age.");
     return errors;
   }

   const user = { name: "", email: "invalid", age: 130 };
   const errors = validateUser(user);
   console.log(errors);
   ```

---

## **5. Case Study: Type-Safe API Integration**
### **Scenario**
- Fetch and display data from a public API using TypeScript.

### **Steps**
1. **Fetch Data**:
   ```typescript
   import axios from "axios";

   interface Post {
     id: number;
     title: string;
     body: string;
   }

   async function fetchPosts(): Promise<Post[]> {
     const response = await axios.get<Post[]>("https://jsonplaceholder.typicode.com/posts");
     return response.data;
   }
   ```

2. **Display Data**:
   ```typescript
   fetchPosts().then((posts) => {
     posts.forEach((post) => {
       console.log(`${post.id}: ${post.title}`);
     });
   });
   ```

---

## **6. Practice Exercises**
1. Migrate a small to-do list app from JavaScript to TypeScript.
2. Build a REST API with endpoints for creating, reading, updating, and deleting users.
3. Create a React app that fetches and displays data from a public API.
4. Write a validation utility for a contact form using TypeScript.

---

Small projects and case studies are an excellent way to apply TypeScript concepts in real-world scenarios, helping you build confidence and expertise.
