
# Linting and Formatting in TypeScript

---

## **Objective:**
Learn how to set up linting and formatting tools like ESLint and Prettier in a TypeScript project to ensure code consistency and quality.

---

## **1. Why Use Linting and Formatting?**
- **Linting:** Identifies and fixes coding errors and enforces coding standards.
- **Formatting:** Ensures consistent code style across the project.
- Improves readability and maintainability of the codebase.

---

## **2. Setting Up ESLint**
### **2.1. Installing ESLint**
- Install ESLint and its TypeScript plugin:
```bash
npm install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev
```

### **2.2. Configuring ESLint**
- Create an ESLint configuration file (`.eslintrc.json`):
```json
{
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": 2020,
    "sourceType": "module"
  },
  "plugins": ["@typescript-eslint"],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended"
  ],
  "rules": {
    "semi": ["error", "always"],
    "quotes": ["error", "double"]
  }
}
```

### **2.3. Running ESLint**
- Add a script to your `package.json`:
```json
"scripts": {
  "lint": "eslint . --ext .ts"
}
```
- Run ESLint:
```bash
npm run lint
```

---

## **3. Setting Up Prettier**
### **3.1. Installing Prettier**
- Install Prettier and its TypeScript plugin:
```bash
npm install prettier eslint-config-prettier eslint-plugin-prettier --save-dev
```

### **3.2. Configuring Prettier**
- Create a Prettier configuration file (`.prettierrc`):
```json
{
  "semi": true,
  "singleQuote": false,
  "printWidth": 80,
  "tabWidth": 2
}
```

### **3.3. Integrating Prettier with ESLint**
- Update the ESLint configuration:
```json
{
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ]
}
```

---

## **4. Automatically Fixing Issues**
- Add a script to automatically fix linting and formatting issues:
```json
"scripts": {
  "lint:fix": "eslint . --ext .ts --fix",
  "format": "prettier --write ."
}
```
- Run the scripts:
```bash
npm run lint:fix
npm run format
```

---

## **5. Linting and Formatting in VSCode**
- Install the following extensions:
  - **ESLint**: For linting.
  - **Prettier - Code Formatter**: For formatting.
- Configure VSCode to use Prettier:
  - Open settings (`Ctrl + ,`) and search for "Prettier".
  - Set `"editor.defaultFormatter": "esbenp.prettier-vscode"`.
  - Enable `"editor.formatOnSave": true`.

---

## **6. Linting and Formatting in CI/CD**
- Add linting and formatting checks to your CI/CD pipeline to enforce quality:
```bash
npm run lint
npm run format --check
```

---

## **7. Practice Exercises**
1. Set up ESLint in a TypeScript project and configure it to enforce double quotes and semicolons.
2. Configure Prettier in the same project to enforce single quotes and a tab width of 4.
3. Add scripts to automatically fix linting and formatting issues.
4. Integrate linting and formatting checks in a GitHub Actions workflow.

---

Proper linting and formatting ensure a clean and consistent codebase, which helps improve collaboration and reduces potential errors in TypeScript projects.
