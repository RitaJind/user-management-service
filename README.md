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

### **Design Patterns Used**
- **MVC Architecture** - Model-View-Controller separation
- **Repository Pattern** - Data access abstraction
- **Middleware Pattern** - Cross-cutting concerns
- **Factory Pattern** - Configuration object creation
- **Strategy Pattern** - Authentication strategies

## 🧪 Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run tests in watch mode
npm run test:watch
```

### **Test Coverage**
- ✅ **Unit Tests** - Controller and service layer testing
- ✅ **Integration Tests** - API endpoint testing
- ✅ **Authentication Tests** - JWT token validation
- ✅ **Database Tests** - MongoDB integration testing

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

### **Production Deployment**
- **Health Checks** - Container health monitoring
- **Graceful Shutdown** - SIGTERM signal handling
- **Resource Limits** - Memory and CPU constraints
- **Security Scanning** - Vulnerability assessment
- **Log Aggregation** - Centralized logging setup

## 🔧 Configuration

### **Environment Variables**
```env
# Database Configuration
MONGO_URI=mongodb://localhost:27017/usermngtservice

# Server Configuration  
PORT=5000
NODE_ENV=production

# Security Configuration
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRES_IN=1h

# Logging Configuration
LOG_LEVEL=info
```

## 📊 Performance & Monitoring

### **Performance Metrics**
- **Response Time**: < 100ms average
- **Throughput**: 1000+ requests/second
- **Memory Usage**: < 150MB average
- **Database Connections**: Connection pooling enabled

### **Monitoring Integration**
- **Health Endpoints** - `/health`, `/metrics`
- **Winston Logging** - Structured JSON logs
- **Error Tracking** - Centralized error aggregation
- **Performance Monitoring** - Request/response timing

---

## 🎯 **TECHNICAL CHALLENGE**

### **🏆 The Scalability Challenge**

**Scenario**: You're a senior developer tasked with scaling this service for a **high-traffic e-learning platform** with 100,000+ concurrent users.

#### **Your Mission** (Choose Your Adventure):

### **🚀 Level 1: Performance Optimization**
**Time**: 30 minutes  
**Goal**: Optimize the existing code for better performance

**Tasks**:
1. **Database Optimization**: Add appropriate indexes to the User model
2. **Caching Layer**: Implement Redis caching for JWT tokens
3. **Connection Pooling**: Optimize MongoDB connection pooling
4. **Rate Limiting**: Add API rate limiting middleware

**Bonus Points**: 
- Implement connection health checks
- Add request/response compression
- Create performance benchmarking tests

### **🔥 Level 2: Microservices Architecture**
**Time**: 60 minutes  
**Goal**: Break down the monolith into proper microservices

**Tasks**:
1. **Service Separation**: Split into separate services:
   - `auth-service` (login/register)
   - `user-profile-service` (user data management)
   - `permission-service` (role management)
2. **API Gateway**: Implement Kong or Express Gateway
3. **Service Discovery**: Add Consul or etcd integration
4. **Inter-Service Communication**: gRPC or message queues

### **🌟 Level 3: Production Infrastructure**
**Time**: 90 minutes  
**Goal**: Make it production-ready for enterprise deployment

**Tasks**:
1. **Kubernetes Deployment**: Create K8s manifests with:
   - Deployments, Services, ConfigMaps
   - Horizontal Pod Autoscaling
   - Ingress controllers
2. **Observability Stack**: Implement:
   - Prometheus metrics
   - Grafana dashboards  
   - ELK stack logging
   - Distributed tracing (Jaeger)
3. **Security Hardening**:
   - RBAC policies
   - Network policies
   - Secret management (HashiCorp Vault)
   - Container image scanning

### **🏅 Level 4: Advanced Features**
**Time**: 120 minutes  
**Goal**: Add enterprise-grade features

**Tasks**:
1. **Multi-tenancy**: Support for multiple organizations
2. **Advanced Auth**: OAuth2/OpenID Connect integration
3. **Event Sourcing**: Implement event-driven architecture
4. **Data Pipeline**: Real-time user analytics with Kafka
5. **Machine Learning**: User behavior analysis and recommendations

---

### **📝 Submission Guidelines**

1. **Fork this repository**
2. **Create a feature branch**: `feature/scalability-challenge`
3. **Document your approach** in `CHALLENGE.md`
4. **Include performance benchmarks** and **before/after metrics**
5. **Create a pull request** with detailed explanation

### **🏆 Evaluation Criteria**

- **Code Quality** (25%) - Clean, maintainable, well-documented code
- **Architecture** (25%) - Scalable design patterns and best practices  
- **Performance** (20%) - Measurable performance improvements
- **Production Readiness** (20%) - Monitoring, logging, error handling
- **Innovation** (10%) - Creative solutions and modern technologies

### **💡 Bonus Challenges**

- **Cloud Native**: Deploy on AWS EKS/GCP GKE with auto-scaling
- **Chaos Engineering**: Implement chaos testing with Chaos Monkey
- **Multi-Region**: Design for global deployment with data replication
- **Compliance**: Add GDPR/SOC2 compliance features

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 About the Developer

**Rita Jindal** - Full Stack Developer & Data Engineer  
🔗 [LinkedIn](https://linkedin.com/in/rita-jindal) | 🐙 [GitHub](https://github.com/RitaJind)

*Passionate about building scalable, secure, and maintainable software solutions. Experienced in microservices architecture, cloud-native development, and data engineering pipelines.*

---

## 📞 Contact & Support

- **Issues**: [GitHub Issues](https://github.com/RitaJind/user-management-service/issues)
- **Discussions**: [GitHub Discussions](https://github.com/RitaJind/user-management-service/discussions)
- **Email**: your-email@example.com

---

*⭐ **Star this repository** if you found it helpful!*
