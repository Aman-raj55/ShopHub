# 🛒 ShopHub - MERN E-Commerce Application

A full-stack e-commerce platform built with the MERN stack (MongoDB, Express, React, Node.js). This project features user authentication, shopping cart functionality, and complete order management.

![MERN Stack](https://img.shields.io/badge/Stack-MERN-green)
![MongoDB](https://img.shields.io/badge/MongoDB-4.4+-green)
![Express](https://img.shields.io/badge/Express-4.x-blue)
![React](https://img.shields.io/badge/React-18.x-blue)
![Node](https://img.shields.io/badge/Node-14.x+-green)

---

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Usage Guide](#usage-guide)
- [Troubleshooting](#troubleshooting)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features

### User Features
- **Browse Products**: View products without authentication
- **Search Functionality**: Real-time product search
- **Shopping Cart**: Add/remove items, adjust quantities
- **User Authentication**: Secure registration and login with JWT
- **Checkout Process**: Complete order placement with shipping details
- **Order History**: View all past orders

### Technical Features
- **RESTful API**: Clean API architecture
- **JWT Authentication**: Secure token-based authentication
- **Password Hashing**: bcrypt encryption for user passwords
- **Responsive Design**: Amazon-inspired UI that works on all devices
- **MongoDB Integration**: NoSQL database for flexible data storage
- **CORS Enabled**: Seamless frontend-backend communication

---

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI library
- **Axios** - HTTP client for API requests
- **CSS3** - Styling

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling

### Security & Authentication
- **JWT (jsonwebtoken)** - Token-based authentication
- **bcryptjs** - Password hashing

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v14.x or higher) - [Download here](https://nodejs.org/)
- **MongoDB** (v4.4 or higher) - [Installation guide](#mongodb-installation)
- **npm** (comes with Node.js)
- **Git** (optional, for cloning)

### MongoDB Installation

#### Windows
1. Download MongoDB Community Server from [MongoDB Download Center](https://www.mongodb.com/try/download/community)
2. Run the installer (.msi file)
3. Choose "Complete" installation
4. Install MongoDB as a Service (checked by default)
5. MongoDB will start automatically

#### macOS
```bash
# Install using Homebrew
brew tap mongodb/brew
brew install mongodb-community

# Start MongoDB
brew services start mongodb-community

# Verify installation
mongosh
```

#### Linux (Ubuntu/Debian)
```bash
# Import MongoDB public GPG key
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -

# Add MongoDB repository
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

# Install MongoDB
sudo apt-get update
sudo apt-get install -y mongodb-org

# Start MongoDB
sudo systemctl start mongod
sudo systemctl enable mongod

# Verify installation
mongosh
```

---

## 🚀 Installation

### Step 1: Clone or Download the Project

```bash
# Clone the repository (if using Git)
git clone <your-repo-url>
cd mern-ecommerce

# Or create the project structure manually
mkdir mern-ecommerce
cd mern-ecommerce
```

### Step 2: Set Up Backend

```bash
# Create and navigate to backend folder
mkdir backend
cd backend

# Initialize npm
npm init -y

# Install backend dependencies
npm install express mongoose cors dotenv bcryptjs jsonwebtoken

# Create server.js file
# (Copy the server.js code provided in the project)
```

### Step 3: Set Up Frontend

```bash
# Navigate back to root directory
cd ..

# Create React app
npx create-react-app frontend

# Navigate to frontend folder
cd frontend

# Install frontend dependencies
npm install axios

# Replace src/App.js and src/App.css with provided files
```

### Step 4: Verify Installation

Your project structure should look like this:

```
mern-ecommerce/
├── backend/
│   ├── node_modules/
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
└── frontend/
    ├── node_modules/
    ├── public/
    ├── src/
    │   ├── App.js
    │   ├── App.css
    │   └── index.js
    ├── package.json
    └── package-lock.json
```

---

## 🎯 Running the Application

### Step 1: Start MongoDB

Ensure MongoDB is running:

```bash
# Check MongoDB status
mongosh

# If connection is successful, you'll see:
# Connected to: mongodb://localhost:27017
```

If MongoDB is not running:
- **Windows**: MongoDB should auto-start as a service
- **macOS**: `brew services start mongodb-community`
- **Linux**: `sudo systemctl start mongod`

### Step 2: Start Backend Server

Open a terminal window:

```bash
cd backend
node server.js
```

You should see:
```
Server running on http://localhost:5000
MongoDB Connected
```

**Important**: Seed the database with sample products by visiting:
```
http://localhost:5000/api/seed
```

You should see:
```json
{
  "message": "Database seeded successfully",
  "count": 8
}
```

### Step 3: Start Frontend Application

Open a **NEW** terminal window (keep backend running):

```bash
cd frontend
npm start
```

The React app will automatically open in your browser at:
```
http://localhost:3000
```

---

## 📁 Project Structure

```
mern-ecommerce/
│
├── backend/
│   ├── server.js                 # Express server & all backend logic
│   │   ├── MongoDB Connection
│   │   ├── Mongoose Schemas (User, Product, Order)
│   │   ├── Authentication Middleware
│   │   ├── API Routes
│   │   └── Database Seeding
│   └── package.json              # Backend dependencies
│
└── frontend/
    ├── src/
    │   ├── App.js                # All React components & logic
    │   │   ├── State Management
    │   │   ├── API Integration
    │   │   ├── Page Components
    │   │   └── UI Rendering
    │   ├── App.css               # All styling
    │   └── index.js              # React entry point
    └── package.json              # Frontend dependencies
```

---

## 🔌 API Endpoints

### Authentication

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/register` | Register new user | No |
| POST | `/api/login` | Login user | No |
| GET | `/api/user` | Get current user | Yes |

### Products

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/products` | Get all products | No |
| GET | `/api/products/:id` | Get single product | No |
| GET | `/api/seed` | Seed database with products | No |

### Orders

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/orders` | Create new order | Yes |
| GET | `/api/orders` | Get user's orders | Yes |

### Request Examples

#### Register User
```javascript
POST http://localhost:5000/api/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

#### Login User
```javascript
POST http://localhost:5000/api/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "password123"
}
```

#### Create Order
```javascript
POST http://localhost:5000/api/orders
Authorization: Bearer <your-jwt-token>
Content-Type: application/json

{
  "items": [
    {
      "productId": "product_id_here",
      "name": "Product Name",
      "price": 49.99,
      "quantity": 2
    }
  ],
  "totalAmount": 99.98,
  "shippingAddress": {
    "street": "123 Main St",
    "city": "New York",
    "state": "NY",
    "zipCode": "10001",
    "country": "USA"
  }
}
```

---

## 📖 Usage Guide

### 1. Browse Products
- Open the app at `http://localhost:3000`
- Products are displayed on the homepage
- Use the search bar to filter products

### 2. Add Items to Cart
- Click "Add to Cart" on any product
- Cart icon shows the number of items
- Click cart icon to view cart

### 3. Register/Login
- Click "Register" to create a new account
- Or click "Login" if you already have an account
- Fill in the required information

### 4. Checkout Process
1. Add items to cart
2. Click "Proceed to Checkout"
3. If not logged in, you'll be redirected to login
4. Fill in shipping address
5. Review your order
6. Click "Place Order"

### 5. View Order History
- Click "Orders" in the header (after logging in)
- See all your past orders with details

---

## 🐛 Troubleshooting

### Common Issues and Solutions

#### 1. **MongoDB Connection Error**

**Error**: `MongooseServerSelectionError: connect ECONNREFUSED 127.0.0.1:27017`

**Solution**:
```bash
# Check if MongoDB is running
mongosh

# If not running, start it:
# Windows: Check Services or reinstall as service
# macOS: brew services start mongodb-community
# Linux: sudo systemctl start mongod
```

#### 2. **Products Not Showing**

**Solution**: Seed the database
```bash
# Visit in browser:
http://localhost:5000/api/seed
```

#### 3. **CORS Error**

**Error**: `Access to XMLHttpRequest blocked by CORS policy`

**Solution**: 
- Ensure backend is running on port 5000
- Verify `cors` is installed: `npm install cors`
- Check that `app.use(cors())` is in server.js

#### 4. **Port Already in Use**

**Error**: `Error: listen EADDRINUSE: address already in use :::5000`

**Solution**:
```bash
# Find and kill the process using the port
# Windows:
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# macOS/Linux:
lsof -ti:5000 | xargs kill -9

# Or change the port in server.js
const PORT = 5001; // Change to different port
```

#### 5. **Can't Type in Input Fields**

**Solution**: This has been fixed in the latest version. Ensure you're using the most recent App.js file.

#### 6. **JWT Token Invalid**

**Solution**: Clear localStorage and login again
```javascript
// In browser console:
localStorage.clear();
```

#### 7. **npm Install Fails**

**Solution**:
```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and package-lock.json
rm -rf node_modules package-lock.json

# Reinstall
npm install
```

---

## 🔐 Security Notes

### Current Implementation
- Passwords are hashed using bcrypt (10 salt rounds)
- JWT tokens expire after 7 days
- Protected routes require valid JWT token
- CORS is enabled for development

### Production Recommendations
1. **Use Environment Variables**:
   ```bash
   # Create .env file in backend folder
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/ecommerce
   JWT_SECRET=your_very_secure_random_string_here
   NODE_ENV=production
   ```

2. **Update server.js to use .env**:
   ```javascript
   require('dotenv').config();
   
   const PORT = process.env.PORT || 5000;
   const JWT_SECRET = process.env.JWT_SECRET;
   const MONGODB_URI = process.env.MONGODB_URI;
   ```

3. **Implement HTTPS** in production
4. **Add rate limiting** to prevent abuse
5. **Implement input validation** and sanitization
6. **Add CSRF protection**
7. **Set secure cookie options** for tokens

---

## 🚀 Future Enhancements

### Planned Features
- [ ] Payment gateway integration (Stripe/PayPal)
- [ ] Product reviews and ratings
- [ ] Admin dashboard for managing products
- [ ] Product categories and filters
- [ ] Wishlist functionality
- [ ] Email notifications for orders
- [ ] Password reset functionality
- [ ] Social media authentication
- [ ] Image upload for products
- [ ] Inventory management
- [ ] Discount codes and coupons
- [ ] Order tracking
- [ ] Multiple shipping addresses

### Technical Improvements
- [ ] Add TypeScript for type safety
- [ ] Implement Redis for caching
- [ ] Add comprehensive testing (Jest, React Testing Library)
- [ ] Implement pagination for products
- [ ] Add loading states and error boundaries
- [ ] Optimize images with lazy loading
- [ ] Add PWA support
- [ ] Implement real-time notifications with Socket.io
- [ ] Deploy to cloud (AWS, Heroku, Vercel)

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/AmazingFeature`
3. **Commit your changes**: `git commit -m 'Add some AmazingFeature'`
4. **Push to the branch**: `git push origin feature/AmazingFeature`
5. **Open a Pull Request**

### Development Guidelines
- Follow the existing code style
- Write meaningful commit messages
- Test your changes thoroughly
- Update documentation as needed

---

## 📝 License

This project is licensed under the MIT License - see below for details:

```
MIT License

Copyright (c) 2024 ShopHub

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Troubleshooting](#troubleshooting) section
2. Search existing [GitHub Issues](https://github.com/yourusername/shophub/issues)
3. Create a new issue with detailed information

---

## 🙏 Acknowledgments

- Design inspired by Amazon's e-commerce platform
- Product images from [Unsplash](https://unsplash.com)
- Built with the MERN stack
- Icons and emojis for enhanced UX

---

## 📊 Project Status

**Current Version**: 1.0.0  
**Status**: Active Development  
**Last Updated**: January 2025

---

## 👨‍💻 Author

Created with ❤️ for learning and demonstration purposes.

---

## 🌟 Show Your Support

If you found this project helpful, please consider giving it a ⭐!

---

**Happy Coding! 🚀**