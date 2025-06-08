# React Interview Questions & Answers

### What is React?

- React is a JavaScript library for building user interfaces.
- It is an open- source, component based library.
- It is created & maintained by Facebook.
- React is used to build single page applications.
- React allows us to create reusable UI components.
- ReactJS uses virtual DOM based mechanism to fill in data (views) in HTML DOM.

### What are the major features of React?

- `Component-Based Architecture`: Apps are built with `independent, reusable components` that return HTML via a render function.
- `Virtual DOM`: React uses an `in-memory DOM` to detect changes and `efficiently update` only what's needed in the real DOM.
- `JSX (JavaScript XML)`: A `syntax extension` that lets you write `HTML-like code in JavaScript`, enhancing readability and expressiveness.
- `Unidirectional Data Flow`: Data flows `one way (parent → child)`, making the app `more predictable and easier to debug`.
- `Declarative UI`: You `describe the UI for a given state`, and React `automatically updates the DOM` when data changes.
- `SPA` (Single Page Application) : A web app that loads a single HTML page and dynamically updates content without full page reloads.

### What is NPX

- NPX : node package executer.
- Its a Package runner/executer tool.
- It can execute any package that you want from the npm registry without even installing that package.
  ex: npx create- react- app my- app

### How to create react project?

#### ✅ Option 1: Using `create-react-app` (Beginner-Friendly)

#### 🔧 Command:

```bash
npx create-react-app my-app
```

#### 📦 What it does:

- Sets up a fully configured React project (Webpack, Babel, ESLint, etc.)
- Includes folder structure, dev server, and build tools

#### 📂 Structure:

```
my-app/
├── node_modules/
├── public/
├── src/
│   └── App.js
├── package.json
└── README.md
```

#### ▶️ Run the app:

```bash
cd my-app
npm start
```

#### ✅ Option 2: Using Vite (Faster, Modern Approach)

#### 🔧 Command:

```bash
npm create vite@latest my-app --template react
```

or for TypeScript:

```bash
npm create vite@latest my-app --template react-ts
```

#### ▶️ Setup:

```bash
cd my-app
npm install
npm run dev
```

#### ⚡ Benefits of Vite:

- Lightning-fast dev server
- Hot Module Replacement (HMR)
- Better suited for modern React apps

#### ✅ Option 3: Manual Setup (Advanced)

If you want full control over every tool (Webpack, Babel, etc.), you can:

1. Initialize project:

   ```bash
   npm init -y
   ```

2. Install dependencies:

   ```bash
   npm install react react-dom
   npm install --save-dev webpack webpack-cli babel-loader @babel/core @babel/preset-react
   ```

3. Create config files (`webpack.config.js`, `.babelrc`)

This is useful for learning internals but not recommended for beginners.

#### Recommendation:

- 🧑‍🎓 Beginners: Use **`create-react-app`**
- ⚡ Pros/Performance: Use **Vite**
- 🔬 Custom control: **Manual setup**

### Compare `package.json` and `package-lock.json` in a React (or any Node.js) project:

| Feature                        | `package.json`                                         | `package-lock.json`                                    |
| ------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| **Purpose**                    | Manages **project metadata** and **dependencies list** | Locks the **exact versions** of installed dependencies |
| **Created/Edited By**          | Developers manually or via `npm install --save`        | Automatically by `npm` when dependencies are installed |
| **Includes Version Ranges**    | Yes (e.g., `^1.0.0`, `~2.1.0`)                         | No, stores **exact versions** (e.g., `1.0.5`)          |
| **Tracks Nested Dependencies** | ❌ Only direct dependencies                            | ✅ All (direct and nested) dependencies                |
| **Needed for Install?**        | ✅ Required for project setup                          | ✅ Ensures consistency across environments             |
| **Version Control**            | ✅ Must be tracked in Git                              | ✅ Should be committed to Git                          |
| **Human-Readable**             | ✅ Easier to read and edit                             | ⚠️ Large, auto-generated (not meant for manual edits)  |
| **Used by**                    | Both `npm` and `yarn`                                  | Mainly `npm` (Yarn uses `yarn.lock`)                   |

#### Summary:

- Use `**package.json**` to declare what your app **needs**.
- Use `**package-lock.json**` to ensure everyone installs **exactly the same** versions.

### `dependencies` vs `devDependencies` in a Node.js/React project (`package.json`):

| Feature                      | `dependencies`                                    | `devDependencies`                                          |
| ---------------------------- | ------------------------------------------------- | ---------------------------------------------------------- |
| **Purpose**                  | Packages required for the **application to run**  | Packages needed **only during development/testing**        |
| **Installed on Production**  | ✅ Yes                                            | ❌ No (unless explicitly included)                         |
| **Examples**                 | `react`, `react-dom`, `axios`, `redux`            | `eslint`, `jest`, `webpack`, `babel`, `vite`, `typescript` |
| **Usage**                    | Used in **runtime code** (in `src/`, client-side) | Used in **build tools, testing, and development setup**    |
| **Install command**          | `npm install <package>` or `--save`               | `npm install <package> --save-dev` or `-D`                 |
| **Should be in production?** | ✅ Yes                                            | ❌ No (kept out of production bundle)                      |

#### Example in `package.json`:

```json
{
  "dependencies": {
    "react": "^18.2.0",
    "axios": "^1.3.0"
  },
  "devDependencies": {
    "eslint": "^8.0.0",
    "jest": "^29.0.0"
  }
}
```

#### Quick Rule of Thumb:

| Ask Yourself:                                            | Then Use:         |
| -------------------------------------------------------- | ----------------- |
| Will it run **in the browser** or in production?         | `dependencies`    |
| Is it only for **development, testing, or build tools**? | `devDependencies` |

### What is JSX?

- JSX stands for `JavaScript XML`.
- Allows writing `HTML-like code inside JavaScript` files.
- React uses JSX to describe UI components in a `declarative way`.

If you don't use JSX syntax then the respective JavaScript code should be written as below,

```javascript
import { createElement } from "react";

export default function App() {
  return createElement(
    "h1",
    { className: "greeting" },
    "Hello, this is a JSX Code!"
  );
}
```

Functional Component

```javascript
export default function App() {
  return <h1 className="greeting">{"Hello, this is a JSX Code!"}</h1>;
}
```

Class Component

```javascript
class App extends React.Component {
  render() {
    return <h1 className="greeting">{"Hello, this is a JSX Code!"}</h1>;
  }
}
```

`Note:` JSX is stricter than HTML

### What is React.StrictMode

- tool for `highlighting potential problems` in a react application.
- It activates `additional checks and warnings` for its descendants(child elements).
- Strict mode checks are run in `development mode` only,they do not impact the production build.
- Strict Mode helps with the below things:
  - Identifying components with unsafe lifecycles (componentWillMount)
  - Warning about legacy string ref API usage
  - Warning about deprecated findDOMNode() usage
  - Detecting unexpected side effects
  - Detecting legacy context API

```jsx
import React, { StrictMode } from "react";

<StrictMode>
  <App />
</StrictMode>;
```

Note: StrictMode renders components twice (on dev but not production) in order to
detect any problems with our code and warn us about them.

### What are component LifeCycle Methods?

- Every component in React goes through a lifecycle of events.
- The three phases are:
  1.Mounting - (constructor,getDerivedStateFromProps,render,componentDidMount)
  2.Updating - (getDerivedStateFromProps,shouldComponentUpdate,render, getSnapshotBeforeUpdate, componentDidUpdate)
  3.Unmounting - (componentWillUnmount)

#### Mounting: means putting elements into the DOM.

1.constructor()
2.static getDerivedStateFromProps(props,state)
3.render()
4.componentDidMount()

Note:- The render() method is required and will always be called,
the others are optional and will be called if you define them.

##### constructor()

- The constructor() method is called before anything else, when the component is initiated.
- It is the natural place to set up the initial state and other initial values.
- The constructor() method is called with the props, as argument,
  and you should always start by calling the 'super(props)' before anything else,
  Otherwise,this.props will be undefined.
- This will initiate the parent's constructor method and allows the component to inherit methods from its parent (React.Component).
- If you neither initialize state nor bind methods for your React component, there is no need to implement a constructor for React component.
- setState() method should not be called in the constructor(). we will get console error
  error - Can't call setState on a component that is not yet mounted

##### static getDerivedStateFromProps()

- The getDerivedStateFromProps() method is called right before rendering the element(s) in the DOM.
- This is the natural place to set the state object based on the initial props.
- It takes (props,state) as argument, and returns an object with changes to the state.
- only fires when the parent causes a re- render and not as a result of a local setState.

##### render()

- The render() method is required, and is the method that actual outputs HTML to the DOM.
- it gets re- invoked when state/props data changes.

##### componentDidMount()

- The componentDidMount() method is called after the component is rendered.
- This is a good place to initiate the network request.
- if we are going to fetch any data from an API then API call should be placed in this lifecycle method,and then we get the response, we can call the setState() method and render the element with updated data.
- good place for DOM manipulation.

#### Updating

1.static getDerivedStateFromProps(props,state)
2.shouldComponentUpdate()
3.render()
4.getSnapshotBeforeUpdate(prevProps, prevState)
5.componentDidUpdate()

##### getDerivedStateFromProps()

- while updating state/props getDerivedStateFromProps() method is called.
- This is the first method that is called when a component gets updated.
- This is still the natural place to set the state object based on the initial props.

##### shouldComponentUpdate()

- In the shouldComponentUpdate() method a boolean value should be returned that specifies whether React should continue with the rendering or not.
- The default value is true.
- shouldComponentUpdate() lifecycle shouldn't be added if the class is extending React.PureComponent.

##### getSnapshotBeforeUpdate(prevProps, prevState)

- In the getSnapshotBeforeUpdate(prevProps, prevState) method we have access to the props and state before the update,meaning that even after the update, we can check what the values were before the update.

example:

- When the component is mounting it is rendered with the favorite color "red".
- When the component has been mounted, a timer changes the state, and after one second,the favorite color becomes "yellow".
- This action triggers the update phase, and since this component has a getSnapshotBeforeUpdate() method,this method is executed, and writes a message to the empty DIV1 element.

##### componentDidUpdate()

- The componentDidUpdate() method is called after the component is updated in the DOM.
- componentDidUpdate() is invoked immediately after the state is updated.
- This method is not called for the initial render,componentDidMount() will be called for the initial render.
- it gets called only when state/props gets updated.

#### Unmounting - Removing the component from DOM

- The next phase in the lifecycle is when a component is removed from the DOM,or unmounting.
- React has only one built- in method that gets called when a component is unmounted.

##### componentWillUnmount()

- Called immediately before a component is destroyed.
- Perform any necessary cleanup in this method, such as cancel network requests,
  or cleaning up any DOM elements created in componentDidMount.
- clearTimeout, ClearInterval , Unsubscribe, detachEventHandlers

### What are Pure Components in React?

- A `Pure Component` is a component that `renders the same output` for the `same props and state`.
- It implements `shouldComponentUpdate()` with a `shallow comparison` of props and state.
- Helps in `avoiding unnecessary re-renders`.

#### ✅ Syntax (Class Component):

```tsx
import React, { PureComponent } from "react";

class MyComponent extends PureComponent {
  render() {
    return <div>{this.props.name}</div>;
  }
}
```

#### ✅ Functional Component Equivalent:

Use **`React.memo()`**:

```tsx
const MyComponent = React.memo((props) => {
  return <div>{props.name}</div>;
});
```

#### 🧠 Key Points:

- Best for **performance optimization**.
- Only works with **primitive values** (or deeply memoized objects).
- Use when component's render output is **purely based on props/state**.

### What is the difference between state and props?

### State

- `Definition:`
  State is a data structure that is managed within a component. It represents information that can change over the lifetime of the component.
- `Mutability:`
  State is mutable, meaning it can be changed using the setter function (`setState` in class components or the updater function from `useState` in functional components).
- `Scope:`
  State is local to the component where it is defined. Only that component can modify its own state.
- `Usage:`
  State is typically used for data that needs to change in response to user actions, network responses, or other dynamic events.
- `Re-rendering:`
  Updating the state triggers a re-render of the component and its descendants.

```javascript
import { useState } from "react";

function User() {
  const [message, setMessage] = useState("Welcome to React world");

  return (
    <div>
      <h1>{message}</h1>
    </div>
  );
}
```

Class Component

```javascript
import React from "react";
class User extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      message: "Welcome to React world",
    };
  }

  render() {
    return (
      <div>
        <h1>{this.state.message}</h1>
      </div>
    );
  }
}
```

### Prop

- `Definition:`
  Props (short for “properties”) are inputs to a component, provided by its parent component.
- `Mutability:`
  Props are read-only. A component cannot modify its own props; they are immutable from the component’s perspective.
- `Scope:`
  Props are used to pass data and event handlers down the component tree, enabling parent components to configure or communicate with their children.
- `Usage:`
  Props are commonly used to make components reusable and configurable. They allow the same component to be rendered with different data or behavior.
- `Analogy:`
  Think of props as arguments to a function, whereas state is like variables declared inside the function.

  ```jsx
  import React from "react";

  const ChildComponent = (props) => {
    return (
      <div>
        <p>{props.name}</p>
        <p>{props.age}</p>
        <p>{props.gender}</p>
      </div>
    );
  };

  const ParentComponent = () => {
    return (
      <div>
        <ChildComponent name="John" age="30" gender="male" />
        <ChildComponent name="Mary" age="25" geneder="female" />
      </div>
    );
  };
  ```

Class Component

```jsx
class ChildComponent extends React.Component {
  render() {
    return (
      <div>
        <p>{this.props.name}</p>
        <p>{this.props.age}</p>
        <p>{this.props.gender}</p>
      </div>
    );
  }
}
```

#### Summary Table

| Feature    | State                              | Props                              |
| ---------- | ---------------------------------- | ---------------------------------- |
| Managed by | The component itself               | Parent component                   |
| Mutable    | Yes                                | No (read-only)                     |
| Scope      | Local to the component             | Passed from parent to child        |
| Usage      | Manage dynamic data and UI changes | Configure and customize component  |
| Update     | Using setState/useState            | Cannot be updated by the component |

### What is the difference between HTML and React event handling?

