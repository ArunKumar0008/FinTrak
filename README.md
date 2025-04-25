# FinTrak - Expense Management System

FinTrak is a comprehensive expense management system designed to streamline financial tracking for businesses of all sizes. With role-based access controls, it enables employees to submit expenses, managers to review and approve them, and administrators to gain insights through advanced analytics.

## 📋 Project Overview

FinTrak provides a modern, responsive user interface with the following key features:

- **User Authentication**: Secure login/signup with role-based access control (Employee, Manager, Admin)
- **Dashboard Analytics**: Visual representation of expense data through charts and graphs
- **Expense Management**: Submit, track, approve, and manage expense requests
- **Reporting Tools**: Generate and export detailed expense reports
- **Responsive Design**: Optimized for all device sizes from mobile to desktop

## 🔧 Tech Stack

- **Frontend**: React.js, Material-UI, Recharts
- **State Management**: React Hooks and Context API
- **Routing**: React Router
- **Build Tool**: Vite
- **Backend**: Java Spring boot
- **Database**: Mysql

## 🚀 Installation & Setup

### Prerequisites
- Node.js (v14.0.0 or later)
- npm (v6.0.0 or later)

### Installation Steps

1. Clone the repository
   ```bash
   git clone https://github.com/ArunKumar0008/FinTrak.git
   cd FinTrak
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Start the development server
   ```bash
   npm run dev
   ```

4. Build for production
   ```bash
   npm run build
   ```

## 🏗️ Project Structure
Front end
```
fintrak/
├── public/
├── src/
│   ├── components/          # Reusable UI components
│   │   ├── DashboardCard.jsx
│   │   ├── DashboardLayout.jsx
│   │   ├── Navbar.jsx
│   │   └── NotificationCenter.jsx
│   ├── pages/
│   │   ├── dashboard/       # Dashboard-related pages
│   │   │   ├── admin/       # Admin-specific pages
│   │   │   ├── manager/     # Manager-specific pages
│   │   │   └── employee/    # Employee-specific pages
│   │   ├── Home.jsx         # Landing page
│   │   ├── Login.jsx        # Authentication pages
│   │   ├── Signup.jsx
│   │   ├── About.jsx
│   │   └── Contact.jsx
│   ├── hooks/               # Custom hooks for authentication, etc.
│   ├── ThemeContext.jsx     # Theme context for dark/light mode
│   ├── App.jsx              # Main application component
│   └── main.jsx             # Entry point
└── package.json
```
Back end
```
Backend/
├── HELP.md
├── mvnw
├── mvnw.cmd
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/zideo/fintrack/
│   │   │       ├── FinTrackApplication.java
│   │   │       ├── controller/
│   │   │       │   └── ExpenseController.java
│   │   │       ├── dto/
│   │   │       │   ├── ExpenseDTO.java
│   │   │       │   └── Status.java
│   │   │       ├── entities/
│   │   │       │   ├── Category.java
│   │   │       │   ├── Department.java
│   │   │       │   ├── Expense.java
│   │   │       │   ├── ExpenseDashboardDTO.java
│   │   │       │   ├── Notification.java
│   │   │       │   ├── Report.java
│   │   │       │   └── User.java
│   │   │       ├── repository/
│   │   │       │   └── ExpenseRepository.java
│   │   │       └── service/
│   │   │           └── ExpenseService.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/com/zideo/fintrack/
│           └── FinTrackApplicationTests.java
└── target/
    └── (compiled classes)

