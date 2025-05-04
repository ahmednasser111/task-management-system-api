# Taskfyer Backend

Taskfyer is a task management backend API built with Node.js, Express, and MongoDB. It supports user authentication, email verification, password reset, and CRUD operations for tasks.

## Features

- User registration and login (JWT-based authentication)
- Email verification and password reset via email
- Role-based access (admin, creator, user)
- CRUD operations for tasks
- Middleware for authentication, authorization, and error handling

## Tech Stack

- Node.js
- Express.js
- MongoDB (Mongoose)
- Nodemailer (with Handlebars templates)
- JWT for authentication
- dotenv for environment variables

## Getting Started

### Prerequisites

- Node.js (v16+ recommended)
- MongoDB database (local or Atlas)
- Gmail account for sending emails (App password required)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/ahmednasser111/task-management-system-api.git
   cd task-management-system-api
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Create a `.env` file in the backend directory and configure the following variables:

   ```
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret
   PORT=8000
   CLIENT_URL=http://localhost:3000
   USER_EMAIL=your_gmail_address
   EMAIL_PASS=your_gmail_app_password
   NODE_ENV=development
   ```

4. Start the server:

   ```bash
   npm run dev
   ```

   The server will run on `http://localhost:8000` by default.

## API Endpoints

### Auth

- `POST /api/v1/register` - Register a new user
- `POST /api/v1/login` - Login user
- `GET /api/v1/logout` - Logout user
- `GET /api/v1/user` - Get current user (protected)
- `PATCH /api/v1/user` - Update user profile (protected)
- `GET /api/v1/login-status` - Check login status
- `POST /api/v1/verify-email` - Send verification email (protected)
- `POST /api/v1/verify-user/:verificationToken` - Verify user email
- `POST /api/v1/forgot-password` - Send password reset email
- `POST /api/v1/reset-password/:resetPasswordToken` - Reset password
- `PATCH /api/v1/change-password` - Change password (protected)

### Admin

- `GET /api/v1/admin/users` - Get all users (creator/admin only)
- `DELETE /api/v1/admin/users/:id` - Delete user (admin only)

### Tasks

- `POST /api/v1/task/create` - Create a new task (protected)
- `GET /api/v1/tasks` - Get all tasks for user (protected)
- `GET /api/v1/task/:id` - Get a single task (protected)
- `PATCH /api/v1/task/:id` - Update a task (protected)
- `DELETE /api/v1/task/:id` - Delete a task (protected)
- `DELETE /api/v1/tasks` - Delete all tasks for user (protected)

## Folder Structure

```
backend/
  src/
    controllers/
    db/
    helpers/
    middleware/
    models/
    routes/
    views/
  .env
  server.js
  README.md
```