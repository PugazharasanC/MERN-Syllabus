# JavaScript Introduction - MERN Stack Development Course

## Session Overview (3 Hours)

This session introduces the foundational concepts of full-stack web development with a focus on the MERN stack (MongoDB, Express, React, Node.js). By the end of this session, participants should understand the basic architecture of web applications, the roles of frontend and backend components, and have seen a simple demonstration of a full-stack application.

## 1. What is Full Stack Web Development? (20 minutes)

### Definition

Full stack web development refers to the practice of developing both client-side (frontend) and server-side (backend) software. A full stack web developer has the ability to work on all layers of an application, from the user interface to the database.

### The Stack Concept

- **Stack** = The collection of technologies used to create a web application
- Popular stacks include:
  - MERN: MongoDB, Express, React, Node.js
  - MEAN: MongoDB, Express, Angular, Node.js
  - LAMP: Linux, Apache, MySQL, PHP
  - JAMstack: JavaScript, APIs, Markup

### Why MERN Stack?

- JavaScript throughout the entire stack
- JSON data format used consistently
- Large community support
- High performance and scalability
- Modern and in-demand in the industry

### Full Stack Developer Responsibilities

- Understand user requirements
- Design user interactions on the frontend
- Develop server-side logic
- Design and interact with databases
- Ensure cross-platform compatibility
- Implement security and data protection
- Test and debug across the entire stack

## 2. Frontend Development (25 minutes)

### What is Frontend?

The frontend (client-side) is everything the user sees and interacts with in the browser.

### Key Components

- **HTML**: Structure and content
- **CSS**: Styling and layout
- **JavaScript**: Interactivity and behavior

### Frontend Frameworks and Libraries