1. In HTML, the event name usually represents in `lowercase as a convention:

```html
<button onclick="activateLasers()"></button>
```

Whereas in React it follows _camelCase_ convention:

```javascript
<button onClick={activateLasers}>
```

2. In HTML, you can return `false` to prevent default behavior:

```html
<a href="#" onclick='console.log("The link was clicked."); return false;' />
```

Whereas in React you must call `preventDefault()` explicitly:

```javascript
function handleClick(event) {
  event.preventDefault();
  console.log("The link was clicked.");
}
```

3. In HTML, you need to invoke the function by appending `()`, Whereas in react you should not append `()` with the function name. (refer "activateLasers" function in the first point for example)

### What are Synthetic Events in React?

- `Synthetic Events` are `React’s wrapper` around the browser’s native DOM events.
- They provide a `consistent and cross-browser-compatible API` for handling events.

#### ✅ Example:

```tsx
function Button() {
  const handleClick = (event: React.MouseEvent<HTMLButtonElement>) => {
    console.log("Clicked!", event);
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```

#### 🧠 Key Features:

| Feature                   | Description                                                                        |
| ------------------------- | ---------------------------------------------------------------------------------- |
| **Cross-browser**         | Normalizes event behavior across different browsers.                               |
| **Event pooling**         | React used to reuse event objects for performance (deprecated in React 17+).       |
| **Same API**              | Works similarly to native DOM events (e.g., `event.target`).                       |
| **SyntheticEvent object** | Contains all standard properties/methods like `stopPropagation`, `preventDefault`. |

#### Types of Synthetic Events:

- `MouseEvent`
- `KeyboardEvent`
- `FocusEvent`
- `ChangeEvent`
- `FormEvent`, etc.

### What Are Inline Conditional Expressions in React?

`Inline conditional expressions` are a way to conditionally render elements `directly inside JSX`, often using `ternary operators` or `logical AND (&&)`.

---

#### ✅ Common Patterns

#### 1. **Ternary Operator**

```tsx
{
  isLoggedIn ? <LogoutButton /> : <LoginButton />;
}
```

- Best when you need to choose between **two components or values**.

---

#### 2. **Logical AND (`&&`)**

```tsx
{
  isAdmin && <AdminPanel />;
}
```

- Renders `AdminPanel` **only if** `isAdmin` is truthy.

---

#### 🧠 Use Cases

| Expression     | Use When You Need To...                            |
| -------------- | -------------------------------------------------- |
| `cond ? A : B` | Choose between two elements                        |
| `cond && A`    | Conditionally render one element if condition true |
| `!cond && A`   | Show an element if condition is false              |

---

#### ❗ Caveats

- `false`, `null`, and `undefined` won’t render anything.
- `0` will **render**, which may be unexpected:

```tsx
{
  0 && <Component />;
} // renders 0 (not empty)
```

### 🔑 What is the `key` Prop in React?

- The `key` prop is a `special attribute` used by React to `identify` which items in a list have `changed, been added, or removed`.
- It helps `React optimize rendering` and `improve performance` by minimizing DOM updates.

#### ✅ Syntax Example:

```tsx
const users = ["Alice", "Bob", "Charlie"];

<ul>
  {users.map((user) => (
    <li key={user}>{user}</li>
  ))}
</ul>;
```

#### 🧠 Why `key` is Important:

| Purpose                   | Explanation                                                  |
| ------------------------- | ------------------------------------------------------------ |
| 🔄 Efficient Re-rendering | Helps React know what to re-render instead of replacing all. |
| 🧠 Keeps Component State  | Retains state when the list updates (like inputs in a form). |
| ⚠️ Avoids Bugs            | Prevents unwanted behavior in dynamic lists.                 |

#### 🚫 Bad `key` Usage:

```tsx
// DO NOT use index as key if list is dynamic or reorderable
<li key={index}>{item}</li>
```

- This can cause **bugs with component state** when items change order or are removed.

#### ✅ Best Practice:

- Use **unique, stable IDs** from your data (e.g., user ID, database ID).

```tsx
<li key={user.id}>{user.name}</li>
```

#### 🔁 Force Re-render Using `key`

- Changing a component’s `key` forces React to `unmount and remount` it.

```tsx
<Component key={someUniqueValue} />
```

Useful for resetting state or restarting component lifecycle.

### What is Virtual DOM?

- The `Virtual DOM (VDOM)` is a `lightweight JavaScript representation` of the real DOM.
- React uses it to `track changes` in the UI efficiently.
- When state or props change, React:

  1. Creates a new Virtual DOM.
     ![vdom](images/vdom1.png)
  2. Compares it with the previous one (diffing).
     ![vdom2](images/vdom2.png)
  3. Updates only the changed parts in the real DOM (reconciliation).
     ![vdom3](images/vdom3.png)

- This process boosts `performance and efficiency`, avoiding unnecessary DOM manipulations.

### What is React Fiber?

- `React Fiber` is the `reconciliation engine` introduced in React 16.
- It’s a complete rewrite of the core algorithm that improves:

  - `Incremental rendering`
  - `Prioritization of updates`
  - `Pause, abort, and resume work`

- Enables `better performance`, especially for animations and complex UI updates.
- Helps React handle large applications with `smoother UI rendering` and `fine-grained control` over component updates.

### 🔁 What is Reconciliation in React?

`Reconciliation` is the process React uses to `compare the new Virtual DOM` with the `previous one` to determine the `minimum number of changes` required to update the `real DOM`.

#### 🧠 Why It Matters:

- DOM updates are `expensive`, so React uses reconciliation to:

  - `Identify differences` efficiently
  - `Apply only necessary updates`
  - `Boost performance`

#### ⚙️ How Reconciliation Works:

1. `Render Phase`:

   - Your component re-renders due to state/prop changes.
   - React creates a `new Virtual DOM`.

2. `Diffing Algorithm`:

   - React compares the `new Virtual DOM` with the `previous one`.
   - Uses heuristics (like `key` props) to detect changes.

3. `Update Phase`:

   - React calculates the `minimal set of operations`.
   - Then updates the `actual DOM` accordingly.

#### 🔑 Key Concepts in Reconciliation:

| Concept             | Explanation                                                             |
| ------------------- | ----------------------------------------------------------------------- |
| **Virtual DOM**     | Lightweight copy of the real DOM used to detect changes                 |
| **Keys**            | Help React identify which items changed in lists                        |
| **Pure Components** | Avoid unnecessary reconciliation by skipping re-renders with same props |

#### 🧪 Real-World Analogy:

Think of it like **editing a document**:

- You don’t rewrite the whole thing—you just fix the changed words.
- React does the same with the DOM during reconciliation.

### What are controlled components?

- In React, a **controlled component** is a form element (like input, textarea, select) whose **value is controlled by React state**.
- The input’s value is **tied to a state variable**, and changes are handled via `onChange`.

---

#### ✅ Example:

```tsx
const [name, setName] = useState("");

<input value={name} onChange={(e) => setName(e.target.value)} />;
```

---

### Key Points:

- React has full control over the form data.
- Makes validation, formatting, and conditional rendering easier.
- Ensures a **single source of truth** (React state).

### What are uncontrolled components?

- `Uncontrolled components` are form elements where the `DOM itself manages the state`, not React.
- React accesses the input values using `ref` instead of `useState`.

### ✅ Example:

```tsx
import { useRef } from "react";

function Form() {
  const inputRef = useRef<HTMLInputElement>(null);

  const handleSubmit = () => {
    alert(inputRef.current?.value);
  };

  return (
    <>
      <input type="text" defaultValue="Hello" ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```

### 🧠 Key Points:

- Uses `defaultValue` instead of `value`.
- Easier for **simple forms**, file uploads, or 3rd-party integrations.
- React doesn’t track or control user input in real-time.
- Less code, but **less control** (harder to do validation, conditional rendering, etc.).

### Difference Between Controlled and Uncontrolled Components

| Feature             | Controlled Component                              | Uncontrolled Component                            |
| ------------------- | ------------------------------------------------- | ------------------------------------------------- |
| **Data Source**     | React state                                       | DOM (internal state of the element)               |
| **Value Access**    | Via `state`                                       | Via `ref`                                         |
| **Form Control**    | Fully controlled by React                         | Partially managed by the DOM                      |
| **Use Case**        | Complex forms, validation, conditional logic      | Simple forms or when less React control is needed |
| **Example Input**   | `<input value={value} onChange={handleChange} />` | `<input defaultValue="John" ref={inputRef} />`    |
| **Code Complexity** | Slightly more verbose                             | Simpler, less boilerplate                         |

### What is the difference between createElement and cloneElement?

- JSX elements will be transpiled to `React.createElement()` functions to create React elements which are going to be used for the object representation of UI.
- Whereas `cloneElement` is used to clone an element and pass it new props.

### What is Lifting State Up in React?

- When several components need to `share the same changing data` then it is recommended to _lift the shared state up_ to their closest common ancestor.
- That means if two child components share the same data from its parent, then move the state to parent instead of maintaining local state in both of the child components.

### What are Higher-Order Components (HOCs)?

- A `Higher-Order Component (HOC)` is a `function` that takes a component and returns a new enhanced component.
- It is a `pattern for code reuse` in React.

#### ✅ Syntax:

```tsx
const EnhancedComponent = withSomething(OriginalComponent);
```

#### 🧠 Purpose:

- Add **shared logic** (like logging, authentication, theming) without repeating code.
- Work like wrappers: take an existing component and return an extended version.

#### ✅ Real-World Example:

```tsx
function withLogger(WrappedComponent) {
  return function (props) {
    console.log("Props:", props);
    return <WrappedComponent {...props} />;
  };
}

// Usage
const LoggedButton = withLogger(Button);
```

#### 📝 Key Points:

- HOCs do **not modify** the original component.
- Common use cases: authentication (`withAuth`), theming (`withTheme`), data fetching (`withData`).
- **Convention:** HOC names start with `with`.

### What is `children` Prop in React?

- The `children` prop is a `special prop` automatically passed to every component.
- It represents the `content nested between the opening and closing tags` of a component.

#### ✅ Example:

```tsx
function Wrapper({ children }) {
  return <div className="box">{children}</div>;
}

// Usage
<Wrapper>
  <p>Hello from inside!</p>
</Wrapper>;
```

Here, the `<p>` element is passed as `children` to `Wrapper`.

#### 🧠 Key Points:

- `children` can be:

  - A single element
  - Multiple elements
  - Text
  - A function (in advanced patterns)

- Useful for creating **reusable layouts**, **modal components**, **wrappers**, etc.

### How to write comments in React?

- The comments in React/JSX are similar to JavaScript Multiline comments but are wrapped in curly braces.

  `Single-line comments:`

  ```javascript
  <div>
    {/* Single-line comments(In vanilla JavaScript, the single-line comments are represented by double slash(//)) */}
    {`Welcome ${user}, let's play React`}
  </div>
  ```

  `Multi-line comments:`

  ```javascript
  <div>
    {/* Multi-line comments for more than
     one line */}
    {`Welcome ${user}, let's play React`}
  </div>
  ```

### Does the lazy function support named exports?

No, **`React.lazy()` does \***not**\* support named exports.**

#### ✅ It **only supports default exports**.

When using `React.lazy()`, you **must export the component as the default export** from the module you're importing.

#### ❌ **Incorrect (named export)**:

```tsx
// MyComponent.tsx
export const MyComponent = () => <div>Hello</div>;

// App.tsx
const LazyComponent = React.lazy(() => import("./MyComponent")); // ❌ This will fail!
```

#### ✅ **Correct (default export)**:

```tsx
// MyComponent.tsx
const MyComponent = () => <div>Hello</div>;
export default MyComponent;

// App.tsx
const LazyComponent = React.lazy(() => import("./MyComponent")); // ✅ Works!
```

#### ✅ Workaround for Named Exports:

If you still want to use named exports, you can **re-export as default** during import:

```tsx
// Lazy import with named export workaround
const LazyComponent = React.lazy(() =>
  import("./MyComponent").then((module) => ({ default: module.MyComponent }))
);
```

### Why Does React Use `className` Instead of `class`?

- `class` is a `reserved keyword in JavaScript` (used for defining classes).
- To avoid conflicts and confusion, React uses `className` as the attribute for specifying CSS classes in JSX.
- `className` corresponds directly to the DOM property `element.className`.

---

#### Key Points:

| Reason                          | Explanation                                                                              |
| ------------------------------- | ---------------------------------------------------------------------------------------- |
| **JavaScript Keyword Conflict** | `class` is reserved in JS, so React uses `className` to avoid syntax errors.             |
| **DOM Property Mapping**        | `className` maps to the DOM's `className` property, making manipulation straightforward. |
| **JSX Syntax Rules**            | JSX is JavaScript XML; using `className` fits better in JS code.                         |

---

### Example:

```jsx
// React JSX
<div className="container">Hello</div>
```

Equivalent to HTML:

```html
<div class="container">Hello</div>
```

### What Are Fragments in React?

- **Fragments** let you group a list of children **without adding extra nodes** to the DOM.
- Useful when you want to return multiple elements from a component **without wrapping them in a div or other container**.

#### Why Use Fragments?

- Avoid unnecessary **extra wrappers** in the DOM.
- Keeps the DOM cleaner and more semantic.
- Helps prevent layout or styling issues caused by extra elements.

#### Syntax:

#### 1. Using React Fragment:

```jsx
import React from "react";

function MyComponent() {
  return (
    <React.Fragment>
      <h1>Title</h1>
      <p>Description</p>
    </React.Fragment>
  );
}
```

#### 2. Using Short Syntax (empty tags):

```jsx
function MyComponent() {
  return (
    <>
      <h1>Title</h1>
      <p>Description</p>
    </>
  );
}
```

#### Note:

- Short syntax `<>...</>` **does not support keys or attributes**.
- Use `<React.Fragment key={someKey}>...</React.Fragment>` when keys are needed (e.g., in lists).

### What Are Portals in React?

- `Portals` provide a way to render a React component’s children `into a DOM node outside the parent component’s DOM hierarchy`.
- Useful for things like `modals, tooltips, dropdowns`, or any UI that needs to visually break out of its container.

---

#### Why Use Portals?

- Avoid `CSS overflow, z-index, or stacking context issues` by rendering outside parent containers.
- Maintain `React component hierarchy` while controlling DOM placement.

---

#### Syntax:

```jsx
import ReactDOM from "react-dom";

function Modal({ children }) {
  return ReactDOM.createPortal(
    children,
    document.getElementById("modal-root") // separate DOM node outside app root
  );
}
```

---

#### Example:

```jsx
function App() {
  return (
    <>
      <h1>App Content</h1>
      <Modal>
        <div className="modal">This is a modal rendered via Portal!</div>
      </Modal>
    </>
  );
}
```

---

#### Key Points:

| Feature                 | Description                                   |
| ----------------------- | --------------------------------------------- |
| `Maintains React tree`  | Keeps parent-child relationship in React code |
| `DOM placement control` | Renders children elsewhere in the DOM         |
| `Useful for UI layers`  | Ideal for modals, tooltips, popovers          |

### Stateless Components vs Stateful Components in React

| Aspect               | Stateless Components                                                              | Stateful Components                                                   |
| -------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Definition**       | Components that **do not manage state** internally; purely render based on props. | Components that **manage and maintain their own state**.              |
| **State Usage**      | No internal state (`useState` or `this.state`)                                    | Has internal state (`useState` in functional, `this.state` in class)  |
| **Side Effects**     | Usually no side effects                                                           | May have side effects (API calls, event handlers)                     |
| **Example**          | Functional component without state:                                               | Functional or class component with state:                             |
|                      | \`\`\`jsx                                                                         | \`\`\`jsx                                                             |
|                      | const Hello = ({ name }) => <h1>Hello {name}</h1>;                                | function Counter() {                                                  |
|                      |                                                                                   | const \[count, setCount] = useState(0);                               |
|                      |                                                                                   | return \<button onClick={() => setCount(count + 1)}>{count}</button>; |
|                      |                                                                                   | }                                                                     |
| **Class Components** | Can be stateless by only implementing `render()` method                           | Stateful by having `this.state` and lifecycle methods                 |
| **Purpose**          | Presentational, reusable UI components                                            | Handle business logic, user interaction, and lifecycle                |
| **Rendering**        | Faster, simpler, easier to test                                                   | Slightly more complex, needs proper state management                  |
| **Modern React**     | Mostly functional stateless components with hooks (can be stateful now)           | Class components traditionally stateful; hooks have blurred the line  |

---

#### Summary:

- **Stateless = No internal state, just props → UI display.**
- **Stateful = Manages own state → interactive, dynamic behavior.**

### How to Apply Validation on Props in React

The most common way to validate props in React is by using **PropTypes**.

---

#### What is PropTypes?

- A **runtime type-checking** tool for React props.
- Helps catch bugs by validating the data type and presence of props.
- Works for **JavaScript projects** (not needed in TypeScript as it provides static typing).

---

#### How to Use PropTypes:

1. **Install prop-types package (if not installed):**

```bash
npm install prop-types
```

2. **Import PropTypes in your component:**

```jsx
import PropTypes from "prop-types";
```

3. **Define prop types for your component:**

```jsx
function MyComponent({ name, age, isAdmin }) {
  return (
    <div>
      <p>Name: {name}</p>
      <p>Age: {age}</p>
      <p>Admin: {isAdmin ? "Yes" : "No"}</p>
    </div>
  );
}

MyComponent.propTypes = {
  name: PropTypes.string.isRequired, // Required string prop
  age: PropTypes.number, // Optional number prop
  isAdmin: PropTypes.bool, // Optional boolean prop
};
```

#### Common PropTypes Validators:

| Validator           | Description                   |
| ------------------- | ----------------------------- |
| `PropTypes.string`  | String                        |
| `PropTypes.number`  | Number                        |
| `PropTypes.bool`    | Boolean                       |
| `PropTypes.func`    | Function                      |
| `PropTypes.array`   | Array                         |
| `PropTypes.object`  | Object                        |
| `PropTypes.node`    | Anything that can be rendered |
| `PropTypes.element` | React element                 |
| `.isRequired`       | Makes the prop required       |

#### Example with Default Props:

```jsx
MyComponent.defaultProps = {
  age: 18,
  isAdmin: false,
};
```

#### Notes:

- PropTypes only run **in development mode**, not in production.
- In **TypeScript**, use interfaces or types for static props validation instead.

### What are the limitations of React?

    Apart from the advantages, there are few limitations of React too,

    1. React is just a view library, not a full framework.
    2. There is a learning curve for beginners who are new to web development.
    3. Integrating React into a traditional MVC framework requires some additional configuration.
    4. The code complexity increases with inline templating and JSX.
    5. Too many smaller components leading to over engineering or boilerplate.

### What is the use of `react-dom` package?

- **`react-dom`** is a package that provides **DOM-specific methods** for React.
- It is responsible for **rendering React components into the actual DOM** in web browsers.
- It acts as the **bridge between React components and the browser DOM**.

#### Key Uses:

| Method                              | Purpose                                                                     |
| ----------------------------------- | --------------------------------------------------------------------------- |
| `ReactDOM.render()`                 | Render a React component tree into a DOM node (usually the root element).   |
| `ReactDOM.createPortal()`           | Render children into a DOM node outside the parent hierarchy (for portals). |
| `ReactDOM.unmountComponentAtNode()` | Remove a mounted React component from the DOM.                              |

#### Example:

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

#### Summary:

- **`react-dom` handles rendering React components into the browser DOM.**
- Separates React core logic (`react` package) from DOM-specific implementations.
- Enables advanced features like **portals** for rendering outside normal DOM tree.

### How to use innerHTML in React?

- The `dangerouslySetInnerHTML` attribute is React's replacement for using `innerHTML` in the browser DOM.
- Just like `innerHTML`, it is risky to use this attribute considering cross-site scripting (XSS) attacks.

  In this example MyComponent uses `dangerouslySetInnerHTML` attribute for setting HTML markup:

  ```javascript
  function createMarkup() {
    return { __html: "First &middot; Second" };
  }

  function MyComponent() {
    return <div dangerouslySetInnerHTML={createMarkup()} />;
  }
  ```

### How to use styles in React?

- The `style` attribute accepts a JavaScript object with `camelCased` properties rather than a CSS string. - This is consistent with the DOM style JavaScript property, is more efficient, and prevents XSS security holes.

  ```javascript
  const divStyle = {
    color: "blue",
    backgroundImage: "url(" + imgUrl + ")",
  };

  function HelloWorldComponent() {
    return <div style={divStyle}>Hello World!</div>;
  }
  ```

- Style keys are camelCased in order to be consistent with accessing the properties on DOM nodes in JavaScript (e.g. `node.style.backgroundImage`).

### Why we need to be careful when spreading props on DOM elements?

- When we `spread props` we run into the risk of adding unknown HTML attributes, which is a bad practice.
- Instead we can use prop destructuring with `...rest` operator, so it will add only required props.

  For example,

  ```javascript
  const ComponentA = () => (
    <ComponentB isDisplay={true} className={"componentStyle"} />
  );

  const ComponentB = ({ isDisplay, ...domProps }) => (
    <div {...domProps}>{"ComponentB"}</div>
  );
  ```

### How to Implement Server Side Rendering (SSR) in React?

#### What is SSR?

- SSR means **rendering React components on the server** into HTML before sending to the client.
- Improves **initial load performance**, **SEO**, and **user experience**.

#### Common Ways to Implement SSR in React:

| Method                       | Description                                                    |
| ---------------------------- | -------------------------------------------------------------- |
| **Using Next.js**            | A popular React framework with built-in SSR support.           |
| **Using ReactDOMServer API** | Manually render components on server using `renderToString()`. |

#### 1. Using ReactDOMServer (Manual SSR)

- Use `react-dom/server` package on Node.js backend.
- Convert React components to HTML string.
- Send HTML string as response.

```js
import express from "express";
import ReactDOMServer from "react-dom/server";
import React from "react";
import App from "./App";

const app = express();

app.get("*", (req, res) => {
  const html = ReactDOMServer.renderToString(<App />);
  res.send(`
    <!DOCTYPE html>
    <html>
      <head><title>SSR React</title></head>
      <body>
        <div id="root">${html}</div>
        <script src="/bundle.js"></script>
      </body>
    </html>
  `);
});

app.listen(3000);
```

#### 2. Using Next.js (Recommended)

- Next.js automatically handles SSR for pages.
- You write React components as usual.
- Use special functions like `getServerSideProps` to fetch data on server.

```js
// pages/index.js
export async function getServerSideProps() {
  // fetch data here
  return { props: { data } };
}

export default function Home({ data }) {
  return <div>{data}</div>;
}
```

### How to enable production mode in React?

- You should use Webpack's `DefinePlugin` method to set `NODE_ENV` to `production`, by which it strip out things like propType validation and extra warnings.

### What is a switching component?

- A _switching component_ is a component that renders one of many components. We need to use object to map prop values to components.

  For example, a switching component to display different pages based on `page` prop:

  ```javascript
  import HomePage from "./HomePage";
  import AboutPage from "./AboutPage";
  import ServicesPage from "./ServicesPage";
  import ContactPage from "./ContactPage";

  const PAGES = {
    home: HomePage,
    about: AboutPage,
    services: ServicesPage,
    contact: ContactPage,
  };

  const Page = (props) => {
    const Handler = PAGES[props.page] || ContactPage;

    return <Handler {...props} />;
  };

  // The keys of the PAGES object can be used in the prop types to catch dev-time errors.
  Page.propTypes = {
    page: PropTypes.oneOf(Object.keys(PAGES)).isRequired,
  };
  ```

### Why Should Component Names Start with a Capital Letter in React?

- **React treats components with capitalized names as custom React components.**
- If a component name starts with a lowercase letter, React treats it as a **native HTML element** (like `<div>`, `<span>`, etc.).
- This distinction is important because React needs to differentiate between **HTML tags and user-defined components**.

---

#### Example:

```jsx
// Correct - treated as React component
function MyButton() {
  return <button>Click me</button>;
}

// Usage
<MyButton />; // React renders this component

// Incorrect - treated as HTML tag, will cause errors or render nothing
function mybutton() {
  return <button>Click me</button>;
}

// Usage
<mybutton />; // React looks for a native HTML tag <mybutton>, which doesn't exist
```

#### Summary:

| Reason                             | Explanation                                                                |
| ---------------------------------- | -------------------------------------------------------------------------- |
| **Capitalized names = Components** | React recognizes capitalized names as React components.                    |
| **Lowercase names = HTML tags**    | React treats lowercase as built-in HTML elements.                          |
| **Avoid rendering errors**         | Using lowercase for components can cause React to fail rendering properly. |

### Are custom DOM attributes supported in React v16?

    Yes. In the past, React used to ignore unknown DOM attributes. If you wrote JSX with an attribute that React doesn't recognize, React would just skip it.

    For example, let's take a look at the below attribute:

    ```javascript
    <div mycustomattribute={"something"} />
    ```

    Would render an empty div to the DOM with React v15:

    ```html
    <div />
    ```

    In React v16 any unknown attributes will end up in the DOM:

    ```html
    <div mycustomattribute="something" />
    ```

    This is useful for supplying browser-specific non-standard attributes, trying new DOM APIs, and integrating with opinionated third-party libraries.

### Why `for` Loop and `if-else` Don't Work Directly Inside JSX?

- **JSX expects expressions, not statements** inside `{}`.
- `for` loops and `if-else` are **statements**, not expressions.
- JSX can only embed **expressions** (values that return something).

---

#### What works in JSX?

- **Expressions** like:

  - Ternary operators (`condition ? trueExpr : falseExpr`)
  - Logical AND (`condition && expr`)
  - Array methods like `.map()` for loops

---

#### Why?

- JSX compiles to `React.createElement()` calls which expect expressions.
- `for` and `if-else` don’t return values directly; they execute code blocks.

---

#### How to handle looping and conditionals in JSX?

**Instead of `for` loop, use `.map()`**

```jsx
const items = ["a", "b", "c"];

return (
  <ul>
    {items.map((item) => (
      <li key={item}>{item}</li>
    ))}
  </ul>
);
```

**Instead of `if-else`, use ternary or logical operator**

```jsx
return <div>{isLoggedIn ? <LogoutButton /> : <LoginButton />}</div>;
```

or

```jsx
return <div>{showMessage && <Message />}</div>;
```

---

#### Summary:

| Statement                                       | Explanation                                       |
| ----------------------------------------------- | ------------------------------------------------- |
| `for` loop                                      | Not an expression → can’t be used inside JSX `{}` |
| `if-else`                                       | Also a statement, not an expression               |
| Use `.map()`, ternary operator, or `&&` instead | JSX accepts expressions, so use these inside `{}` |

### How to conditionally apply class attributes?

- You shouldn't use curly braces inside quotes because it is going to be evaluated as a string.

  ```javascript
  <div className="btn-panel {this.props.visible ? 'show' : 'hidden'}">
  ```

- Instead you need to move curly braces outside (don't forget to include spaces between class names):

  ```javascript
  <div className={'btn-panel ' + (this.props.visible ? 'show' : 'hidden')}>
  ```

- _Template strings_ will also work:

  ```javascript
  <div className={`btn-panel ${this.props.visible ? 'show' : 'hidden'}`}>
  ```

### Difference Between `React` and `ReactDOM`

| Aspect             | `React`                                              | `ReactDOM`                                       |
| ------------------ | ---------------------------------------------------- | ------------------------------------------------ |
| **Purpose**        | Core React library for building components and logic | Handles rendering of React components to the DOM |
| **Focus**          | Defines components, hooks, JSX, etc.                 | Interacts with the **browser DOM**               |
| **Where Used**     | Both client-side and server-side (like in SSR)       | Only on the **client-side (browser)**            |
| **Common Methods** | `useState`, `useEffect`, `createContext`, etc.       | `createRoot()`, `render()`, `createPortal()`     |
| **Installation**   | Installed via `react` package                        | Installed via `react-dom` package                |

---

#### Code Example:

```jsx
// Import core React functionality
import React from "react";

// Import DOM-specific rendering methods
import ReactDOM from "react-dom/client";

// Import App component
import App from "./App";

// Render to the browser DOM
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

---

#### Summary:

- `**React**` = The brain (components, hooks, logic)
- `**ReactDOM**` = The body (puts components into the real DOM)

### How to use React label element?

- If you try to render a `<label>` element bound to a text input using the standard `for` attribute, then it produces HTML missing that attribute and prints a warning to the console.

  ```javascript
  <label for={'user'}>{'User'}</label>
  <input type={'text'} id={'user'} />
  ```

- Since `for` is a reserved keyword in JavaScript, use `htmlFor` instead.

  ```javascript
  <label htmlFor={'user'}>{'User'}</label>
  <input type={'text'} id={'user'} />
  ```

### How to combine multiple inline style objects?

- You can use _spread operator_ in regular React:

  ```javascript
  <button style={{ ...styles.panel.button, ...styles.panel.submitButton }}>
    {"Submit"}
  </button>
  ```

- If you're using React Native then you can use the array notation:

  ```javascript
  <button style={[styles.panel.button, styles.panel.submitButton]}>
    {"Submit"}
  </button>
  ```

### How to re-render the view when the browser is resized?

- You can use the `useState` hook to manage the width and height state variables, and the `useEffect` hook to add and remove the `resize` event listener. The `[]` dependency array passed to useEffect ensures that the effect only runs once (on mount) and not on every re-render.

  ```javascript
  import React, { useState, useEffect } from "react";
  function WindowDimensions() {
    const [dimensions, setDimensions] = useState({
      width: window.innerWidth,
      height: window.innerHeight,
    });

    useEffect(() => {
      function handleResize() {
        setDimensions({
          width: window.innerWidth,
          height: window.innerHeight,
        });
      }
      window.addEventListener("resize", handleResize);
      return () => window.removeEventListener("resize", handleResize);
    }, []);

    return (
      <span>
        {dimensions.width} x {dimensions.height}
      </span>
    );
  }
  ```

    <details>
    <summary><h4>Using Class Component</h4></summary>

  You can listen to the `resize` event in `componentDidMount()` and then update the dimensions (`width` and `height`). You should remove the listener in `componentWillUnmount()` method.

  ```javascript
  class WindowDimensions extends React.Component {
    constructor(props) {
      super(props);
      this.updateDimensions = this.updateDimensions.bind(this);
    }

    componentWillMount() {
      this.updateDimensions();
    }

    componentDidMount() {
      window.addEventListener("resize", this.updateDimensions);
    }

    componentWillUnmount() {
      window.removeEventListener("resize", this.updateDimensions);
    }

    updateDimensions() {
      this.setState({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    }

    render() {
      return (
        <span>
          {this.state.width} x {this.state.height}
        </span>
      );
    }
  }
  ```

    </details>

### How to pretty print JSON with React?

    We can use `<pre>` tag so that the formatting of the `JSON.stringify()` is retained:

    ```javascript
    const data = { name: "John", age: 42 };

    function User {
        return <pre>{JSON.stringify(data, null, 2)}</pre>;
    }

    const container = createRoot(document.getElementById("container"));

    container.render(<User />);
    ```

      <details><summary><b>See Class</b></summary>
      <p>

    ```javascript
    const data = { name: "John", age: 42 };

    class User extends React.Component {
      render() {
        return <pre>{JSON.stringify(data, null, 2)}</pre>;
      }
    }

    React.render(<User />, document.getElementById("container"));
    ```

      </p>
      </details>

### How to focus an input element on page load?

    You need to use `useEffect` hook to set focus on input field during page load time for functional component.

    ```javascript
    import React, { useEffect, useRef } from "react";

    const App = () => {
      const inputElRef = useRef(null);

      useEffect(() => {
        inputElRef.current.focus();
      }, []);

      return (
        <div>
          <input defaultValue={"Won't focus"} />
          <input ref={inputElRef} defaultValue={"Will focus"} />
        </div>
      );
    };

    ReactDOM.render(<App />, document.getElementById("app"));
    ```

      <details><summary><b>See Class</b></summary>
      <p>
      You can do it by creating _ref_ for `input` element and using it in `componentDidMount()`:

    ```javascript
    class App extends React.Component {
      componentDidMount() {
        this.nameInput.focus();
      }

      render() {
        return (
          <div>
            <input defaultValue={"Won't focus"} />
            <input
              ref={(input) => (this.nameInput = input)}
              defaultValue={"Will focus"}
            />
          </div>
        );
      }
    }

    ReactDOM.render(<App />, document.getElementById("app"));
    ```

      </p>
      </details>

### How can we find the version of React at runtime in the browser?

    You can use `React.version` to get the version.

    ```javascript
    const REACT_VERSION = React.version;

    ReactDOM.render(
      <div>{`React version: ${REACT_VERSION}`}</div>,
      document.getElementById("app")
    );
    ```

### How to add Google Analytics for React Router?

    Add a listener on the `history` object to record each page view:

    ```javascript
    history.listen(function (location) {
      window.ga("set", "page", location.pathname + location.search);
      window.ga("send", "pageview", location.pathname + location.search);
    });
    ```

### How do you apply vendor prefixes to inline styles in React?

- React _does not_ apply _vendor prefixes_ automatically. You need to add vendor prefixes manually.

  ```javascript
  <div
    style={{
      transform: "rotate(90deg)",
      WebkitTransform: "rotate(90deg)", // note the capital 'W' here
      msTransform: "rotate(90deg)", // 'ms' is the only lowercase vendor prefix
    }}
  />
  ```

### What are the exceptions on React component naming?

- The component names should start with an uppercase letter but there are few exceptions to this convention. - The lowercase tag names with a dot (property accessors) are still considered as valid component names.
  For example, the below tag can be compiled to a valid component,

  ```javascript
       render() {
            return (
              <obj.component/> // `React.createElement(obj.component)`
            )
      }
  ```

74. ### Is it possible to use async/await in plain React?

    # Can You Use async/await in Plain React?

    Yes, you can use `async/await` in plain React, as long as your JavaScript environment supports ES2017+. Nowadays most modern browsers and build tools support ES2017+ version. If you're using `Create React App`, `Next.js`, `Remix`, or any modern React setup, `async/await` is supported out of the box through `Babel`.

    ### Example Usage

    ```jsx
    import { useEffect, useState } from "react";

    function UserProfile() {
      const [user, setUser] = useState(null);

      useEffect(() => {
        const fetchUser = async () => {
          const response = await fetch("/api/user");
          const data = await response.json();
          setUser(data);
        };

        fetchUser();
      }, []);

      return user ? <div>Hello, {user.name}</div> : <div>Loading...</div>;
    }
    ```

    But If you're not using a bundler like `Webpack or Babel`, you will need _Babel_ and [transform-async-to-generator](https://babeljs.io/docs/en/babel-plugin-transform-async-to-generator) plugin. However, React Native ships with Babel and a set of transforms.

75. ### What are the common folder structures for React?

    There are two common practices for React project file structure.

    1.  `Grouping by features or routes:`

        One common way to structure projects is locate CSS, JS, and tests together, grouped by feature or route.

        ```
        common/
        ├─ Avatar.js
        ├─ Avatar.css
        ├─ APIUtils.js
        └─ APIUtils.test.js
        feed/
        ├─ index.js
        ├─ Feed.js
        ├─ Feed.css
        ├─ FeedStory.js
        ├─ FeedStory.test.js
        └─ FeedAPI.js
        profile/
        ├─ index.js
        ├─ Profile.js
        ├─ ProfileHeader.js
        ├─ ProfileHeader.css
        └─ ProfileAPI.js
        ```

    2.  `Grouping by file type:`

        Another popular way to structure projects is to group similar files together.

        ```
        api/
        ├─ APIUtils.js
        ├─ APIUtils.test.js
        ├─ ProfileAPI.js
        └─ UserAPI.js
        components/
        ├─ Avatar.js
        ├─ Avatar.css
        ├─ Feed.js
        ├─ Feed.css
        ├─ FeedStory.js
        ├─ FeedStory.test.js
        ├─ Profile.js
        ├─ ProfileHeader.js
        └─ ProfileHeader.css
        ```

76. ### What are the popular packages for animation?

    _React Transition Group_ and _React Motion_ are popular animation packages in React ecosystem.

77. ### What is the benefit of styles modules?

    It is recommended to avoid hard coding style values in components. Any values that are likely to be used across different UI components should be extracted into their own modules.

    For example, these styles could be extracted into a separate component:

    ```javascript
    export const colors = {
      white,
      black,
      blue,
    };

    export const space = [0, 8, 16, 32, 64];
    ```

    And then imported individually in other components:

    ```javascript
    import { space, colors } from "./styles";
    ```

78. ### What are the popular React-specific linters?

    ESLint is a popular JavaScript linter. There are plugins available that analyse specific code styles. One of the most common for React is an npm package called `eslint-plugin-react`. By default, it will check a number of best practices, with rules checking things from keys in iterators to a complete set of prop types.

    Another popular plugin is `eslint-plugin-jsx-a11y`, which will help fix common issues with accessibility. As JSX offers slightly different syntax to regular HTML, issues with `alt` text and `tabindex`, for example, will not be picked up by regular plugins.

## React Router

79. ### What is React Router?

    React Router is a powerful routing library built on top of React that helps you add new screens and flows to your application incredibly quickly, all while keeping the URL in sync with what's being displayed on the page.

80. ### How React Router is different from history library?

    React Router is a wrapper around the `history` library which handles interaction with the browser's `window.history` with its browser and hash histories. It also provides memory history which is useful for environments that don't have global history, such as mobile app development (React Native) and unit testing with Node.

81. ### What are the `<Router>` components of React Router v6?

    React Router v6 provides below 4 `<Router>` components:

    1.  `<BrowserRouter>`:Uses the HTML5 history API for standard web apps.
    2.  `<HashRouter>`:Uses hash-based routing for static servers.
    3.  `<MemoryRouter>`:Uses in-memory routing for testing and non-browser environments.
    4.  `<StaticRouter>`:Provides static routing for server-side rendering (SSR).

    The above components will create _browser_, _hash_, _memory_ and _static_ history instances. React Router v6 makes the properties and methods of the `history` instance associated with your router available through the context in the `router` object.

82. ### What is the purpose of `push()` and `replace()` methods of `history`?

    A history instance has two methods for navigation purpose.

    1.  `push()`
    2.  `replace()`

    If you think of the history as an array of visited locations, `push()` will add a new location to the array and `replace()` will replace the current location in the array with the new one.

83. ### How do you programmatically navigate using React Router v4?

    There are three different ways to achieve programmatic routing/navigation within components.

    1.  `Using the `withRouter()` higher-order function:`

        The `withRouter()` higher-order function will inject the history object as a prop of the component. This object provides `push()` and `replace()` methods to avoid the usage of context.

        ```javascript
        import { withRouter } from "react-router-dom"; // this also works with 'react-router-native'

        const Button = withRouter(({ history }) => (
          <button
            type="button"
            onClick={() => {
              history.push("/new-location");
            }}
          >
            {"Click Me!"}
          </button>
        ));
        ```

    2.  `Using `<Route>` component and render props pattern:`

        The `<Route>` component passes the same props as `withRouter()`, so you will be able to access the history methods through the history prop.

        ```javascript
        import { Route } from "react-router-dom";

        const Button = () => (
          <Route
            render={({ history }) => (
              <button
                type="button"
                onClick={() => {
                  history.push("/new-location");
                }}
              >
                {"Click Me!"}
              </button>
            )}
          />
        );
        ```

    3.  `Using context:`

        This option is not recommended and treated as unstable API.

        ```javascript
        const Button = (props, context) => (
          <button
            type="button"
            onClick={() => {
              context.history.push("/new-location");
            }}
          >
            {"Click Me!"}
          </button>
        );

        Button.contextTypes = {
          history: React.PropTypes.shape({
            push: React.PropTypes.func.isRequired,
          }),
        };
        ```

84. ### How to get query parameters in React Router v4?

    The ability to parse query strings was taken out of React Router v4 because there have been user requests over the years to support different implementation. So the decision has been given to users to choose the implementation they like. The recommended approach is to use query strings library.

    ```javascript
    const queryString = require("query-string");
    const parsed = queryString.parse(props.location.search);
    ```

    You can also use `URLSearchParams` if you want something native:

    ```javascript
    const params = new URLSearchParams(props.location.search);
    const foo = params.get("name");
    ```

    You should use a _polyfill_ for IE11.

85. ### Why you get "Router may have only one child element" warning?

    You have to wrap your Route's in a `<Switch>` block because `<Switch>` is unique in that it renders a route exclusively.

    At first you need to add `Switch` to your imports:

    ```javascript
    import { Switch, Router, Route } from "react-router";
    ```

    Then define the routes within `<Switch>` block:

    ```javascript
    <Router>
      <Switch>
        <Route {/* ... */} />
        <Route {/* ... */} />
      </Switch>
    </Router>
    ```

86. ### How to pass params to `history.push` method in React Router v4?

    While navigating you can pass props to the `history` object:

    ```javascript
    this.props.history.push({
      pathname: "/template",
      search: "?name=sudheer",
      state: { detail: response.data },
    });
    ```

    The `search` property is used to pass query params in `push()` method.

87. ### How to implement _default_ or _NotFound_ page?

    A `<Switch>` renders the first child `<Route>` that matches. A `<Route>` with no path always matches. So you just need to simply drop path attribute as below

    ```javascript
    <Switch>
      <Route exact path="/" component={Home} />
      <Route path="/user" component={User} />
      <Route component={NotFound} />
    </Switch>
    ```

88. ### How to get history on React Router v4?

    Below are the list of steps to get history object on React Router v4,

    1.  Create a module that exports a `history` object and import this module across the project.

        For example, create `history.js` file:

        ```javascript
        import { createBrowserHistory } from "history";

        export default createBrowserHistory({
          /* pass a configuration object here if needed */
        });
        ```

    2.  You should use the `<Router>` component instead of built-in routers. Import the above `history.js` inside `index.js` file:

        ```javascript
        import { Router } from "react-router-dom";
        import history from "./history";
        import App from "./App";

        ReactDOM.render(
          <Router history={history}>
            <App />
          </Router>,
          holder
        );
        ```

    3.  You can also use push method of `history` object similar to built-in history object:

        ```javascript
        // some-other-file.js
        import history from "./history";

        history.push("/go-here");
        ```

89. ### How to perform automatic redirect after login?

    The `react-router` package provides `<Redirect>` component in React Router. Rendering a `<Redirect>` will navigate to a new location. Like server-side redirects, the new location will override the current location in the history stack.

    ```javascript
    import { Redirect } from "react-router";

    export default function Login {
        if (this.state.isLoggedIn === true) {
          return <Redirect to="/your/redirect/page" />;
        } else {
          return <div>{"Login Please"}</div>;
        }
    }
    ```

      <details><summary><b>See Class</b></summary>
      <p>

    ```jsx
    import React, { Component } from "react";
    import { Redirect } from "react-router";

    export default class LoginComponent extends Component {
      render() {
        if (this.state.isLoggedIn === true) {
          return <Redirect to="/your/redirect/page" />;
        } else {
          return <div>{"Login Please"}</div>;
        }
      }
    }
    ```

       </p>
       </details>

## React Internationalization

90. ### What is React Intl?

    The _React Intl_ library makes internationalization in React straightforward, with off-the-shelf components and an API that can handle everything from formatting strings, dates, and numbers, to pluralization. React Intl is part of _FormatJS_ which provides bindings to React via its components and API.

91. ### What are the main features of React Intl?

    Below are the main features of React Intl,

    1.  Display numbers with separators.
    2.  Display dates and times correctly.
    3.  Display dates relative to "now".
    4.  Pluralize labels in strings.
    5.  Support for 150+ languages.
    6.  Runs in the browser and Node.
    7.  Built on standards.

92. ### What are the two ways of formatting in React Intl?

    The library provides two ways to format strings, numbers, and dates:

    1.  `Using react components:`

        ```javascript
        <FormattedMessage
          id={"account"}
          defaultMessage={"The amount is less than minimum balance."}
        />
        ```

    2.  `Using an API:`

        ```javascript
        const messages = defineMessages({
          accountMessage: {
            id: "account",
            defaultMessage: "The amount is less than minimum balance.",
          },
        });

        formatMessage(messages.accountMessage);
        ```

93. ### How to use `<FormattedMessage>` as placeholder using React Intl?

    The `<Formatted... />` components from `react-intl` return elements, not plain text, so they can't be used for placeholders, alt text, etc. In that case, you should use lower level API `formatMessage()`. You can inject the `intl` object into your component using `injectIntl()` higher-order component and then format the message using `formatMessage()` available on that object.

    ```javascript
    import React from "react";
    import { injectIntl, intlShape } from "react-intl";

    const MyComponent = ({ intl }) => {
      const placeholder = intl.formatMessage({ id: "messageId" });
      return <input placeholder={placeholder} />;
    };

    MyComponent.propTypes = {
      intl: intlShape.isRequired,
    };

    export default injectIntl(MyComponent);
    ```

94. ### How to access current locale with React Intl?

    You can get the current locale in any component of your application using `injectIntl()`:

    ```javascript
    import { injectIntl, intlShape } from "react-intl";

    const MyComponent = ({ intl }) => (
      <div>{`The current locale is ${intl.locale}`}</div>
    );

    MyComponent.propTypes = {
      intl: intlShape.isRequired,
    };

    export default injectIntl(MyComponent);
    ```

95. ### How to format date using React Intl?

    The `injectIntl()` higher-order component will give you access to the `formatDate()` method via the props in your component. The method is used internally by instances of `FormattedDate` and it returns the string representation of the formatted date.

    ```javascript
    import { injectIntl, intlShape } from "react-intl";

    const stringDate = this.props.intl.formatDate(date, {
      year: "numeric",
      month: "numeric",
      day: "numeric",
    });

    const MyComponent = ({ intl }) => (
      <div>{`The formatted date is ${stringDate}`}</div>
    );

    MyComponent.propTypes = {
      intl: intlShape.isRequired,
    };

    export default injectIntl(MyComponent);
    ```

## React Testing

96. ### What is Shallow Renderer in React testing?

    _Shallow rendering_ is useful for writing unit test cases in React. It lets you render a component _one level deep_ and assert facts about what its render method returns, without worrying about the behavior of child components, which are not instantiated or rendered.

    For example, if you have the following component:

    ```javascript
    function MyComponent() {
      return (
        <div>
          <span className={"heading"}>{"Title"}</span>
          <span className={"description"}>{"Description"}</span>
        </div>
      );
    }
    ```

    Then you can assert as follows:

    ```javascript
    import ShallowRenderer from "react-test-renderer/shallow";

    // in your test
    const renderer = new ShallowRenderer();
    renderer.render(<MyComponent />);

    const result = renderer.getRenderOutput();

    expect(result.type).toBe("div");
    expect(result.props.children).toEqual([
      <span className={"heading"}>{"Title"}</span>,
      <span className={"description"}>{"Description"}</span>,
    ]);
    ```

97. ### What is `TestRenderer` package in React?

    This package provides a renderer that can be used to render components to pure JavaScript objects, without depending on the DOM or a native mobile environment. This package makes it easy to grab a snapshot of the platform view hierarchy (similar to a DOM tree) rendered by a ReactDOM or React Native without using a browser or `jsdom`.

    ```javascript
    import TestRenderer from "react-test-renderer";

    const Link = ({ page, children }) => <a href={page}>{children}</a>;

    const testRenderer = TestRenderer.create(
      <Link page={"https://www.facebook.com/"}>{"Facebook"}</Link>
    );

    console.log(testRenderer.toJSON());
    // {
    //   type: 'a',
    //   props: { href: 'https://www.facebook.com/' },
    //   children: [ 'Facebook' ]
    // }
    ```

98. ### What is the purpose of ReactTestUtils package?

    _ReactTestUtils_ are provided in the `with-addons` package and allow you to perform actions against a simulated DOM for the purpose of unit testing.

99. ### What is Jest?

    _Jest_ is a JavaScript unit testing framework created by Facebook based on Jasmine and provides automated mock creation and a `jsdom` environment. It's often used for testing components.

100.  ### What are the advantages of Jest over Jasmine?

      There are couple of advantages compared to Jasmine:

      - Automatically finds tests to execute in your source code.
      - Automatically mocks dependencies when running your tests.
      - Allows you to test asynchronous code synchronously.
      - Runs your tests with a fake DOM implementation (via `jsdom`) so that your tests can be run on the command line.
      - Runs tests in parallel processes so that they finish sooner.

101.  ### Give a simple example of Jest test case

      Let's write a test for a function that adds two numbers in `sum.js` file:

      ```javascript
      const sum = (a, b) => a + b;

      export default sum;
      ```

      Create a file named `sum.test.js` which contains actual test:

      ```javascript
      import sum from "./sum";

      test("adds 1 + 2 to equal 3", () => {
        expect(sum(1, 2)).toBe(3);
      });
      ```

      And then add the following section to your `package.json`:

      ```json
      {
        "scripts": {
          "test": "jest"
        }
      }
      ```

      Finally, run `yarn test` or `npm test` and Jest will print a result:

      ```console
      $ yarn test
      PASS ./sum.test.js
      ✓ adds 1 + 2 to equal 3 (2ms)
      ```

## React Redux

102. ### What is flux?

     _Flux_ is an _application design paradigm_ used as a replacement for the more traditional MVC pattern. It is not a framework or a library but a new kind of architecture that complements React and the concept of Unidirectional Data Flow. Facebook uses this pattern internally when working with React.

     The workflow between dispatcher, stores and views components with distinct inputs and outputs as follows:

     ![flux](images/flux.png)

103. ### What is Redux?

     _Redux_ is a predictable state container for JavaScript apps based on the _Flux design pattern_. Redux can be used together with React, or with any other view library. It is tiny (about 2kB) and has no dependencies.

104. ### What are the core principles of Redux?

     Redux follows three fundamental principles:

     1. `Single source of truth:` The state of your whole application is stored in an object tree within a single store. The single state tree makes it easier to keep track of changes over time and debug or inspect the application.
     2. `State is read-only:` The only way to change the state is to emit an action, an object describing what happened. This ensures that neither the views nor the network callbacks will ever write directly to the state.
     3. `Changes are made with pure functions:` To specify how the state tree is transformed by actions, you write reducers. Reducers are just pure functions that take the previous state and an action as parameters, and return the next state.

105. ### What are the downsides of Redux compared to Flux?

     Instead of saying downsides we can say that there are few compromises of using Redux over Flux. Those are as follows:

     1. `You will need to learn to avoid mutations:` Flux is un-opinionated about mutating data, but Redux doesn't like mutations and many packages complementary to Redux assume you never mutate the state. You can enforce this with dev-only packages like `redux-immutable-state-invariant`, Immutable.js, or instructing your team to write non-mutating code.
     2. `You're going to have to carefully pick your packages:` While Flux explicitly doesn't try to solve problems such as undo/redo, persistence, or forms, Redux has extension points such as middleware and store enhancers, and it has spawned a rich ecosystem.
     3. `There is no nice Flow integration yet:` Flux currently lets you do very impressive static type checks which Redux doesn't support yet.

106. ### What is the difference between `mapStateToProps()` and `mapDispatchToProps()`?

     `mapStateToProps()` is a utility which helps your component get updated state (which is updated by some other components):

     ```javascript
     const mapStateToProps = (state) => {
       return {
         todos: getVisibleTodos(state.todos, state.visibilityFilter),
       };
     };
     ```

     `mapDispatchToProps()` is a utility which will help your component to fire an action event (dispatching action which may cause change of application state):

     ```javascript
     const mapDispatchToProps = (dispatch) => {
       return {
         onTodoClick: (id) => {
           dispatch(toggleTodo(id));
         },
       };
     };
     ```

     It is recommended to always use the “object shorthand” form for the `mapDispatchToProps`.

     Redux wraps it in another function that looks like (…args) => dispatch(onTodoClick(…args)), and pass that wrapper function as a prop to your component.

     ```javascript
     const mapDispatchToProps = {
       onTodoClick,
     };
     ```

107. ### Can I dispatch an action in reducer?

     Dispatching an action within a reducer is an `anti-pattern`. Your reducer should be _without side effects_, simply digesting the action payload and returning a new state object. Adding listeners and dispatching actions within the reducer can lead to chained actions and other side effects.

108. ### How to access Redux store outside a component?

     You just need to export the store from the module where it created with `createStore()`. Also, it shouldn't pollute the global window object.

     ```javascript
     store = createStore(myReducer);

     export default store;
     ```

109. ### What are the drawbacks of MVW pattern?

     1. DOM manipulation is very expensive which causes applications to behave slow and inefficient.
     2. Due to circular dependencies, a complicated model was created around models and views.
     3. Lot of data changes happens for collaborative applications(like Google Docs).
     4. No way to do undo (travel back in time) easily without adding so much extra code.

110. ### Are there any similarities between Redux and RxJS?

     These libraries are very different for very different purposes, but there are some vague similarities.

     Redux is a tool for managing state throughout the application. It is usually used as an architecture for UIs. Think of it as an alternative to (half of) Angular. RxJS is a reactive programming library. It is usually used as a tool to accomplish asynchronous tasks in JavaScript. Think of it as an alternative to Promises. Redux uses the Reactive paradigm because the Store is reactive. The Store observes actions from a distance, and changes itself. RxJS also uses the Reactive paradigm, but instead of being an architecture, it gives you basic building blocks, Observables, to accomplish this pattern.

111. ### How to reset state in Redux?

     You need to write a _root reducer_ in your application which delegate handling the action to the reducer generated by `combineReducers()`.

     For example, let us take `rootReducer()` to return the initial state after `USER_LOGOUT` action. As we know, reducers are supposed to return the initial state when they are called with `undefined` as the first argument, no matter the action.

     ```javascript
     const appReducer = combineReducers({
       /* your app's top-level reducers */
     });

     const rootReducer = (state, action) => {
       if (action.type === "USER_LOGOUT") {
         state = undefined;
       }

       return appReducer(state, action);
     };
     ```

     In case of using `redux-persist`, you may also need to clean your storage. `redux-persist` keeps a copy of your state in a storage engine. First, you need to import the appropriate storage engine and then, to parse the state before setting it to undefined and clean each storage state key.

     ```javascript
     const appReducer = combineReducers({
       /* your app's top-level reducers */
     });

     const rootReducer = (state, action) => {
       if (action.type === "USER_LOGOUT") {
         Object.keys(state).forEach((key) => {
           storage.removeItem(`persist:${key}`);
         });

         state = undefined;
       }

       return appReducer(state, action);
     };
     ```

112. ### What is the difference between React context and React Redux?

     You can use `Context` in your application directly and is going to be great for passing down data to deeply nested components which what it was designed for.

     Whereas `Redux` is much more powerful and provides a large number of features that the Context API doesn't provide. Also, React Redux uses context internally but it doesn't expose this fact in the public API.

113. ### Why are Redux state functions called reducers?

     Reducers always return the accumulation of the state (based on all previous and current actions). Therefore, they act as a reducer of state. Each time a Redux reducer is called, the state and action are passed as parameters. This state is then reduced (or accumulated) based on the action, and then the next state is returned. You could _reduce_ a collection of actions and an initial state (of the store) on which to perform these actions to get the resulting final state.

114. ### How to make AJAX request in Redux?

     You can use `redux-thunk` middleware which allows you to define async actions.

     Let's take an example of fetching specific account as an AJAX call using _fetch API_:

     ```javascript
     export function fetchAccount(id) {
       return (dispatch) => {
         dispatch(setLoadingAccountState()); // Show a loading spinner
         fetch(`/account/${id}`, (response) => {
           dispatch(doneFetchingAccount()); // Hide loading spinner
           if (response.status === 200) {
             dispatch(setAccount(response.json)); // Use a normal function to set the received state
           } else {
             dispatch(someError);
           }
         });
       };
     }

     function setAccount(data) {
       return { type: "SET_Account", data: data };
     }
     ```

115. ### Should I keep all component's state in Redux store?

     Keep your data in the Redux store, and the UI related state internally in the component.

116. ### What is the proper way to access Redux store?

     The best way to access your store in a component is to use the `connect()` function, that creates a new component that wraps around your existing one. This pattern is called _Higher-Order Components_, and is generally the preferred way of extending a component's functionality in React. This allows you to map state and action creators to your component, and have them passed in automatically as your store updates.

     Let's take an example of `<FilterLink>` component using connect:

     ```javascript
     import { connect } from "react-redux";
     import { setVisibilityFilter } from "../actions";
     import Link from "../components/Link";

     const mapStateToProps = (state, ownProps) => ({
       active: ownProps.filter === state.visibilityFilter,
     });

     const mapDispatchToProps = (dispatch, ownProps) => ({
       onClick: () => dispatch(setVisibilityFilter(ownProps.filter)),
     });

     const FilterLink = connect(mapStateToProps, mapDispatchToProps)(Link);

     export default FilterLink;
     ```

     Due to it having quite a few performance optimizations and generally being less likely to cause bugs, the Redux developers almost always recommend using `connect()` over accessing the store directly (using context API).

     ```javascript
     function MyComponent {
       someMethod() {
         doSomethingWith(this.context.store);
       }
     }
     ```

117. ### What is the difference between component and container in React Redux?

     `Component` is a class or function component that describes the presentational part of your application.

     `Container` is an informal term for a component that is connected to a Redux store. Containers _subscribe_ to Redux state updates and _dispatch_ actions, and they usually don't render DOM elements; they delegate rendering to presentational child components.

118. ### What is the purpose of the constants in Redux?

     Constants allows you to easily find all usages of that specific functionality across the project when you use an IDE. It also prevents you from introducing silly bugs caused by typos – in which case, you will get a `ReferenceError` immediately.

     Normally we will save them in a single file (`constants.js` or `actionTypes.js`).

     ```javascript
     export const ADD_TODO = "ADD_TODO";
     export const DELETE_TODO = "DELETE_TODO";
     export const EDIT_TODO = "EDIT_TODO";
     export const COMPLETE_TODO = "COMPLETE_TODO";
     export const COMPLETE_ALL = "COMPLETE_ALL";
     export const CLEAR_COMPLETED = "CLEAR_COMPLETED";
     ```

     In Redux, you use them in two places:

     1. `During action creation:`

        Let's take `actions.js`:

        ```javascript
        import { ADD_TODO } from "./actionTypes";

        export function addTodo(text) {
          return { type: ADD_TODO, text };
        }
        ```

     2. `In reducers:`

        Let's create `reducer.js`:

        ```javascript
        import { ADD_TODO } from "./actionTypes";

        export default (state = [], action) => {
          switch (action.type) {
            case ADD_TODO:
              return [
                ...state,
                {
                  text: action.text,
                  completed: false,
                },
              ];
            default:
              return state;
          }
        };
        ```

119. ### What are the different ways to write `mapDispatchToProps()`?

     There are a few ways of binding _action creators_ to `dispatch()` in `mapDispatchToProps()`.

     Below are the possible options:

     ```javascript
     const mapDispatchToProps = (dispatch) => ({
       action: () => dispatch(action()),
     });
     ```

     ```javascript
     const mapDispatchToProps = (dispatch) => ({
       action: bindActionCreators(action, dispatch),
     });
     ```

     ```javascript
     const mapDispatchToProps = { action };
     ```

     The third option is just a shorthand for the first one.

120. ### What is the use of the `ownProps` parameter in `mapStateToProps()` and `mapDispatchToProps()`?

     If the `ownProps` parameter is specified, React Redux will pass the props that were passed to the component into your _connect_ functions. So, if you use a connected component:

     ```javascript
     import ConnectedComponent from "./containers/ConnectedComponent";

     <ConnectedComponent user={"john"} />;
     ```

     The `ownProps` inside your `mapStateToProps()` and `mapDispatchToProps()` functions will be an object:

     ```javascript
     {
       user: "john";
     }
     ```

     You can use this object to decide what to return from those functions.

121. ### How to structure Redux top level directories?

     Most of the applications has several top-level directories as below:

     1. `Components`: Used for _dumb_ components unaware of Redux.
     2. `Containers`: Used for _smart_ components connected to Redux.
     3. `Actions`: Used for all action creators, where file names correspond to part of the app.
     4. `Reducers`: Used for all reducers, where files name correspond to state key.
     5. `Store`: Used for store initialization.

     This structure works well for small and medium size apps.

122. ### What is redux-saga?

     `redux-saga` is a library that aims to make side effects (asynchronous things like data fetching and impure things like accessing the browser cache) in React/Redux applications easier and better.

     It is available in NPM:

     ```console
     $ npm install --save redux-saga
     ```

123. ### What is the mental model of redux-saga?

     _Saga_ is like a separate thread in your application, that's solely responsible for side effects. `redux-saga` is a redux _middleware_, which means this thread can be started, paused and cancelled from the main application with normal Redux actions, it has access to the full Redux application state and it can dispatch Redux actions as well.

124. ### What are the differences between `call()` and `put()` in redux-saga?

     Both `call()` and `put()` are effect creator functions. `call()` function is used to create effect description, which instructs middleware to call the promise. `put()` function creates an effect, which instructs middleware to dispatch an action to the store.

     Let's take example of how these effects work for fetching particular user data.

     ```javascript
     function* fetchUserSaga(action) {
       // `call` function accepts rest arguments, which will be passed to `api.fetchUser` function.
       // Instructing middleware to call promise, it resolved value will be assigned to `userData` variable
       const userData = yield call(api.fetchUser, action.userId);

       // Instructing middleware to dispatch corresponding action.
       yield put({
         type: "FETCH_USER_SUCCESS",
         userData,
       });
     }
     ```

125. ### What is Redux Thunk?

     _Redux Thunk_ middleware allows you to write action creators that return a function instead of an action. The thunk can be used to delay the dispatch of an action, or to dispatch only if a certain condition is met. The inner function receives the store methods `dispatch()` and `getState()` as parameters.

126. ### What are the differences between `redux-saga` and `redux-thunk`?

     Both _Redux Thunk_ and _Redux Saga_ take care of dealing with side effects. In most of the scenarios, Thunk uses _Promises_ to deal with them, whereas Saga uses _Generators_. Thunk is simple to use and Promises are familiar to many developers, Sagas/Generators are more powerful but you will need to learn them. But both middleware can coexist, so you can start with Thunks and introduce Sagas when/if you need them.

127. ### What is Redux DevTools?

     _Redux DevTools_ is a live-editing time travel environment for Redux with hot reloading, action replay, and customizable UI. If you don't want to bother with installing Redux DevTools and integrating it into your project, consider using Redux DevTools Extension for Chrome and Firefox.

128. ### What are the features of Redux DevTools?

     Some of the main features of Redux DevTools are below,

     1. Lets you inspect every state and action payload.
     2. Lets you go back in time by _cancelling_ actions.
     3. If you change the reducer code, each _staged_ action will be re-evaluated.
     4. If the reducers throw, you will see during which action this happened, and what the error was.
     5. With `persistState()` store enhancer, you can persist debug sessions across page reloads.

129. ### What are Redux selectors and why use them?

     _Selectors_ are functions that take Redux state as an argument and return some data to pass to the component.

     For example, to get user details from the state:

     ```javascript
     const getUserData = (state) => state.user.data;
     ```

     These selectors have two main benefits,

     1. The selector can compute derived data, allowing Redux to store the minimal possible state
     2. The selector is not recomputed unless one of its arguments changes

130. ### What is Redux Form?

     _Redux Form_ works with React and Redux to enable a form in React to use Redux to store all of its state. Redux Form can be used with raw HTML5 inputs, but it also works very well with common UI frameworks like Material UI, React Widgets and React Bootstrap.

131. ### What are the main features of Redux Form?

     Some of the main features of Redux Form are:

     1. Field values persistence via Redux store.
     2. Validation (sync/async) and submission.
     3. Formatting, parsing and normalization of field values.

132. ### How to add multiple middlewares to Redux?

     You can use `applyMiddleware()`.

     For example, you can add `redux-thunk` and `logger` passing them as arguments to `applyMiddleware()`:

     ```javascript
     import { createStore, applyMiddleware } from "redux";
     const createStoreWithMiddleware = applyMiddleware(
       ReduxThunk,
       logger
     )(createStore);
     ```

133. ### How to set initial state in Redux?

     You need to pass initial state as second argument to createStore:

     ```javascript
     const rootReducer = combineReducers({
       todos: todos,
       visibilityFilter: visibilityFilter,
     });

     const initialState = {
       todos: [{ id: 123, name: "example", completed: false }],
     };

     const store = createStore(rootReducer, initialState);
     ```

134. ### How Relay is different from Redux?

     Relay is similar to Redux in that they both use a single store. The main difference is that relay only manages state originated from the server, and all access to the state is used via _GraphQL_ queries (for reading data) and mutations (for changing data). Relay caches the data for you and optimizes data fetching for you, by fetching only changed data and nothing more.

135. ### What is an action in Redux?

     _Actions_ are plain JavaScript objects or payloads of information that send data from your application to your store. They are the only source of information for the store. Actions must have a type property that indicates the type of action being performed.

     For example, let's take an action which represents adding a new todo item:

     ```
     {
       type: ADD_TODO,
       text: 'Add todo item'
     }
     ```

## React Native

136. ### What is the difference between React Native and React?

     `React` is a JavaScript library, supporting both front end web and being run on the server, for building user interfaces and web applications.

     `React Native` is a mobile framework that compiles to native app components, allowing you to build native mobile applications (iOS, Android, and Windows) in JavaScript that allows you to use React to build your components, and implements React under the hood.

137. ### How to test React Native apps?

     React Native can be tested only in mobile simulators like iOS and Android. You can run the app in your mobile using expo app (https://expo.io) Where it syncs using QR code, your mobile and computer should be in same wireless network.

138. ### How to do logging in React Native?

     You can use `console.log`, `console.warn`, etc. As of React Native v0.29 you can simply run the following to see logs in the console:

     ```
     $ react-native log-ios
     $ react-native log-android
     ```

139. ### How to debug your React Native?

     Follow the below steps to debug React Native app:

     1. Run your application in the iOS simulator.
     2. Press `Command + D` and a webpage should open up at `http://localhost:8081/debugger-ui`.
     3. Enable _Pause On Caught Exceptions_ for a better debugging experience.
     4. Press `Command + Option + I` to open the Chrome Developer tools, or open it via `View` -> `Developer` -> `Developer Tools`.
     5. You should now be able to debug as you normally would.

## React supported libraries & Integration

140. ### What is reselect and how it works?

     _Reselect_ is a `selector library` (for Redux) which uses _memoization_ concept. It was originally written to compute derived data from Redux-like applications state, but it can't be tied to any architecture or library.

     Reselect keeps a copy of the last inputs/outputs of the last call, and recomputes the result only if one of the inputs changes. If the same inputs are provided twice in a row, Reselect returns the cached output. It's memoization and cache are fully customizable.

141. ### What is Flow?

     _Flow_ is a _static type checker_ designed to find type errors in JavaScript. Flow types can express much more fine-grained distinctions than traditional type systems. For example, Flow helps you catch errors involving `null`, unlike most type systems.

142. ### What is the difference between Flow and PropTypes?

     Flow is a _static analysis tool_ (static checker) which uses a superset of the language, allowing you to add type annotations to all of your code and catch an entire class of bugs at compile time.

     PropTypes is a _basic type checker_ (runtime checker) which has been patched onto React. It can't check anything other than the types of the props being passed to a given component. If you want more flexible typechecking for your entire project Flow/TypeScript are appropriate choices.

143. ### How to use Font Awesome icons in React?

     The below steps followed to include Font Awesome in React:

     1. Install `font-awesome`:

        ```console
        $ npm install --save font-awesome
        ```

     2. Import `font-awesome` in your `index.js` file:

        ```javascript
        import "font-awesome/css/font-awesome.min.css";
        ```

     3. Add Font Awesome classes in `className`:

        ```javascript
        function MyComponent {
          return <div><i className={'fa fa-spinner'} /></div>
        }
        ```

144. ### What is React Dev Tools?

     _React Developer Tools_ let you inspect the component hierarchy, including component props and state. It exists both as a browser extension (for Chrome and Firefox), and as a standalone app (works with other environments including Safari, IE, and React Native).

     The official extensions available for different browsers or environments.

     1. `Chrome extension`
     2. `Firefox extension`
     3. `Standalone app` (Safari, React Native, etc)

145. ### Why is DevTools not loading in Chrome for local files?

     If you opened a local HTML file in your browser (`file://...`) then you must first open _Chrome Extensions_ and check `Allow access to file URLs`.

146. ### How to use Polymer in React?

     You need to follow below steps to use Polymer in React,

     1. Create a Polymer element:

        ```javascript
        <link
          rel="import"
          href="../../bower_components/polymer/polymer.html"
        />;
        Polymer({
          is: "calendar-element",
          ready: function () {
            this.textContent = "I am a calendar";
          },
        });
        ```

     2. Create the Polymer component HTML tag by importing it in a HTML document, e.g. import it in the `index.html` of your React application:

        ```html
        <link
          rel="import"
          href="./src/polymer-components/calendar-element.html"
        />
        ```

     3. Use that element in the JSX file:

        ```javascript
        export default function MyComponent {
          return <calendar-element />;
        }
        ```

147. ### What are the advantages of React over Vue.js?

     React has the following advantages over Vue.js:

     1. Gives more flexibility in large apps developing.
     2. Easier to test.
     3. Suitable for mobile apps creating.
     4. More information and solutions available.

`Note:` The above list of advantages are purely opinionated and it vary based on the professional experience. But they are helpful as base parameters.

148. ### What is the difference between React and Angular?

     Let's see the difference between React and Angular in a table format.

     | React                                                                                       | Angular                                                                                                                            |
     | ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
     | React is a library and has only the View layer                                              | Angular is a framework and has complete MVC functionality                                                                          |
     | React handles rendering on the server side                                                  | AngularJS renders only on the client side but Angular 2 and above renders on the server side                                       |
     | React uses JSX that looks like HTML in JS which can be confusing                            | Angular follows the template approach for HTML, which makes code shorter and easy to understand                                    |
     | React Native, which is a React type to build mobile applications are faster and more stable | Ionic, Angular's mobile native app is relatively less stable and slower                                                            |
     | In React, data flows only in one way and hence debugging is easy                            | In Angular, data flows both way i.e it has two-way data binding between children and parent and hence debugging is often difficult |

`Note:` The above list of differences are purely opinionated and it vary based on the professional experience. But they are helpful as base parameters.

149. ### Why React tab is not showing up in DevTools?

     When the page loads, _React DevTools_ sets a global named `__REACT_DEVTOOLS_GLOBAL_HOOK__`, then React communicates with that hook during initialization. If the website is not using React or if React fails to communicate with DevTools then it won't show up the tab.

150. ### What are Styled Components?

     `styled-components` is a JavaScript library for styling React applications. It removes the mapping between styles and components, and lets you write actual CSS augmented with JavaScript.

151. ### Give an example of Styled Components?

     Lets create `<Title>` and `<Wrapper>` components with specific styles for each.

     ```javascript
     import React from "react";
     import styled from "styled-components";

     // Create a <Title> component that renders an <h1> which is centered, red and sized at 1.5em
     const Title = styled.h1`
       font-size: 1.5em;
       text-align: center;
       color: palevioletred;
     `;

     // Create a <Wrapper> component that renders a <section> with some padding and a papayawhip background
     const Wrapper = styled.section`
       padding: 4em;
       background: papayawhip;
     `;
     ```

     These two variables, `Title` and `Wrapper`, are now components that you can render just like any other react component.

     ```javascript
     <Wrapper>
       <Title>{"Lets start first styled component!"}</Title>
     </Wrapper>
     ```

152. ### What is Relay?

     Relay is a JavaScript framework for providing a data layer and client-server communication to web applications using the React view layer.

## Miscellaneous

153. ### What are the main features of Reselect library?

     Let's see the main features of Reselect library,

     1. Selectors can compute derived data, allowing Redux to store the minimal possible state.
     2. Selectors are efficient. A selector is not recomputed unless one of its arguments changes.
     3. Selectors are composable. They can be used as input to other selectors.

154. #### Give an example of Reselect usage?

     Let's take calculations and different amounts of a shipment order with the simplified usage of Reselect:

     ```javascript
     import { createSelector } from "reselect";

     const shopItemsSelector = (state) => state.shop.items;
     const taxPercentSelector = (state) => state.shop.taxPercent;

     const subtotalSelector = createSelector(shopItemsSelector, (items) =>
       items.reduce((acc, item) => acc + item.value, 0)
     );

     const taxSelector = createSelector(
       subtotalSelector,
       taxPercentSelector,
       (subtotal, taxPercent) => subtotal * (taxPercent / 100)
     );

     export const totalSelector = createSelector(
       subtotalSelector,
       taxSelector,
       (subtotal, tax) => ({ total: subtotal + tax })
     );

     let exampleState = {
       shop: {
         taxPercent: 8,
         items: [
           { name: "apple", value: 1.2 },
           { name: "orange", value: 0.95 },
         ],
       },
     };

     console.log(subtotalSelector(exampleState)); // 2.15
     console.log(taxSelector(exampleState)); // 0.172
     console.log(totalSelector(exampleState)); // { total: 2.322 }
     ```

155. ### Can Redux only be used with React?

     Redux can be used as a data store for any UI layer. The most common usage is with React and React Native, but there are bindings available for Angular, Angular 2, Vue, Mithril, and more. Redux simply provides a subscription mechanism which can be used by any other code.

156. ### Do you need to have a particular build tool to use Redux?

     Redux is originally written in ES6 and transpiled for production into ES5 with Webpack and Babel. You should be able to use it regardless of your JavaScript build process. Redux also offers a UMD build that can be used directly without any build process at all.

157. ### How Redux Form `initialValues` get updated from state?

     You need to add `enableReinitialize : true` setting.

     ```javascript
     const InitializeFromStateForm = reduxForm({
       form: "initializeFromState",
       enableReinitialize: true,
     })(UserEdit);
     ```

     If your `initialValues` prop gets updated, your form will update too.

158. ### How React PropTypes allow different types for one prop?

     You can use `oneOfType()` method of `PropTypes`.

     For example, the height property can be defined with either `string` or `number` type as below:

     ```javascript
     Component.propTypes = {
       size: PropTypes.oneOfType([PropTypes.string, PropTypes.number]),
     };
     ```

159. ### Can I import an SVG file as react component?

     You can import SVG directly as component instead of loading it as a file. This feature is available with `react-scripts@2.0.0` and higher.

     ```javascript
     import { ReactComponent as Logo } from "./logo.svg";

     const App = () => (
       <div>
         {/* Logo is an actual react component */}
         <Logo />
       </div>
     );
     ```

     `Note`: Don't forget about the curly braces in the import.

160. ### What is render hijacking in react?

     The concept of render hijacking is the ability to control what a component will output from another component. It means that you decorate your component by wrapping it into a Higher-Order component. By wrapping, you can inject additional props or make other changes, which can cause changing logic of rendering. It does not actually enable hijacking, but by using HOC you make your component behave differently.

161. ### How to pass numbers to React component?

     We can pass `numbers` as `props` to React component using curly braces `{}` where as `strings` in double quotes `""` or single quotes `''`

     ```jsx
     import React from "react";

     const ChildComponent = ({ name, age }) => {
       return (
         <>
           My Name is {name} and Age is {age}
         </>
       );
     };

     const ParentComponent = () => {
       return (
         <>
           <ChildComponent name="Chetan" age={30} />
         </>
       );
     };

     export default ParentComponent;
     ```

162. ### Do I need to keep all my state into Redux? Should I ever use react internal state?

     It is up to the developer's decision, i.e., it is developer's job to determine what kinds of state make up your application, and where each piece of state should live. Some users prefer to keep every single piece of data in Redux, to maintain a fully serializable and controlled version of their application at all times. Others prefer to keep non-critical or UI state, such as “is this dropdown currently open”, inside a component's internal state.

     Below are the rules of thumb to determine what kind of data should be put into Redux

     1. Do other parts of the application care about this data?
     2. Do you need to be able to create further derived data based on this original data?
     3. Is the same data being used to drive multiple components?
     4. Is there value to you in being able to restore this state to a given point in time (ie, time travel debugging)?
     5. Do you want to cache the data (i.e, use what's in state if it's already there instead of re-requesting it)?

163. ### What is the purpose of registerServiceWorker in React?

     React creates a service worker for you without any configuration by default. The service worker is a web API that helps you cache your assets and other files so that when the user is offline or on a slow network, he/she can still see results on the screen, as such, it helps you build a better user experience, that's what you should know about service worker for now. It's all about adding offline capabilities to your site.

     ```jsx
     import React from "react";
     import ReactDOM from "react-dom";
     import App from "./App";
     import registerServiceWorker from "./registerServiceWorker";

     ReactDOM.render(<App />, document.getElementById("root"));
     registerServiceWorker();
     ```

164. ### What is React memo function?

     Class components can be restricted from re-rendering when their input props are the same using `PureComponent or shouldComponentUpdate`. Now you can do the same with function components by wrapping them in `React.memo`.

     ```jsx
     const MyComponent = React.memo(function MyComponent(props) {
       /* only rerenders if props change */
     });
     ```

165. ### What is React lazy function?

     The `React.lazy` function lets you render a dynamic import as a regular component. It will automatically load the bundle containing the `OtherComponent` when the component gets rendered. This must return a Promise which resolves to a module with a default export containing a React component.

     ```jsx
     const OtherComponent = React.lazy(() => import("./OtherComponent"));

     function MyComponent() {
       return (
         <div>
           <OtherComponent />
         </div>
       );
     }
     ```

     `Note:`
     `React.lazy` and `Suspense` is not yet available for server-side rendering. If you want to do code-splitting in a server rendered app, we still recommend React Loadable.

166. ### How to prevent unnecessary updates using setState?

     You can compare the current value of the state with an existing state value and decide whether to rerender the page or not. If the values are the same then you need to return `null` to stop re-rendering otherwise return the latest state value.

     For example, the user profile information is conditionally rendered as follows,

     ```jsx
     getUserProfile = (user) => {
       const latestAddress = user.address;
       this.setState((state) => {
         if (state.address === latestAddress) {
           return null;
         } else {
           return { title: latestAddress };
         }
       });
     };
     ```

167. ### How do you render Array, Strings and Numbers in React 16 Version?

     `Arrays`: Unlike older releases, you don't need to make sure `render` method return a single element in React16. You are able to return multiple sibling elements without a wrapping element by returning an array.

     For example, let us take the below list of developers,

     ```jsx
     const ReactJSDevs = () => {
       return [
         <li key="1">John</li>,
         <li key="2">Jackie</li>,
         <li key="3">Jordan</li>,
       ];
     };
     ```

     You can also merge this array of items in another array component.

     ```jsx
     const JSDevs = () => {
       return (
         <ul>
           <li>Brad</li>
           <li>Brodge</li>
           <ReactJSDevs />
           <li>Brandon</li>
         </ul>
       );
     };
     ```

     `Strings and Numbers:` You can also return string and number type from the render method.

     ```jsx
     render() {
      return 'Welcome to ReactJS questions';
     }
     // Number
     render() {
      return 2018;
     }
     ```

168. ### What are hooks?

     Hooks is a special JavaScript function that allows you use state and other React features without writing a class. This pattern has been introduced as a new feature in React 16.8 and helped to isolate the stateful logic from the components.

     Let's see an example of useState hook:

     ```jsx
     import { useState } from "react";

     function Example() {
       // Declare a new state variable, which we'll call "count"
       const [count, setCount] = useState(0);

       return (
         <>
           <p>You clicked {count} times</p>
           <button onClick={() => setCount(count + 1)}>Click me</button>
         </>
       );
     }
     ```

     `Note:` Hooks can be used inside an existing function component without rewriting the component.

169. ### What rules need to be followed for hooks?

     You need to follow two rules in order to use hooks,

     1. `Call Hooks only at the top level of your react functions:` You should always use hooks at the top level of react function before any early returns. i.e, You shouldn’t call Hooks inside loops, conditions, or nested functions. This will ensure that Hooks are called in the same order each time a component renders and it preserves the state of Hooks between multiple re-renders due to `useState` and `useEffect` calls.

     Let's see the difference using an example,
     `Correct usage:`:

     ```jsx
     function UserProfile() {
       // Correct: Hooks called at the top level
       const [name, setName] = useState("John");
       const [country, setCountry] = useState("US");

       return (
         <div>
           <h1>Name: {name}</h1>
           <p>Country: {country}</p>
         </div>
       );
     }
     ```

     `Incorrect usage:`:

     ```jsx
     function UserProfile() {
       const [name, setName] = useState("John");

       if (name === "John") {
         // Incorrect: useState is called inside a conditional
         const [country, setCountry] = useState("US");
       }

       return (
         <div>
           <h1>Name: {name}</h1>
           <p>Country: {country}</p> {/* This will throw an error if the name condition isn't met */}
         </div>
       );
     }
     ```

     The `useState` hook for the country field is being called conditionally within an `if` block. This can lead to inconsistent state behavior and may cause hooks to be called in a different order on each re-render.

     2. `Call Hooks from React Functions only:` You shouldn’t call Hooks from regular JavaScript functions or class components. Instead, you should call them from either function components or custom hooks.

     Let's find the difference of correct and incorrect usage with below examples,

     `Correct usage:`:

     ```jsx
     //Example1:
     function Counter() {
       // Correct: useState is used inside a functional component
       const [count, setCount] = useState(0);

       return <div>Counter: {count}</div>;
     }
     //Example2:
     function useFetchData(url) {
       const [data, setData] = useState(null);

       useEffect(() => {
         fetch(url)
           .then((response) => response.json())
           .then((data) => setData(data));
       }, [url]);

       return data;
     }

     function UserProfile() {
       // Correct: Using a custom hook here
       const user = useFetchData("https://some-api.com/user");

       return (
         <div>
           <h1>{user ? user.name : "Loading profile..."}</h1>
         </div>
       );
     }
     ```

     `Incorrect usage:`:

     ```jsx
     //Example1
     function normalFunction() {
       // Incorrect: Can't call hooks in normal functions
       const [count, setCount] = useState(0);
     }

     //Example2
     function fetchData(url) {
       // Incorrect: Hooks can't be used in non-React functions
       const [data, setData] = useState(null);

       useEffect(() => {
         fetch(url)
           .then((response) => response.json())
           .then((data) => setData(data));
       }, [url]);

       return data;
     }
     ```

     In the above incorrect usage example, both `useState` and `useEffect` are used in non-React functions(`normalFunction` and `fetchData`), which is not allowed.

170. ### How to ensure hooks followed the rules in your project?

     React team released an ESLint plugin called `eslint-plugin-react-hooks` that enforces Hook's two rules. It is part of Hooks API. You can add this plugin to your project using the below command,

     ```javascript
     npm install eslint-plugin-react-hooks --save-dev
     ```

     And apply the below config in your ESLint config file,

     ```javascript
     // Your ESLint configuration
     {
       "plugins": [
         // ...
         "react-hooks"
       ],
       "rules": {
         // ...
         "react-hooks/rules-of-hooks": "error"
       }
     }
     ```

     This plugin also provide another important rule through `react-hooks/exhaustive-deps`. It ensures that the dependencies of useEffect, useCallback, and useMemo hooks are correctly listed to avoid potential bugs.

     ```jsx
     useEffect(() => {
       // Forgetting `message` will result in incorrect behavior
       console.log(message);
     }, []); // Here `message` should be a dependency
     ```

     The recommended `eslint-config-react-app` preset already includes the hooks rules of this plugin.
     For example, the linter enforce proper naming convention for hooks. If you rename your custom hooks which as prefix "use" to something else then linter won't allow you to call built-in hooks such as useState, useEffect etc inside of your custom hook anymore.

     `Note:` This plugin is intended to use in Create React App by default.

171. ### What are the differences between Flux and Redux?

     Below are the major differences between Flux and Redux

     | Flux                                           | Redux                                      |
     | ---------------------------------------------- | ------------------------------------------ |
     | State is mutable                               | State is immutable                         |
     | The Store contains both state and change logic | The Store and change logic are separate    |
     | There are multiple stores exist                | There is only one store exist              |
     | All the stores are disconnected and flat       | Single store with hierarchical reducers    |
     | It has a singleton dispatcher                  | There is no concept of dispatcher          |
     | React components subscribe to the store        | Container components uses connect function |

172. ### What are the benefits of React Router V4?

     Below are the main benefits of React Router V4 module,

     1. In React Router v4(version 4), the API is completely about components. A router can be visualized as a single component(`<BrowserRouter>`) which wraps specific child router components(`<Route>`).
     2. You don't need to manually set history. The router module will take care history by wrapping routes with `<BrowserRouter>` component.
     3. The application size is reduced by adding only the specific router module(Web, core, or native)

173. ### Can you describe about componentDidCatch lifecycle method signature?

     The `componentDidCatch` lifecycle method is invoked after an error has been thrown by a descendant component. The method receives two parameters,

     1. error: - The error object which was thrown
     2. info: - An object with a componentStack key contains the information about which component threw the error.

     The method structure would be as follows

     ```javascript
     componentDidCatch(error, info);
     ```

174. ### In which scenarios do error boundaries not catch errors?

     Below are the cases in which error boundaries don't work,

     1. Inside Event handlers
     2. Asynchronous code using `setTimeout or requestAnimationFrame` callbacks
     3. During Server side rendering
     4. When errors thrown in the error boundary code itself

175. ### What is the behavior of uncaught errors in react 16?

     In React 16, errors that were not caught by any error boundary will result in unmounting of the whole React component tree. The reason behind this decision is that it is worse to leave corrupted UI in place than to completely remove it. For example, it is worse for a payments app to display a wrong amount than to render nothing.

176. ### What is the proper placement for error boundaries?

     The granularity of error boundaries usage is up to the developer based on project needs. You can follow either of these approaches,

     1. You can wrap top-level route components to display a generic error message for the entire application.
     2. You can also wrap individual components in an error boundary to protect them from crashing the rest of the application.

177. ### What is the benefit of component stack trace from error boundary?

     Apart from error messages and javascript stack, React16 will display the component stack trace with file names and line numbers using error boundary concept.

     For example, BuggyCounter component displays the component stack trace as below,

     ![stacktrace](images/error_boundary.png)

178. ### What are default props?

     The _defaultProps_ can be defined as a property on the component to set the default values for the props. These default props are used when props not supplied(i.e., undefined props), but not for `null` or `0` as props. That means, If you provide null value then it remains null value. It's the same behavior with 0 as well.

     For example, let us create color default prop for the button component,

     ```javascript
     function MyButton {
       // ...
     }

     MyButton.defaultProps = {
       color: "red",
     };
     ```

     If `props.color` is not provided then it will set the default value to 'red'. i.e, Whenever you try to access the color prop it uses the default value

     ```javascript
     function MyButton() {
       return <MyButton />; // props.color will contain red value
     }
     ```

179. ### What is the purpose of displayName class property?

     The displayName string is used in debugging messages. Usually, you don’t need to set it explicitly because it’s inferred from the name of the function or class that defines the component. You might want to set it explicitly if you want to display a different name for debugging purposes or when you create a higher-order component.

     For example, To ease debugging, choose a display name that communicates that it’s the result of a withSubscription HOC.

     ```javascript
     function withSubscription(WrappedComponent) {
       class WithSubscription extends React.Component {
         /* ... */
       }
       WithSubscription.displayName = `WithSubscription(${getDisplayName(
         WrappedComponent
       )})`;
       return WithSubscription;
     }
     function getDisplayName(WrappedComponent) {
       return (
         WrappedComponent.displayName || WrappedComponent.name || "Component"
       );
     }
     ```

180. ### What is the browser support for react applications?

     React supports all popular browsers, including Internet Explorer 9 and above, although some polyfills are required for older browsers such as IE 9 and IE 10. If you use `es5-shim and es5-sham` polyfill then it even support old browsers that doesn't support ES5 methods.

181. ### What is code-splitting?

     Code-Splitting is a feature supported by bundlers like Webpack and Browserify which can create multiple bundles that can be dynamically loaded at runtime. The react project supports code splitting via dynamic import() feature.

     For example, in the below code snippets, it will make moduleA.js and all its unique dependencies as a separate chunk that only loads after the user clicks the 'Load' button.

     `moduleA.js`

     ```javascript
     const moduleA = "Hello";

     export { moduleA };
     ```

     `App.js`

     ```javascript
     export default function App {
       function handleClick() {
         import("./moduleA")
           .then(({ moduleA }) => {
             // Use moduleA
           })
           .catch((err) => {
             // Handle failure
           });
       };

      return (
        <div>
          <button onClick={this.handleClick}>Load</button>
        </div>
      );
     }
     ```

  <details><summary><b>See Class</b></summary>
    <p>

```javascript
import React, { Component } from "react";

class App extends Component {
  handleClick = () => {
    import("./moduleA")
      .then(({ moduleA }) => {
        // Use moduleA
      })
      .catch((err) => {
        // Handle failure
      });
  };

  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Load</button>
      </div>
    );
  }
}

export default App;
```

  </p>
</details>

182. ### What are Keyed Fragments?

     The Fragments declared with the explicit <React.Fragment> syntax may have keys. The general use case is mapping a collection to an array of fragments as below,

     ```javascript
     function Glossary(props) {
       return (
         <dl>
           {props.items.map((item) => (
             // Without the `key`, React will fire a key warning
             <React.Fragment key={item.id}>
               <dt>{item.term}</dt>
               <dd>{item.description}</dd>
             </React.Fragment>
           ))}
         </dl>
       );
     }
     ```

     `Note:` key is the only attribute that can be passed to Fragment. In the future, there might be a support for additional attributes, such as event handlers.

183. ### Does React support all HTML attributes?

     As of React 16, both standard or custom DOM attributes are fully supported. Since React components often take both custom and DOM-related props, React uses the camelCase convention just like the DOM APIs.

     Let us take few props with respect to standard HTML attributes,

     ```javascript
     <div tabIndex="-1" />      // Just like node.tabIndex DOM API
     <div className="Button" /> // Just like node.className DOM API
     <input readOnly={true} />  // Just like node.readOnly DOM API
     ```

     These props work similarly to the corresponding HTML attributes, with the exception of the special cases. It also support all SVG attributes.

184. ### When component props defaults to true?

     If you pass no value for a prop, it defaults to true. This behavior is available so that it matches the behavior of HTML.

     For example, below expressions are equivalent,

     ```javascript
     <MyInput autocomplete />

     <MyInput autocomplete={true} />
     ```

     `Note:` It is not recommended to use this approach because it can be confused with the ES6 object shorthand (example, `{name}` which is short for `{name: name}`)

185. ### What is NextJS and major features of it?

     Next.js is a popular and lightweight framework for static and server‑rendered applications built with React. It also provides styling and routing solutions. Below are the major features provided by NextJS,

     1. Server-rendered by default
     2. Automatic code splitting for faster page loads
     3. Simple client-side routing (page based)
     4. Webpack-based dev environment which supports (HMR)
     5. Able to implement with Express or any other Node.js HTTP server
     6. Customizable with your own Babel and Webpack configurations

186. ### How do you pass an event handler to a component?

     You can pass event handlers and other functions as props to child components. The functions can be passed to child component as below,

     ```jsx
     function Button({ onClick }) {
       return <button onClick={onClick}>Download</button>;
     }

     export default function downloadExcel() {
       function handleClick() {
         alert("Downloaded");
       }

       return <Button onClick={handleClick}></Button>;
     }
     ```

187. ### How to prevent a function from being called multiple times?

     If you use an event handler such as `onClick or onScroll` and want to prevent the callback from being fired too quickly, then you can limit the rate at which callback is executed. This can be achieved in the below possible ways,

     1. `Throttling:` Changes based on a time based frequency. For example, it can be used using \_.throttle lodash function
     2. `Debouncing:` Publish changes after a period of inactivity. For example, it can be used using \_.debounce lodash function
     3. `RequestAnimationFrame throttling:` Changes based on requestAnimationFrame. For example, it can be used using raf-schd lodash function

188. ### How JSX prevents Injection Attacks?

     React DOM escapes any values embedded in JSX before rendering them. Thus it ensures that you can never inject anything that’s not explicitly written in your application. Everything is converted to a string before being rendered.

     For example, you can embed user input as below,

     ```javascript
     const name = response.potentiallyMaliciousInput;
     const element = <h1>{name}</h1>;
     ```

     This way you can prevent XSS(Cross-site-scripting) attacks in the application.

189. ### How do you update rendered elements?

     You can update UI(represented by rendered element) by passing the newly created element to ReactDOM's render method.

     For example, lets take a ticking clock example, where it updates the time by calling render method multiple times,

     ```javascript
     function tick() {
       const element = (
         <div>
           <h1>Hello, world!</h1>
           <h2>It is {new Date().toLocaleTimeString()}.</h2>
         </div>
       );
       ReactDOM.render(element, document.getElementById("root"));
     }

     setInterval(tick, 1000);
     ```

190. ### How do you say that props are readonly?

     When you declare a component as a function or a class, it must never modify its own props.

     Let us take a below capital function,

     ```javascript
     function capital(amount, interest) {
       return amount + interest;
     }
     ```

     The above function is called “pure” because it does not attempt to change their inputs, and always return the same result for the same inputs. Hence, React has a single rule saying "All React components must act like pure functions with respect to their props."

191. ### What are the conditions to safely use the index as a key?

     There are three conditions to make sure, it is safe use the index as a key.

     1. The list and items are static– they are not computed and do not change
     2. The items in the list have no ids
     3. The list is never reordered or filtered.

192. ### Should keys be globally unique?

     The keys used within arrays should be unique among their siblings but they don’t need to be globally unique. i.e, You can use the same keys with two different arrays.

     For example, the below `Book` component uses two arrays with different arrays,

     ```javascript
     function Book(props) {
       const index = (
         <ul>
           {props.pages.map((page) => (
             <li key={page.id}>{page.title}</li>
           ))}
         </ul>
       );
       const content = props.pages.map((page) => (
         <div key={page.id}>
           <h3>{page.title}</h3>
           <p>{page.content}</p>
           <p>{page.pageNumber}</p>
         </div>
       ));
       return (
         <div>
           {index}
           <hr />
           {content}
         </div>
       );
     }
     ```

193. ### What is the popular choice for form handling?

     `Formik` is a form library for react which provides solutions such as validation, keeping track of the visited fields, and handling form submission.

     In detail, You can categorize them as follows,

     1. Getting values in and out of form state
     2. Validation and error messages
     3. Handling form submission

     It is used to create a scalable, performant, form helper with a minimal API to solve annoying stuff.

194. ### What are the advantages of formik over redux form library?

     Below are the main reasons to recommend formik over redux form library,

     1. The form state is inherently short-term and local, so tracking it in Redux (or any kind of Flux library) is unnecessary.
     2. Redux-Form calls your entire top-level Redux reducer multiple times ON EVERY SINGLE KEYSTROKE. This way it increases input latency for large apps.
     3. Redux-Form is 22.5 kB minified gzipped whereas Formik is 12.7 kB

195. ### Why are you not required to use inheritance?

     In React, it is recommended to use composition over inheritance to reuse code between components. Both Props and composition give you all the flexibility you need to customize a component’s look and behavior explicitly and safely.
     Whereas, If you want to reuse non-UI functionality between components, it is suggested to extract it into a separate JavaScript module. Later components import it and use that function, object, or class, without extending it.

196. ### Can I use web components in react application?

     Yes, you can use web components in a react application. Even though many developers won't use this combination, it may require especially if you are using third-party UI components that are written using Web Components.

     For example, let us use `Vaadin` date picker web component as below,

     ```javascript
     import "./App.css";
     import "@vaadin/vaadin-date-picker";
     export default function App() {
       return (
         <div className="App">
           <vaadin-date-picker label="When were you born?"></vaadin-date-picker>
         </div>
       );
     }
     ```

197. ### What is dynamic import?

     You can achieve code-splitting in your app using dynamic import.

     Let's take an example of addition,

     1. `Normal Import`

     ```javascript
     import { add } from "./math";
     console.log(add(10, 20));
     ```

     2. `Dynamic Import`

     ```javascript
     import("./math").then((math) => {
       console.log(math.add(10, 20));
     });
     ```

198. ### What are loadable components?

     With the release of React 18, React.lazy and Suspense are now available for server-side rendering. However, prior to React 18, it was recommended to use Loadable Components for code-splitting in a server-side rendered app because React.lazy and Suspense were not available for server-side rendering. Loadable Components lets you render a dynamic import as a regular component. For example, you can use Loadable Components to load the OtherComponent in a separate bundle like this:

     ```javascript
     import loadable from "@loadable/component";

     const OtherComponent = loadable(() => import("./OtherComponent"));

     function MyComponent() {
       return (
         <div>
           <OtherComponent />
         </div>
       );
     }
     ```

     Now OtherComponent will be loaded in a separated bundle
     Loadable Components provides additional benefits beyond just code-splitting, such as automatic code reloading, error handling, and preloading. By using Loadable Components, you can ensure that your application loads quickly and efficiently, providing a better user experience for your users.

199. ### What is suspense component?

     If the module containing the dynamic import is not yet loaded by the time parent component renders, you must show some fallback content while you’re waiting for it to load using a loading indicator. This can be done using `Suspense` component.

     For example, the below code uses suspense component,

     ```javascript
     const OtherComponent = React.lazy(() => import("./OtherComponent"));

     function MyComponent() {
       return (
         <div>
           <Suspense fallback={<div>Loading...</div>}>
             <OtherComponent />
           </Suspense>
         </div>
       );
     }
     ```

     As mentioned in the above code, Suspense is wrapped above the lazy component.

200. ### What is route based code splitting?

     One of the best place to do code splitting is with routes. The entire page is going to re-render at once so users are unlikely to interact with other elements in the page at the same time. Due to this, the user experience won't be disturbed.

     Let us take an example of route based website using libraries like React Router with React.lazy,

     ```javascript
     import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
     import React, { Suspense, lazy } from "react";

     const Home = lazy(() => import("./routes/Home"));
     const About = lazy(() => import("./routes/About"));

     const App = () => (
       <Router>
         <Suspense fallback={<div>Loading...</div>}>
           <Switch>
             <Route exact path="/" component={Home} />
             <Route path="/about" component={About} />
           </Switch>
         </Suspense>
       </Router>
     );
     ```

     In the above code, the code splitting will happen at each route level.

201. ### What is the purpose of default value in context?

     The defaultValue argument is only used when a component does not have a matching Provider above it in the tree. This can be helpful for testing components in isolation without wrapping them.

     Below code snippet provides default theme value as Luna.

     ```javascript
     const MyContext = React.createContext(defaultValue);
     ```

202. ### What is diffing algorithm?

     React needs to use algorithms to find out how to efficiently update the UI to match the most recent tree. The diffing algorithms is generating the minimum number of operations to transform one tree into another. However, the algorithms have a complexity in the order of O(n³) where n is the number of elements in the tree.

     In this case, displaying 1000 elements would require in the order of one billion comparisons. This is far too expensive. Instead, React implements a heuristic O(n) algorithm based on two assumptions:

     1. Two elements of different types will produce different trees.
     2. The developer can hint at which child elements may be stable across different renders with a key prop.

203. ### What are the rules covered by diffing algorithm?

     When diffing two trees, React first compares the two root elements. The behavior is different depending on the types of the root elements. It covers the below rules during reconciliation algorithm,

     1. `Elements Of Different Types:`
        Whenever the root elements have different types, React will tear down the old tree and build the new tree from scratch. For example, elements <a> to <img>, or from <Article> to <Comment> of different types lead a full rebuild.
     2. `DOM Elements Of The Same Type:`
        When comparing two React DOM elements of the same type, React looks at the attributes of both, keeps the same underlying DOM node, and only updates the changed attributes. Lets take an example with same DOM elements except className attribute,

        ```javascript
        <div className="show" title="ReactJS" />

        <div className="hide" title="ReactJS" />
        ```

     3. `Component Elements Of The Same Type:`
        When a component updates, the instance stays the same, so that state is maintained across renders. React updates the props of the underlying component instance to match the new element, and calls componentWillReceiveProps() and componentWillUpdate() on the underlying instance. After that, the render() method is called and the diff algorithm recurses on the previous result and the new result.
     4. `Recursing On Children:`
        when recursing on the children of a DOM node, React just iterates over both lists of children at the same time and generates a mutation whenever there’s a difference. For example, when adding an element at the end of the children, converting between these two trees works well.

        ```javascript
        <ul>
          <li>first</li>
          <li>second</li>
        </ul>

        <ul>
          <li>first</li>
          <li>second</li>
          <li>third</li>
        </ul>

        ```

     5. `Handling keys:`
        React supports a key attribute. When children have keys, React uses the key to match children in the original tree with children in the subsequent tree. For example, adding a key can make the tree conversion efficient,

     ```javascript
     <ul>
       <li key="2015">Duke</li>
       <li key="2016">Villanova</li>
     </ul>

     <ul>
       <li key="2014">Connecticut</li>
       <li key="2015">Duke</li>
       <li key="2016">Villanova</li>
     </ul>
     ```

204. ### When do you need to use refs?

     There are few use cases to go for refs,

     1. Managing focus, text selection, or media playback.
     2. Triggering imperative animations.
     3. Integrating with third-party DOM libraries.

205. ### Must prop be named as render for render props?

     Even though the pattern named render props, you don’t have to use a prop named render to use this pattern. i.e, Any prop that is a function that a component uses to know what to render is technically a “render prop”. Lets take an example with the children prop for render props,

     ```javascript
     <Mouse
       children={(mouse) => (
         <p>
           The mouse position is {mouse.x}, {mouse.y}
         </p>
       )}
     />
     ```

     Actually children prop doesn’t need to be named in the list of “attributes” in JSX element. Instead, you can keep it directly inside element,

     ```javascript
     <Mouse>
       {(mouse) => (
         <p>
           The mouse position is {mouse.x}, {mouse.y}
         </p>
       )}
     </Mouse>
     ```

     While using this above technique(without any name), explicitly state that children should be a function in your propTypes.

     ```javascript
     Mouse.propTypes = {
       children: PropTypes.func.isRequired,
     };
     ```

206. ### What are the problems of using render props with pure components?

     If you create a function inside a render method, it negates the purpose of pure component. Because the shallow prop comparison will always return false for new props, and each render in this case will generate a new value for the render prop. You can solve this issue by defining the render function as instance method.

207. ### What is windowing technique?

     Windowing is a technique that only renders a small subset of your rows at any given time, and can dramatically reduce the time it takes to re-render the components as well as the number of DOM nodes created. If your application renders long lists of data then this technique is recommended. Both react-window and react-virtualized are popular windowing libraries which provides several reusable components for displaying lists, grids, and tabular data.

208. ### How do you print falsy values in JSX?

     The falsy values such as false, null, undefined, and true are valid children but they don't render anything. If you still want to display them then you need to convert it to string. Let's take an example on how to convert to a string,

     ```javascript
     <div>My JavaScript variable is {String(myVariable)}.</div>
     ```

209. ### What is the typical use case of portals?

     React portals are very useful when a parent component has overflow: hidden or has properties that affect the stacking context (e.g. z-index, position, opacity) and you need to visually “break out” of its container.

     For example, dialogs, global message notifications, hovercards, and tooltips.

210. ### How do you set default value for uncontrolled component?

     In React, the value attribute on form elements will override the value in the DOM. With an uncontrolled component, you might want React to specify the initial value, but leave subsequent updates uncontrolled. To handle this case, you can specify a `defaultValue` attribute instead of `value`.

     ```javascript
     render() {
       return (
         <form onSubmit={this.handleSubmit}>
           <label>
             User Name:
             <input
               defaultValue="John"
               type="text"
               ref={this.input} />
           </label>
           <input type="submit" value="Submit" />
         </form>
       );
     }
     ```

     The same applies for `select` and `textArea` inputs. But you need to use `defaultChecked` for `checkbox` and `radio` inputs.

211. ### What is your favorite React stack?

     Even though the tech stack varies from developer to developer, the most popular stack is used in react boilerplate project code. It mainly uses Redux and redux-saga for state management and asynchronous side-effects, react-router for routing purpose, styled-components for styling react components, axios for invoking REST api, and other supported stack such as webpack, reselect, ESNext, Babel.
     You can clone the project https://github.com/react-boilerplate/react-boilerplate and start working on any new react project.

212. ### What is the difference between Real DOM and Virtual DOM?

     Below are the main differences between Real DOM and Virtual DOM,

     | Real DOM                             | Virtual DOM                          |
     | ------------------------------------ | ------------------------------------ |
     | Updates are slow                     | Updates are fast                     |
     | DOM manipulation is very expensive.  | DOM manipulation is very easy        |
     | You can update HTML directly.        | You Can’t directly update HTML       |
     | It causes too much of memory wastage | There is no memory wastage           |
     | Creates a new DOM if element updates | It updates the JSX if element update |

213. ### How to add Bootstrap to a react application?

     Bootstrap can be added to your React app in a three possible ways,

     1. Using the Bootstrap CDN:
        This is the easiest way to add bootstrap. Add both bootstrap CSS and JS resources in a head tag.
     2. Bootstrap as Dependency:
        If you are using a build tool or a module bundler such as Webpack, then this is the preferred option for adding Bootstrap to your React application
        ```javascript
        npm install bootstrap
        ```
     3. React Bootstrap Package:
        In this case, you can add Bootstrap to our React app is by using a package that has rebuilt Bootstrap components to work particularly as React components. Below packages are popular in this category,
        1. react-bootstrap
        2. reactstrap

214. ### Can you list down top websites or applications using react as front end framework?

     Below are the `top 10 websites` using React as their front-end framework,

     1. Facebook
     2. Uber
     3. Instagram
     4. WhatsApp
     5. Khan Academy
     6. Airbnb
     7. Dropbox
     8. Flipboard
     9. Netflix
     10. PayPal

215. ### Is it recommended to use CSS In JS technique in React?

     React does not have any opinion about how styles are defined but if you are a beginner then good starting point is to define your styles in a separate \*.css file as usual and refer to them using className. This functionality is not part of React but came from third-party libraries. But If you want to try a different approach(CSS-In-JS) then styled-components library is a good option.

216. ### Do I need to rewrite all my class components with hooks?

     No. But you can try Hooks in a few components(or new components) without rewriting any existing code. Because there are no plans to remove classes in ReactJS.

217. ### How to fetch data with React Hooks?

     The effect hook called `useEffect` can be used to fetch data from an API and to set the data in the local state of the component with the useState hook’s update function.

     Here is an example of fetching a list of react articles from an API using fetch.

     ```javascript
     import React from "react";

     function App() {
       const [data, setData] = React.useState({ hits: [] });

       React.useEffect(() => {
         fetch("http://hn.algolia.com/api/v1/search?query=react")
           .then((response) => response.json())
           .then((data) => setData(data));
       }, []);

       return (
         <ul>
           {data.hits.map((item) => (
             <li key={item.objectID}>
               <a href={item.url}>{item.title}</a>
             </li>
           ))}
         </ul>
       );
     }

     export default App;
     ```

     A popular way to simplify this is by using the library axios.

     We provided an empty array as second argument to the useEffect hook to avoid activating it on component updates. This way, it only fetches on component mount.

218. ### Is Hooks cover all use cases for classes?

     Hooks doesn't cover all use cases of classes but there is a plan to add them soon. Currently there are no Hook equivalents to the uncommon `getSnapshotBeforeUpdate` and `componentDidCatch` lifecycles yet.

219. ### What is the stable release for hooks support?

     React includes a stable implementation of React Hooks in 16.8 release for below packages

     1. React DOM
     2. React DOM Server
     3. React Test Renderer
     4. React Shallow Renderer

220. ### Why do we use array destructuring (square brackets notation) in `useState`?

     When we declare a state variable with `useState`, it returns a pair — an array with two items. The first item is the current value, and the second is a function that updates the value. Using [0] and [1] to access them is a bit confusing because they have a specific meaning. This is why we use array destructuring instead.

     For example, the array index access would look as follows:

     ```javascript
     var userStateVariable = useState("userProfile"); // Returns an array pair
     var user = userStateVariable[0]; // Access first item
     var setUser = userStateVariable[1]; // Access second item
     ```

     Whereas with array destructuring the variables can be accessed as follows:

     ```javascript
     const [user, setUser] = useState("userProfile");
     ```

221. ### What are the sources used for introducing hooks?

     Hooks got the ideas from several different sources. Below are some of them,

     1. Previous experiments with functional APIs in the react-future repository
     2. Community experiments with render prop APIs such as Reactions Component
     3. State variables and state cells in DisplayScript.
     4. Subscriptions in Rx.
     5. Reducer components in ReasonReact.

222. ### How do you access imperative API of web components?

     Web Components often expose an imperative API to implement its functions. You will need to use a `ref` to interact with the DOM node directly if you want to access imperative API of a web component. But if you are using third-party Web Components, the best solution is to write a React component that behaves as a `wrapper` for your Web Component.

223. ### What is formik?

     Formik is a small react form library that helps you with the three major problems,

     1. Getting values in and out of form state
     2. Validation and error messages
     3. Handling form submission

224. ### What are typical middleware choices for handling asynchronous calls in Redux?

     Some of the popular middleware choices for handling asynchronous calls in Redux eco system are `Redux Thunk, Redux Promise, Redux Saga`.

225. ### Do browsers understand JSX code?

     No, browsers can't understand JSX code. You need a transpiler to convert your JSX to regular Javascript that browsers can understand. The most widely used transpiler right now is Babel.

226. ### Describe about data flow in react?

     React implements one-way reactive data flow using props which reduce boilerplate and is easier to understand than traditional two-way data binding.

227. ### What is MobX?

     MobX is a simple, scalable and battle tested state management solution for applying functional reactive programming (TFRP). For ReactJS application, you need to install below packages,

     ```bash
     npm install mobx --save
     npm install mobx-react --save
     ```

228. ### What are the differences between Redux and MobX?

     Below are the main differences between Redux and MobX,

     | Topic         | Redux                                                         | MobX                                                                   |
     | ------------- | ------------------------------------------------------------- | ---------------------------------------------------------------------- |
     | Definition    | It is a javascript library for managing the application state | It is a library for reactively managing the state of your applications |
     | Programming   | It is mainly written in ES6                                   | It is written in JavaScript(ES5)                                       |
     | Data Store    | There is only one large store exist for data storage          | There is more than one store for storage                               |
     | Usage         | Mainly used for large and complex applications                | Used for simple applications                                           |
     | Performance   | Need to be improved                                           | Provides better performance                                            |
     | How it stores | Uses JS Object to store                                       | Uses observable to store the data                                      |

229. ### Should I learn ES6 before learning ReactJS?

     No, you don’t have to learn es2015/es6 to learn react. But you may find many resources or React ecosystem uses ES6 extensively. Let's see some of the frequently used ES6 features,

     1. `Destructuring:` To get props and use them in a component

        ```javascript
        // in es 5
        var someData = this.props.someData;
        var dispatch = this.props.dispatch;

        // in es6
        const { someData, dispatch } = this.props;
        ```

     2. `Spread operator:` Helps in passing props down into a component

        ```javascript
        // in es 5
        <SomeComponent someData={this.props.someData} dispatch={this.props.dispatch} />

        // in es6
        <SomeComponent {...this.props} />
        ```

     3. `Arrow functions:` Makes compact syntax
        ```javascript
        // es 5
        var users = usersList.map(function (user) {
          return <li>{user.name}</li>;
        });
        // es 6
        const users = usersList.map((user) => <li>{user.name}</li>);
        ```

230. ### What is Concurrent Rendering?

     The Concurrent rendering makes React apps to be more responsive by rendering component trees without blocking the main UI thread. It allows React to interrupt a long-running render to handle a high-priority event. i.e, When you enabled concurrent Mode, React will keep an eye on other tasks that need to be done, and if there's something with a higher priority it will pause what it is currently rendering and let the other task finish first. You can enable this in two ways,

     ```javascript
     // 1. Part of an app by wrapping with ConcurrentMode
     <React.unstable_ConcurrentMode>
       <Something />
     </React.unstable_ConcurrentMode>;

     // 2. Whole app using createRoot
     ReactDOM.unstable_createRoot(domNode).render(<App />);
     ```

231. ### What is the difference between async mode and concurrent mode?

     Both refers the same thing. Previously concurrent Mode being referred to as "Async Mode" by React team. The name has been changed to highlight React’s ability to perform work on different priority levels. So it avoids the confusion from other approaches to Async Rendering.

232. ### Can I use javascript urls in react16.9?

     Yes, you can use javascript: URLs but it will log a warning in the console. Because URLs starting with javascript: are dangerous by including unsanitized output in a tag like `<a href>` and create a security hole.

     ```javascript
     const companyProfile = {
       website: "javascript: alert('Your website is hacked')",
     };
     // It will log a warning
     <a href={companyProfile.website}>More details</a>;
     ```

     Remember that the future versions will throw an error for javascript URLs.

233. ### What is the purpose of eslint plugin for hooks?

     The ESLint plugin enforces rules of Hooks to avoid bugs. It assumes that any function starting with ”use” and a capital letter right after it is a Hook. In particular, the rule enforces that,

     1. Calls to Hooks are either inside a PascalCase function (assumed to be a component) or another useSomething function (assumed to be a custom Hook).
     2. Hooks are called in the same order on every render.

234. ### What is the difference between Imperative and Declarative in React?

     Imagine a simple UI component, such as a "Like" button. When you tap it, it turns blue if it was previously grey, and grey if it was previously blue.

     The imperative way of doing this would be:

     ```javascript
     if (user.likes()) {
       if (hasBlue()) {
         removeBlue();
         addGrey();
       } else {
         removeGrey();
         addBlue();
       }
     }
     ```

     Basically, you have to check what is currently on the screen and handle all the changes necessary to redraw it with the current state, including undoing the changes from the previous state. You can imagine how complex this could be in a real-world scenario.

     In contrast, the declarative approach would be:

     ```javascript
     if (this.state.liked) {
       return <blueLike />;
     } else {
       return <greyLike />;
     }
     ```

     Because the declarative approach separates concerns, this part of it only needs to handle how the UI should look in a specific state, and is therefore much simpler to understand.

235. ### What are the benefits of using TypeScript with ReactJS?

     Below are some of the benefits of using TypeScript with ReactJS,

     1. It is possible to use latest JavaScript features
     2. Use of interfaces for complex type definitions
     3. IDEs such as VS Code was made for TypeScript
     4. Avoid bugs with the ease of readability and Validation

236. ### How do you make sure that user remains authenticated on page refresh while using Context API State Management?

     When a user logs in and reload, to persist the state generally we add the load user action in the useEffect hooks in the main App.js. While using Redux, loadUser action can be easily accessed.

     `App.js`

     ```js
     import { loadUser } from "../actions/auth";
     store.dispatch(loadUser());
     ```

     - But while using `Context API`, to access context in App.js, wrap the AuthState in index.js so that App.js can access the auth context. Now whenever the page reloads, no matter what route you are on, the user will be authenticated as `loadUser` action will be triggered on each re-render.

     `index.js`

     ```js
     import React from "react";
     import ReactDOM from "react-dom";
     import App from "./App";
     import AuthState from "./context/auth/AuthState";

     ReactDOM.render(
       <React.StrictMode>
         <AuthState>
           <App />
         </AuthState>
       </React.StrictMode>,
       document.getElementById("root")
     );
     ```

     `App.js`

     ```js
     const authContext = useContext(AuthContext);

     const { loadUser } = authContext;

     useEffect(() => {
       loadUser();
     }, []);
     ```

     `loadUser`

     ```js
     const loadUser = async () => {
       const token = sessionStorage.getItem("token");

       if (!token) {
         dispatch({
           type: ERROR,
         });
       }
       setAuthToken(token);

       try {
         const res = await axios("/api/auth");

         dispatch({
           type: USER_LOADED,
           payload: res.data.data,
         });
       } catch (err) {
         console.error(err);
       }
     };
     ```

237. ### What are the benefits of new JSX transform?

     There are three major benefits of new JSX transform,

     1. It is possible to use JSX without importing React packages
     2. The compiled output might improve the bundle size in a small amount
     3. The future improvements provides the flexibility to reduce the number of concepts to learn React.

238. ### How is the new JSX transform different from old transform??

     The new JSX transform doesn’t require React to be in scope. i.e, You don't need to import React package for simple scenarios.

     Let's take an example to look at the main differences between the old and the new transform,

     `Old Transform:`

     ```js
     import React from "react";

     function App() {
       return <h1>Good morning!!</h1>;
     }
     ```

     Now JSX transform convert the above code into regular JavaScript as below,

     ```js
     import React from "react";

     function App() {
       return React.createElement("h1", null, "Good morning!!");
     }
     ```

     `New Transform:`

     The new JSX transform doesn't require any React imports

     ```js
     function App() {
       return <h1>Good morning!!</h1>;
     }
     ```

     Under the hood JSX transform compiles to below code

     ```js
     import { jsx as _jsx } from "react/jsx-runtime";

     function App() {
       return _jsx("h1", { children: "Good morning!!" });
     }
     ```

     `Note:` You still need to import React to use Hooks.

239. ### What are React Server components?

     React Server Component is a way to write React component that gets rendered in the server-side with the purpose of improving React app performance. These components allow us to load components from the backend.

     `Note:` React Server Components is still under development and not recommended for production yet.

240. ### What is prop drilling?

     Prop Drilling is the process by which you pass data from one component of the React Component tree to another by going through other components that do not need the data but only help in passing it around.

241. ### What is the difference between useState and useRef hook?

     1. useState causes components to re-render after state updates whereas useRef doesn’t cause a component to re-render when the value or state changes.
        Essentially, useRef is like a “box” that can hold a mutable value in its (.current) property.
     2. useState allows us to update the state inside components. While useRef allows referencing DOM elements.

242. ### What is a wrapper component?

     A wrapper in React is a component that wraps or surrounds another component or group of components. It can be used for a variety of purposes such as adding additional functionality, styling, or layout to the wrapped components.

     For example, consider a simple component that displays a message:

     ```javascript
     const Message = ({ text }) => {
       return <p>{text}</p>;
     };
     ```

     We can create a wrapper component that will add a border to the message component:

     ```javascript
     const MessageWrapper = (props) => {
       return (
         <div style={{ border: "1px solid black" }}>
           <Message {...props} />
         </div>
       );
     };
     ```

     Now we can use the MessageWrapper component instead of the Message component and the message will be displayed with a border:

     ```javascript
     <MessageWrapper text="Hello World" />
     ```

     Wrapper component can also accept its own props and pass them down to the wrapped component, for example, we can create a wrapper component that will add a title to the message component:

     ```javascript
     const MessageWrapperWithTitle = ({ title, ...props }) => {
       return (
         <div>
           <h3>{title}</h3>
           <Message {...props} />
         </div>
       );
     };
     ```

     Now we can use the MessageWrapperWithTitle component and pass title props:

     ```javascript
     <MessageWrapperWithTitle title="My Message" text="Hello World" />
     ```

     This way, the wrapper component can add additional functionality, styling, or layout to the wrapped component while keeping the wrapped component simple and reusable.

243. ### What are the differences between useEffect and useLayoutEffect hooks?

     useEffect and useLayoutEffect are both React hooks that can be used to synchronize a component with an external system, such as a browser API or a third-party library. However, there are some key differences between the two:

     - Timing: useEffect runs after the browser has finished painting, while useLayoutEffect runs synchronously before the browser paints. This means that useLayoutEffect can be used to measure and update layout in a way that feels more synchronous to the user.

     - Browser Paint: useEffect allows browser to paint the changes before running the effect, hence it may cause some visual flicker. useLayoutEffect synchronously runs the effect before browser paints and hence it will avoid visual flicker.

     - Execution Order: The order in which multiple useEffect hooks are executed is determined by React and may not be predictable. However, the order in which multiple useLayoutEffect hooks are executed is determined by the order in which they were called.

     - Error handling: useEffect has a built-in mechanism for handling errors that occur during the execution of the effect, so that it does not crash the entire application. useLayoutEffect does not have this mechanism, and errors that occur during the execution of the effect will crash the entire application.

     In general, it's recommended to use useEffect as much as possible, because it is more performant and less prone to errors. useLayoutEffect should only be used when you need to measure or update layout, and you can't achieve the same result using useEffect.

244. ### What are the differences between Functional and Class Components?

     There are two different ways to create components in ReactJS. The main differences are listed down as below,

     ## 1. Syntax:

     The class components uses ES6 classes to create the components. It uses `render` function to display the HTML content in the webpage.

     The syntax for class component looks like as below.

     ```js
     class App extends React.Component {
       render() {
         return <h1>This is a class component</h1>;
       }
     }
     ```

     `Note:` The `Pascal Case` is the recommended approach to provide naming to a component.

     Functional component has been improved over the years with some added features like Hooks. Here is a syntax for functional component.

     ```js
     function App() {
       return (
         <div className="App">
           <h1>Hello, I'm a function component</h1>
         </div>
       );
     }
     ```

     ## 2. State:

     State contains information or data about a component which may change over time.

     In class component, you can update the state when a user interacts with it or server updates the data using the `setState()` method. The initial state is going to be assigned in the `Constructor()` method using the `this.state` object and it is possible to assign different data types such as string, boolean, numbers, etc.

     `A simple example showing how we use the setState() and constructor():`

     ```js
     class App extends Component {
       constructor() {
         super();
         this.state = {
           message: "This is a class component",
         };
       }
       updateMessage() {
         this.setState({
           message: "Updating the class component",
         });
       }
       render() {
         return (
           <>
             <h1>{this.state.message}</h1>
             <button
               onClick={() => {
                 this.updateMessage();
               }}
             >
               Click!!
             </button>
           </>
         );
       }
     }
     ```

     You didn't use state in functional components because it was only supported in class components. But over the years hooks have been implemented in functional components which enables to use state too.

     The `useState()` hook can used to implement state in functional components. It returns an array with two items: the first item is current state and the next one is a function (setState) that updates the value of the current state.

     Let's see an example to demonstrate the state in functional components,

     ```js
     function App() {
       const [message, setMessage] = useState("This is a functional component");
       const updateMessage = () => {
         setMessage("Updating the functional component");
       };
       return (
         <div className="App">
           <h1>{message} </h1>
           <button onClick={updateMessage}>Click me!!</button>
         </div>
       );
     }
     ```

     ## 3. Props:

     Props are referred to as "properties". The props are passed into React component just like arguments passed to a function. In other words, they are similar to HTML attributes.

     The props are accessible in child class component using `this.props` as shown in below example,

     ```js
     class Child extends React.Component {
       render() {
         return (
           <h1>
             {" "}
             This is a functional component and component name is {
               this.props.name
             }{" "}
           </h1>
         );
       }
     }

     class Parent extends React.Component {
       render() {
         return (
           <div className="Parent">
             <Child name="First child component" />
             <Child name="Second child component" />
           </div>
         );
       }
     }
     ```

     Props in functional components are similar to that of the class components but the difference is the absence of 'this' keyword.

     ```js
     function Child(props) {
       return (
         <h1>
           This is a child component and the component name is{props.name}
         </h1>
       );
     }

     function Parent() {
       return (
         <div className="Parent">
           <Child name="First child component" />
           <Child name="Second child component" />
         </div>
       );
     }
     ```

245. ### What is strict mode in React?

     `React.StrictMode` is a useful component for highlighting potential problems in an application. Just like `<Fragment>`, `<StrictMode>` does not render any extra DOM elements. It activates additional checks and warnings for its descendants. These checks apply for _development mode_ only.

     ```javascript
     import { StrictMode } from "react";

     function App() {
       return (
         <div>
           <Header />
           <StrictMode>
             <div>
               <ComponentOne />
               <ComponentTwo />
             </div>
           </StrictMode>
           <Header />
         </div>
       );
     }
     ```

     In the example above, the _strict mode_ checks apply to `<ComponentOne>` and `<ComponentTwo>` components only. i.e., Part of the application only.

     `Note:` Frameworks such as NextJS has this flag enabled by default.

246. ### What is the benefit of strict mode?

     The <StrictMode> will be helpful in the below cases,

     1. To find the bugs caused by impure rendering where the components will re-render twice.
     2. To find the bugs caused by missing cleanup of effects where the components will re-run effects one more extra time.
     3. Identifying components with `unsafe lifecycle methods`.
     4. Warning about `legacy string ref` API usage.
     5. Detecting unexpected `side effects`.
     6. Detecting `legacy context` API.
     7. Warning about deprecated `findDOMNode` usage

247. ### Why does strict mode render twice in React?

     StrictMode renders components twice in development mode(not production) in order to detect any problems with your code and warn you about those problems. This is used to detect accidental side effects in the render phase. If you used `create-react-app` development tool then it automatically enables StrictMode by default.

     ```js
     const root = createRoot(document.getElementById("root"));
     root.render(
       <StrictMode>
         <App />
       </StrictMode>
     );
     ```

     If you want to disable this behavior then you can simply remove `strict` mode.

     ```js
     const root = createRoot(document.getElementById("root"));
     root.render(<App />);
     ```

     To detect side effects the following functions are invoked twice:

     1. Function component bodies, excluding the code inside event handlers.
     2. Functions passed to `useState`, `useMemo`, or `useReducer` (any other Hook)
     3. Class component's `constructor`, `render`, and `shouldComponentUpdate` methods
     4. Class component static `getDerivedStateFromProps` method
     5. State updater functions

248. ### What are the rules of JSX?

     The below 3 rules needs to be followed while using JSX in a react application.

     1. `Return a single root element`:
        If you are returning multiple elements from a component, wrap them in a single parent element. Otherwise you will receive the below error in your browser console.

        `html Adjacent JSX elements must be wrapped in an enclosing tag.`

     2. `All the tags needs to be closed:`
        Unlike HTML, all tags needs to closed explicitly with in JSX. This rule applies for self-closing tags(like hr, br and img tags) as well.
     3. `Use camelCase naming:`
        It is suggested to use camelCase naming for attributes in JSX. For example, the common attributes of HTML elements such as `class`, `tabindex` will be used as `className` and `tabIndex`.  
        `Note:` There is an exception for `aria-*` and `data-*` attributes which should be lower cased all the time.

249. ### What is the reason behind multiple JSX tags to be wrapped?

     Behind the scenes, JSX is transformed into plain javascript objects. It is not possible to return two or more objects from a function without wrapping into an array. This is the reason you can't simply return two or more JSX tags from a function without
     wrapping them into a single parent tag or a Fragment.

250. ### How do you prevent mutating array variables?

     The preexisting variables outside of the function scope including state, props and context leads to a mutation and they result in unpredictable bugs during the rendering stage. The below points should be taken care while working with arrays variables.

     1. You need to take copy of the original array and perform array operations on it for the rendering purpose. This is called local mutation.
     2. Avoid triggering mutation methods such as push, pop, sort and reverse methods on original array. It is safe to use filter, map and slice method because they create a new array.

251. ### What are capture phase events?

     The `onClickCapture` React event is helpful to catch all the events of child elements irrespective of event propagation logic or even if the events propagation stopped. This is useful if you need to log every click events for analytics purpose.

     For example, the below code triggers the click event of parent first followed by second level child eventhough leaf child button elements stops the propagation.

     ```jsx
     <div onClickCapture={() => alert("parent")}>
       <div onClickCapture={() => alert("child")}>
         <button onClick={(e) => e.stopPropagation()} />
         <button onClick={(e) => e.stopPropagation()} />
       </div>
     </div>
     ```

     The event propagation for the above code snippet happens in the following order:

     1. It travels downwards in the DOM tree by calling all `onClickCapture` event handlers.
     2. It executes `onClick` event handler on the target element.
     3. It travels upwards in the DOM tree by call all `onClick` event handlers above to it.

252. ### How does React updates screen in an application?

     React updates UI in three steps,

     1. `Triggering or initiating a render:` The component is going to triggered for render in two ways.

        1. `Initial render:` When the app starts, you can trigger the initial render by calling `creatRoot` with the target DOM node followed by invoking component's `render` method. For example, the following code snippet renders `App` component on root DOM node.

        ```jsx
        import { createRoot } from "react-dom/client";

        const root = createRoot(document.getElementById("root"));
        root.render(<App />);
        ```

        2. `Re-render when the state updated:` When you update the component state using the state setter function, the componen't state automatically queues for a render.

     2. `Rendering components:` After triggering a render, React will call your components to display them on the screen. React will call the root component for initial render and call the function component whose state update triggered the render. This is a recursive process for all nested components of the target component.

     3. `Commit changes to DOM:` After calling components, React will modify the DOM for initial render using `appendChild()` DOM API and apply minimal necessary DOM updates for re-renders based on differences between rerenders.

253. ### How does React batch multiple state updates?

     React prevents component from re-rendering for each and every state update by grouping multiple state updates within an event handler. This strategy improves the application performance and this process known as `batching`. The older version of React only supported batching for browser events whereas React18 supported for asynchronous actions, timeouts and intervals along with native events. This improved version of batching is called `automatic batching`.

     Let's demonstrate this automatic batching feature with a below example.

     ```jsx
     import { useState } from "react";

     export default function BatchingState() {
       const [count, setCount] = useState(0);
       const [message, setMessage] = useState("batching");

       console.log("Application Rendered");

       const handleUsers = () => {
         fetch("https://jsonplaceholder.typicode.com/users/1").then(() => {
           // Automatic Batching re-render only once
           setCount(count + 1);
           setMessage("users fetched");
         });
       };

       return (
         <>
           <h1>{count}</h1>
           <button onClick={handleAsyncFetch}>Click Me!</button>
         </>
       );
     }
     ```

     The preceding code updated two state variables with in an event handler. However, React will perform automatic batching feature and the component will be re-rendered only once for better performance.

254. ### Is it possible to prevent automatic batching?

     Yes, it is possible to prevent automatic batching default behavior. There might be cases where you need to re-render your component after each state update or updating one state depends on another state variable. Considering this situation, React introduced `flushSync` method from `react-dom` API for the usecases where you need to flush state updates to DOM immediately.

     The usage of `flushSync` method within an `onClick` event handler will be looking like as below,

     ```jsx
     import { flushSync } from "react-dom";

     const handleClick = () => {
       flushSync(() => {
         setClicked(!clicked); //Component will create a re-render here
       });

       setCount(count + 1); // Component will create a re-render again here
     };
     ```

     In the above click handler, React will update DOM at first using flushSync and second time updates DOM because of the counter setter function by avoiding automatic batching.

255. ### What is React hydration?

     React hydration is used to add client-side JavaScript interactivity to pre-rendered static HTML generated by the server. It is used only for server-side rendering(SSR) to enhance the initial rendering time and make it SEO friendly application. This hydration acts as a bridge to reduce the gap between server side and client-side rendering.

     After the page loaded with generated static HTML, React will add application state and interactivity by attaching all event handlers for the respective elements. Let's demonstrate this with an example.

     Consider that React DOM API(using `renderToString`) generated HTML for `<App>` component which contains `<button>` element to increment the counter.

     ```jsx
     import {useState} from 'react';
     import { renderToString } from 'react-dom/server';

     export default function App() {
       const [count, setCount] = React.useState(0);

       return (
         <h1>Counter</h1>
         <button onClick={() => setCount(prevCount => prevCount + 1)}>
           {count} times
         </button>
         );
     }

     const html = renderToString(<App />);
     ```

     The above code generates the below HTML with a header text and button component without any interactivity.

     ```html
     <h1>Counter</h1>
     <button>
       <!-- -->0<!-- -->
       times
     </button>
     ```

     At this stage `hydrateRoot` API can be used to perform hydration by attaching `onClick` event handler.

     ```jsx
     import { hydrateRoot } from "react-dom/client";
     import App from "./App.js";

     hydrateRoot(document.getElementById("root"), <App />);
     ```

     After this step, you are able to run React application on server-side and hydrating the javascript bundle on client-side for smooth user experience and SEO purposes.

256. ### How do you update objects inside state?

     You cannot update the objects which exists in the state directly. Instead, you should create a fresh new object (or copy from the existing object) and update the latest state using the newly created object. Eventhough JavaScript objects are mutable, you need to treat objects inside state as read-only while updating the state.

     Let's see this comparison with an example. The issue with regular object mutation approach can be described by updating the user details fields of `Profile` component. The properties of `Profile` component such as firstName, lastName and age details mutated in an event handler as shown below.

     ```jsx
     import { useState } from "react";

     export default function Profile() {
       const [user, setUser] = useState({
         firstName: "John",
         lastName: "Abraham",
         age: 30,
       });

       function handleFirstNameChange(e) {
         user.firstName = e.target.value;
       }

       function handleLastNameChange(e) {
         user.lastName = e.target.value;
       }

       function handleAgeChange(e) {
         user.age = e.target.value;
       }

       return (
         <>
           <label>
             First name:
             <input value={user.firstName} onChange={handleFirstNameChange} />
           </label>
           <label>
             Last name:
             <input value={user.lastName} onChange={handleLastNameChange} />
           </label>
           <label>
             Age:
             <input value={user.age} onChange={handleAgeChange} />
           </label>
           <p>
             Profile:
             {person.firstName} {person.lastName} ({person.age})
           </p>
         </>
       );
     }
     ```

     Once you run the application with above user profile component, you can observe that user profile details won't be update upon entering the input fields.
     This issue can be fixed by creating a new copy of object which includes existing properties through spread syntax(...obj) and add changed values in a single event handler itself as shown below.

     ```jsx
     handleProfileChange(e) {
       setUser({
       ...user,
         [e.target.name]: e.target.value
       });
     }
     ```

     The above event handler is concise instead of maintaining separate event handler for each field. Now, UI displays the updated field values as expected without an issue.

257. ### How do you update nested objects inside state?

     You cannot simply use spread syntax for all kinds of objects inside state. Because spread syntax is shallow and it copies properties for one level deep only. If the object has nested object structure, UI doesn't work as expected with regular JavaScript nested property mutation. Let's demonstrate this behavior with an example of User object which has address nested object inside of it.

     ```jsx
     const user = {
       name: "John",
       age: 32,
       address: {
         country: "Singapore",
         postalCode: 440004,
       },
     };
     ```

     If you try to update the country nested field in a regular javascript fashion(as shown below) then user profile screen won't be updated with latest value.

     ```js
     user.address.country = "Germany";
     ```

     This issue can be fixed by flattening all the fields into a top-level object or create a new object for each nested object and point it to it's parent object. In this example, first you need to create copy of address object and update it with the latest value. Later, the address object should be linked to parent user object something like below.

     ```js
     setUser({
       ...user,
       address: {
         ...user.address,
         country: "Germany",
       },
     });
     ```

     This approach is bit verbose and not easy for deep hierarchical state updates. But this workaround can be used for few levels of nested objects without much hassle.

258. ### How do you update arrays inside state?

     Eventhough arrays in JavaScript are mutable in nature, you need to treat them as immutable while storing them in a state. That means, similar to objects, the arrays cannot be updated directly inside state. Instead, you need to create a copy of the existing array and then set the state to use newly copied array.

     To ensure that arrays are not mutated, the mutation operations like direct direct assignment(arr[1]='one'), push, pop, shift, unshift, splice etc methods should be avoided on original array. Instead, you can create a copy of existing array with help of array operations such as filter, map, slice, spread syntax etc.

     For example, the below push operation doesn't add the new todo to the total todo's list in an event handler.

     ```jsx
     onClick = {
       todos.push({
         id: id+1,
         name: name
       })
     }
     ```

     This issue is fixed by replacing push operation with spread syntax where it will create a new array and the UI updated with new todo.

     ```jsx
     onClick = {
       [
         ...todos,
         { id: id+1, name: name }
       ]
     }
     ```

259. ### How do you use immer library for state updates?

     Immer library enforces the immutability of state based on `copy-on-write` mechanism. It uses JavaScript proxy to keep track of updates to immutable states. Immer has 3 main states as below,

     1. `Current state:` It refers to actual state
     2. `Draft state:` All new changes will be applied to this state. In this state, draft is just a proxy of the current state.
     3. `Next state:` It is formed after all mutations applied to the draft state

     Immer can be used by following below instructions,

     1. Install the dependency using `npm install use-immer` command
     2. Replace `useState` hook with `useImmer` hook by importing at the top
     3. The setter function of `useImmer` hook can be used to update the state.

     For example, the mutation syntax of immer library simplifies the nested address object of user state as follows,

     ```jsx
     import { useImmer } from "use-immer";
     const [user, setUser] = useImmer({
       name: "John",
       age: 32,
       address: {
         country: "Singapore",
         postalCode: 440004,
       },
     });

     //Update user details upon any event
     setUser((draft) => {
       draft.address.country = "Germany";
     });
     ```

     The preceding code enables you to update nested objects with a conceise mutation syntax.

260. ### What are the benefits of preventing the direct state mutations?

261. ### What are the preferred and non-preferred array operations for updating the state?

     The below table represent preferred and non-preferred array operations for updating the component state.

     | Action    | Preferred            | Non-preferred              |
     | --------- | -------------------- | -------------------------- |
     | Adding    | concat, [...arr]     | push, unshift              |
     | Removing  | filter, slice        | pop, shift, splice         |
     | Replacing | map                  | splice, arr[i] = someValue |
     | sorting   | copying to new array | reverse, sort              |

     If you use Immer library then you can able to use all array methods without any problem.

262. ### What will happen by defining nested function components?

Technically it is possible to write nested function components but it is not suggested to write nested function definitions. Because it leads to unexpected bugs and performance issues.

263. ### Can I use keys for non-list items?

     Keys are primarily used for rendering list items but they are not just for list items. You can also use them React to distinguish components. By default, React uses order of the components in

264. ### What are the guidelines to be followed for writing reducers?

     There are two guidelines to be taken care while writing reducers in your code.

     1. Reducers must be pure without mutating the state. That means, same input always returns the same output. These reducers run during rendering time similar to state updater functions. So these functions should not send any requests, schedule time outs and any other side effects.

     2. Each action should describe a single user interaction eventhough there are multiple changes applied to data. For example, if you "reset" registration form which has many user input fields managed by a reducer, it is suggested to send one "reset" action instead of creating separate action for each fields. The proper ordering of actions should reflect the user interactions in the browser and it helps a lot for debugging purpose.

265. ### What is useReducer hook? Can you describe its usage?

266. ### How do you compare useState and useReducer?

267. ### How does context works using useContext hook?

268. ### What are the use cases of useContext hook?

     Some of the common use cases of useContext are listed below,

     1. `Theme customizations:` The useContext hook can be used to manage and apply custom themes for an application. That means it allows users to personalize the appearance of the application.
     2. `Support localization:` The context hook is helpful to implement localization by providing translated strings to components based on the user's language/locale preference.
     3. `User authentication:` It can be used to manage user authentication or session status and display user specific information with in components.

269. ### When to use client and server components?

     You can efficiently build nextjs application if you are aware about which part of the application needs to use client components and which other parts needs to use server components. The common cases of both client and server components are listed below:

     `Client components:`

     1. Whenever your need to add interactivity and event listeners such as onClick(), onChange(), etc to the pages
     2. If you need to use State and Lifecycle Effects like useState(), useReducer(), useEffect() etc.
     3. If there is a requirement to use browser-only APIs.
     4. If you need to implement custom hooks that depend on state, effects, or browser-only APIs.
     5. There are React Class components in the pages.

     `Server components:`

     1. If the component logic is about data fetching.
     2. If you need to access backend resources directly.
     3. When you need to keep sensitive information((access tokens, API keys, etc) ) on the server.
     4. If you want reduce client-side JavaScript and placing large dependencies on the server.

270. ### What are the differences between page router and app router in nextjs?

271. ### Can you describe the useMemo() Hook?

     The `useMemo()` Hook in React is used to `optimize performance` by `memoizing the result of expensive calculations`. It ensures that a function is `only re-executed when its dependencies change`, preventing unnecessary computations on every re-render.

     #### Syntax

     ```js
     const memoizedValue = useMemo(
       () => computeExpensiveValue(arg),
       [dependencies]
     );
     ```

     - `computeExpensiveValue`:  
       A function that returns the computed result.

     - `dependencies`:  
       An array of values that, when changed, will cause the memoized function to re-run.

     If the dependencies haven’t changed since the last render, React returns the `cached result` instead of re-running the function.

     Let's exaplain the usage of `useMemo` hook with an example of user search and its respective filtered users list.

     #### Example: Memoizing a Filtered List

     ```javascript
     import React, { useState, useMemo } from "react";

     const users = [
       { id: 1, name: "Sudheer" },
       { id: 2, name: "Brendon" },
       { id: 3, name: "Charlie" },
       { id: 4, name: "Dary" },
       { id: 5, name: "Eden" },
     ];

     export default function UserSearch() {
       const [searchTerm, setSearchTerm] = useState("");
       const [counter, setCounter] = useState(0);

       // Memoize the filtered user list based on the search term
       const filteredUsers = useMemo(() => {
         console.log("Filtering users...");
         return users.filter((user) =>
           user.name.toLowerCase().includes(searchTerm.toLowerCase())
         );
       }, [searchTerm]);

       return (
         <div>
           <h2>Counter: {counter}</h2>
           <button onClick={() => setCounter((prev) => prev + 1)}>
             Increment Counter
           </button>

           <h2>Search Users</h2>
           <input
             type="text"
             value={searchTerm}
             onChange={(e) => setSearchTerm(e.target.value)}
             placeholder="Enter name"
           />

           <ul>
             {filteredUsers.map((user) => (
               <li key={user.id}>{user.name}</li>
             ))}
           </ul>
         </div>
       );
     }
     ```

     In the above example:

     - The filteredUsers list is only recomputed when searchTerm changes.
     - Pressing the "Increment Counter" button does not trigger the filtering logic again, as it's not a dependency.
     - The console will only log "Filtering users..." when the search term updates.

## Old Q&A

1.  ### Why should we not update the state directly?

    If you try to update the state directly then it won't re-render the component.

    ```javascript
    //Wrong
    this.state.message = "Hello world";
    ```

    Instead use `setState()` method. It schedules an update to a component's state object. When state changes, the component responds by re-rendering.

    ```javascript
    //Correct
    this.setState({ message: "Hello World" });
    ```

    `Note:` You can directly assign to the state object either in _constructor_ or using latest javascript's class field declaration syntax.

2.  ### What is the purpose of callback function as an argument of `setState()`?

    The callback function provided as the second argument to `setState` is executed after the state has been updated and the component has re-rendered. Because `setState()` is asynchronous, you cannot reliably perform actions that require the updated state immediately after calling `setState`. The callback ensures your code runs only after the update and re-render are complete.

    #### Example

    ```jsx
    this.setState({ name: "Sudheer" }, () => {
      console.log(
        "The name has been updated and the component has re-rendered."
      );
    });
    ```

    #### When to use the callback?

    Use the `setState` callback when you need to perform an action immediately after the DOM has been updated in response to a state change. i.e, The callback is a reliable way to perform actions after a state update and re-render, especially when the timing is critical due to the asynchronous nature of state updates in React. For example, if you need to interact with the updated DOM, trigger analytics, or perform further computations that depend on the new state or rendered output.

    #### Note

    - In modern React (with function components), you can achieve similar effects using the `useEffect` hook to respond to state changes.
    - In class components, you can also use lifecycle methods like `componentDidUpdate` for broader post-update logic.
    - The `setState` callback is still useful for one-off actions that directly follow a specific state change.

3.  ### How to bind methods or event handlers in JSX callbacks?

    There are 3 possible ways to achieve this in class components:

    1. `Binding in Constructor:` In JavaScript classes, the methods are not bound by default. The same rule applies for React event handlers defined as class methods. Normally we bind them in constructor.

       ```javascript
       class User extends Component {
         constructor(props) {
           super(props);
           this.handleClick = this.handleClick.bind(this);
         }
         handleClick() {
           console.log("SingOut triggered");
         }
         render() {
           return <button onClick={this.handleClick}>SingOut</button>;
         }
       }
       ```

    2. `Public class fields syntax:` If you don't like to use bind approach then _public class fields syntax_ can be used to correctly bind callbacks. The Create React App enables this syntax by default.

       ```javascript
       handleClick = () => {
         console.log("SingOut triggered", this);
       };
       ```

       ```javascript
       <button onClick={this.handleClick}>SingOut</button>
       ```

    3. `Arrow functions in callbacks:` It is possible to use _arrow functions_ directly in the callbacks.

       ```javascript
       handleClick() {
           console.log('SingOut triggered');
       }
       render() {
           return <button onClick={() => this.handleClick()}>SignOut</button>;
       }
       ```

    `Note:` If the callback is passed as prop to child components, those components might do an extra re-rendering. In those cases, it is preferred to go with `.bind()` or _public class fields syntax_ approach considering performance.

4.  ### How to pass a parameter to an event handler or callback?

    You can use an _arrow function_ to wrap around an _event handler_ and pass parameters:

    ```javascript
    <button onClick={() => this.handleClick(id)} />
    ```

    This is an equivalent to calling `.bind`:

    ```javascript
    <button onClick={this.handleClick.bind(this, id)} />
    ```

    Apart from these two approaches, you can also pass arguments to a function which is defined as arrow function

    ```javascript
    <button onClick={this.handleClick(id)} />;
    handleClick = (id) => () => {
      console.log("Hello, your ticket number is", id);
    };
    ```

5.  ### What is the use of refs?

    The _ref_ is used to return a reference to the element. They _should be avoided_ in most cases, however, they can be useful when you need a direct access to the DOM element or an instance of a component.

6.  ### How to create refs?

    There are two approaches

    1. This is a recently added approach. _Refs_ are created using `React.createRef()` method and attached to React elements via the `ref` attribute. In order to use _refs_ throughout the component, just assign the _ref_ to the instance property within constructor.

       ```javascript
       class MyComponent extends React.Component {
         constructor(props) {
           super(props);
           this.myRef = React.createRef();
         }
         render() {
           return <div ref={this.myRef} />;
         }
       }
       ```

    2. You can also use ref callbacks approach regardless of React version. For example, the search bar component's input element is accessed as follows,
       ```javascript
       class SearchBar extends Component {
         constructor(props) {
           super(props);
           this.txtSearch = null;
           this.state = { term: "" };
           this.setInputSearchRef = (e) => {
             this.txtSearch = e;
           };
         }
         onInputChange(event) {
           this.setState({ term: this.txtSearch.value });
         }
         render() {
           return (
             <input
               value={this.state.term}
               onChange={this.onInputChange.bind(this)}
               ref={this.setInputSearchRef}
             />
           );
         }
       }
       ```

    You can also use _refs_ in function components using `closures`.
    `Note`: You can also use inline ref callbacks even though it is not a recommended approach.

7.  ### What are forward refs?

    _Ref forwarding_ is a feature that lets some components take a _ref_ they receive, and pass it further down to a child.

    ```javascript
    const ButtonElement = React.forwardRef((props, ref) => (
      <button ref={ref} className="CustomButton">
        {props.children}
      </button>
    ));

    // Create ref to the DOM button:
    const ref = React.createRef();
    <ButtonElement ref={ref}>{"Forward Ref"}</ButtonElement>;
    ```

8.  ### Which is preferred option with in callback refs and findDOMNode()?

    It is preferred to use _callback refs_ over `findDOMNode()` API. Because `findDOMNode()` prevents certain improvements in React in the future.

    The `legacy` approach of using `findDOMNode`:

    ```javascript
    class MyComponent extends Component {
      componentDidMount() {
        findDOMNode(this).scrollIntoView();
      }

      render() {
        return <div />;
      }
    }
    ```

    The recommended approach is:

    ```javascript
    class MyComponent extends Component {
      constructor(props) {
        super(props);
        this.node = createRef();
      }
      componentDidMount() {
        this.node.current.scrollIntoView();
      }

      render() {
        return <div ref={this.node} />;
      }
    }
    ```

9.  ### Why are String Refs legacy?

    If you worked with React before, you might be familiar with an older API where the `ref` attribute is a string, like `ref={'textInput'}`, and the DOM node is accessed as `this.refs.textInput`. We advise against it because _string refs have below issues_, and are considered legacy. String refs were `removed in React v16`.

    1. They _force React to keep track of currently executing component_. This is problematic because it makes react module stateful, and thus causes weird errors when react module is duplicated in the bundle.
    2. They are _not composable_ — if a library puts a ref on the passed child, the user can't put another ref on it. Callback refs are perfectly composable.
    3. They _don't work with static analysis_ like Flow. Flow can't guess the magic that framework does to make the string ref appear on `this.refs`, as well as its type (which could be different). Callback refs are friendlier to static analysis.
    4. It doesn't work as most people would expect with the "render callback" pattern (e.g. <DataGrid renderRow={this.renderRow} />)

       ```javascript
       class MyComponent extends Component {
         renderRow = (index) => {
           // This won't work. Ref will get attached to DataTable rather than MyComponent:
           return <input ref={"input-" + index} />;

           // This would work though! Callback refs are awesome.
           return <input ref={(input) => (this["input-" + index] = input)} />;
         };

         render() {
           return (
             <DataTable data={this.props.data} renderRow={this.renderRow} />
           );
         }
       }
       ```

10. ### What are the different phases of component lifecycle?

    The component lifecycle has three distinct lifecycle phases:

    1. `Mounting:` The component is ready to mount in the browser DOM. This phase covers initialization from `constructor()`, `getDerivedStateFromProps()`, `render()`, and `componentDidMount()` lifecycle methods.

    2. `Updating:` In this phase, the component gets updated in two ways, sending the new props and updating the state either from `setState()` or `forceUpdate()`. This phase covers `getDerivedStateFromProps()`, `shouldComponentUpdate()`, `render()`, `getSnapshotBeforeUpdate()` and `componentDidUpdate()` lifecycle methods.

    3. `Unmounting:` In this last phase, the component is not needed and gets unmounted from the browser DOM. This phase includes `componentWillUnmount()` lifecycle method.

    It's worth mentioning that React internally has a concept of phases when applying changes to the DOM. They are separated as follows

    4. `Render` The component will render without any side effects. This applies to Pure components and in this phase, React can pause, abort, or restart the render.

    5. `Pre-commit` Before the component actually applies the changes to the DOM, there is a moment that allows React to read from the DOM through the `getSnapshotBeforeUpdate()`.

    6. `Commit` React works with the DOM and executes the final lifecycles respectively `componentDidMount()` for mounting, `componentDidUpdate()` for updating, and `componentWillUnmount()` for unmounting.

    React 16.3+ Phases (or an [interactive version](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/))

    ![phases 16.4+](images/phases16.4.png)

    Before React 16.3

    ![phases 16.2](images/phases.png)

11. ### What are the lifecycle methods of React?

    Before React 16.3

    - `componentWillMount:` Executed before rendering and is used for App level configuration in your root component.
    - `componentDidMount:` Executed after first rendering and here all AJAX requests, DOM or state updates, and set up event listeners should occur.
    - `componentWillReceiveProps:` Executed when particular prop updates to trigger state transitions.
    - `shouldComponentUpdate:` Determines if the component will be updated or not. By default it returns `true`. If you are sure that the component doesn't need to render after state or props are updated, you can return false value. It is a great place to improve performance as it allows you to prevent a re-render if component receives new prop.
    - `componentWillUpdate:` Executed before re-rendering the component when there are props & state changes confirmed by `shouldComponentUpdate()` which returns true.
    - `componentDidUpdate:` Mostly it is used to update the DOM in response to prop or state changes.
    - `componentWillUnmount:` It will be used to cancel any outgoing network requests, or remove all event listeners associated with the component.

    React 16.3+

    - `getDerivedStateFromProps:` Invoked right before calling `render()` and is invoked on _every_ render. This exists for rare use cases where you need a derived state. Worth reading [if you need derived state](https://reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html).
    - `componentDidMount:` Executed after first rendering and where all AJAX requests, DOM or state updates, and set up event listeners should occur.
    - `shouldComponentUpdate:` Determines if the component will be updated or not. By default, it returns `true`. If you are sure that the component doesn't need to render after the state or props are updated, you can return a false value. It is a great place to improve performance as it allows you to prevent a re-render if component receives a new prop.
    - `getSnapshotBeforeUpdate:` Executed right before rendered output is committed to the DOM. Any value returned by this will be passed into `componentDidUpdate()`. This is useful to capture information from the DOM i.e. scroll position.
    - `componentDidUpdate:` Mostly it is used to update the DOM in response to prop or state changes. This will not fire if `shouldComponentUpdate()` returns `false`.
    - `componentWillUnmount` It will be used to cancel any outgoing network requests, or remove all event listeners associated with the component.

12. ### How to create props proxy for HOC component?

    You can add/edit props passed to the component using _props proxy_ pattern like this:

    ```javascript
    function HOC(WrappedComponent) {
      return class Test extends Component {
        render() {
          const newProps = {
            title: "New Header",
            footer: false,
            showFeatureX: false,
            showFeatureY: true,
          };

          return <WrappedComponent {...this.props} {...newProps} />;
        }
      };
    }
    ```

13. ### What is context?

    _Context_ provides a way to pass data through the component tree without having to pass props down manually at every level.

    For example, authenticated users, locale preferences, UI themes need to be accessed in the application by many components.

    ```javascript
    const { Provider, Consumer } = React.createContext(defaultValue);
    ```

14. ### What is the purpose of using super constructor with props argument?

    A child class constructor cannot make use of `this` reference until the `super()` method has been called. The same applies to ES6 sub-classes as well. The main reason for passing props parameter to `super()` call is to access `this.props` in your child constructors.

    `Passing props:`

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);

        console.log(this.props); // prints { name: 'John', age: 42 }
      }
    }
    ```

    `Not passing props:`

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super();

        console.log(this.props); // prints undefined

        // but props parameter is still available
        console.log(props); // prints { name: 'John', age: 42 }
      }

      render() {
        // no difference outside constructor
        console.log(this.props); // prints { name: 'John', age: 42 }
      }
    }
    ```

    The above code snippets reveals that `this.props` is different only within the constructor. It would be the same outside the constructor.

15. ### How to set state with a dynamic key name?

    If you are using ES6 or the Babel transpiler to transform your JSX code then you can accomplish this with _computed property names_.

    ```javascript
    handleInputChange(event) {
      this.setState({ [event.target.id]: event.target.value })
    }
    ```

16. ### What would be the common mistake of function being called every time the component renders?

    You need to make sure that function is not being called while passing the function as a parameter.

    ```javascript
    render() {
      // Wrong: handleClick is called instead of passed as a reference!
      return <button onClick={this.handleClick()}>{'Click Me'}</button>
    }
    ```

    Instead, pass the function itself without parenthesis:

    ```javascript
    render() {
      // Correct: handleClick is passed as a reference!
      return <button onClick={this.handleClick}>{'Click Me'}</button>
    }
    ```

17. ### What are error boundaries in React v16?

    _Error boundaries_ are components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed.

    A class component becomes an error boundary if it defines a new lifecycle method called `componentDidCatch(error, info)` or `static getDerivedStateFromError() `:

    ```javascript
    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = { hasError: false };
      }

      componentDidCatch(error, info) {
        // You can also log the error to an error reporting service
        logErrorToMyService(error, info);
      }

      static getDerivedStateFromError(error) {
        // Update state so the next render will show the fallback UI.
        return { hasError: true };
      }

      render() {
        if (this.state.hasError) {
          // You can render any custom fallback UI
          return <h1>{"Something went wrong."}</h1>;
        }
        return this.props.children;
      }
    }
    ```

    After that use it as a regular component:

    ```javascript
    <ErrorBoundary>
      <MyWidget />
    </ErrorBoundary>
    ```

18. ### How are error boundaries handled in React v15?

    React v15 provided very basic support for _error boundaries_ using `unstable_handleError` method. It has been renamed to `componentDidCatch` in React v16.

19. ### What is the purpose of render method of `react-dom`?

    This method is used to render a React element into the DOM in the supplied container and return a reference to the component. If the React element was previously rendered into container, it will perform an update on it and only mutate the DOM as necessary to reflect the latest changes.

    ```
    ReactDOM.render(element, container, [callback])
    ```

    If the optional callback is provided, it will be executed after the component is rendered or updated.

20. ### What will happen if you use `setState()` in constructor?

    When you use `setState()`, then apart from assigning to the object state React also re-renders the component and all its children. You would get error like this: _Can only update a mounted or mounting component._ So we need to use `this.state` to initialize variables inside constructor.

21. ### Is it good to use `setState()` in `componentWillMount()` method?

    Yes, it is safe to use `setState()` inside `componentWillMount()` method. But at the same it is recommended to avoid async initialization in `componentWillMount()` lifecycle method. `componentWillMount()` is invoked immediately before mounting occurs. It is called before `render()`, therefore setting state in this method will not trigger a re-render. Avoid introducing any side-effects or subscriptions in this method. We need to make sure async calls for component initialization happened in `componentDidMount()` instead of `componentWillMount()`.

    ```javascript
    componentDidMount() {
      axios.get(`api/todos`)
        .then((result) => {
          this.setState({
            messages: [...result.data]
          })
        })
    }
    ```

22. ### What will happen if you use props in initial state?

    If the props on the component are changed without the component being refreshed, the new prop value will never be displayed because the constructor function will never update the current state of the component. The initialization of state from props only runs when the component is first created.

    The below component won't display the updated input value:

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);

        this.state = {
          records: [],
          inputValue: this.props.inputValue,
        };
      }

      render() {
        return <div>{this.state.inputValue}</div>;
      }
    }
    ```

    Using props inside render method will update the value:

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);

        this.state = {
          record: [],
        };
      }

      render() {
        return <div>{this.props.inputValue}</div>;
      }
    }
    ```

