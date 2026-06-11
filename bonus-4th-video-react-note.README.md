✨ Pattern

React Performance Optimization + useMemo + Memoization + Expensive Computations + React Re-renders + useRef + let vs State vs Ref + JavaScript Fundamentals Behind React

💡 Idea

This episode teaches a very important lesson:

Not Every Value
Should Be State

And:

Not Every Re-render
Should Recalculate Everything

Akshay introduces two major concepts:

useMemo
    ↓
Optimize Expensive Calculations

and

useRef
    ↓
Store Persistent Values
Without Re-rendering

The real goal of the episode is to teach:

Performance
+
Re-rendering
+
React Internals
+
JavaScript Fundamentals
🔥 Episode Flow
1. React Documentation
        ↓
2. Important React Hooks
        ↓
3. Why Components Re-render
        ↓
4. Expensive Calculations
        ↓
5. Nth Prime Example
        ↓
6. Performance Problems
        ↓
7. useMemo
        ↓
8. Memoization
        ↓
9. Dependency Arrays
        ↓
10. useCallback Introduction
        ↓
11. useRef Introduction
        ↓
12. let Variable Behavior
        ↓
13. State Variable Behavior
        ↓
14. React Re-render Cycle
        ↓
15. Ref Object Internals
        ↓
16. Ref Persistence
        ↓
17. useRef Real-world Example
        ↓
18. Interval Storage
        ↓
19. Mount vs Re-render
        ↓
20. Final Comparison
📘 Chapter 1: React Documentation

Akshay starts by emphasizing:

Official React Docs
=
Source Of Truth

Many developers learn React from:

Blogs
YouTube Videos
Articles

But eventually:

React Docs

should become your primary source.

Engineering Lesson

When confused:

Docs
>
Tutorials
📘 Chapter 2: Most Important React Hooks

Akshay discusses hooks commonly used in real projects.

Most Frequently Used
useState
useEffect

These are the foundation of React.

Other hooks:

useMemo
useCallback
useRef
useContext

are used when specific problems arise.

📘 Chapter 3: Why Components Re-render

Before understanding optimization:

Need to understand:

Re-rendering

A React component re-renders when:

State Changes
setState(...)
Parent Re-renders
Parent Updated
↓
Child Re-renders
Props Change
New Props
↓
Re-render

This is the foundation of the episode.

📘 Chapter 4: Performance Problem

Akshay creates:

Nth Prime Number Calculator

Purpose:

Simulate Heavy Computation

Example:

Input Number
      ↓
Calculate Nth Prime

Prime calculation is intentionally:

CPU Intensive
Problem

Whenever component re-renders:

Prime Calculation
Runs Again

Even when:

Calculation Not Needed
📘 Chapter 5: Theme Toggle Example

Two states:

number

and

isDarkTheme

Suppose:

Theme Changes

Question:

Should prime number recalculate?

No

But React re-renders whole component.

Therefore:

Prime Calculation Runs Again

Result:

Slow UI
📘 Chapter 6: Understanding useMemo ⭐⭐⭐

This is the main concept.

What Is useMemo?
Memoization

means:

Store Result
Reuse Result

instead of recalculating.

Syntax:

const value = useMemo(
   () => expensiveCalculation(),
   [dependency]
);
How It Works

First Render:

Run Calculation
Store Result

Future Re-renders:

Use Cached Result

Unless:

Dependency Changes
Flow

Without useMemo:

Render
 ↓
Calculation
 ↓
Render
 ↓
Calculation
 ↓
Render
 ↓
Calculation

With useMemo:

Render
 ↓
Calculation
 ↓
Cache Result
 ↓
Render
 ↓
Use Cache
📘 Chapter 7: Dependency Array

Critical concept.

Example:

useMemo(
  () => findNthPrime(num),
  [num]
);

Meaning:

Only Recalculate
When num Changes

If:

Theme Changes

Result:

Use Cached Prime

No recalculation.

🎯 Interview Question

What happens if dependency array changes?

Answer:

Memoized Value
Gets Recomputed
📘 Chapter 8: Benefits of useMemo
Performance
Less CPU Work
Better UX
Faster UI
Avoid Browser Freezing
Heavy Logic Runs Less Often
Better Scalability
Large Components
Stay Responsive
⚠️ Important Warning

Akshay indirectly teaches:

Don't Use useMemo Everywhere

Only when:

Expensive Calculation

exists.

Otherwise:

Extra Complexity
📘 Chapter 9: Alternative Optimizations

useMemo is not the only solution.

Other options:

Split Components
Separate Logic
State Isolation
Move State Down
Better Architecture
Reduce Re-renders
Engineering Lesson

Optimization starts with:

Good Design

not hooks.

📘 Chapter 10: useCallback Introduction

Akshay briefly introduces:

useCallback()

Relationship:

useMemo
Caches Value
useCallback
Caches Function

Simple Interview Answer:

useMemo → Value
useCallback → Function
📘 Chapter 11: useRef Introduction

Now begins the second major topic.

Definition:

Store Value
Without Triggering Re-render

And:

Persist Value
Across Re-renders

This definition becomes clear only after understanding:

let
state
ref
📘 Chapter 12: Normal Variable (let)

