React Complete Course - Ultimate Beginner's Guide
A comprehensive, detailed guide to learning React from absolute zero. Every concept explained in plain English with extensive notes, real examples, and complete projects.

📚 Complete Table of Contents
Introduction to React

Setting Up Your Development Environment

Understanding the Project Structure

JSX - JavaScript XML

Components - The Building Blocks

Props - Passing Data Between Components

State - Managing Changing Data

Events - Handling User Interactions

Lists and Keys - Rendering Multiple Items

Conditional Rendering - Showing/Hiding Content

Forms and User Input - Collecting Data

useEffect - Side Effects in Components

Fetching Data from APIs - Getting External Data

Local Storage - Saving Data in Browser

React Router - Navigation Without Refresh

React Icons - Beautiful Icons Made Easy

Building Real Projects

Project 1: Counter App with Explanation

Project 2: Todo App with Local Storage

Project 3: Weather App with API

Project 4: Movie Search App

Project 5: Notes App with Categories

Project 6: Expense Tracker

Project 7: Recipe Finder

Project 8: User Management Dashboard

Project 9: Blog Posts with Comments

Project 10: Complete Portfolio Website

Common Mistakes and How to Fix Them

Best Practices for Clean Code

Next Steps in Your React Journey

1. Introduction to React
What Exactly is React?
React is a JavaScript library for building user interfaces. Let's break that down:

JavaScript Library: It's a collection of pre-written JavaScript code that helps you build websites faster

User Interfaces: Everything you see on a website - buttons, forms, menus, text, images

Why Was React Created?
Before React (2013), building complex websites was difficult because:

Manual DOM Manipulation: Developers had to write code like this:

javascript
// Old way - Hard to manage
const button = document.getElementById('myButton');
const counter = document.getElementById('counter');
let count = 0;

button.addEventListener('click', () => {
  count++;
  counter.innerHTML = count; // Manually update the DOM
});
Hard to Reuse Code: If you wanted the same button on multiple pages, you had to copy-paste code

Slow Performance: Every small change meant updating the entire page

What Problems Does React Solve?
Problem 1: Keeping UI in Sync with Data

jsx
// React way - Declarative
function Counter() {
  const [count, setCount] = useState(0);
  
  // React automatically updates the UI when count changes
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
Problem 2: Code Reusability

jsx
// Create once, use anywhere
function Button({ text, color }) {
  return <button style={{ backgroundColor: color }}>{text}</button>;
}

// Use in many places
<Button text="Click Me" color="blue" />
<Button text="Delete" color="red" />
<Button text="Save" color="green" />
Problem 3: Performance

React uses a Virtual DOM (a lightweight copy of the real DOM)

It only updates what actually changed, not everything

This makes apps much faster

Key Concepts You'll Learn
Components: Reusable pieces of UI

Props: Data passed between components

State: Data that changes over time

Hooks: Functions that let you use React features

JSX: JavaScript + HTML combined

Why React is So Popular Today
Reason	Explanation
Easy to Learn	If you know JavaScript and HTML, you can learn React
Huge Community	Millions of developers use React, so help is everywhere
Great Job Market	React skills are in high demand globally
Facebook Backed	Created and maintained by Meta (Facebook)
Flexible	Works with any backend (Node.js, Python, PHP, etc.)
Mobile Apps	React Native lets you build mobile apps with React skills
2. Setting Up Your Development Environment
Step 1: Install Node.js
What is Node.js?
Node.js allows JavaScript to run outside the browser. We need it to:

Create React projects

Install packages

Run development servers

How to Install:

Go to nodejs.org

Download the LTS version (Long Term Support)

Run the installer (click Next, Next, Finish)

Open your terminal/command prompt

Verify installation:

bash
# Check Node.js version
node --version
# Should show something like: v18.17.0

# Check npm version (npm comes with Node.js)
npm --version
# Should show something like: 9.6.7
Step 2: Choose a Code Editor
Visual Studio Code (VS Code) is the best choice for React development.

Why VS Code?

Free and open source

Great React support

Lots of useful extensions

Integrated terminal

Download: code.visualstudio.com

Recommended Extensions:

ES7+ React/Redux/React-Native snippets - Shortcuts for React code

Prettier - Automatically formats your code

Tailwind CSS IntelliSense - Helps with Tailwind classes

JavaScript (ES6) code snippets - JavaScript shortcuts

Step 3: Create Your First React App
We'll use Vite - it's faster and more modern than Create React App.

Open terminal and run these commands:

bash
# Create a new React project
npm create vite@latest my-react-app -- --template react

# What this does:
# - Downloads Vite
# - Creates a folder called 'my-react-app'
# - Sets up a React project with all necessary files
bash
# Navigate into your project folder
cd my-react-app

# What this does:
# - Changes directory to your project folder
# - You need to be in this folder to run commands
bash
# Install all dependencies
npm install

# What this does:
# - Reads package.json file
# - Downloads all required packages into node_modules folder
# - This might take 1-2 minutes
bash
# Install Tailwind CSS for styling
npm install -D tailwindcss postcss autoprefixer

# What this does:
# - Installs Tailwind CSS for easy styling
# - We'll use Tailwind for all our projects
bash
# Initialize Tailwind CSS
npx tailwindcss init -p

# What this does:
# - Creates tailwind.config.js file
# - Sets up PostCSS configuration
Step 4: Configure Tailwind CSS
1. Update tailwind.config.js:

javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
2. Replace content of src/index.css:

css
@tailwind base;
@tailwind components;
@tailwind utilities;
Step 5: Start the Development Server
bash
npm run dev
What this does:

Starts a local development server

Opens your app at http://localhost:5173

Automatically refreshes when you save files

You should see: "Welcome to React!" in your browser

Understanding the Terminal Output
text
VITE v4.4.0  ready in 300 ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
Local: The URL to open in your browser

Network: How to access from other devices on your network

3. Understanding the Project Structure
Let's explore every file and folder in your React project:

text
my-react-app/
├── node_modules/              # All installed packages (don't touch this)
├── public/                    # Static files (images, icons)
│   └── vite.svg              # Logo icon
├── src/                       # Your source code (you work here)
│   ├── assets/               # Images, fonts, etc.
│   ├── components/           # Reusable components (create this)
│   ├── pages/                # Page components (create this)
│   ├── App.jsx              # Main component
│   ├── App.css              # Styles for App (optional)
│   ├── main.jsx             # Entry point
│   └── index.css            # Global styles
├── .gitignore               # Files to ignore in Git
├── index.html               # Main HTML file
├── package.json             # Project dependencies and scripts
├── vite.config.js           # Vite configuration
└── README.md                # Project documentation
Detailed File Explanations
index.html - The Starting Point
html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + React</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
Important Notes:

<div id="root"></div> - This is where React injects your app

<script src="/src/main.jsx"> - Loads your React code

You rarely need to modify this file

src/main.jsx - The Entry Point
jsx
import React from 'react'                    // Import React library
import ReactDOM from 'react-dom/client'      // Import ReactDOM for rendering
import App from './App.jsx'                  // Import your main component
import './index.css'                         // Import global styles

// Create a root element and render your App
ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>      // Helps catch common mistakes
    <App />               // Your main component
  </React.StrictMode>,
)
What's happening:

createRoot finds the <div id="root"> in index.html

.render() puts your React app inside that div

<App /> is your main component that contains everything else

src/App.jsx - Your Main Component
jsx
import './App.css'         // Import styles

function App() {
  return (
    <>
      <h1 className="text-3xl font-bold text-blue-600">
        Welcome to React!
      </h1>
    </>
  )
}

export default App         // Make this available to other files
Important Notes:

Every React component is a function

The function returns JSX (HTML-like code)

export default makes the component importable elsewhere

The empty <></> is a Fragment (wraps multiple elements)

package.json - Project Information
json
{
  "name": "my-react-app",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",              // Development server
    "build": "vite build",      // Build for production
    "preview": "vite preview"   // Preview production build
  },
  "dependencies": {
    "react": "^18.2.0",         // React library
    "react-dom": "^18.2.0"      // React DOM rendering
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.0.0",
    "vite": "^4.4.0",
    "tailwindcss": "^3.3.0"     // Styling
  }
}
Understanding:

dependencies: Packages needed for production

devDependencies: Packages only needed during development

scripts: Commands you can run with npm run [name]

4. JSX - JavaScript XML
What is JSX?
JSX is a syntax extension that lets you write HTML-like code inside JavaScript. It's not HTML, it's JavaScript that looks like HTML.

Why Use JSX?
Without JSX, creating elements looks like this:

javascript
// Without JSX - Very verbose
const element = React.createElement('h1', { className: 'title' }, 'Hello World');
With JSX:

jsx
// With JSX - Clean and readable
const element = <h1 className="title">Hello World</h1>;
JSX Rules You Must Remember
jsx
function JSXRules() {
  // 1. Must have one parent element
  // ❌ Wrong - Two elements at root level
  return (
    <h1>Title</h1>
    <p>Content</p>
  )
  
  // ✅ Correct - Wrapped in a div or fragment
  return (
    <div>
      <h1>Title</h1>
      <p>Content</p>
    </div>
  )
  
  // ✅ Also correct - Using fragment
  return (
    <>
      <h1>Title</h1>
      <p>Content</p>
    </>
  )
}
jsx
// 2. Use className instead of class
// ❌ Wrong
<div class="container"></div>

// ✅ Correct
<div className="container"></div>
jsx
// 3. JavaScript expressions go in curly braces {}
function UserGreeting() {
  const name = "John";
  const age = 25;
  const isLoggedIn = true;
  
  return (
    <div>
      {/* Variables */}
      <p>Name: {name}</p>
      
      {/* Expressions */}
      <p>Age in 5 years: {age + 5}</p>
      
      {/* Ternary operators */}
      <p>{isLoggedIn ? "Welcome back!" : "Please login"}</p>
      
      {/* Function calls */}
      <p>{new Date().toLocaleDateString()}</p>
    </div>
  );
}
jsx
// 4. CamelCase for attributes
// ❌ Wrong
<button onclick="handleClick">Click</button>
<div tabindex="0">Focusable</div>

// ✅ Correct
<button onClick={handleClick}>Click</button>
<div tabIndex="0">Focusable</div>
jsx
// 5. Inline styles are objects
function StyledComponent() {
  const buttonStyle = {
    backgroundColor: 'blue',
    color: 'white',
    padding: '10px 20px',
    borderRadius: '5px'
  };
  
  return (
    // CSS properties are camelCase
    <button style={buttonStyle}>
      Click Me
    </button>
  );
}
jsx
// 6. Comments in JSX
function ComponentWithComments() {
  return (
    <div>
      {/* This is a JSX comment */}
      <h1>Hello</h1>
      {/*
        Multi-line
        comment
      */}
    </div>
  );
}
Complete JSX Example with Notes
jsx
function CompleteJSXExample() {
  // Variables can be used in JSX
  const userName = "Alice";
  const userAge = 28;
  const userCity = "New York";
  const isAdmin = true;
  const hobbies = ["Reading", "Gaming", "Coding"];
  
  // Functions can be called
  const formatName = (name) => {
    return name.toUpperCase();
  };
  
  // Conditional logic
  const getRoleBadge = () => {
    if (isAdmin) {
      return <span className="bg-red-500 text-white px-2 py-1 rounded">Admin</span>;
    }
    return <span className="bg-gray-500 text-white px-2 py-1 rounded">User</span>;
  };
  
  return (
    <div className="max-w-md mx-auto bg-white rounded-lg shadow-lg p-6">
      {/* Title with dynamic content */}
      <h1 className="text-2xl font-bold mb-4">
        Welcome, {formatName(userName)}!
      </h1>
      
      {/* User information */}
      <div className="space-y-2 mb-4">
        <p>📍 Age: {userAge} years old</p>
        <p>🏙️ City: {userCity}</p>
        <p>⭐ Role: {getRoleBadge()}</p>
      </div>
      
      {/* Conditional rendering with ternary */}
      <div className="mb-4">
        {userAge >= 18 ? (
          <p className="text-green-600">✅ You are an adult</p>
        ) : (
          <p className="text-yellow-600">⚠️ You are a minor</p>
        )}
      </div>
      
      {/* List rendering */}
      <div className="mb-4">
        <h2 className="font-bold mb-2">Hobbies:</h2>
        <ul className="list-disc list-inside">
          {hobbies.map((hobby, index) => (
            <li key={index} className="text-gray-700">
              {hobby}
            </li>
          ))}
        </ul>
      </div>
      
      {/* Inline styles */}
      <button 
        onClick={() => alert(`Hello ${userName}!`)}
        style={{
          backgroundColor: '#3b82f6',
          color: 'white',
          padding: '8px 16px',
          borderRadius: '8px',
          border: 'none',
          cursor: 'pointer'
        }}
      >
        Say Hello
      </button>
    </div>
  );
}
Common JSX Mistakes and Fixes
jsx
// ❌ Mistake 1: Using 'class' instead of 'className'
<div class="container">Content</div>

// ✅ Fix
<div className="container">Content</div>

// ❌ Mistake 2: Forgetting to wrap multiple elements
return (
  <h1>Title</h1>
  <p>Paragraph</p>
)

// ✅ Fix
return (
  <div>
    <h1>Title</h1>
    <p>Paragraph</p>
  </div>
)

// ❌ Mistake 3: Using 'for' instead of 'htmlFor' in labels
<label for="email">Email</label>
<input id="email" type="email" />

// ✅ Fix
<label htmlFor="email">Email</label>
<input id="email" type="email" />

// ❌ Mistake 4: Forgetting curly braces for JavaScript
<p>2 + 2 = 2 + 2</p>  // Shows "2 + 2 = 2 + 2"

// ✅ Fix
<p>2 + 2 = {2 + 2}</p>  // Shows "2 + 2 = 4"

// ❌ Mistake 5: Using if statements directly in JSX
return (
  <div>
    {if (isLoggedIn) { <p>Welcome</p> }}  // Doesn't work
  </div>
)

// ✅ Fix - Use ternary or && operator
return (
  <div>
    {isLoggedIn ? <p>Welcome</p> : <p>Login</p>}
    {isLoggedIn && <p>Welcome</p>}
  </div>
)
5. Components - The Building Blocks
What Are Components?
Think of components like Lego blocks. Each block is a piece of UI that you can reuse anywhere in your app.

Types of Components
There are two types, but we focus on Functional Components (modern approach).

jsx
// Functional Component - Modern way
function Welcome() {
  return <h1>Hello, World!</h1>;
}

// Arrow Function Component - Also modern
const Welcome = () => {
  return <h1>Hello, World!</h1>;
}

// Implicit return (short form)
const Welcome = () => <h1>Hello, World!</h1>;
Creating Your First Component
jsx
// components/Button.jsx
// This is a reusable button component

function Button({ text, color, onClick }) {
  // Define styles based on color prop
  const colors = {
    blue: 'bg-blue-500 hover:bg-blue-600',
    red: 'bg-red-500 hover:bg-red-600',
    green: 'bg-green-500 hover:bg-green-600'
  };
  
  // Choose color or default to blue
  const buttonColor = colors[color] || colors.blue;
  
  return (
    <button
      onClick={onClick}
      className={`${buttonColor} text-white px-4 py-2 rounded-lg transition-colors`}
    >
      {text}
    </button>
  );
}

export default Button;
Using Components in Other Components
jsx
// App.jsx
import Button from './components/Button';

function App() {
  const handleClick = () => {
    alert('Button was clicked!');
  };
  
  return (
    <div className="p-8 space-y-4">
      <h1 className="text-2xl font-bold">My App</h1>
      
      {/* Using the Button component multiple times */}
      <Button text="Click Me" color="blue" onClick={handleClick} />
      <Button text="Delete" color="red" onClick={handleClick} />
      <Button text="Save" color="green" onClick={handleClick} />
    </div>
  );
}

export default App;
Component Composition - Building Complex UI
jsx
// Building a card component by combining smaller components

// 1. Create Avatar component
function Avatar({ image, name }) {
  return (
    <img 
      src={image} 
      alt={name}
      className="w-12 h-12 rounded-full object-cover"
    />
  );
}

// 2. Create UserInfo component
function UserInfo({ name, email }) {
  return (
    <div>
      <h3 className="font-bold">{name}</h3>
      <p className="text-sm text-gray-500">{email}</p>
    </div>
  );
}

// 3. Create Actions component
function Actions({ onLike, onShare }) {
  return (
    <div className="flex gap-2 mt-4">
      <button 
        onClick={onLike}
        className="bg-blue-500 text-white px-3 py-1 rounded text-sm"
      >
        Like
      </button>
      <button 
        onClick={onShare}
        className="bg-gray-500 text-white px-3 py-1 rounded text-sm"
      >
        Share
      </button>
    </div>
  );
}

// 4. Combine them into a Card component
function UserCard({ user }) {
  return (
    <div className="border rounded-lg p-4 shadow-md">
      <div className="flex items-start gap-3">
        <Avatar image={user.avatar} name={user.name} />
        <UserInfo name={user.name} email={user.email} />
      </div>
      <p className="mt-3 text-gray-700">{user.bio}</p>
      <Actions 
        onLike={() => alert(`Liked ${user.name}`)}
        onShare={() => alert(`Shared ${user.name}`)}
      />
    </div>
  );
}

// 5. Use the Card component
function App() {
  const user = {
    name: "John Doe",
    email: "john@example.com",
    avatar: "https://via.placeholder.com/48",
    bio: "React developer and coding enthusiast"
  };
  
  return (
    <div className="p-8">
      <UserCard user={user} />
    </div>
  );
}
Component Organization Best Practices
text
src/
├── components/           # Reusable components
│   ├── Button.jsx       # Button component
│   ├── Card.jsx         # Card component
│   ├── Input.jsx        # Input component
│   └── Modal.jsx        # Modal component
├── pages/               # Page components
│   ├── Home.jsx         # Home page
│   ├── About.jsx        # About page
│   └── Contact.jsx      # Contact page
├── layouts/             # Layout components
│   ├── Header.jsx       # Header layout
│   └── Footer.jsx       # Footer layout
└── App.jsx              # Main component
Component Example with Detailed Notes
jsx
// components/ProductCard.jsx
// This component displays a product with image, title, price, and add to cart button

import { useState } from 'react';  // We'll learn about useState soon

function ProductCard({ product, onAddToCart }) {
  // product is an object with properties:
  // - id: unique identifier
  // - name: product name
  // - price: product price
  // - image: image URL
  
  // State to track if product is added to cart
  const [isAdded, setIsAdded] = useState(false);
  
  // Handle add to cart button click
  const handleAddToCart = () => {
    setIsAdded(true);  // Show "Added" message
    onAddToCart(product);  // Call the parent function
    
    // Reset the added message after 2 seconds
    setTimeout(() => setIsAdded(false), 2000);
  };
  
  return (
    <div className="border rounded-lg overflow-hidden shadow-lg hover:shadow-xl transition-shadow">
      {/* Product Image */}
      <img 
        src={product.image} 
        alt={product.name}
        className="w-full h-48 object-cover"
      />
      
      {/* Product Details */}
      <div className="p-4">
        <h3 className="text-lg font-bold mb-2">{product.name}</h3>
        <p className="text-gray-600 mb-4">${product.price}</p>
        
        {/* Add to Cart Button */}
        <button
          onClick={handleAddToCart}
          disabled={isAdded}
          className={`w-full py-2 rounded transition-colors ${
            isAdded 
              ? 'bg-green-500 cursor-not-allowed' 
              : 'bg-blue-500 hover:bg-blue-600'
          } text-white`}
        >
          {isAdded ? 'Added to Cart ✓' : 'Add to Cart'}
        </button>
      </div>
    </div>
  );
}

export default ProductCard;
6. Props - Passing Data Between Components
What Are Props?
Props (short for properties) are like arguments to functions. They allow parent components to pass data to child components.

Props Analogy
Think of props like gift boxes:

Parent component wraps data in a box (props)

Child component receives and opens the box

Child can use the data but cannot change it

Basic Props Example
jsx
// Parent Component - Sends data
function App() {
  return (
    <div>
      {/* Passing props to child */}
      <ChildComponent 
        name="John"           // String prop
        age={25}              // Number prop (note curly braces)
        isStudent={true}      // Boolean prop
        hobbies={['coding', 'reading']}  // Array prop
        address={{ city: 'NY', zip: '10001' }}  // Object prop
      />
    </div>
  );
}

// Child Component - Receives data
function ChildComponent({ name, age, isStudent, hobbies, address }) {
  return (
    <div>
      <p>Name: {name}</p>
      <p>Age: {age}</p>
      <p>Student: {isStudent ? 'Yes' : 'No'}</p>
      <p>Hobbies: {hobbies.join(', ')}</p>
      <p>City: {address.city}</p>
    </div>
  );
}
Different Ways to Use Props
jsx
// Example 1: Destructuring props
// Option A: Destructure in parameters (recommended)
function Greeting({ name, age }) {
  return <p>{name} is {age} years old</p>;
}

// Option B: Use props object
function Greeting(props) {
  return <p>{props.name} is {props.age} years old</p>;
}

// Option C: Destructure inside function
function Greeting(props) {
  const { name, age } = props;
  return <p>{name} is {age} years old</p>;
}
Passing Functions as Props
jsx
// Parent component
function ParentComponent() {
  // Define a function in parent
  const handleChildClick = (message) => {
    alert(`Child says: ${message}`);
  };
  
  return (
    <div>
      {/* Pass function to child */}
      <ChildComponent onButtonClick={handleChildClick} />
    </div>
  );
}

// Child component
function ChildComponent({ onButtonClick }) {
  return (
    <button onClick={() => onButtonClick("Hello Parent!")}>
      Send Message to Parent
    </button>
  );
}
Children Prop (Special Prop)
The children prop allows you to pass components/elements as content.

jsx
// Component that accepts children
function Card({ title, children }) {
  return (
    <div className="border rounded-lg shadow-md">
      <div className="bg-gray-100 p-3 border-b">
        <h3 className="font-bold">{title}</h3>
      </div>
      <div className="p-4">
        {children}  {/* This renders whatever is between <Card> tags */}
      </div>
    </div>
  );
}

// Using the Card component
function App() {
  return (
    <div className="p-8 space-y-4">
      {/* Card with paragraph content */}
      <Card title="Welcome Card">
        <p>This is some content inside the card</p>
      </Card>
      
      {/* Card with button content */}
      <Card title="Action Card">
        <button className="bg-blue-500 text-white px-4 py-2 rounded">
          Click Me
        </button>
      </Card>
      
      {/* Card with multiple elements */}
      <Card title="User Card">
        <div className="flex items-center gap-3">
          <img src="avatar.jpg" className="w-12 h-12 rounded-full" />
          <div>
            <p className="font-bold">John Doe</p>
            <p className="text-sm text-gray-500">john@example.com</p>
          </div>
        </div>
      </Card>
    </div>
  );
}
Default Props
Set default values for props in case they're not provided.

jsx
function Button({ text, color, size }) {
  // Default values
  const buttonColor = color || 'blue';
  const buttonSize = size || 'medium';
  
  const sizes = {
    small: 'px-3 py-1 text-sm',
    medium: 'px-4 py-2 text-base',
    large: 'px-6 py-3 text-lg'
  };
  
  return (
    <button className={`bg-${buttonColor}-500 text-white ${sizes[buttonSize]} rounded`}>
      {text || 'Click Me'}  {/* Default text */}
    </button>
  );
}

// Usage
<Button />  // Uses all defaults
<Button text="Save" />  // Uses default color and size
<Button text="Delete" color="red" size="large" />
Props Are Read-Only - Important!
jsx
// ❌ NEVER modify props directly
function ChildComponent({ count }) {
  count = count + 1;  // This is WRONG!
  return <p>{count}</p>;
}

// ✅ Props are read-only
function ChildComponent({ count, onIncrement }) {
  // Use state or call functions to change data
  return (
    <div>
      <p>{count}</p>
      <button onClick={onIncrement}>Increment</button>
    </div>
  );
}
Complete Props Example with Detailed Notes
jsx
// components/UserProfile.jsx
// This component displays user information and actions

function UserProfile({ 
  user,           // User object with name, email, avatar
  onEdit,         // Function to call when editing
  onDelete,       // Function to call when deleting
  showActions = true,  // Whether to show action buttons (default true)
  className = ''       // Additional CSS classes
}) {
  // If user is not provided, show error message
  if (!user) {
    return (
      <div className="bg-red-100 text-red-700 p-4 rounded">
        Error: User data is required
      </div>
    );
  }
  
  return (
    <div className={`border rounded-lg p-4 shadow-md ${className}`}>
      {/* User Avatar and Name Section */}
      <div className="flex items-center gap-4 mb-4">
        {user.avatar && (
          <img 
            src={user.avatar} 
            alt={user.name}
            className="w-16 h-16 rounded-full object-cover"
          />
        )}
        <div>
          <h2 className="text-xl font-bold">{user.name}</h2>
          <p className="text-gray-600">{user.email}</p>
        </div>
      </div>
      
      {/* Additional User Info */}
      <div className="space-y-2 mb-4">
        <p><span className="font-semibold">Role:</span> {user.role || 'User'}</p>
        <p><span className="font-semibold">Joined:</span> {user.joinDate || 'Recently'}</p>
        {user.bio && (
          <p><span className="font-semibold">Bio:</span> {user.bio}</p>
        )}
      </div>
      
      {/* Action Buttons */}
      {showActions && (
        <div className="flex gap-2 pt-4 border-t">
          <button
            onClick={() => onEdit(user)}
            className="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition"
          >
            Edit Profile
          </button>
          <button
            onClick={() => onDelete(user.id)}
            className="bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600 transition"
          >
            Delete Account
          </button>
        </div>
      )}
    </div>
  );
}

export default UserProfile;
7. State - Managing Changing Data
What is State?
State is data that can change over time in your component. When state changes, React automatically re-renders the component to show the new data.

useState Hook - The Simplest State Management
jsx
import { useState } from 'react';

function Counter() {
  // useState returns an array with two items:
  // 1. Current state value
  // 2. Function to update the state
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>Current count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}
Understanding useState Syntax
jsx
// Basic syntax
const [state, setState] = useState(initialValue);

// Breaking it down:
// state     - variable that holds the current value
// setState  - function to update the state
// useState  - React hook that creates state
// initialValue - starting value (can be any type)
Different Types of State
jsx
// Example 1: String state
function NameInput() {
  const [name, setName] = useState('');
  
  return (
    <input 
      value={name}
      onChange={(e) => setName(e.target.value)}
      placeholder="Enter your name"
    />
  );
}

// Example 2: Number state
function AgeCounter() {
  const [age, setAge] = useState(0);
  
  return (
    <div>
      <p>Age: {age}</p>
      <button onClick={() => setAge(age + 1)}>Birthday!</button>
    </div>
  );
}

// Example 3: Boolean state
function ToggleButton() {
  const [isOn, setIsOn] = useState(false);
  
  return (
    <button onClick={() => setIsOn(!isOn)}>
      {isOn ? 'ON' : 'OFF'}
    </button>
  );
}

// Example 4: Array state
function TodoList() {
  const [todos, setTodos] = useState([]);
  
  const addTodo = () => {
    setTodos([...todos, 'New Todo']);
  };
  
  return (
    <div>
      <button onClick={addTodo}>Add Todo</button>
      <ul>
        {todos.map((todo, index) => (
          <li key={index}>{todo}</li>
        ))}
      </ul>
    </div>
  );
}

// Example 5: Object state
function UserForm() {
  const [user, setUser] = useState({
    name: '',
    email: '',
    age: 0
  });
  
  const updateName = (newName) => {
    setUser({
      ...user,  // Keep all existing properties
      name: newName  // Update only the name
    });
  };
  
  return (
    <div>
      <input 
        value={user.name}
        onChange={(e) => updateName(e.target.value)}
      />
      <p>Name: {user.name}</p>
      <p>Email: {user.email}</p>
      <p>Age: {user.age}</p>
    </div>
  );
}
Updating State Correctly
jsx
// ❌ WRONG - Direct mutation
function WrongUpdate() {
  const [count, setCount] = useState(0);
  
  const increment = () => {
    count = count + 1;  // This doesn't work!
  };
  
  return <button onClick={increment}>{count}</button>;
}

