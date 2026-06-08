✨ Pattern

Machine Coding Interviews + YouTube Clone Architecture + Redux State Management + React Router + YouTube Data API + Dynamic Routing + Video Embedding + Component Design

💡 Idea

This episode is not actually about building YouTube.

It is about:

How Senior Engineers Think During
Machine Coding Interviews

Akshay is teaching:

Requirements
      ↓
Planning
      ↓
Architecture
      ↓
State Management
      ↓
Routing
      ↓
API Integration
      ↓
Scalable Design

The YouTube Clone is just the medium.

The real lesson is:

How to approach and execute a machine coding round professionally.

🔥 Episode Flow
1. Machine Coding Strategy
         ↓
2. Requirement Clarification
         ↓
3. YouTube HLD & LLD
         ↓
4. App Architecture
         ↓
5. Header Creation
         ↓
6. Sidebar Creation
         ↓
7. Sidebar Toggle using Redux
         ↓
8. Button List Architecture
         ↓
9. YouTube API Integration
         ↓
10. Video Cards
         ↓
11. Dynamic Video Rendering
         ↓
12. React Router Setup
         ↓
13. Watch Page
         ↓
14. Query Parameters
         ↓
15. Dynamic Video Embedding
         ↓
16. Interview Practice Strategy
📘 Chapter 1: Machine Coding Interview Mindset

One of the biggest lessons of the episode.

Most candidates immediately start coding.

Wrong approach.

Correct approach:

Requirement Gathering
         ↓
Feature Identification
         ↓
Architecture Planning
         ↓
Low-Level Design
         ↓
Implementation

Akshay repeatedly emphasizes:

Do Not Jump Into Coding

First ask:

What Features?
Search
Sidebar
Video List
Watch Page
Comments
Suggestions

Then:

What Tech Stack?
React
Redux
Tailwind
React Router

Then:

Architecture?
Header
Sidebar
Body
MainContainer
VideoContainer
WatchPage
Interview Lesson

Good developers write code.

Great developers:

Think Before Writing Code
📘 Chapter 2: High-Level Design (HLD)

Before coding:

Akshay designs:

YouTube
│
├── Header
│
├── Sidebar
│
└── Body
      │
      ├── MainContainer
      │
      └── WatchPage

This is HLD.

Question:

Why design first?

Answer:

Large Applications
Need Structure

Without structure:

Messy Components
Messy State
Messy Logic
📘 Chapter 3: Low-Level Design (LLD)

After HLD:

Break into components.

Header
│
├── Hamburger
├── Logo
└── Search Bar
Sidebar
│
├── Home
├── Shorts
├── Subscriptions
└── Categories
MainContainer
│
├── ButtonList
└── VideoContainer
VideoContainer
│
└── VideoCard

This is LLD.

📘 Chapter 4: CRA vs Parcel During Interviews

Interesting lesson.

Akshay deliberately uses:

Create React App

instead of configuring:

Webpack
Parcel
Vite

Why?

Machine Coding Goal:

Build Features

NOT:

Configure Bundlers

Interviewers care about:

Problem Solving
Architecture
React Skills

More than:

Webpack Config
📘 Chapter 5: Sidebar Design

Sidebar contains sections:

Home
Shorts
Videos
Live
Subscriptions
├── Music
├── Sports
├── Gaming
└── Movies
Watch Later

Akshay intentionally keeps it simple.

Reason:

Functionality First
Important Interview Advice

Do NOT spend:

20 Minutes
Making Text Bold

during interviews.

Instead spend time on:

Features
Logic
Architecture
📘 Chapter 6: Sidebar Collapse Problem

Feature:

Hamburger Click
       ↓
Collapse Sidebar

Question:

Where should state live?

Options:

Header

or

Body

or

Global Store

Akshay chooses:

Redux Store

Why?

Because:

Sidebar State
Can Affect
Multiple Pages

Thinking:

Small App Thinking ❌

Large App Thinking ✅
📘 Chapter 7: Redux Setup

Full Redux Flow Revision.

Install:

npm i @reduxjs/toolkit
npm i react-redux

