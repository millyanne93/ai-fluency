# Prompt Ladder: Backend API Code Generation

**Voice Card:** Technical, clear, honest, no buzzwords, warm.

---

## Baseline — Weak Prompt

**Prompt:**
"Write backend code for a task management API."

**Why this is weak:**
Too vague — no language, framework, or database specified. The output would be generic and not production-ready.

**Output (excerpt):**
> This is a very broad request. A "task management API" can be implemented in many ways. Here is a very basic example in Node.js and Express.
>
> ```javascript
> const express = require('express');
> const app = express();
> app.use(express.json());
> let tasks = [];
> let id = 1;
> app.get('/tasks', (req, res) => res.json(tasks));
> app.post('/tasks', (req, res) => {
>     const task = { id: id++, title: req.body.title };
>     tasks.push(task);
>     res.status(201).json(task);
> });
> app.listen(3000);
> ```
>
> You'll need to install `express` with `npm install express`. This is a very minimal starting point. For a production application, you would want to add better error handling, a database, and validation.

---

## Version 1 — Added Goal & Language

**Prompt:**
"Write a simple REST API for a task management application using Node.js, Express, and SQLite. Use the better-sqlite3 library. The database should have a tasks table with id, title, and done columns. The API should allow a user to create, read, update, and delete tasks."

**Layer added:** Goal + Language + Database

**Notes:**
- **What changed in the prompt:** I specified the goal (CRUD API), the language (Node.js/Express), and the database (SQLite with better-sqlite3).
- **What improved in the output:** The code now uses a real database instead of an in-memory array. Data persistence is now possible.
- **What still failed:** No validation for empty titles. No error handling for missing tasks (404). Code is all in one file.
- **What I would try next:** Add validation and 404 handling.

**Output (excerpt):**
> ```javascript
> const express = require('express');
> const Database = require('better-sqlite3');
> const app = express();
> app.use(express.json());
> const db = new Database('tasks.db');
> db.exec(`CREATE TABLE IF NOT EXISTS tasks ( id INTEGER PRIMARY KEY AUTOINCREMENT, title TEXT NOT NULL, done INTEGER DEFAULT 0 )`);
> app.get('/tasks', (req, res) => { /* ... */ });
> app.post('/tasks', (req, res) => {
>   const { title } = req.body;
>   const insert = db.prepare('INSERT INTO tasks (title) VALUES (?)');
>   const info = insert.run(title);
>   res.status(201).json({ id: info.lastInsertRowid, title });
> });
> // ... similar for other endpoints
> ```

---

## Version 2 — Added Validation & Error Handling

**Prompt:**
"Write a simple REST API for a task management application using Node.js, Express, and SQLite. Use the better-sqlite3 library. The database should have a tasks table with id, title, and done columns. The API should allow a user to create, read, update, and delete tasks.

Add validation to prevent creating tasks with an empty title.

Add error handling to return a 404 status when a task doesn't exist."

**Layer added:** Validation + Error Handling

