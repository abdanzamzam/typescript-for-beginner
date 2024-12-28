
# Installation and Setup

## Prerequisites
Before starting with TypeScript, make sure you meet the following requirements:
1. **Node.js**: Download and install Node.js from the [official Node.js website](https://nodejs.org). This installation also includes npm (Node Package Manager).
2. **Code Editor**: Use a modern code editor like [Visual Studio Code](https://code.visualstudio.com/), which has built-in support for TypeScript.

---

## Installing TypeScript
There are two ways to install TypeScript: globally or locally in a project.

### Global Installation
With a global installation, you can use the `tsc` command from any directory:
```bash
npm install -g typescript
```

### Local Installation
To add TypeScript only to a specific project:
```bash
npm install typescript --save-dev
```

---

## Setting Up a TypeScript Project
Follow these steps to set up a TypeScript project:

### Step 1: Initialize the Project
1. Create a new directory for your project and navigate to it:
   ```bash
   mkdir my-typescript-project
   cd my-typescript-project
   ```

2. Initialize a `package.json` file:
   ```bash
   npm init -y
   ```

### Step 2: Install TypeScript
Install TypeScript locally for your project:
```bash
npm install typescript --save-dev
```

### Step 3: Create a `tsconfig.json` File
Generate a TypeScript configuration file:
```bash
npx tsc --init
```

This will create a `tsconfig.json` file with default settings. You can customize it as needed.

Example simple `tsconfig.json`:
```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist",
    "rootDir": "./src"
  }
}
```
- **`target`**: Specifies the JavaScript version to be generated.
- **`outDir`**: Location of the compiled JavaScript files.
- **`rootDir`**: Location of the TypeScript source files.

### Step 4: Create Source and Output Directories
Create the following directories:
```bash
mkdir src dist
```

---

## Writing Your First TypeScript Code
1. Create a file `src/index.ts`:
   ```typescript
   const greet = (name: string): string => {
       return `Hello, ${name}!`;
   };

   console.log(greet("World"));
   ```

2. Compile the TypeScript file to JavaScript:
   ```bash
   npx tsc
   ```

3. Run the generated JavaScript file:
   ```bash
   node dist/index.js
   ```

---

## Editor Integration
It is recommended to use **Visual Studio Code** for the best TypeScript development experience:
- Install the [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) extension for linting.
- Install the [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) extension for automatic code formatting.

---

## Summary
The process of installing and configuring TypeScript helps create a robust and efficient development environment. With this setup, you can start writing TypeScript code immediately with type safety and better tooling.