Create:

Store

Create:

appSlice

Initial State:

{
  isMenuOpen: true
}

Reducer:

toggleMenu()

Logic:

state.isMenuOpen =
!state.isMenuOpen

Store Setup Flow:

Install Redux
      ↓
Create Store
      ↓
Create Slice
      ↓
Provide Store
      ↓
Subscribe Components
📘 Chapter 8: Dispatch Flow

Header:

Hamburger Click

Action:

dispatch(toggleMenu())

Flow:

Click
   ↓
Dispatch
   ↓
Reducer
   ↓
Store Update
   ↓
Subscribed Components Update

One of the best Redux revision examples.

📘 Chapter 9: Subscription Flow

Sidebar needs Redux data.

Use:

useSelector()

Important Lesson:

Subscribe only to:

store.app.isMenuOpen

NOT:

store

Why?

Performance.

Akshay revisits a major Redux principle:

Subscribe To
Only Required Data
📘 Chapter 10: Early Return Pattern

Sidebar Logic:

if (!isMenuOpen)
    return null;

Known as:

Early Return Pattern

Benefits:

Cleaner
Readable
Simple

Interviewers like this style.

📘 Chapter 11: Why Redux Impresses Interviewers

Akshay explicitly explains:

Instead of:

useState()

Use:

Redux Store

Because it shows:

Scalable Thinking

Explain to interviewer:

Action
  ↓
Reducer
  ↓
Store Update
  ↓
Subscription
  ↓
UI Update

This demonstrates React maturity.

📘 Chapter 12: Button List Architecture

Button List:

All
Gaming
Live
Music
News
Cricket
Cooking

Wrong Approach:

<button>All</button>
<button>Gaming</button>
<button>News</button>

Better:

<Button name="All" />

Props:

name

Then render dynamically.

Engineering Lesson
Make Components Reusable

Not:

One Component Per Button
📘 Chapter 13: YouTube API Integration

Question:

Hardcoded Videos?

OR

Live API?

Akshay chooses:

Live YouTube API

Reason:

Real-world experience.

API Used:

YouTube Data API v3

Fetch:

Most Popular Videos
Getting API Key

Flow:

Google Cloud
      ↓
Credentials
      ↓
API Key

Store:

constants.js

Initially.

Production:

.env
📘 Chapter 14: Axios vs Fetch

Interesting discussion.

Many students suggest:

Axios

Akshay's view:

Fetch Works Fine

Important lesson:

Don't Add Libraries
Without Need

If Fetch solves the problem:

Use Fetch
📘 Chapter 15: VideoContainer Architecture

API Flow:

useEffect
      ↓
fetch()
      ↓
json()
      ↓
setVideos()
      ↓
Reconciliation
      ↓
UI Update

State:

const [videos, setVideos]

Why state?

Because:

State Change
Triggers Re-render
📘 Chapter 16: VideoCard Design

Akshay follows:

Make It Work For One
      ↓
Then Scale

This is one of the best coding lessons.

Wrong:

videos.map(...)

immediately.

Correct:

Pass First Video
Build One Card
Verify
Then Map

Benefits:

Easy Debugging
Less Complexity
Less Panic
📘 Chapter 17: VideoCard Data Structure

Data extracted:

snippet
statistics

Inside snippet:

title
channelTitle
thumbnails

Inside statistics:

viewCount

Card UI:

Thumbnail
Title
Channel
Views
📘 Chapter 18: Rendering Video Cards

After one card works:

videos.map(...)

Key:

video.id

Result:

50 Video Cards

rendered dynamically.

📘 Chapter 19: Indian Trending Videos

Interesting customization.

Default:

US Trending

Modified:

regionCode=IN

Result:

Indian Trending Videos

Lesson:

APIs are configurable.

📘 Chapter 20: React Router Architecture

One of the biggest concepts.

Question:

What changes on Watch Page?

Header? ❌
Sidebar? ❌
Main Content? ✅

Therefore:

Body
│
├── Sidebar
│
└── Outlet

Outlet changes.

Everything else remains.

This is excellent architecture thinking.