// ✅ CORRECT - Using setter function
function CorrectUpdate() {
  const [count, setCount] = useState(0);
  
  const increment = () => {
    setCount(count + 1);  // This works!
  };
  
  return <button onClick={increment}>{count}</button>;
}
State Updates May Be Asynchronous
jsx
function AsyncUpdate() {
  const [count, setCount] = useState(0);
  
  const handleClick = () => {
    setCount(count + 1);
    console.log(count);  // This shows the OLD value, not the new one!
    // React schedules the update, but it doesn't happen immediately
  };
  
  // To get the updated value, use useEffect or functional update
  const handleCorrectClick = () => {
    setCount(prevCount => {
      const newCount = prevCount + 1;
      console.log(newCount);  // This shows the correct value
      return newCount;
    });
  };
  
  return (
    <div>
      <button onClick={handleClick}>Wrong (log old value)</button>
      <button onClick={handleCorrectClick}>Correct (log new value)</button>
      <p>Count: {count}</p>
    </div>
  );
}
Functional Updates (When New State Depends on Old State)
jsx
function Counter() {
  const [count, setCount] = useState(0);
  
  // ❌ BAD - Multiple updates might not work correctly
  const badIncrement = () => {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
    // Result: count increases by only 1, not 3
  };
  
  // ✅ GOOD - Using functional updates
  const goodIncrement = () => {
    setCount(prev => prev + 1);
    setCount(prev => prev + 1);
    setCount(prev => prev + 1);
    // Result: count increases by 3
  };
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={badIncrement}>Bad Increment (adds 1)</button>
      <button onClick={goodIncrement}>Good Increment (adds 3)</button>
    </div>
  );
}
Working with Arrays in State
jsx
function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [input, setInput] = useState('');
  
  // ADD item to array
  const addTodo = () => {
    if (input.trim()) {
      setTodos([...todos, { id: Date.now(), text: input, completed: false }]);
      setInput('');
    }
  };
  
  // REMOVE item from array
  const removeTodo = (id) => {
    setTodos(todos.filter(todo => todo.id !== id));
  };
  
  // UPDATE item in array
  const toggleTodo = (id) => {
    setTodos(todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    ));
  };
  
  return (
    <div>
      <input 
        value={input}
        onChange={(e) => setInput(e.target.value)}
        placeholder="Add todo..."
      />
      <button onClick={addTodo}>Add</button>
      
      <ul>
        {todos.map(todo => (
          <li key={todo.id}>
            <input
              type="checkbox"
              checked={todo.completed}
              onChange={() => toggleTodo(todo.id)}
            />
            <span style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}>
              {todo.text}
            </span>
            <button onClick={() => removeTodo(todo.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
Working with Objects in State
jsx
function UserProfile() {
  const [user, setUser] = useState({
    name: 'John Doe',
    email: 'john@example.com',
    age: 25,
    address: {
      street: '123 Main St',
      city: 'New York',
      country: 'USA'
    }
  });
  
  // Update simple property
  const updateName = (newName) => {
    setUser({
      ...user,  // Spread all existing properties
      name: newName  // Override name
    });
  };
  
  // Update nested property
  const updateCity = (newCity) => {
    setUser({
      ...user,
      address: {
        ...user.address,  // Spread existing address
        city: newCity     // Override city
      }
    });
  };
  
  // Using functional update with previous state
  const incrementAge = () => {
    setUser(prevUser => ({
      ...prevUser,
      age: prevUser.age + 1
    }));
  };
  
  return (
    <div>
      <input 
        value={user.name}
        onChange={(e) => updateName(e.target.value)}
      />
      <input 
        value={user.address.city}
        onChange={(e) => updateCity(e.target.value)}
      />
      <button onClick={incrementAge}>Have Birthday</button>
      
      <pre>{JSON.stringify(user, null, 2)}</pre>
    </div>
  );
}
Multiple State Variables
jsx
function RegistrationForm() {
  // Multiple state variables for different concerns
  const [username, setUsername] = useState('');
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [isLoading, setIsLoading] = useState(false);
  const [errors, setErrors] = useState({});
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    setIsLoading(true);
    
    try {
      // Submit form data
      console.log({ username, email, password });
      await new Promise(resolve => setTimeout(resolve, 1000));
      alert('Registration successful!');
    } catch (error) {
      setErrors({ submit: error.message });
    } finally {
      setIsLoading(false);
    }
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input 
        value={username}
        onChange={(e) => setUsername(e.target.value)}
        placeholder="Username"
      />
      <input 
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Email"
      />
      <input 
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
        placeholder="Password"
      />
      <button type="submit" disabled={isLoading}>
        {isLoading ? 'Registering...' : 'Register'}
      </button>
    </form>
  );
}
Complete State Example with Detailed Notes
jsx
// components/ShoppingCart.jsx
// This component manages a shopping cart with add, remove, update quantity

import { useState } from 'react';

function ShoppingCart() {
  // State: cart items array
  // Each item has: id, name, price, quantity
  const [cart, setCart] = useState([]);
  
  // State: show checkout form or not
  const [showCheckout, setShowCheckout] = useState(false);
  
  // State: loading state for API calls
  const [isProcessing, setIsProcessing] = useState(false);
  
  // Add item to cart
  const addToCart = (product) => {
    // Check if item already exists in cart
    const existingItem = cart.find(item => item.id === product.id);
    
    if (existingItem) {
      // If exists, increase quantity
      setCart(cart.map(item =>
        item.id === product.id
          ? { ...item, quantity: item.quantity + 1 }
          : item
      ));
    } else {
      // If new, add with quantity 1
      setCart([...cart, { ...product, quantity: 1 }]);
    }
  };
  
  // Remove item completely from cart
  const removeFromCart = (id) => {
    setCart(cart.filter(item => item.id !== id));
  };
  
  // Update quantity of an item
  const updateQuantity = (id, newQuantity) => {
    if (newQuantity <= 0) {
      // If quantity becomes 0 or negative, remove item
      removeFromCart(id);
    } else {
      // Otherwise update quantity
      setCart(cart.map(item =>
        item.id === id
          ? { ...item, quantity: newQuantity }
          : item
      ));
    }
  };
  
  // Calculate total price
  const calculateTotal = () => {
    return cart.reduce((total, item) => total + (item.price * item.quantity), 0);
  };
  
  // Handle checkout
  const handleCheckout = async () => {
    setIsProcessing(true);
    
    try {
      // Simulate API call to submit order
      await new Promise(resolve => setTimeout(resolve, 2000));
      alert(`Order placed! Total: $${calculateTotal().toFixed(2)}`);
      
      // Clear cart after successful order
      setCart([]);
      setShowCheckout(false);
    } catch (error) {
      alert('Error processing order. Please try again.');
    } finally {
      setIsProcessing(false);
    }
  };
  
  return (
    <div className="max-w-2xl mx-auto p-4">
      <h1 className="text-2xl font-bold mb-4">Shopping Cart</h1>
      
      {/* Product listing - just for demo */}
      <div className="mb-6">
        <h2 className="text-xl font-semibold mb-2">Products</h2>
        <div className="space-y-2">
          {[
            { id: 1, name: 'T-Shirt', price: 19.99 },
            { id: 2, name: 'Jeans', price: 49.99 },
            { id: 3, name: 'Shoes', price: 79.99 }
          ].map(product => (
            <div key={product.id} className="flex justify-between items-center border p-3 rounded">
              <div>
                <p className="font-semibold">{product.name}</p>
                <p className="text-gray-600">${product.price}</p>
              </div>
              <button
                onClick={() => addToCart(product)}
                className="bg-blue-500 text-white px-3 py-1 rounded hover:bg-blue-600"
              >
                Add to Cart
              </button>
            </div>
          ))}
        </div>
      </div>
      
      {/* Cart display */}
      {cart.length > 0 && (
        <div className="border rounded-lg p-4">
          <h2 className="text-xl font-semibold mb-3">Your Cart ({cart.length} items)</h2>
          
          {cart.map(item => (
            <div key={item.id} className="flex justify-between items-center mb-3 pb-3 border-b">
              <div className="flex-1">
                <p className="font-semibold">{item.name}</p>
                <p className="text-gray-600">${item.price}</p>
              </div>
              
              <div className="flex items-center gap-2">
                <button
                  onClick={() => updateQuantity(item.id, item.quantity - 1)}
                  className="bg-gray-200 px-2 py-1 rounded hover:bg-gray-300"
                >
                  -
                </button>
                <span className="w-8 text-center">{item.quantity}</span>
                <button
                  onClick={() => updateQuantity(item.id, item.quantity + 1)}
                  className="bg-gray-200 px-2 py-1 rounded hover:bg-gray-300"
                >
                  +
                </button>
                <button
                  onClick={() => removeFromCart(item.id)}
                  className="text-red-500 ml-2 hover:text-red-700"
                >
                  Remove
                </button>
              </div>
            </div>
          ))}
          
          <div className="mt-4 pt-3 border-t">
            <p className="text-xl font-bold text-right">
              Total: ${calculateTotal().toFixed(2)}
            </p>
            
            <button
              onClick={() => setShowCheckout(true)}
              className="mt-3 w-full bg-green-500 text-white py-2 rounded hover:bg-green-600"
            >
              Proceed to Checkout
            </button>
          </div>
        </div>
      )}
      
      {/* Checkout Modal */}
      {showCheckout && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center">
          <div className="bg-white rounded-lg p-6 max-w-md w-full">
            <h2 className="text-xl font-bold mb-4">Checkout</h2>
            
            <div className="mb-4">
              <p className="mb-2">Total Amount: ${calculateTotal().toFixed(2)}</p>
              <input
                type="text"
                placeholder="Card Number"
                className="w-full border p-2 rounded mb-2"
              />
              <input
                type="text"
                placeholder="Name on Card"
                className="w-full border p-2 rounded"
              />
            </div>
            
            <div className="flex gap-2">
              <button
                onClick={handleCheckout}
                disabled={isProcessing}
                className="flex-1 bg-green-500 text-white py-2 rounded hover:bg-green-600 disabled:opacity-50"
              >
                {isProcessing ? 'Processing...' : 'Place Order'}
              </button>
              <button
                onClick={() => setShowCheckout(false)}
                className="flex-1 bg-gray-500 text-white py-2 rounded hover:bg-gray-600"
              >
                Cancel
              </button>
            </div>
          </div>
        </div>
      )}
    </div>
  );
}

export default ShoppingCart;
8. Events - Handling User Interactions
What Are Events?
Events are actions that happen when users interact with your app:

Clicking a button

Typing in an input

Moving the mouse

Submitting a form

Basic Event Handling
jsx
function EventExample() {
  // Define event handler functions
  const handleClick = () => {
    alert('Button was clicked!');
  };
  
  const handleMouseEnter = () => {
    console.log('Mouse entered the button');
  };
  
  const handleMouseLeave = () => {
    console.log('Mouse left the button');
  };
  
  return (
    <button
      onClick={handleClick}          // Click event
      onMouseEnter={handleMouseEnter} // Mouse enter event
      onMouseLeave={handleMouseLeave} // Mouse leave event
      className="bg-blue-500 text-white px-4 py-2 rounded"
    >
      Hover or Click Me
    </button>
  );
}
Different Types of Events
jsx
function AllEvents() {
  // Click events
  const handleClick = (e) => {
    console.log('Clicked!', e.target);
  };
  
  // Change events (input, select, textarea)
  const handleChange = (e) => {
    console.log('Value changed to:', e.target.value);
  };
  
  // Submit events (forms)
  const handleSubmit = (e) => {
    e.preventDefault(); // IMPORTANT: Prevents page refresh
    console.log('Form submitted');
  };
  
  // Keyboard events
  const handleKeyDown = (e) => {
    console.log(`Key pressed: ${e.key}`);
    if (e.key === 'Enter') {
      console.log('Enter key pressed!');
    }
  };
  
  // Focus events
  const handleFocus = () => {
    console.log('Input focused');
  };
  
  const handleBlur = () => {
    console.log('Input lost focus');
  };
  
  return (
    <div className="space-y-4">
      {/* Click event */}
      <button onClick={handleClick} className="bg-blue-500 text-white p-2 rounded">
        Click Me
      </button>
      
      {/* Change event */}
      <input
        type="text"
        onChange={handleChange}
        className="border p-2 rounded block w-full"
        placeholder="Type something..."
      />
      
      {/* Form submit */}
      <form onSubmit={handleSubmit}>
        <button type="submit" className="bg-green-500 text-white p-2 rounded">
          Submit Form
        </button>
      </form>
      
      {/* Keyboard event */}
      <input
        type="text"
        onKeyDown={handleKeyDown}
        className="border p-2 rounded block w-full"
        placeholder="Press any key..."
      />
      
      {/* Focus/Blur events */}
      <input
        type="text"
        onFocus={handleFocus}
        onBlur={handleBlur}
        className="border p-2 rounded block w-full"
        placeholder="Click me then click outside"
      />
    </div>
  );
}
Passing Parameters to Event Handlers
jsx
function ParameterExample() {
  // Method 1: Using arrow function in onClick
  const handleClick = (name) => {
    alert(`Hello, ${name}!`);
  };
  
  // Method 2: Using bind
  const handleClickWithBind = (name) => {
    alert(`Hello, ${name}!`);
  };
  
  return (
    <div className="space-y-4">
      {/* Arrow function method - most common */}
      <button 
        onClick={() => handleClick('John')}
        className="bg-blue-500 text-white p-2 rounded"
      >
        Say Hello to John
      </button>
      
      {/* Bind method */}
      <button 
        onClick={handleClickWithBind.bind(null, 'Jane')}
        className="bg-green-500 text-white p-2 rounded"
      >
        Say Hello to Jane
      </button>
      
      {/* Passing event object AND parameters */}
      <button 
        onClick={(e) => {
          console.log('Event:', e);
          handleClick('Bob');
        }}
        className="bg-red-500 text-white p-2 rounded"
      >
        Log Event and Say Hello
      </button>
    </div>
  );
}
Common Event Patterns
jsx
// 1. Toggle State on Click
function ToggleButton() {
  const [isActive, setIsActive] = useState(false);
  
  const handleToggle = () => {
    setIsActive(!isActive);
  };
  
  return (
    <button
      onClick={handleToggle}
      className={`px-4 py-2 rounded ${isActive ? 'bg-green-500' : 'bg-gray-500'} text-white`}
    >
      {isActive ? 'Active' : 'Inactive'}
    </button>
  );
}

// 2. Input Change with Validation
function ValidatedInput() {
  const [value, setValue] = useState('');
  const [error, setError] = useState('');
  
  const handleChange = (e) => {
    const newValue = e.target.value;
    setValue(newValue);
    
    // Validate while typing
    if (newValue.length < 3) {
      setError('Must be at least 3 characters');
    } else {
      setError('');
    }
  };
  
  return (
    <div>
      <input
        value={value}
        onChange={handleChange}
        className={`border p-2 rounded ${error ? 'border-red-500' : 'border-gray-300'}`}
      />
      {error && <p className="text-red-500 text-sm mt-1">{error}</p>}
    </div>
  );
}

// 3. Form Submit with Multiple Fields
function LoginForm() {
  const [formData, setFormData] = useState({
    username: '',
    password: ''
  });
  const [isSubmitting, setIsSubmitting] = useState(false);
  
  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: value
    }));
  };
  
  const handleSubmit = async (e) => {
    e.preventDefault(); // Prevent page refresh
    
    setIsSubmitting(true);
    
    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      console.log('Form submitted:', formData);
      alert('Login successful!');
    } catch (error) {
      alert('Login failed');
    } finally {
      setIsSubmitting(false);
    }
  };
  
  return (
    <form onSubmit={handleSubmit} className="space-y-4">
      <div>
        <label className="block mb-1">Username:</label>
        <input
          type="text"
          name="username"
          value={formData.username}
          onChange={handleChange}
          className="border p-2 rounded w-full"
          required
        />
      </div>
      
      <div>
        <label className="block mb-1">Password:</label>
        <input
          type="password"
          name="password"
          value={formData.password}
          onChange={handleChange}
          className="border p-2 rounded w-full"
          required
        />
      </div>
      
      <button
        type="submit"
        disabled={isSubmitting}
        className="bg-blue-500 text-white px-4 py-2 rounded w-full disabled:opacity-50"
      >
        {isSubmitting ? 'Logging in...' : 'Login'}
      </button>
    </form>
  );
}

// 4. Keyboard Shortcuts
function KeyboardShortcut() {
  const [count, setCount] = useState(0);
  
  const handleKeyDown = (e) => {
    // Check if Ctrl + Shift + K is pressed
    if (e.ctrlKey && e.shiftKey && e.key === 'K') {
      setCount(prev => prev + 1);
      alert('Keyboard shortcut activated!');
    }
    
    // Check if Escape key is pressed
    if (e.key === 'Escape') {
      setCount(0);
    }
  };
  
  return (
    <div 
      onKeyDown={handleKeyDown}
      tabIndex="0" // Make div focusable
      className="border p-8 text-center"
    >
      <p>Count: {count}</p>
      <p className="text-sm text-gray-500">Press Ctrl+Shift+K to increment</p>
      <p className="text-sm text-gray-500">Press Escape to reset</p>
    </div>
  );
}

// 5. Double Click Event
function DoubleClickExample() {
  const [clickCount, setClickCount] = useState(0);
  
  const handleDoubleClick = () => {
    setClickCount(prev => prev + 1);
  };
  
  return (
    <div>
      <button
        onDoubleClick={handleDoubleClick}
        className="bg-blue-500 text-white px-4 py-2 rounded"
      >
        Double Click Me
      </button>
      <p className="mt-2">Double clicks: {clickCount}</p>
    </div>
  );
}
The Event Object (e) Explained
jsx
function EventObjectExplained() {
  const handleClick = (e) => {
    // e is the synthetic event object
    console.log('Event type:', e.type);           // "click"
    console.log('Target element:', e.target);     // The button element
    console.log('Mouse X position:', e.clientX);  // X coordinate
    console.log('Mouse Y position:', e.clientY);  // Y coordinate
    console.log('Alt key pressed:', e.altKey);    // Boolean
    console.log('Ctrl key pressed:', e.ctrlKey);  // Boolean
    console.log('Shift key pressed:', e.shiftKey); // Boolean
  };
  
  const handleInput = (e) => {
    console.log('Input value:', e.target.value);
    console.log('Input name:', e.target.name);
    console.log('Input type:', e.target.type);
  };
  
  const handleForm = (e) => {
    e.preventDefault(); // Stop page refresh
    console.log('Form submitted');
    
    // Get form data
    const formData = new FormData(e.target);
    console.log('Form data:', Object.fromEntries(formData));
  };
  
  return (
    <div>
      <button onClick={handleClick} className="bg-blue-500 text-white p-2 rounded m-2">
        Click me with modifier keys
      </button>
      
      <input
        name="email"
        type="email"
        onChange={handleInput}
        className="border p-2 rounded m-2"
        placeholder="Type something..."
      />
      
      <form onSubmit={handleForm} className="m-2">
        <input name="username" placeholder="Username" className="border p-2 rounded m-2" />
        <button type="submit" className="bg-green-500 text-white p-2 rounded">Submit</button>
      </form>
    </div>
  );
}
9. Lists and Keys - Rendering Multiple Items
Why We Need Keys
When rendering lists, React needs a way to identify which items have changed, been added, or been removed. Keys give each item a stable identity.

Basic List Rendering
jsx
function FruitList() {
  const fruits = ['Apple', 'Banana', 'Orange', 'Mango'];
  
  return (
    <ul className="list-disc pl-5">
      {/* map() creates a new array of JSX elements */}
      {fruits.map((fruit, index) => (
        // Use index as key ONLY if list is static (won't change)
        <li key={index} className="mb-1">
          {fruit}
        </li>
      ))}
    </ul>
  );
}
Using Unique IDs as Keys (Best Practice)
jsx
function UserList() {
  // Each user has a unique ID - perfect for keys
  const users = [
    { id: 1, name: 'John', email: 'john@example.com' },
    { id: 2, name: 'Jane', email: 'jane@example.com' },
    { id: 3, name: 'Bob', email: 'bob@example.com' }
  ];
  
  return (
    <div className="space-y-2">
      {users.map(user => (
        // Use unique ID as key - BEST PRACTICE
        <div key={user.id} className="border p-3 rounded">
          <p className="font-bold">{user.name}</p>
          <p className="text-gray-600">{user.email}</p>
        </div>
      ))}
    </div>
  );
}
Dynamic List with Add/Remove
jsx
function DynamicList() {
  const [items, setItems] = useState([
    { id: 1, text: 'Learn React' },
    { id: 2, text: 'Build a project' },
    { id: 3, text: 'Master JavaScript' }
  ]);
  const [newItem, setNewItem] = useState('');
  
  // Add new item with unique ID
  const addItem = () => {
    if (newItem.trim()) {
      setItems([
        ...items,
        { id: Date.now(), text: newItem } // Date.now() gives unique ID
      ]);
      setNewItem('');
    }
  };
  
  // Remove item by ID
  const removeItem = (id) => {
    setItems(items.filter(item => item.id !== id));
  };
  
  return (
    <div className="max-w-md">
      <div className="flex gap-2 mb-4">
        <input
          value={newItem}
          onChange={(e) => setNewItem(e.target.value)}
          className="border p-2 rounded flex-1"
          placeholder="Add new item..."
        />
        <button
          onClick={addItem}
          className="bg-blue-500 text-white px-4 py-2 rounded"
        >
          Add
        </button>
      </div>
      
      <ul className="space-y-2">
        {items.map(item => (
          <li key={item.id} className="flex justify-between items-center bg-gray-100 p-2 rounded">
            <span>{item.text}</span>
            <button
              onClick={() => removeItem(item.id)}
              className="text-red-500 hover:text-red-700"
            >
              Delete
            </button>
          </li>
        ))}
      </ul>
    </div>
  );
}
List with Complex Objects
jsx
function ProductCatalog() {
  const [products, setProducts] = useState([
    { id: 1, name: 'Laptop', price: 999, category: 'Electronics', inStock: true },
    { id: 2, name: 'Shirt', price: 29, category: 'Clothing', inStock: true },
    { id: 3, name: 'Book', price: 19, category: 'Books', inStock: false },
    { id: 4, name: 'Phone', price: 699, category: 'Electronics', inStock: true }
  ]);
  
  const [filter, setFilter] = useState('all');
  const [sortBy, setSortBy] = useState('name');
  
  // Filter products
  const filteredProducts = products.filter(product => {
    if (filter === 'inStock') return product.inStock;
    if (filter === 'outOfStock') return !product.inStock;
    return true;
  });
  
  // Sort products
  const sortedProducts = [...filteredProducts].sort((a, b) => {
    if (sortBy === 'price') return a.price - b.price;
    if (sortBy === 'name') return a.name.localeCompare(b.name);
    return 0;
  });
  
  return (
    <div className="max-w-4xl mx-auto p-4">
      <h1 className="text-2xl font-bold mb-4">Product Catalog</h1>
      
      {/* Filters */}
      <div className="flex gap-4 mb-4">
        <select
          value={filter}
          onChange={(e) => setFilter(e.target.value)}
          className="border p-2 rounded"
        >
          <option value="all">All Products</option>
          <option value="inStock">In Stock</option>
          <option value="outOfStock">Out of Stock</option>
        </select>
        
        <select
          value={sortBy}
          onChange={(e) => setSortBy(e.target.value)}
          className="border p-2 rounded"
        >
          <option value="name">Sort by Name</option>
          <option value="price">Sort by Price</option>
        </select>
      </div>
      
      {/* Product List */}
      <div className="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
        {sortedProducts.map(product => (
          <div key={product.id} className="border rounded-lg p-4 shadow-sm">
            <h3 className="font-bold text-lg mb-2">{product.name}</h3>
            <p className="text-gray-600">${product.price}</p>
            <p className="text-sm text-gray-500 mb-2">{product.category}</p>
            <span className={`inline-block px-2 py-1 rounded text-xs ${
              product.inStock 
                ? 'bg-green-100 text-green-700' 
                : 'bg-red-100 text-red-700'
            }`}>
              {product.inStock ? 'In Stock' : 'Out of Stock'}
            </span>
          </div>
        ))}
      </div>
      
      {/* Statistics */}
      <div className="mt-6 p-4 bg-gray-100 rounded">
        <p>Total Products: {products.length}</p>
        <p>In Stock: {products.filter(p => p.inStock).length}</p>
        <p>Out of Stock: {products.filter(p => !p.inStock).length}</p>
      </div>
    </div>
  );
}
List Rendering Patterns
jsx
function ListPatterns() {
  const [items, setItems] = useState([
    { id: 1, text: 'Item 1', completed: false },
    { id: 2, text: 'Item 2', completed: true },
    { id: 3, text: 'Item 3', completed: false }
  ]);
  
  // Pattern 1: Separate component for list item
  const TodoItem = ({ item, onToggle, onDelete }) => {
    return (
      <li className="flex items-center gap-2 p-2 border rounded">
        <input
          type="checkbox"
          checked={item.completed}
          onChange={() => onToggle(item.id)}
        />
        <span className={item.completed ? 'line-through text-gray-500 flex-1' : 'flex-1'}>
          {item.text}
        </span>
        <button
          onClick={() => onDelete(item.id)}
          className="text-red-500"
        >
          Delete
        </button>
      </li>
    );
  };
  
  // Pattern 2: Conditional rendering within list
  const getItemClass = (completed) => {
    return completed ? 'line-through text-gray-500' : '';
  };
  
  // Pattern 3: Empty state handling
  const EmptyState = () => (
    <div className="text-center py-8 text-gray-500">
      No items to display. Add some items!
    </div>
  );
  
  const handleToggle = (id) => {
    setItems(items.map(item =>
      item.id === id ? { ...item, completed: !item.completed } : item
    ));
  };
  
  const handleDelete = (id) => {
    setItems(items.filter(item => item.id !== id));
  };
  
  return (
    <div className="max-w-md mx-auto">
      <h2 className="text-xl font-bold mb-4">Todo List</h2>
      
      {/* List with conditional empty state */}
      {items.length === 0 ? (
        <EmptyState />
      ) : (
        <ul className="space-y-2">
          {items.map(item => (
            <TodoItem
              key={item.id}
              item={item}
              onToggle={handleToggle}
              onDelete={handleDelete}
            />
          ))}
        </ul>
      )}
      
      {/* Statistics */}
      <div className="mt-4 text-sm text-gray-600">
        <p>Total: {items.length}</p>
        <p>Completed: {items.filter(i => i.completed).length}</p>
        <p>Pending: {items.filter(i => !i.completed).length}</p>
      </div>
    </div>
  );
}
Key Rules and Best Practices
jsx
function KeyRules() {
  const items = [
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' },
    { id: 3, name: 'Item 3' }
  ];
  
  // ✅ GOOD: Using unique IDs
  const goodExample = items.map(item => (
    <div key={item.id}>{item.name}</div>
  ));
  
  // ⚠️ OK: Using index (only if list never changes)
  const okayExample = items.map((item, index) => (
    <div key={index}>{item.name}</div>
  ));
  
  // ❌ BAD: Using random values
  const badExample = items.map(item => (
    <div key={Math.random()}>{item.name}</div> // New key on every render!
  ));
  
  // ❌ BAD: Using array index when list can change
  const [dynamicItems, setDynamicItems] = useState(items);
  // If you delete the first item, keys shift and React gets confused
  
  return null;
}
10. Conditional Rendering - Showing/Hiding Content
What is Conditional Rendering?
Conditional rendering means showing different UI based on certain conditions (like if a user is logged in, if data is loading, etc.)

