🎓 Episode 8 — Class-Based Components (Let’s Get Classy)
🧠 Why Learn Class-Based Components?
Even though functional components are modern, class-based components are still important:

🎯 Reasons:
💼 Interview Questions → Frequently asked
🏢 Legacy Codebases → Many companies still use them
🧩 Deep React Understanding → Helps understand lifecycle & internals
⚙️ Historical Context → Shows how React evolved

👉 Think of it as:

Functional Components = 🆕 Modern
Class Components = 🧱 Foundation

🔁 Functional vs Class Components
🧩 Functional Component
const User = () => {
  return <h1>Hello</h1>;
};

🏗️ Class Component
class User extends React.Component {
  render() {
    return <h1>Hello</h1>;
  }
}

⚡ Key Difference

Functional	Class
Function	Class
Returns JSX	render() returns JSX
Hooks used	Lifecycle methods used

🧱 Creating Class-Based Component
✅ Basic Structure
class User extends React.Component {
  render() {
    return <div>User Component</div>;
  }
}

🔥 Important Points:
Must use class
Must extend React.Component
Must have render() method

📦 Props in Class Components
📤 Passing Props
<User name="Akshay" />

📥 Receiving Props
constructor(props) {
  super(props);
  console.log(props);
}

📌 Using Props
this.props.name

⚠️ Important:
super(props) is mandatory
Use this.props everywhere

🧠 State in Class Components
🆚 Functional vs Class

Functional	Class
useState()	this.state
setState()	this.setState()

🧱 Creating State
constructor(props) {
  super(props);

  this.state = {
    count: 0,
  };
}

📊 Using State
this.state.count

✏️ Updating State (VERY IMPORTANT)
❌ Wrong way:
this.state.count = this.state.count + 1; // ❌ NEVER

✅ Correct way:
this.setState({
  count: this.state.count + 1,
});

🚨 Rule:
👉 Never directly mutate state

🔄 Multiple State Variables
this.state = {
  count: 0,
  count2: 2,
};

👉 State is always a single object

🔁 Lifecycle Methods (CORE 🔥)
🔄 Mounting Phase (Component Loads)
🧠 Order:
constructor()
render()
componentDidMount()
📌 Explanation:
🏗️ constructor → Initialize state & props
🎨 render → Returns JSX
🚀 componentDidMount → Runs after DOM update

🔄 Updating Phase
Triggered when:
state changes
props change

🧠 Order:
render()
componentDidUpdate()

🔄 Unmounting Phase
🧠 Method:
componentWillUnmount()

👉 Called when component is removed

⚡ Full Lifecycle Flow
📊 Simple Flow:
Mount:
constructor → render → componentDidMount

Update:
render → componentDidUpdate

Unmount:
componentWillUnmount

👨‍👩‍👧 Parent-Child Lifecycle Order
🧠 Order:
Parent Constructor
Parent Render
Child Constructor
Child Render
Child componentDidMount
Parent componentDidMount

🔥 Multiple Children (VERY IMPORTANT 🔥)
🧠 Actual Order:
Parent Constructor
Parent Render

Child1 Constructor
Child1 Render

Child2 Constructor
Child2 Render

Child1 componentDidMount
Child2 componentDidMount

Parent componentDidMount

⚡ Why This Happens?
🚀 React Optimization

React uses:

🧩 Two Phases:
1️⃣ Render Phase
constructor
render
Virtual DOM diff
2️⃣ Commit Phase
DOM update
componentDidMount

💡 Key Insight:

👉 React batches render phase
👉 DOM updates happen together (performance optimization)

🌐 API Calls in Class Components
📍 Where?
👉 componentDidMount()

🧠 Why?

❌ Don’t wait for API before rendering
✅ Render first → Fetch later → Update UI

🧪 Example:
async componentDidMount() {
  const data = await fetch(API);
  const json = await data.json();

  this.setState({
    userInfo: json,
  });
}

🔄 Lifecycle with API
🧠 Flow:
constructor → render (dummy data)
→ componentDidMount → API call
→ setState → render again (real data)
→ componentDidUpdate

🧹 Cleanup (VERY IMPORTANT 🔥)
Problem:
setInterval(() => {
  console.log("Running...");
}, 1000);

👉 Keeps running even after leaving page ❌

✅ Solution:
componentWillUnmount() {
  clearInterval(this.timer);
}

💡 Use Case:
Timers ⏱️
Event listeners 🎧
Subscriptions 🔔

⚠️ Important Concepts
❌ Never Compare:
👉 useEffect ≠ componentDidMount
They are NOT equivalent

🧠 Why Hooks Exist?
Because class components were:

😵 Complex
📉 Hard to maintain
🔁 Too much boilerplate

🔥 Advanced Insight (INTERVIEW GOLD 🏆)
💡 setState Behavior:
Merges state (not replaces)
Updates only provided fields

💡 React Re-render:
Triggered by state/props change
Uses Virtual DOM diffing

🧪 Homework (VERY IMPORTANT)
📝 1.
👉 Why do we use super(props)?

📝 2.
👉 Why can’t we make useEffect callback async?

🎯 Final Takeaways
Class components = 🧱 foundation of React
Lifecycle = 🧠 core interview topic
setState = ⚡ controlled updates
componentDidMount = 🌐 API calls
componentWillUnmount = 🧹 cleanup
React = ⚡ optimized via batching

🏁 Final Verdict
📊 Interview Readiness:
👉 This episode alone = 9/10 interview power 💪