**Notes:**
- **What changed in the prompt:** I added specific instructions for validation (title can't be empty) and error handling (404 for non-existent tasks).
- **What improved in the output:** The code now returns a `400` error for an empty title and a `404` error if a task is not found. It's now robust enough for basic use.
- **What still failed:** The code is still in one file. No structure or comments.
- **What I would try next:** Add code structure and comments.

**Output (excerpt):**
> ```javascript
> app.post('/tasks', (req, res) => {
>   const { title } = req.body;
>   if (!title || title.trim() === '') {
>     return res.status(400).json({ error: 'Title is required.' });
>   }
>   // ... insert logic
> });
> app.get('/tasks/:id', (req, res) => {
>   const task = db.prepare('SELECT * FROM tasks WHERE id = ?').get(req.params.id);
>   if (!task) {
>     return res.status(404).json({ error: 'Task not found.' });
>   }
>   res.json(task);
> });
> ```

---

## Version 3 — Added Structure & Documentation

**Prompt:**
"Write a simple REST API for a task management application using Node.js, Express, and SQLite. Use the better-sqlite3 library. The database should have a tasks table with id, title, and done columns. The API should allow a user to create, read, update, and delete tasks.

Add validation to prevent creating tasks with an empty title.

Add error handling to return a 404 status when a task doesn't exist.

Organize the code by separating the database setup and helpers into a separate file called database.js.

Add comments explaining the purpose of each major section."

**Layer added:** Code Structure + Documentation

**Notes:**
- **What changed in the prompt:** I requested a specific code structure (`database.js`) and comments.
- **What improved in the output:** The code is now more professional, organized, and maintainable.
- **What still failed:** The final output is still a bit messy. No examples of requests/responses.
- **What I would try next:** Add an example of a successful request/response.

**Output (excerpt):**
> **database.js**
> ```javascript
> const Database = require("better-sqlite3");
> const db = new Database("tasks.db");
> db.exec(`CREATE TABLE IF NOT EXISTS tasks ...`);
> const statements = {
>   getAll: db.prepare("SELECT * FROM tasks"),
>   getById: db.prepare("SELECT * FROM tasks WHERE id = ?"),
>   // ...
> };
> module.exports = statements;
> ```
>
> **server.js**
> ```javascript
> const express = require("express");
> const db = require("./database");
> // ... routes with validation and error handling
> ```

---

## Version 4 — Added Examples & Format

**Prompt:**
"Write a simple REST API for a task management application using Node.js, Express, and SQLite. Use the better-sqlite3 library. The database should have a tasks table with id, title, and done columns. The API should allow a user to create, read, update, and delete tasks.

Add validation to prevent creating tasks with an empty title.

Add error handling to return a 404 status when a task doesn't exist.

Organize the code by separating the database setup and helpers into a separate file called database.js.

Add comments explaining the purpose of each major section.

Provide an example of a successful request and response for creating a task.

Format the final response as a single Markdown code block."

**Layer added:** Examples + Format

**Notes:**
- **What changed in the prompt:** I added an example of a request/response and specified the output format.
- **What improved in the output:** The final answer is cleanly formatted and includes a clear example of how to use the API.
- **What still failed:** The code is still a bit basic — no advanced features like pagination or filtering.
- **What I would try next:** Add production-ready features like better error logging, input sanitization, and API versioning.

**Output (excerpt):**
> ```markdown
> # Task Management REST API
>
> ## Project Structure
> ```
> task-manager/
> ├── database.js
> ├── server.js
> └── package.json
> ```
>
> ## Example Request
> ```http
> POST /tasks
> Content-Type: application/json
> { "title": "Learn Express", "done": false }
> ```
> ## Example Response
> ```json
> { "id": 1, "title": "Learn Express", "done": 0 }
> ```
> ```

---

## Version 5 — Added Production-Ready Polish

**Prompt:**
"Write a production-ready REST API for a task management application in Node.js using Express and SQLite (better-sqlite3). The database has a "tasks" table with id (integer primary key), title (text, required), and done (boolean, default false). Provide all CRUD endpoints (GET, POST, PUT, DELETE) with proper validation and error handling, ensuring a 404 response for non-existent resources. Structure the code with clear separation of concerns (a database helper file and a server file), include explanatory comments, and format the response as a Markdown code block. Also include an example of a successful request/response for creating a task."

**Layer added:** Production-Ready Quality (clear separation of concerns, proper error handling, reusable helpers)

**Notes:**
- **What changed in the prompt:** I combined all previous layers into a single, polished request and added "production-ready" quality expectations.
- **What improved in the output:** The final code is clean, well-structured, and includes helper functions, proper error handling, and is ready to be used as a template for real projects.
- **What still failed:** The prompt doesn't ask for testing instructions or deployment steps.
- **What I would try next:** Add instructions for running tests or deploying to a cloud service.

**Output (excerpt):**
> ```javascript
> // database.js — Helper functions with proper error handling
> function getAllTasks() { /* ... */ }
> function getTaskById(id) { /* ... */ }
> function createTask(title, done = false) { /* ... */ }
> // server.js — Clean routes with validation and 404 handling
> app.get('/tasks', (req, res) => { /* ... */ });
> app.post('/tasks', (req, res) => { /* ... */ });
> ```

---

## Final Prompt — (Reusable)

"Write a production-ready REST API for a task management application in Node.js using Express and SQLite (better-sqlite3). The database has a 'tasks' table with id (integer primary key), title (text, required), and done (boolean, default false). Provide all CRUD endpoints (GET, POST, PUT, DELETE) with proper validation and error handling, ensuring a 404 response for non-existent resources. Structure the code with clear separation of concerns (a database helper file and a server file), include explanatory comments, and format the response as a Markdown code block. Also include an example of a successful request/response for creating a task."
