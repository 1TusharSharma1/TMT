# 🚀 Task Management System

A full-stack task management application built with **React**, **Node.js**, **Express**, and **MongoDB**. Features role-based access control, real-time notifications, beautiful UI with dark/light themes, and comprehensive task management capabilities.

![Task Manager Screenshot](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![React](https://img.shields.io/badge/React-19.1.1-blue)
![Node.js](https://img.shields.io/badge/Node.js-Latest-green)
![MongoDB](https://img.shields.io/badge/MongoDB-8.5.0-brightgreen)

## ✨ Features

### 🔐 **Authentication & Authorization**
- **User Registration & Login** with JWT token-based authentication
- **Role-based Access Control** with three roles:
  - **User**: Can view and update tasks assigned to them
  - **Manager**: Can create tasks, manage their team's tasks
  - **Admin**: Full system access including user management
- **Protected Routes** with automatic redirects
- **Token persistence** in localStorage with auto-login

### 📋 **Task Management**
- **Create, Read, Update, Delete** tasks with comprehensive validation
- **Task Status Management**: Pending, In-Progress, Completed
- **Due Date Validation**: Past dates blocked, only today and future dates allowed
- **Task Assignment** to specific users
- **Optimistic UI Updates** for instant feedback
- **Real-time Status Updates** with toast notifications
- **Task Filtering** based on user roles and permissions

### 👥 **User Management** (Admin Only)
- **View All Users** in a comprehensive table
- **Role Management**: Edit user roles dynamically
- **User Deletion** capabilities
- **Loading States** with skeleton components

### 📅 **Calendar Integration**
- **FullCalendar Integration** with month/week/day views
- **Color-coded Tasks** by status:
  - 🔴 **Red**: Pending tasks
  - 🟡 **Yellow**: In-progress tasks
  - 🟢 **Green**: Completed tasks
- **Interactive Calendar** with task visualization
- **Multiple View Modes**: Month, Week, Day grid

### 🎨 **Modern UI/UX**
- **Dark/Light Theme Toggle** with system preference detection
- **Responsive Design** optimized for all devices
- **Glass-morphism Effects** with backdrop blur
- **Gradient Backgrounds** with animated decorative elements
- **Loading Skeletons** for better perceived performance
- **Toast Notifications** for user feedback
- **Accessible Components** with ARIA labels and focus management

### 🛡️ **Security Features**
- **Password Hashing** with bcrypt
- **JWT Token Validation** on all protected routes
- **Role-based Route Protection**
- **CORS Configuration** for cross-origin requests
- **Input Validation** with Zod schema validation
- **SQL Injection Protection** via MongoDB ODM

## 🏗️ **Architecture**

### **Backend (Node.js/Express)**
```
backend/
├── controllers/
│   ├── Authcontroller.js      # Authentication logic
│   ├── Taskcontroller.js      # Task CRUD operations
│   └── User.js                # User management
├── middleware/
│   ├── auth.js                # JWT verification
│   └── role.js                # Role-based authorization
├── models/
│   ├── Task.js                # Task schema & validation
│   └── Users.js               # User schema & methods
├── router/
│   ├── auth.js                # Auth routes
│   ├── taskRouter.js          # Task routes
│   └── Userroute.js           # User management routes
├── .env                       # Environment variables
└── server.js                  # Express server setup
```

### **Frontend (React)**
```
frontend/
├── public/                    # Static assets
├── src/
│   ├── components/
│   │   ├── layout/
│   │   │   └── Layout.js      # Shared layout with navigation
│   │   ├── ui/                # Reusable UI components
│   │   │   ├── Button.js      # Button with variants
│   │   │   ├── Card.js        # Card container
│   │   │   ├── Badge.js       # Status badges
│   │   │   ├── Input.js       # Form inputs with validation
│   │   │   ├── Modal.js       # Accessible modal
│   │   │   └── Skeleton.js    # Loading placeholders
│   │   ├── AuthContext.js     # Authentication state
│   │   ├── ProtectedRoute.js  # Route protection
│   │   ├── DashboardPage.js   # Main dashboard
│   │   ├── CalendarPage.js    # Calendar view
│   │   ├── TaskForm.js        # Task creation/editing
│   │   ├── TaskList.js        # Task display grid
│   │   ├── UserList.js        # User management table
│   │   ├── LoginPage.js       # Login form
│   │   └── SignupPage.js      # Registration form
│   ├── api.js                 # Axios configuration
│   ├── App.js                 # Main app component
│   └── index.css              # Global styles & theme
└── package.json
```

## 🚀 **Quick Start**

### **Prerequisites**
- Node.js (v16+ recommended)
- MongoDB (local or Atlas)
- Git

### **Installation**

1. **Clone the repository**
```bash
git clone <repository-url>
cd Task-management
```

2. **Backend Setup**
```bash
cd backend
npm install

# Create .env file
echo "PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/task-management-db
JWT_SECRET=your-super-secret-jwt-key" > .env

# Start the server
npm start
```

3. **Frontend Setup**
```bash
cd ../frontend
npm install

# Create .env file
echo "REACT_APP_API_URL=http://localhost:5000/api" > .env

# Start the development server
npm start
```

4. **Access the Application**
- Frontend: [http://localhost:3000](http://localhost:3000)
- Backend API: [http://localhost:5000](http://localhost:5000)

## 📖 **Usage Guide**

### **Getting Started**
1. **Register** a new account (choose role: User, Manager, or Admin)
2. **Login** with your credentials
3. **Navigate** using the header menu

### **Task Management**
- **Creating Tasks** (Manager/Admin): Use the task form on the dashboard
- **Viewing Tasks**: See all assigned tasks in the grid layout
- **Updating Status**: Use the dropdown on each task card
- **Editing Tasks**: Click the "Edit" button to modify task details
- **Calendar View**: Switch to calendar to see tasks by due date

### **User Management** (Admin Only)
- Access via the "Users" navigation link
- **Edit Roles**: Click "Edit" next to any user
- **Delete Users**: Use the "Delete" button (be careful!)

### **Theme Switching**
- Click the 🌙/☀️ icon in the header to toggle dark/light mode
- Preference is saved in localStorage

## 🔧 **API Endpoints**

### **Authentication**
```
POST /api/auth/register  # User registration
POST /api/auth/login     # User login
```

### **Tasks**
```
GET    /api/tasks        # Get tasks (filtered by role)
POST   /api/tasks        # Create task (Manager/Admin)
PUT    /api/tasks/:id    # Update task
DELETE /api/tasks/:id    # Delete task (Admin)
```

### **Users**
```
GET    /api/users        # Get all users (Manager/Admin)
PUT    /api/users/:id    # Update user role (Admin)
DELETE /api/users/:id    # Delete user (Admin)
```

## 🛠️ **Technical Stack**

### **Frontend Technologies**
- **React 19.1.1** with Hooks and Context
- **React Router 7.8** for navigation
- **React Hook Form 7.53** + **Zod 3.23** for validation
- **Tailwind CSS 3.4** for styling
- **FullCalendar 6.1** for calendar functionality
- **React Hot Toast** for notifications
- **Axios** for HTTP requests
- **clsx** for conditional styling

### **Backend Technologies**
- **Node.js** with Express 4.19
- **MongoDB 8.5** with Mongoose ODM
- **JWT** for authentication
- **bcryptjs** for password hashing
- **CORS** for cross-origin requests
- **dotenv** for environment management

### **Development Tools**
- **Create React App** for frontend tooling
- **PostCSS** + **Autoprefixer** for CSS processing
- **ESLint** for code linting
- **React Testing Library** for testing setup

## 🎯 **Key Features Breakdown**

### **🔍 Smart Task Filtering**
- **Users**: See only tasks assigned to them
- **Managers**: See their created tasks + team member tasks
- **Admins**: See all tasks in the system

### **📱 Responsive Design**
- **Mobile-first** approach with breakpoints
- **Touch-friendly** interfaces on mobile
- **Collapsible navigation** on small screens
- **Optimized task cards** for different screen sizes

### **🎨 Design System**
- **CSS Variables** for consistent theming
- **Reusable Components** with prop-based variants
- **Focus States** for accessibility
- **Loading States** throughout the application
- **Error Handling** with user-friendly messages

### **⚡ Performance Optimizations**
- **Code Splitting** with React.lazy (ready for implementation)
- **Optimistic Updates** for immediate feedback
- **Skeleton Loading** to improve perceived performance
- **Efficient Re-renders** with React hooks optimization

## 🔒 **Security Considerations**

- **Environment Variables** for sensitive data
- **JWT Tokens** with expiration (1 hour)
- **Password Hashing** with salt rounds
- **Input Validation** on both client and server
- **Role-based Access Control** throughout the application
- **Protected Routes** with automatic redirects

## 📱 **Browser Support**
- **Chrome** (last 2 versions)
- **Firefox** (last 2 versions)
- **Safari** (last 2 versions)
- **Edge** (last 2 versions)

## 🤝 **Contributing**

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 **License**

This project is licensed under the ISC License - see the package.json files for details.

## 🐛 **Known Issues & Limitations**

- **Token Expiration**: Currently set to 1 hour (consider implementing refresh tokens)
- **Real-time Updates**: No WebSocket implementation (tasks don't update live across users)
- **File Uploads**: No attachment support for tasks
- **Email Notifications**: Not implemented
- **Task Dependencies**: No task relationship features

## 🚀 **Future Enhancements**

- [ ] **Real-time Collaboration** with WebSockets
- [ ] **Task Comments** and activity history
- [ ] **File Attachments** for tasks
- [ ] **Email Notifications** for due dates
- [ ] **Task Templates** and recurring tasks
- [ ] **Advanced Filtering** and search
- [ ] **Time Tracking** functionality
- [ ] **Gantt Chart** view
- [ ] **Mobile App** with React Native
- [ ] **Export/Import** functionality

## 📞 **Support**

For support, please open an issue in the GitHub repository or contact the development team.

---

**Built with ❤️ by the Task Management Team**