23. ### How you use decorators in React?

    You can _decorate_ your _class_ components, which is the same as passing the component into a function. `Decorators` are flexible and readable way of modifying component functionality.

    ```javascript
    @setTitle("Profile")
    class Profile extends React.Component {
      //....
    }

    /*
      title is a string that will be set as a document title
      WrappedComponent is what our decorator will receive when
      put directly above a component class as seen in the example above
    */
    const setTitle = (title) => (WrappedComponent) => {
      return class extends React.Component {
        componentDidMount() {
          document.title = title;
        }

        render() {
          return <WrappedComponent {...this.props} />;
        }
      };
    };
    ```

    `Note:` Decorators are a feature that didn't make it into ES7, but are currently a _stage 2 proposal_.

24. ### What is CRA and its benefits?

    The `create-react-app` CLI tool allows you to quickly create & run React applications with no configuration step.

    Let's create Todo App using _CRA_:

    ```console
    # Installation
    $ npm install -g create-react-app

    # Create new project
    $ create-react-app todo-app
    $ cd todo-app

    # Build, test and run
    $ npm run build
    $ npm run test
    $ npm start
    ```

    It includes everything we need to build a React app:

    1. React, JSX, ES6, and Flow syntax support.
    2. Language extras beyond ES6 like the object spread operator.
    3. Autoprefixed CSS, so you don’t need -webkit- or other prefixes.
    4. A fast interactive unit test runner with built-in support for coverage reporting.
    5. A live development server that warns about common mistakes.
    6. A build script to bundle JS, CSS, and images for production, with hashes and sourcemaps.

