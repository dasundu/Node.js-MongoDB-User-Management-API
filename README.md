# 🚀 Node.js MongoDB User Management API

![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)
![Node.js](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)

A comprehensive RESTful API built with **Node.js**, **Express.js**, and **MongoDB** for user management. Features complete CRUD operations with proper error handling and data validation.

## 📋 Table of Contents

- [🌟 Overview](#-overview)
- [✨ Features](#-features)
- [🛠 Tech Stack](#-tech-stack)
- [📋 Prerequisites](#-prerequisites)
- [🚀 Quick Start](#-quick-start)
- [📁 Project Structure](#-project-structure)
- [🔗 API Endpoints](#-api-endpoints)
- [💡 Usage Examples](#-usage-examples)
- [🧪 Testing](#-testing)
- [🗄️ Database Schema](#️-database-schema)
- [🐛 Troubleshooting](#-troubleshooting)
- [🤝 Contributing](#-contributing)

## 🌟 Overview

A modern **User Management API** built with the MEAN/MERN stack backend technologies. This project demonstrates best practices for building RESTful APIs with Node.js and MongoDB, including:

- Clean MVC architecture
- Mongoose ODM for data modeling
- Comprehensive error handling
- Input validation and sanitization
- RESTful routing conventions

Perfect for learning Node.js backend development and MongoDB integration!

## ✨ Features

- 🔐 **Complete CRUD Operations** - Create, Read, Update, Delete users
- 🌐 **RESTful API Design** - Following REST principles and HTTP standards
- 📊 **MongoDB Integration** - NoSQL document-based data storage with Mongoose ODM
- ✅ **Data Validation** - Email uniqueness and required field validation
- 🛡️ **Error Handling** - Comprehensive error responses with proper HTTP status codes
- 📱 **JSON API** - Clean JSON request/response format
- 🔄 **Auto-generated IDs** - MongoDB ObjectId for unique identification
- ⚡ **Async/Await** - Modern JavaScript async programming

## 🛠 Tech Stack

- **Runtime**: Node.js (v14+)
- **Framework**: Express.js
- **Database**: MongoDB
- **ODM**: Mongoose
- **Middleware**: body-parser, express.json()
- **Architecture**: MVC (Model-View-Controller)

## 📋 Prerequisites

Before running this project, make sure you have:

- **Node.js** (v14 or higher) - [Download here](https://nodejs.org/)
- **MongoDB** Community Server - [Download here](https://www.mongodb.com/try/download/community)
- **MongoDB Compass** (Optional but recommended) - [Download here](https://www.mongodb.com/products/compass)
- **Postman** or similar API testing tool - [Download here](https://www.postman.com/)
- **Git** - [Download here](https://git-scm.com/)

## 🚀 Quick Start

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/your-username/nodejs-mongodb-user-api.git
cd nodejs-mongodb-user-api
```

### 2️⃣ Install Dependencies
```bash
npm install
```

### 3️⃣ Start MongoDB
```bash
# Start MongoDB service (varies by OS)
mongod

# macOS (if installed via Homebrew)
brew services start mongodb/brew/mongodb-community

# Linux (systemd)
sudo systemctl start mongod

# Windows
net start MongoDB
```

### 4️⃣ Run the Application
```bash
npm start
# or
node server.js
```

🎉 **Server runs on**: `http://localhost:3000`

### 5️⃣ Verify Installation
```bash
curl http://localhost:3000/users
# Should return: []
```

## 📁 Project Structure

```
nodejs-mongodb-user-api/
├── 📄 server.js              # Main application entry point
├── 📄 package.json           # Project dependencies and scripts
├── 📄 package-lock.json      # Dependency lock file
├── 📁 models/
│   └── 📄 user.js            # User data model (Mongoose schema)
├── 📁 routes/
│   └── 📄 users.js           # User API routes and controllers
├── 📄 .gitignore             # Git ignore file
└── 📄 README.md              # Project documentation
```

### File Descriptions

- **`server.js`**: Express server setup, MongoDB connection, middleware configuration
- **`models/user.js`**: Mongoose schema defining user data structure and validation
- **`routes/users.js`**: API route handlers for all user-related endpoints
- **`package.json`**: Project metadata, dependencies, and npm scripts

## 🔗 API Endpoints

| Method | Endpoint | Description | Request Body | Response |
|--------|----------|-------------|--------------|----------|
| `GET` | `/users` | Get all users | None | Array of users |
| `GET` | `/users/:id` | Get user by ID | None | Single user object |
| `POST` | `/users` | Create new user | User object | Created user |
| `PATCH` | `/users/:id` | Update user | Updated fields | Updated user |
| `DELETE` | `/users/:id` | Delete user | None | Success message |

### Status Codes
- `200` - OK (GET, PATCH, DELETE)
- `201` - Created (POST)
- `400` - Bad Request (Validation errors)
- `404` - Not Found (Invalid ID)
- `500` - Internal Server Error

## 💡 Usage Examples

### Create a User
```bash
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "age": 30,
    "email": "john.doe@example.com"
  }'
```

**Response:**
```json
{
  "_id": "507f1f77bcf86cd799439011",
  "name": "John Doe",
  "age": 30,
  "email": "john.doe@example.com",
  "__v": 0
}
```

### Get All Users
```bash
curl http://localhost:3000/users
```

**Response:**
```json
[
  {
    "_id": "507f1f77bcf86cd799439011",
    "name": "John Doe",
    "age": 30,
    "email": "john.doe@example.com",
    "__v": 0
  }
]
```

### Get User by ID
```bash
curl http://localhost:3000/users/507f1f77bcf86cd799439011
```

### Update a User
```bash
curl -X PATCH http://localhost:3000/users/507f1f77bcf86cd799439011 \
  -H "Content-Type: application/json" \
  -d '{
    "age": 31,
    "name": "John Updated Doe"
  }'
```

### Delete a User
```bash
curl -X DELETE http://localhost:3000/users/507f1f77bcf86cd799439011
```

**Response:**
```json
{
  "message": "User Deleted Successfully",
  "name": "John Updated Doe"
}
```

## 🧪 Testing

### Using Postman
1. Import the provided `postman-collection.json`
2. Set base URL: `http://localhost:3000`
3. Test all CRUD operations

### Using curl
All endpoints can be tested using the curl examples above.

### Sample Test Data
```json
// User 1
{
  "name": "Alice Johnson",
  "age": 28,
  "email": "alice@example.com"
}

// User 2
{
  "name": "Bob Smith",
  "age": 35,
  "email": "bob@example.com"
}

// User 3
{
  "name": "Charlie Brown",
  "age": 25,
  "email": "charlie@example.com"
}
```

### Running Tests
```bash
# Install testing dependencies (if you add them)
npm install --save-dev jest supertest

# Run tests
npm test
```

## 🗄️ Database Schema

### User Document Structure
```javascript
{
  "_id": ObjectId("..."),        // Auto-generated MongoDB ID
  "name": String,                // User's full name
  "age": Number,                 // User's age
  "email": String,               // User's email (unique, required)
  "__v": Number                  // Version key (Mongoose)
}
```

### Mongoose Schema
```javascript
const userSchema = new mongoose.Schema({
  name: String,
  age: Number,
  email: {
    type: String,
    required: true,
    unique: true
  }
});
```

### MongoDB Commands
```javascript
// Connect to database
use myNodeProject

// Find all users
db.users.find()

// Find users older than 25
db.users.find({"age": {"$gt": 25}})

// Find user by email
db.users.findOne({"email": "john@example.com"})

// Update user
db.users.updateOne(
  {"_id": ObjectId("...")},
  {"$set": {"age": 31}}
)

// Delete user
db.users.deleteOne({"_id": ObjectId("...")})

// Count users
db.users.countDocuments()
```

## 🐛 Troubleshooting

### Common Issues

#### MongoDB Connection Error
```
❌ MongooseError: connect ECONNREFUSED 127.0.0.1:27017
```
**Solutions:**
- Start MongoDB service: `mongod`
- Check if MongoDB is running: `ps aux | grep mongod`
- Verify MongoDB port: Default is 27017

#### Port Already in Use
```
❌ Error: listen EADDRINUSE :::3000
```
**Solutions:**
```bash
# Find process using port 3000
lsof -ti:3000

# Kill the process
kill -9 $(lsof -ti:3000)

# Or use different port in server.js
const port = process.env.PORT || 3001;
```

#### Duplicate Email Error
```
❌ MongoServerError: E11000 duplicate key error
```
**Solution:** Use unique email addresses for each user

#### Validation Errors
```
❌ ValidationError: Path `email` is required
```
**Solution:** Include all required fields (email) in POST requests

#### Invalid ObjectId
```
❌ CastError: Cast to ObjectId failed
```
**Solution:** Use valid MongoDB ObjectId format (24 hex characters)

### Debug Commands
```bash
# Check Node.js version
node --version

# Check npm version
npm --version

# Check MongoDB connection
mongosh --eval "db.adminCommand('ismaster')"

# View running processes
ps aux | grep node
ps aux | grep mongod

# Check application logs
tail -f /var/log/mongodb/mongod.log
```

## 🚀 Deployment

### Environment Variables
Create `.env` file:
```env
NODE_ENV=production
PORT=3000
MONGODB_URI=mongodb://localhost:27017/myNodeProject
```

### Package.json Scripts
```json
{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js",
    "test": "jest"
  }
}
```

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🎯 Learning Objectives

After completing this project, you will understand:

- ✅ Node.js server development with Express.js
- ✅ MongoDB document-based data modeling
- ✅ Mongoose ODM for schema definition and validation
- ✅ RESTful API design principles
- ✅ CRUD operations in NoSQL databases
- ✅ Error handling and HTTP status codes
- ✅ Async/await programming patterns
- ✅ MVC architecture in Node.js applications

## 🙏 Acknowledgments

- MongoDB Documentation
- Express.js Guide
- Mongoose Documentation
- Node.js Best Practices

---

⭐ **Star this repo** if it helped you learn Node.js and MongoDB!
