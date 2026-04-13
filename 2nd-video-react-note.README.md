Namaste React – Episode 02 Notes
🔥 Igniting Our App

1️⃣ Pushing Code to GitHub
📌 Concept
Before continuing development, it is a good practice to push your code to GitHub.

🧠 Idea
GitHub acts as a remote backup + collaboration platform for your project.

⚙️ Steps
Create a repository on GitHub.
Then in your project folder run:

git init
git branch -M main
git add .
git commit -m "Episode 1"
git remote add origin <repository-url>
git push origin main

⭐ Important
Git ≠ GitHub

Tool	Meaning
Git	Version control system
GitHub	Platform that hosts Git repositories

2️⃣ Why Our Code is NOT Production Ready
📌 Problem
The app we built earlier is not optimized for production.

🧠 Idea
Before deploying an application, many optimizations must happen.

⚙️ Production Optimizations

Your code must be:

📦 Bundled
🧹 Minified
🗜️ Compressed
🖼️ Image optimized
⚡ Cached
✂️ Code split

These optimizations are handled by Bundlers.

3️⃣ What is a Bundler?
📌 Concept
A bundler prepares your app for production.

🧠 Idea
It packages all files into optimized bundles.

🔧 Popular Bundlers
Bundler	Description
Webpack	Most widely used
Parcel	Zero-config bundler
Vite	Modern fast bundler

In this course we use:
Parcel

Because:
easy configuration
fast builds
beginner friendly

4️⃣ What is NPM?
📌 Concept
NPM is a package manager.

🧠 Important Fact

Many people say:
NPM = Node Package Manager
❌ This is technically incorrect

NPM does not officially stand for anything.
It is simply called npm.

⚙️ What NPM Does

NPM manages:
packages
dependencies
libraries
tools

Example packages:

React
Parcel
Babel
Lodash

5️⃣ Initializing NPM

📌 Command
npm init

This creates:
📄 package.json

🧠 Idea
package.json is the configuration file for NPM.

It stores:
project name
version
dependencies
scripts
metadata

Example:

{
 "name": "namaste-react",
 "version": "1.0.0"
}

6️⃣ Installing Parcel
📌 Command
npm install -D parcel

⚙️ Explanation
Part	Meaning
npm	package manager
install	install package
parcel	package name
-D	dev dependency

🧠 Dev Dependency vs Dependency
Type		Usage
Dev Dependency	Needed during development
Dependency	Needed in production

Parcel is a dev dependency.

7️⃣ Versioning and Caret (^)

Example in package.json:
"parcel": "^2.8.3"

📌 Meaning
^ allows minor updates automatically

Example:
2.8.3 → 2.8.4 allowed
2.8.3 → 3.0.0 NOT allowed

⭐ Why?
Major updates may break the project.

8️⃣ package.json vs package-lock.json
Many developers don't know this difference.

📄 package.json

Stores:
dependency names
approximate versions

Example:
"parcel": "^2.8.3"

🔒 package-lock.json

Stores:
exact versions
dependency tree
security hash

Example:
parcel 2.8.3

🧠 Purpose

Ensures:
same dependencies on every machine

Avoids the problem:
"Works on my machine but not in production"

9️⃣ node_modules
📌 Concept
When we install packages:
npm install

NPM downloads code into:
node_modules/

This folder contains:
actual package code
all dependencies
dependency trees

🧠 Transitive Dependencies

Example:

Our Project
   ↓
Parcel
   ↓
Other packages
   ↓
More packages

Dependencies of dependencies are called:
Transitive Dependencies

🔟 Why node_modules is Huge
Even if you install one package, many other packages get installed.

Example:

parcel
   ↓
babel
   ↓
many utilities

This creates hundreds of folders.

1️⃣1️⃣ Should node_modules be pushed to GitHub?
❌ No

Because it can be regenerated.

Add to .gitignore
node_modules

🧠 Why?
Because we already have:

package.json
package-lock.json

We can recreate node_modules with:
npm install

1️⃣2️⃣ Starting Parcel Server

Run:
npx parcel index.html

📌 Important
Tool	Purpose
npm	installs packages
npx	executes packages

1️⃣3️⃣ Installing React using NPM

Remove CDN links.
Install React:
npm install react

Install React DOM:
npm install react-dom

Now React is stored in:
node_modules/react

1️⃣4️⃣ Importing React
Since React is now in node_modules, we must import it.

import React from "react";
import ReactDOM from "react-dom/client";

1️⃣5️⃣ Fixing Import Error
Browser error:
Browser scripts cannot have imports

Solution
Use module type.

<script type="module" src="app.js"></script>

1️⃣6️⃣ Parcel Superpowers
Parcel automatically provides many features.

🚀 Features

1️⃣ Dev Server
localhost:1234

2️⃣ Hot Module Replacement (HMR)
Auto refresh when code changes.

3️⃣ File Watching
Parcel monitors files for changes.

4️⃣ Faster Builds
Using caching.

5️⃣ Image Optimization
6️⃣ Code Splitting
7️⃣ Minification
8️⃣ Bundling
9️⃣ Compression
🔟 Tree Shaking

1️⃣7️⃣ What is HMR?
🔥 Hot Module Replacement
Automatically refreshes the page when files change.

Example:
Save file → Browser refreshes instantly
This improves developer experience.

1️⃣8️⃣ Parcel Cache

Parcel creates:
.parcel-cache

Purpose:
cache builds
faster recompilation

1️⃣9️⃣ Production Build
Command
npx parcel build index.html

This generates:
dist/
📦 dist folder
Contains optimized files.

Example:

dist
 ├ index.html
 ├ index.css
 └ index.js

These files are:
minified
compressed
optimized

2️⃣0️⃣ Files That Should NOT Go to GitHub

Add to .gitignore:

node_modules
dist
.parcel-cache

Files that SHOULD go to GitHub
package.json
package-lock.json
src files

2️⃣1️⃣ Browserslist
📌 Purpose
Defines which browsers your app should support.

Example in package.json:

"browserslist": [
 "last 2 versions"
]

Meaning:
App works on last two versions of all browsers.

2️⃣2️⃣ Differential Bundling
Parcel generates different bundles for different browsers.

Example:
modern browsers
older browsers
This improves compatibility.

2️⃣3️⃣ Why React Apps Are Fast

Many developers wrongly think:
React makes apps fast

Reality
Performance comes from:

React
Parcel
Babel
Browserslist
Bundlers
Optimizations

React is only one piece.

⭐ Quick Revision
npm init
→ creates package.json

npm install
→ installs dependencies

node_modules
→ actual dependency code

package-lock.json
→ exact versions

npx parcel index.html
→ start dev server

npx parcel build index.html
→ production build

✅ Episode 2 completed — App Ignited 🔥