25. ### What is the lifecycle methods order in mounting?

    The lifecycle methods are called in the following order when an instance of a component is being created and inserted into the DOM.

    1. `constructor()`
    2. `static getDerivedStateFromProps()`
    3. `render()`
    4. `componentDidMount()`

26. ### What are the lifecycle methods going to be deprecated in React v16?

    The following lifecycle methods going to be unsafe coding practices and will be more problematic with async rendering.

    1. `componentWillMount()`
    2. `componentWillReceiveProps()`
    3. `componentWillUpdate()`

    Starting with React v16.3 these methods are aliased with `UNSAFE_` prefix, and the unprefixed version will be removed in React v17.

27. ### What is the purpose of `getDerivedStateFromProps()` lifecycle method?

    The new static `getDerivedStateFromProps()` lifecycle method is invoked after a component is instantiated as well as before it is re-rendered. It can return an object to update state, or `null` to indicate that the new props do not require any state updates.

    ```javascript
    class MyComponent extends React.Component {
      static getDerivedStateFromProps(props, state) {
        // ...
      }
    }
    ```

    This lifecycle method along with `componentDidUpdate()` covers all the use cases of `componentWillReceiveProps()`.

28. ### What is the purpose of `getSnapshotBeforeUpdate()` lifecycle method?

    The new `getSnapshotBeforeUpdate()` lifecycle method is called right before DOM updates. The return value from this method will be passed as the third parameter to `componentDidUpdate()`.

    ```javascript
    class MyComponent extends React.Component {
      getSnapshotBeforeUpdate(prevProps, prevState) {
        // ...
      }
    }
    ```

    This lifecycle method along with `componentDidUpdate()` covers all the use cases of `componentWillUpdate()`.