- **React**: Component-based UI library (what we'll focus on)
- **Angular**: Full-featured framework by Google
- **Vue**: Progressive JavaScript framework
- **Svelte**: Compiler-based approach to UI building

### The DOM (Document Object Model)

- Represents HTML as a tree structure
- Allows JavaScript to access and modify webpage elements
- Serves as the bridge between HTML and JavaScript

### Example: Simple DOM Manipulation

```javascript
// Selecting an element
const heading = document.getElementById('main-heading');

// Modifying content
heading.textContent = 'Welcome to MERN Stack Development!';

// Adding event listeners
const button = document.querySelector('button');
button.addEventListener('click', () => {
  alert('Button clicked!');
});
```

### React Key Concepts Preview

- Components and component hierarchy
- Virtual DOM for efficient updates
- JSX for templating
- Props and state management
- Hooks for functional components

## 3. Backend Development (25 minutes)

### What is Backend?

The backend (server-side) handles business logic, database operations, authentication, and serves data to the frontend.

### Key Responsibilities

- Process data from the client
- Interact with databases
- Authenticate and authorize users
- Business logic implementation
- API creation and management

### Backend Technologies

- **Node.js**: JavaScript runtime for server-side applications
- **Express.js**: Web application framework for Node.js
- **MongoDB**: NoSQL database
- **REST APIs**: Architectural style for designing networked applications
- **GraphQL**: Query language for APIs (alternative to REST)

### MVC Architecture

- **Model**: Data and business logic
- **View**: User interface
- **Controller**: Request handling and response

### Example: Simple Express Server

```javascript
const express = require('express');
const app = express();
const PORT = 3000;

// Middleware to parse JSON bodies
app.use(express.json());

// A simple route
app.get('/api/hello', (req, res) => {
  res.json({ message: 'Hello, MERN developers!' });
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

## 4. Databases (25 minutes)

### Types of Databases

- **Relational Databases** (SQL)
  - PostgreSQL, MySQL, Oracle, SQL Server
  - Structured data with tables, rows, columns
  - ACID compliance (Atomicity, Consistency, Isolation, Durability)

- **NoSQL Databases**
  - Document stores: MongoDB, CouchDB
  - Key-value stores: Redis, DynamoDB
  - Column stores: Cassandra, HBase
  - Graph databases: Neo4j, ArangoDB

### MongoDB Basics

- Document-oriented NoSQL database
- Stores data in flexible, JSON-like BSON documents
- Designed for scalability and developer agility
- Schema-less design allows for flexible data models

### MongoDB Document Example

```javascript
// A MongoDB document representing a user
{
  "_id": ObjectId("60d5ec7a1c9d440000000000"),
  "username": "merndev",
  "email": "dev@example.com",
  "skills": ["JavaScript", "React", "Node.js"],
  "projects": [
    {
      "name": "E-commerce site",
      "technologies": ["MERN", "Redux", "Stripe"]
    }
  ],
  "joined": ISODate("2023-01-15T08:00:00Z")
}
```

### Database Operations (CRUD)

- **Create**: Insert new documents
- **Read**: Query and retrieve documents
- **Update**: Modify existing documents
- **Delete**: Remove documents

### MongoDB with Node.js (Preview)

```javascript
const { MongoClient } = require('mongodb');

// Connection URL and database name
const url = 'mongodb://localhost:27017';
const dbName = 'mernCourse';

async function main() {
  // Create a new MongoClient
  const client = new MongoClient(url);

  try {
    // Connect to the MongoDB server
    await client.connect();
    console.log('Connected to MongoDB');

    // Access the database
    const db = client.db(dbName);

    // Insert a document
    const result = await db.collection('users').insertOne({
      name: 'John Doe',
      email: 'john@example.com',
      createdAt: new Date()
    });

    console.log(`User inserted with id: ${result.insertedId}`);
  } finally {
    // Close the connection
    await client.close();
  }
}

main().catch(console.error);
```

## 5. Introduction to Web Browsers (15 minutes)

### Browser Components

- **User Interface**: Address bar, back/forward buttons, bookmarks
- **Browser Engine**: Marshals actions between UI and rendering engine
- **Rendering Engine**: Displays requested content (HTML, CSS)
- **Networking**: Handles HTTP requests
- **JavaScript Engine**: Interprets and executes JavaScript code
- **UI Backend**: Used for drawing basic widgets
- **Data Storage**: Cookies, localStorage, IndexedDB, etc.

### How Browsers Work

1. Parse HTML to construct the DOM tree
2. Parse CSS to construct the CSSOM tree
3. Combine DOM and CSSOM to create the render tree
4. Run layout to compute the geometry of each node
5. Paint the individual nodes to the screen

### Browser Developer Tools

- Elements panel: Inspect and modify the DOM and CSS
- Console: View logs and execute JavaScript
- Network: Monitor requests and responses
- Performance: Analyze runtime performance
- Application: Inspect storage, cache, and more

## 6. JavaScript V8 Engine (15 minutes)

### What is V8?

- High-performance JavaScript and WebAssembly engine
- Written in C++ by Google
- Powers Google Chrome and Node.js
- Compiles JavaScript directly to native machine code
- Features optimizations like hidden classes, inline caching

### How V8 Works

1. **Parsing**: JavaScript code is parsed into an Abstract Syntax Tree (AST)
2. **Compilation**: The AST is compiled to bytecode by Ignition (V8's interpreter)
3. **Optimization**: TurboFan (V8's optimizer) identifies hot code paths and optimizes them
4. **Execution**: The optimized machine code is executed
5. **Garbage Collection**: Automatic memory management frees unused memory

### V8 in Node.js vs. Browser

- Same core engine in both environments
- Different APIs and capabilities
- Browser: DOM, window, fetch, etc.
- Node.js: fs, http, process, etc.

## 7. Evolution of HTTP (20 minutes)

### HTTP History

- **HTTP/0.9 (1991)**: Simple one-line protocol for HTML retrieval
- **HTTP/1.0 (1996)**: Added headers, status codes, content types
- **HTTP/1.1 (1997)**: Persistent connections, pipelining, host headers
- **HTTP/2 (2015)**: Multiplexing, server push, header compression
- **HTTP/3 (2022)**: QUIC transport protocol, improved performance

### Key HTTP Concepts

- **Stateless protocol**: Each request/response is independent
- **Client-server model**: Clients request, servers respond
- **Resource-based**: URLs identify resources
- **Text-based**: Messages are human-readable (except HTTP/2+)

### HTTPS (HTTP Secure)

- Encrypts HTTP using TLS/SSL
- Provides data integrity, confidentiality, and authentication
- Increasingly important for all websites

## 8. HTTP Methods (15 minutes)

### Common HTTP Methods

- **GET**: Retrieve a resource
- **POST**: Create a new resource
- **PUT**: Update a resource by replacing it entirely
- **PATCH**: Update a resource partially
- **DELETE**: Remove a resource
- **HEAD**: Same as GET but returns only headers, no body
- **OPTIONS**: Returns supported HTTP methods for a URL

### REST API Best Practices

- Use nouns for resources, not verbs
- Use plural nouns for collections
- Use HTTP methods to indicate actions
- Use nested resources for relationships
- Provide meaningful HTTP status codes

### Example REST API Endpoints

```
GET    /api/users         # Get all users
GET    /api/users/123     # Get a specific user
POST   /api/users         # Create a new user
PUT    /api/users/123     # Update a user completely
PATCH  /api/users/123     # Update a user partially
DELETE /api/users/123     # Delete a user
```

## 9. How the Server Looks at the URL (15 minutes)

### URL Structure

- **Protocol**: http:// or https://
- **Host**: <www.example.com>
- **Port**: :3000 (optional, default is 80 for HTTP, 443 for HTTPS)
- **Path**: /products/123
- **Query parameters**: ?category=electronics&sort=price
- **Fragment**: #reviews (client-side only)

### Server URL Processing

1. Parse the URL to extract components
2. Route the request to the appropriate handler based on the path
3. Extract and validate query parameters
4. Process path parameters (e.g., IDs in `/users/123`)
5. Handle the request based on the HTTP method

### URL Routing in Express

```javascript
const express = require('express');
const app = express();

// Basic route
app.get('/', (req, res) => {
  res.send('Welcome to our API!');
});

// Path parameters
app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});