Example:

let x = 0;

Button:

x++;

Observation:

Value Changes

But:

UI Does Not Update

Why?

No Re-render
Important Lesson

Normal variables:

Can Change

but

React Doesn't Track Them
📘 Chapter 13: State Variable

Example:

const [y,setY]

Update:

setY(y + 1)

Result:

Value Changes
      ↓
Re-render Happens
      ↓
UI Updates

State is tracked by React.

📘 Chapter 14: Biggest JavaScript Lesson ⭐⭐⭐

Akshay goes very deep here.

Question:

Why does:

let x

reset after re-render?

Answer:

Because:

Component
=
Function

When React re-renders:

Function Executes Again

Which means:

New Execution Context

Which means:

New Memory Space

Therefore:

All let Variables
Are Recreated

Huge JavaScript revision.

Topics touched:

Execution Context
Call Stack
Memory Creation Phase
Function Invocation
Thread Of Execution
📘 Chapter 15: Why State Persists

Question:

Why Doesn't State Reset?

Answer:

React stores state separately.

React preserves:

State Values

between renders.

Unlike:

let Variables
📘 Chapter 16: Understanding useRef Internals ⭐⭐⭐

Syntax:

const ref = useRef(0);

Important:

Many developers think:

ref = 0

Wrong.

Actual structure:

{
   current: 0
}

React returns:

Object

with:

current

property.

Reading Value
ref.current
Updating Value
ref.current++

No setter needed.

📘 Chapter 17: Ref Behavior

When:

ref.current++

Result:

Value Changes

But:

No Re-render

Same as:

let

At first glance.

📘 Chapter 18: The Biggest Difference
let Variable
Changes
No Re-render
Resets Later
Ref Variable
Changes
No Re-render
Persists Later

This is why useRef exists.

📘 Chapter 19: let vs State vs Ref ⭐⭐⭐

The most important table of the episode.

Feature	let	state	ref
Value Changes	✅	✅	✅
Triggers Re-render	❌	✅	❌
Persists Across Re-renders	❌	✅	✅
React Tracks It	❌	✅	✅

Memorize this.

Interviewers love this comparison.

📘 Chapter 20: Practical useRef Example

Akshay uses:

setInterval()

Need:

Store Interval ID

Need access later:

clearInterval()

Question:

Do we need UI update?

No

Question:

Need persistence?

Yes

Perfect:

useRef()
📘 Chapter 21: Interval Cleanup Revision

Topics revisited:

setInterval()
clearInterval()

And:

useEffect()

cleanup.

Example:

return () => {
  clearInterval(id);
}

Prevents:

Memory Leaks
📘 Chapter 22: Mount vs Re-render

Very important distinction.

Ref Persists Across
Re-render
Ref Does NOT Persist Across
Unmount
 ↓
Mount

Because:

Whole Component
Gets Destroyed

Same applies to local state.

📘 Chapter 23: Real Understanding Of useRef

Akshay repeatedly emphasizes:

Need Value
      +
Need Persistence
      +
Don't Need Re-render

Use:

useRef()

This is the easiest way to remember it.

🛠 Practical Examples
useMemo
Number Changes
      ↓
Prime Recalculates
Theme Changes
      ↓
Prime Uses Cache
let Variable
x++
 ↓
Changes
 ↓
Re-render
 ↓
Reset
State Variable
setState
 ↓
Re-render
 ↓
Preserved
Ref Variable
ref.current++
 ↓
No Re-render
 ↓
Preserved
⚠️ Tricky Points
useMemo caches values, not functions.
useCallback caches functions.
useRef returns an object.
Value is inside .current.
Ref updates don't trigger re-renders.
let variables reset after re-render.
Ref persists across re-renders, not remounts.
Component re-render = function executes again.
❌ Mistakes To Avoid

❌ Using useMemo everywhere.

❌ Thinking useRef behaves like useState.

❌ Forgetting .current.

❌ Using let when persistence is required.

❌ Using state when UI doesn't need updating.

❌ Ignoring cleanup of intervals.

❌ Forgetting React components are just JavaScript functions.

🎯 Important Interview Questions
useMemo
What is memoization?
Why use useMemo?
When should you use useMemo?
What happens when dependencies change?
useCallback
Difference between useMemo and useCallback?
useRef
What is useRef?
Why does useRef not trigger re-render?
Why is value stored in .current?
When would you use useRef?
React Internals
Why do components re-render?
Why do let variables reset?
Why does state persist?
Difference between re-render and remount?
JavaScript
What is an execution context?
How does function invocation affect variables?
⭐ Episode Rating

10/10

One of the deepest React fundamentals episodes.

💼 Interview Importance

10/10

Contains:

useMemo
useCallback
useRef
React Re-renders
Memoization
React Internals
JavaScript Fundamentals

These are extremely common interview topics.

🚀 Job Readiness Impact

10/10

After this episode, you understand:

✅ React Re-rendering
✅ Performance Optimization
✅ Memoization
✅ useMemo
✅ useCallback Basics
✅ useRef
✅ React Internals
✅ JavaScript Execution Contexts

This episode is where many React concepts finally "click" because Akshay connects React hooks back to core JavaScript fundamentals.