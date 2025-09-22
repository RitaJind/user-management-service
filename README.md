# 🔐 User Management Service

A **production-ready microservice** built with Node.js, Express, and MongoDB for scalable user authentication and authorization. This service demonstrates enterprise-grade architecture patterns, security best practices, and modern DevOps workflows.

![Node.js](https://img.shields.io/badge/Node.js-18+-green.svg)
![Express](https://img.shields.io/badge/Express-4.18+-blue.svg)
![MongoDB](https://img.shields.io/badge/MongoDB-4.4+-green.svg)
![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## 🚀 Project Overview

This microservice implements a **secure user management system** with JWT-based authentication, role-based access control, and comprehensive API endpoints. Built following **RESTful principles** and **clean architecture patterns**, it's designed for enterprise environments requiring scalable user authentication.

### 🏗️ **Architecture Highlights**
- **Microservice Architecture** - Containerized, independently deployable
- **Security-First Design** - bcrypt hashing, JWT tokens, CORS protection
- **Database Abstraction** - Mongoose ODM with schema validation
- **Centralized Error Handling** - Winston logging with structured error responses
- **Environment Configuration** - 12-factor app principles with dotenv
- **Container Orchestration** - Docker Compose with MongoDB integration

## 📋 Features

### 🔑 **Authentication & Authorization**
- ✅ **User Registration** with secure password hashing (bcrypt)
- ✅ **JWT Authentication** with configurable token expiration
- ✅ **Role-Based Access Control** (Student, Instructor, Admin)
- ✅ **Password Security** - Minimum complexity requirements
- ✅ **CORS Protection** - Cross-origin request handling

### 🛠️ **Technical Features**
- ✅ **RESTful API Design** - Standard HTTP methods and status codes
- ✅ **Input Validation** - Mongoose schema validation
- ✅ **Error Handling** - Centralized error middleware with logging
- ✅ **Health Monitoring** - Built-in health check endpoints
- ✅ **Container Ready** - Docker and Docker Compose support
- ✅ **Test Coverage** - Jest and Supertest integration

## 🏃‍♂️ Quick Start

### **Prerequisites**
- Node.js 18+ 
- MongoDB 4.4+
- Docker & Docker Compose (optional)

### **Option 1: Local Development**
```bash
# Clone the repository
git clone https://github.com/RitaJind/user-management-service.git
cd user-management-service

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your MongoDB connection details

# Start the service
npm start
```

### **Option 2: Docker Deployment**
```bash
# Start both application and MongoDB
docker-compose up --build

# View running services
docker-compose ps

# View logs
docker-compose logs -f
```

## 📡 API Documentation

### **Base URL**: `http://localhost:5000/api/users`

### **Authentication Endpoints**

#### **POST /register**
Register a new user account.

```bash
curl -X POST http://localhost:5000/api/users/register \
  -H "Content-Type: application/json" \
  -d '{
    "username": "johndoe",
    "email": "john@example.com",
    "password": "SecurePass123!"
  }'
```

**Response:**
```json
{
  "message": "User registered successfully."
}
```

#### **POST /login**
Authenticate user and receive JWT token.

```bash
curl -X POST http://localhost:5000/api/users/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john@example.com",
    "password": "SecurePass123!"
  }'
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

## 🏗️ Architecture & Design Patterns

### **Project Structure**
```
src/
├── app.js              # Application entry point
├── config/             # Configuration management
│   ├── db.js          # MongoDB connection
│   ├── env.js         # Environment variables
│   └── server.js      # Express server configuration
├── controllers/        # Request handlers
│   └── userController.js
├── middlewares/        # Custom middleware
│   └── authMiddleware.js
├── models/            # Database models
│   └── userModel.js
├── routes/            # API route definitions
│   └── userRoutes.js
├── services/          # Business logic layer
│   └── userService.js
└── utils/             # Utility functions
    ├── errorHandler.js
    └── logger.js
```

## 🧪 Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run tests in watch mode
npm run test:watch
```

## 🐳 Docker & DevOps

### **Container Architecture**
```yaml
services:
  app:                    # Node.js Application
    build: .
    ports: ["5000:5000"]
    environment:
      - MONGO_URI=mongodb://mongo:27017/usermngtservice
      
  mongo:                  # MongoDB Database
    image: mongo:latest
    ports: ["27017:27017"]
    volumes:
      - mongodb_data:/data/db
```

## 👨‍💻 About the Senior Software Engineer

**Rita Jindal** - Full Stack Developer  

*Passionate about building scalable, secure, and maintainable software solutions. Experienced in microservices architecture, cloud-native development, and full-stack web applications.*