5 Ways to Conditionally Render
jsx
function ConditionalRendering() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [isLoading, setIsLoading] = useState(false);
  const [userRole, setUserRole] = useState('guest');
  const [items, setItems] = useState([]);
  
  // 1. If/Else Statement (for complex logic)
  const renderHeader = () => {
    if (isLoggedIn) {
      return <div>Welcome back, User!</div>;
    } else {
      return <div>Please log in</div>;
    }
  };
  
  // 2. Ternary Operator (for simple conditions)
  const renderLoginButton = () => {
    return (
      <button onClick={() => setIsLoggedIn(!isLoggedIn)}>
        {isLoggedIn ? 'Logout' : 'Login'}
      </button>
    );
  };
  
  // 3. && Operator (show/hide based on condition)
  const renderLoading = () => {
    return isLoading && <div className="spinner">Loading...</div>;
  };
  
  // 4. Switch Statement (multiple conditions)
  const renderRoleMessage = () => {
    switch(userRole) {
      case 'admin':
        return <div className="text-red-500">Admin Access: Full permissions</div>;
      case 'editor':
        return <div className="text-blue-500">Editor Access: Can edit content</div>;
      case 'viewer':
        return <div className="text-green-500">Viewer Access: Read only</div>;
      default:
        return <div className="text-gray-500">Guest Access: Limited features</div>;
    }
  };
  
  // 5. Variable Assignment (store JSX in variable)
  const getMessage = () => {
    let message;
    if (items.length === 0) {
      message = <p>No items found. Add some items!</p>;
    } else if (items.length < 5) {
      message = <p>You have {items.length} items. Add more!</p>;
    } else {
      message = <p>Great! You have plenty of items.</p>;
    }
    return message;
  };
  
  return (
    <div className="p-4 space-y-4">
      <h1 className="text-2xl font-bold">Conditional Rendering Examples</h1>
      
      {/* Example 1: If/Else */}
      <div className="border p-4 rounded">
        <h2 className="font-bold">1. If/Else</h2>
        {renderHeader()}
        {renderLoginButton()}
      </div>
      
      {/* Example 2: Ternary */}
      <div className="border p-4 rounded">
        <h2 className="font-bold">2. Ternary Operator</h2>
        <button
          onClick={() => setIsLoading(!isLoading)}
          className="bg-blue-500 text-white px-3 py-1 rounded"
        >
          Toggle Loading
        </button>
        {isLoading ? (
          <div className="mt-2 text-yellow-600">Loading data...</div>
        ) : (
          <div className="mt-2 text-green-600">Data loaded!</div>
        )}
      </div>
      
      {/* Example 3: && Operator */}
      <div className="border p-4 rounded">
        <h2 className="font-bold">3. && Operator</h2>
        <button
          onClick={() => setIsLoading(!isLoading)}
          className="bg-blue-500 text-white px-3 py-1 rounded"
        >
          Toggle Loading
        </button>
        {isLoading && (
          <div className="mt-2 text-blue-600">
            <div className="animate-pulse">Loading spinner...</div>
          </div>
        )}
      </div>
      
      {/* Example 4: Switch */}
      <div className="border p-4 rounded">
        <h2 className="font-bold">4. Switch Statement</h2>
        <div className="flex gap-2 mb-2">
          <button onClick={() => setUserRole('admin')} className="bg-red-500 text-white px-2 py-1 rounded">Admin</button>
          <button onClick={() => setUserRole('editor')} className="bg-blue-500 text-white px-2 py-1 rounded">Editor</button>
          <button onClick={() => setUserRole('viewer')} className="bg-green-500 text-white px-2 py-1 rounded">Viewer</button>
          <button onClick={() => setUserRole('guest')} className="bg-gray-500 text-white px-2 py-1 rounded">Guest</button>
        </div>
        {renderRoleMessage()}
      </div>
      
      {/* Example 5: Variable Assignment */}
      <div className="border p-4 rounded">
        <h2 className="font-bold">5. Variable Assignment</h2>
        <button
          onClick={() => setItems([...items, `Item ${items.length + 1}`])}
          className="bg-blue-500 text-white px-3 py-1 rounded mr-2"
        >
          Add Item
        </button>
        <button
          onClick={() => setItems([])}
          className="bg-red-500 text-white px-3 py-1 rounded"
        >
          Clear All
        </button>
        <div className="mt-2">{getMessage()}</div>
        <ul className="mt-2 list-disc pl-5">
          {items.map((item, i) => (
            <li key={i}>{item}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}
Real-World Conditional Rendering Examples
jsx
function RealWorldExamples() {
  const [isAuthenticated, setIsAuthenticated] = useState(false);
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState(null);
  const [data, setData] = useState(null);
  const [isModalOpen, setIsModalOpen] = useState(false);
  
  // Simulate API call
  const fetchData = async () => {
    setIsLoading(true);
    setError(null);
    
    try {
      await new Promise(resolve => setTimeout(resolve, 2000));
      // Simulate random error
      if (Math.random() < 0.3) {
        throw new Error('Failed to fetch data');
      }
      setData({ message: 'Data loaded successfully!' });
    } catch (err) {
      setError(err.message);
    } finally {
      setIsLoading(false);
    }
  };
  
  return (
    <div className="max-w-2xl mx-auto p-4 space-y-6">
      {/* Example 1: Authentication */}
      <div className="border rounded-lg p-4">
        <h2 className="font-bold mb-2">1. Authentication State</h2>
        {!isAuthenticated ? (
          <div>
            <p className="mb-2">You are not logged in.</p>
            <button
              onClick={() => setIsAuthenticated(true)}
              className="bg-blue-500 text-white px-4 py-2 rounded"
            >
              Login
            </button>
          </div>
        ) : (
          <div>
            <p className="mb-2 text-green-600">Welcome back! You are logged in.</p>
            <button
              onClick={() => setIsAuthenticated(false)}
              className="bg-red-500 text-white px-4 py-2 rounded"
            >
              Logout
            </button>
          </div>
        )}
      </div>
      
      {/* Example 2: Loading/Error/Success States */}
      <div className="border rounded-lg p-4">
        <h2 className="font-bold mb-2">2. Data Fetching States</h2>
        <button
          onClick={fetchData}
          disabled={isLoading}
          className="bg-blue-500 text-white px-4 py-2 rounded mb-3 disabled:opacity-50"
        >
          {isLoading ? 'Loading...' : 'Fetch Data'}
        </button>
        
        {/* Loading State */}
        {isLoading && (
          <div className="bg-blue-100 text-blue-700 p-3 rounded">
            Loading data, please wait...
          </div>
        )}
        
        {/* Error State */}
        {error && (
          <div className="bg-red-100 text-red-700 p-3 rounded">
            Error: {error}
            <button
              onClick={() => setError(null)}
              className="ml-2 text-red-700 underline"
            >
              Dismiss
            </button>
          </div>
        )}
        
        {/* Success State */}
        {data && !isLoading && !error && (
          <div className="bg-green-100 text-green-700 p-3 rounded">
            {data.message}
          </div>
        )}
      </div>
      
      {/* Example 3: Modal with Conditional */}
      <div className="border rounded-lg p-4">
        <h2 className="font-bold mb-2">3. Modal Dialog</h2>
        <button
          onClick={() => setIsModalOpen(true)}
          className="bg-blue-500 text-white px-4 py-2 rounded"
        >
          Open Modal
        </button>
        
        {/* Modal - Only renders when isModalOpen is true */}
        {isModalOpen && (
          <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center">
            <div className="bg-white rounded-lg p-6 max-w-md w-full">
              <h3 className="text-xl font-bold mb-4">Modal Title</h3>
              <p className="mb-4">This is a modal dialog. Click outside or press ESC to close.</p>
              <button
                onClick={() => setIsModalOpen(false)}
                className="bg-gray-500 text-white px-4 py-2 rounded"
              >
                Close
              </button>
            </div>
          </div>
        )}
      </div>
      
      {/* Example 4: Feature Flags */}
      <div className="border rounded-lg p-4">
        <h2 className="font-bold mb-2">4. Feature Flags (A/B Testing)</h2>
        <div className="space-y-2">
          {process.env.NODE_ENV === 'development' && (
            <div className="bg-yellow-100 text-yellow-700 p-2 rounded">
              ⚠️ Development Mode: Extra debugging info shown
            </div>
          )}
          
          {/* Only show beta features to certain users */}
          {isAuthenticated && (
            <div className="bg-purple-100 text-purple-700 p-2 rounded">
              🚀 Beta Feature: Try our new dashboard!
            </div>
          )}
        </div>
      </div>
      
      {/* Example 5: Multi-step Form */}
      <div className="border rounded-lg p-4">
        <h2 className="font-bold mb-2">5. Multi-step Form</h2>
        <MultiStepForm />
      </div>
    </div>
  );
}

// Multi-step Form Component
function MultiStepForm() {
  const [step, setStep] = useState(1);
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    interests: []
  });
  
  const nextStep = () => setStep(step + 1);
  const prevStep = () => setStep(step - 1);
  
  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    if (type === 'checkbox') {
      if (checked) {
        setFormData({
          ...formData,
          interests: [...formData.interests, value]
        });
      } else {
        setFormData({
          ...formData,
          interests: formData.interests.filter(i => i !== value)
        });
      }
    } else {
      setFormData({ ...formData, [name]: value });
    }
  };
  
  const handleSubmit = () => {
    alert('Form submitted: ' + JSON.stringify(formData, null, 2));
    setStep(1);
    setFormData({ name: '', email: '', interests: [] });
  };
  
  return (
    <div>
      {/* Step 1: Personal Info */}
      {step === 1 && (
        <div className="space-y-4">
          <div>
            <label className="block mb-1">Name:</label>
            <input
              type="text"
              name="name"
              value={formData.name}
              onChange={handleChange}
              className="border p-2 rounded w-full"
            />
          </div>
          <div>
            <label className="block mb-1">Email:</label>
            <input
              type="email"
              name="email"
              value={formData.email}
              onChange={handleChange}
              className="border p-2 rounded w-full"
            />
          </div>
          <button
            onClick={nextStep}
            disabled={!formData.name || !formData.email}
            className="bg-blue-500 text-white px-4 py-2 rounded disabled:opacity-50"
          >
            Next
          </button>
        </div>
      )}
      
      {/* Step 2: Interests */}
      {step === 2 && (
        <div className="space-y-4">
          <div>
            <label className="block mb-2">Interests:</label>
            <div className="space-y-2">
              {['Coding', 'Design', 'Music', 'Sports'].map(interest => (
                <label key={interest} className="flex items-center">
                  <input
                    type="checkbox"
                    value={interest}
                    checked={formData.interests.includes(interest)}
                    onChange={handleChange}
                    className="mr-2"
                  />
                  {interest}
                </label>
              ))}
            </div>
          </div>
          <div className="flex gap-2">
            <button onClick={prevStep} className="bg-gray-500 text-white px-4 py-2 rounded">
              Previous
            </button>
            <button onClick={nextStep} className="bg-blue-500 text-white px-4 py-2 rounded">
              Next
            </button>
          </div>
        </div>
      )}
      
      {/* Step 3: Review */}
      {step === 3 && (
        <div className="space-y-4">
          <div className="bg-gray-100 p-4 rounded">
            <p><strong>Name:</strong> {formData.name}</p>
            <p><strong>Email:</strong> {formData.email}</p>
            <p><strong>Interests:</strong> {formData.interests.join(', ') || 'None'}</p>
          </div>
          <div className="flex gap-2">
            <button onClick={prevStep} className="bg-gray-500 text-white px-4 py-2 rounded">
              Previous
            </button>
            <button onClick={handleSubmit} className="bg-green-500 text-white px-4 py-2 rounded">
              Submit
            </button>
          </div>
        </div>
      )}
      
      {/* Progress indicator */}
      <div className="mt-4 flex gap-2">
        {[1, 2, 3].map(s => (
          <div
            key={s}
            className={`h-2 flex-1 rounded ${
              s <= step ? 'bg-blue-500' : 'bg-gray-300'
            }`}
          />
        ))}
      </div>
    </div>
  );
}
11. Forms and User Input - Collecting Data
Complete Form Handling Guide
Forms are how users interact with your app - logging in, signing up, searching, etc.

Controlled Components (Recommended)
Controlled components have their value controlled by React state.

jsx
function ControlledForm() {
  // State for each form field
  const [formData, setFormData] = useState({
    username: '',
    email: '',
    password: '',
    confirmPassword: '',
    age: '',
    country: '',
    agreeToTerms: false
  });
  
  // State for validation errors
  const [errors, setErrors] = useState({});
  
  // State for submission
  const [isSubmitting, setIsSubmitting] = useState(false);
  
  // Handle input changes
  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    
    // Update state based on input type
    setFormData({
      ...formData,
      [name]: type === 'checkbox' ? checked : value
    });
    
    // Clear error for this field when user types
    if (errors[name]) {
      setErrors({
        ...errors,
        [name]: ''
      });
    }
  };
  
  // Validate form
  const validateForm = () => {
    const newErrors = {};
    
    // Username validation
    if (!formData.username) {
      newErrors.username = 'Username is required';
    } else if (formData.username.length < 3) {
      newErrors.username = 'Username must be at least 3 characters';
    }
    
    // Email validation
    if (!formData.email) {
      newErrors.email = 'Email is required';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Email is invalid';
    }
    
    // Password validation
    if (!formData.password) {
      newErrors.password = 'Password is required';
    } else if (formData.password.length < 6) {
      newErrors.password = 'Password must be at least 6 characters';
    }
    
    // Confirm password validation
    if (formData.password !== formData.confirmPassword) {
      newErrors.confirmPassword = 'Passwords do not match';
    }
    
    // Age validation
    if (formData.age && (formData.age < 18 || formData.age > 100)) {
      newErrors.age = 'Age must be between 18 and 100';
    }
    
    // Terms validation
    if (!formData.agreeToTerms) {
      newErrors.agreeToTerms = 'You must agree to the terms';
    }
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };
  
  // Handle form submission
  const handleSubmit = async (e) => {
    e.preventDefault(); // IMPORTANT: Prevent page refresh
    
    // Validate before submitting
    if (!validateForm()) {
      return;
    }
    
    setIsSubmitting(true);
    
    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 2000));
      
      console.log('Form submitted:', formData);
      alert('Registration successful!');
      
      // Reset form after successful submission
      setFormData({
        username: '',
        email: '',
        password: '',
        confirmPassword: '',
        age: '',
        country: '',
        agreeToTerms: false
      });
    } catch (error) {
      alert('Registration failed. Please try again.');
    } finally {
      setIsSubmitting(false);
    }
  };
  
  return (
    <form onSubmit={handleSubmit} className="max-w-md mx-auto p-6 bg-white rounded-lg shadow-md">
      <h2 className="text-2xl font-bold mb-6 text-center">Register Account</h2>
      
      {/* Username Field */}
      <div className="mb-4">
        <label className="block text-gray-700 mb-2">Username *</label>
        <input
          type="text"
          name="username"
          value={formData.username}
          onChange={handleChange}
          className={`w-full p-2 border rounded focus:outline-none focus:ring-2 ${
            errors.username ? 'border-red-500 focus:ring-red-200' : 'border-gray-300 focus:ring-blue-200'
          }`}
          placeholder="Enter username"
        />
        {errors.username && (
          <p className="text-red-500 text-sm mt-1">{errors.username}</p>
        )}
      </div>
      
      {/* Email Field */}
      <div className="mb-4">
        <label className="block text-gray-700 mb-2">Email *</label>
        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={handleChange}
          className={`w-full p-2 border rounded focus:outline-none focus:ring-2 ${
            errors.email ? 'border-red-500 focus:ring-red-200' : 'border-gray-300 focus:ring-blue-200'
          }`}
          placeholder="Enter email"
        />
        {errors.email && (
          <p className="text-red-500 text-sm mt-1">{errors.email}</p>
        )}
      </div>
      
      {/* Password Field */}
      <div className="mb-4">
        <label className="block text-gray-700 mb-2">Password *</label>
        <input
          type="password"
          name="password"
          value={formData.password}
          onChange={handleChange}
          className={`w-full p-2 border rounded focus:outline-none focus:ring-2 ${
            errors.password ? 'border-red-500 focus:ring-red-200' : 'border-gray-300 focus:ring-blue-200'
          }`}
          placeholder="Enter password"
        />
        {errors.password && (
          <p className="text-red-500 text-sm mt-1">{errors.password}</p>
        )}
      </div>
      
      {/* Confirm Password Field */}
      <div className="mb-4">
        <label className="block text-gray-700 mb-2">Confirm Password *</label>
        <input
          type="password"
          name="confirmPassword"
          value={formData.confirmPassword}
          onChange={handleChange}
          className={`w-full p-2 border rounded focus:outline-none focus:ring-2 ${
            errors.confirmPassword ? 'border-red-500 focus:ring-red-200' : 'border-gray-300 focus:ring-blue-200'
          }`}
          placeholder="Confirm password"
        />
        {errors.confirmPassword && (
          <p className="text-red-500 text-sm mt-1">{errors.confirmPassword}</p>
        )}
      </div>
      
      {/* Age Field */}
      <div className="mb-4">
        <label className="block text-gray-700 mb-2">Age (Optional)</label>
        <input
          type="number"
          name="age"
          value={formData.age}
          onChange={handleChange}
          className="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-200"
          placeholder="Enter age"
        />
        {errors.age && (
          <p className="text-red-500 text-sm mt-1">{errors.age}</p>
        )}
      </div>
      
      {/* Country Select */}
      <div className="mb-4">
        <label className="block text-gray-700 mb-2">Country</label>
        <select
          name="country"
          value={formData.country}
          onChange={handleChange}
          className="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-200"
        >
          <option value="">Select a country</option>
          <option value="usa">United States</option>
          <option value="canada">Canada</option>
          <option value="uk">United Kingdom</option>
          <option value="australia">Australia</option>
        </select>
      </div>
      
      {/* Terms Checkbox */}
      <div className="mb-6">
        <label className="flex items-center">
          <input
            type="checkbox"
            name="agreeToTerms"
            checked={formData.agreeToTerms}
            onChange={handleChange}
            className="mr-2"
          />
          <span className="text-gray-700">I agree to the Terms and Conditions *</span>
        </label>
        {errors.agreeToTerms && (
          <p className="text-red-500 text-sm mt-1">{errors.agreeToTerms}</p>
        )}
      </div>
      
      {/* Submit Button */}
      <button
        type="submit"
        disabled={isSubmitting}
        className="w-full bg-blue-500 text-white py-2 rounded hover:bg-blue-600 transition disabled:opacity-50"
      >
        {isSubmitting ? 'Registering...' : 'Register'}
      </button>
    </form>
  );
}
Different Input Types
jsx
function InputTypes() {
  const [form, setForm] = useState({
    text: '',
    email: '',
    password: '',
    number: 0,
    tel: '',
    url: '',
    date: '',
    time: '',
    datetime: '',
    month: '',
    week: '',
    color: '#000000',
    range: 50,
    checkbox: false,
    radio: '',
    textarea: '',
    select: ''
  });
  
  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    setForm({
      ...form,
      [name]: type === 'checkbox' ? checked : value
    });
  };
  
  return (
    <div className="max-w-md mx-auto p-4 space-y-4">
      {/* Text Input */}
      <div>
        <label className="block mb-1">Text Input:</label>
        <input
          type="text"
          name="text"
          value={form.text}
          onChange={handleChange}
          className="border p-2 rounded w-full"
          placeholder="Enter text"
        />
      </div>
      
      {/* Email Input */}
      <div>
        <label className="block mb-1">Email Input:</label>
        <input
          type="email"
          name="email"
          value={form.email}
          onChange={handleChange}
          className="border p-2 rounded w-full"
          placeholder="example@email.com"
        />
      </div>
      
      {/* Password Input */}
      <div>
        <label className="block mb-1">Password Input:</label>
        <input
          type="password"
          name="password"
          value={form.password}
          onChange={handleChange}
          className="border p-2 rounded w-full"
          placeholder="Enter password"
        />
      </div>
      
      {/* Number Input */}
      <div>
        <label className="block mb-1">Number Input:</label>
        <input
          type="number"
          name="number"
          value={form.number}
          onChange={handleChange}
          className="border p-2 rounded w-full"
          min="0"
          max="100"
        />
      </div>
      
      {/* Date Input */}
      <div>
        <label className="block mb-1">Date Input:</label>
        <input
          type="date"
          name="date"
          value={form.date}
          onChange={handleChange}
          className="border p-2 rounded w-full"
        />
      </div>
      
      {/* Color Input */}
      <div>
        <label className="block mb-1">Color Input:</label>
        <input
          type="color"
          name="color"
          value={form.color}
          onChange={handleChange}
          className="border p-2 rounded w-full h-10"
        />
      </div>
      
      {/* Range Input */}
      <div>
        <label className="block mb-1">Range Input: {form.range}</label>
        <input
          type="range"
          name="range"
          value={form.range}
          onChange={handleChange}
          className="w-full"
          min="0"
          max="100"
        />
      </div>
      
      {/* Checkbox */}
      <div>
        <label className="flex items-center">
          <input
            type="checkbox"
            name="checkbox"
            checked={form.checkbox}
            onChange={handleChange}
            className="mr-2"
          />
          Checkbox
        </label>
      </div>
      
      {/* Radio Buttons */}
      <div>
        <label className="block mb-1">Radio Buttons:</label>
        <label className="mr-4">
          <input
            type="radio"
            name="radio"
            value="option1"
            checked={form.radio === 'option1'}
            onChange={handleChange}
            className="mr-1"
          />
          Option 1
        </label>
        <label>
          <input
            type="radio"
            name="radio"
            value="option2"
            checked={form.radio === 'option2'}
            onChange={handleChange}
            className="mr-1"
          />
          Option 2
        </label>
      </div>
      
      {/* Textarea */}
      <div>
        <label className="block mb-1">Textarea:</label>
        <textarea
          name="textarea"
          value={form.textarea}
          onChange={handleChange}
          rows="3"
          className="border p-2 rounded w-full"
          placeholder="Enter multiple lines..."
        />
      </div>
      
      {/* Select Dropdown */}
      <div>
        <label className="block mb-1">Select Dropdown:</label>
        <select
          name="select"
          value={form.select}
          onChange={handleChange}
          className="border p-2 rounded w-full"
        >
          <option value="">Choose an option</option>
          <option value="option1">Option 1</option>
          <option value="option2">Option 2</option>
          <option value="option3">Option 3</option>
        </select>
      </div>
      
      {/* Display current form data */}
      <div className="bg-gray-100 p-4 rounded mt-4">
        <h3 className="font-bold mb-2">Current Form Data:</h3>
        <pre className="text-sm">{JSON.stringify(form, null, 2)}</pre>
      </div>
    </div>
  );
}
12. useEffect - Side Effects in Components
What is useEffect?
useEffect is a hook that lets you perform side effects in functional components. Side effects are things like:

Fetching data from an API

Updating the document title

Setting up timers or intervals

Subscribing to events

Working with localStorage

Understanding useEffect
jsx
import { useState, useEffect } from 'react';

