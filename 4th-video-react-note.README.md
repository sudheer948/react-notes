Namaste React – Episode 04 Notes
--------------------------------
🚀 Namaste React — Episode 4
🗣️ Talk is Cheap, Show Me The Code

🎯 Episode Goal
This episode marks the start of real React coding.

Until now:
Episode 1 → React Basics
Episode 2 → Setup + Tools
Episode 3 → Foundations

From this episode:
👉 We start building a real-world project

Project we build in this course:
🍔 Food Ordering App
(similar to Swiggy / Zomato)

Example features:

Restaurant list
Search
Cards
Cart
Navigation

🧠 Important Development Principle

Before writing code:
⚠️ Always do planning

Senior engineers always follow:

1️⃣ Planning
2️⃣ Design
3️⃣ Components
4️⃣ Coding

If planning is good → coding becomes easy.

✏️ Step 1 — UI Planning (Wireframe)
First we draw a basic layout of the app.

-----------------------------------------
|            Header           		 |
|  Logo        Nav Items     	         |
-----------------------------------------

|            Body             		 |
|  Search Bar                            |
|                                        |
|  Restaurant Cards                      |
|  Restaurant Cards                      |
|  Restaurant Cards                      |
|                                        |
-----------------------------------------

|            Footer                      |
|  Links | Contact | Copyright 		 |
-----------------------------------------

🧩 Step 2 — Component Planning
React apps are built using components.

Component structure:

AppLayout
   |
   |---- Header
   |       |---- Logo
   |       |---- NavItems
   |
   |---- Body
   |       |---- Search
   |       |---- RestaurantContainer
   |               |---- RestaurantCard
   |
   |---- Footer

This approach is called:
🧠 Component Based Architecture

⚙️ Step 3 — Create App Layout Component

A React component is simply:
📌 A JavaScript function that returns JSX

Example:

const AppLayout = () => {
  return (
    <div className="app">
      <Header />
      <Body />
      <Footer />
    </div>
  );
};

🧩 Header Component

Header contains:
Logo
Navigation Links

const Header = () => {
  return (
    <div className="header">
      
      <div className="logo-container">
        <img className="logo" src="logo-url"/>
      </div>

      <div className="nav-items">
        <ul>
          <li>Home</li>
          <li>About</li>
          <li>Contact</li>
          <li>Cart</li>
        </ul>
      </div>

    </div>
  );
};

🎨 Basic CSS Example

Example styling:

.header {
  display: flex;
  justify-content: space-between;
  border: 1px solid black;
}

.logo {
  width: 200px;
}

.nav-items ul {
  display: flex;
  list-style-type: none;
}

.nav-items ul li {
  padding: 10px;
  margin: 10px;
}

⚡ Parcel Feature — HMR
Parcel automatically refreshes the page.

This is called:
🔥 Hot Module Replacement (HMR)

Benefit:
Faster development
Instant UI updates

🧩 Body Component

Body contains:
Search
Restaurant Container

const Body = () => {
  return (
    <div className="body">
      
      <div className="search">
        Search
      </div>

      <div className="rest-container">
        <RestaurantCard />
      </div>

    </div>
  );
};

🍔 Restaurant Card Component
Each restaurant is displayed using a card component.

const RestaurantCard = () => {
  return (
    <div className="res-card">
      <img className="res-logo" src="image-url" />

      <h3>Meghana Foods</h3>

      <h4>Biryani, North Indian</h4>

      <h4>4.4 Stars</h4>

      <h4>38 Minutes</h4>
    </div>
  );
};

🎨 Styling the Card

.res-card {
  width: 200px;
  padding: 5px;
}

.res-card:hover {
  border: 1px solid black;
  cursor: pointer;
}

.res-logo {
  width: 100%;
}

🧠 Why Create Separate Components?
Because components are reusable.

Example:
Instead of repeating:

Restaurant Card
Restaurant Card
Restaurant Card
Restaurant Card

We create one component and reuse it.

⚡ Inline Styling in React
React supports inline styles.

Important rule:
⚠️ Style must be JavaScript object

Example:
<div style={{ backgroundColor: "lightgray" }}>

Why two {}?

First {} → JavaScript inside JSX
Second {} → JavaScript object

style = { { backgroundColor: "gray" } }

🎨 Ways to Add CSS in React

3 ways:
1️⃣ External CSS file
className="res-card"

2️⃣ Inline CSS
style={{backgroundColor:"gray"}}

3️⃣ CSS Frameworks
Examples:
Tailwind
Material UI
Bootstrap

