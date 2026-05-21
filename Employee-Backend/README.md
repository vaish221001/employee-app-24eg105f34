# Employee Backend – REST API

## Overview

An Express.js REST API server for the Employee Management System. It connects to a MongoDB database via Mongoose and exposes CRUD endpoints for managing employee records. In production, it also serves the built React frontend as static files.

---

## Project Structure

```
Employee-Backend/
├── server.js               → Express server, DB connection, middleware, error handling
├── APIs/
│   └── EmployeeAPI.js      → CRUD route handlers for /employee-api
├── models/
│   └── EmployeeModel.js    → Mongoose schema & model definition
├── dist/                    → Served static frontend build (production)
├── .env                     → Environment variables (MONGODB_URL, PORT)
├── employee-req.http        → REST client test requests
└── package.json
```

---

## Employee Schema

| Field         | Type   | Validation                  |
| ------------- | ------ | --------------------------- |
| `name`        | String | Required                    |
| `email`       | String | Required, Unique            |
| `mobile`      | Number | Required                    |
| `designation` | String | Required                    |
| `companyName` | String | Required                    |
| `createdAt`   | Date   | Auto-generated (timestamps) |
| `updatedAt`   | Date   | Auto-generated (timestamps) |

---

## API Routes

Base Route: `/employee-api`

| Method | Endpoint                 | Description             | Status Code |
| ------ | ------------------------ | ----------------------- | ----------- |
| POST   | `/employees`             | Create a new employee   | 201         |
| GET    | `/employees`             | Retrieve all employees  | 200         |
| PUT    | `/employees/:employeeId` | Update employee details | 200         |
| DELETE | `/employees/:employeeId` | Delete an employee      | 200 / 404   |

### Error Handling

The server includes centralized error-handling middleware that catches and responds with appropriate status codes:

| Error Type      | Status | Description                       |
| --------------- | ------ | --------------------------------- |
| ValidationError | 400    | Missing or invalid field values   |
| CastError       | 400    | Invalid MongoDB ObjectId format   |
| Duplicate Key   | 409    | Email already exists (code 11000) |
| Server Error    | 500    | Internal server error             |

---

## Middleware

- **CORS** – Configured to allow requests from `http://localhost:5173` (Vite dev server)
- **JSON Parser** – `express.json()` for parsing request bodies
- **Static Files** – Serves the frontend build from `../employee-frontend/dist` in production
- **Catch-All Route** – Returns `index.html` for all unmatched routes (React Router support)

---

## Environment Variables

Create a `.env` file in this directory with:

```env
MONGODB_URL=<your-mongodb-connection-string>
PORT=5000
```

---

## Packages

### Dependencies

| Package        | Version  | Purpose                                |
| -------------- | -------- | -------------------------------------- |
| `express`      | ^5.2.1   | Web framework for building REST APIs   |
| `mongoose`     | ^9.3.3   | MongoDB ODM for schema & queries       |
| `dotenv`       | ^17.3.1  | Load environment variables from `.env` |
| `cors`         | ^2.8.6   | Enable Cross-Origin Resource Sharing   |
| `bcryptjs`     | ^3.0.3   | Password hashing utility               |
| `jsonwebtoken` | ^9.0.3   | JWT token generation & verification    |
| `cookie-parser`| ^1.4.7   | Parse cookies from requests            |
| `nodemon`      | ^3.1.14  | Auto-restart server on file changes    |

---

## How to Run

```bash
# Install dependencies
npm install

# Start the server
node server.js

# Or with auto-restart on changes
nodemon server.js
```

> Server starts on port `5000` by default. Ensure MongoDB is running and `MONGODB_URL` is set in `.env`.

---

## Author

Abhishikth Paul Ganta
