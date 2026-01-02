# Quick Start Guide

## 🚀 Get Started in 5 Minutes

### Step 1: Install Dependencies

```bash
# Install server dependencies
cd server
npm install

# Install client dependencies
cd ../client
npm install
```

### Step 2: Set Up Environment Variables

Create `server/.env` file:

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/eat-and-out
JWT_SECRET=your_super_secret_jwt_key_change_this
NODE_ENV=development
```

### Step 3: Start MongoDB

Make sure MongoDB is running on your system.

**Windows:**
```bash
# If MongoDB is installed as a service, it should start automatically
# Or start manually:
net start MongoDB
```

**Mac/Linux:**
```bash
# Start MongoDB service
sudo systemctl start mongod
# Or
mongod
```

### Step 4: Create Admin User

```bash
cd server
node seed.js
```

This creates an admin user:
- Email: `admin@eatandout.com`
- Password: `admin123`

⚠️ **Change the password after first login!**

### Step 5: Start the Application

**Terminal 1 - Backend:**
```bash
cd server
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd client
npm run dev
```

### Step 6: Access the Application

- **Website**: http://localhost:3000
- **Admin Panel**: http://localhost:3000/admin/login
- **API**: http://localhost:5000/api

## 📝 Next Steps

1. **Update Google Maps**: Edit `client/src/pages/Contact.jsx` and replace the Google Maps embed URL with your actual restaurant location coordinates.

2. **Add Menu Items**: 
   - Login to admin panel
   - Go to Menu Items tab
   - Click "Add New Item"
   - Fill in the form and upload images

3. **Customize Content**: 
   - Update restaurant information in About page
   - Add more images to Gallery
   - Customize colors in `tailwind.config.js`

## 🎨 Customization

### Change Colors

Edit `client/tailwind.config.js`:

```javascript
colors: {
  primary: {
    dark: '#0a0a0a',      // Background dark
    black: '#1a1a1a',     // Cards/Components
    orange: '#ff6b35',    // Primary accent
    red: '#d62828',       // Hover states
    cream: '#fef5e7',     // Text light
    gold: '#f4a261'       // Accent
  }
}
```

### Update Restaurant Info

Edit these files:
- `client/src/pages/About.jsx` - About content
- `client/src/components/Footer.jsx` - Contact info
- `client/src/pages/Contact.jsx` - Contact details

## 🐛 Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running
- Check `MONGODB_URI` in `.env`
- For MongoDB Atlas, verify connection string

### Images Not Loading
- Check `client/public/images/` folder
- Verify image paths in components
- Check browser console for 404 errors

### Admin Login Not Working
- Run `node server/seed.js` to create admin user
- Check JWT_SECRET in `.env`
- Verify MongoDB connection

### Port Already in Use
- Change PORT in `server/.env`
- Update proxy in `client/vite.config.js`

## 📚 Full Documentation

See `README.md` for complete documentation.