function UseEffectBasics() {
  const [count, setCount] = useState(0);
  const [name, setName] = useState('');
  
  // 1. Effect runs after EVERY render (including the first one)
  useEffect(() => {
    console.log('This runs after every render');
  });
  
  // 2. Effect runs ONLY ONCE (when component mounts)
  useEffect(() => {
    console.log('This runs only once when component first renders');
    
    // Optional cleanup function (runs when component unmounts)
    return () => {
      console.log('Cleanup: component is unmounting');
    };
  }, []); // Empty dependency array = run once
  
  // 3. Effect runs when specific dependencies change
  useEffect(() => {
    console.log(`Count changed to: ${count}`);
    document.title = `Count: ${count}`;
  }, [count]); // Only runs when count changes
  
  // 4. Effect runs when multiple dependencies change
  useEffect(() => {
    console.log('Either count or name changed');
  }, [count, name]); // Runs when count OR name changes
  
  return (
    <div className="p-4">
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      
      <input
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter name"
        className="border p-2 rounded ml-2"
      />
    </div>
  );
}
Common useEffect Patterns
jsx
function UseEffectPatterns() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  const [searchTerm, setSearchTerm] = useState('');
  const [debouncedTerm, setDebouncedTerm] = useState('');
  const [seconds, setSeconds] = useState(0);
  
  // Pattern 1: Data fetching on mount
  useEffect(() => {
    const fetchData = async () => {
      try {
        setLoading(true);
        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
        const result = await response.json();
        setData(result);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    };
    
    fetchData();
  }, []); // Empty array = runs once on mount
  
  // Pattern 2: Debounced search (wait for user to stop typing)
  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedTerm(searchTerm);
    }, 500); // Wait 500ms after user stops typing
    
    return () => clearTimeout(timer); // Cleanup previous timeout
  }, [searchTerm]);
  
  // Pattern 3: Timer with cleanup
  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(prev => prev + 1);
    }, 1000);
    
    return () => clearInterval(interval); // Cleanup interval
  }, []);
  
  // Pattern 4: Event listener
  useEffect(() => {
    const handleResize = () => {
      console.log('Window resized:', window.innerWidth);
    };
    
    window.addEventListener('resize', handleResize);
    
    return () => window.removeEventListener('resize', handleResize);
  }, []);
  
  // Pattern 5: Local storage sync
  useEffect(() => {
    const savedData = localStorage.getItem('myData');
    if (savedData) {
      setData(JSON.parse(savedData));
    }
  }, []);
  
  useEffect(() => {
    if (data) {
      localStorage.setItem('myData', JSON.stringify(data));
    }
  }, [data]);
  
  // Pattern 6: Fetch when search term changes
  useEffect(() => {
    if (debouncedTerm) {
      const fetchSearch = async () => {
        const response = await fetch(`https://api.example.com/search?q=${debouncedTerm}`);
        const results = await response.json();
        console.log('Search results:', results);
      };
      
      fetchSearch();
    }
  }, [debouncedTerm]);
  
  return (
    <div className="p-4 space-y-4">
      <div>
        <h2 className="font-bold">Data Fetching:</h2>
        {loading && <p>Loading...</p>}
        {error && <p className="text-red-500">Error: {error}</p>}
        {data && <pre>{JSON.stringify(data, null, 2)}</pre>}
      </div>
      
      <div>
        <h2 className="font-bold">Search with Debounce:</h2>
        <input
          type="text"
          value={searchTerm}
          onChange={(e) => setSearchTerm(e.target.value)}
          className="border p-2 rounded w-full"
          placeholder="Type to search..."
        />
        <p className="text-sm text-gray-500 mt-1">
          Searching for: {debouncedTerm || 'nothing yet'}
        </p>
      </div>
      
      <div>
        <h2 className="font-bold">Timer:</h2>
        <p>Seconds elapsed: {seconds}</p>
      </div>
    </div>
  );
}
Real-World useEffect Examples
jsx
function RealWorldUseEffect() {
  const [users, setUsers] = useState([]);
  const [posts, setPosts] = useState([]);
  const [selectedUserId, setSelectedUserId] = useState(null);
  const [isLoading, setIsLoading] = useState(false);
  const [isOnline, setIsOnline] = useState(navigator.onLine);
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  
  // Example 1: Fetch users on component mount
  useEffect(() => {
    const fetchUsers = async () => {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users');
        const data = await response.json();
        setUsers(data);
      } catch (error) {
        console.error('Error fetching users:', error);
      }
    };
    
    fetchUsers();
  }, []); // Runs once
  
  // Example 2: Fetch posts when selected user changes
  useEffect(() => {
    if (!selectedUserId) return;
    
    const fetchPosts = async () => {
      setIsLoading(true);
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${selectedUserId}`);
        const data = await response.json();
        setPosts(data);
      } catch (error) {
        console.error('Error fetching posts:', error);
      } finally {
        setIsLoading(false);
      }
    };
    
    fetchPosts();
  }, [selectedUserId]); // Runs when selectedUserId changes
  
  // Example 3: Online/offline status
  useEffect(() => {
    const handleOnline = () => setIsOnline(true);
    const handleOffline = () => setIsOnline(false);
    
    window.addEventListener('online', handleOnline);
    window.addEventListener('offline', handleOffline);
    
    return () => {
      window.removeEventListener('online', handleOnline);
      window.removeEventListener('offline', handleOffline);
    };
  }, []);
  
  // Example 4: Track mouse position
  useEffect(() => {
    const handleMouseMove = (e) => {
      setMousePosition({ x: e.clientX, y: e.clientY });
    };
    
    window.addEventListener('mousemove', handleMouseMove);
    
    return () => window.removeEventListener('mousemove', handleMouseMove);
  }, []);
  
  // Example 5: Save to localStorage when posts change
  useEffect(() => {
    if (posts.length > 0) {
      localStorage.setItem('cachedPosts', JSON.stringify(posts));
    }
  }, [posts]);
  
  // Example 6: Load cached posts from localStorage on mount
  useEffect(() => {
    const cachedPosts = localStorage.getItem('cachedPosts');
    if (cachedPosts) {
      setPosts(JSON.parse(cachedPosts));
    }
  }, []);
  
  return (
    <div className="max-w-4xl mx-auto p-4">
      {/* Online Status Indicator */}
      <div className={`mb-4 p-2 rounded text-center ${
        isOnline ? 'bg-green-100 text-green-700' : 'bg-red-100 text-red-700'
      }`}>
        {isOnline ? '🟢 Online' : '🔴 Offline'}
      </div>
      
      {/* Mouse Position */}
      <div className="mb-4 text-sm text-gray-600">
        Mouse Position: ({mousePosition.x}, {mousePosition.y})
      </div>
      
      {/* User List */}
      <div className="mb-6">
        <h2 className="text-xl font-bold mb-3">Users</h2>
        <div className="grid gap-2 md:grid-cols-2">
          {users.map(user => (
            <button
              key={user.id}
              onClick={() => setSelectedUserId(user.id)}
              className={`p-3 text-left rounded transition ${
                selectedUserId === user.id
                  ? 'bg-blue-500 text-white'
                  : 'bg-gray-100 hover:bg-gray-200'
              }`}
            >
              {user.name}
            </button>
          ))}
        </div>
      </div>
      
      {/* Posts for Selected User */}
      {selectedUserId && (
        <div>
          <h2 className="text-xl font-bold mb-3">
            Posts by {users.find(u => u.id === selectedUserId)?.name}
          </h2>
          
          {isLoading ? (
            <div className="text-center py-8">Loading posts...</div>
          ) : posts.length === 0 ? (
            <div className="text-center py-8 text-gray-500">No posts found</div>
          ) : (
            <div className="space-y-4">
              {posts.map(post => (
                <div key={post.id} className="border rounded-lg p-4">
                  <h3 className="font-bold text-lg mb-2">{post.title}</h3>
                  <p className="text-gray-600">{post.body}</p>
                </div>
              ))}
            </div>
          )}
        </div>
      )}
    </div>
  );
}
useEffect Cleanup Examples
jsx
function UseEffectCleanup() {
  const [showTimer, setShowTimer] = useState(true);
  
  return (
    <div className="p-4">
      <button
        onClick={() => setShowTimer(!showTimer)}
        className="bg-blue-500 text-white px-4 py-2 rounded mb-4"
      >
        {showTimer ? 'Hide' : 'Show'} Timer
      </button>
      
      {showTimer && <TimerComponent />}
    </div>
  );
}

function TimerComponent() {
  const [seconds, setSeconds] = useState(0);
  
  useEffect(() => {
    console.log('Timer component mounted');
    
    // Set up interval
    const interval = setInterval(() => {
      setSeconds(prev => prev + 1);
      console.log('Timer tick:', seconds + 1);
    }, 1000);
    
    // Cleanup function - runs when component unmounts
    return () => {
      console.log('Timer component unmounting - cleaning up interval');
      clearInterval(interval);
    };
  }, []); // Empty dependency array
  
  return (
    <div className="border p-4 rounded">
      <h2 className="text-xl font-bold">Timer: {seconds} seconds</h2>
      <p className="text-sm text-gray-500">
        This timer will be cleaned up when component unmounts
      </p>
    </div>
  );
}
13. Fetching Data from APIs - Getting External Data
What is API Fetching?
API fetching is how your React app gets data from servers (like getting user profiles, posts, weather data, etc.)

Simple API Fetching
jsx
import { useState, useEffect } from 'react';

function SimpleAPIFetching() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  // Fetch data when component loads
  useEffect(() => {
    // Using fetch API (built into browser)
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        // Check if response is ok
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json(); // Parse JSON
      })
      .then(data => {
        setUsers(data); // Save data to state
        setLoading(false); // Stop loading
      })
      .catch(error => {
        setError(error.message); // Save error
        setLoading(false); // Stop loading
      });
  }, []); // Empty array = run once
  
  // Show loading state
  if (loading) {
    return (
      <div className="flex justify-center items-center h-64">
        <div className="text-xl">Loading users...</div>
      </div>
    );
  }
  
  // Show error state
  if (error) {
    return (
      <div className="bg-red-100 text-red-700 p-4 rounded">
        Error: {error}
      </div>
    );
  }
  
  // Show data
  return (
    <div className="p-4">
      <h1 className="text-2xl font-bold mb-4">Users</h1>
      <div className="grid gap-4 md:grid-cols-2">
        {users.map(user => (
          <div key={user.id} className="border rounded-lg p-4">
            <h2 className="font-bold text-lg">{user.name}</h2>
            <p className="text-gray-600">Email: {user.email}</p>
            <p className="text-gray-600">Phone: {user.phone}</p>
          </div>
        ))}
      </div>
    </div>
  );
}
Async/Await Syntax (Cleaner)
jsx
function AsyncAwaitFetching() {
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    // Async function inside useEffect
    const fetchPosts = async () => {
      try {
        setLoading(true);
        
        // Wait for fetch to complete
        const response = await fetch('https://jsonplaceholder.typicode.com/posts');
        
        // Check if response is ok
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        // Wait for JSON parsing
        const data = await response.json();
        
        // Save data
        setPosts(data.slice(0, 10)); // Get first 10 posts
        setError(null);
      } catch (err) {
        // Handle any errors
        setError(err.message);
      } finally {
        // Always stop loading
        setLoading(false);
      }
    };
    
    fetchPosts(); // Call the function
  }, []);
  
  if (loading) return <div className="text-center p-8">Loading posts...</div>;
  if (error) return <div className="text-red-500 p-8">Error: {error}</div>;
  
  return (
    <div className="p-4">
      <h1 className="text-2xl font-bold mb-4">Posts</h1>
      <div className="space-y-4">
        {posts.map(post => (
          <div key={post.id} className="border rounded-lg p-4">
            <h2 className="font-bold text-lg mb-2">{post.title}</h2>
            <p className="text-gray-600">{post.body}</p>
          </div>
        ))}
      </div>
    </div>
  );
}
POST Request (Sending Data)
jsx
function CreatePost() {
  const [title, setTitle] = useState('');
  const [body, setBody] = useState('');
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [response, setResponse] = useState(null);
  const [error, setError] = useState(null);
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    
    setIsSubmitting(true);
    setError(null);
    
    try {
      // Send POST request
      const res = await fetch('https://jsonplaceholder.typicode.com/posts', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          title: title,
          body: body,
          userId: 1,
        }),
      });
      
      if (!res.ok) {
        throw new Error('Failed to create post');
      }
      
      const data = await res.json();
      setResponse(data);
      
      // Clear form
      setTitle('');
      setBody('');
      
    } catch (err) {
      setError(err.message);
    } finally {
      setIsSubmitting(false);
    }
  };
  
  return (
    <div className="max-w-md mx-auto p-4">
      <h1 className="text-2xl font-bold mb-4">Create New Post</h1>
      
      <form onSubmit={handleSubmit} className="space-y-4">
        <div>
          <label className="block mb-1">Title:</label>
          <input
            type="text"
            value={title}
            onChange={(e) => setTitle(e.target.value)}
            className="w-full border p-2 rounded"
            required
          />
        </div>
        
        <div>
          <label className="block mb-1">Content:</label>
          <textarea
            value={body}
            onChange={(e) => setBody(e.target.value)}
            rows="5"
            className="w-full border p-2 rounded"
            required
          />
        </div>
        
        <button
          type="submit"
          disabled={isSubmitting}
          className="w-full bg-blue-500 text-white py-2 rounded hover:bg-blue-600 disabled:opacity-50"
        >
          {isSubmitting ? 'Creating...' : 'Create Post'}
        </button>
        
        {error && (
          <div className="bg-red-100 text-red-700 p-3 rounded">
            Error: {error}
          </div>
        )}
        
        {response && (
          <div className="bg-green-100 text-green-700 p-3 rounded">
            Post created successfully! ID: {response.id}
          </div>
        )}
      </form>
    </div>
  );
}
Custom Fetch Hook (Reusable)
jsx
// hooks/useFetch.js
import { useState, useEffect } from 'react';

function useFetch(url, options = {}) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    let isMounted = true; // Prevent state update if component unmounts
    
    const fetchData = async () => {
      try {
        setLoading(true);
        setError(null);
        
        const response = await fetch(url, options);
        
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const result = await response.json();
        
        if (isMounted) {
          setData(result);
        }
      } catch (err) {
        if (isMounted) {
          setError(err.message);
        }
      } finally {
        if (isMounted) {
          setLoading(false);
        }
      }
    };
    
    fetchData();
    
    // Cleanup function
    return () => {
      isMounted = false;
    };
  }, [url, JSON.stringify(options)]); // Re-fetch if URL or options change
  
  return { data, loading, error };
}

// Using the custom hook
function UserList() {
  const { data: users, loading, error } = useFetch('https://jsonplaceholder.typicode.com/users');
  
  if (loading) return <div>Loading users...</div>;
  if (error) return <div>Error: {error}</div>;
  
  return (
    <div className="p-4">
      <h1 className="text-2xl font-bold mb-4">Users</h1>
      <div className="grid gap-2">
        {users?.map(user => (
          <div key={user.id} className="border p-3 rounded">
            <p className="font-bold">{user.name}</p>
            <p className="text-gray-600">{user.email}</p>
          </div>
        ))}
      </div>
    </div>
  );
}
Search with API
jsx
function SearchWithAPI() {
  const [searchTerm, setSearchTerm] = useState('');
  const [results, setResults] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  
  // Debounce search to avoid too many API calls
  useEffect(() => {
    if (searchTerm.length < 2) {
      setResults([]);
      return;
    }
    
    const timer = setTimeout(() => {
      performSearch();
    }, 500); // Wait 500ms after user stops typing
    
    return () => clearTimeout(timer);
  }, [searchTerm]);
  
  const performSearch = async () => {
    setLoading(true);
    setError(null);
    
    try {
      const response = await fetch(
        `https://jsonplaceholder.typicode.com/posts?q=${searchTerm}`
      );
      
      if (!response.ok) {
        throw new Error('Search failed');
      }
      
      const data = await response.json();
      setResults(data);
    } catch (err) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  };
  
  return (
    <div className="max-w-2xl mx-auto p-4">
      <h1 className="text-2xl font-bold mb-4">Search Posts</h1>
      
      <div className="mb-4">
        <input
          type="text"
          value={searchTerm}
          onChange={(e) => setSearchTerm(e.target.value)}
          className="w-full border p-2 rounded"
          placeholder="Search posts (min 2 characters)..."
        />
        <p className="text-sm text-gray-500 mt-1">
          {searchTerm.length < 2 && 'Type at least 2 characters to search'}
        </p>
      </div>
      
      {loading && (
        <div className="text-center py-8">Searching...</div>
      )}
      
      {error && (
        <div className="bg-red-100 text-red-700 p-3 rounded mb-4">
          Error: {error}
        </div>
      )}
      
      {results.length > 0 && (
        <div className="space-y-4">
          <p className="font-semibold">Found {results.length} results:</p>
          {results.map(result => (
            <div key={result.id} className="border rounded-lg p-4">
              <h3 className="font-bold text-lg mb-2">{result.title}</h3>
              <p className="text-gray-600">{result.body}</p>
            </div>
          ))}
        </div>
      )}
      
      {searchTerm.length >= 2 && !loading && results.length === 0 && !error && (
        <div className="text-center py-8 text-gray-500">
          No results found for "{searchTerm}"
        </div>
      )}
    </div>
  );
}
14. Local Storage - Saving Data in Browser
What is Local Storage?
Local Storage is a way to save data in the user's browser. Data stays even after closing the browser or restarting the computer.

Basic Local Storage Operations
jsx
function LocalStorageBasics() {
  const [name, setName] = useState(() => {
    // Get saved name from localStorage when component loads
    const saved = localStorage.getItem('name');
    return saved || '';
  });
  
  const [count, setCount] = useState(() => {
    const saved = localStorage.getItem('count');
    return saved ? parseInt(saved) : 0;
  });
  
  // Save name whenever it changes
  useEffect(() => {
    localStorage.setItem('name', name);
    console.log('Saved name to localStorage');
  }, [name]);
  
  // Save count whenever it changes
  useEffect(() => {
    localStorage.setItem('count', count.toString());
    console.log('Saved count to localStorage');
  }, [count]);
  
  const clearStorage = () => {
    localStorage.removeItem('name');
    localStorage.removeItem('count');
    setName('');
    setCount(0);
    console.log('Cleared localStorage');
  };
  
  return (
    <div className="max-w-md mx-auto p-4 space-y-4">
      <div>
        <label className="block mb-1">Name:</label>
        <input
          type="text"
          value={name}
          onChange={(e) => setName(e.target.value)}
          className="border p-2 rounded w-full"
          placeholder="Enter your name"
        />
        <p className="text-sm text-gray-500 mt-1">
          Your name is saved automatically
        </p>
      </div>
      
      <div>
        <p className="mb-2">Count: {count}</p>
        <button
          onClick={() => setCount(count + 1)}
          className="bg-blue-500 text-white px-4 py-2 rounded mr-2"
        >
          Increment
        </button>
        <button
          onClick={() => setCount(count - 1)}
          className="bg-red-500 text-white px-4 py-2 rounded"
        >
          Decrement
        </button>
      </div>
      
      <button
        onClick={clearStorage}
        className="bg-gray-500 text-white px-4 py-2 rounded"
      >
        Clear All Saved Data
      </button>
      
      <div className="bg-gray-100 p-4 rounded">
        <h3 className="font-bold mb-2">Current localStorage:</h3>
        <pre className="text-sm">
          name: {localStorage.getItem('name') || '(empty)'}
          {'\n'}
          count: {localStorage.getItem('count') || '(empty)'}
        </pre>
      </div>
    </div>
  );
}
Custom useLocalStorage Hook
jsx
// hooks/useLocalStorage.js
import { useState, useEffect } from 'react';

function useLocalStorage(key, initialValue) {
  // Get from localStorage on initial load
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error('Error reading from localStorage:', error);
      return initialValue;
    }
  });
  
  // Save to localStorage whenever storedValue changes
  useEffect(() => {
    try {
      localStorage.setItem(key, JSON.stringify(storedValue));
    } catch (error) {
      console.error('Error saving to localStorage:', error);
    }
  }, [key, storedValue]);
  
  return [storedValue, setStoredValue];
}

// Using the custom hook
function TodoAppWithStorage() {
  const [todos, setTodos] = useLocalStorage('todos', []);
  const [input, setInput] = useState('');
  
  const addTodo = () => {
    if (input.trim()) {
      setTodos([...todos, { id: Date.now(), text: input, completed: false }]);
      setInput('');
    }
  };
  
  const toggleTodo = (id) => {
    setTodos(todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    ));
  };
  
  const deleteTodo = (id) => {
    setTodos(todos.filter(todo => todo.id !== id));
  };
  
  const clearAllTodos = () => {
    setTodos([]);
  };
  
  return (
    <div className="max-w-md mx-auto p-4">
      <h1 className="text-2xl font-bold mb-4">Todo List (with LocalStorage)</h1>
      
      <div className="flex gap-2 mb-4">
        <input
          value={input}
          onChange={(e) => setInput(e.target.value)}
          onKeyPress={(e) => e.key === 'Enter' && addTodo()}
          className="border p-2 rounded flex-1"
          placeholder="Add a todo..."
        />
        <button
          onClick={addTodo}
          className="bg-blue-500 text-white px-4 py-2 rounded"
        >
          Add
        </button>
      </div>
      
      {todos.length === 0 ? (
        <div className="text-center py-8 text-gray-500">
          No todos yet. Add one above!
        </div>
      ) : (
        <ul className="space-y-2">
          {todos.map(todo => (
            <li key={todo.id} className="flex items-center gap-2 border p-2 rounded">
              <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => toggleTodo(todo.id)}
                className="w-4 h-4"
              />
              <span className={todo.completed ? 'line-through text-gray-500 flex-1' : 'flex-1'}>
                {todo.text}
              </span>
              <button
                onClick={() => deleteTodo(todo.id)}
                className="text-red-500 hover:text-red-700"
              >
                Delete
              </button>
            </li>
          ))}
        </ul>
      )}
      
      {todos.length > 0 && (
        <button
          onClick={clearAllTodos}
          className="mt-4 w-full bg-red-500 text-white py-2 rounded hover:bg-red-600"
        >
          Clear All Todos
        </button>
      )}
      
      <div className="mt-4 text-sm text-gray-500">
        <p>Your todos are saved automatically!</p>
        <p>Close the browser and reopen - your todos will still be here.</p>
      </div>
    </div>
  );
}
Complete Notes App with LocalStorage
jsx
function NotesApp() {
  const [notes, setNotes] = useLocalStorage('notes', []);
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');
  const [editingId, setEditingId] = useState(null);
  const [search, setSearch] = useState('');
  const [selectedCategory, setSelectedCategory] = useState('all');
  
  const categories = ['all', 'work', 'personal', 'ideas', 'todo'];
  
  const addOrUpdateNote = () => {
    if (!title.trim()) return;
    
    if (editingId) {
      // Update existing note
      setNotes(notes.map(note =>
        note.id === editingId
          ? { ...note, title, content, category: selectedCategory, updatedAt: new Date().toISOString() }
          : note
      ));
      setEditingId(null);
    } else {
      // Add new note
      setNotes([...notes, {
        id: Date.now(),
        title,
        content,
        category: selectedCategory,
        createdAt: new Date().toISOString(),
        updatedAt: new Date().toISOString()
      }]);
    }
    
    // Clear form
    setTitle('');
    setContent('');
    setSelectedCategory('all');
  };
  
  const editNote = (note) => {
    setTitle(note.title);
    setContent(note.content);
    setSelectedCategory(note.category);
    setEditingId(note.id);
  };
  
  const deleteNote = (id) => {
    if (confirm('Are you sure you want to delete this note?')) {
      setNotes(notes.filter(note => note.id !== id));
    }
  };
  
  const cancelEdit = () => {
    setEditingId(null);
    setTitle('');
    setContent('');
    setSelectedCategory('all');
  };
  
  // Filter notes based on search and category
  const filteredNotes = notes.filter(note => {
    const matchesSearch = note.title.toLowerCase().includes(search.toLowerCase()) ||
                          note.content.toLowerCase().includes(search.toLowerCase());
    const matchesCategory = selectedCategory === 'all' || note.category === selectedCategory;
    return matchesSearch && matchesCategory;
  });
  
  return (
    <div className="max-w-6xl mx-auto p-4">
      <h1 className="text-3xl font-bold mb-6">📝 Notes App</h1>
      
      <div className="grid md:grid-cols-3 gap-6">
        {/* Form Section */}
        <div className="md:col-span-1">
          <div className="bg-white rounded-lg shadow p-4">
            <h2 className="text-xl font-bold mb-4">
              {editingId ? 'Edit Note' : 'Create New Note'}
            </h2>
            
            <div className="space-y-4">
              <div>
                <label className="block mb-1">Title *</label>
                <input
                  type="text"
                  value={title}
                  onChange={(e) => setTitle(e.target.value)}
                  className="w-full border p-2 rounded"
                  placeholder="Note title..."
                />
              </div>
              
              <div>
                <label className="block mb-1">Category</label>
                <select
                  value={selectedCategory}
                  onChange={(e) => setSelectedCategory(e.target.value)}
                  className="w-full border p-2 rounded"
                >
                  {categories.filter(c => c !== 'all').map(cat => (
                    <option key={cat} value={cat}>{cat.charAt(0).toUpperCase() + cat.slice(1)}</option>
                  ))}
                </select>
              </div>
              
              <div>
                <label className="block mb-1">Content</label>
                <textarea
                  value={content}
                  onChange={(e) => setContent(e.target.value)}
                  rows="6"
                  className="w-full border p-2 rounded"
                  placeholder="Write your note here..."
                />
              </div>
              
              <div className="flex gap-2">
                <button
                  onClick={addOrUpdateNote}
                  className="flex-1 bg-blue-500 text-white py-2 rounded hover:bg-blue-600"
                >
                  {editingId ? 'Update Note' : 'Add Note'}
                </button>
                {editingId && (
                  <button
                    onClick={cancelEdit}
                    className="px-4 bg-gray-500 text-white rounded hover:bg-gray-600"
                  >
                    Cancel
                  </button>
                )}
              </div>
            </div>
          </div>
        </div>
        
        {/* Notes List Section */}
        <div className="md:col-span-2">
          {/* Search and Filter */}
          <div className="mb-4 flex gap-2">
            <input
              type="text"
              value={search}
              onChange={(e) => setSearch(e.target.value)}
              className="flex-1 border p-2 rounded"
              placeholder="Search notes..."
            />
            <select
              value={selectedCategory}
              onChange={(e) => setSelectedCategory(e.target.value)}
              className="border p-2 rounded"
            >
              {categories.map(cat => (
                <option key={cat} value={cat}>
                  {cat === 'all' ? 'All Categories' : cat.charAt(0).toUpperCase() + cat.slice(1)}
                </option>
              ))}
            </select>
          </div>
          
          {/* Notes Grid */}
          {filteredNotes.length === 0 ? (
            <div className="text-center py-12 text-gray-500">
              {search || selectedCategory !== 'all' 
                ? 'No notes match your filters' 
                : 'No notes yet. Create your first note!'}
            </div>
          ) : (
            <div className="grid gap-4">
              {filteredNotes.map(note => (
                <div key={note.id} className="border rounded-lg p-4 hover:shadow-lg transition">
                  <div className="flex justify-between items-start mb-2">
                    <div>
                      <h3 className="font-bold text-lg">{note.title}</h3>
                      <span className="inline-block bg-gray-100 text-gray-600 text-xs px-2 py-1 rounded mt-1">
                        {note.category}
                      </span>
                    </div>
                    <div className="flex gap-2">
                      <button
                        onClick={() => editNote(note)}
                        className="text-blue-500 hover:text-blue-700"
                      >
                        Edit
                      </button>
                      <button
                        onClick={() => deleteNote(note.id)}
                        className="text-red-500 hover:text-red-700"
                      >
                        Delete
                      </button>
                    </div>
                  </div>
                  <p className="text-gray-600 mt-2">{note.content}</p>
                  <div className="text-xs text-gray-400 mt-2">
                    Created: {new Date(note.createdAt).toLocaleDateString()}
                  </div>
                </div>
              ))}
            </div>
          )}
          
          {/* Stats */}
          <div className="mt-4 p-3 bg-gray-100 rounded text-sm text-gray-600">
            Total: {notes.length} notes | 
            Showing: {filteredNotes.length} notes
          </div>
        </div>
      </div>
    </div>
  );
}
15. React Router - Navigation Without Refresh
What is React Router?
React Router allows you to create multi-page apps without refreshing the browser. It handles navigation between different views in your app.

Installation
bash
npm install react-router-dom
Basic Setup
jsx
// main.jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import { BrowserRouter } from 'react-router-dom'
import App from './App'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <BrowserRouter>  {/* Wrap app with BrowserRouter */}
      <App />
    </BrowserRouter>
  </React.StrictMode>,
)
jsx
// App.jsx
import { Routes, Route, Link, NavLink, useNavigate } from 'react-router-dom';
import Home from './pages/Home';
import About from './pages/About';
import Contact from './pages/Contact';
import Users from './pages/Users';
import UserDetail from './pages/UserDetail';
import NotFound from './pages/NotFound';

function App() {
  const navigate = useNavigate();
  
  return (
    <div className="min-h-screen bg-gray-100">
      {/* Navigation Bar */}
      <nav className="bg-white shadow-md p-4">
        <div className="container mx-auto flex gap-4">
          {/* Link - basic navigation */}
          <Link to="/" className="text-blue-500 hover:text-blue-700">
            Home
          </Link>
          
          {/* NavLink - adds active class */}
          <NavLink 
            to="/about" 
            className={({ isActive }) => 
              isActive ? 'text-blue-700 font-bold' : 'text-blue-500 hover:text-blue-700'
            }
          >
            About
          </NavLink>
          
          <Link to="/contact" className="text-blue-500 hover:text-blue-700">
            Contact
          </Link>
          
          <Link to="/users" className="text-blue-500 hover:text-blue-700">
            Users
          </Link>
          
          {/* Programmatic navigation button */}
          <button
            onClick={() => navigate('/about')}
            className="bg-green-500 text-white px-3 py-1 rounded"
          >
            Go to About
          </button>
        </div>
      </nav>
      
      {/* Page Content */}
      <div className="container mx-auto p-4">
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
          <Route path="/users" element={<Users />} />
          <Route path="/users/:id" element={<UserDetail />} />
          <Route path="*" element={<NotFound />} /> {/* 404 page */}
        </Routes>
      </div>
    </div>
  );
}

export default App;
Creating Pages
jsx
// pages/Home.jsx
import { useNavigate } from 'react-router-dom';

function Home() {
  const navigate = useNavigate();
  
  return (
    <div className="text-center py-12">
      <h1 className="text-4xl font-bold mb-4">Welcome to My App</h1>
      <p className="text-gray-600 mb-6">This is the home page</p>
      <button
        onClick={() => navigate('/about')}
        className="bg-blue-500 text-white px-6 py-2 rounded hover:bg-blue-600"
      >
        Learn More
      </button>
    </div>
  );
}

export default Home;
jsx
// pages/About.jsx
function About() {
  return (
    <div className="py-12">
      <h1 className="text-3xl font-bold mb-4">About Us</h1>
      <p className="text-gray-600 mb-4">
        This is a sample React application using React Router for navigation.
        We're learning how to create multi-page apps without page refresh!
      </p>
      <div className="bg-blue-50 p-4 rounded">
        <h2 className="font-bold mb-2">Features:</h2>
        <ul className="list-disc list-inside space-y-1">
          <li>Client-side routing</li>
          <li>Dynamic routes with parameters</li>
          <li>404 error handling</li>
          <li>Programmatic navigation</li>
        </ul>
      </div>
    </div>
  );
}

export default About;
jsx
// pages/Users.jsx
import { useState, useEffect } from 'react';
import { Link } from 'react-router-dom';

function Users() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  
  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(res => res.json())
      .then(data => {
        setUsers(data);
        setLoading(false);
      });
  }, []);
  
  if (loading) {
    return <div className="text-center py-12">Loading users...</div>;
  }
  
  return (
    <div>
      <h1 className="text-3xl font-bold mb-6">Users</h1>
      <div className="grid gap-4 md:grid-cols-2">
        {users.map(user => (
          <Link
            key={user.id}
            to={`/users/${user.id}`}
            className="border rounded-lg p-4 hover:shadow-lg transition block"
          >
            <h2 className="font-bold text-lg">{user.name}</h2>
            <p className="text-gray-600">{user.email}</p>
            <p className="text-sm text-gray-500 mt-2">Click to view details →</p>
          </Link>
        ))}
      </div>
    </div>
  );
}

export default Users;
jsx
// pages/UserDetail.jsx
import { useState, useEffect } from 'react';
import { useParams, useNavigate, Link } from 'react-router-dom';

