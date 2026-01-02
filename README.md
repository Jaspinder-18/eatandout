# Eat & Out - Premium Restaurant Website

A modern, fully animated restaurant website built with the MERN stack, featuring Three.js 3D graphics, GSAP animations, and a complete admin panel.

## 🎯 Features

- **Modern UI/UX**: Dark theme with warm color palette (black, orange, red, cream)
- **3D Graphics**: Three.js rotating food model in hero section
- **Smooth Animations**: GSAP ScrollTrigger animations throughout
- **Responsive Design**: Mobile-first, fully responsive on all devices
- **Menu Management**: Dynamic menu with categories (Punjabi, Chinese, Fast Food, North Indian)
- **Admin Panel**: Secure JWT-based admin dashboard for managing menu items
- **Contact Form**: Integrated contact form with backend storage
- **Image Gallery**: Animated gallery with modal view
- **Google Maps**: Embedded map showing restaurant location

## 🛠️ Tech Stack

### Frontend
- **React 18** with Vite
- **Tailwind CSS** for styling
- **GSAP** (ScrollTrigger, timelines) for animations
- **Three.js** via @react-three/fiber and @react-three/drei
- **React Router** for navigation
- **Axios** for API calls

### Backend
- **Node.js** with Express.js
- **MongoDB** with Mongoose
- **JWT** for authentication
- **Multer** for file uploads
- **Bcrypt** for password hashing

## 📁 Project Structure

```
eat-and-out/
├── client/                 # Frontend React application
│   ├── public/
│   │   └── images/        # Restaurant images
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── pages/         # Page components
│   │   ├── context/       # React context (Auth)
│   │   ├── utils/         # Utility functions
│   │   └── styles/        # Global styles
│   ├── package.json
│   └── vite.config.js
├── server/                 # Backend Express application
│   ├── config/            # Database configuration
│   ├── models/            # MongoDB models
│   ├── routes/            # API routes
│   ├── middleware/        # Auth middleware
│   ├── uploads/           # Uploaded images
│   ├── package.json
│   └── server.js
└── README.md
```

## 🚀 Setup Instructions

### Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or MongoDB Atlas)
- npm or yarn

### 1. Clone and Install Dependencies

```bash
# Install server dependencies
cd server
npm install

# Install client dependencies
cd ../client
npm install
```

### 2. Environment Variables

#### Server (.env file in `server/` directory)

Create a `.env` file in the `server/` directory:

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/eat-and-out
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
NODE_ENV=development
```

**For MongoDB Atlas:**
```env
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/eat-and-out
```

#### Client (Optional - for production)

Create a `.env` file in the `client/` directory if you need to change the API URL:

```env
VITE_API_URL=http://localhost:5000
```

### 3. Create Admin User

Run the seed script to create an admin user:

```bash
cd server
node seed.js
```

Or manually create an admin user using MongoDB:

```javascript
// In MongoDB shell or Compass
use eat-and-out
db.admins.insertOne({
  email: "admin@eatandout.com",
  password: "$2a$10$..." // Hashed password (use bcrypt)
})
```

**Default Admin Credentials** (after running seed.js):
- Email: `admin@eatandout.com`
- Password: `admin123` (change this in production!)

### 4. Start the Application

#### Terminal 1 - Backend Server

```bash
cd server
npm run dev
```

Server will run on `http://localhost:5000`

#### Terminal 2 - Frontend Client

```bash
cd client
npm run dev
```

Client will run on `http://localhost:3000`

## 📝 API Endpoints

### Public Endpoints

- `GET /api/menu` - Get all menu items
- `GET /api/menu?category=Punjabi` - Get menu items by category
- `GET /api/menu/:id` - Get single menu item
- `POST /api/contact` - Submit contact form
- `POST /api/auth/login` - Admin login

### Protected Endpoints (Require JWT Token)

- `POST /api/menu` - Create menu item
- `PUT /api/menu/:id` - Update menu item
- `DELETE /api/menu/:id` - Delete menu item
- `GET /api/contact` - Get all contact messages
- `PUT /api/contact/:id/read` - Mark message as read

## 🎨 Pages

1. **Home** (`/`) - Hero section with 3D model, about section, popular dishes
2. **Menu** (`/menu`) - Dynamic menu with category filters
3. **About** (`/about`) - Restaurant information and values
4. **Gallery** (`/gallery`) - Image gallery with modal view
5. **Contact** (`/contact`) - Contact form and Google Maps
6. **Admin Login** (`/admin/login`) - Admin authentication
7. **Admin Dashboard** (`/admin/dashboard`) - Menu and message management

## 🎬 Animations

### GSAP Features Used

- **ScrollTrigger**: Section reveals on scroll
- **Timelines**: Sequential animations
- **Parallax**: Background elements movement
- **Stagger**: Sequential item animations
- **Transform**: Scale, rotation, translate effects

### Three.js Features

- **3D Food Model**: Rotating burger/plate in hero
- **Auto-rotation**: Smooth camera movement
- **Lighting**: Ambient, directional, and point lights
- **Environment**: Sunset preset for warm lighting

## 🖼️ Images

Restaurant images are located in `client/public/images/`:
- `MAINPIC.png` - Main restaurant exterior
- `MAINPIC1.png` - Restaurant image 1
- `MAINPIC2.png` - Restaurant image 2
- `MAINPIC3.png` - Restaurant image 3

## 🔒 Security

- JWT tokens for admin authentication
- Password hashing with bcrypt
- Protected routes on frontend and backend
- Input validation on forms
- File upload restrictions (images only, 5MB max)

## 🚀 Production Deployment

### Build Frontend

```bash
cd client
npm run build
```

The `dist/` folder contains the production build.

### Environment Variables

Update `.env` files with production values:
- Use strong JWT_SECRET
- Use production MongoDB URI
- Update API URLs if needed

### Serve Static Files

In production, serve the `client/dist` folder and configure your server to handle API routes.

## 📦 NPM Packages

### Server Dependencies
- express
- mongoose
- dotenv
- bcryptjs
- jsonwebtoken
- cors
- multer
- express-validator

### Client Dependencies
- react
- react-dom
- react-router-dom
- axios
- gsap
- @react-three/fiber
- @react-three/drei
- three
- framer-motion (optional)
- tailwindcss
- vite

## 🐛 Troubleshooting

### MongoDB Connection Issues
- Ensure MongoDB is running
- Check MONGODB_URI in `.env`
- Verify network access for MongoDB Atlas

### Images Not Loading
- Check image paths in `client/public/images/`
- Verify server uploads directory exists
- Check CORS settings

### Admin Login Fails
- Ensure admin user exists in database
- Check JWT_SECRET is set
- Verify password hashing

## 📄 License

This project is created for Eat & Out restaurant.

## 👨‍💻 Development

For development:
- Backend: `npm run dev` (uses nodemon)
- Frontend: `npm run dev` (uses Vite HMR)

## 📞 Support

For issues or questions, contact the development team.

---

**Built with ❤️ for Eat & Out Restaurant**

