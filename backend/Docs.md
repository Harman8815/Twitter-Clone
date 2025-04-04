# Server Documentation

This document provides an overview of the server-side codebase, including database models, controllers, routes, and middleware.

---

## Project Structure

```
server/
├── controllers/
│   ├── auth.controller.js         # Handles authentication-related logic
│   ├── user.controller.js         # Handles user-related operations
│   ├── post.controller.js         # Handles post-related operations
│   └── notification.controller.js # Handles notification-related operations
│
├── db/
│   └── connectMongoDB.js          # MongoDB connection logic
│
├── middleware/
│   └── protectRoute.js            # Middleware to protect routes (authentication)
│
├── models/
│   ├── user.model.js              # User schema and model
│   ├── post.model.js              # Post schema and model
│   └── notification.model.js      # Notification schema and model
│
├── routes/
│   ├── auth.routes.js             # Routes for authentication
│   ├── user.routes.js             # Routes for user-related operations
│   ├── post.routes.js             # Routes for post-related operations
│   └── notification.routes.js     # Routes for notification-related operations
│
├── lib/
│   └── utils/
│       └── generateToken.js       # Utility function to generate JWT tokens
│
├── docs.md                        # Documentation for the server-side codebase
├── server.js                      # Main entry point of the server
└── .env                           # Environment variables (not included in version control)
```

---

## Database Models

### 1. **User Model** ([models/user.model.js](server/models/user.model.js))
The `User` model represents a user in the application. It includes the following fields:
- `username` (String, required, unique): The user's username.
- `fullName` (String, required): The user's full name.
- `password` (String, required, minLength: 6): The user's hashed password.
- `email` (String, required, unique): The user's email address.
- `followers` (Array of ObjectIds): References to users following this user.
- `following` (Array of ObjectIds): References to users this user is following.
- `profileImg` (String): URL of the user's profile image.
- `coverImg` (String): URL of the user's cover image.
- `bio` (String): The user's bio.
- `link` (String): A link shared by the user.
- `likedPosts` (Array of ObjectIds): References to posts liked by the user.

---

### 2. **Post Model** ([models/post.model.js](server/models/post.model.js))
The `Post` model represents a post in the application. It includes:
- `user` (ObjectId, required): Reference to the user who created the post.
- `text` (String): The text content of the post.
- `img` (String): URL of the image associated with the post.
- `likes` (Array of ObjectIds): References to users who liked the post.
- `comments` (Array of objects): Each comment includes:
  - `text` (String, required): The comment text.
  - `user` (ObjectId, required): Reference to the user who made the comment.

---

### 3. **Notification Model** ([models/notification.model.js](server/models/notification.model.js))
The `Notification` model represents notifications sent to users. It includes:
- `from` (ObjectId, required): Reference to the user who triggered the notification.
- `to` (ObjectId, required): Reference to the user receiving the notification.
- `type` (String, required): The type of notification (`follow`, `like`).
- `read` (Boolean, default: false): Whether the notification has been read.

---

### 4. **Message Model** ([models/message.model.js](server/models/message.model.js))
The `Message` model represents a direct message between users. It includes:
- `sender` (ObjectId, required): Reference to the user who sent the message.
- `receiver` (ObjectId, required): Reference to the user who received the message.
- `text` (String, required): The content of the message.
- `timestamp` (Date, default: Date.now): The time when the message was sent.

---

## Routes

### 1. **Auth Routes** ([routes/auth.routes.js](server/routes/auth.routes.js))
Handles user authentication-related endpoints.

#### **Endpoints:**
- `GET /api/auth/me`
- `POST /api/auth/signup`
- `POST /api/auth/login`
- `POST /api/auth/logout`

---

### 2. **User Routes** ([routes/user.routes.js](server/routes/user.routes.js))
Handles user-related operations.

#### **Endpoints:**
- `GET /api/users/profile/:username`
- `POST /api/users/follow/:id`

---

### 3. **Post Routes** ([routes/post.routes.js](server/routes/post.routes.js))
Handles post-related operations.

#### **Endpoints:**
- `POST /api/posts/create`
- `POST /api/posts/like/:id`

---

### 4. **Notification Routes** ([routes/notification.routes.js](server/routes/notification.routes.js))
Handles notification-related operations.

#### **Endpoints:**
- `GET /api/notifications`
- `DELETE /api/notifications`

---

### 5. **Message Routes** ([routes/message.routes.js](server/routes/message.routes.js))
Handles direct messaging between users.

#### **Endpoints:**
- `POST /api/messages/send`
  - **Controller:** `sendMessage`
  - **Description:** Sends a message from one user to another.
  - **Request Example:**
    ```json
    {
      "receiver": "receiver_user_id",
      "text": "Hello, how are you?"
    }
    ```
- `GET /api/messages/:userId`
  - **Controller:** `getMessages`
  - **Description:** Retrieves messages between the logged-in user and another user.
  - **Example Response:**
    ```json
    [
      {
        "sender": "user1_id",
        "receiver": "user2_id",
        "text": "Hey!",
        "timestamp": "2025-04-02T12:00:00Z"
      }
    ]
    ```
- `DELETE /api/messages/:messageId`
  - **Controller:** `deleteMessage`
  - **Description:** Deletes a specific message.

---

## Middleware

### **Protect Route** ([middleware/protectRoute.js](server/middleware/protectRoute.js))
Ensures that a user is authenticated before accessing protected routes.

---

## Database Connection

### **MongoDB Connection** ([db/connectMongoDB.js](server/db/connectMongoDB.js))
Handles the connection to MongoDB using Mongoose.

---

## Utility Functions

### **Generate Token** ([lib/utils/generateToken.js](server/lib/utils/generateToken.js))
Generates a JWT token and sets it as a cookie.

---

## Server Entry Point

### **Server.js** ([server.js](server/server.js))
The main entry point of the server, configuring middleware, routes, and database connection.

