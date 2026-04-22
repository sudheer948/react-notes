🚀 Namaste React — Episode 5
🪝 Let’s Get Hooked

🎯 Goal of the Episode
In this episode we learn the real superpower of React.

Topics covered:

🧹 Code restructuring (industry practices)
📁 Folder structure
📦 Export / Import
🧰 Utils & constants
🪝 React Hooks
⚛️ useState
🔄 Re-rendering
🌳 Virtual DOM
⚡ React Fiber
🔍 Diff Algorithm
🔄 Reconciliation

This episode is one of the most important React fundamentals.

🤔 Why Use React?

Important myth:
Anything React can do can also be done with HTML + CSS + JavaScript.

So why React?
Because React:

⚡ Improves developer experience
⚡ Helps build large scalable applications
⚡ Writes less code for complex UI
⚡ Handles efficient DOM updates

React focuses mainly on:
Efficient DOM Manipulation

This is the core reason React is fast.

🧹 Cleaning Our Application

Previously we wrote everything in:
app.js

Example:

Header
Body
RestaurantCard
AppLayout

All components were in one file.

Problem:

❌ Huge file
❌ Hard to maintain
❌ Difficult for teams

Industry practice:
Separate files for each component

📁 Folder Structure (Industry Convention)

A common React project structure:

project
│
├── index.html
├── package.json
│
└── src
     │
     ├── app.js
     │
     ├── components
     │     ├── Header.js
     │     ├── Body.js
     │     └── RestaurantCard.js
     │
     └── utils
           ├── constants.js
           └── mockData.js

📦 Why Use src Folder?
Almost every project contains a src folder.

Meaning:
src = source code

Benefits:

Keeps project clean
Easy to locate code
Industry standard
React itself does not force folder structure.
Teams decide their own structure.

🧩 Components Folder

Inside src we create:
components/

Purpose:
Store all React components.

Example:

components/
  Header.js
  Body.js
  RestaurantCard.js

Rule:
📌 Component file name = component name

Example:
Header.js → Header component
Body.js → Body component

📦 Moving Components to Separate Files

Example:

Header.js
const Header = () => {
  return (
    <div className="header">
      <img src={logoUrl}/>
    </div>
  );
};

export default Header;

Importing Component

In app.js:
import Header from "./components/Header";

Rule:
First Export → Then Import

📤 Types of Export
React uses two types of export.

1️⃣ Default Export
Only one default export per file.

Example:
export default Header;

Import:
import Header from "./Header";

2️⃣ Named Export
Used when exporting multiple things.

Example:
export const CDN_URL = "...";
export const LOGO_URL = "...";

Import:
import { CDN_URL, LOGO_URL } from "./constants";

📊 Default vs Named Export
Type	Export			Import
Default	export default Header	import Header from "./Header"
Named	export const CDN_URL	import { CDN_URL } from "./constants"

🧰 Utilities Folder
Hardcoded values should not be inside components.

Bad practice:
Header.js
logo URL inside component ❌

Good practice:
utils/constants.js

Example:
export const CDN_URL = "...";
export const LOGO_URL = "...";

🧪 Mock Data File
Mock restaurant data should also be separate.

Example:
utils/mockData.js
export const resList = [ ... ];

Then import:
import { resList } from "../utils/mockData";

🎯 Feature to Build
We now add a Top Rated Restaurant Filter.

Goal:
When user clicks button:
Show only restaurants with rating > 4

🔘 Creating Button
Inside Body component:

<button className="filter-btn">
Top Rated Restaurants
</button>

🖱️ Event Handling in React
React uses camelCase events.

Example:

onClick
onChange
onMouseOver

Example:
<button onClick={() => console.log("Clicked")}>

⚡ Dynamic UI Concept
Currently UI is static.

React apps should be:
Dynamic + Interactive

Example UI flow:

Restaurant Data
      ↓
React Component
      ↓
UI Rendering

If data changes → UI updates.

❌ Problem with Normal Variables

Example:
let listOfRestaurants = resList;

If we modify:
listOfRestaurants = filteredList;

React will NOT update UI.

Why?
Because React does not track normal variables.

🪝 React Hooks
React provides special functions called:
Hooks

Definition:
Hooks are normal JavaScript functions provided by React.

⭐ Most Important Hooks
Two hooks are used most frequently:

1️⃣ useState
2️⃣ useEffect

Usage frequency:
useState  → 80%
useEffect → 20%

🪝 useState Hook

it manages the state of a component.

Purpose:
Create State Variables.
State variable = special variable React tracks.

📦 Importing useState
import { useState } from "react";

Named import.

⚛️ Creating State Variable

Syntax:
const [state, setState] = useState(defaultValue);

Example:
const [listOfRestaurants, setListOfRestaurants] = useState(resList);

🧠 Array Destructuring
useState() returns an array.

Example:
const arr = useState();

Equivalent to:
const list = arr[0];
const setList = arr[1];

React uses array destructuring.

🔄 Updating State

Wrong:
listOfRestaurants = newData ❌

Correct:
setListOfRestaurants(newData)

⭐ Important Rule
Never modify state directly.
Always use setter function.

Example:
setListOfRestaurants(filteredList);

🔁 React Re-rendering

Golden rule:
Whenever a state variable updates,
React re-renders the component.

Meaning:

State change
      ↓
Component re-render
      ↓
UI update

⚡ Example Flow

User clicks button

Click Button
     ↓
Filter restaurants
     ↓
setListOfRestaurants()
     ↓
React detects state change
     ↓
Component re-renders
     ↓
UI updates

🌳 Virtual DOM
DOM = HTML tree.

Example:

div
 └── RestaurantCard
 └── RestaurantCard
 └── RestaurantCard

Virtual DOM:
JavaScript object representation of DOM

Example:

{
 type: "div",
 children: [...]
}

⚡ Why Virtual DOM is Fast
React compares objects, not actual HTML.
Object comparison is much faster.

🔍 Diff Algorithm

When state changes:
React creates:

Old Virtual DOM
New Virtual DOM

Then it compares them.

Example:
Old DOM
7 cards

New DOM
3 cards

React calculates the difference.
Only updates required elements.

🔄 Reconciliation

Definition:
Process of comparing old Virtual DOM
with new Virtual DOM and updating UI.

Steps:

State Change
      ↓
New Virtual DOM
      ↓
Diff Algorithm
      ↓
Update Real DOM

⚡ React Fiber
React Fiber = new rendering algorithm.

Introduced in:
React 16

Purpose:

Better rendering
Incremental updates
Faster UI updates

🧠 Why React is Fast

Interview answer:
React is fast because:

Virtual DOM
Diff Algorithm
Efficient DOM Manipulation
React Fiber

🧠 Data Layer vs UI Layer
React keeps these in sync.

Data Layer
(state variables)
      ↓
React
      ↓
UI Layer
(DOM)

If data changes → UI updates.

📌 Key Concepts Learned

This episode covered:

✅ Folder structure
✅ Component separation
✅ Export / Import
✅ Named export vs default export
✅ Utilities folder
✅ Mock data separation
✅ Event handlers
✅ React Hooks
✅ useState
✅ State variables
✅ Re-rendering
✅ Virtual DOM
✅ Diff algorithm
✅ React Fiber

🎯 Important React Rule

Memorize this line:

Whenever a state variable changes,
React re-renders the component.

This is core React behavior.

⏭️ Next Episode
Next topics will include:

🔄 useEffect
🌐 Fetching APIs
🍔 Real restaurant data
⚛️ React lifecycle

Your Food Ordering App will become fully dynamic.