29. ### What is the recommended way for naming components?

    It is recommended to name the component by reference instead of using `displayName`.

    Using `displayName` for naming component:

    ```javascript
    export default React.createClass({
      displayName: "TodoApp",
      // ...
    });
    ```

    The `recommended` approach:

    ```javascript
    export default class TodoApp extends React.Component {
      // ...
    }
    ```

    also

    ```javascript
    const TodoApp = () => {
      //...
    };
    export default TodoApp;
    ```

30. ### What is the recommended ordering of methods in component class?

    _Recommended_ ordering of methods from _mounting_ to _render stage_:

    1. `static` methods
    2. `constructor()`
    3. `getChildContext()`
    4. `componentWillMount()`
    5. `componentDidMount()`
    6. `componentWillReceiveProps()`
    7. `shouldComponentUpdate()`
    8. `componentWillUpdate()`
    9. `componentDidUpdate()`
    10. `componentWillUnmount()`
    11. click handlers or event handlers like `onClickSubmit()` or `onChangeDescription()`
    12. getter methods for render like `getSelectReason()` or `getFooterContent()`
    13. optional render methods like `renderNavigation()` or `renderProfilePicture()`
    14. `render()`

31. ### Why we need to pass a function to setState()?

    The reason behind for this is that `setState()` is an asynchronous operation. React batches state changes for performance reasons, so the state may not change immediately after `setState()` is called. That means you should not rely on the current state when calling `setState()` since you can't be sure what that state will be. The solution is to pass a function to `setState()`, with the previous state as an argument. By doing this you can avoid issues with the user getting the old state value on access due to the asynchronous nature of `setState()`.

    Let's say the initial count value is zero. After three consecutive increment operations, the value is going to be incremented only by one.

    ```javascript
    // assuming this.state.count === 0
    this.setState({ count: this.state.count + 1 });
    this.setState({ count: this.state.count + 1 });
    this.setState({ count: this.state.count + 1 });
    // this.state.count === 1, not 3
    ```

    If we pass a function to `setState()`, the count gets incremented correctly.

    ```javascript
    this.setState((prevState, props) => ({
      count: prevState.count + props.increment,
    }));
    // this.state.count === 3 as expected
    ```

    `(OR)`

    ### Why function is preferred over object for `setState()`?

    React may batch multiple `setState()` calls into a single update for performance. Because `this.props` and `this.state` may be updated asynchronously, you should not rely on their values for calculating the next state.

    This counter example will fail to update as expected:

    ```javascript
    // Wrong
    this.setState({
      counter: this.state.counter + this.props.increment,
    });
    ```

    The preferred approach is to call `setState()` with function rather than object. That function will receive the previous state as the first argument, and the props at the time the update is applied as the second argument.

    ```javascript
    // Correct
    this.setState((prevState, props) => ({
      counter: prevState.counter + props.increment,
    }));
    ```

