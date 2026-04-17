📚 Namaste React – Episode 3
🧱 Laying the Foundation

⚠️ One of the most important episodes of the series because it explains the core fundamentals of React.

This episode covers:

NPM Scripts
React Elements
JSX
Babel
React Components
Component Composition
JSX Superpowers
JSX Security

🚀 Running the Project

Previously we used:
npx parcel index.html

📌 What this does

Runs Parcel bundler
Creates a development build
Hosts the app on
localhost:1234

Parcel performs many tasks automatically like:
Bundling
Hot Module Reloading
Caching
Transpiling
Dev server creation

⚙️ NPM Scripts
Instead of running long commands every time, we create scripts in package.json.

Example
"scripts": {
  "start": "parcel index.html",
  "build": "parcel build index.html"
}

▶️ Run Development Server
npm run start

or shortcut:

npm start
Important
npm start = npm run start

But
npm build ❌
npm run build ✔
🏭 Build for Production
npm run build

This creates optimized files in dist folder.

💡 Industry Tip

When joining a new project:
1️⃣ Open package.json
2️⃣ Check scripts section
You will know exactly how to run the project.

🧩 React Element
A React Element represents UI in React.

Example:
const heading = React.createElement(
  "h1",
  { id: "heading" },
  "Namaste React"
);

📌 Arguments of createElement
React.createElement(tag, attributes, children)

Example:

tag → h1
attributes → { id: "heading" }
children → "Namaste React"

⚠️ Important Concept
Many developers think React element = HTML element.

❌ Wrong

✔️ Truth
React Element = JavaScript Object

When rendered → becomes HTML.

🔄 Rendering in React

First create root:

const root = ReactDOM.createRoot(
  document.getElementById("root")
);

Render element:

root.render(heading);

Flow
React Element (Object)
        ↓
ReactDOM.render
        ↓
Converted to HTML
        ↓
Displayed in browser

📌 Important Behavior
React replaces everything inside root.

Example:

<div id="root">
Akshay is here
</div>

After render:

<h1>Namaste React</h1>

❗ Developer Tip

Inside HTML often write:
<div id="root">Not rendered</div>

If React fails → you will see "Not rendered".

😵 Problem with React.createElement
Creating complex UI becomes messy.

Example:

React.createElement(
 "div",
 {},
 React.createElement("h1", {}, "Hello")
)

Hard to read.
✨ Solution → JSX
React introduced JSX.

🧠 What is JSX?
JSX is a syntax for writing React elements easily.

Example:
const jsxHeading = <h1>Namaste React</h1>;

Much cleaner than:
React.createElement("h1", {}, "Namaste React")

❗ Very Important
Many developers misunderstand this.

JSX is NOT
❌ HTML inside JavaScript

JSX is
✔️ HTML-like syntax

JSX ≠ HTML
JSX ≠ JavaScript
JSX = HTML-like syntax

🔄 JSX vs React.createElement
These two are equivalent.

JSX:
const heading = <h1>Namaste React</h1>;

Compiled to:
React.createElement("h1", {}, "Namaste React");

⚙️ How JSX Works Behind the Scenes
JSX cannot run directly in browsers.
Browsers understand JavaScript (ECMAScript) only.
JSX must be converted first.

🔧 Transpiling

JSX is transpiled before reaching the browser.

JSX
 ↓
Babel
 ↓
React.createElement
 ↓
React Element Object
 ↓
HTML in DOM

🧙 Babel
Babel = JavaScript Compiler / Transpiler

Responsibilities:
Convert JSX → React.createElement
Convert modern JS → browser-compatible JS

Example transformation:
JSX
<h1>Namaste React</h1>

Babel output

React.createElement("h1", null, "Namaste React");

🧠 Important Relationship
Parcel
   ↓
Uses Babel
   ↓
Babel transpiles JSX
   ↓
Browser executes JavaScript

Parcel = manager
Babel = compiler

⚠️ JSX Rules
1️⃣ Use className

HTML:
class="heading"

JSX:
className="heading"

2️⃣ CamelCase Attributes

HTML:
tabindex

JSX:
tabIndex

3️⃣ Multi-line JSX Needs Parentheses

Single line:
const heading = <h1>Hello</h1>;

Multi line:
const heading = (
  <h1>
     Hello
  </h1>
);

🧰 Useful VS Code Extensions

⭐ Prettier
Auto formats code.

⭐ Bracket Pair Colorizer
Colors nested brackets.

⭐ ESLint
Code linting.

🧩 React Components
React apps are built using components.

Example UI pieces:

Header
Footer
Card
Button
Search bar
All are components.

🧠 Types of Components

1️⃣ Class Components (Old)
Use JavaScript classes.
class Header extends React.Component {}
Rarely used today.

2️⃣ Functional Components (Modern)
Use JavaScript functions.
Industry standard.

⭐ React Functional Component

Definition:
A JavaScript function that returns JSX.

Example:
const HeadingComponent = () => {
  return <h1>Namaste React</h1>;
};

🧠 Alternative Syntax

Without return:
const HeadingComponent = () => (
   <h1>Namaste React</h1>
);

Both are valid.

🚀 Rendering Components

React element:
root.render(heading);

Component:
root.render(<HeadingComponent />);

🧩 Component Composition

Component inside another component.

Example:
const Title = () => (
   <h1>Title Component</h1>
);

const Heading = () => (
   <div>
      <Title />
      <h2>Heading Component</h2>
   </div>
);

This is called:
Component Composition

⚡ JSX Superpower
Inside JSX you can write JavaScript expressions.

Example:
const number = 1000;

<h1>{number}</h1>

Output:
1000

🧮 JavaScript Expressions in JSX

Examples:
<h1>{100 + 200}</h1>

Output
300

You can run any expression.

🧪 JSX + JavaScript
const data = 1000;

const Heading = () => (
   <h1>{data}</h1>
);

🔐 JSX Security
JSX prevents XSS (Cross Site Scripting).

Example attack attempt:
<script>alert("hack")</script>
JSX sanitizes the data automatically.
So malicious scripts cannot run.
This is built-in security.

🧠 Advanced JSX Behavior

You can insert:

React Element
{element}
Component
<Title />
Function Call
{Title()}

All are valid.

🔁 Three Equivalent Ways
<Title />
<Title></Title>
{Title()}
All render the component.

📌 Final Important Understanding

Everything in React eventually becomes:

JSX
 ↓
React.createElement
 ↓
JavaScript Object (React Element)
 ↓
HTML in DOM

🧠 Key Takeaways
JSX
HTML-like syntax
Makes React code readable
Transpiled by Babel

Babel
Converts JSX to React.createElement
Makes code browser compatible

React Element
JavaScript object
Created using JSX or createElement

React Component
Function that returns JSX

Component Composition
Component inside component.

JSX Superpower
Use JavaScript inside {}.

JSX Security
Protects from XSS attacks automatically.

🧠 Big Realization
Your React code is readable not because of React.

JSX makes React readable.

📚 Next Episode
You will start building real React components and applications and dive deeper into React.