function UserDetail() {
  const { id } = useParams(); // Get the :id from URL
  const navigate = useNavigate();
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/users/${id}`)
      .then(res => {
        if (!res.ok) {
          throw new Error('User not found');
        }
        return res.json();
      })
      .then(data => {
        setUser(data);
        setLoading(false);
      })
      .catch(err => {
        setError(err.message);
        setLoading(false);
      });
  }, [id]);
  
  if (loading) {
    return <div className="text-center py-12">Loading user details...</div>;
  }
  
  if (error) {
    return (
      <div className="text-center py-12">
        <div className="bg-red-100 text-red-700 p-4 rounded mb-4">
          Error: {error}
        </div>
        <Link to="/users" className="bg-blue-500 text-white px-4 py-2 rounded">
          Back to Users
        </Link>
      </div>
    );
  }
  
  return (
    <div>
      <div className="mb-4">
        <Link to="/users" className="text-blue-500 hover:text-blue-700">
          ← Back to Users
        </Link>
      </div>
      
      <div className="border rounded-lg p-6">
        <h1 className="text-3xl font-bold mb-4">{user.name}</h1>
        
        <div className="grid md:grid-cols-2 gap-6">
          <div>
            <h2 className="text-xl font-semibold mb-2">Contact Info</h2>
            <p className="mb-1"><strong>Email:</strong> {user.email}</p>
            <p className="mb-1"><strong>Phone:</strong> {user.phone}</p>
            <p className="mb-1"><strong>Website:</strong> {user.website}</p>
          </div>
          
          <div>
            <h2 className="text-xl font-semibold mb-2">Address</h2>
            <p className="mb-1">
              {user.address.street}, {user.address.suite}
            </p>
            <p className="mb-1">
              {user.address.city}, {user.address.zipcode}
            </p>
          </div>
          
          <div>
            <h2 className="text-xl font-semibold mb-2">Company</h2>
            <p className="mb-1"><strong>Name:</strong> {user.company.name}</p>
            <p className="mb-1"><strong>Catchphrase:</strong> {user.company.catchPhrase}</p>
          </div>
        </div>
      </div>
      
      {/* Navigation buttons */}
      <div className="flex gap-4 mt-6">
        <button
          onClick={() => navigate(-1)}
          className="bg-gray-500 text-white px-4 py-2 rounded hover:bg-gray-600"
        >
          Go Back
        </button>
        <button
          onClick={() => navigate('/users')}
          className="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
        >
          All Users
        </button>
      </div>
    </div>
  );
}

export default UserDetail;
jsx
// pages/Contact.jsx
import { useState } from 'react';
import { useNavigate } from 'react-router-dom';

function Contact() {
  const navigate = useNavigate();
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  });
  const [submitted, setSubmitted] = useState(false);
  
  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData({ ...formData, [name]: value });
  };
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Form submitted:', formData);
    setSubmitted(true);
    
    // Redirect to home after 2 seconds
    setTimeout(() => {
      navigate('/');
    }, 2000);
  };
  
  if (submitted) {
    return (
      <div className="text-center py-12">
        <div className="bg-green-100 text-green-700 p-4 rounded mb-4">
          Thank you for contacting us! Redirecting to home...
        </div>
      </div>
    );
  }
  
  return (
    <div className="max-w-lg mx-auto py-8">
      <h1 className="text-3xl font-bold mb-6">Contact Us</h1>
      
      <form onSubmit={handleSubmit} className="space-y-4">
        <div>
          <label className="block mb-1">Name:</label>
          <input
            type="text"
            name="name"
            value={formData.name}
            onChange={handleChange}
            className="w-full border p-2 rounded"
            required
          />
        </div>
        
        <div>
          <label className="block mb-1">Email:</label>
          <input
            type="email"
            name="email"
            value={formData.email}
            onChange={handleChange}
            className="w-full border p-2 rounded"
            required
          />
        </div>
        
        <div>
          <label className="block mb-1">Message:</label>
          <textarea
            name="message"
            value={formData.message}
            onChange={handleChange}
            rows="5"
            className="w-full border p-2 rounded"
            required
          />
        </div>
        
        <button
          type="submit"
          className="w-full bg-blue-500 text-white py-2 rounded hover:bg-blue-600"
        >
          Send Message
        </button>
      </form>
    </div>
  );
}

export default Contact;
jsx
// pages/NotFound.jsx
import { Link } from 'react-router-dom';

function NotFound() {
  return (
    <div className="text-center py-12">
      <h1 className="text-6xl font-bold text-gray-300 mb-4">404</h1>
      <h2 className="text-2xl font-bold mb-4">Page Not Found</h2>
      <p className="text-gray-600 mb-6">
        The page you're looking for doesn't exist or has been moved.
      </p>
      <Link
        to="/"
        className="bg-blue-500 text-white px-6 py-2 rounded hover:bg-blue-600"
      >
        Go Home
      </Link>
    </div>
  );
}

export default NotFound;
Nested Routes
jsx
// Dashboard Layout Component
function DashboardLayout() {
  return (
    <div className="flex">
      <aside className="w-64 bg-gray-800 text-white min-h-screen p-4">
        <h2 className="text-xl font-bold mb-4">Dashboard</h2>
        <nav className="space-y-2">
          <NavLink to="/dashboard" end className="block p-2 hover:bg-gray-700 rounded">
            Overview
          </NavLink>
          <NavLink to="/dashboard/profile" className="block p-2 hover:bg-gray-700 rounded">
            Profile
          </NavLink>
          <NavLink to="/dashboard/settings" className="block p-2 hover:bg-gray-700 rounded">
            Settings
          </NavLink>
        </nav>
      </aside>
      
      <div className="flex-1 p-6">
        <Outlet /> {/* This renders the nested routes */}
      </div>
    </div>
  );
}

// Add to your Routes
<Route path="/dashboard" element={<DashboardLayout />}>
  <Route index element={<DashboardOverview />} />
  <Route path="profile" element={<DashboardProfile />} />
  <Route path="settings" element={<DashboardSettings />} />
</Route>
Protected Routes
jsx
// components/ProtectedRoute.jsx
import { Navigate } from 'react-router-dom';

function ProtectedRoute({ children, isAuthenticated }) {
  if (!isAuthenticated) {
    return <Navigate to="/login" replace />;
  }
  
  return children;
}

// Usage in App.jsx
function App() {
  const [isAuthenticated, setIsAuthenticated] = useState(false);
  
  return (
    <Routes>
      <Route path="/login" element={<Login onLogin={() => setIsAuthenticated(true)} />} />
      <Route path="/dashboard" element={
        <ProtectedRoute isAuthenticated={isAuthenticated}>
          <Dashboard />
        </ProtectedRoute>
      } />
    </Routes>
  );
}
16. React Icons - Beautiful Icons Made Easy
Installation
bash
npm install react-icons
Icon Libraries Available
React Icons includes many popular icon libraries:

Fa - Font Awesome

Ai - Ant Design Icons

Bs - Bootstrap Icons

Bi - BoxIcons

Fi - Feather Icons

Gi - Game Icons

Hi - Heroicons

Im - IcoMoon

Io - Ionicons

Md - Material Design Icons

Ri - Remix Icon

Si - Simple Icons

Vsc - VS Code Icons

Basic Usage
jsx
import { FaHeart, FaStar, FaUser, FaHome, FaSearch } from 'react-icons/fa';
import { MdDelete, MdEdit, MdSave, MdEmail } from 'react-icons/md';
import { AiOutlineLoading, AiOutlineWarning } from 'react-icons/ai';

function BasicIcons() {
  return (
    <div className="p-4 space-y-4">
      <h1 className="text-2xl font-bold">Basic Icons</h1>
      
      {/* Simple icons */}
      <div className="flex gap-4 text-3xl">
        <FaHeart className="text-red-500" />
        <FaStar className="text-yellow-500" />
        <FaUser className="text-blue-500" />
        <FaHome className="text-green-500" />
        <FaSearch className="text-gray-500" />
      </div>
      
      {/* Icons with different sizes */}
      <div className="flex gap-4 items-center">
        <MdDelete className="text-red-500 text-sm" />
        <MdEdit className="text-blue-500 text-2xl" />
        <MdSave className="text-green-500 text-4xl" />
        <MdEmail className="text-purple-500 text-6xl" />
      </div>
      
      {/* Icons with styling */}
      <div className="flex gap-4">
        <FaHeart className="text-red-500 animate-pulse" />
        <AiOutlineLoading className="text-blue-500 animate-spin" />
        <AiOutlineWarning className="text-yellow-500 animate-bounce" />
      </div>
    </div>
  );
}
Icon Buttons
jsx
function IconButtons() {
  const [liked, setLiked] = useState(false);
  const [saved, setSaved] = useState(false);
  
  return (
    <div className="p-4 space-y-4">
      <h1 className="text-2xl font-bold">Icon Buttons</h1>
      
      {/* Basic icon buttons */}
      <div className="flex gap-4">
        <button className="bg-blue-500 text-white p-2 rounded hover:bg-blue-600">
          <FaHeart />
        </button>
        
        <button className="bg-red-500 text-white p-2 rounded hover:bg-red-600">
          <MdDelete />
        </button>
        
        <button className="bg-green-500 text-white p-2 rounded hover:bg-green-600">
          <MdSave />
        </button>
      </div>
      
      {/* Buttons with text */}
      <div className="flex gap-4">
        <button className="bg-blue-500 text-white px-4 py-2 rounded flex items-center gap-2 hover:bg-blue-600">
          <FaHeart />
          Like
        </button>
        
        <button className="bg-red-500 text-white px-4 py-2 rounded flex items-center gap-2 hover:bg-red-600">
          <MdDelete />
          Delete
        </button>
        
        <button className="bg-green-500 text-white px-4 py-2 rounded flex items-center gap-2 hover:bg-green-600">
          <MdSave />
          Save
        </button>
      </div>
      
      {/* Interactive icon buttons */}
      <div className="flex gap-4">
        <button
          onClick={() => setLiked(!liked)}
          className={`p-2 rounded flex items-center gap-2 ${
            liked ? 'bg-red-500 text-white' : 'bg-gray-200 text-gray-700'
          }`}
        >
          {liked ? <FaHeart /> : <FaHeart />}
          {liked ? 'Liked' : 'Like'}
        </button>
        
        <button
          onClick={() => setSaved(!saved)}
          className={`p-2 rounded flex items-center gap-2 ${
            saved ? 'bg-green-500 text-white' : 'bg-gray-200 text-gray-700'
          }`}
        >
          {saved ? <MdSave /> : <MdSave />}
          {saved ? 'Saved' : 'Save'}
        </button>
      </div>
    </div>
  );
}
Icon Components
jsx
// components/Icon.jsx
function Icon({ icon: IconComponent, size = 'md', color = 'currentColor', className = '' }) {
  const sizes = {
    sm: 'text-sm',
    md: 'text-base',
    lg: 'text-lg',
    xl: 'text-xl',
    '2xl': 'text-2xl',
    '3xl': 'text-3xl'
  };
  
  return (
    <IconComponent 
      className={`${sizes[size]} ${className}`}
      style={{ color }}
    />
  );
}

// components/IconButton.jsx
function IconButton({ icon, onClick, label, variant = 'primary', disabled = false }) {
  const variants = {
    primary: 'bg-blue-500 hover:bg-blue-600 text-white',
    danger: 'bg-red-500 hover:bg-red-600 text-white',
    success: 'bg-green-500 hover:bg-green-600 text-white',
    outline: 'border border-gray-300 hover:bg-gray-100 text-gray-700'
  };
  
  return (
    <button
      onClick={onClick}
      disabled={disabled}
      className={`px-4 py-2 rounded flex items-center gap-2 transition ${variants[variant]} ${
        disabled ? 'opacity-50 cursor-not-allowed' : ''
      }`}
    >
      {icon}
      {label && <span>{label}</span>}
    </button>
  );
}

// Usage
function App() {
  return (
    <div className="p-4 space-y-4">
      <Icon icon={FaHeart} size="3xl" color="red" />
      <Icon icon={FaStar} size="2xl" color="gold" />
      
      <IconButton 
        icon={<FaHeart />}
        label="Like"
        variant="primary"
        onClick={() => alert('Liked!')}
      />
      
      <IconButton 
        icon={<MdDelete />}
        label="Delete"
        variant="danger"
        onClick={() => alert('Deleted!')}
      />
    </div>
  );
}
Complete Icon Library Example
jsx
function IconLibraryDemo() {
  const [search, setSearch] = useState('');
  const [copied, setCopied] = useState(null);
  
  // Common icons with their names and components
  const icons = [
    { name: 'Home', component: FaHome, category: 'navigation' },
    { name: 'User', component: FaUser, category: 'people' },
    { name: 'Heart', component: FaHeart, category: 'actions' },
    { name: 'Star', component: FaStar, category: 'actions' },
    { name: 'Search', component: FaSearch, category: 'actions' },
    { name: 'Settings', component: FaCog, category: 'actions' },
    { name: 'Delete', component: MdDelete, category: 'actions' },
    { name: 'Edit', component: MdEdit, category: 'actions' },
    { name: 'Save', component: MdSave, category: 'actions' },
    { name: 'Email', component: MdEmail, category: 'communication' },
    { name: 'Phone', component: MdPhone, category: 'communication' },
    { name: 'Location', component: MdLocationOn, category: 'navigation' },
    { name: 'Loading', component: AiOutlineLoading, category: 'status' },
    { name: 'Warning', component: AiOutlineWarning, category: 'status' }
  ];
  
  const filteredIcons = icons.filter(icon =>
    icon.name.toLowerCase().includes(search.toLowerCase())
  );
  
  const copyIconName = (iconName) => {
    navigator.clipboard.writeText(iconName);
    setCopied(iconName);
    setTimeout(() => setCopied(null), 2000);
  };
  
  return (
    <div className="max-w-4xl mx-auto p-4">
      <h1 className="text-3xl font-bold mb-6">React Icons Library</h1>
      
      {/* Search Bar */}
      <div className="mb-6">
        <div className="relative">
          <FaSearch className="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400" />
          <input
            type="text"
            value={search}
            onChange={(e) => setSearch(e.target.value)}
            className="w-full border p-2 pl-10 rounded"
            placeholder="Search icons..."
          />
        </div>
      </div>
      
      {/* Icons Grid */}
      <div className="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-4">
        {filteredIcons.map(icon => {
          const IconComponent = icon.component;
          return (
            <div
              key={icon.name}
              onClick={() => copyIconName(icon.name)}
              className="border rounded-lg p-4 text-center hover:shadow-lg cursor-pointer transition"
            >
              <IconComponent className="text-4xl mx-auto mb-2 text-blue-500" />
              <p className="text-sm font-medium">{icon.name}</p>
              <p className="text-xs text-gray-500">{icon.category}</p>
              {copied === icon.name && (
                <span className="text-xs text-green-500">Copied!</span>
              )}
            </div>
          );
        })}
      </div>
      
      {/* Usage Examples */}
      <div className="mt-8 p-4 bg-gray-100 rounded">
        <h2 className="text-xl font-bold mb-4">Usage Examples</h2>
        
        <div className="space-y-2">
          <p><strong>Import:</strong> <code className="bg-gray-800 text-white px-2 py-1 rounded">import {{ '{ FaHeart }' }} from 'react-icons/fa'</code></p>
          <p><strong>Usage:</strong> <code className="bg-gray-800 text-white px-2 py-1 rounded">&lt;FaHeart /&gt;</code></p>
          <p><strong>With styling:</strong> <code className="bg-gray-800 text-white px-2 py-1 rounded">&lt;FaHeart className="text-red-500 text-2xl" /&gt;</code></p>
        </div>
      </div>
    </div>
  );
}
17. Building Real Projects
Project 1: Counter App with Explanation
jsx
// Complete Counter App with detailed comments
import { useState } from 'react';
import { FaPlus, FaMinus, FaRedo } from 'react-icons/fa';

function CounterApp() {
  // State: 'count' holds the current number, 'setCount' updates it
  // useState(0) initializes count with 0
  const [count, setCount] = useState(0);
  
  // Helper functions for better readability
  const increment = () => {
    // Using functional update to ensure we get the latest value
    setCount(prevCount => prevCount + 1);
  };
  
  const decrement = () => {
    setCount(prevCount => prevCount - 1);
  };
  
  const reset = () => {
    setCount(0);
  };
  
  // Determine message based on count value
  const getMessage = () => {
    if (count > 10) return "Wow, you're on fire! 🔥";
    if (count > 5) return "Getting there! 🚀";
    if (count > 0) return "Keep going! 💪";
    if (count === 0) return "Start counting! 🎯";
    return "Going down? 📉";
  };
  
  // Determine color based on count
  const getCountColor = () => {
    if (count > 10) return "text-red-600";
    if (count > 5) return "text-orange-500";
    if (count > 0) return "text-green-500";
    if (count === 0) return "text-gray-500";
    return "text-blue-500";
  };
  
  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-50 to-purple-50 flex items-center justify-center p-4">
      <div className="bg-white rounded-2xl shadow-xl p-8 max-w-md w-full">
        {/* Title */}
        <h1 className="text-3xl font-bold text-center text-gray-800 mb-2">
          Counter App
        </h1>
        <p className="text-center text-gray-500 mb-8">
          Click the buttons to change the count
        </p>
        
        {/* Counter Display */}
        <div className="text-center mb-8">
          <div className={`text-7xl font-bold mb-2 ${getCountColor()}`}>
            {count}
          </div>
          <p className="text-gray-600">{getMessage()}</p>
        </div>
        
        {/* Control Buttons */}
        <div className="flex gap-4 justify-center mb-8">
          {/* Decrement Button */}
          <button
            onClick={decrement}
            disabled={count <= -10}
            className={`
              bg-red-500 text-white px-6 py-3 rounded-xl flex items-center gap-2 
              transition-all duration-200 hover:bg-red-600 hover:scale-105
              disabled:opacity-50 disabled:cursor-not-allowed disabled:hover:scale-100
            `}
            title="Decrease count by 1"
          >
            <FaMinus /> Decrement
          </button>
          
          {/* Reset Button */}
          <button
            onClick={reset}
            className="bg-gray-500 text-white px-6 py-3 rounded-xl flex items-center gap-2 
                       transition-all duration-200 hover:bg-gray-600 hover:scale-105"
            title="Reset count to zero"
          >
            <FaRedo /> Reset
          </button>
          
          {/* Increment Button */}
          <button
            onClick={increment}
            disabled={count >= 10}
            className={`
              bg-green-500 text-white px-6 py-3 rounded-xl flex items-center gap-2 
              transition-all duration-200 hover:bg-green-600 hover:scale-105
              disabled:opacity-50 disabled:cursor-not-allowed disabled:hover:scale-100
            `}
            title="Increase count by 1"
          >
            <FaPlus /> Increment
          </button>
        </div>
        
        {/* Stats Section */}
        <div className="border-t pt-6">
          <h3 className="font-semibold text-gray-700 mb-3">Statistics:</h3>
          <div className="grid grid-cols-3 gap-4 text-center">
            <div className="bg-gray-50 p-2 rounded">
              <div className="text-sm text-gray-500">Current</div>
              <div className="font-bold text-lg">{count}</div>
            </div>
            <div className="bg-gray-50 p-2 rounded">
              <div className="text-sm text-gray-500">Status</div>
              <div className="font-bold text-lg">
                {count > 0 ? 'Positive' : count < 0 ? 'Negative' : 'Zero'}
              </div>
            </div>
            <div className="bg-gray-50 p-2 rounded">
              <div className="text-sm text-gray-500">Absolute</div>
              <div className="font-bold text-lg">{Math.abs(count)}</div>
            </div>
          </div>
        </div>
        
        {/* Tips */}
        <div className="mt-6 p-3 bg-blue-50 rounded-lg">
          <p className="text-sm text-blue-800">
            💡 Tip: Try clicking the buttons quickly or use the keyboard!
          </p>
        </div>
      </div>
    </div>
  );
}

export default CounterApp;
Project 2: Todo App with Local Storage
jsx
// Complete Todo App with local storage persistence
import { useState, useEffect } from 'react';
import { FaPlus, FaTrash, FaCheck, FaUndo } from 'react-icons/fa';

function TodoApp() {
  // State for todos - load from localStorage on initial render
  const [todos, setTodos] = useState(() => {
    const saved = localStorage.getItem('todos');
    return saved ? JSON.parse(saved) : [];
  });
  
  // State for new todo input
  const [input, setInput] = useState('');
  
  // State for filtering todos
  const [filter, setFilter] = useState('all'); // 'all', 'active', 'completed'
  
  // State for edit mode
  const [editingId, setEditingId] = useState(null);
  const [editText, setEditText] = useState('');
  
  // Save todos to localStorage whenever they change
  useEffect(() => {
    localStorage.setItem('todos', JSON.stringify(todos));
  }, [todos]);
  
  // Add a new todo
  const addTodo = () => {
    if (input.trim()) {
      const newTodo = {
        id: Date.now(), // Unique ID based on timestamp
        text: input.trim(),
        completed: false,
        createdAt: new Date().toISOString()
      };
      setTodos([...todos, newTodo]);
      setInput(''); // Clear input field
    }
  };
  
  // Toggle todo completion status
  const toggleTodo = (id) => {
    setTodos(todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    ));
  };
  
  // Delete a todo
  const deleteTodo = (id) => {
    if (confirm('Are you sure you want to delete this todo?')) {
      setTodos(todos.filter(todo => todo.id !== id));
    }
  };
  
  // Start editing a todo
  const startEdit = (todo) => {
    setEditingId(todo.id);
    setEditText(todo.text);
  };
  
  // Save edited todo
  const saveEdit = (id) => {
    if (editText.trim()) {
      setTodos(todos.map(todo =>
        todo.id === id ? { ...todo, text: editText.trim() } : todo
      ));
      setEditingId(null);
      setEditText('');
    }
  };
  
  // Cancel editing
  const cancelEdit = () => {
    setEditingId(null);
    setEditText('');
  };
  
  // Clear all completed todos
  const clearCompleted = () => {
    setTodos(todos.filter(todo => !todo.completed));
  };
  
  // Filter todos based on selected filter
  const filteredTodos = todos.filter(todo => {
    if (filter === 'active') return !todo.completed;
    if (filter === 'completed') return todo.completed;
    return true;
  });
  
  // Calculate statistics
  const stats = {
    total: todos.length,
    completed: todos.filter(t => t.completed).length,
    active: todos.filter(t => !t.completed).length
  };
  
  return (
    <div className="min-h-screen bg-gradient-to-br from-purple-50 to-pink-50 py-8 px-4">
      <div className="max-w-2xl mx-auto">
        {/* Header */}
        <div className="text-center mb-8">
          <h1 className="text-4xl font-bold text-gray-800 mb-2">📝 Todo List</h1>
          <p className="text-gray-600">Organize your tasks and get things done!</p>
        </div>
        
        {/* Input Section */}
        <div className="bg-white rounded-lg shadow-md p-6 mb-6">
          <div className="flex gap-2">
            <input
              type="text"
              value={input}
              onChange={(e) => setInput(e.target.value)}
              onKeyPress={(e) => e.key === 'Enter' && addTodo()}
              className="flex-1 border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-purple-500"
              placeholder="What needs to be done?"
            />
            <button
              onClick={addTodo}
              className="bg-purple-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-purple-600 transition"
            >
              <FaPlus /> Add
            </button>
          </div>
        </div>
        
        {/* Filter Tabs */}
        <div className="flex gap-2 mb-6">
          <button
            onClick={() => setFilter('all')}
            className={`px-4 py-2 rounded-lg transition ${
              filter === 'all' 
                ? 'bg-purple-500 text-white' 
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`}
          >
            All ({stats.total})
          </button>
          <button
            onClick={() => setFilter('active')}
            className={`px-4 py-2 rounded-lg transition ${
              filter === 'active' 
                ? 'bg-purple-500 text-white' 
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`}
          >
            Active ({stats.active})
          </button>
          <button
            onClick={() => setFilter('completed')}
            className={`px-4 py-2 rounded-lg transition ${
              filter === 'completed' 
                ? 'bg-purple-500 text-white' 
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`}
          >
            Completed ({stats.completed})
          </button>
          {stats.completed > 0 && (
            <button
              onClick={clearCompleted}
              className="ml-auto px-4 py-2 bg-red-500 text-white rounded-lg hover:bg-red-600 transition"
            >
              Clear Completed
            </button>
          )}
        </div>
        
        {/* Todo List */}
        <div className="bg-white rounded-lg shadow-md overflow-hidden">
          {filteredTodos.length === 0 ? (
            <div className="text-center py-12 text-gray-500">
              {filter === 'all' && stats.total === 0 && 'No todos yet. Add one above!'}
              {filter === 'active' && stats.active === 0 && 'No active todos! Great job!'}
              {filter === 'completed' && stats.completed === 0 && 'No completed todos yet.'}
            </div>
          ) : (
            <ul className="divide-y divide-gray-200">
              {filteredTodos.map(todo => (
                <li key={todo.id} className="p-4 hover:bg-gray-50 transition group">
                  <div className="flex items-center gap-3">
                    {/* Checkbox */}
                    <input
                      type="checkbox"
                      checked={todo.completed}
                      onChange={() => toggleTodo(todo.id)}
                      className="w-5 h-5 rounded border-gray-300 text-purple-500 focus:ring-purple-500"
                    />
                    
                    {/* Todo Content */}
                    {editingId === todo.id ? (
                      <div className="flex-1 flex gap-2">
                        <input
                          type="text"
                          value={editText}
                          onChange={(e) => setEditText(e.target.value)}
                          onKeyPress={(e) => e.key === 'Enter' && saveEdit(todo.id)}
                          className="flex-1 border rounded px-2 py-1 focus:outline-none focus:ring-2 focus:ring-purple-500"
                          autoFocus
                        />
                        <button
                          onClick={() => saveEdit(todo.id)}
                          className="text-green-500 hover:text-green-700"
                        >
                          Save
                        </button>
                        <button
                          onClick={cancelEdit}
                          className="text-gray-500 hover:text-gray-700"
                        >
                          Cancel
                        </button>
                      </div>
                    ) : (
                      <div className="flex-1">
                        <p className={`${todo.completed ? 'line-through text-gray-400' : 'text-gray-800'}`}>
                          {todo.text}
                        </p>
                        <p className="text-xs text-gray-400 mt-1">
                          Created: {new Date(todo.createdAt).toLocaleDateString()}
                        </p>
                      </div>
                    )}
                    
                    {/* Action Buttons */}
                    {!editingId && (
                      <div className="flex gap-2 opacity-0 group-hover:opacity-100 transition">
                        {!todo.completed && (
                          <button
                            onClick={() => startEdit(todo)}
                            className="text-blue-500 hover:text-blue-700"
                            title="Edit"
                          >
                            ✏️
                          </button>
                        )}
                        <button
                          onClick={() => deleteTodo(todo.id)}
                          className="text-red-500 hover:text-red-700"
                          title="Delete"
                        >
                          <FaTrash />
                        </button>
                      </div>
                    )}
                  </div>
                </li>
              ))}
            </ul>
          )}
        </div>
        
        {/* Stats Footer */}
        <div className="mt-6 text-center text-sm text-gray-500">
          <p>✅ {stats.completed} completed • 📝 {stats.active} remaining • 📊 {stats.total} total</p>
          <p className="mt-2">💾 Your todos are automatically saved in your browser!</p>
        </div>
      </div>
    </div>
  );
}

export default TodoApp;
Project 3: Weather App with API
jsx
// Complete Weather App with API integration
import { useState } from 'react';
import { FaSearch, FaTemperatureHigh, FaTint, FaWind, FaSun, FaCloudRain, FaSnowflake } from 'react-icons/fa';

function WeatherApp() {
  const [city, setCity] = useState('');
  const [weather, setWeather] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  
  // API key - In real app, store this in environment variables
  // Sign up at https://openweathermap.org to get your free API key
  const API_KEY = 'YOUR_API_KEY_HERE'; // Replace with your actual API key
  const API_URL = 'https://api.openweathermap.org/data/2.5/weather';
  
  const searchWeather = async () => {
    if (!city.trim()) {
      setError('Please enter a city name');
      return;
    }
    
    setLoading(true);
    setError(null);
    
    try {
      const response = await fetch(
        `${API_URL}?q=${city}&appid=${API_KEY}&units=metric`
      );
      
      if (!response.ok) {
        if (response.status === 404) {
          throw new Error('City not found. Please check the city name.');
        }
        throw new Error('Failed to fetch weather data');
      }
      
      const data = await response.json();
      setWeather(data);
    } catch (err) {
      setError(err.message);
      setWeather(null);
    } finally {
      setLoading(false);
    }
  };
  
  // Handle Enter key press
  const handleKeyPress = (e) => {
    if (e.key === 'Enter') {
      searchWeather();
    }
  };
  
  // Get weather icon based on condition
  const getWeatherIcon = (condition) => {
    const condition_lower = condition?.toLowerCase() || '';
    if (condition_lower.includes('rain')) return <FaCloudRain className="text-blue-500" />;
    if (condition_lower.includes('snow')) return <FaSnowflake className="text-blue-300" />;
    if (condition_lower.includes('clear')) return <FaSun className="text-yellow-500" />;
    return <FaSun className="text-yellow-500" />;
  };
  
  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-400 to-purple-500 py-8 px-4">
      <div className="max-w-md mx-auto">
        {/* Header */}
        <div className="text-center text-white mb-8">
          <h1 className="text-4xl font-bold mb-2">🌤️ Weather App</h1>
          <p className="text-blue-100">Get current weather for any city</p>
        </div>
        
        {/* Search Section */}
        <div className="bg-white rounded-lg shadow-lg p-6 mb-6">
          <div className="flex gap-2">
            <input
              type="text"
              value={city}
              onChange={(e) => setCity(e.target.value)}
              onKeyPress={handleKeyPress}
              className="flex-1 border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
              placeholder="Enter city name..."
            />
            <button
              onClick={searchWeather}
              disabled={loading}
              className="bg-blue-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-blue-600 transition disabled:opacity-50"
            >
              {loading ? '...' : <FaSearch />}
              Search
            </button>
          </div>
          
          {error && (
            <div className="mt-4 p-3 bg-red-100 text-red-700 rounded-lg">
              ⚠️ {error}
            </div>
          )}
        </div>
        
        {/* Weather Display */}
        {weather && (
          <div className="bg-white rounded-lg shadow-lg overflow-hidden">
            {/* City Header */}
            <div className="bg-blue-500 text-white p-6 text-center">
              <h2 className="text-2xl font-bold">{weather.name}, {weather.sys.country}</h2>
              <div className="text-6xl font-bold my-4">
                {Math.round(weather.main.temp)}°C
              </div>
              <div className="flex items-center justify-center gap-2 text-lg">
                {getWeatherIcon(weather.weather[0].description)}
                <span className="capitalize">{weather.weather[0].description}</span>
              </div>
            </div>
            
            {/* Weather Details */}
            <div className="p-6">
              <h3 className="font-semibold text-gray-700 mb-4">Weather Details</h3>
              <div className="grid grid-cols-2 gap-4">
                <div className="flex items-center gap-3 p-3 bg-gray-50 rounded">
                  <FaTemperatureHigh className="text-red-500 text-xl" />
                  <div>
                    <div className="text-sm text-gray-500">Feels Like</div>
                    <div className="font-semibold">{Math.round(weather.main.feels_like)}°C</div>
                  </div>
                </div>
                
                <div className="flex items-center gap-3 p-3 bg-gray-50 rounded">
                  <FaTint className="text-blue-500 text-xl" />
                  <div>
                    <div className="text-sm text-gray-500">Humidity</div>
                    <div className="font-semibold">{weather.main.humidity}%</div>
                  </div>
                </div>
                
                <div className="flex items-center gap-3 p-3 bg-gray-50 rounded">
                  <FaWind className="text-gray-500 text-xl" />
                  <div>
                    <div className="text-sm text-gray-500">Wind Speed</div>
                    <div className="font-semibold">{weather.wind.speed} m/s</div>
                  </div>
                </div>
                
                <div className="flex items-center gap-3 p-3 bg-gray-50 rounded">
                  <FaTemperatureHigh className="text-blue-500 text-xl" />
                  <div>
                    <div className="text-sm text-gray-500">Pressure</div>
                    <div className="font-semibold">{weather.main.pressure} hPa</div>
                  </div>
                </div>
              </div>
              
              {/* Additional Info */}
              <div className="mt-4 p-3 bg-blue-50 rounded-lg">
                <div className="grid grid-cols-2 gap-2 text-sm">
                  <div>
                    <span className="text-gray-500">Min Temperature:</span>
                    <span className="ml-2 font-semibold">{Math.round(weather.main.temp_min)}°C</span>
                  </div>
                  <div>
                    <span className="text-gray-500">Max Temperature:</span>
                    <span className="ml-2 font-semibold">{Math.round(weather.main.temp_max)}°C</span>
                  </div>
                  <div>
                    <span className="text-gray-500">Visibility:</span>
                    <span className="ml-2 font-semibold">{(weather.visibility / 1000).toFixed(1)} km</span>
                  </div>
                  <div>
                    <span className="text-gray-500">Clouds:</span>
                    <span className="ml-2 font-semibold">{weather.clouds.all}%</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        )}
        
        {/* Welcome Message */}
        {!weather && !loading && !error && (
          <div className="bg-white rounded-lg shadow-lg p-8 text-center text-gray-500">
            <FaSun className="text-6xl mx-auto mb-4 text-yellow-500" />
            <p>Enter a city name above to see the weather!</p>
            <p className="text-sm mt-2">Try: London, Tokyo, New York, Paris</p>
          </div>
        )}
      </div>
    </div>
  );
}

export default WeatherApp;
Project 4: Movie Search App
jsx
// Complete Movie Search App with OMDB API
import { useState } from 'react';
import { FaSearch, FaStar, FaFilm, FaCalendar, FaImdb } from 'react-icons/fa';

function MovieSearchApp() {
  const [searchTerm, setSearchTerm] = useState('');
  const [movies, setMovies] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [selectedMovie, setSelectedMovie] = useState(null);
  
  // OMDB API - Get your free API key at http://www.omdbapi.com/apikey.aspx
  const API_KEY = 'YOUR_API_KEY_HERE'; // Replace with your actual API key
  const API_URL = 'http://www.omdbapi.com/';
  
  const searchMovies = async () => {
    if (!searchTerm.trim()) {
      setError('Please enter a movie name');
      return;
    }
    
    setLoading(true);
    setError(null);
    setSelectedMovie(null);
    
    try {
      const response = await fetch(
        `${API_URL}?s=${searchTerm}&apikey=${API_KEY}`
      );
      
      if (!response.ok) {
        throw new Error('Failed to fetch movies');
      }
      
      const data = await response.json();
      
      if (data.Response === 'False') {
        throw new Error(data.Error || 'No movies found');
      }
      
      setMovies(data.Search);
    } catch (err) {
      setError(err.message);
      setMovies([]);
    } finally {
      setLoading(false);
    }
  };
  
  const getMovieDetails = async (imdbID) => {
    setLoading(true);
    try {
      const response = await fetch(
        `${API_URL}?i=${imdbID}&apikey=${API_KEY}`
      );
      const data = await response.json();
      setSelectedMovie(data);
    } catch (err) {
      console.error('Error fetching details:', err);
    } finally {
      setLoading(false);
    }
  };
  
  const closeModal = () => {
    setSelectedMovie(null);
  };
  
  return (
    <div className="min-h-screen bg-gray-900 py-8 px-4">
      <div className="max-w-6xl mx-auto">
        {/* Header */}
        <div className="text-center text-white mb-8">
          <h1 className="text-5xl font-bold mb-2 flex items-center justify-center gap-2">
            <FaFilm /> Movie Search
          </h1>
          <p className="text-gray-400">Find information about your favorite movies</p>
        </div>
        
        {/* Search Section */}
        <div className="max-w-md mx-auto mb-8">
          <div className="flex gap-2">
            <input
              type="text"
              value={searchTerm}
              onChange={(e) => setSearchTerm(e.target.value)}
              onKeyPress={(e) => e.key === 'Enter' && searchMovies()}
              className="flex-1 bg-gray-800 text-white border border-gray-700 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
              placeholder="Enter movie name..."
            />
            <button
              onClick={searchMovies}
              disabled={loading}
              className="bg-blue-600 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-blue-700 transition disabled:opacity-50"
            >
              {loading ? '...' : <FaSearch />}
              Search
            </button>
          </div>
          
          {error && (
            <div className="mt-4 p-3 bg-red-900 text-red-200 rounded-lg">
              ⚠️ {error}
            </div>
          )}
        </div>
        
        {/* Movies Grid */}
        {loading && !movies.length ? (
          <div className="text-center text-white py-12">
            <div className="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-white"></div>
            <p className="mt-4">Loading movies...</p>
          </div>
        ) : movies.length > 0 ? (
          <>
            <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
              {movies.map(movie => (
                <div
                  key={movie.imdbID}
                  onClick={() => getMovieDetails(movie.imdbID)}
                  className="bg-gray-800 rounded-lg overflow-hidden cursor-pointer transform transition hover:scale-105"
                >
                  {movie.Poster !== 'N/A' ? (
                    <img
                      src={movie.Poster}
                      alt={movie.Title}
                      className="w-full h-80 object-cover"
                    />
                  ) : (
                    <div className="w-full h-80 bg-gray-700 flex items-center justify-center">
                      <FaFilm className="text-4xl text-gray-500" />
                    </div>
                  )}
                  <div className="p-4">
                    <h3 className="text-white font-semibold truncate">{movie.Title}</h3>
                    <p className="text-gray-400 text-sm">{movie.Year}</p>
                  </div>
                </div>
              ))}
            </div>
            <p className="text-center text-gray-400 mt-8">
              Found {movies.length} movies
            </p>
          </>
        ) : (
          !loading && !error && (
            <div className="text-center text-gray-400 py-12">
              <FaFilm className="text-6xl mx-auto mb-4" />
              <p>Search for a movie to get started!</p>
              <p className="text-sm mt-2">Try: Avengers, Inception, Titanic</p>
            </div>
          )
        )}
        
        {/* Movie Details Modal */}
        {selectedMovie && (
          <div className="fixed inset-0 bg-black bg-opacity-75 flex items-center justify-center p-4 z-50">
            <div className="bg-gray-800 rounded-lg max-w-2xl w-full max-h-
continue
Project 4: Movie Search App (continued)
jsx
            <div className="bg-gray-800 rounded-lg max-w-2xl w-full max-h-[90vh] overflow-y-auto">
              {/* Modal Header */}
              <div className="sticky top-0 bg-gray-800 p-4 border-b border-gray-700 flex justify-between items-center">
                <h2 className="text-xl font-bold text-white">{selectedMovie.Title}</h2>
                <button
                  onClick={closeModal}
                  className="text-gray-400 hover:text-white text-2xl"
                >
                  ✕
                </button>
              </div>
              
              {/* Modal Content */}
              <div className="p-6">
                <div className="flex flex-col md:flex-row gap-6">
                  {/* Poster */}
                  <div className="md:w-1/3">
                    {selectedMovie.Poster !== 'N/A' ? (
                      <img
                        src={selectedMovie.Poster}
                        alt={selectedMovie.Title}
                        className="w-full rounded-lg shadow-lg"
                      />
                    ) : (
                      <div className="w-full aspect-[2/3] bg-gray-700 rounded-lg flex items-center justify-center">
                        <FaFilm className="text-6xl text-gray-500" />
                      </div>
                    )}
                  </div>
                  
                  {/* Details */}
                  <div className="md:w-2/3 space-y-3">
                    <div className="flex items-center gap-2 text-gray-300">
                      <FaCalendar />
                      <span>{selectedMovie.Year}</span>
                      <span className="mx-2">•</span>
                      <span>{selectedMovie.Runtime}</span>
                      <span className="mx-2">•</span>
                      <span>{selectedMovie.Genre}</span>
                    </div>
                    
                    <div className="flex items-center gap-2">
                      <FaStar className="text-yellow-500" />
                      <span className="text-white font-semibold">{selectedMovie.imdbRating}</span>
                      <span className="text-gray-400">/10</span>
                      <span className="text-gray-400 ml-2">({selectedMovie.imdbVotes} votes)</span>
                    </div>
                    
                    <div className="flex items-center gap-2 text-gray-300">
                      <FaImdb />
                      <span>IMDb ID: {selectedMovie.imdbID}</span>
                    </div>
                    
                    <div className="border-t border-gray-700 pt-3 mt-3">
                      <h3 className="text-white font-semibold mb-2">Plot</h3>
                      <p className="text-gray-300 text-sm leading-relaxed">
                        {selectedMovie.Plot}
                      </p>
                    </div>
                    
                    <div className="grid grid-cols-2 gap-4 text-sm">
                      <div>
                        <span className="text-gray-400">Director:</span>
                        <p className="text-white">{selectedMovie.Director}</p>
                      </div>
                      <div>
                        <span className="text-gray-400">Writer:</span>
                        <p className="text-white">{selectedMovie.Writer}</p>
                      </div>
                      <div>
                        <span className="text-gray-400">Actors:</span>
                        <p className="text-white">{selectedMovie.Actors}</p>
                      </div>
                      <div>
                        <span className="text-gray-400">Country:</span>
                        <p className="text-white">{selectedMovie.Country}</p>
                      </div>
                      <div>
                        <span className="text-gray-400">Language:</span>
                        <p className="text-white">{selectedMovie.Language}</p>
                      </div>
                      <div>
                        <span className="text-gray-400">Awards:</span>
                        <p className="text-white">{selectedMovie.Awards}</p>
                      </div>
                    </div>
                    
                    {selectedMovie.BoxOffice && selectedMovie.BoxOffice !== 'N/A' && (
                      <div className="bg-green-900 bg-opacity-30 p-3 rounded-lg">
                        <span className="text-gray-400">Box Office:</span>
                        <span className="text-white ml-2 font-semibold">{selectedMovie.BoxOffice}</span>
                      </div>
                    )}
                  </div>
                </div>
              </div>
              
              {/* Modal Footer */}
              <div className="sticky bottom-0 bg-gray-800 p-4 border-t border-gray-700 flex justify-end">
                <button
                  onClick={closeModal}
                  className="px-4 py-2 bg-gray-700 text-white rounded hover:bg-gray-600 transition"
                >
                  Close
                </button>
              </div>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}

export default MovieSearchApp;
Project 5: Notes App with Categories
jsx
// Complete Notes App with categories, search, and local storage
import { useState, useEffect } from 'react';
import { FaPlus, FaTrash, FaEdit, FaSave, FaTimes, FaSearch, FaTag } from 'react-icons/fa';

function NotesApp() {
  // State for notes
  const [notes, setNotes] = useState(() => {
    const saved = localStorage.getItem('notes');
    return saved ? JSON.parse(saved) : [];
  });
  
  // State for form
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');
  const [category, setCategory] = useState('personal');
  const [editingId, setEditingId] = useState(null);
  
  // State for UI
  const [search, setSearch] = useState('');
  const [selectedCategory, setSelectedCategory] = useState('all');
  const [showForm, setShowForm] = useState(false);
  
  // Categories
  const categories = [
    { id: 'personal', name: 'Personal', color: 'blue', icon: '👤' },
    { id: 'work', name: 'Work', color: 'green', icon: '💼' },
    { id: 'ideas', name: 'Ideas', color: 'purple', icon: '💡' },
    { id: 'todo', name: 'Todo', color: 'yellow', icon: '✓' },
    { id: 'important', name: 'Important', color: 'red', icon: '⭐' }
  ];
  
  // Save notes to localStorage
  useEffect(() => {
    localStorage.setItem('notes', JSON.stringify(notes));
  }, [notes]);
  
  // Add or update note
  const saveNote = () => {
    if (!title.trim()) {
      alert('Please enter a title');
      return;
    }
    
    if (editingId) {
      // Update existing note
      setNotes(notes.map(note =>
        note.id === editingId
          ? {
              ...note,
              title,
              content,
              category,
              updatedAt: new Date().toISOString()
            }
          : note
      ));
      setEditingId(null);
    } else {
      // Add new note
      setNotes([...notes, {
        id: Date.now(),
        title,
        content,
        category,
        createdAt: new Date().toISOString(),
        updatedAt: new Date().toISOString()
      }]);
    }
    
    // Reset form
    setTitle('');
    setContent('');
    setCategory('personal');
    setShowForm(false);
  };
  
  // Edit note
  const editNote = (note) => {
    setTitle(note.title);
    setContent(note.content);
    setCategory(note.category);
    setEditingId(note.id);
    setShowForm(true);
  };
  
  // Delete note
  const deleteNote = (id) => {
    if (confirm('Are you sure you want to delete this note?')) {
      setNotes(notes.filter(note => note.id !== id));
    }
  };
  
  // Cancel editing
  const cancelEdit = () => {
    setTitle('');
    setContent('');
    setCategory('personal');
    setEditingId(null);
    setShowForm(false);
  };
  
  // Filter notes
  const filteredNotes = notes.filter(note => {
    const matchesSearch = note.title.toLowerCase().includes(search.toLowerCase()) ||
                          note.content.toLowerCase().includes(search.toLowerCase());
    const matchesCategory = selectedCategory === 'all' || note.category === selectedCategory;
    return matchesSearch && matchesCategory;
  });
  
  // Get category color
  const getCategoryColor = (categoryId) => {
    const cat = categories.find(c => c.id === categoryId);
    return cat ? cat.color : 'gray';
  };
  
  // Get category icon
  const getCategoryIcon = (categoryId) => {
    const cat = categories.find(c => c.id === categoryId);
    return cat ? cat.icon : '📝';
  };
  
  // Format date
  const formatDate = (dateString) => {
    const date = new Date(dateString);
    return date.toLocaleDateString() + ' ' + date.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
  };
  
  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-50 to-gray-100">
      <div className="max-w-6xl mx-auto p-4">
        {/* Header */}
        <div className="text-center mb-8">
          <h1 className="text-4xl font-bold text-gray-800 mb-2">📝 Notes App</h1>
          <p className="text-gray-600">Organize your thoughts with categories</p>
        </div>
        
        {/* Action Bar */}
        <div className="flex flex-wrap gap-4 mb-6">
          <button
            onClick={() => setShowForm(!showForm)}
            className="bg-blue-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-blue-600 transition"
          >
            <FaPlus /> {showForm ? 'Hide Form' : 'New Note'}
          </button>
          
          <div className="flex-1 min-w-[200px]">
            <div className="relative">
              <FaSearch className="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400" />
              <input
                type="text"
                value={search}
                onChange={(e) => setSearch(e.target.value)}
                className="w-full pl-10 pr-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
                placeholder="Search notes..."
              />
            </div>
          </div>
        </div>
        
        {/* Category Filters */}
        <div className="flex flex-wrap gap-2 mb-6">
          <button
            onClick={() => setSelectedCategory('all')}
            className={`px-4 py-2 rounded-lg transition ${
              selectedCategory === 'all'
                ? 'bg-gray-800 text-white'
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`}
          >
            All ({notes.length})
          </button>
          {categories.map(cat => {
            const count = notes.filter(n => n.category === cat.id).length;
            return (
              <button
                key={cat.id}
                onClick={() => setSelectedCategory(cat.id)}
                className={`px-4 py-2 rounded-lg transition ${
                  selectedCategory === cat.id
                    ? `bg-${cat.color}-500 text-white`
                    : `bg-${cat.color}-100 text-${cat.color}-700 hover:bg-${cat.color}-200`
                }`}
              >
                {cat.icon} {cat.name} ({count})
              </button>
            );
          })}
        </div>
        
        {/* Note Form */}
        {showForm && (
          <div className="bg-white rounded-lg shadow-lg p-6 mb-6">
            <h2 className="text-xl font-bold mb-4">
              {editingId ? 'Edit Note' : 'Create New Note'}
            </h2>
            
            <div className="space-y-4">
              <div>
                <label className="block text-gray-700 mb-2">Title *</label>
                <input
                  type="text"
                  value={title}
                  onChange={(e) => setTitle(e.target.value)}
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                  placeholder="Enter note title..."
                />
              </div>
              
              <div>
                <label className="block text-gray-700 mb-2">Category</label>
                <select
                  value={category}
                  onChange={(e) => setCategory(e.target.value)}
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                  {categories.map(cat => (
                    <option key={cat.id} value={cat.id}>
                      {cat.icon} {cat.name}
                    </option>
                  ))}
                </select>
              </div>
              
              <div>
                <label className="block text-gray-700 mb-2">Content</label>
                <textarea
                  value={content}
                  onChange={(e) => setContent(e.target.value)}
                  rows="6"
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                  placeholder="Write your note here..."
                />
              </div>
              
              <div className="flex gap-2">
                <button
                  onClick={saveNote}
                  className="bg-green-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-green-600 transition"
                >
                  <FaSave /> {editingId ? 'Update' : 'Save'}
                </button>
                <button
                  onClick={cancelEdit}
                  className="bg-gray-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-gray-600 transition"
                >
                  <FaTimes /> Cancel
                </button>
              </div>
            </div>
          </div>
        )}
        
        {/* Notes Grid */}
        {filteredNotes.length === 0 ? (
          <div className="text-center py-12">
            <div className="text-6xl mb-4">📭</div>
            <p className="text-gray-500">
              {search || selectedCategory !== 'all'
                ? 'No notes match your filters'
                : 'No notes yet. Create your first note!'}
            </p>
          </div>
        ) : (
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            {filteredNotes.map(note => (
              <div
                key={note.id}
                className="bg-white rounded-lg shadow-md hover:shadow-xl transition-shadow overflow-hidden"
              >
                {/* Category Badge */}
                <div className={`bg-${getCategoryColor(note.category)}-500 px-3 py-1 text-white text-sm flex items-center gap-1`}>
                  <FaTag className="text-xs" />
                  <span>{getCategoryIcon(note.category)} {categories.find(c => c.id === note.category)?.name}</span>
                </div>
                
                {/* Content */}
                <div className="p-4">
                  <h3 className="font-bold text-lg mb-2 line-clamp-2">{note.title}</h3>
                  <p className="text-gray-600 text-sm mb-4 line-clamp-3">{note.content}</p>
                  
                  {/* Metadata */}
                  <div className="text-xs text-gray-400 mb-4">
                    <div>Created: {formatDate(note.createdAt)}</div>
                    <div>Updated: {formatDate(note.updatedAt)}</div>
                  </div>
                  
                  {/* Actions */}
                  <div className="flex gap-2 pt-3 border-t">
                    <button
                      onClick={() => editNote(note)}
                      className="flex-1 bg-blue-500 text-white px-3 py-1 rounded text-sm flex items-center justify-center gap-1 hover:bg-blue-600 transition"
                    >
                      <FaEdit /> Edit
                    </button>
                    <button
                      onClick={() => deleteNote(note.id)}
                      className="flex-1 bg-red-500 text-white px-3 py-1 rounded text-sm flex items-center justify-center gap-1 hover:bg-red-600 transition"
                    >
                      <FaTrash /> Delete
                    </button>
                  </div>
                </div>
              </div>
            ))}
          </div>
        )}
        
        {/* Stats Footer */}
        <div className="mt-8 p-4 bg-white rounded-lg shadow text-center text-gray-600">
          <p>
            📊 Total: {notes.length} notes • 
            📝 Active: {filteredNotes.length} showing • 
            🏷️ {categories.length} categories
          </p>
          <p className="text-sm mt-1">
            💾 Your notes are automatically saved in your browser!
          </p>
        </div>
      </div>
    </div>
  );
}

export default NotesApp;
Project 6: Expense Tracker
jsx
// Complete Expense Tracker with charts and local storage
import { useState, useEffect } from 'react';
import { FaPlus, FaTrash, FaEdit, FaChartLine, FaWallet, FaShoppingCart, FaHome, FaCar, FaUtensils, FaFilm } from 'react-icons/fa';

function ExpenseTracker() {
  // State for transactions
  const [transactions, setTransactions] = useState(() => {
    const saved = localStorage.getItem('transactions');
    return saved ? JSON.parse(saved) : [];
  });
  
  // State for form
  const [description, setDescription] = useState('');
  const [amount, setAmount] = useState('');
  const [type, setType] = useState('expense');
  const [category, setCategory] = useState('food');
  const [editingId, setEditingId] = useState(null);
  
  // State for filters
  const [filterType, setFilterType] = useState('all');
  const [filterCategory, setFilterCategory] = useState('all');
  const [dateRange, setDateRange] = useState({ start: '', end: '' });
  
  // Categories
  const categories = {
    expense: [
      { id: 'food', name: 'Food & Dining', icon: FaUtensils, color: 'orange' },
      { id: 'transport', name: 'Transportation', icon: FaCar, color: 'blue' },
      { id: 'shopping', name: 'Shopping', icon: FaShoppingCart, color: 'pink' },
      { id: 'entertainment', name: 'Entertainment', icon: FaFilm, color: 'purple' },
      { id: 'bills', name: 'Bills & Utilities', icon: FaHome, color: 'red' }
    ],
    income: [
      { id: 'salary', name: 'Salary', icon: FaWallet, color: 'green' },
      { id: 'freelance', name: 'Freelance', icon: FaChartLine, color: 'teal' },
      { id: 'investment', name: 'Investment', icon: FaChartLine, color: 'indigo' },
      { id: 'gift', name: 'Gift', icon: FaWallet, color: 'yellow' }
    ]
  };
  
  // Save to localStorage
  useEffect(() => {
    localStorage.setItem('transactions', JSON.stringify(transactions));
  }, [transactions]);
  
  // Add or update transaction
  const saveTransaction = () => {
    if (!description.trim()) {
      alert('Please enter a description');
      return;
    }
    
    if (!amount || isNaN(amount) || Number(amount) <= 0) {
      alert('Please enter a valid amount');
      return;
    }
    
    if (editingId) {
      // Update existing
      setTransactions(transactions.map(t =>
        t.id === editingId
          ? {
              ...t,
              description,
              amount: Number(amount),
              type,
              category,
              updatedAt: new Date().toISOString()
            }
          : t
      ));
      setEditingId(null);
    } else {
      // Add new
      setTransactions([...transactions, {
        id: Date.now(),
        description,
        amount: Number(amount),
        type,
        category,
        date: new Date().toISOString(),
        createdAt: new Date().toISOString()
      }]);
    }
    
    // Reset form
    setDescription('');
    setAmount('');
    setType('expense');
    setCategory('food');
  };
  
  // Delete transaction
  const deleteTransaction = (id) => {
    if (confirm('Are you sure you want to delete this transaction?')) {
      setTransactions(transactions.filter(t => t.id !== id));
    }
  };
  
  // Edit transaction
  const editTransaction = (transaction) => {
    setDescription(transaction.description);
    setAmount(transaction.amount.toString());
    setType(transaction.type);
    setCategory(transaction.category);
    setEditingId(transaction.id);
  };
  
  // Calculate totals
  const calculateTotals = () => {
    const income = transactions
      .filter(t => t.type === 'income')
      .reduce((sum, t) => sum + t.amount, 0);
    
    const expense = transactions
      .filter(t => t.type === 'expense')
      .reduce((sum, t) => sum + t.amount, 0);
    
    const balance = income - expense;
    
    return { income, expense, balance };
  };
  
  // Filter transactions
  const filteredTransactions = transactions.filter(t => {
    // Type filter
    if (filterType !== 'all' && t.type !== filterType) return false;
    
    // Category filter
    if (filterCategory !== 'all' && t.category !== filterCategory) return false;
    
    // Date range filter
    if (dateRange.start) {
      const tDate = new Date(t.date).toISOString().split('T')[0];
      if (dateRange.start && tDate < dateRange.start) return false;
      if (dateRange.end && tDate > dateRange.end) return false;
    }
    
    return true;
  });
  
  // Group transactions by date
  const groupedTransactions = filteredTransactions.reduce((groups, transaction) => {
    const date = new Date(transaction.date).toLocaleDateString();
    if (!groups[date]) groups[date] = [];
    groups[date].push(transaction);
    return groups;
  }, {});
  
  const totals = calculateTotals();
  
  // Get category details
  const getCategoryDetails = (categoryId, type) => {
    const catList = type === 'income' ? categories.income : categories.expense;
    return catList.find(c => c.id === categoryId);
  };
  
  return (
    <div className="min-h-screen bg-gray-100">
      <div className="max-w-6xl mx-auto p-4">
        {/* Header */}
        <div className="text-center mb-8">
          <h1 className="text-4xl font-bold text-gray-800 mb-2">💰 Expense Tracker</h1>
          <p className="text-gray-600">Track your income and expenses</p>
        </div>
        
        {/* Summary Cards */}
        <div className="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
          <div className="bg-white rounded-lg shadow p-6">
            <div className="flex items-center justify-between">
              <div>
                <p className="text-gray-500 text-sm">Total Balance</p>
                <p className={`text-3xl font-bold ${totals.balance >= 0 ? 'text-green-600' : 'text-red-600'}`}>
                  ${totals.balance.toFixed(2)}
                </p>
              </div>
              <FaWallet className="text-4xl text-gray-400" />
            </div>
          </div>
          
          <div className="bg-white rounded-lg shadow p-6">
            <div className="flex items-center justify-between">
              <div>
                <p className="text-gray-500 text-sm">Total Income</p>
                <p className="text-3xl font-bold text-green-600">
                  ${totals.income.toFixed(2)}
                </p>
              </div>
              <FaChartLine className="text-4xl text-green-500" />
            </div>
          </div>
          
          <div className="bg-white rounded-lg shadow p-6">
            <div className="flex items-center justify-between">
              <div>
                <p className="text-gray-500 text-sm">Total Expenses</p>
                <p className="text-3xl font-bold text-red-600">
                  ${totals.expense.toFixed(2)}
                </p>
              </div>
              <FaShoppingCart className="text-4xl text-red-500" />
            </div>
          </div>
        </div>
        
        {/* Add Transaction Form */}
        <div className="bg-white rounded-lg shadow p-6 mb-8">
          <h2 className="text-xl font-bold mb-4">
            {editingId ? 'Edit Transaction' : 'Add New Transaction'}
          </h2>
          
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
            <input
              type="text"
              value={description}
              onChange={(e) => setDescription(e.target.value)}
              className="border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
              placeholder="Description..."
            />
            
            <input
              type="number"
              value={amount}
              onChange={(e) => setAmount(e.target.value)}
              className="border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
              placeholder="Amount..."
              step="0.01"
            />
            
            <select
              value={type}
              onChange={(e) => {
                setType(e.target.value);
                setCategory(e.target.value === 'income' ? 'salary' : 'food');
              }}
              className="border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
            >
              <option value="expense">Expense</option>
              <option value="income">Income</option>
            </select>
            
            <select
              value={category}
              onChange={(e) => setCategory(e.target.value)}
              className="border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
            >
              {(type === 'income' ? categories.income : categories.expense).map(cat => (
                <option key={cat.id} value={cat.id}>{cat.name}</option>
              ))}
            </select>
          </div>
          
          <div className="flex gap-2 mt-4">
            <button
              onClick={saveTransaction}
              className="bg-blue-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-blue-600 transition"
            >
              <FaPlus /> {editingId ? 'Update' : 'Add'} Transaction
            </button>
            {editingId && (
              <button
                onClick={() => {
                  setEditingId(null);
                  setDescription('');
                  setAmount('');
                  setType('expense');
                  setCategory('food');
                }}
                className="bg-gray-500 text-white px-6 py-2 rounded-lg hover:bg-gray-600 transition"
              >
                Cancel
              </button>
            )}
          </div>
        </div>
        
        {/* Filters */}
        <div className="bg-white rounded-lg shadow p-4 mb-6">
          <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
            <select
              value={filterType}
              onChange={(e) => setFilterType(e.target.value)}
              className="border border-gray-300 rounded-lg px-4 py-2"
            >
              <option value="all">All Transactions</option>
              <option value="income">Income Only</option>
              <option value="expense">Expense Only</option>
            </select>
            
            <select
              value={filterCategory}
              onChange={(e) => setFilterCategory(e.target.value)}
              className="border border-gray-300 rounded-lg px-4 py-2"
            >
              <option value="all">All Categories</option>
              {[...categories.expense, ...categories.income].map(cat => (
                <option key={cat.id} value={cat.id}>{cat.name}</option>
              ))}
            </select>
            
            <div className="flex gap-2">
              <input
                type="date"
                value={dateRange.start}
                onChange={(e) => setDateRange({ ...dateRange, start: e.target.value })}
                className="flex-1 border border-gray-300 rounded-lg px-4 py-2"
                placeholder="Start Date"
              />
              <input
                type="date"
                value={dateRange.end}
                onChange={(e) => setDateRange({ ...dateRange, end: e.target.value })}
                className="flex-1 border border-gray-300 rounded-lg px-4 py-2"
                placeholder="End Date"
              />
              {(dateRange.start || dateRange.end) && (
                <button
                  onClick={() => setDateRange({ start: '', end: '' })}
                  className="px-3 bg-gray-500 text-white rounded-lg hover:bg-gray-600"
                >
                  Clear
                </button>
              )}
            </div>
          </div>
        </div>
        
        {/* Transactions List */}
        <div className="bg-white rounded-lg shadow overflow-hidden">
          <div className="p-4 bg-gray-50 border-b">
            <h2 className="font-bold">Transactions</h2>
            <p className="text-sm text-gray-500">
              Showing {filteredTransactions.length} of {transactions.length} transactions
            </p>
          </div>
          
          {filteredTransactions.length === 0 ? (
            <div className="text-center py-12 text-gray-500">
              No transactions found
            </div>
          ) : (
            <div className="divide-y divide-gray-200">
              {Object.entries(groupedTransactions).map(([date, dayTransactions]) => (
                <div key={date}>
                  <div className="bg-gray-50 px-4 py-2 font-semibold text-gray-600">
                    {date}
                  </div>
                  {dayTransactions.map(transaction => {
                    const categoryDetails = getCategoryDetails(transaction.category, transaction.type);
                    const IconComponent = categoryDetails?.icon;
                    const isIncome = transaction.type === 'income';
                    
                    return (
                      <div key={transaction.id} className="p-4 hover:bg-gray-50 transition flex items-center justify-between">
                        <div className="flex items-center gap-3">
                          {IconComponent && (
                            <div className={`w-10 h-10 rounded-full flex items-center justify-center bg-${categoryDetails?.color}-100`}>
                              <IconComponent className={`text-${categoryDetails?.color}-600`} />
                            </div>
                          )}
                          <div>
                            <p className="font-semibold">{transaction.description}</p>
                            <p className="text-sm text-gray-500">{categoryDetails?.name}</p>
                          </div>
                        </div>
                        
                        <div className="flex items-center gap-4">
                          <p className={`font-bold ${isIncome ? 'text-green-600' : 'text-red-600'}`}>
                            {isIncome ? '+' : '-'}${transaction.amount.toFixed(2)}
                          </p>
                          <button
                            onClick={() => editTransaction(transaction)}
                            className="text-blue-500 hover:text-blue-700"
                          >
                            <FaEdit />
                          </button>
                          <button
                            onClick={() => deleteTransaction(transaction.id)}
                            className="text-red-500 hover:text-red-700"
                          >
                            <FaTrash />
                          </button>
                        </div>
                      </div>
                    );
                  })}
                </div>
              ))}
            </div>
          )}
        </div>
      </div>
    </div>
  );
}

export default ExpenseTracker;
Project 7: Recipe Finder
jsx
// Complete Recipe Finder with API integration
import { useState } from 'react';
import { FaSearch, FaClock, FaUtensils, FaHeart, FaRegHeart, FaStar, FaExternalLinkAlt } from 'react-icons/fa';

function RecipeFinder() {
  const [searchTerm, setSearchTerm] = useState('');
  const [recipes, setRecipes] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [selectedRecipe, setSelectedRecipe] = useState(null);
  const [favorites, setFavorites] = useState(() => {
    const saved = localStorage.getItem('favoriteRecipes');
    return saved ? JSON.parse(saved) : [];
  });
  
  // Spoonacular API - Get your free API key at https://spoonacular.com/food-api
  const API_KEY = 'YOUR_API_KEY_HERE'; // Replace with your actual API key
  const API_URL = 'https://api.spoonacular.com/recipes';
  
  const searchRecipes = async () => {
    if (!searchTerm.trim()) {
      setError('Please enter an ingredient or recipe name');
      return;
    }
    
    setLoading(true);
    setError(null);
    
    try {
      const response = await fetch(
        `${API_URL}/complexSearch?query=${searchTerm}&number=12&apiKey=${API_KEY}`
      );
      
      if (!response.ok) {
        throw new Error('Failed to fetch recipes');
      }
      
      const data = await response.json();
      setRecipes(data.results);
      
      if (data.results.length === 0) {
        setError('No recipes found. Try a different search term.');
      }
    } catch (err) {
      setError(err.message);
      setRecipes([]);
    } finally {
      setLoading(false);
    }
  };
  
  const getRecipeDetails = async (id) => {
    setLoading(true);
    try {
      const response = await fetch(
        `${API_URL}/${id}/information?apiKey=${API_KEY}`
      );
      const data = await response.json();
      setSelectedRecipe(data);
    } catch (err) {
      console.error('Error fetching details:', err);
    } finally {
      setLoading(false);
    }
  };
  
  const toggleFavorite = (recipe) => {
    const isFavorite = favorites.some(fav => fav.id === recipe.id);
    
    if (isFavorite) {
      setFavorites(favorites.filter(fav => fav.id !== recipe.id));
    } else {
      setFavorites([...favorites, { id: recipe.id, title: recipe.title, image: recipe.image }]);
    }
  };
  
  const isFavorite = (recipeId) => {
    return favorites.some(fav => fav.id === recipeId);
  };
  
  // Save favorites to localStorage
  useState(() => {
    localStorage.setItem('favoriteRecipes', JSON.stringify(favorites));
  }, [favorites]);
  
  return (
    <div className="min-h-screen bg-gradient-to-br from-orange-50 to-red-50">
      <div className="max-w-6xl mx-auto p-4">
        {/* Header */}
        <div className="text-center mb-8">
          <h1 className="text-5xl font-bold text-gray-800 mb-2">🍳 Recipe Finder</h1>
          <p className="text-gray-600">Discover delicious recipes with ingredients you have</p>
        </div>
        
        {/* Search Section */}
        <div className="max-w-2xl mx-auto mb-8">
          <div className="flex gap-2">
            <input
              type="text"
              value={searchTerm}
              onChange={(e) => setSearchTerm(e.target.value)}
              onKeyPress={(e) => e.key === 'Enter' && searchRecipes()}
              className="flex-1 bg-white border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-2 focus:ring-orange-500"
              placeholder="Search by ingredient, cuisine, or recipe name..."
            />
            <button
              onClick={searchRecipes}
              disabled={loading}
              className="bg-orange-500 text-white px-6 py-3 rounded-lg flex items-center gap-2 hover:bg-orange-600 transition disabled:opacity-50"
            >
              {loading ? '...' : <FaSearch />}
              Search
            </button>
          </div>
          
          {error && (
            <div className="mt-4 p-3 bg-red-100 text-red-700 rounded-lg">
              ⚠️ {error}
            </div>
          )}
        </div>
        
        {/* Favorites Section */}
        {favorites.length > 0 && (
          <div className="mb-8">
            <h2 className="text-2xl font-bold mb-4 flex items-center gap-2">
              <FaHeart className="text-red-500" /> Your Favorites
            </h2>
            <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
              {favorites.map(recipe => (
                <div
                  key={recipe.id}
                  onClick={() => getRecipeDetails(recipe.id)}
                  className="bg-white rounded-lg shadow-md overflow-hidden cursor-pointer transform transition hover:scale-105"
                >
                  <img
                    src={recipe.image}
                    alt={recipe.title}
                    className="w-full h-40 object-cover"
                  />
                  <div className="p-3">
                    <p className="font-semibold text-sm line-clamp-2">{recipe.title}</p>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}
        
        {/* Recipes Grid */}
        {loading && !selectedRecipe ? (
          <div className="text-center py-12">
            <div className="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-orange-500"></div>
            <p className="mt-4 text-gray-600">Searching for recipes...</p>
          </div>
        ) : recipes.length > 0 ? (
          <>
            <h2 className="text-2xl font-bold mb-4">Search Results</h2>
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
              {recipes.map(recipe => (
                <div
                  key={recipe.id}
                  className="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-xl transition"
                >
                  <div className="relative">
                    <img
                      src={recipe.image}
                      alt={recipe.title}
                      className="w-full h-48 object-cover"
                    />
                    <button
                      onClick={() => toggleFavorite(recipe)}
                      className="absolute top-2 right-2 bg-white rounded-full p-2 shadow-md hover:scale-110 transition"
                    >
                      {isFavorite(recipe.id) ? (
                        <FaHeart className="text-red-500" />
                      ) : (
                        <FaRegHeart className="text-gray-500" />
                      )}
                    </button>
                  </div>
                  <div className="p-4">
                    <h3 className="font-bold text-lg mb-2 line-clamp-2">{recipe.title}</h3>
                    <div className="flex items-center gap-4 text-sm text-gray-500 mb-3">
                      <div className="flex items-center gap-1">
                        <FaClock /> {recipe.readyInMinutes || 'N/A'} min
                      </div>
                      <div className="flex items-center gap-1">
                        <FaUtensils /> {recipe.servings || 'N/A'} servings
                      </div>
                    </div>
                    <button
                      onClick={() => getRecipeDetails(recipe.id)}
                      className="w-full bg-orange-500 text-white py-2 rounded-lg hover:bg-orange-600 transition"
                    >
                      View Recipe
                    </button>
                  </div>
                </div>
              ))}
            </div>
          </>
        ) : (
          !loading && !error && (
            <div className="text-center py-12">
              <div className="text-6xl mb-4">🍽️</div>
              <p className="text-gray-500">Search for a recipe to get started!</p>
              <p className="text-sm text-gray-400 mt-2">Try: pasta, chicken, vegetarian, dessert</p>
            </div>
          )
        )}
        
        {/* Recipe Details Modal */}
        {selectedRecipe && (
          <div className="fixed inset-0 bg-black bg-opacity-75 flex items-center justify-center p-4 z-50 overflow-y-auto">
            <div className="bg-white rounded-lg max-w-4xl w-full max-h-[90vh] overflow-y-auto">
              {/* Modal Header */}
              <div className="sticky top-0 bg-white p-4 border-b flex justify-between items-center">
                <h2 className="text-2xl font-bold">{selectedRecipe.title}</h2>
                <button
                  onClick={() => setSelectedRecipe(null)}
                  className="text-gray-500 hover:text-gray-700 text-2xl"
                >
                  ✕
                </button>
              </div>
              
              {/* Modal Content */}
              <div className="p-6">
                <img
                  src={selectedRecipe.image}
                  alt={selectedRecipe.title}
                  className="w-full max-h-96 object-cover rounded-lg mb-6"
                />
                
                <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-6">
                  <div className="bg-gray-50 p-3 rounded-lg text-center">
                    <FaClock className="inline-block text-orange-500 mb-1" />
                    <p className="text-sm text-gray-500">Ready In</p>
                    <p className="font-bold">{selectedRecipe.readyInMinutes} minutes</p>
                  </div>
                  <div className="bg-gray-50 p-3 rounded-lg text-center">
                    <FaUtensils className="inline-block text-orange-500 mb-1" />
                    <p className="text-sm text-gray-500">Servings</p>
                    <p className="font-bold">{selectedRecipe.servings}</p>
                  </div>
                  <div className="bg-gray-50 p-3 rounded-lg text-center">
                    <FaStar className="inline-block text-yellow-500 mb-1" />
                    <p className="text-sm text-gray-500">Health Score</p>
                    <p className="font-bold">{selectedRecipe.healthScore || 'N/A'}</p>
                  </div>
                </div>
                
                {/* Ingredients */}
                <div className="mb-6">
                  <h3 className="text-xl font-bold mb-3">Ingredients</h3>
                  <ul className="grid grid-cols-1 md:grid-cols-2 gap-2">
                    {selectedRecipe.extendedIngredients?.map(ingredient => (
                      <li key={ingredient.id} className="flex items-center gap-2 text-gray-700">
                        <span className="w-2 h-2 bg-orange-500 rounded-full"></span>
                        {ingredient.original}
                      </li>
                    ))}
                  </ul>
                </div>
                
                {/* Instructions */}
                <div className="mb-6">
                  <h3 className="text-xl font-bold mb-3">Instructions</h3>
                  {selectedRecipe.instructions ? (
                    <div dangerouslySetInnerHTML={{ __html: selectedRecipe.instructions }} />
                  ) : (
                    <p className="text-gray-500">No instructions available.</p>
                  )}
                </div>
                
                {/* Source Link */}
                {selectedRecipe.sourceUrl && (
                  <a
                    href={selectedRecipe.sourceUrl}
                    target="_blank"
                    rel="noopener noreferrer"
                    className="inline-flex items-center gap-2 text-orange-500 hover:text-orange-600"
                  >
                    View Full Recipe <FaExternalLinkAlt className="text-sm" />
                  </a>
                )}
              </div>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}

export default RecipeFinder;
Project 8: User Management Dashboard
jsx
// Complete User Management Dashboard with CRUD operations
import { useState, useEffect } from 'react';
import { FaUserPlus, FaEdit, FaTrash, FaSearch, FaUsers, FaUserCheck, FaUserTimes } from 'react-icons/fa';

function UserManagementDashboard() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  const [search, setSearch] = useState('');
  const [showForm, setShowForm] = useState(false);
  const [editingUser, setEditingUser] = useState(null);
  
  // Form state
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    phone: '',
    role: 'user',
    status: 'active'
  });
  
  // Fetch users from API
  useEffect(() => {
    fetchUsers();
  }, []);
  
  const fetchUsers = async () => {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/users');
      const data = await response.json();
      // Transform data to match our format
      const formattedUsers = data.map(user => ({
        id: user.id,
        name: user.name,
        email: user.email,
        phone: user.phone,
        role: user.id === 1 ? 'admin' : user.id === 2 ? 'manager' : 'user',
        status: user.id % 2 === 0 ? 'active' : 'inactive',
        createdAt: new Date().toISOString()
      }));
      setUsers(formattedUsers);
    } catch (err) {
      setError('Failed to fetch users');
    } finally {
      setLoading(false);
    }
  };
  
  // Add or update user
  const saveUser = () => {
    if (!formData.name || !formData.email) {
      alert('Please fill in all required fields');
      return;
    }
    
    if (editingUser) {
      // Update existing user
      setUsers(users.map(user =>
        user.id === editingUser.id
          ? { ...user, ...formData, updatedAt: new Date().toISOString() }
          : user
      ));
    } else {
      // Add new user
      const newUser = {
        id: Date.now(),
        ...formData,
        createdAt: new Date().toISOString()
      };
      setUsers([newUser, ...users]);
    }
    
    resetForm();
  };
  
  // Edit user
  const editUser = (user) => {
    setEditingUser(user);
    setFormData({
      name: user.name,
      email: user.email,
      phone: user.phone || '',
      role: user.role,
      status: user.status
    });
    setShowForm(true);
  };
  
  // Delete user
  const deleteUser = (id) => {
    if (confirm('Are you sure you want to delete this user?')) {
      setUsers(users.filter(user => user.id !== id));
    }
  };
  
  // Reset form
  const resetForm = () => {
    setFormData({
      name: '',
      email: '',
      phone: '',
      role: 'user',
      status: 'active'
    });
    setEditingUser(null);
    setShowForm(false);
  };
  
  // Filter users
  const filteredUsers = users.filter(user =>
    user.name.toLowerCase().includes(search.toLowerCase()) ||
    user.email.toLowerCase().includes(search.toLowerCase())
  );
  
  // Statistics
  const stats = {
    total: users.length,
    active: users.filter(u => u.status === 'active').length,
    inactive: users.filter(u => u.status === 'inactive').length,
    admins: users.filter(u => u.role === 'admin').length
  };
  
  // Get role badge color
  const getRoleColor = (role) => {
    switch(role) {
      case 'admin': return 'bg-red-100 text-red-700';
      case 'manager': return 'bg-purple-100 text-purple-700';
      default: return 'bg-blue-100 text-blue-700';
    }
  };
  
  // Get status badge color
  const getStatusColor = (status) => {
    return status === 'active' ? 'bg-green-100 text-green-700' : 'bg-gray-100 text-gray-700';
  };
  
  if (loading) {
    return (
      <div className="min-h-screen flex items-center justify-center">
        <div className="text-center">
          <div className="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-blue-500"></div>
          <p className="mt-4 text-gray-600">Loading users...</p>
        </div>
      </div>
    );
  }
  
  return (
    <div className="min-h-screen bg-gray-100">
      <div className="max-w-7xl mx-auto p-4">
        {/* Header */}
        <div className="mb-8">
          <h1 className="text-3xl font-bold text-gray-800 mb-2">User Management Dashboard</h1>
          <p className="text-gray-600">Manage users, roles, and permissions</p>
        </div>
        
        {/* Stats Cards */}
        <div className="grid grid-cols-1 md:grid-cols-4 gap-4 mb-8">
          <div className="bg-white rounded-lg shadow p-4 flex items-center gap-4">
            <div className="bg-blue-100 p-3 rounded-full">
              <FaUsers className="text-blue-600 text-xl" />
            </div>
            <div>
              <p className="text-gray-500 text-sm">Total Users</p>
              <p className="text-2xl font-bold">{stats.total}</p>
            </div>
          </div>
          
          <div className="bg-white rounded-lg shadow p-4 flex items-center gap-4">
            <div className="bg-green-100 p-3 rounded-full">
              <FaUserCheck className="text-green-600 text-xl" />
            </div>
            <div>
              <p className="text-gray-500 text-sm">Active Users</p>
              <p className="text-2xl font-bold">{stats.active}</p>
            </div>
          </div>
          
          <div className="bg-white rounded-lg shadow p-4 flex items-center gap-4">
            <div className="bg-gray-100 p-3 rounded-full">
              <FaUserTimes className="text-gray-600 text-xl" />
            </div>
            <div>
              <p className="text-gray-500 text-sm">Inactive Users</p>
              <p className="text-2xl font-bold">{stats.inactive}</p>
            </div>
          </div>
          
          <div className="bg-white rounded-lg shadow p-4 flex items-center gap-4">
            <div className="bg-red-100 p-3 rounded-full">
              <FaUserCheck className="text-red-600 text-xl" />
            </div>
            <div>
              <p className="text-gray-500 text-sm">Administrators</p>
              <p className="text-2xl font-bold">{stats.admins}</p>
            </div>
          </div>
        </div>
        
        {/* Action Bar */}
        <div className="flex flex-wrap gap-4 mb-6">
          <button
            onClick={() => setShowForm(!showForm)}
            className="bg-blue-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-blue-600 transition"
          >
            <FaUserPlus /> {showForm ? 'Cancel' : 'Add User'}
          </button>
          
          <div className="flex-1 min-w-[200px]">
            <div className="relative">
              <FaSearch className="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400" />
              <input
                type="text"
                value={search}
                onChange={(e) => setSearch(e.target.value)}
                className="w-full pl-10 pr-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
                placeholder="Search users..."
              />
            </div>
          </div>
        </div>
        
        {/* User Form */}
        {showForm && (
          <div className="bg-white rounded-lg shadow p-6 mb-6">
            <h2 className="text-xl font-bold mb-4">
              {editingUser ? 'Edit User' : 'Add New User'}
            </h2>
            
            <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div>
                <label className="block text-gray-700 mb-2">Name *</label>
                <input
                  type="text"
                  value={formData.name}
                  onChange={(e) => setFormData({ ...formData, name: e.target.value })}
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>
              
              <div>
                <label className="block text-gray-700 mb-2">Email *</label>
                <input
                  type="email"
                  value={formData.email}
                  onChange={(e) => setFormData({ ...formData, email: e.target.value })}
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>
              
              <div>
                <label className="block text-gray-700 mb-2">Phone</label>
                <input
                  type="tel"
                  value={formData.phone}
                  onChange={(e) => setFormData({ ...formData, phone: e.target.value })}
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>
              
              <div>
                <label className="block text-gray-700 mb-2">Role</label>
                <select
                  value={formData.role}
                  onChange={(e) => setFormData({ ...formData, role: e.target.value })}
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                  <option value="user">User</option>
                  <option value="manager">Manager</option>
                  <option value="admin">Admin</option>
                </select>
              </div>
              
              <div>
                <label className="block text-gray-700 mb-2">Status</label>
                <select
                  value={formData.status}
                  onChange={(e) => setFormData({ ...formData, status: e.target.value })}
                  className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                  <option value="active">Active</option>
                  <option value="inactive">Inactive</option>
                </select>
              </div>
            </div>
            
            <div className="flex gap-2 mt-4">
              <button
                onClick={saveUser}
                className="bg-green-500 text-white px-6 py-2 rounded-lg hover:bg-green-600 transition"
              >
                {editingUser ? 'Update User' : 'Create User'}
              </button>
              <button
                onClick={resetForm}
                className="bg-gray-500 text-white px-6 py-2 rounded-lg hover:bg-gray-600 transition"
              >
                Cancel
              </button>
            </div>
          </div>
        )}
        
        {/* Users Table */}
        <div className="bg-white rounded-lg shadow overflow-hidden">
          <div className="overflow-x-auto">
            <table className="w-full">
              <thead className="bg-gray-50">
                <tr>
                  <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">User</th>
                  <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Contact</th>
                  <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Role</th>
                  <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
                  <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Actions</th>
                </tr>
              </thead>
              <tbody className="bg-white divide-y divide-gray-200">
                {filteredUsers.map(user => (
                  <tr key={user.id} className="hover:bg-gray-50">
                    <td className="px-6 py-4">
                      <div className="flex items-center">
                        <div className="flex-shrink-0 h-10 w-10 bg-blue-100 rounded-full flex items-center justify-center">
                          <FaUsers className="text-blue-600" />
                        </div>
                        <div className="ml-4">
                          <div className="text-sm font-medium text-gray-900">{user.name}</div>
                          <div className="text-sm text-gray-500">ID: {user.id}</div>
                        </div>
                      </div>
                    </td>
                    <td className="px-6 py-4">
                      <div className="text-sm text-gray-900">{user.email}</div>
                      <div className="text-sm text-gray-500">{user.phone || 'No phone'}</div>
                    </td>
                    <td className="px-6 py-4">
                      <span className={`px-2 py-1 inline-flex text-xs leading-5 font-semibold rounded-full ${getRoleColor(user.role)}`}>
                        {user.role}
                      </span>
                    </td>
                    <td className="px-6 py-4">
                      <span className={`px-2 py-1 inline-flex text-xs leading-5 font-semibold rounded-full ${getStatusColor(user.status)}`}>
                        {user.status}
                      </span>
                    </td>
                    <td className="px-6 py-4 text-sm font-medium">
                      <button
                        onClick={() => editUser(user)}
                        className="text-blue-600 hover:text-blue-900 mr-3"
                      >
                        <FaEdit />
                      </button>
                      <button
                        onClick={() => deleteUser(user.id)}
                        className="text-red-600 hover:text-red-900"
                      >
                        <FaTrash />
                      </button>
                    </td>
                  </tr>
                ))}
              </tbody>
            </table>
          </div>
          
          {filteredUsers.length === 0 && (
            <div className="text-center py-12 text-gray-500">
              No users found
            </div>
          )}
        </div>
      </div>
    </div>
  );
}

export default UserManagementDashboard;
Project 9: Blog Posts with Comments
jsx
// Complete Blog App with posts, comments, and local storage
import { useState, useEffect } from 'react';
import { FaHeart, FaRegHeart, FaComment, FaShare, FaCalendar, FaUser, FaPlus, FaTimes } from 'react-icons/fa';

function BlogApp() {
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(true);
  const [selectedPost, setSelectedPost] = useState(null);
  const [showCreateForm, setShowCreateForm] = useState(false);
  const [newPost, setNewPost] = useState({ title: '', content: '', author: '' });
  const [commentText, setCommentText] = useState('');
  
  // Fetch posts from API
  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then(res => res.json())
      .then(data => {
        // Add additional fields
        const formattedPosts = data.slice(0, 10).map(post => ({
          ...post,
          author: `Author ${post.userId}`,
          likes: Math.floor(Math.random() * 100),
          liked: false,
          comments: [
            { id: 1, author: 'John Doe', text: 'Great post!', date: new Date().toISOString() },
            { id: 2, author: 'Jane Smith', text: 'Thanks for sharing!', date: new Date().toISOString() }
          ],
          createdAt: new Date().toISOString()
        }));
        setPosts(formattedPosts);
        setLoading(false);
      });
  }, []);
  
  // Like a post
  const likePost = (postId) => {
    setPosts(posts.map(post =>
      post.id === postId
        ? { ...post, liked: !post.liked, likes: post.liked ? post.likes - 1 : post.likes + 1 }
        : post
    ));
  };
  
  // Add comment
  const addComment = (postId) => {
    if (!commentText.trim()) return;
    
    const newComment = {
      id: Date.now(),
      author: 'You',
      text: commentText,
      date: new Date().toISOString()
    };
    
    setPosts(posts.map(post =>
      post.id === postId
        ? { ...post, comments: [...post.comments, newComment] }
        : post
    ));
    setCommentText('');
  };
  
  // Create new post
  const createPost = () => {
    if (!newPost.title || !newPost.content || !newPost.author) {
      alert('Please fill in all fields');
      return;
    }
    
    const post = {
      id: Date.now(),
      title: newPost.title,
      body: newPost.content,
      author: newPost.author,
      likes: 0,
      liked: false,
      comments: [],
      createdAt: new Date().toISOString()
    };
    
    setPosts([post, ...posts]);
    setNewPost({ title: '', content: '', author: '' });
    setShowCreateForm(false);
  };
  
  // Format date
  const formatDate = (dateString) => {
    const date = new Date(dateString);
    return date.toLocaleDateString() + ' ' + date.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
  };
  
  if (loading) {
    return (
      <div className="min-h-screen flex items-center justify-center">
        <div className="text-center">
          <div className="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-blue-500"></div>
          <p className="mt-4 text-gray-600">Loading blog posts...</p>
        </div>
      </div>
    );
  }
  
  return (
    <div className="min-h-screen bg-gray-100">
      <div className="max-w-4xl mx-auto p-4">
        {/* Header */}
        <div className="bg-white rounded-lg shadow p-6 mb-6">
          <div className="flex justify-between items-center">
            <div>
              <h1 className="text-3xl font-bold text-gray-800">📝 Blog Posts</h1>
              <p className="text-gray-600 mt-1">Share your thoughts with the world</p>
            </div>
            <button
              onClick={() => setShowCreateForm(true)}
              className="bg-blue-500 text-white px-6 py-2 rounded-lg flex items-center gap-2 hover:bg-blue-600 transition"
            >
              <FaPlus /> New Post
            </button>
          </div>
        </div>
        
        {/* Posts List */}
        <div className="space-y-6">
          {posts.map(post => (
            <div key={post.id} className="bg-white rounded-lg shadow overflow-hidden">
              <div className="p-6">
                {/* Post Header */}
                <div className="flex justify-between items-start mb-4">
                  <div>
                    <h2 className="text-2xl font-bold text-gray-800 mb-2">{post.title}</h2>
                    <div className="flex items-center gap-4 text-sm text-gray-500">
                      <div className="flex items-center gap-1">
                        <FaUser className="text-sm" />
                        {post.author}
                      </div>
                      <div className="flex items-center gap-1">
                        <FaCalendar className="text-sm" />
                        {formatDate(post.createdAt)}
                      </div>
                    </div>
                  </div>
                </div>
                
                {/* Post Content */}
                <p className="text-gray-700 mb-4 leading-relaxed">{post.body}</p>
                
                {/* Post Actions */}
                <div className="flex items-center gap-6 pt-4 border-t">
                  <button
                    onClick={() => likePost(post.id)}
                    className="flex items-center gap-2 text-gray-500 hover:text-red-500 transition"
                  >
                    {post.liked ? <FaHeart className="text-red-500" /> : <FaRegHeart />}
                    <span>{post.likes} likes</span>
                  </button>
                  
                  <button
                    onClick={() => setSelectedPost(selectedPost?.id === post.id ? null : post)}
                    className="flex items-center gap-2 text-gray-500 hover:text-blue-500 transition"
                  >
                    <FaComment />
                    <span>{post.comments.length} comments</span>
                  </button>
                  
                  <button className="flex items-center gap-2 text-gray-500 hover:text-green-500 transition">
                    <FaShare />
                    <span>Share</span>
                  </button>
                </div>
                
                {/* Comments Section */}
                {selectedPost?.id === post.id && (
                  <div className="mt-6 pt-4 border-t">
                    <h3 className="font-semibold mb-3">Comments ({post.comments.length})</h3>
                    
                    {/* Add Comment */}
                    <div className="flex gap-2 mb-4">
                      <input
                        type="text"
                        value={commentText}
                        onChange={(e) => setCommentText(e.target.value)}
                        className="flex-1 border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                        placeholder="Write a comment..."
                      />
                      <button
                        onClick={() => addComment(post.id)}
                        className="bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition"
                      >
                        Post
                      </button>
                    </div>
                    
                    {/* Comments List */}
                    <div className="space-y-3">
                      {post.comments.map(comment => (
                        <div key={comment.id} className="bg-gray-50 rounded-lg p-3">
                          <div className="flex justify-between items-start mb-1">
                            <span className="font-semibold text-sm">{comment.author}</span>
                            <span className="text-xs text-gray-500">{formatDate(comment.date)}</span>
                          </div>
                          <p className="text-gray-700 text-sm">{comment.text}</p>
                        </div>
                      ))}
                    </div>
                  </div>
                )}
              </div>
            </div>
          ))}
        </div>
        
        {/* Create Post Modal */}
        {showCreateForm && (
          <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50">
            <div className="bg-white rounded-lg max-w-2xl w-full">
              <div className="p-6">
                <div className="flex justify-between items-center mb-4">
                  <h2 className="text-2xl font-bold">Create New Post</h2>
                  <button
                    onClick={() => setShowCreateForm(false)}
                    className="text-gray-500 hover:text-gray-700"
                  >
                    <FaTimes />
                  </button>
                </div>
                
                <div className="space-y-4">
                  <div>
                    <label className="block text-gray-700 mb-2">Author Name *</label>
                    <input
                      type="text"
                      value={newPost.author}
                      onChange={(e) => setNewPost({ ...newPost, author: e.target.value })}
                      className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                      placeholder="Your name..."
                    />
                  </div>
                  
                  <div>
                    <label className="block text-gray-700 mb-2">Title *</label>
                    <input
                      type="text"
                      value={newPost.title}
                      onChange={(e) => setNewPost({ ...newPost, title: e.target.value })}
                      className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                      placeholder="Post title..."
                    />
                  </div>
                  
                  <div>
                    <label className="block text-gray-700 mb-2">Content *</label>
                    <textarea
                      value={newPost.content}
                      onChange={(e) => setNewPost({ ...newPost, content: e.target.value })}
                      rows="6"
                      className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                      placeholder="Write your post content here..."
                    />
                  </div>
                  
                  <div className="flex gap-2">
                    <button
                      onClick={createPost}
                      className="flex-1 bg-blue-500 text-white py-2 rounded-lg hover:bg-blue-600 transition"
                    >
                      Publish Post
                    </button>
                    <button
                      onClick={() => setShowCreateForm(false)}
                      className="flex-1 bg-gray-500 text-white py-2 rounded-lg hover:bg-gray-600 transition"
                    >
                      Cancel
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}

export default BlogApp;
Project 10: Complete Portfolio Website
jsx
// Complete Portfolio Website
import { useState } from 'react';
import { FaGithub, FaLinkedin, FaTwitter, FaEnvelope, FaPhone, FaMapMarker, FaBriefcase, FaGraduationCap, FaCode, FaReact, FaNodeJs, FaDatabase, FaHtml5, FaCss3, FaJs } from 'react-icons/fa';

function PortfolioWebsite() {
  const [activeSection, setActiveSection] = useState('home');
  const [showContact, setShowContact] = useState(false);
  
  // Portfolio data
  const portfolio = {
    name: 'John Developer',
    title: 'Full Stack Developer',
    bio: 'Passionate developer with 5+ years of experience building web applications. Love creating beautiful and functional websites that solve real-world problems.',
    email: 'john@example.com',
    phone: '+1 234 567 890',
    location: 'San Francisco, CA',
    social: {
      github: 'https://github.com/johndeveloper',
      linkedin: 'https://linkedin.com/in/johndeveloper',
      twitter: 'https://twitter.com/johndeveloper'
    },
    skills: [
      { name: 'React', icon: FaReact, level: 90, color: 'blue' },
      { name: 'Node.js', icon: FaNodeJs, level: 85, color: 'green' },
      { name: 'JavaScript', icon: FaJs, level: 95, color: 'yellow' },
      { name: 'HTML5', icon: FaHtml5, level: 95, color: 'orange' },
      { name: 'CSS3', icon: FaCss3, level: 90, color: 'blue' },
      { name: 'MongoDB', icon: FaDatabase, level: 80, color: 'green' }
    ],
    experience: [
      {
        company: 'Tech Corp',
        position: 'Senior Full Stack Developer',
        period: '2021 - Present',
        description: 'Leading development of enterprise web applications, mentoring junior developers, and implementing best practices.'
      },
      {
        company: 'Web Solutions Inc',
        position: 'Frontend Developer',
        period: '2019 - 2021',
        description: 'Developed responsive web applications using React, collaborated with design team, and optimized performance.'
      }
    ],
    education: [
      {
        school: 'University of Technology',
        degree: 'Bachelor of Science in Computer Science',
        period: '2015 - 2019',
        description: 'Graduated with honors, focus on web development and software engineering.'
      }
    ],
    projects: [
      {
        title: 'E-commerce Platform',
        description: 'Full-stack e-commerce application with React, Node.js, and MongoDB',
        tech: ['React', 'Node.js', 'MongoDB', 'Tailwind'],
        image: 'https://via.placeholder.com/300x200',
        link: '#'
      },
      {
        title: 'Task Management App',
        description: 'Productivity app for managing tasks and projects',
        tech: ['React', 'Firebase', 'Material-UI'],
        image: 'https://via.placeholder.com/300x200',
        link: '#'
      },
      {
        title: 'Weather Dashboard',
        description: 'Real-time weather application with API integration',
        tech: ['React', 'OpenWeather API', 'Chart.js'],
        image: 'https://via.placeholder.com/300x200',
        link: '#'
      }
    ]
  };
  
  // Scroll to section
  const scrollToSection = (sectionId) => {
    const element = document.getElementById(sectionId);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
      setActiveSection(sectionId);
    }
  };
  
  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-50 to-gray-100">
      {/* Navigation */}
      <nav className="sticky top-0 bg-white shadow-md z-50">
        <div className="max-w-6xl mx-auto px-4">
          <div className="flex justify-between items-center py-4">
            <h1 className="text-2xl font-bold text-blue-600">{portfolio.name}</h1>
            <div className="hidden md:flex space-x-6">
              {['home', 'about', 'skills', 'experience', 'projects', 'contact'].map(section => (
                <button
                  key={section}
                  onClick={() => scrollToSection(section)}
                  className={`capitalize hover:text-blue-600 transition ${
                    activeSection === section ? 'text-blue-600 font-semibold' : 'text-gray-600'
                  }`}
                >
                  {section}
                </button>
              ))}
            </div>
          </div>
        </div>
      </nav>
      
      {/* Hero Section */}
      <section id="home" className="min-h-screen flex items-center justify-center bg-gradient-to-r from-blue-600 to-purple-600 text-white">
        <div className="text-center px-4">
          <h1 className="text-5xl md:text-6xl font-bold mb-4">Hello, I'm {portfolio.name}</h1>
          <p className="text-xl md:text-2xl mb-6">{portfolio.title}</p>
          <p className="text-lg max-w-2xl mx-auto mb-8">{portfolio.bio}</p>
          <button
            onClick={() => scrollToSection('contact')}
            className="bg-white text-blue-600 px-8 py-3 rounded-full font-semibold hover:bg-gray-100 transition transform hover:scale-105"
          >
            Get In Touch
          </button>
        </div>
      </section>
      
      {/* About Section */}
      <section id="about" className="py-20 bg-white">
        <div className="max-w-6xl mx-auto px-4">
          <h2 className="text-3xl font-bold text-center mb-12">About Me</h2>
          <div className="grid md:grid-cols-2 gap-12">
            <div>
              <p className="text-gray-700 leading-relaxed mb-4">
                {portfolio.bio}
              </p>
              <p className="text-gray-700 leading-relaxed">
                I'm passionate about creating elegant solutions to complex problems and continuously learning new technologies.
                When I'm not coding, you can find me reading tech blogs, contributing to open source, or mentoring aspiring developers.
              </p>
            </div>
            <div className="space-y-3">
              <div className="flex items-center gap-3">
                <FaEnvelope className="text-blue-600" />
                <span>{portfolio.email}</span>
              </div>
              <div className="flex items-center gap-3">
                <FaPhone className="text-blue-600" />
                <span>{portfolio.phone}</span>
              </div>
              <div className="flex items-center gap-3">
                <FaMapMarker className="text-blue-600" />
                <span>{portfolio.location}</span>
              </div>
              <div className="flex gap-4 mt-4">
                <a href={portfolio.social.github} target="_blank" rel="noopener noreferrer" className="text-gray-600 hover:text-gray-900">
                  <FaGithub size={24} />
                </a>
                <a href={portfolio.social.linkedin} target="_blank" rel="noopener noreferrer" className="text-gray-600 hover:text-gray-900">
                  <FaLinkedin size={24} />
                </a>
                <a href={portfolio.social.twitter} target="_blank" rel="noopener noreferrer" className="text-gray-600 hover:text-gray-900">
                  <FaTwitter size={24} />
                </a>
              </div>
            </div>
          </div>
        </div>
      </section>
      
      {/* Skills Section */}
      <section id="skills" className="py-20 bg-gray-50">
        <div className="max-w-6xl mx-auto px-4">
          <h2 className="text-3xl font-bold text-center mb-12">Technical Skills</h2>
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            {portfolio.skills.map(skill => {
              const Icon = skill.icon;
              return (
                <div key={skill.name} className="bg-white rounded-lg shadow-md p-6">
                  <div className="flex items-center gap-3 mb-4">
                    <Icon className={`text-${skill.color}-500 text-2xl`} />
                    <h3 className="font-semibold text-lg">{skill.name}</h3>
                  </div>
                  <div className="w-full bg-gray-200 rounded-full h-2">
                    <div
                      className={`bg-${skill.color}-500 h-2 rounded-full`}
                      style={{ width: `${skill.level}%` }}
                    />
                  </div>
                  <p className="text-right text-sm text-gray-600 mt-1">{skill.level}%</p>
                </div>
              );
            })}
          </div>
        </div>
      </section>
      
      {/* Experience & Education */}
      <section id="experience" className="py-20 bg-white">
        <div className="max-w-6xl mx-auto px-4">
          <h2 className="text-3xl font-bold text-center mb-12">Experience & Education</h2>
          <div className="grid md:grid-cols-2 gap-12">
            {/* Experience */}
            <div>
              <h3 className="text-2xl font-bold mb-6 flex items-center gap-2">
                <FaBriefcase /> Work Experience
              </h3>
              <div className="space-y-6">
                {portfolio.experience.map((exp, index) => (
                  <div key={index} className="border-l-4 border-blue-600 pl-4">
                    <h4 className="font-bold text-lg">{exp.position}</h4>
                    <p className="text-gray-600">{exp.company}</p>
                    <p className="text-sm text-gray-500 mb-2">{exp.period}</p>
                    <p className="text-gray-700">{exp.description}</p>
                  </div>
                ))}
              </div>
            </div>
            
            {/* Education */}
            <div>
              <h3 className="text-2xl font-bold mb-6 flex items-center gap-2">
                <FaGraduationCap /> Education
              </h3>
              <div className="space-y-6">
                {portfolio.education.map((edu, index) => (
                  <div key={index} className="border-l-4 border-green-600 pl-4">
                    <h4 className="font-bold text-lg">{edu.degree}</h4>
                    <p className="text-gray-600">{edu.school}</p>
                    <p className="text-sm text-gray-500 mb-2">{edu.period}</p>
                    <p className="text-gray-700">{edu.description}</p>
                  </div>
                ))}
              </div>
            </div>
          </div>
        </div>
      </section>
      
      {/* Projects Section */}
      <section id="projects" className="py-20 bg-gray-50">
        <div className="max-w-6xl mx-auto px-4">
          <h2 className="text-3xl font-bold text-center mb-12">Featured Projects</h2>
          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            {portfolio.projects.map((project, index) => (
              <div key={index} className="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-xl transition">
                <img src={project.image} alt={project.title} className="w-full h-48 object-cover" />
                <div className="p-6">
                  <h3 className="font-bold text-xl mb-2">{project.title}</h3>
                  <p className="text-gray-600 mb-4">{project.description}</p>
                  <div className="flex flex-wrap gap-2 mb-4">
                    {project.tech.map(tech => (
                      <span key={tech} className="px-2 py-1 bg-gray-100 text-gray-600 text-xs rounded">
                        {tech}
                      </span>
                    ))}
                  </div>
                  <a
                    href={project.link}
                    className="inline-block text-blue-600 hover:text-blue-700 font-semibold"
                  >
                    View Project →
                  </a>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>
      
      {/* Contact Section */}
      <section id="contact" className="py-20 bg-gradient-to-r from-blue-600 to-purple-600 text-white">
        <div className="max-w-4xl mx-auto px-4 text-center">
          <h2 className="text-3xl font-bold mb-6">Get In Touch</h2>
          <p className="text-xl mb-8">Have a project in mind? Let's work together!</p>
          <div className="flex flex-wrap justify-center gap-4 mb-8">
            <a
              href={`mailto:${portfolio.email}`}
              className="bg-white text-blue-600 px-6 py-3 rounded-full flex items-center gap-2 hover:bg-gray-100 transition"
            >
              <FaEnvelope /> Email Me
            </a>
            <a
              href={portfolio.social.github}
              target="_blank"
              rel="noopener noreferrer"
              className="bg-gray-800 text-white px-6 py-3 rounded-full flex items-center gap-2 hover:bg-gray-900 transition"
            >
              <FaGithub /> GitHub
            </a>
            <a
              href={portfolio.social.linkedin}
              target="_blank"
              rel="noopener noreferrer"
              className="bg-blue-800 text-white px-6 py-3 rounded-full flex items-center gap-2 hover:bg-blue-900 transition"
            >
              <FaLinkedin /> LinkedIn
            </a>
          </div>
          
          {/* Contact Form */}
          <div className="bg-white text-gray-800 rounded-lg p-6 mt-8">
            <h3 className="text-2xl font-bold mb-4">Send a Message</h3>
            <form className="space-y-4">
              <div className="grid md:grid-cols-2 gap-4">
                <input
                  type="text"
                  placeholder="Your Name"
                  className="border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
                <input
                  type="email"
                  placeholder="Your Email"
                  className="border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>
              <input
                type="text"
                placeholder="Subject"
                className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
              />
              <textarea
                placeholder="Your Message"
                rows="5"
                className="w-full border border-gray-300 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
              />
              <button
                type="submit"
                className="w-full bg-blue-600 text-white py-2 rounded-lg hover:bg-blue-700 transition"
              >
                Send Message
              </button>
            </form>
          </div>
        </div>
      </section>
      
      {/* Footer */}
      <footer className="bg-gray-900 text-white py-6 text-center">
        <p>© 2024 {portfolio.name}. All rights reserved.</p>
        <p className="text-sm text-gray-400 mt-2">Built with React & Tailwind CSS</p>
      </footer>
    </div>
  );
}

export default PortfolioWebsite;
18. Common Mistakes and How to Fix Them
Mistake 1: Directly Modifying State
jsx
// ❌ WRONG
function WrongUpdate() {
  const [user, setUser] = useState({ name: 'John', age: 25 });
  
  const updateAge = () => {
    user.age = 26; // Direct mutation
    setUser(user); // Won't trigger re-render
  };
  
  return <button onClick={updateAge}>Update Age</button>;
}

// ✅ CORRECT
function CorrectUpdate() {
  const [user, setUser] = useState({ name: 'John', age: 25 });
  
  const updateAge = () => {
    setUser({ ...user, age: 26 }); // Create new object
  };
  
  return <button onClick={updateAge}>Update Age</button>;
}
Mistake 2: Not Using Keys in Lists
jsx
// ❌ WRONG
function WrongList() {
  const items = ['Apple', 'Banana', 'Orange'];
  
  return (
    <ul>
      {items.map(item => (
        <li>{item}</li> // No key
      ))}
    </ul>
  );
}

// ✅ CORRECT
function CorrectList() {
  const items = ['Apple', 'Banana', 'Orange'];
  
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{item}</li> // Use key
      ))}
    </ul>
  );
}

// ✅ EVEN BETTER
function BetterList() {
  const items = [
    { id: 1, name: 'Apple' },
    { id: 2, name: 'Banana' },
    { id: 3, name: 'Orange' }
  ];
  
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>{item.name}</li> // Use unique ID
      ))}
    </ul>
  );
}
Mistake 3: Forgetting to Prevent Default in Forms
jsx
// ❌ WRONG
function WrongForm() {
  const handleSubmit = () => {
    console.log('Form submitted');
    // Page will refresh!
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}

// ✅ CORRECT
function CorrectForm() {
  const handleSubmit = (e) => {
    e.preventDefault(); // Prevent page refresh
    console.log('Form submitted');
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
Mistake 4: Using State in useEffect Without Dependencies
jsx
// ❌ WRONG
function WrongEffect() {
  const [count, setCount] = useState(0);
  
  useEffect(() => {
    // This will run infinitely!
    setCount(count + 1);
  }); // No dependencies
  
  return <div>{count}</div>;
}

// ✅ CORRECT
function CorrectEffect() {
  const [count, setCount] = useState(0);
  
  useEffect(() => {
    // Runs only when count changes
    document.title = `Count: ${count}`;
  }, [count]); // Add dependency
  
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
Mistake 5: Not Handling Loading and Error States
jsx
// ❌ WRONG
function WrongFetch() {
  const [data, setData] = useState(null);
  
  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(data => setData(data));
  }, []);
  
  return <div>{data.name}</div>; // Crashes if data is null!
}

// ✅ CORRECT
function CorrectFetch() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(data => {
        setData(data);
        setLoading(false);
      })
      .catch(err => {
        setError(err.message);
        setLoading(false);
      });
  }, []);
  
  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  return <div>{data.name}</div>;
}
Mistake 6: Forgetting to Cleanup Effects
jsx
// ❌ WRONG
function WrongTimer() {
  const [seconds, setSeconds] = useState(0);
  
  useEffect(() => {
    // Creates new interval every time component re-renders!
    setInterval(() => {
      setSeconds(s => s + 1);
    }, 1000);
  }, []);
  
  return <div>{seconds} seconds</div>;
}

// ✅ CORRECT
function CorrectTimer() {
  const [seconds, setSeconds] = useState(0);
  
  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(s => s + 1);
    }, 1000);
    
    return () => clearInterval(interval); // Cleanup
  }, []);
  
  return <div>{seconds} seconds</div>;
}
Mistake 7: Using Index as Key in Dynamic Lists
jsx
// ❌ WRONG
function WrongDynamicList() {
  const [items, setItems] = useState(['A', 'B', 'C']);
  
  const removeItem = (index) => {
    setItems(items.filter((_, i) => i !== index));
  };
  
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>  {/* Index as key - will cause bugs */}
          {item}
          <button onClick={() => removeItem(index)}>Delete</button>
        </li>
      ))}
    </ul>
  );
}

// ✅ CORRECT
function CorrectDynamicList() {
  const [items, setItems] = useState([
    { id: 1, text: 'A' },
    { id: 2, text: 'B' },
    { id: 3, text: 'C' }
  ]);
  
  const removeItem = (id) => {
    setItems(items.filter(item => item.id !== id));
  };
  
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>  {/* Unique ID as key */}
          {item.text}
          <button onClick={() => removeItem(item.id)}>Delete</button>
        </li>
      ))}
    </ul>
  );
}
Mistake 8: Calling Hooks Conditionally
jsx
// ❌ WRONG
function WrongHooks() {
  const [count, setCount] = useState(0);
  
  if (count > 5) {
    // Can't call hook conditionally!
    useEffect(() => {
      console.log('Count is high');
    }, [count]);
  }
  
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}

// ✅ CORRECT
function CorrectHooks() {
  const [count, setCount] = useState(0);
  
  useEffect(() => {
    if (count > 5) {
      console.log('Count is high');
    }
  }, [count]); // Condition inside the hook
  
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
Mistake 9: Not Using Functional Updates When Needed
jsx
// ❌ WRONG
function WrongCounter() {
  const [count, setCount] = useState(0);
  
  const incrementThree = () => {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
    // Only increments by 1!
  };
  
  return (
    <div>
      <p>{count}</p>
      <button onClick={incrementThree}>+3</button>
    </div>
  );
}

// ✅ CORRECT
function CorrectCounter() {
  const [count, setCount] = useState(0);
  
  const incrementThree = () => {
    setCount(prev => prev + 1);
    setCount(prev => prev + 1);
    setCount(prev => prev + 1);
    // Increments by 3!
  };
  
  return (
    <div>
      <p>{count}</p>
      <button onClick={incrementThree}>+3</button>
    </div>
  );
}
Mistake 10: Forgetting to Handle Promise Rejections
jsx
// ❌ WRONG
function WrongPromise() {
  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(data => setData(data));
    // No .catch() for errors!
  }, []);
}

// ✅ CORRECT
function CorrectPromise() {
  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(data => setData(data))
      .catch(err => setError(err.message));
    // Handles errors
  }, []);
}

// ✅ EVEN BETTER with async/await
function BetterPromise() {
  useEffect(() => {
    const fetchData = async () => {
      try {
        const res = await fetch('https://api.example.com/data');
        const data = await res.json();
        setData(data);
      } catch (err) {
        setError(err.message);
      }
    };
    
    fetchData();
  }, []);
}
19. Best Practices for Clean Code
1. Component Structure
jsx
// Good component structure
import { useState, useEffect } from 'react';
import PropTypes from 'prop-types';
import './Component.css';

// 1. Imports
// 2. Constants
// 3. Helper functions
// 4. Component
// 5. PropTypes
// 6. Export

const MAX_ITEMS = 10;

const formatDate = (date) => {
  return new Date(date).toLocaleDateString();
};

function UserCard({ user, onEdit, onDelete }) {
  const [isEditing, setIsEditing] = useState(false);
  
  useEffect(() => {
    // Effect logic
  }, []);
  
  const handleEdit = () => {
    setIsEditing(true);
    onEdit(user);
  };
  
  return (
    <div className="user-card">
      <h3>{user.name}</h3>
      <p>{user.email}</p>
      <button onClick={handleEdit}>Edit</button>
      <button onClick={() => onDelete(user.id)}>Delete</button>
    </div>
  );
}

UserCard.propTypes = {
  user: PropTypes.shape({
    id: PropTypes.number.isRequired,
    name: PropTypes.string.isRequired,
    email: PropTypes.string.isRequired
  }).isRequired,
  onEdit: PropTypes.func.isRequired,
  onDelete: PropTypes.func.isRequired
};

export default UserCard;
2. Naming Conventions
jsx
// ✅ GOOD NAMES
// Components - PascalCase
function UserProfile() {}
function TodoList() {}
function NavigationBar() {}

// Variables and functions - camelCase
const userName = 'John';
const fetchUserData = () => {};
const handleButtonClick = () => {};

// Constants - UPPER_CASE
const API_URL = 'https://api.example.com';
const MAX_RETRY_COUNT = 3;

// Booleans - is/has/should prefix
const isLoading = true;
const hasError = false;
const shouldRender = true;

// Event handlers - handle prefix
const handleClick = () => {};
const handleSubmit = () => {};
const handleInputChange = () => {};

// ❌ BAD NAMES
const User = () => {}; // Too generic
const a = 'John'; // Meaningless
const func = () => {}; // Not descriptive
const data = fetchData(); // Too vague
3. Organizing State
jsx
// ✅ GOOD - Group related state
const [user, setUser] = useState({
  name: '',
  email: '',
  age: 0
});

// Instead of:
const [name, setName] = useState('');
const [email, setEmail] = useState('');
const [age, setAge] = useState(0);

// ✅ GOOD - Separate unrelated state
const [user, setUser] = useState({});
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState(null);

// Instead of:
const [state, setState] = useState({
  user: {},
  isLoading: false,
  error: null
}); // Harder to update
4. Conditional Rendering
jsx
// ✅ GOOD - Extract complex conditions
const renderContent = () => {
  if (isLoading) return <Spinner />;
  if (error) return <ErrorMessage error={error} />;
  if (!data) return <EmptyState />;
  return <DataDisplay data={data} />;
};

return <div>{renderContent()}</div>;

// Instead of:
return (
  <div>
    {isLoading && <Spinner />}
    {error && <ErrorMessage error={error} />}
    {!isLoading && !error && !data && <EmptyState />}
    {!isLoading && !error && data && <DataDisplay data={data} />}
  </div>
);
5. Destructuring Props
jsx
// ✅ GOOD - Destructure in parameters
function UserCard({ user, onEdit, onDelete, className }) {
  return <div className={className}>...</div>;
}

// Instead of:
function UserCard(props) {
  return <div className={props.className}>...</div>;
}

// ✅ GOOD - Destructure objects
const { name, email, age } = user;
6. File Organization
text
src/
├── components/           # Reusable components
│   ├── common/          # Very generic components
│   │   ├── Button.jsx
│   │   ├── Input.jsx
│   │   └── Card.jsx
│   └── features/        # Feature-specific components
│       ├── UserCard.jsx
│       └── TodoItem.jsx
├── pages/               # Page components
│   ├── Home.jsx
│   ├── About.jsx
│   └── Contact.jsx
├── hooks/               # Custom hooks
│   ├── useFetch.js
│   └── useLocalStorage.js
├── utils/               # Helper functions
│   ├── api.js
│   └── formatters.js
├── constants/           # Constants
│   └── config.js
├── styles/              # Global styles
│   └── global.css
├── App.jsx
└── main.jsx
7. Performance Tips
jsx
// 1. Use React.memo for expensive components
const ExpensiveComponent = React.memo(({ data }) => {
  // Component logic
});

// 2. Use useCallback for functions passed to child components
const handleClick = useCallback(() => {
  // Function logic
}, [dependency]);

// 3. Use useMemo for expensive calculations
const expensiveValue = useMemo(() => {
  return computeExpensiveValue(data);
}, [data]);

// 4. Lazy load components
const LazyComponent = React.lazy(() => import('./HeavyComponent'));

// 5. Avoid inline functions in JSX
// ❌ BAD
<button onClick={() => handleClick(id)}>Click</button>

// ✅ GOOD
const handleButtonClick = () => handleClick(id);
<button onClick={handleButtonClick}>Click</button>
20. Next Steps in Your React Journey
What You've Learned
✅ JSX syntax and how it works
✅ Creating and using components
✅ Passing data with props
✅ Managing state with useState
✅ Handling events
✅ Rendering lists with keys
✅ Conditional rendering
✅ Working with forms
✅ Side effects with useEffect
✅ Fetching data from APIs
✅ Saving data with localStorage
✅ Navigation with React Router
✅ Using React Icons
✅ Building 10 complete projects

What to Learn Next
1. Advanced React Concepts
useReducer for complex state management

useRef for DOM access

useLayoutEffect for synchronous effects

Forwarding refs with forwardRef

Higher-Order Components (HOCs)

Render props pattern

Error Boundaries

2. State Management Libraries
Redux Toolkit

Zustand

Jotai

Recoil

3. Testing React Apps
Jest for unit testing

React Testing Library

Cypress for end-to-end testing

4. Type Safety with TypeScript
Adding TypeScript to React

Type checking props and state

Creating typed custom hooks

5. Build Production Apps
Next.js (React framework)

Gatsby (static site generator)

Remix (full-stack framework)

6. Mobile Development
React Native for iOS and Android

Expo for easier React Native development

7. Backend Integration
GraphQL with Apollo Client

Firebase for backend services

Supabase for open-source backend

Practice Projects Ideas
E-commerce Store - Full cart, checkout, product filtering

Social Media Dashboard - Feed, posts, comments, likes

Chat Application - Real-time messaging with WebSockets

Project Management Tool - Kanban board, task assignments

Video Streaming Platform - Video player, playlists, comments

Fitness Tracker - Workout logging, progress charts

Job Board - Job listings, applications, filters

Learning Management System - Courses, lessons, quizzes

Resources
Documentation:

React Official Docs

React Router Docs

Tailwind CSS Docs

Practice Platforms:

Frontend Mentor

LeetCode

CodeSandbox

Community:

React Discord

Reddit r/reactjs

Stack Overflow

Final Tips
Build, Build, Build - The best way to learn is by building projects

Read Code - Look at open-source React projects on GitHub

Stay Updated - React releases new features regularly

Join Community - Learn from other developers

Share Your Work - Put projects on GitHub and portfolio

Keep Learning - Technology changes, stay curious!

Congratulations! 🎉
You've completed the React Complete Course! You now have the knowledge and skills to build modern web applications with React. Remember:

Start with small projects and gradually increase complexity

Don't be afraid to make mistakes - that's how you learn

The React community is friendly and helpful

Your journey as a developer is just beginning

Happy Coding! 🚀