```

## 🔌 API Integration Points

For the backend team developing with SpringBoot, here are the key integration points:

### Authentication Endpoints

- `POST /api/auth/login`: User login with credentials and role
- `POST /api/auth/signup`: User registration
- `GET /api/auth/profile`: Get current user profile

### Expense Management

- `GET /api/expenses`: List expenses (with filters for status, date range)
- `POST /api/expenses`: Create new expense
- `PUT /api/expenses/{id}`: Update expense
- `DELETE /api/expenses/{id}`: Delete expense
- `PUT /api/expenses/{id}/approve`: Approve expense
- `PUT /api/expenses/{id}/reject`: Reject expense

### Analytics

- `GET /api/analytics/summary`: Get expense summary (total, pending, approved)
- `GET /api/analytics/by-category`: Get expenses grouped by category
- `GET /api/analytics/by-department`: Get expenses grouped by department
- `GET /api/analytics/monthly`: Get monthly expense trends

### Data Models

**User Model**
```json
{
  "id": "string",
  "name": "string",
  "workId": "string",
  "email": "string",
  "role": "EMPLOYEE | MANAGER | ADMIN",
  "department": "string",
  "position": "string",
  "profileImage": "string",
  "contactNumber": "string",
  "dateJoined": "date",
  "isActive": "boolean"
}
```

**Expense Model**
```json
{
  "id": "string",
  "employeeId": "string",
  "employeeName": "string",
  "departmentId": "string",
  "departmentName": "string",
  "categoryId": "string",
  "categoryName": "string",
  "amount": "number",
  "date": "date",
  "description": "string",
  "status": "PENDING | APPROVED | REJECTED",
  "receiptUrl": "string",
  "attachments": ["string"],
  "submittedDate": "date",
  "approvedBy": "string",
  "approvedDate": "date",
  "rejectionReason": "string",
  "notes": "string",
  "tags": ["string"]
}
```

**Department Model**
```json
{
  "id": "string",
  "name": "string",
  "managerId": "string",
  "managerName": "string",
  "budget": "number",
  "budgetUsed": "number",
  "budgetRemaining": "number",
  "employeeCount": "number",
  "description": "string",
  "isActive": "boolean"
}
```

**Category Model**
```json
{
  "id": "string",
  "name": "string",
  "description": "string",
  "icon": "string",
  "color": "string",
  "isDefault": "boolean",
  "isActive": "boolean",
  "limits": {
    "perTransaction": "number",
    "daily": "number",
    "monthly": "number"
  }
}
```

**Analytics Summary Model**
```json
{
  "totalExpenses": "number",
  "pendingExpenses": "number",
  "approvedExpenses": "number",
  "rejectedExpenses": "number",
  "thisMonthTotal": "number",
  "lastMonthTotal": "number",
  "percentageChange": "number",
  "topCategories": [
    {
      "categoryName": "string",
      "amount": "number",
      "percentage": "number"
    }
  ],
  "topDepartments": [
    {
      "departmentName": "string",
      "amount": "number",
      "percentage": "number"
    }
  ],
  "monthlyBreakdown": [
    {
      "month": "string",
      "expenses": "number",
      "budget": "number"
    }
  ]
}
```

**Notification Model**
```json
{
  "id": "string",
  "userId": "string",
  "type": "EXPENSE_SUBMITTED | EXPENSE_APPROVED | EXPENSE_REJECTED | REMINDER | SYSTEM",
  "title": "string",
  "message": "string",
  "referenceId": "string",
  "referenceType": "EXPENSE | USER | DEPARTMENT",
  "isRead": "boolean",
  "createdAt": "date"
}
```

**Report Model**
```json
{
  "id": "string",
  "name": "string",
  "type": "EXPENSE | DEPARTMENT | USER | CATEGORY",
  "filters": {
    "startDate": "date",
    "endDate": "date",
    "departments": ["string"],
    "categories": ["string"],
    "status": ["string"],
    "users": ["string"]
  },
  "createdBy": "string",
  "createdAt": "date",
  "lastGenerated": "date",
  "format": "PDF | EXCEL | CSV",
  "isScheduled": "boolean",
  "scheduleFrequency": "DAILY | WEEKLY | MONTHLY | QUARTERLY"
}
```

## 🎨 UI Components

The UI is built with Material-UI with a custom theme that supports both light and dark modes. Key features include:

- Glass-morphism design for cards and forms
- Responsive layout that adapts to screen size
- Interactive data visualization with Recharts
- Consistent teal blue color scheme (#26A6B5) with hover states

## 🔄 State Management

The application uses React's Context API for global state management:
- `ThemeContext`: Controls light/dark mode
- Authentication state is managed through custom hooks

## 📝 License

[MIT License](LICENSE)

## 👥 Contributors

- [Arunkumar](https://github.com/ArunKumar0008)
