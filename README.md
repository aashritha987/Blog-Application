# Blog Application 📝

A full-stack MERN (MongoDB, Express, React, Node.js) blog application with user authentication, JWT tokens, Redux state management, and comprehensive blog management features.

## 📋 Project Overview

A complete blogging platform featuring:
- User authentication and authorization
- JWT-based secure sessions
- Create, read, update, and delete blog posts
- User profiles and management
- Redux state management
- Responsive UI design
- MongoDB data persistence
- RESTful API architecture

## 🛠️ Tech Stack

### Frontend
- **React** ^18.2.0 - UI library
- **Vite** - Build tool & dev server
- **Redux Toolkit** ^2.3.0 - State management
- **React Router DOM** - Client-side routing
- **React Icons** - Icon library
- **Tailwind CSS** - Utility-first CSS framework
- **Flowbite React** - Component library

### Backend
- **Node.js** - Runtime environment
- **Express** ^4.19.2 - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** ^8.5.1 - MongoDB ODM
- **JWT (jsonwebtoken)** - Token authentication
- **Bcryptjs** - Password hashing
- **Nodemon** - Development auto-reload
- **Dotenv** - Environment variable management

## 📋 Prerequisites

Ensure you have the following installed:
- **Node.js** (v14.0.0 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** - Package manager
- **MongoDB** (v4.0 or higher) - [Download](https://www.mongodb.com/try/download/community)
- **Git** - [Download](https://git-scm.com/)

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/aashritha987/Blog-Application.git
cd Blog-Application
```

### 2. Setup Backend

```bash
npm install
```

#### Configure Backend Environment Variables

Create a `.env` file in the root directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# MongoDB Configuration
MONGODB_URI=mongodb://localhost:27017/blog-app
MONGODB_USER=your_mongodb_user
MONGODB_PASSWORD=your_mongodb_password

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRE=7d

# CORS Configuration
CORS_ORIGIN=http://localhost:5173

# Email Configuration (optional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASSWORD=your_app_password
```

#### Run Backend Server

```bash
# Start development server with auto-reload
npm run dev

# Or start production server
npm start

# Server will run on http://localhost:5000
```

### 3. Setup Frontend

```bash
cd client
npm install
```

#### Configure Frontend Environment Variables

Create a `.env` file in the `client` directory:

```env
# API Configuration
VITE_API_URL=http://localhost:5000/api

# Environment
VITE_ENV=development
```

#### Run Frontend Server

```bash
# From client directory
npm run dev

# Application will open at http://localhost:5173
```

## 📁 Project Structure

```
Blog-Application/
├── api/                         # Backend (Node.js + Express)
│   ├── models/                  # MongoDB schemas
│   │   ├── User.js
│   │   └── Post.js
│   ├── routes/                  # API routes
│   │   ├── auth.js
│   │   └── posts.js
│   ├── middleware/              # Custom middleware
│   │   ├── auth.js
│   │   └── errorHandler.js
│   ├── controllers/             # Route controllers
│   │   ├── authController.js
│   │   └── postController.js
│   ├── config/                  # Configuration
│   │   └── database.js
│   ├── index.js                 # Express server entry
│   ├── .env
│   └── package.json
│
├── client/                      # Frontend (React + Vite)
│   ├── src/
│   │   ├── components/          # React components
│   │   │   ├── Header.jsx
│   │   │   ├── Footer.jsx
│   │   │   └── BlogCard.jsx
│   │   ├── pages/               # Page components
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── CreatePost.jsx
│   │   │   └── PostDetail.jsx
│   │   ├── redux/               # Redux store
│   │   │   ├── slices/
│   │   │   │   ├── authSlice.js
│   │   │   │   └── postSlice.js
│   │   │   └── store.js
│   │   ├── services/            # API services
│   │   │   ├── authService.js
│   │   │   └── postService.js
│   │   ├── styles/              # CSS files
│   │   ├── App.jsx              # Root component
│   │   └── main.jsx             # React entry point
│   ├── public/                  # Static assets
│   ├── .env
│   ├── vite.config.js
│   └── package.json
│
├── .gitignore
└── README.md
```

## 📖 Available Scripts

### Backend Scripts

```bash
# Development server with auto-reload
npm run dev

# Production server
npm start

# Run tests
npm test
```

### Frontend Scripts

```bash
# Development server with hot-reload
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Run linter
npm run lint
```

## 🔑 Key Features

- ✅ User registration and login
- ✅ JWT-based authentication
- ✅ Create new blog posts
- ✅ Edit and delete posts
- ✅ View all posts with pagination
- ✅ Search and filter posts
- ✅ User profiles
- ✅ Redux state management
- ✅ Responsive design
- ✅ Error handling and validation
- ✅ Secure password hashing
- ✅ Token refresh mechanism

## 🔌 API Endpoints

### Authentication
```
POST   /api/auth/register     - Register new user
POST   /api/auth/login        - User login
POST   /api/auth/logout       - User logout
POST   /api/auth/refresh      - Refresh JWT token
GET    /api/auth/me           - Get current user
```

### Blog Posts
```
GET    /api/posts             - Get all posts
GET    /api/posts/:id         - Get post by ID
POST   /api/posts             - Create new post (auth required)
PATCH  /api/posts/:id         - Update post (auth required)
DELETE /api/posts/:id         - Delete post (auth required)
GET    /api/posts/search?q=   - Search posts
```

### Users
```
GET    /api/users/:id         - Get user profile
PATCH  /api/users/:id         - Update user profile (auth required)
```

## 🗄️ Database Schema

### User Model
```javascript
{
  _id: ObjectId,
  name: String,
  email: String (unique),
  password: String (hashed),
  profilePicture: String,
  bio: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Post Model
```javascript
{
  _id: ObjectId,
  title: String,
  content: String,
  author: ObjectId (ref: User),
  tags: [String],
  category: String,
  featured: Boolean,
  views: Number,
  createdAt: Date,
  updatedAt: Date
}
```

## 🔐 Authentication Flow

1. User registers with email and password
2. Password is hashed using bcryptjs
3. User credentials stored in MongoDB
4. On login, password verified and JWT token generated
5. Token sent to frontend and stored in Redux/localStorage
6. Token included in Authorization header for protected routes
7. Backend validates token on protected endpoints
8. Token auto-refreshes before expiration

## 🚀 Deployment

### Deploy Frontend to Vercel

```bash
npm install -g vercel
cd client
vercel
```

### Deploy Frontend to Netlify

```bash
cd client
npm run build
# Drag and drop the 'dist' folder to Netlify
```

### Deploy Backend to Heroku

```bash
# Install Heroku CLI
npm install -g heroku

# Login to Heroku
heroku login

# Create app
heroku create your-blog-app-name

# Set environment variables
heroku config:set JWT_SECRET=your_secret_key
heroku config:set MONGODB_URI=your_mongodb_uri

# Deploy
git push heroku main
```

### Deploy Backend to Railway

```bash
# Install Railway CLI
npm install -g @railway/cli

# Login to Railway
railway login

# Initialize and deploy
railway init
railway up
```

## 🐛 Troubleshooting

### Issue: "Cannot find module 'mongoose'"
**Solution:** Reinstall backend dependencies:
```bash
rm -rf node_modules package-lock.json
npm install
```

### Issue: "MongoDB connection refused"
**Solution:** Ensure MongoDB is running:
```bash
# macOS
brew services start mongodb-community

# Windows
net start MongoDB

# Linux
sudo systemctl start mongod
```

### Issue: "JWT token expired"
**Solution:** Login again to get a new token. The app should handle automatic token refresh.

### Issue: CORS errors when calling API
**Solution:** Verify `CORS_ORIGIN` in backend `.env`:
```env
CORS_ORIGIN=http://localhost:5173
```

### Issue: Port 5000 or 5173 already in use
**Solution:** Kill the process or use different port:
```bash
# macOS/Linux - Kill process on port 5000
lsof -i :5000
kill -9 <PID>

# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Or change PORT in backend .env
# Or change PORT in vite.config.js for frontend
```

### Issue: "Cannot POST /api/posts" - 401 Unauthorized
**Solution:** Ensure you're sending the JWT token in the Authorization header:
```javascript
headers: {
  'Authorization': `Bearer ${token}`
}
```

## 📚 Resources

- [React Documentation](https://react.dev)
- [Redux Toolkit](https://redux-toolkit.js.org/)
- [Vite Documentation](https://vitejs.dev/)
- [Express.js Guide](https://expressjs.com/)
- [MongoDB Manual](https://docs.mongodb.com/manual/)
- [JWT Introduction](https://jwt.io/introduction)
- [Tailwind CSS](https://tailwindcss.com/)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the ISC License.

## 👤 Author

**Aashritha Danthala**
- GitHub: [@aashritha987](https://github.com/aashritha987)
- Email: aashrithadanthala03@gmail.com

## 📞 Support

For issues and feature requests, please open an issue on [GitHub](https://github.com/aashritha987/Blog-Application/issues).
