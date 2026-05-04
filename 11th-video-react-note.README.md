🚀 Namaste React — Episode 11
🛢️ Data is the New Oil
🎯 Goal of the Episode

In this episode, we learn:

🧠 Managing data layer in React
🧩 Higher Order Components (HOC)
📦 Controlled vs Uncontrolled Components
🔼 Lifting State Up (VERY IMPORTANT 🔥)
🌳 React Component Hierarchy
⚠️ Props Drilling problem
🌐 React Context API
🔁 Updating global data dynamically

🧠 Core Idea of the Episode
💡 React has 2 Layers
UI Layer (JSX)
↓
Data Layer (State, Props, Variables)

🎯 Golden Line
👉 UI is driven by Data

🧠 Important Understanding
UI is static
Data is dynamic
React = Sync between UI & Data
🎯 Interview Line
👉 “A React app mainly consists of a UI layer and a Data layer. The UI is a function of data.”

🧩 Higher Order Components (HOC)
🧠 Pattern
Component Enhancement

💡 Idea
A function that takes a component → returns a component

📌 Definition
👉 HOC = function(Component) → New Component

🎯 Purpose
👉 Add extra features without modifying original component

📌 Example Use Case

👉 Add Promoted Label on RestaurantCard

⚛️ HOC Code
const withPromotedLabel = (RestaurantCard) => {
  return (props) => {
    return (
      <div>
        <label>Promoted</label>
        <RestaurantCard {...props} />
      </div>
    );
  };
};
🧠 Flow
RestaurantCard
     ↓
HOC (Enhance)
     ↓
New Component (PromotedCard)

🎯 Key Concept

👉 Do NOT modify original component
👉 Just enhance it

🧠 Interview Line
👉 “HOC is used to reuse component logic and enhance UI without modifying original components.”

🧠 Pure Functions in HOC
💡 Idea
👉 HOC should NOT modify original component

🎯 Rule
No side effects
Just wrap + return

🧩 Accordion Feature (Project Part)
🎯 What we built
Restaurant Menu UI
Categories (Accordion)
Expand / Collapse behavior

🧠 Data Handling
👉 Filter only Item Categories

cards.filter((c) =>
  c.card?.card?.["@type"] === "type.googleapis.com/...ItemCategory"
);
⚠️ Important JS Concept

👉 Access special keys:
object["key-name"]
🧩 Controlled vs Uncontrolled Components
🧠 Core Concept
❌ Uncontrolled Component

👉 Component manages its own state

const [showItems, setShowItems] = useState(false);
✅ Controlled Component

👉 Parent controls component via props

<RestaurantCategory showItems={true} />
🎯 Difference
Type	Control
Uncontrolled	Self
Controlled	Parent
🧠 Interview Line
👉 “Controlled components are driven by props, while uncontrolled components manage their own state.”

🔼 Lifting State Up (VERY IMPORTANT 🔥)
🧠 Pattern
State Management

💡 Idea
Move state from child → parent

❌ Problem
Each accordion had its own state:

Category 1 → showItems
Category 2 → showItems

👉 No coordination ❌

✅ Solution

Move state to parent:
const [showIndex, setShowIndex] = useState(0);

🎯 Logic
showItems = index === showIndex
🔁 Flow
Click Category
     ↓
Call setShowIndex(index)
     ↓
Parent updates state
     ↓
All children re-render
     ↓
Only one opens

🧠 Interview Line
👉 “Lifting state up allows parent to control multiple child components.”

🧠 Toggle Logic
📌 Code
setShowIndex(index);
🎯 Behavior
Only ONE accordion open
Others auto-close
🧪 React DevTools (VERY IMPORTANT TOOL 🔥)
🎯 Features
View component tree 🌳
Inspect props & state 📦
Debug efficiently 🔍
Performance profiling ⚡
🧠 Key Learning

👉 UI Layer (left)
👉 Data Layer (right)

⚠️ Props Drilling Problem
🧠 Pattern
Deep Data Passing

💡 Idea
Passing props through multiple layers

❌ Example
App
 ↓
Category
 ↓
ItemList

👉 Data passed through all levels ❌

🎯 Problem
Messy code
Hard to maintain
Unnecessary passing

🧠 Interview Line
👉 “Props drilling is passing data through multiple components unnecessarily.”

🌐 React Context API (SUPER IMPORTANT 🔥🔥)
🧠 Pattern
Global State

💡 Idea
Access data anywhere without props

📌 Create Context
import { createContext } from "react";

const UserContext = createContext({
  loggedInUser: "Default User",
});
📌 Use Context (Functional)
const { loggedInUser } = useContext(UserContext);
📌 Use Context (Class)
<UserContext.Consumer>
  {(data) => <h1>{data.loggedInUser}</h1>}
</UserContext.Consumer>
🧠 Context Provider
📌 Wrap App
<UserContext.Provider value={{ loggedInUser: "Akshay" }}>
  <App />
</UserContext.Provider>

🎯 Effect
👉 All components get this value

🔁 Dynamic Context Update
📌 Using State
const [username, setUsername] = useState("Akshay");
<UserContext.Provider value={{ loggedInUser: username }}>
📌 Update via Input
<input
  value={username}
  onChange={(e) => setUsername(e.target.value)}
/>
🎯 Result
👉 Changes everywhere instantly 🔥

🌍 Context Superpower
💡 Works Across:
Components
Pages
Lazy Loaded Routes ⚡

🎯 Key Insight
👉 Even lazy-loaded components get updated data

🧠 Nested Context (ADVANCED 🔥)
📌 Example
<UserContext.Provider value="Akshay">
  <Header />
  <UserContext.Provider value="Elon Musk">
    <Header />
  </UserContext.Provider>
</UserContext.Provider>
🎯 Result
Outer → Akshay
Inner → Elon Musk
🧠 When to Use Context?
✅ Use When
Global data needed
Theme 🌙
Logged-in user 👤
Language 🌍
❌ Avoid When
Only few components need data
⚖️ Context vs Redux
🧠 Context
Built-in
Simple
Good for small-medium apps
🧠 Redux
External library
Scalable
Complex state handling
🎯 Interview Line
👉 “Context is suitable for small to medium apps, while Redux is preferred for large-scale state management.”

🧠 Final Recap
✅ Concepts Covered
HOC
Accordion UI
Controlled vs Uncontrolled
Lifting State Up
React DevTools
Props Drilling
Context API
Dynamic Context Updates
🎯 Final Understanding

👉 Data Layer is EVERYTHING
👉 Parent should control shared state
👉 Context removes props drilling
👉 React = UI driven by data

🏁 Final Verdict
📊 Interview Readiness
👉 This episode = 🔥 11/10 (VERY IMPORTANT)

💬 Final Thought
👉 If you understand this episode deeply:

You are no longer a beginner.
You are thinking like a React Engineer.
