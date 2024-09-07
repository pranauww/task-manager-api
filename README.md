# Task Manager App

This is a RESTful Task Manager API built using **Node.js**, **Express**, and **MongoDB**. It allows users to create accounts, manage tasks, and track progress. The app also supports file uploads for user avatars and provides email notifications for certain account actions using **SendGrid**.

## Features
- **User Registration/Login**: Create and manage user accounts securely with password hashing.
- **JWT Authentication**: Token-based authentication using JSON Web Tokens (JWT) for secure access.
- **Task Management**: Users can create, update, delete, and fetch tasks.
- **File Upload**: Users can upload profile avatars.
- **Email Notifications**: Sends welcome and cancellation emails to users.
- **Data Validation**: Ensures valid input using `validator`.
- **Timestamps**: Automatic timestamps for tasks and users (createdAt, updatedAt).

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Environment Variables](#environment-variables)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/task-manager.git
    cd task-manager
    ```

2. Install the required dependencies:
    ```bash
    npm install
    ```

3. Set up the MongoDB database and other environment variables (see below).

4. Start the app:
    - Development: 
        ```bash
        npm run dev
        ```
    - Production:
        ```bash
        npm start
        ```

## Usage

- The app is built with a REST API structure. You can use tools like **Postman** or **cURL** to test the endpoints.
- **Authentication**: Some routes require a valid JWT token in the `Authorization` header.
    ```
    Authorization: Bearer <token>
    ```

## Environment Variables

To run this project, you will need to add the following environment variables to your `.env` file:

```bash
MONGODB_URL=mongodb://127.0.0.1:27017/task-manager-api
JWT_SECRET=your_jwt_secret
SENDGRID_API_KEY=your_sendgrid_api_key
PORT=3000
```

## API Endpoints

### User Routes:
- **POST** `/users`: Create a new user (Signup)
- **POST** `/users/login`: Login a user
- **POST** `/users/logout`: Logout the authenticated user
- **GET** `/users/me`: Fetch the authenticated user's profile
- **PATCH** `/users/me`: Update the authenticated user's profile
- **DELETE** `/users/me`: Delete the authenticated user's profile
- **POST** `/users/me/avatar`: Upload user avatar
- **DELETE** `/users/me/avatar`: Delete user avatar

### Task Routes:
- **POST** `/tasks`: Create a new task
- **GET** `/tasks`: Fetch all tasks (supports filtering, pagination, and sorting)
- **GET** `/tasks/:id`: Fetch a specific task by ID
- **PATCH** `/tasks/:id`: Update a task by ID
- **DELETE** `/tasks/:id`: Delete a task by ID

## Code Overview

### `index.js`
Main entry point for the app. Sets up Express, middleware, and routers for users and tasks.

### `mongoose.js`
Handles MongoDB connection using **Mongoose**.

### `account.js`
Sends welcome and cancellation emails using **SendGrid**.

### `auth.js`
Middleware for authenticating users via JWT tokens.

### `user.js`
Mongoose schema for users, includes email validation, password hashing, and authentication logic.

### `task.js`
Mongoose schema for tasks, with reference to the owner (user) and automatic timestamps.

### `routers/user.js` and `routers/task.js`
Define the API routes for managing users and tasks, with full CRUD functionality.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.