32. ### Why is `isMounted()` an anti-pattern and what is the proper solution?

    The primary use case for `isMounted()` is to avoid calling `setState()` after a component has been unmounted, because it will emit a warning.

    ```javascript
    if (this.isMounted()) {
      this.setState({...})
    }
    ```

    Checking `isMounted()` before calling `setState()` does eliminate the warning, but it also defeats the purpose of the warning. Using `isMounted()` is a code smell because the only reason you would check is because you think you might be holding a reference after the component has unmounted.

    An optimal solution would be to find places where `setState()` might be called after a component has unmounted, and fix them. Such situations most commonly occur due to callbacks, when a component is waiting for some data and gets unmounted before the data arrives. Ideally, any callbacks should be canceled in `componentWillUnmount()`, prior to unmounting.

33. ### What is the difference between constructor and getInitialState?

    You should initialize state in the constructor when using ES6 classes, and `getInitialState()` method when using `React.createClass()`.

    `Using ES6 classes:`

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.state = {
          /* initial state */
        };
      }
    }
    ```

    `Using `React.createClass()`:`

    ```javascript
    const MyComponent = React.createClass({
      getInitialState() {
        return {
          /* initial state */
        };
      },
    });
    ```

    `Note:` `React.createClass()` is deprecated and removed in React v16. Use plain JavaScript classes instead.

34. ### Can you force a component to re-render without calling setState?

    By default, when your component's state or props change, your component will re-render. If your `render()` method depends on some other data, you can tell React that the component needs re-rendering by calling `forceUpdate()`.

    ```javascript
    component.forceUpdate(callback);
    ```

    It is recommended to avoid all uses of `forceUpdate()` and only read from `this.props` and `this.state` in `render()`.

35. ### What is the difference between `super()` and `super(props)` in React using ES6 classes?

    When you want to access `this.props` in `constructor()` then you should pass props to `super()` method.

    `Using `super(props)`:`

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        console.log(this.props); // { name: 'John', ... }
      }
    }
    ```

    `Using `super()`:`

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super();
        console.log(this.props); // undefined
      }
    }
    ```

    Outside `constructor()` both will display same value for `this.props`.

36. ### What is the difference between `setState()` and `replaceState()` methods?

    When you use `setState()` the current and previous states are merged. `replaceState()` throws out the current state, and replaces it with only what you provide. Usually `setState()` is used unless you really need to remove all previous keys for some reason. You can also set state to `false`/`null` in `setState()` instead of using `replaceState()`.

37. ### How to listen to state changes?

    The `componentDidUpdate` lifecycle method will be called when state changes. You can compare provided state and props values with current state and props to determine if something meaningful changed.

    ```
    componentDidUpdate(object prevProps, object prevState)
    ```

    `Note:` The previous releases of ReactJS also uses `componentWillUpdate(object nextProps, object nextState)` for state changes. It has been deprecated in latest releases.

38. ### What is the recommended approach of removing an array element in React state?

    The better approach is to use `Array.prototype.filter()` method.

    For example, let's create a `removeItem()` method for updating the state.

    ```javascript
    removeItem(index) {
      this.setState({
        data: this.state.data.filter((item, i) => i !== index)
      })
    }
    ```

39. ### Is it possible to use React without rendering HTML?

    It is possible. Below are the possible options:

    ```javascript
    render() {
      return false
    }
    ```

    ```javascript
    render() {
      return true
    }
    ```

    ```javascript
    render() {
      return null
    }
    ```

    React version >=16.0.0:

    ```javascript
    render() {
      return []
    }
    ```

    ```javascript
    render() {
      return ""
    }
    ```

    React version >=16.2.0:

    ```javascript
    render() {
      return <React.Fragment></React.Fragment>
    }
    ```

    ```javascript
    render() {
      return <></>
    }
    ```

    React version >=18.0.0:

    ```javascript
    render() {
      return undefined
    }
    ```

40. ### What are the possible ways of updating objects in state?

    1. `Calling `setState()` with an object to merge with state:`

       - Using `Object.assign()` to create a copy of the object:

         ```javascript
         const user = Object.assign({}, this.state.user, { age: 42 });
         this.setState({ user });
         ```

       - Using _spread operator_:

         ```javascript
         const user = { ...this.state.user, age: 42 };
         this.setState({ user });
         ```

    2. `Calling `setState()` with a function:`

       ```javascript
       this.setState((prevState) => ({
         user: {
           ...prevState.user,
           age: 42,
         },
       }));
       ```

41. ### What are the approaches to include polyfills in your `create-react-app`?

    There are approaches to include polyfills in create-react-app,

    1. `Manual import from `core-js`:`

       Create a file called (something like) `polyfills.js` and import it into root `index.js` file. Run `npm install core-js` or `yarn add core-js` and import your specific required features.

       ```javascript
       import "core-js/fn/array/find";
       import "core-js/fn/array/includes";
       import "core-js/fn/number/is-nan";
       ```

    2. `Using Polyfill service:`

       Use the polyfill.io CDN to retrieve custom, browser-specific polyfills by adding this line to `index.html`:

       ```html
       <script src="https://cdn.polyfill.io/v2/polyfill.min.js?features=default,Array.prototype.includes"></script>
       ```

       In the above script we had to explicitly request the `Array.prototype.includes` feature as it is not included in the default feature set.

42. ### How to use https instead of http in create-react-app?

    You just need to use `HTTPS=true` configuration. You can edit your `package.json` scripts section:

    ```json
    "scripts": {
      "start": "set HTTPS=true && react-scripts start"
    }
    ```

    or just run `set HTTPS=true && npm start`

43. ### How to avoid using relative path imports in create-react-app?

    Create a file called `.env` in the project root and write the import path:

    ```
    NODE_PATH=src/app
    ```

    After that restart the development server. Now you should be able to import anything inside `src/app` without relative paths.

44. ### How to update a component every second?

    You need to use `setInterval()` to trigger the change, but you also need to clear the timer when the component unmounts to prevent errors and memory leaks.

    ```javascript
    componentDidMount() {
      this.interval = setInterval(() => this.setState({ time: Date.now() }), 1000)
    }

    componentWillUnmount() {
      clearInterval(this.interval)
    }
    ```

45. ### Why is a component constructor called only once?

    React's _reconciliation_ algorithm assumes that without any information to the contrary, if a custom component appears in the same place on subsequent renders, it's the same component as before, so reuses the previous instance rather than creating a new one.

46. ### How to define constants in React?

    You can use ES7 `static` field to define constant.

    ```javascript
    class MyComponent extends React.Component {
      static DEFAULT_PAGINATION = 10;
    }
    ```

47. ### How to programmatically trigger click event in React?

    You could use the ref prop to acquire a reference to the underlying `HTMLInputElement` object through a callback, store the reference as a class property, then use that reference to later trigger a click from your event handlers using the `HTMLElement.click` method.

    This can be done in two steps:

    1. Create ref in render method:

       ```javascript
       <input ref={(input) => (this.inputElement = input)} />
       ```

    2. Apply click event in your event handler:

       ```javascript
       this.inputElement.click();
       ```

48. ### How to make AJAX call and in which component lifecycle methods should I make an AJAX call?

    You can use AJAX libraries such as Axios, jQuery AJAX, and the browser built-in `fetch`. You should fetch data in the `componentDidMount()` lifecycle method. This is so you can use `setState()` to update your component when the data is retrieved.

    For example, the employees list fetched from API and set local state:

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.state = {
          employees: [],
          error: null,
        };
      }

      componentDidMount() {
        fetch("https://api.example.com/items")
          .then((res) => res.json())
          .then(
            (result) => {
              this.setState({
                employees: result.employees,
              });
            },
            (error) => {
              this.setState({ error });
            }
          );
      }

      render() {
        const { error, employees } = this.state;
        if (error) {
          return <div>Error: {error.message}</div>;
        } else {
          return (
            <ul>
              {employees.map((employee) => (
                <li key={employee.name}>
                  {employee.name}-{employee.experience}
                </li>
              ))}
            </ul>
          );
        }
      }
    }
    ```

