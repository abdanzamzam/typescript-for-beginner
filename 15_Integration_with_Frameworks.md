
# Integration with Frameworks in TypeScript

---

## **Objective:**
Understand how to use TypeScript with popular frameworks such as React, Angular, and Node.js to build robust and type-safe applications.

---

## **1. Why Use TypeScript with Frameworks?**
- **Improved Type Safety:** Reduces runtime errors by catching issues during development.
- **Enhanced Development Experience:** Offers better autocompletion, refactoring, and debugging.
- **Scalability:** Helps maintain large codebases by enforcing strict type rules.

---

## **2. Using TypeScript with React**
### **2.1. Setting Up a React Project with TypeScript**
- Create a new React app using TypeScript:
```bash
npx create-react-app my-app --template typescript
```

### **2.2. TypeScript in React Components**
- **Function Components**:
```typescript
interface Props {
  name: string;
  age: number;
}

const User: React.FC<Props> = ({ name, age }) => {
  return (
    <div>
      <p>Name: {name}</p>
      <p>Age: {age}</p>
    </div>
  );
};

export default User;
```

- **Class Components**:
```typescript
import React, { Component } from "react";

interface Props {
  name: string;
}

interface State {
  count: number;
}

class Counter extends Component<Props, State> {
  state: State = { count: 0 };

  increment = (): void => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <h1>{this.props.name}</h1>
        <button onClick={this.increment}>Count: {this.state.count}</button>
      </div>
    );
  }
}

export default Counter;
```

---

## **3. Using TypeScript with Angular**
### **3.1. Setting Up an Angular Project with TypeScript**
- Angular comes with TypeScript by default. Create a new project:
```bash
ng new my-angular-app
```

### **3.2. TypeScript in Angular Components**
- **Defining a Component**:
```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-user",
  template: `
    <h1>{{ name }}</h1>
    <p>Age: {{ age }}</p>
  `,
})
export class UserComponent {
  name: string = "Alice";
  age: number = 30;
}
```

- **Using Interfaces for Models**:
```typescript
export interface User {
  id: number;
  name: string;
}

@Component({
  selector: "app-users",
  template: `
    <ul>
      <li *ngFor="let user of users">{{ user.name }}</li>
    </ul>
  `,
})
export class UsersComponent {
  users: User[] = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
  ];
}
```

---

## **4. Using TypeScript with Node.js**
### **4.1. Setting Up a Node.js Project with TypeScript**
- Initialize a Node.js project with TypeScript:
```bash
mkdir my-node-app
cd my-node-app
npm init -y
npm install typescript @types/node ts-node --save-dev
npx tsc --init
```

### **4.2. Writing a Simple Express Server**
- **Installing Required Packages**:
```bash
npm install express @types/express
```

- **Creating the Server**:
```typescript
import express, { Request, Response } from "express";

const app = express();

app.get("/", (req: Request, res: Response) => {
  res.send("Hello, TypeScript with Node.js!");
});

app.listen(3000, () => {
  console.log("Server is running on port 3000");
});
```

---

## **5. Key Features of TypeScript in Frameworks**
### **5.1. React**
- Strong typing for props and state.
- Better handling of hooks (`useState`, `useEffect`) with custom types.
- Type-safe context and reducers with `useReducer`.

### **5.2. Angular**
- Built-in support for TypeScript.
- Strong typing for services, components, and modules.
- Dependency injection with typed services.

### **5.3. Node.js**
- Type-safe APIs and middleware with Express.
- Integration with TypeORM or Sequelize for type-safe database interactions.
- Using types for environment variables and configurations.

---

## **6. Practice Exercises**
1. Create a React component that accepts a list of users and displays them as a table.
2. Build an Angular service to fetch and display a list of products using a strongly typed model.
3. Implement a simple Node.js API with Express and TypeScript to handle CRUD operations for a `Task` model.

---

Integrating TypeScript with modern frameworks ensures a strong foundation for building scalable, maintainable, and error-resistant applications.
