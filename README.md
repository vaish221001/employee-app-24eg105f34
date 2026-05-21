Employee Management System (MERN Stack)
Overview
A full-stack web application built with the MERN stack for managing employee records. Users can add, view, update, and delete employee information through a clean React-based interface, with data persisted in a MongoDB database via an Express.js REST API.

Features
Add new employee records with validation
View list of all employees
View individual employee details
Edit/update employee information
Delete employee records
Client-side routing with React Router
Global state management with Zustand
Form handling with React Hook Form
Duplicate email detection (HTTP 409)
Error handling for validation, cast, and server errors
Static file serving for production deployment
Project Structure
Employee-App/
├── Employee-Backend/
│   ├── APIs/
│   │   └── EmployeeAPI.js          → CRUD route handlers
│   ├── models/
│   │   └── EmployeeModel.js        → Mongoose schema & model
│   ├── dist/                        → Served static frontend build
│   ├── server.js                    → Express server, DB connection, middleware
│   ├── .env                         → Environment variables (MONGODB_URL, PORT)
│   ├── employee-req.http            → REST client test requests
│   └── package.json
│
├── employee-frontend/
│   ├── src/
│   │   ├── App.jsx                  → Router configuration & route definitions
│   │   ├── main.jsx                 → Entry point
│   │   ├── components/
│   │   │   ├── Home.jsx             → Landing page
│   │   │   ├── Header.jsx           → Navigation bar
│   │   │   ├── CreateEmp.jsx        → Add new employee form
│   │   │   ├── EditEmployee.jsx     → Edit employee form
│   │   │   ├── Employee.jsx         → Individual employee view
│   │   │   ├── ListOfEmps.jsx       → Employee list/card view
│   │   │   └── RootLayout.jsx       → Layout wrapper
│   │   └── store/
│   │       └── CounterStore.js      → Zustand global store
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
│
├── package.json                      → Root deployment scripts
└── .gitignore
Employee Schema
Field	Type	Validation
name	String	Required
email	String	Required, Unique
mobile	Number	Required
designation	String	Required
companyName	String	Required
createdAt	Date	Auto-generated (timestamps)
updatedAt	Date	Auto-generated (timestamps)
API Routes
Base Route: /employee-api

Method	Endpoint	Description	Status Code
POST	/employees	Create a new employee	201
GET	/employees	Retrieve all employees	200
PUT	/employees/:employeeId	Update employee details	200
DELETE	/employees/:employeeId	Delete an employee	200 / 404
Error Responses
Error Type	Status	Description
ValidationError	400	Missing or invalid field values
CastError	400	Invalid ID format
Duplicate Key	409	Email already exists (code 11000)
Server Error	500	Internal server error
Frontend Components
Component	Description
Home.jsx	Landing page of the application
Header.jsx	Navigation bar with routing links
CreateEmp.jsx	Form to add a new employee (React Hook Form)
EditEmployee.jsx	Form to update existing employee details
Employee.jsx	Displays individual employee information
ListOfEmps.jsx	Shows all employees in a list/card view
RootLayout.jsx	Layout wrapper with <Outlet /> for child routes
Frontend Routes
Path	Component	Description
/	Home	Landing page
/create-emp	CreateEmp	Add new employee form
/list	ListOfEmps	View all employees
/employee	Employee	View single employee
/edit-emp	EditEmployee	Edit employee details
Packages
Backend Dependencies
Package	Version	Purpose
express	^5.2.1	Web framework for REST API
mongoose	^9.3.3	MongoDB ODM for schema & queries
dotenv	^17.3.1	Load environment variables from .env
cors	^2.8.6	Enable Cross-Origin Resource Sharing
bcryptjs	^3.0.3	Password hashing utility
jsonwebtoken	^9.0.3	JWT token generation & verification
cookie-parser	^1.4.7	Parse cookies from requests
nodemon	^3.1.14	Auto-restart server on file changes
Frontend Dependencies
Package	Version	Purpose
react	^19.2.4	UI component library
react-dom	^19.2.4	React DOM rendering
react-router	^7.13.2	Client-side routing
react-hook-form	^7.72.0	Performant form handling & validation
zustand	^5.0.12	Lightweight global state management
axios	^1.14.0	HTTP client for API requests
tailwindcss	^4.2.2	Utility-first CSS framework
@tailwindcss/vite	^4.2.2	Tailwind CSS Vite plugin
Frontend Dev Dependencies
Package	Version	Purpose
vite	^6.0.3	Build tool and dev server
@vitejs/plugin-react	^4.3.0	React support for Vite
eslint	^9.39.4	Code linting
@eslint/js	^9.39.4	ESLint JavaScript config
eslint-plugin-react-hooks	^7.0.1	Lint rules for React hooks
eslint-plugin-react-refresh	^0.5.2	React Refresh lint rules
globals	^17.4.0	Global variable definitions
How to Run
Backend
cd Employee-Backend
npm install
node server.js        # or: nodemon server.js
Server starts on port 5000 (default). Requires a MONGODB_URL in the .env file.

Frontend
cd employee-frontend
npm install
npm run dev
Dev server starts at http://localhost:5173.

Production Deployment (Single Server)
# From the Employee-App root
npm install    # Runs postinstall: installs backend, frontend, and builds frontend
npm start      # Starts the backend which serves the frontend build