49. ### What are render props?

    `Render Props` is a simple technique for sharing code between components using a prop whose value is a function. The below component uses render prop which returns a React element.

    ```javascript
    <DataProvider render={(data) => <h1>{`Hello ${data.target}`}</h1>} />
    ```

    Libraries such as React Router and DownShift are using this pattern.

50. ### How to dispatch an action on load?

    You can dispatch an action in `componentDidMount()` method and in `render()` method you can verify the data.

    ```javascript
    class App extends Component {
      componentDidMount() {
        this.props.fetchData();
      }

      render() {
        return this.props.isLoaded ? (
          <div>{"Loaded"}</div>
        ) : (
          <div>{"Not Loaded"}</div>
        );
      }
    }

    const mapStateToProps = (state) => ({
      isLoaded: state.isLoaded,
    });

    const mapDispatchToProps = { fetchData };

    export default connect(mapStateToProps, mapDispatchToProps)(App);
    ```

51. ### How to use `connect()` from React Redux?

    You need to follow two steps to use your store in your container:

    1. `Use `mapStateToProps()`:` It maps the state variables from your store to the props that you specify.
    2. `Connect the above props to your container:` The object returned by the `mapStateToProps` function is connected to the container. You can import `connect()` from `react-redux`.

       ```javascript
       import React from "react";
       import { connect } from "react-redux";

       class App extends React.Component {
         render() {
           return <div>{this.props.containerData}</div>;
         }
       }

       function mapStateToProps(state) {
         return { containerData: state.data };
       }

       export default connect(mapStateToProps)(App);
       ```

