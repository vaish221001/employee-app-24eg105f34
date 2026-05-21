# Employee Management System (MERN Stack)

## Overview

Employee Management System is a full-stack MERN application developed to manage employee records efficiently.

The application allows users to:

- Add employee details
- View employee records
- Edit employee information
- Delete employees
- Store employee data in MongoDB
- Access the application through a responsive React interface

---

# Tech Stack

## Frontend
- React.js
- React Router
- Zustand
- React Hook Form
- Axios
- Tailwind CSS
- Vite

## Backend
- Node.js
- Express.js
- MongoDB
- Mongoose

---

# Features

✔ Add New Employees  
✔ View Employee List  
✔ View Employee Details  
✔ Update Employee Records  
✔ Delete Employee Records  
✔ Form Validation  
✔ Duplicate Email Detection  
✔ Error Handling  
✔ REST API Architecture  
✔ Responsive UI  

---

# Project Structure

```plaintext
Employee-Management-System
│
├── backend
│   ├── APIs
│   │   └── EmployeeAPI.js
│   │
│   ├── Models
│   │   └── EmployeeModel.js
│   │
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── frontend
│   ├── src
│   │
│   ├── components
│   │   ├── Home.jsx
│   │   ├── Header.jsx
│   │   ├── CreateEmp.jsx
│   │   ├── EditEmployee.jsx
│   │   ├── Employee.jsx
│   │   ├── ListOfEmps.jsx
│   │   └── RootLayout.jsx
│   │
│   ├── App.jsx
│   ├── main.jsx
│   └── package.json
│
└── README.md
```

---

# Employee Schema

| Field | Type | Validation |
|--------|------|-----------|
| name | String | Required |
| email | String | Required, Unique |
| mobile | Number | Required |
| designation | String | Required |
| companyName | String | Required |
| createdAt | Date | Auto Generated |
| updatedAt | Date | Auto Generated |

---

# API Routes

Base Route:

```bash
/employee-api
```

| Method | Endpoint | Description |
|--------|---------|-------------|
| POST | /employees | Add Employee |
| GET | /employees | Get Employees |
| PUT | /employees/:employeeId | Update Employee |
| DELETE | /employees/:employeeId | Delete Employee |

---

# Error Handling

| Error | Status |
|--------|--------|
| Validation Error | 400 |
| Invalid ID | 400 |
| Duplicate Email | 409 |
| Server Error | 500 |

---

# Frontend Routes

| Route | Component |
|--------|----------|
| / | Home |
| /create-emp | Create Employee |
| /list | Employee List |
| /employee | Employee Details |
| /edit-emp | Edit Employee |

---

# Installation

## Clone Repository

```bash
git clone YOUR_REPO_LINK
```

---

## Backend Setup

```bash
cd backend
npm install
npm start
```

Runs on:

```txt
http://localhost:5000
```

---

## Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Runs on:

```txt
http://localhost:5173
```

---

# Environment Variables

Create `.env`

```env
DB_URL=your_mongodb_url
PORT=5000
```

---

# Deployment

## Backend
Deploy on Render

## Frontend
Deploy on Vercel

---

# Future Improvements

- Authentication
- Search & Filter
- Pagination
- Employee Dashboard
- Analytics

---

## Author

Developed using MERN Stack
