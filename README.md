# Taskfyer Backend

Taskfyer is a task management backend API built with Node.js, Express, and MongoDB. It supports user authentication, email verification, password reset, and CRUD operations for tasks.

---

## Table of Contents

1. [Features](#features)
2. [Tech Stack](#tech-stack)
3. [Getting Started](#getting-started)
4. [Environment Variables](#environment-variables)
5. [API Endpoints](#api-endpoints)
   - [Authentication](#authentication)
   - [Admin](#admin)
   - [Tasks](#tasks)
6. [Middleware](#middleware)
7. [Error Handling](#error-handling)
8. [Email Templates](#email-templates)
9. [Folder Structure](#folder-structure)
10. [License](#license)
11. [Author](#author)

---

## Features

- User registration and login (JWT-based authentication)
- Email verification and password reset via email
- Role-based access (admin, creator, user)
- CRUD operations for tasks
- Middleware for authentication, authorization, and error handling

---

## Tech Stack

- Node.js
- Express.js
- MongoDB (Mongoose)
- Nodemailer (with Handlebars templates)
- JWT for authentication
- dotenv for environment variables

---

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

3. Create a `.env` file in the backend directory and configure the following variables (see [Environment Variables](#environment-variables)).

4. Start the server:

   ```bash
   npm run dev
   ```

   The server will run on `http://localhost:8000` by default.

---

## Environment Variables

The `.env` file should include the following variables:

```
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PORT=8000
CLIENT_URL=http://localhost:3000
USER_EMAIL=your_gmail_address
EMAIL_PASS=your_gmail_app_password
NODE_ENV=development
```

---

## API Endpoints

### Authentication

| Method | Endpoint                          | Description                          | Protected |
|--------|-----------------------------------|--------------------------------------|-----------|
| POST   | `/api/v1/register`                | Register a new user                  | No        |
| POST   | `/api/v1/login`                   | Login user                           | No        |
| GET    | `/api/v1/logout`                  | Logout user                          | Yes       |
| GET    | `/api/v1/user`                    | Get current user                     | Yes       |
| PATCH  | `/api/v1/user`                    | Update user profile                  | Yes       |
| GET    | `/api/v1/login-status`            | Check login status                   | Yes       |
| POST   | `/api/v1/verify-email`            | Send verification email              | Yes       |
| POST   | `/api/v1/verify-user/:token`      | Verify user email                    | No        |
| POST   | `/api/v1/forgot-password`         | Send password reset email            | No        |
| POST   | `/api/v1/reset-password/:token`   | Reset password                       | No        |
| PATCH  | `/api/v1/change-password`         | Change password                      | Yes       |

### Admin

| Method | Endpoint                          | Description                          | Protected |
|--------|-----------------------------------|--------------------------------------|-----------|
| GET    | `/api/v1/admin/users`             | Get all users                        | Yes       |
| DELETE | `/api/v1/admin/users/:id`         | Delete a user                        | Yes       |

### Tasks

| Method | Endpoint                          | Description                          | Protected |
|--------|-----------------------------------|--------------------------------------|-----------|
| POST   | `/api/v1/task/create`             | Create a new task                    | Yes       |
| GET    | `/api/v1/tasks`                   | Get all tasks for the user           | Yes       |
| GET    | `/api/v1/task/:id`                | Get a single task                    | Yes       |
| PATCH  | `/api/v1/task/:id`                | Update a task                        | Yes       |
| DELETE | `/api/v1/task/:id`                | Delete a task                        | Yes       |
| DELETE | `/api/v1/tasks`                   | Delete all tasks for the user        | Yes       |

---

## Middleware

### Authentication Middleware

- **`protect`**: Ensures the user is authenticated.
- **`adminMiddleware`**: Restricts access to admin users.
- **`creatorMiddleware`**: Restricts access to creators and admins.
- **`verifiedMiddleware`**: Ensures the user has verified their email.

---

## Error Handling

The project uses a centralized error handler to manage errors. Errors are logged and returned in a consistent format:

```json
{
  "message": "Error message",
  "stack": "Error stack trace (only in development)"
}
```

---

## Email Templates

The project uses Handlebars templates for sending emails. Templates are located in the `src/views` directory.

### Available Templates

1. **`emailVerification.handlebars`**: Used for email verification.
2. **`forgotPassword.handlebars`**: Used for password reset.

---

## Folder Structure

```
backend/
  src/
    controllers/       # API controllers
    db/                # Database connection
    helpers/           # Utility functions
    middleware/        # Middleware functions
    models/            # Mongoose models
    routes/            # API routes
    views/             # Email templates
  .env                 # Environment variables
  server.js            # Entry point
  README.md            # Project overview and documentation
```

---
## License

This project is licensed under the [MIT License](LICENSE).

---

## Author

[Ahmed Nasser](https://github.com/ahmednasser111)