52. ### Whats the purpose of `at` symbol in the Redux connect decorator?

    The `@` symbol is in fact a JavaScript expression used to signify decorators. _Decorators_ make it possible to annotate and modify classes and properties at design time.

    Let's take an example setting up Redux without and with a decorator.

    - `Without decorator:`

      ```javascript
      import React from "react";
      import * as actionCreators from "./actionCreators";
      import { bindActionCreators } from "redux";
      import { connect } from "react-redux";

      function mapStateToProps(state) {
        return { todos: state.todos };
      }

      function mapDispatchToProps(dispatch) {
        return { actions: bindActionCreators(actionCreators, dispatch) };
      }

      class MyApp extends React.Component {
        // ...define your main app here
      }

      export default connect(mapStateToProps, mapDispatchToProps)(MyApp);
      ```

    - `With decorator:`

      ```javascript
      import React from "react";
      import * as actionCreators from "./actionCreators";
      import { bindActionCreators } from "redux";
      import { connect } from "react-redux";

      function mapStateToProps(state) {
        return { todos: state.todos };
      }

      function mapDispatchToProps(dispatch) {
        return { actions: bindActionCreators(actionCreators, dispatch) };
      }

      @connect(mapStateToProps, mapDispatchToProps)
      export default class MyApp extends React.Component {
        // ...define your main app here
      }
      ```

    The above examples are almost similar except the usage of decorator. The decorator syntax isn't built into any JavaScript runtimes yet, and is still experimental and subject to change. You can use babel for the decorators support.

53. ### How to use TypeScript in `create-react-app` application?

        Starting from react-scripts@3.3.0+ releases onwards, you can now optionally start a new app from a template by appending `--template [template-name]` to the creation command. If you don't select a template, it will create your project with base template. Remember that templates are always named in the format `cra-template-[template-name]`, here you only need to fill the `[template-name]` section.

        The typeScript can be used in your project by appending `--template typescript` to the creation command.

         ```bash
         npx create-react-app my-app --template typescript
         ```

        But if you are using React Scripting between react-scripts@2.1.0 and react-scripts@3.2.x , there is a built-in support for TypeScript. i.e, `create-react-app` now supports TypeScript natively. You can just pass `--typescript` option as below

         ```bash
         npx create-react-app my-app --typescript

         # or

         yarn create react-app my-app --typescript
         ```

         Whereas for lower versions of react scripts, just supply `--scripts-version` option as `react-scripts-ts` while you create a new project. `react-scripts-ts` is a set of adjustments to take the standard `create-react-app` project pipeline and bring TypeScript into the mix.

         Now the project layout should look like the following:

         ```
         my-app/
         ├─ .gitignore
         ├─ images.d.ts
         ├─ node_modules/
         ├─ public/
         ├─ src/
         │  └─ ...
         ├─ package.json
         ├─ tsconfig.json
         ├─ tsconfig.prod.json
         ├─ tsconfig.test.json
         └─ tslint.json
         ```

54. ### Does the statics object work with ES6 classes in React?

    No, `statics` only works with `React.createClass()`:

    ```javascript
    someComponent = React.createClass({
      statics: {
        someMethod: function () {
          // ..
        },
      },
    });
    ```

    But you can write statics inside ES6+ classes as below,

    ```javascript
    class Component extends React.Component {
      static propTypes = {
        // ...
      };

      static someMethod() {
        // ...
      }
    }
    ```

    or writing them outside class as below,

    ```javascript
    class Component extends React.Component {
       ....
    }

    Component.propTypes = {...}
    Component.someMethod = function(){....}
    ```

55. ### Why are inline ref callbacks or functions not recommended?

    If the ref callback is defined as an inline function, it will get called twice during updates, first with null and then again with the DOM element. This is because a new instance of the function is created with each render, so React needs to clear the old ref and set up the new one.

    ```jsx
    class UserForm extends Component {
      handleSubmit = () => {
        console.log("Input Value is: ", this.input.value);
      };

      render() {
        return (
          <form onSubmit={this.handleSubmit}>
            <input type="text" ref={(input) => (this.input = input)} /> //
            Access DOM input in handle submit
            <button type="submit">Submit</button>
          </form>
        );
      }
    }
    ```

    But our expectation is for the ref callback to get called once, when the component mounts. One quick fix is to use the ES7 class property syntax to define the function

    ```jsx
    class UserForm extends Component {
      handleSubmit = () => {
        console.log("Input Value is: ", this.input.value);
      };

      setSearchInput = (input) => {
        this.input = input;
      };

      render() {
        return (
          <form onSubmit={this.handleSubmit}>
            <input type="text" ref={this.setSearchInput} /> // Access DOM input
            in handle submit
            <button type="submit">Submit</button>
          </form>
        );
      }
    }
    ```

56. ### What are HOC factory implementations?

    There are two main ways of implementing HOCs in React.

    1. Props Proxy (PP) and
    2. Inheritance Inversion (II).

    But they follow different approaches for manipulating the _WrappedComponent_.

    `Props Proxy`

    In this approach, the render method of the HOC returns a React Element of the type of the WrappedComponent. We also pass through the props that the HOC receives, hence the name `Props Proxy`.

    ```jsx
    function ppHOC(WrappedComponent) {
      return class PP extends React.Component {
        render() {
          return <WrappedComponent {...this.props} />;
        }
      };
    }
    ```

    `Inheritance Inversion`

    In this approach, the returned HOC class (Enhancer) extends the WrappedComponent. It is called Inheritance Inversion because instead of the WrappedComponent extending some Enhancer class, it is passively extended by the Enhancer. In this way the relationship between them seems `inverse`.

    ```jsx
    function iiHOC(WrappedComponent) {
      return class Enhancer extends WrappedComponent {
        render() {
          return super.render();
        }
      };
    }
    ```

57. ### How to use class field declarations syntax in React classes?

    React Class Components can be made much more concise using the class field declarations. You can initialize the local state without using the constructor and declare class methods by using arrow functions without the extra need to bind them.

    Let's take a counter example to demonstrate class field declarations for state without using constructor and methods without binding,

    ```jsx
    class Counter extends Component {
      state = { value: 0 };

      handleIncrement = () => {
        this.setState((prevState) => ({
          value: prevState.value + 1,
        }));
      };

      handleDecrement = () => {
        this.setState((prevState) => ({
          value: prevState.value - 1,
        }));
      };

      render() {
        return (
          <div>
            {this.state.value}

            <button onClick={this.handleIncrement}>+</button>
            <button onClick={this.handleDecrement}>-</button>
          </div>
        );
      }
    }
    ```

58. ### Why do you not need error boundaries for event handlers?

    Error boundaries do not catch errors inside event handlers.

    React doesn’t need error boundaries to recover from errors in event handlers. Unlike the render method and lifecycle methods, the event handlers don’t happen during rendering. So if they throw, React still knows what to display on the screen.

    If you need to catch an error inside an event handler, use the regular JavaScript try / catch statement:

    ```javascript
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.state = { error: null };
        this.handleClick = this.handleClick.bind(this);
      }

      handleClick() {
        try {
          // Do something that could throw
        } catch (error) {
          this.setState({ error });
        }
      }

      render() {
        if (this.state.error) {
          return <h1>Caught an error.</h1>;
        }
        return <button onClick={this.handleClick}>Click Me</button>;
      }
    }
    ```

    Note that the above example is demonstrating regular JavaScript behavior and doesn’t use error boundaries.

59. ### What is the difference between try catch block and error boundaries?

    Try catch block works with imperative code whereas error boundaries are meant for declarative code to render on the screen.

    For example, the try catch block used for below imperative code

    ```javascript
    try {
      showButton();
    } catch (error) {
      // ...
    }
    ```

    Whereas error boundaries wrap declarative code as below,

    ```javascript
    <ErrorBoundary>
      <MyComponent />
    </ErrorBoundary>
    ```

    So if an error occurs in a `componentDidUpdate` method caused by a `setState` somewhere deep in the tree, it will still correctly propagate to the closest error boundary.

60. ### What is the required method to be defined for a class component?

    The `render()` method is the only required method in a class component. i.e, All methods other than render method are optional for a class component.

61. ### What are the possible return types of render method?

    Below are the list of following types used and return from render method,

    1. `React elements:` Elements that instruct React to render a DOM node. It includes html elements such as `<div/>` and user defined elements.
    2. `Arrays and fragments:` Return multiple elements to render as Arrays and Fragments to wrap multiple elements
    3. `Portals:` Render children into a different DOM subtree.
    4. `String and numbers:` Render both Strings and Numbers as text nodes in the DOM
    5. `Booleans or null:` Doesn't render anything but these types are used to conditionally render content.

62. ### What is the main purpose of constructor?

    The constructor is mainly used for two purposes,

    1. To initialize local state by assigning object to this.state
    2. For binding event handler methods to the instance
       For example, the below code covers both the above cases,

    ```javascript
    constructor(props) {
      super(props);
      // Don't call this.setState() here!
      this.state = { counter: 0 };
      this.handleClick = this.handleClick.bind(this);
    }
    ```

63. ### Is it mandatory to define constructor for React component?

    No, it is not mandatory. i.e, If you don’t initialize state and you don’t bind methods, you don’t need to implement a constructor for your React component.

64. ### Why should not call setState in componentWillUnmount?

    You should not call `setState()` in `componentWillUnmount()` because once a component instance is unmounted, it will never be mounted again.

65. ### What is the purpose of getDerivedStateFromError?

    This lifecycle method is invoked after an error has been thrown by a descendant component. It receives the error that was thrown as a parameter and should return a value to update state.

    The signature of the lifecycle method is as follows,

    ```javascript
    static getDerivedStateFromError(error)
    ```

    Let us take error boundary use case with the above lifecycle method for demonstration purpose,

    ```javascript
    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = { hasError: false };
      }

      static getDerivedStateFromError(error) {
        // Update state so the next render will show the fallback UI.
        return { hasError: true };
      }

      render() {
        if (this.state.hasError) {
          // You can render any custom fallback UI
          return <h1>Something went wrong.</h1>;
        }

        return this.props.children;
      }
    }
    ```

66. ### What is the methods order when component re-rendered?

    An update can be caused by changes to props or state. The below methods are called in the following order when a component is being re-rendered.

    1. static getDerivedStateFromProps()
    2. shouldComponentUpdate()
    3. render()
    4. getSnapshotBeforeUpdate()
    5. componentDidUpdate()

67. ### What are the methods invoked during error handling?

    Below methods are called when there is an error during rendering, in a lifecycle method, or in the constructor of any child component.

    1. static getDerivedStateFromError()
    2. componentDidCatch()

68. ### What is the purpose of unmountComponentAtNode method?

    This method is available from react-dom package and it removes a mounted React component from the DOM and clean up its event handlers and state. If no component was mounted in the container, calling this function does nothing. Returns true if a component was unmounted and false if there was no component to unmount.

    The method signature would be as follows,

    ```javascript
    ReactDOM.unmountComponentAtNode(container);
    ```

69. ### What are the limitations with HOCs?

    Higher-order components come with a few caveats apart from its benefits. Below are the few listed in an order,

    1. `Don’t use HOCs inside the render method:`
       It is not recommended to apply a HOC to a component within the render method of a component.

       ```javascript
       render() {
         // A new version of EnhancedComponent is created on every render
         // EnhancedComponent1 !== EnhancedComponent2
         const EnhancedComponent = enhance(MyComponent);
         // That causes the entire subtree to unmount/remount each time!
         return <EnhancedComponent />;
       }
       ```

       The above code impacts on performance by remounting a component that causes the state of that component and all of its children to be lost. Instead, apply HOCs outside the component definition so that the resulting component is created only once.

    2. `Static methods must be copied over:`
       When you apply a HOC to a component the new component does not have any of the static methods of the original component

       ```javascript
       // Define a static method
       WrappedComponent.staticMethod = function () {
         /*...*/
       };
       // Now apply a HOC
       const EnhancedComponent = enhance(WrappedComponent);

       // The enhanced component has no static method
       typeof EnhancedComponent.staticMethod === "undefined"; // true
       ```

       You can overcome this by copying the methods onto the container before returning it,

       ```javascript
       function enhance(WrappedComponent) {
         class Enhance extends React.Component {
           /*...*/
         }
         // Must know exactly which method(s) to copy :(
         Enhance.staticMethod = WrappedComponent.staticMethod;
         return Enhance;
       }
       ```

    3. `Refs aren’t passed through:`
       For HOCs you need to pass through all props to the wrapped component but this does not work for refs. This is because ref is not really a prop similar to key. In this case you need to use the React.forwardRef API

70. ### How to debug forwardRefs in DevTools?

    `React.forwardRef` accepts a render function as parameter and DevTools uses this function to determine what to display for the ref forwarding component.

    For example, If you don't name the render function or not using displayName property then it will appear as ”ForwardRef” in the DevTools,

    ```javascript
    const WrappedComponent = React.forwardRef((props, ref) => {
      return <LogProps {...props} forwardedRef={ref} />;
    });
    ```

    But If you name the render function then it will appear as `”ForwardRef(myFunction)”`

    ```javascript
    const WrappedComponent = React.forwardRef(function myFunction(props, ref) {
      return <LogProps {...props} forwardedRef={ref} />;
    });
    ```

    As an alternative, You can also set displayName property for forwardRef function,

    ```javascript
    function logProps(Component) {
      class LogProps extends React.Component {
        // ...
      }

      function forwardRef(props, ref) {
        return <LogProps {...props} forwardedRef={ref} />;
      }

      // Give this component a more helpful display name in DevTools.
      // e.g. "ForwardRef(logProps(MyComponent))"
      const name = Component.displayName || Component.name;
      forwardRef.displayName = `logProps(${name})`;

      return React.forwardRef(forwardRef);
    }
    ```

71. ### Is it good to use arrow functions in render methods?

    Yes, You can use. It is often the easiest way to pass parameters to callback functions. But you need to optimize the performance while using it.

    ```javascript
    class Foo extends Component {
      handleClick() {
        console.log("Click happened");
      }
      render() {
        return <button onClick={() => this.handleClick()}>Click Me</button>;
      }
    }
    ```

    `Note:` Using an arrow function in render method creates a new function each time the component renders, which may have performance implications

72. ### How do you say that state updates are merged?

    When you call setState() in the component, React merges the object you provide into the current state.

    For example, let us take a facebook user with posts and comments details as state variables,

    ```javascript
      constructor(props) {
        super(props);
        this.state = {
          posts: [],
          comments: []
        };
      }
    ```

    Now you can update them independently with separate `setState()` calls as below,

    ```javascript
     componentDidMount() {
        fetchPosts().then(response => {
          this.setState({
            posts: response.posts
          });
        });

        fetchComments().then(response => {
          this.setState({
            comments: response.comments
          });
        });
      }
    ```

    As mentioned in the above code snippets, `this.setState({comments})` updates only comments variable without modifying or replacing `posts` variable.

73. ### How do you pass arguments to an event handler?

    During iterations or loops, it is common to pass an extra parameter to an event handler. This can be achieved through arrow functions or bind method.

    Let us take an example of user details updated in a grid,

    ```javascript
    <button onClick={(e) => this.updateUser(userId, e)}>Update User details</button>
    <button onClick={this.updateUser.bind(this, userId)}>Update User details</button>
    ```

    In the both approaches, the synthetic argument `e` is passed as a second argument. You need to pass it explicitly for arrow functions and it will be passed automatically for `bind` method.

74. ### How to prevent component from rendering?

    You can prevent component from rendering by returning null based on specific condition. This way it can conditionally render component.

    ```javascript
    function Greeting(props) {
      if (!props.loggedIn) {
        return null;
      }

      return <div className="greeting">welcome, {props.name}</div>;
    }
    ```

    ```javascript
    class User extends React.Component {
      constructor(props) {
        super(props);
        this.state = {loggedIn: false, name: 'John'};
      }

      render() {
       return (
           <div>
             //Prevent component render if it is not loggedIn
             <Greeting loggedIn={this.state.loggedIn} />
             <UserDetails name={this.state.name}>
           </div>
       );
      }
    ```

    In the above example, the `greeting` component skips its rendering section by applying condition and returning null value.

75. ### Give an example on How to use context?

    `Context` is designed to share data that can be considered `global` for a tree of React components.

    For example, in the code below lets manually thread through a “theme” prop in order to style the Button component.

    ```javascript
    //Lets create a context with a default theme value "luna"
    const ThemeContext = React.createContext("luna");
    // Create App component where it uses provider to pass theme value in the tree
    class App extends React.Component {
      render() {
        return (
          <ThemeContext.Provider value="nova">
            <Toolbar />
          </ThemeContext.Provider>
        );
      }
    }
    // A middle component where you don't need to pass theme prop anymore
    function Toolbar(props) {
      return (
        <div>
          <ThemedButton />
        </div>
      );
    }
    // Lets read theme value in the button component to use
    class ThemedButton extends React.Component {
      static contextType = ThemeContext;
      render() {
        return <Button theme={this.context} />;
      }
    }
    ```

76. ### How do you use contextType?

    ContextType is used to consume the context object. The contextType property can be used in two ways,

    1. `contextType as property of class:`
       The contextType property on a class can be assigned a Context object created by React.createContext(). After that, you can consume the nearest current value of that Context type using this.context in any of the lifecycle methods and render function.

       Lets assign contextType property on MyClass as below,

       ```javascript
       class MyClass extends React.Component {
         componentDidMount() {
           let value = this.context;
           /* perform a side-effect at mount using the value of MyContext */
         }
         componentDidUpdate() {
           let value = this.context;
           /* ... */
         }
         componentWillUnmount() {
           let value = this.context;
           /* ... */
         }
         render() {
           let value = this.context;
           /* render something based on the value of MyContext */
         }
       }
       MyClass.contextType = MyContext;
       ```

    2. `Static field`
       You can use a static class field to initialize your contextType using public class field syntax.

       ```javascript
       class MyClass extends React.Component {
         static contextType = MyContext;
         render() {
           let value = this.context;
           /* render something based on the value */
         }
       }
       ```

77. ### What is a consumer?

    A Consumer is a React component that subscribes to context changes. It requires a function as a child which receives current context value as argument and returns a react node. The value argument passed to the function will be equal to the value prop of the closest Provider for this context above in the tree.

    Lets take a simple example,

    ```javascript
    <MyContext.Consumer>
      {value => /* render something based on the context value */}
    </MyContext.Consumer>
    ```

78. ### How do you solve performance corner cases while using context?

    The context uses reference identity to determine when to re-render, there are some gotchas that could trigger unintentional renders in consumers when a provider’s parent re-renders.

    For example, the code below will re-render all consumers every time the Provider re-renders because a new object is always created for value.

    ```javascript
    class App extends React.Component {
      render() {
        return (
          <Provider value={{ something: "something" }}>
            <Toolbar />
          </Provider>
        );
      }
    }
    ```

    This can be solved by lifting up the value to parent state,

    ```javascript
    class App extends React.Component {
      constructor(props) {
        super(props);
        this.state = {
          value: { something: "something" },
        };
      }

      render() {
        return (
          <Provider value={this.state.value}>
            <Toolbar />
          </Provider>
        );
      }
    }
    ```

79. ### What is the purpose of forward ref in HOCs?

    Refs will not get passed through because ref is not a prop. It is handled differently by React just like `key`. If you add a ref to a HOC, the ref will refer to the outermost container component, not the wrapped component. In this case, you can use Forward Ref API. For example, we can explicitly forward refs to the inner FancyButton component using the React.forwardRef API.

    The below HOC logs all props,

    ```javascript
    function logProps(Component) {
      class LogProps extends React.Component {
        componentDidUpdate(prevProps) {
          console.log("old props:", prevProps);
          console.log("new props:", this.props);
        }

        render() {
          const { forwardedRef, ...rest } = this.props;

          // Assign the custom prop "forwardedRef" as a ref
          return <Component ref={forwardedRef} {...rest} />;
        }
      }

      return React.forwardRef((props, ref) => {
        return <LogProps {...props} forwardedRef={ref} />;
      });
    }
    ```

    Let's use this HOC to log all props that get passed to our “fancy button” component,

    ```javascript
    class FancyButton extends React.Component {
      focus() {
        // ...
      }

      // ...
    }
    export default logProps(FancyButton);
    ```

    Now let's create a ref and pass it to FancyButton component. In this case, you can set focus to button element.

    ```javascript
    import FancyButton from "./FancyButton";

    const ref = React.createRef();
    ref.current.focus();
    <FancyButton label="Click Me" handleClick={handleClick} ref={ref} />;
    ```

80. ### Is ref argument available for all functions or class components?

    Regular function or class components don’t receive the ref argument, and ref is not available in props either. The second ref argument only exists when you define a component with React.forwardRef call.

81. ### Why do you need additional care for component libraries while using forward refs?

    When you start using forwardRef in a component library, you should treat it as a breaking change and release a new major version of your library. This is because your library likely has a different behavior such as what refs get assigned to, and what types are exported. These changes can break apps and other libraries that depend on the old behavior.

82. ### How to create react class components without ES6?

    If you don’t use ES6 then you may need to use the create-react-class module instead. For default props, you need to define getDefaultProps() as a function on the passed object. Whereas for initial state, you have to provide a separate getInitialState method that returns the initial state.

    ```javascript
    var Greeting = createReactClass({
      getDefaultProps: function () {
        return {
          name: "Jhohn",
        };
      },
      getInitialState: function () {
        return { message: this.props.message };
      },
      handleClick: function () {
        console.log(this.state.message);
      },
      render: function () {
        return <h1>Hello, {this.props.name}</h1>;
      },
    });
    ```

    `Note:` If you use createReactClass then auto binding is available for all methods. i.e, You don't need to use `.bind(this)` with in constructor for event handlers.

83. ### Is it possible to use react without JSX?

    Yes, JSX is not mandatory for using React. Actually it is convenient when you don’t want to set up compilation in your build environment. Each JSX element is just syntactic sugar for calling `React.createElement(component, props, ...children)`.

    For example, let us take a greeting example with JSX,

    ```javascript
    class Greeting extends React.Component {
      render() {
        return <div>Hello {this.props.message}</div>;
      }
    }

    ReactDOM.render(
      <Greeting message="World" />,
      document.getElementById("root")
    );
    ```

    You can write the same code without JSX as below,

    ```javascript
    class Greeting extends React.Component {
      render() {
        return React.createElement("div", null, `Hello ${this.props.message}`);
      }
    }

    ReactDOM.render(
      React.createElement(Greeting, { message: "World" }, null),
      document.getElementById("root")
    );
    ```

84. ### How do you create HOC using render props?

    You can implement most higher-order components (HOC) using a regular component with a render prop. For example, if you would prefer to have a withMouse HOC instead of a <Mouse> component, you could easily create one using a regular <Mouse> with a render prop.

    ```javascript
    function withMouse(Component) {
      return class extends React.Component {
        render() {
          return (
            <Mouse
              render={(mouse) => <Component {...this.props} mouse={mouse} />}
            />
          );
        }
      };
    }
    ```

    This way render props gives the flexibility of using either pattern.

85. ### What is react scripts?

    The `react-scripts` package is a set of scripts from the create-react-app starter pack which helps you kick off projects without configuring. The `react-scripts start` command sets up the development environment and starts a server, as well as hot module reloading.

86. ### What are the features of create react app?

    Below are the list of some of the features provided by create react app.

    1. React, JSX, ES6, Typescript and Flow syntax support.
    2. Autoprefixed CSS
    3. CSS Reset/Normalize
    4. A live development server
    5. A fast interactive unit test runner with built-in support for coverage reporting
    6. A build script to bundle JS, CSS, and images for production, with hashes and sourcemaps
    7. An offline-first service worker and a web app manifest, meeting all the Progressive Web App criteria.

87. ### What is the purpose of renderToNodeStream method?

    The `ReactDOMServer#renderToNodeStream` method is used to generate HTML on the server and send the markup down on the initial request for faster page loads. It also helps search engines to crawl your pages easily for SEO purposes.
    `Note:` Remember this method is not available in the browser but only server.

88. ### How do you get redux scaffolding using create-react-app?

    Redux team has provided official redux+js or redux+typescript templates for create-react-app project. The generated project setup includes,

    1. Redux Toolkit and React-Redux dependencies
    2. Create and configure Redux store
    3. React-Redux `<Provider>` passing the store to React components
    4. Small "counter" example to demo how to add redux logic and React-Redux hooks API to interact with the store from components
       The below commands need to be executed along with template option as below,
    5. `Javascript template:`

    ```js
    npx create-react-app my-app --template redux
    ```

    2. `Typescript template:`

    ```js
    npx create-react-app my-app --template redux-typescript
    ```

89. ### What is state mutation and how to prevent it?

    `State mutation` happens when you try to update the state of a component without actually using `setState` function. This can happen when you are trying to do some computations using a state variable and unknowingly save the result in the same state variable. This is the main reason why it is advised to return new instances of state variables from the reducers by using Object.assign({}, ...) or spread syntax.

    This can cause unknown issues in the UI as the value of the state variable got updated without telling React to check what all components were being affected from this update and it can cause UI bugs.

    Ex:

    ```javascript
    class A extends React.component {
      constructor(props) {
        super(props);
        this.state = {
          loading: false
        }
     }

    componentDidMount() {
      let { loading } = this.state;
      loading = (() => true)(); // Trying to perform an operation and directly saving in a state variable
    }

    ```

    `How to prevent it:` Make sure your state variables are immutable by either enforcing immutability by using plugins like Immutable.js, always using `setState` to make updates, and returning new instances in reducers when sending updated state values.

## Disclaimer

The questions provided in this repository are the summary of frequently asked questions across numerous companies. We cannot guarantee that these questions will actually be asked during your interview process, nor should you focus on memorizing all of them. The primary purpose is for you to get a sense of what some companies might ask — do not get discouraged if you don't know the answer to all of them ⁠— that is ok!

Good luck with your interview 😊

---