📘 Chapter 21: Nested Routing

Structure:

/
  ↓
MainContainer
/Watch
  ↓
WatchPage

Router:

createBrowserRouter()

Render:

RouterProvider

Children:

Outlet

Important interview topic.

📘 Chapter 22: Making Cards Clickable

Wrap:

<Link />

Generate URL:

/watch?v=VIDEO_ID

Exactly like YouTube.

Lesson:

Dynamic Routing
📘 Chapter 23: Sidebar Auto Collapse

YouTube Behavior:

Open Watch Page
       ↓
Collapse Sidebar

Question:

Can toggleMenu work?

No.

Because:

Toggle
May Open
May Close

Need:

closeMenu()

Reducer:

state.isMenuOpen = false;

Excellent state-management decision.

📘 Chapter 24: Query Parameters

Important React Router topic.

Initial Attempt:

useParams()

Problem:

Not Route Params

Actual:

Query Params

Correct Hook:

useSearchParams()

Read:

searchParams.get("v")

Returns:

Video ID

Interview Favorite Topic.

📘 Chapter 25: Video Embedding

Use:

<iframe />

Source:

YouTube Embed URL
+
Video ID

Flow:

URL
    ↓
Extract Video ID
    ↓
Build Embed URL
    ↓
Render Video

Result:

Dynamic Watch Page.

📘 Chapter 26: Future Features

Akshay intentionally leaves:

Comments
Comments API
Suggestions
Related Videos
Video Metadata
Title
Channel
Subscribers

As Homework.

This teaches:

How To Explore APIs
📘 Chapter 27: Biggest Lesson Of The Episode

The most important takeaway:

Practice Like A Real Interview

Akshay's Advice:

Record Yourself
Screen Recording ON
Speak While Coding
Explain Every Decision
Time Yourself
2 Hour Limit
Do Planning
5 Minutes
Requirement Clarification
Think Aloud
Like An Interview

This is probably the most valuable career advice in the entire episode.

🛠 Practical Examples
Redux Flow
Click
 ↓
Dispatch
 ↓
Reducer
 ↓
Store
 ↓
UI
Watch Page Flow
Video Card
      ↓
Link Click
      ↓
URL Changes
      ↓
Read Query Param
      ↓
Embed Video
API Flow
YouTube API
      ↓
Fetch
      ↓
State
      ↓
Map
      ↓
Video Cards
⚠️ Tricky Points
useParams() ≠ useSearchParams()
Build one card first, then map.
Redux is better than local state for global sidebar behavior.
Subscribe only to required state.
Toggle and Close are different actions.
Fetch is perfectly acceptable.
Routing should only rerender changing sections.
❌ Mistakes To Avoid
Starting coding without planning.
Spending interview time on CSS.
Mapping before one card works.
Subscribing to entire Redux store.
Using toggle when explicit close is needed.
Hardcoding videos.
Ignoring API documentation.
Not explaining code during interviews.
🎯 Important Interview Questions
React
Why use Redux for sidebar state?
What is useSelector?
What is useDispatch?
Explain reconciliation.
What is the Early Return Pattern?
Routing
useParams vs useSearchParams?
What is Outlet?
What is nested routing?
Why use Link instead of anchor tags?
API
Fetch vs Axios?
How do you integrate YouTube APIs?
Why use useEffect for API calls?
Machine Coding
How do you approach a machine coding round?
Why is planning important?
How do you structure a large React app?
⭐ Episode Rating

10/10

Not because of YouTube.

Because it teaches:

Machine Coding
React Architecture
Redux
Routing
API Integration
Interview Thinking

all in one project.

💼 Interview Importance

10/10

This episode is practically a machine coding interview workshop.

🚀 Job Readiness Impact

9.5/10

After fully understanding this episode, you gain experience with:

✅ Component Design
✅ Redux Architecture
✅ Routing Architecture
✅ API Integration
✅ Query Parameters
✅ Dynamic Rendering
✅ Scalable State Management
✅ Machine Coding Strategy

Most importantly, you learn how an experienced frontend engineer approaches building a feature from scratch under interview conditions.