// Query parameters
app.get('/products', (req, res) => {
  const category = req.query.category;
  const sort = req.query.sort || 'name';

  res.send(`Products in ${category}, sorted by ${sort}`);
});

app.listen(3000);
```

## 10. Request & Response Cycle (25 minutes)

### The Complete Cycle

1. **Client initiates request**: Browser sends HTTP request
2. **DNS resolution**: Domain name converted to IP address
3. **TCP connection**: Client establishes connection with server
4. **TLS handshake**: If HTTPS, encryption is established
5. **Server receives request**: Web server accepts connection
6. **Server processes request**: Application server handles logic
7. **Database interaction**: If needed, data is retrieved/modified
8. **Response preparation**: Server builds HTTP response
9. **Response transmission**: Server sends response to client
10. **Client processing**: Browser processes HTML, CSS, JavaScript
11. **DOM construction**: Browser builds the page
12. **Additional requests**: For images, scripts, styles, etc.
13. **Page rendering**: Final page is displayed to user

### HTTP Request Structure

```zsh
GET /api/products HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

### HTTP Response Structure

```bash
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: max-age=3600
Date: Mon, 20 Jun 2023 12:00:00 GMT

{
  "products": [
    { "id": 1, "name": "Smartphone", "price": 699 },
    { "id": 2, "name": "Laptop", "price": 1299 }
  ],
  "total": 2
}
```

### Status Codes

- **1xx**: Informational
- **2xx**: Success (200 OK, 201 Created, 204 No Content)
- **3xx**: Redirection (301 Moved Permanently, 302 Found)
- **4xx**: Client errors (400 Bad Request, 401 Unauthorized, 404 Not Found)
- **5xx**: Server errors (500 Internal Server Error, 503 Service Unavailable)

## 11. Browser JS vs Node.js (15 minutes)

### Common Features

- Same language syntax (ECMAScript)
- Core JavaScript functionality
- JSON parsing/stringifying
- Promises and async/await
- ES6+ features

### Browser JavaScript

- DOM manipulation
- Window object
- Browser APIs (fetch, localStorage, etc.)
- Browser events (click, submit, etc.)
- Restricted file system access
- Same-origin policy

### Node.js JavaScript

- File system access
- OS-level operations
- Network access without CORS restrictions
- Buffer for binary data
- Streams for data processing
- Global object instead of window
- CommonJS modules (require/module.exports)
- Access to npm ecosystem

### Example: Reading a File

Browser (limited to user-selected files):

```javascript
// Using File API in the browser
const fileInput = document.getElementById('fileInput');
fileInput.addEventListener('change', (event) => {
  const file = event.target.files[0];
  const reader = new FileReader();

  reader.onload = (e) => {
    console.log(e.target.result);
  };

  reader.readAsText(file);
});
```

Node.js:

