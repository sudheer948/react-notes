Namaste React – Episode 01 Notes
🚀 Inception (Foundation of React)

1️⃣ About React

📌 Concept
React is a JavaScript library used to build large-scale frontend applications.

🧠 Idea
React simplifies building complex UI by managing DOM efficiently using JavaScript.

⚙️ Key Points

React is the most popular JavaScript library for UI.
Created and maintained by Facebook (Meta).
Used for large-scale applications.
React focuses on performance and maintainability.

2️⃣ Course Learning Tips (Very Important)

📝 Tip 1 – Make Your Own Notes
Always write concepts in your own notebook
Helps with long-term memory

💻 Tip 2 – Code Along
Do NOT just watch videos.

Instead:
Pause the video
Code yourself
Experiment

🧑‍💻 Tip 3 – Maintain GitHub Repository

Create a repo like:
Namaste-React

Push:
assignments
notes
practice code

Benefits:
portfolio
revision
GitHub activity graph

3️⃣ Tools Required

🌐 Browser
Recommended:
Google Chrome

Why?
Best developer tools
Strong debugging support

Open developer tools:
Right Click → Inspect
📝 Code Editor

Recommended editor:
VS Code

Reasons:
Extensions
Emmet support
Fast developer experience

4️⃣ Starting From Scratch

Create a folder:
Namaste-React
Open it in VS Code.

Then create:
index.html

5️⃣ Emmet in VS Code

📌 Concept
Emmet automatically generates HTML structure.

Example
Type:
html:5
Press Enter

It generates:

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title></title>
</head>
<body>

</body>
</html>

6️⃣ Hello World Using HTML
Code
<body>

<div id="root">
<h1>Hello World</h1>
</div>

</body>
Output
Hello World

Browser Behavior
Browser reads HTML and directly renders it to DOM.

7️⃣ Hello World Using JavaScript
Instead of writing HTML directly, we can create elements using JavaScript.

Step 1 – Create element
const heading = document.createElement("h1");
Step 2 – Add text
heading.innerHTML = "Hello World from JavaScript";
Step 3 – Select root
const root = document.getElementById("root");
Step 4 – Append element
root.appendChild(heading);

Final Code
<script>

const heading = document.createElement("h1");
heading.innerHTML = "Hello World from JavaScript";

const root = document.getElementById("root");
root.appendChild(heading);

</script>

Result
Hello World from JavaScript

8️⃣ Why Browser Understands JavaScript?

Browsers have:
🧠 JavaScript Engine

Examples:
Chrome → V8
Firefox → SpiderMonkey

Browser already understands APIs like:

document
createElement
innerHTML
getElementById

These are called Browser APIs.

9️⃣ Browser Does NOT Understand React

Browser only understands:

HTML
CSS
JavaScript

React is not built into the browser.
So we must add React to our project.

🔟 Adding React to Project
Method 1 — CDN
CDN = Content Delivery Network

It hosts libraries online.
We import React using script tags.
Add before closing body tag

<script src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
Now React is available in our project.

1️⃣1️⃣ What Happens After Importing React?

If you open console:
React

You will see a React object.
That means React is loaded.

Example properties:

React.Component
React.Fragment
React.Children

1️⃣2️⃣ React is Just JavaScript

Important idea:
React = JavaScript library
React code is just JavaScript written by Facebook engineers.

Example file:
react.development.js
Contains React source code.

1️⃣3️⃣ Why Two React Files?

We imported two files:
1️⃣ react.development.js
Contains Core React logic

2️⃣ react-dom.development.js
Responsible for DOM manipulation
React itself is platform-independent.

It works in:
browsers
mobile apps (React Native)
3D environments

ReactDOM connects React with the browser DOM.

1️⃣4️⃣ First React Program

Step 1 — Create element
const heading = React.createElement(
"h1",
{},
"Hello World from React"
);

Parameters
React.createElement(type, props, children)

Parameter	Meaning
type		tag name
props		attributes
children	inner content

Step 2 — Create Root
const root = ReactDOM.createRoot(
document.getElementById("root")
);

Step 3 — Render Element
root.render(heading);

Final React Code
const heading = React.createElement(
"h1",
{},
"Hello World from React"
);

const root = ReactDOM.createRoot(
document.getElementById("root")
);

root.render(heading);

1️⃣5️⃣ React Element is NOT HTML
Important concept.

console.log(heading)

Output:
Object

So:
React Element = JavaScript Object
React converts that object into real HTML during rendering.

React Rendering Flow
React.createElement()
        ↓
Creates React Object
        ↓
root.render()
        ↓
React converts object → HTML
        ↓
Browser displays it

1️⃣6️⃣ Creating Nested Elements

Example HTML

<div id="parent">
  <div id="child">
    <h1>I am H1</h1>
  </div>
</div>

React version:

const parent = React.createElement(
"div",
{id:"parent"},
React.createElement(
"div",
{id:"child"},
React.createElement("h1",{}, "I am H1")
)
);

1️⃣7️⃣ Multiple Children

If multiple children exist:

<div>
<h1></h1>
<h2></h2>
</div>

We pass array of children

React.createElement(
"div",
{},
[
React.createElement("h1",{}, "I am H1"),
React.createElement("h2",{}, "I am H2")
]
)

1️⃣8️⃣ Why React.createElement is Ugly
Nested structures become messy.

Example:
React.createElement(
React.createElement(
React.createElement(

Hard to read.

Solution:
JSX
JSX will be introduced in the next episode.

1️⃣9️⃣ File Separation
Instead of writing React inside HTML:

Create
app.js

Move React code there.

Link it:
<script src="./app.js"></script>

Cleaner project structure.

2️⃣0️⃣ Root Rendering Behavior
Important concept.

If HTML has:

<div id="root">
<h1>Akshay is here</h1>
</div>

Then React renders:
root.render(parent)

Result:
Existing content is replaced
Not appended.

2️⃣1️⃣ React Works Only Inside Root

Example:

<h1>Top</h1>
<div id="root"></div>
<h1>Bottom</h1>

React will only modify:
div#root

Everything else remains untouched.

2️⃣2️⃣ Why React is Called a Library
Because React can be used in small parts of an application.

Example:
only header
only sidebar
only footer

Frameworks usually control the entire application.
React does not force that.

2️⃣3️⃣ Important Curiosity Questions
Good developers ask questions like:

What is CDN?
What is crossOrigin?
Why two React files?
What is React element?
Why does file order matter?
What is development vs production build?

Curiosity makes you a better engineer.

🧠 Final Episode Summary

We learned:

1️⃣ Hello World using HTML
2️⃣ Hello World using JavaScript
3️⃣ How to add React using CDN
4️⃣ React.createElement()
5️⃣ ReactDOM.createRoot()
6️⃣ root.render()
7️⃣ React Element = JavaScript Object
8️⃣ Nested React elements
9️⃣ Multiple children using arrays
🔟 React replaces DOM inside root
1️⃣1️⃣ React is a JavaScript library

⭐ Quick Revision (Important)
React.createElement()
→ creates React element (object)

ReactDOM.createRoot()
→ creates root container

root.render()
→ converts React object → HTML
→ inserts into DOM
