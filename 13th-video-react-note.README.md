Namaste React 🚀 Episode 13 — Testing (Complete Notes: Part 1 + Part 2)
✨ Pattern

Pattern: Unit Testing + Integration Testing + Mocking + User Event Simulation

💡 Idea

Testing ensures our React app works correctly without manually checking everything.

We mainly test:

Individual functions → Unit Testing
Individual components → Component Testing
Full feature flows (multiple components together) → Integration Testing
Entire app journey → End-to-End Testing

In this episode, we focus mainly on:

Unit Testing + Integration Testing

using:

Jest
React Testing Library (RTL)
JSDOM
Mock Functions
Mock APIs
Fire Events
Coverage Reports

This is one of the most important real-world React interview topics.

📘 Detailed Interview-Friendly Notes
1. Types of Testing
1. Unit Testing

Testing a small isolated unit like:

function
helper
one small component

Example:

sum(a, b)

Test only this function.

2. Integration Testing

Testing how multiple components work together.

Example:

Search Feature

involves:

Input box
Button
API call
Restaurant cards
State updates

All together = Integration Testing

3. End-to-End Testing (E2E)

Testing full user journey.

Example:

Login → Add to Cart → Payment → Order Success

Tools:

Cypress
Playwright

(Not covered deeply here)

2. Setting Up Testing

Install:

npm install --save-dev @testing-library/react
npm install --save-dev jest
npm install --save-dev babel-jest
npm install --save-dev @babel/preset-env
npm install --save-dev @babel/preset-react
npm install --save-dev @testing-library/jest-dom
npm install --save-dev jest-environment-jsdom
Babel Config
module.exports = {
  presets: [
    ["@babel/preset-env", {
      targets: {
        node: "current"
      }
    }],
    ["@babel/preset-react", {
      runtime: "automatic"
    }]
  ]
};
Parcel Conflict Fix

Remove Parcel’s Babel config:

.parcelrc

if needed.

Because:

Parcel + Jest Babel conflict

can happen.

Jest Config
npm init jest@latest

Recommended modern setup.

(Not npx jest --init)

3. First Unit Test (sum function)
sum.js
export const sum = (a, b) => {
  return a + b;
};
sum.test.js
import { sum } from "../sum";

test("should calculate sum correctly", () => {
  const result = sum(3, 4);

  expect(result).toBe(7);
});
4. Test File Naming

Use:

Component.test.js

Example:

Header.test.js
Contact.test.js
Body.test.js

Jest automatically detects these.

5. Rendering Component in Test
import { render } from "@testing-library/react";
import Header from "../Header";

test("should render Header", () => {
  render(<Header />);
});

This checks if rendering crashes or not.

6. BrowserRouter Required for <Link />

If component contains:

<Link />

test will fail unless wrapped in:

<BrowserRouter>
Correct Way
render(
  <BrowserRouter>
    <Header />
  </BrowserRouter>
);
7. screen.getByRole() Best Practice

Preferred way:

screen.getByRole()

Example:

const loginButton = screen.getByRole("button", {
  name: "Login"
});

Why?

Because it is:

semantic
accessible
cleaner
interview preferred
8. getByText() Alternative

Can also use:

screen.getByText("Login")

But:

Prefer getByRole() first
9. toBeInTheDocument()

Used for assertion:

expect(loginButton).toBeInTheDocument();

Need import:

import "@testing-library/jest-dom";

Without this:

toBeInTheDocument is not a function
10. Fire Events (User Interaction)

To simulate click:

fireEvent.click(button)

Example:

fireEvent.click(loginButton)
11. Testing Login → Logout
it("should change Login to Logout", () => {
  render(<Header />);

  const loginButton = screen.getByRole("button", {
    name: "Login"
  });

  fireEvent.click(loginButton);

  const logoutButton = screen.getByRole("button", {
    name: "Logout"
  });

  expect(logoutButton).toBeInTheDocument();
});

Very important interview question.

12. Regex in Testing

Instead of exact string:

screen.getByText("Cart - 0 items")

use regex:

screen.getByText(/Cart/)

Why?

Because count may change:

0
1
2

Regex makes tests flexible.

13. Testing Components with Props

Example:

<RestaurantCard resData={restaurant.info} />

This requires:

Mock Props Data
14. Mock JSON Data

Create:

mocks/

File:

resCardMock.json

Paste copied restaurant object from browser console.

Import
import MOCK_DATA from "../mocks/resCardMock.json";
Test
render(
  <RestaurantCard resData={MOCK_DATA} />
);
15. Testing with Mock Props

Example:

const name = screen.getByText(
  "Leon's Burgers & Wings"
);

expect(name).toBeInTheDocument();
16. Higher Order Component Testing

Example:

withPromotedLabel(RestaurantCard)

Need to test:

Promoted Label appears correctly

Important HOC interview question.

(Homework from course)

17. Why fetch Fails in Jest

Error:

fetch is not defined

Why?

Because Jest uses:

JSDOM

not real browser.

And:

fetch = Browser API

NOT JavaScript feature.

Very important concept.

18. Mocking Fetch

We create fake fetch:

global.fetch = jest.fn(() =>
  Promise.resolve({
    json: () =>
      Promise.resolve(MOCK_DATA),
  })
);
Why This Exact Structure?

Because real fetch works like:

fetch()
→ Promise
→ response.json()
→ Promise
→ actual data

We must copy same structure.

This is asked in interviews.

19. act() for Async Updates

When component uses:

fetch
useEffect
state updates

Use:

await act(async () => {
  render(<Body />);
});
Import
import { act } from "react-dom/test-utils";

Without act():

React gives warning.

Very important.

20. data-testid

When:

getByRole()

doesn’t work

use:

data-testid
Component
<input data-testid="searchInput" />
Test
screen.getByTestId("searchInput")

Reliable fallback.

21. Change Input Value

Simulate typing:

fireEvent.change(searchInput, {
  target: {
    value: "burger",
  },
});

Because browser normally gives:

e.target.value

We manually fake it.

22. Search Feature Integration Test

Flow:

Initial → 20 cards
Type → burger
Click → Search
Final → 4 cards
Test Logic
expect(cardsBefore.length).toBe(20);

fireEvent.change(input, {
  target: { value: "burger" }
});

fireEvent.click(searchButton);

expect(cardsAfter.length).toBe(4);

This is true Integration Testing.

Very strong interview example.

23. Top Rated Filter Test

Flow:

Initial → 20 cards
Click → Top Rated
Final → 13 cards

Test:

fireEvent.click(topRatedButton);

expect(cardsAfter.length).toBe(13);
24. Redux Store Testing (Cart)

Advanced interview-level topic.

Test flow:

Restaurant Menu
→ Click Add
→ Header Cart Updates
→ Cart Page Updates
→ Clear Cart

This is real production testing.

25. Provider Required for Redux

Wrap with:

<Provider store={appStore}>

Otherwise:

React Redux error

comes.

26. Full Wrapper Needed

Final testing wrapper:

render(
  <BrowserRouter>
    <Provider store={appStore}>
      <Header />
      <RestaurantMenu />
      <Cart />
    </Provider>
  </BrowserRouter>
);

Very important.

27. Add to Cart Test

Flow:

Click Add
→ Cart - 1 item
→ Click again
→ Cart - 2 items

Test:

expect(
  screen.getByText("Cart - 2 items")
).toBeInTheDocument();
28. Clear Cart Test

Flow:

Click Clear Cart
→ Cart Empty

Test:

expect(
  screen.getByText("Cart is Empty")
).toBeInTheDocument();
29. Watch Mode

Avoid running:

npm run test

again and again.

Use:

"watch-test": "jest --watch"

Then run:

npm run watch-test

Auto reruns tests.

Huge productivity boost.

30. beforeAll / beforeEach / afterEach / afterAll

Useful helper functions.

beforeAll

Runs once before all tests

beforeAll(() => {})
beforeEach

Runs before every test

beforeEach(() => {})
afterEach

Runs after every test

afterEach(() => {})
afterAll

Runs once after all tests

afterAll(() => {})

Used for:

setup
cleanup
logs
reset state
31. Coverage Report

Generate:

npm test -- --coverage

This creates:

coverage/

folder.

32. Open HTML Coverage Report

Open:

coverage/lcov-report/index.html

using browser.

It shows:

tested lines
untested lines
missing branches

Very useful for improving quality.

33. Target Coverage

Good companies expect:

80–90%+

For this project:

Aim for 100%

Because project is small.

🛠 Practical Examples

Real interview features:

Login / Logout test
Search feature test
Filter button test
Add to Cart test
Redux update test
API mocking
Router testing

These are highly practical.

⚠️ Tricky Points

Most students fail here:

forgetting BrowserRouter
forgetting Provider
forgetting @testing-library/jest-dom
wrong fetch mocking
missing act()
wrong testID spelling
exact string mismatch

These cause most bugs.

❌ Mistakes to Avoid

Never:

getByText()

for everything blindly.

Prefer:

getByRole()

first.

Never hit real API in tests.

Always use:

mock fetch

Never write one giant test.

Break into:

small isolated tests.

🎯 Important Interview Questions
Q1. Why fetch is not defined in Jest?

Because Jest uses JSDOM, not real browser.

Fetch is browser API.

Q2. Why use act()?

To handle async state updates safely.

Q3. Difference between Unit and Integration Testing?

Unit → one component/function

Integration → multiple components together

Q4. Why use BrowserRouter in tests?

Because <Link /> depends on router context.

Q5. Why use Provider in tests?

Redux store dependency.

Q6. Why use mock fetch?

Tests should not depend on real API.

Q7. Why prefer getByRole()?

Accessibility + cleaner + interview standard

⭐ Episode Rating
100/10

One of the most important episodes of Namaste React.

This is actual production-level React knowledge.

💼 Interview Importance
EXTREMELY HIGH

Testing questions strongly affect hiring.

Most developers are weak here.

Strong advantage for serious candidates.

🚀 Job Readiness Impact

After mastering this episode:

you are no longer just a React learner.

You start thinking like:

Production React Developer

That is the real transition point.