🚀 Namaste React — Episode 7
🧭 Finding the Path (Routing + Deep Hooks)

🎯 Goal of the Episode
This is a power-packed episode where we learn:

🧭 Routing in React
📄 Multiple pages (About, Contact, etc.)
🌳 Nested / Children Routes
🔗 Navigation using Link
❌ Error Handling in Routing
🧩 Dynamic Routing (real-world use case)
🪝 Deep dive into:
useEffect
useState (best practices)
🪝 Deep Dive into Hooks
⚛️ useEffect Hook — Complete Understanding

🧠 Pattern
Side Effects / Lifecycle Control

💡 Idea
Run code after rendering based on dependencies

📌 Syntax
useEffect(() => {
   // callback logic
}, [dependencies]);

🔥 MOST IMPORTANT INTERVIEW QUESTION

👉 When is useEffect called?
✅ Answer:
useEffect is called after every render

🎯 3 Cases of useEffect

1️⃣ No Dependency Array
useEffect(() => {
   console.log("called");
});

📌 Behavior:
Runs after every render
Initial render + re-renders

2️⃣ Empty Dependency Array
useEffect(() => {
   console.log("called once");
}, []);

📌 Behavior:
Runs only once
Only on initial render

3️⃣ With Dependencies
useEffect(() => {
   console.log("called when btn changes");
}, [btnName]);

📌 Behavior:
Runs when dependency changes

🔁 Summary Table
Case		Behavior
No array	Every render
[]		Only once
[dep]		When dep changes

⚛️ useState — 	Best Practices
❌ NEVER DO THESE

🚫 Outside component
🚫 Inside if/else
🚫 Inside loops
🚫 Inside functions

👉 Leads to:

Errors
Inconsistent behavior

✅ Correct Usage
const [state, setState] = useState();

📌 Always:
Inside component
At the top level

🧠 Why?

React expects:
Hooks order to be consistent
Execution to be predictable

🧭 Routing in React
🤔 Why Routing?

To create:
/ → Home
/about → About page
/contact → Contact page

📦 Library Used
👉 react-router-dom

⚙️ Installation
npm install react-router-dom

🧩 Creating Routes
🔧 Step 1: Create Router
import { createBrowserRouter } from "react-router-dom";

📌 Routing Configuration
const appRouter = createBrowserRouter([
  {
    path: "/",
    element: <AppLayout />,
  },
  {
    path: "/about",
    element: <About />,
  },
]);

🧠 Key Idea
👉 Configuration = Array of Objects

Each object defines:

path
element

🔌 Step 2: Provide Router
import { RouterProvider } from "react-router-dom";

<RouterProvider router={appRouter} />

❌ Error Handling in Routing

📌 Default Behavior

React Router shows:
👉 404 Error Page

🎯 Custom Error Page
{
  path: "/",
  element: <AppLayout />,
  errorElement: <Error />
}

🪝 useRouteError Hook
import { useRouteError } from "react-router-dom";
const err = useRouteError();

💡 Use Case
Show detailed error:

err.status
err.statusText

🌳 Nested / Children Routes

❓ Problem
Header disappears on route change ❌

✅ Solution → Children Routes
📌 Config
{
  path: "/",
  element: <AppLayout />,
  children: [
    {
      path: "/about",
      element: <About />,
    },
  ],
}

🧩 Outlet Component
import { Outlet } from "react-router-dom";

<Outlet />
🧠 Idea
👉 Outlet = Placeholder
Children render inside Outlet
Header stays constant

🔄 Flow

Route change
    ↓
Match child route
    ↓
Render inside <Outlet />

🔗 Navigation in React
❌ Using Anchor Tag
<a href="/about">About</a>

❌ Problem:
Reloads entire page

✅ Using Link
import { Link } from "react-router-dom";

<Link to="/about">About</Link>

⚡ Benefit
No full page reload
Faster navigation

🧠 Behind the Scenes

👉 Link → converts to <a> tag
👉 But React tracks navigation

⚡ Single Page Application (SPA)
🧠 Idea
Only one page
Components change dynamically

🔄 Difference

Server-Side Routing
Loads new HTML
Full refresh

Client-Side Routing (React)
No reload
Just component swap

🔁 Dynamic Routing (🔥 Important)
🎯 Goal
/restaurant/123
/restaurant/456

📌 Dynamic Route
{
  path: "/restaurant/:resId",
  element: <RestaurantMenu />
}
🧠 Idea
:resId = dynamic value

🪝 useParams Hook
import { useParams } from "react-router-dom";
const { resId } = useParams();

💡 Use Case
Get ID from URL → Fetch data

🌐 Fetching Data (useEffect + API)
useEffect(() => {
  fetchMenu();
}, []);

🧠 Why [] ?
👉 Only fetch once

⚛️ State for API Data
const [resInfo, setResInfo] = useState(null);
🎨 Conditional Rendering
if (resInfo === null) return <Shimmer />;
🔁 Rendering List (map)
itemCards.map((item) => (
  <li key={item.id}>
    {item.card.info.name}
  </li>
));

⚠️ Important Rule
👉 Always use key

🔗 Linking Cards to Dynamic Routes
<Link to={"/restaurant/" + id}>
  <RestaurantCard />
</Link>

🎯 Result
Click → Opens dynamic page
WITHOUT reload 🚀

🧠 Important Concepts Recap
✅ Hooks
useEffect (3 cases)
useState rules

✅ Routing
createBrowserRouter
RouterProvider
Link
Outlet

✅ Error Handling
errorElement
useRouteError

✅ Advanced Routing
Children routes
Dynamic routing
useParams

✅ Rendering
map()
keys
conditional rendering

🎯 Golden Interview Points

💬 React Routing is:
Client-side routing
No page reload
Uses Virtual DOM updates

💬 Link vs Anchor:
Anchor → reloads page ❌
Link → fast navigation ✅

💬 useEffect:
Runs after render
Controlled via dependency array

💬 Dynamic Routing:
:param in path
Access via useParams

🧠 Final Understanding

👉 React = Single Page App
👉 Routing = Component switching
👉 Link = No reload navigation
👉 Outlet = Dynamic rendering area

⏭️ Next Episode
📡 More real-world features
🍔 Food app improvements
⚡ Advanced routing

💬 Final Thought
If you truly understand this episode, you now know:

👉 How real apps like Swiggy routing works
👉 How pages change without reload
👉 How dynamic data is loaded

If you revise this once or twice…

👉 You can confidently explain routing in interviews 🔥