```javascript
// Using fs module in Node.js
const fs = require('fs');

// Synchronous
try {
  const data = fs.readFileSync('file.txt', 'utf8');
  console.log(data);
} catch (err) {
  console.error(err);
}

// Asynchronous
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});

// With promises
const fsPromises = require('fs').promises;

async function readFile() {
  try {
    const data = await fsPromises.readFile('file.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();
```

## 12. Simple Demo of a Full Stack Application (45 minutes)

### Project Structure

```
fullstack-demo/
├── client/               # Frontend (React)
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   └── src/
│       ├── App.jsx
│       ├── main.jsx
│       └── components/
│           └── TaskList.jsx
│
└── server/               # Backend (Node.js/Express)
    ├── package.json
    ├── index.js
    └── routes/
        └── tasks.js
```

### Backend Setup (Express)

First, create the server directory and initialize the project:

```bash
mkdir -p fullstack-demo/server
cd fullstack-demo/server
npm init -y
npm install express cors mongoose
```

Create the main server file (`index.js`):

```javascript
const express = require('express');
const cors = require('cors');
const mongoose = require('mongoose');

// Initialize Express app
const app = express();
const PORT = process.env.PORT || 5000;

// Middleware
app.use(cors());
app.use(express.json());

// Connect to MongoDB (local instance for demo)
mongoose.connect('mongodb://localhost:27017/taskmanager')
  .then(() => console.log('Connected to MongoDB'))
  .catch(err => console.error('MongoDB connection error:', err));

// Define Task schema
const taskSchema = new mongoose.Schema({
  title: { type: String, required: true },
  completed: { type: Boolean, default: false },
  createdAt: { type: Date, default: Date.now }
});

// Create Task model
const Task = mongoose.model('Task', taskSchema);

// Routes
app.get('/api/tasks', async (req, res) => {
  try {
    const tasks = await Task.find().sort({ createdAt: -1 });
    res.json(tasks);
  } catch (err) {
    res.status(500).json({ message: err.message });
  }
});

app.post('/api/tasks', async (req, res) => {
  try {
    const task = new Task({
      title: req.body.title,
      completed: req.body.completed || false
    });

    const newTask = await task.save();
    res.status(201).json(newTask);
  } catch (err) {
    res.status(400).json({ message: err.message });
  }
});

app.put('/api/tasks/:id', async (req, res) => {
  try {
    const task = await Task.findById(req.params.id);
    if (!task) return res.status(404).json({ message: 'Task not found' });

    if (req.body.title) task.title = req.body.title;
    if (req.body.completed !== undefined) task.completed = req.body.completed;

    const updatedTask = await task.save();
    res.json(updatedTask);
  } catch (err) {
    res.status(400).json({ message: err.message });
  }
});

app.delete('/api/tasks/:id', async (req, res) => {
  try {
    const task = await Task.findById(req.params.id);
    if (!task) return res.status(404).json({ message: 'Task not found' });

    await task.deleteOne();
    res.json({ message: 'Task deleted' });
  } catch (err) {
    res.status(500).json({ message: err.message });
  }
});

// Start server
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

### Frontend Setup (React with Vite)

Create the client directory and initialize the React app with Vite:

```bash
mkdir -p fullstack-demo/client
cd fullstack-demo/client
npm create vite@latest . -- --template react
npm install
```

Update the main `App.jsx`:

```javascript
import React, { useState, useEffect } from 'react';
import './App.css';

