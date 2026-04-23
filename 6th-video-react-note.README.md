📘 Episode 6 — Exploring the World (Fetching Data, useEffect, Shimmer UI, Search)

1️⃣ Monolith vs Microservice Architecture

Monolith Architecture
In traditional web applications, everything exists inside one big project.

Example structure:

Single Project
 ├── UI
 ├── Backend APIs
 ├── Authentication
 ├── Database Logic
 ├── Notifications
 └── Business Logic

Example
A Java project might contain:

Java Project
 ├── API code
 ├── JSP pages (UI)
 ├── DB connection
 ├── Authentication
 └── Notifications

Problem with Monolith
Even for a small change:

Example:
Change button color

You must:
Rebuild entire project
Compile whole project
Deploy whole application

So the entire application redeploys for a tiny change.

Microservice Architecture
Modern applications break systems into small independent services.

Example:

Application
 ├── UI Service
 ├── Backend Service
 ├── Authentication Service
 ├── Database Service
 ├── Notification Service
 └── Payment Service

Each service has one responsibility.

Principles

1️⃣ Separation of Concerns
Each service handles a separate task.

Example:

UI → display
Backend → business logic
Auth → authentication
Notifications → SMS / Email

2️⃣ Single Responsibility Principle
Each service does only one job.

Example:

SMS Service → send SMS
Email Service → send emails

Advantages of Microservices

1️⃣ Independent deployment
2️⃣ Faster development
3️⃣ Different teams work independently
4️⃣ Different tech stacks possible

Example:

UI → React
Backend → Java
Notification → Golang
Analytics → Python

2️⃣ How Microservices Communicate
Services communicate through APIs.

Example:

UI → calls backend API
Backend → fetches DB data
Backend → calls notification service

Ports Example
Different services run on different ports.

UI Service → localhost:1234
Backend → localhost:1000
SMS Service → localhost:3000

These ports map to URLs.

Example:

domain.com/       → UI
domain.com/api    → backend
domain.com/sms    → SMS service

3️⃣ React Application in Microservices

Our React app acts as:
UI Microservice

It communicates with backend APIs to fetch data.

Example:
React App → API → Backend → Database

4️⃣ Fetching Data in Web Applications
Two approaches exist.

Approach 1

Flow
Page Load
   ↓
Make API Call
   ↓
Wait for response
   ↓
Render UI

Problem
If API takes 500ms

User sees:
Blank screen for 500ms
Poor UX.

Approach 2 (React Approach)

Flow
Page Load
   ↓
Render UI (empty or skeleton)
   ↓
Make API Call
   ↓
Update UI with data

Result
Page loads instantly
Content appears gradually
Better User Experience (UX).

5️⃣ useEffect Hook

What is a Hook?
A hook is simply:
A JavaScript function provided by React

Example hooks:

useState
useEffect
useContext
useReducer

Purpose of useEffect
useEffect runs after the component renders.

Syntax
useEffect(() => {

   // callback function

}, [dependencyArray]);

Arguments

1️⃣ Callback function
Code that runs after render.

2️⃣ Dependency array
Controls when the effect runs.

Execution Flow
Component Render
        ↓
DOM Painted
        ↓
useEffect callback runs

6️⃣ Fetching API using useEffect
We fetch data inside useEffect.

Example:

useEffect(() => {
   fetchData();
}, []);
Fetch Function
const fetchData = async () => {

   const data = await fetch(API_URL);

   const json = await data.json();

   setListOfRestaurants(json.data.cards);

};

Why async/await?
fetch() returns a Promise.

We resolve it using:
async/await

7️⃣ CORS Problem
When calling API from another domain:
localhost → swiggy.com

Browser blocks request.

Error:
Blocked by CORS policy

Why CORS Exists
Security mechanism preventing cross-origin requests.

Example:
Origin A → cannot directly access Origin B

Solution (Development Only)
Use CORS Chrome Extension.
This bypasses browser restrictions.

8️⃣ Rendering API Data
Restaurant list stored in state.
const [listOfRestaurants, setListOfRestaurants] = useState([]);

When API data arrives:
setListOfRestaurants(newData)

React automatically:
Re-renders component

9️⃣ Optional Chaining
APIs often return deep nested objects.

Example:
json.data.cards[2].data.data.cards

Safer approach:
json?.data?.cards?.[2]?.data?.data?.cards

Prevents crashes if data is missing.

🔟 Conditional Rendering
Render UI based on conditions.

Example:
if(listOfRestaurants.length === 0){
   return <Shimmer />
}

This shows loading UI until data loads.

11️⃣ Shimmer UI

Instead of showing:
Loading...
We show skeleton cards.

Example:

[ □ ]  [ □ ]  [ □ ]
[ □ ]  [ □ ]  [ □ ]

Benefits:

Better UX
User expects content
Feels faster

Used by:

YouTube
Swiggy
Amazon
Facebook

12️⃣ Why State Variables Are Needed

Example:
let button = "Login"
Changing it will not re-render UI.

React doesn't track normal variables.

State Variables
const [btnName, setBtnName] = useState("Login")

Now React tracks the value.

When state updates
setBtnName("Logout")

React automatically:
Re-renders component

13️⃣ React Rendering Mechanism
Whenever state changes
React re-renders component

Flow:

State change
      ↓
Component re-render
      ↓
New Virtual DOM
      ↓
Compare with old Virtual DOM
      ↓
Update only changed DOM

14️⃣ Reconciliation
React compares:

Old Virtual DOM
vs
New Virtual DOM

Only updates changed parts.

Example:
Login → Logout
Only button changes.
Not entire page.

15️⃣ Search Feature
Search bar added to filter restaurants.

Example:
<input />
<button>Search</button>

16️⃣ Controlled Inputs
Input value controlled by state.

Example:
const [searchText, setSearchText] = useState("");

Bind input:

<input
 value={searchText}
 onChange={(e) => setSearchText(e.target.value)}
/>

Now React controls the input.

17️⃣ Filtering Restaurants
Filtering logic:

const filteredRestaurant = listOfRestaurants.filter((res) =>
 res.info.name.toLowerCase().includes(searchText.toLowerCase())
);

18️⃣ Bug in Search
If we update original data:
listOfRestaurants = filtered data
Next search only runs on filtered results.
Original list lost.

19️⃣ Correct Solution
Maintain two states.

allRestaurants
filteredRestaurants

Example:

const [listOfRestaurants, setListOfRestaurants] = useState([]);
const [filteredRestaurants, setFilteredRestaurants] = useState([]);

Render using:
filteredRestaurants

Filter using:
listOfRestaurants

20️⃣ Important React Rule

⭐ Golden Rule

Whenever state updates
React triggers re-render

21️⃣ React Performance
Even though components re-render many times:
React is still fast

Because:

Virtual DOM
Efficient diffing
Reconciliation
React Fiber

React only updates necessary DOM nodes.

🔑 Key Takeaways

1️⃣ Modern apps use microservices
2️⃣ React UI communicates with backend APIs
3️⃣ Data fetching done using useEffect
4️⃣ fetch() returns Promise
5️⃣ React state change → re-render
6️⃣ Conditional rendering improves UX
7️⃣ Shimmer UI improves loading experience
8️⃣ Controlled inputs use state
9️⃣ Reconciliation updates only necessary DOM
🔟 Separate original data and filtered data
