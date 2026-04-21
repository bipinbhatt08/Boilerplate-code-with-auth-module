# 🚀 Auth Boilerplate (Node.js + Express + MongoDB)

⚡ Minimal and scalable authentication system.  
Clone → setup `.env` → run → done.

---

## 📖 Introduction

This project is a minimal and scalable authentication boilerplate built with Node.js, Express, and MongoDB.

It provides a complete authentication system using JWT-based access and refresh tokens, along with essential features like email verification and password reset. The goal is to give developers a clean starting point that can be easily extended for real-world applications.

The architecture follows a modular approach using controllers, services, DTOs, and middleware to keep the codebase maintainable and easy to scale.

---

## ✨ Features

- 🔐 JWT Authentication (Access + Refresh Tokens)
- 📧 Email Verification
- 🔁 Refresh Token Rotation
- 🔑 Forgot / Reset Password
- 🛡️ Password hashing with bcrypt
- 📦 Clean architecture (DTOs, middleware, services)
- 🍪 Supports Cookies & Authorization headers

---

## ⚙️ How It Works

### 🔐 Authentication Flow

1. **User Registration**
   - User signs up with name, email, and password
   - Password is hashed using bcrypt
   - A verification token is generated
   - Verification email is sent to the user

2. **Email Verification**
   - User clicks the verification link (`/verify-email/:token`)
   - Token is validated
   - User is marked as verified

3. **Login**
   - User provides email and password
   - Credentials are validated
   - Two tokens are generated:
     - **Access Token** (short-lived)
     - **Refresh Token** (long-lived)
   - Refresh token is stored in the database (hashed)

4. **Access Protected Routes**
   - Client sends access token (via cookies or Authorization header)
   - Middleware verifies the token
   - If valid, user is allowed access

5. **Token Refresh**
   - When access token expires, client sends refresh token
   - Server verifies:
     - Token validity
     - Match with hashed token in database
   - New access token and refresh token are issued

6. **Logout**
   - Refresh token is removed from database
   - User session is invalidated

---

### 🔑 Password Reset Flow

1. **Forgot Password**
   - User submits email
   - Reset token is generated
   - Email with reset link is sent

2. **Reset Password**
   - User sends new password with token
   - Token is verified
   - Password is updated
   - Reset token is removed

---

### 🔒 Security Approach

- Passwords are hashed using bcrypt
- Refresh tokens are stored as hashed values
- Sensitive fields are hidden using `select: false`
- Tokens are rotated on refresh
- Verification and reset tokens are temporary and invalidated after use

---

## 🚀 How to Run the Project

Follow these steps to run the project locally.

---

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/bipinbhatt08/Boilerplate-code-with-auth-module.git
cd projects
```
### 2️⃣ Install Dependencies
```bash
npm install
```
### 3️⃣ Setup Environment Variables
Create a .env file in the root directory (env.example is reference)

### 4️⃣ Start MongoDB (Docker)
Make sure Docker is running:
```bash
npm run db:up
```
### 5️⃣ Start the Server
```bash
npm run dev
```
---

## 📬 API Collection (Postman)

You can test all API endpoints using the Postman collection:

👉 [View Postman Collection](https://web.postman.co/workspace/broadway-learning~c3462699-0f29-4cc1-8c69-9e8dad6a675a/collection/30097916-bb9a44b5-f4dc-4470-b7d4-be3dcb9b0001?action=share&source=copy-link&creator=30097916))

---