function App() {
  const [tasks, setTasks] = useState([]);
  const [newTaskTitle, setNewTaskTitle] = useState('');
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  const API_URL = 'http://localhost:5000/api';

  // Fetch tasks from API
  useEffect(() => {
    const fetchTasks = async () => {
      try {
        const response = await fetch(`${API_URL}/tasks`);
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        setTasks(data);
        setLoading(false);
      } catch (err) {
        setError(err.message);
        setLoading(false);
      }
    };

    fetchTasks();
  }, []);

  // Add a new task
  const handleAddTask = async (e) => {
    e.preventDefault();
    if (!newTaskTitle.trim()) return;

    try {
      const response = await fetch(`${API_URL}/tasks`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({ title: newTaskTitle }),
      });

      if (!response.ok) {
        throw new Error('Failed to add task');
      }

      const newTask = await response.json();
      setTasks([newTask, ...tasks]);
      setNewTaskTitle('');
    } catch (err) {
      setError(err.message);
    }
  };

  // Toggle task completion
  const toggleTaskCompletion = async (taskId) => {
    const taskToUpdate = tasks.find(task => task._id === taskId);
    if (!taskToUpdate) return;

    try {
      const response = await fetch(`${API_URL}/tasks/${taskId}`, {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({ completed: !taskToUpdate.completed }),
      });

      if (!response.ok) {
        throw new Error('Failed to update task');
      }

      const updatedTask = await response.json();
      setTasks(tasks.map(task =>
        task._id === taskId ? updatedTask : task
      ));
    } catch (err) {
      setError(err.message);
    }
  };

  // Delete a task
  const deleteTask = async (taskId) => {
    try {
      const response = await fetch(`${API_URL}/tasks/${taskId}`, {
        method: 'DELETE',
      });

      if (!response.ok) {
        throw new Error('Failed to delete task');
      }

      setTasks(tasks.filter(task => task._id !== taskId));
    } catch (err) {
      setError(err.message);
    }
  };

  if (loading) return <div className="app-container">Loading...</div>;
  if (error) return <div className="app-container">Error: {error}</div>;

  return (
    <div className="app-container">
      <h1>Task Manager</h1>

      <form onSubmit={handleAddTask} className="task-form">
        <input
          type="text"
          value={newTaskTitle}
          onChange={(e) => setNewTaskTitle(e.target.value)}
          placeholder="Add a new task..."
          className="task-input"
        />
        <button type="submit" className="add-button">Add Task</button>
      </form>

      <div className="task-list">
        {tasks.length === 0 ? (
          <p className="no-tasks">No tasks yet. Add one above!</p>
        ) : (
          tasks.map(task => (
            <div key={task._id} className={`task-item ${task.completed ? 'completed' : ''}`}>
              <span
                className="task-title"
                onClick={() => toggleTaskCompletion(task._id)}
              >
                {task.title}
              </span>
              <div className="task-actions">
                <button
                  className="delete-button"
                  onClick={() => deleteTask(task._id)}
                >
                  Delete
                </button>
              </div>
            </div>
          ))
        )}
      </div>
    </div>
  );
}

export default App;
```

Add some basic styling in `App.css`:

```css
.app-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #333;
}

.task-form {
  display: flex;
  margin-bottom: 20px;
}

.task-input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px 0 0 4px;
  font-size: 16px;
}

.add-button {
  padding: 10px 15px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 0 4px 4px 0;
  cursor: pointer;
  font-size: 16px;
}

.task-list {
  border: 1px solid #ddd;
  border-radius: 4px;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  border-bottom: 1px solid #eee;
}

.task-item:last-child {
  border-bottom: none;
}

.task-item.completed .task-title {
  text-decoration: line-through;
  color: #888;
}

.task-title {
  flex: 1;
  cursor: pointer;
}

.task-actions {
  display: flex;
  gap: 10px;
}

.delete-button {
  padding: 5px 10px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.no-tasks {
  padding: 20px;
  text-align: center;
  color: #888;
}
```

### Running the Application

In the server directory:

```bash
node index.js
```

In the client directory:

```bash
npm run dev
```

### Demonstration Flow

1. Show the backend server starting up and connecting to MongoDB
2. Show the frontend application running in the browser
3. Demonstrate adding tasks, toggling their completion status, and deleting them
4. Explain the client-server communication happening behind the scenes
5. Show network requests in the browser's developer tools
6. Highlight how the React frontend and Express backend work together

## Conclusion and Next Steps (15 minutes)

### What We've Learned

- The components of full stack web development
- Frontend vs. backend responsibilities
- The role of databases in web applications
- How browsers interpret and execute JavaScript
- The HTTP protocol and request-response cycle
- Differences between browser and Node.js environments
- Basic implementation of a MERN stack application

### Next Session Preview

- Deep dive into JavaScript fundamentals
- Introduction to ES6+ features
- Advanced Node.js concepts
- Express.js routing and middleware
- MongoDB data modeling
- React component patterns
- State management in React applications

### Resources for Further Learning

- Mozilla Developer Network (MDN)
- The Node.js documentation
- React documentation
- MongoDB University
- Express.js documentation
- GitHub repositories with MERN stack examples

### Projects to Try

- Extend the task manager with user authentication
- Add categories or tags to tasks
- Implement due dates and reminders
- Create a dashboard with task statistics
- Add a search and filter feature

## Q&A (Remaining time)

Open discussion for questions from participants.