📦 Creating Multiple Restaurant Cards

Example:

<RestaurantCard />
<RestaurantCard />
<RestaurantCard />
<RestaurantCard />

But this is not scalable.
Instead we use dynamic data.

🧠 Dynamic Data Problem

Current card is hardcoded:

Meghana Foods
Biryani
38 minutes

But real apps need:

Meghana Foods
KFC
McDonalds
Pizza Hut

Solution:
👉 Props

📌 What Are Props?
Props = Properties
Props allow us to pass data into components.

Important idea:
🧠 Passing props to component
Passing arguments to function

📦 Passing Props Example
<RestaurantCard
  resName="KFC"
  cuisine="Burger"
/>

Component receives props:

const RestaurantCard = (props) => {

  return (
    <div>
      <h3>{props.resName}</h3>
      <h4>{props.cuisine}</h4>
    </div>
  );
};

✨ Destructuring Props

Instead of:

props.resName
props.cuisine

We can destructure:
const RestaurantCard = ({ resName, cuisine }) => {

Cleaner code.
🌍 Real World Data Comes From APIs

Backend usually sends data as:
📦 JSON

Example structure:

{
  "data": {
     "name": "KFC",
     "avgRating": 4.3,
     "cuisines": ["Burger", "Fast Food"],
     "costForTwo": 40000
  }
}

🧠 Config Driven UI (Very Important Concept)

Large companies use:
⚙️ Config Driven UI

Meaning:
UI is controlled by data from backend.

Example:
Different cities show different UI.

Delhi → different offers
Mumbai → different offers
Bangalore → different offers

Backend sends config JSON
Frontend renders UI based on that data.

Used by:

Amazon
Flipkart
Swiggy
Uber
Paytm

Important for:
🎯 System Design Interviews
🧠 UI Layer vs Data Layer

Modern Frontend Apps have two layers.

UI Layer

Visual components

Header
Cards
Search
Buttons

Data Layer

API
JSON
Backend Data

A good frontend engineer must understand both.

📦 Restaurant Data Example

Instead of passing many props:

name
rating
deliveryTime
image

We pass a single object
<RestaurantCard resData={restaurantObj} />

Inside component:
const RestaurantCard = ({ resData }) => {

🧩 Using Data

Example:
<h3>{resData.data.name}</h3>
<h4>{resData.data.cuisines.join(", ")}</h4>
<h4>{resData.data.avgRating} stars</h4>

<h4>
₹ {resData.data.costForTwo / 100} for two
</h4>

🧠 Why .join()?
Cuisine is an array:

["Biryani","North Indian"]

To display:
Biryani, North Indian

We use:
array.join(", ")

🔁 Rendering Many Restaurants

Real API returns:

[
  {restaurant1},
  {restaurant2},
  {restaurant3}
]

Instead of writing many components manually:

<RestaurantCard />
<RestaurantCard />
<RestaurantCard />

We use map()

🔥 map() Rendering Pattern
restList.map((restaurant) => (
  <RestaurantCard resData={restaurant}/>
))

This creates cards dynamically.

⚠️ React Key Warning

When rendering lists:
React shows warning:
Each child should have a unique key

Solution:

<RestaurantCard
   key={restaurant.data.id}
   resData={restaurant}
/>

🧠 Why React Needs Keys

Keys help React:
⚡ Optimize Rendering

Without key:
React re-renders all items

With key:
React updates only changed items

Example:
Old list
A B C

New list
X A B C

With keys → React inserts only X
Without keys → React re-renders everything.

⚠️ Index As Key

You can do:
key={index}

But React docs say:
❌ Not recommended

Better:
key={restaurant.id}

Rule:
Unique ID > Index > No Key

🎯 Major Concepts Covered

This episode taught:

✅ Component planning
✅ Functional components
✅ JSX rendering
✅ CSS in React
✅ Inline styles
✅ Props
✅ Destructuring props
✅ Dynamic data
✅ JSON APIs
✅ Config Driven UI
✅ map() rendering
✅ Keys in React

Huge episode for React fundamentals.

🧠 Homework (Instructor Advice)

Practice everything:

1️⃣ Build the header
2️⃣ Build restaurant card
3️⃣ Add dynamic props
4️⃣ Render using map()
5️⃣ Add keys

Without practice:
❌ React will not stick.

⏭️ Next Episode

Next episode will teach:
🌐 Fetching data from API
Instead of hardcoded data.

Using:

fetch()
useEffect()
state

We will build a real production style app.

