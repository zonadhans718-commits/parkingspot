# 🅿️ Parkify - MERN Stack Parking Management System

A full-stack web application that helps users find and book parking spots in busy cities across India.

![MERN Stack](https://img.shields.io/badge/MERN-Stack-green)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-brightgreen)
![Express.js](https://img.shields.io/badge/Express.js-Backend-blue)
![React](https://img.shields.io/badge/React-Frontend-61DAFB)
![Node.js](https://img.shields.io/badge/Node.js-Runtime-green)

---

## 🚀 Features

### 🔐 **User Authentication**
- Secure JWT-based authentication
- Register and login functionality
- Protected routes for bookings
- Auto-logout on token expiration

### 🔍 **Smart Search System**
- **Autocomplete suggestions** as you type
- **Recent searches** saved locally (last 5)
- **Typo tolerance** - handles common misspellings
- **Alternate city names** (Bengaluru/Bangalore, Bombay/Mumbai, etc.)
- **42+ typo variations** supported
- **Fuzzy matching** algorithm

### 🅿️ **Parking Management**
- Search parking spots by city
- View detailed parking information
- Real-time slot availability
- Price per hour display
- Amenities listing
- Google Maps integration

### 📅 **Booking System**
- Book parking for specific date/time
- **Phone number validation** (accepts +91 format)
- **Vehicle number validation** (Indian format)
- **Past date prevention** - can't book past times
- **Time overlap detection** - prevents double booking
- Calculate total price automatically
- View all bookings history
- Cancel active bookings

### 🗺️ **Navigation**
- **Get Directions** button
- Opens Google Maps with exact coordinates
- Works on desktop and mobile

### 🌙 **Dark Mode**
- Full dark mode support
- Saves user preference
- Auto-detects system theme
- Smooth transitions

### ✨ **Enhanced UX**
- Better loading states with spinners
- Network error handling
- Retry buttons on errors
- Input validation with clear messages
- Responsive design (mobile + desktop)
- Professional error messages

---

## 🛠️ Tech Stack

### **Frontend**
- **React.js** 18 - UI library
- **React Router** v6 - Navigation
- **Axios** - HTTP requests
- **TailwindCSS** - Styling
- **Vite** - Build tool
- **Context API** - State management

### **Backend**
- **Node.js** - Runtime
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **bcryptjs** - Password hashing

---

## 📋 Prerequisites

Before you begin, ensure you have:
- **Node.js** (v16 or higher) - [Download](https://nodejs.org/)
- **MongoDB** (v5 or higher) - [Download](https://www.mongodb.com/try/download/community)
- **npm** or **yarn** package manager
- **Git** for cloning the repository

---

## 🔧 Installation & Setup

### **1. Clone the Repository**

```bash
git clone <your-repo-url>
cd parkify
```

---

### **2. Backend Setup**

#### **Install Dependencies**
```bash
cd backend
npm install
```

#### **Environment Variables**
Create a `.env` file in the `backend` folder:

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/parking-spot-finder
JWT_SECRET=parkify_secret_key_2024_change_in_production
JWT_EXPIRE=7d
```

**For MongoDB Atlas (Cloud):**
```env
PORT=5000
MONGODB_URI=mongodb+srv://username:password@cluster0.xxxxx.mongodb.net/parkify?retryWrites=true&w=majority
JWT_SECRET=parkify_secret_key_2024_change_in_production
JWT_EXPIRE=7d
```

#### **Start MongoDB**

**Windows:**
```bash
# MongoDB runs as a service automatically
# Or manually: mongod
```

**Mac/Linux:**
```bash
sudo service mongod start
# Or: brew services start mongodb-community
```

#### **Seed Database**
```bash
node seedData.js
```

**Expected Output:**
```
✅ MongoDB Connected Successfully
🗑️  Old parking spots deleted
✅ Sample parking spots created (43 spots)
✅ Admin user created (admin@parking.com / admin123)
✅ Test user created (user@test.com / user123)
```

#### **Start Backend Server**
```bash
npm start
```

**Expected Output:**
```
🚀 Server running on port 5000
✅ MongoDB Connected Successfully
```

---

### **3. Frontend Setup**

Open a **new terminal window**.

#### **Install Dependencies**
```bash
cd frontend
npm install
```

#### **Start Frontend**
```bash
npm run dev
```

**Expected Output:**
```
  VITE v5.0.8  ready in 500 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: use --host to expose
```

---

## 🎯 Access the Application

Open your browser and navigate to:
```
http://localhost:3000
```

---

## 👥 Test Accounts

### **User Account**
- **Email:** `user@test.com`
- **Password:** `user123`
- **Role:** Regular User

### **Admin Account**
- **Email:** `admin@parking.com`
- **Password:** `admin123`
- **Role:** Administrator

---

## 🗺️ Cities & Parking Spots

### **Available Cities (43 Total Parking Spots)**

| City | Spots | Price Range | Total Capacity |
|------|-------|-------------|----------------|
| **Bangalore** | 3 | ₹40-60/hour | 330 slots |
| **Delhi** | 3 | ₹50-80/hour | 620 slots |
| **Mumbai** | 6 | ₹50-100/hour | 2,250 slots |
| **Pune** | 5 | ₹30-60/hour | 1,000 slots |
| **Hyderabad** | 5 | ₹25-60/hour | 1,370 slots |
| **Chennai** | 5 | ₹30-60/hour | 1,400 slots |
| **Mangalore** | 6 | ₹20-40/hour | 830 slots |
| **Calicut** | 5 | ₹20-40/hour | 780 slots |

**Total:** 8,580 parking slots across 8 major Indian cities!

---

## 🔍 Search Features

### **Supported City Name Variations**

Our smart search recognizes:

| Official Name | Alternate Names | Common Typos |
|---------------|-----------------|--------------|
| **Bangalore** | Bengaluru | bangalor, bangalure, banglore |
| **Delhi** | Dilli | delli, deli, dehli |
| **Mumbai** | Bombay | mumbay, mumbi, bombai |
| **Chennai** | Madras | chenai, chnnai, madras |
| **Calicut** | Kozhikode | calcut, kozikode, kozhikod |
| **Mangalore** | Mangaluru | mangalor, mangalure |
| **Pune** | Poona | poona, puna, punee |
| **Hyderabad** | - | hydrabad, haidarabad |

**Total: 42+ typo variations supported!**

---

## 📁 Project Structure

```
parkify/
├── backend/
│   ├── config/
│   │   └── db.js                 # MongoDB connection
│   ├── controllers/
│   │   ├── authController.js     # Authentication logic
│   │   ├── parkingController.js  # Parking CRUD operations
│   │   └── bookingController.js  # Booking management
│   ├── middleware/
│   │   └── auth.js               # JWT verification
│   ├── models/
│   │   ├── User.js               # User schema
│   │   ├── ParkingSpot.js        # Parking schema
│   │   └── Booking.js            # Booking schema
│   ├── routes/
│   │   ├── authRoutes.js         # Auth endpoints
│   │   ├── parkingRoutes.js      # Parking endpoints
│   │   └── bookingRoutes.js      # Booking endpoints
│   ├── .env                      # Environment variables
│   ├── server.js                 # Express server
│   ├── seedData.js               # Database seeding
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── components/
    │   │   ├── Navbar.jsx          # Navigation bar
    │   │   └── PrivateRoute.jsx    # Protected routes
    │   ├── context/
    │   │   ├── AuthContext.jsx     # Auth state management
    │   │   └── ThemeContext.jsx    # Dark mode management
    │   ├── pages/
    │   │   ├── Home.jsx            # Homepage with search
    │   │   ├── Login.jsx           # Login page
    │   │   ├── Register.jsx        # Registration page
    │   │   ├── ParkingList.jsx     # Search results
    │   │   ├── BookingPage.jsx     # Booking form
    │   │   └── MyBookings.jsx      # User bookings
    │   ├── services/
    │   │   └── api.js              # Axios configuration
    │   ├── App.jsx                 # Main app component
    │   ├── main.jsx                # Entry point
    │   └── index.css               # Global styles
    ├── index.html
    ├── vite.config.js
    ├── tailwind.config.js
    ├── postcss.config.js
    └── package.json
```

---

## 🔑 API Endpoints

### **Authentication**
```
POST   /api/auth/register      # Register new user
POST   /api/auth/login         # Login user
GET    /api/auth/me            # Get current user (Protected)
```

### **Parking Spots**
```
GET    /api/parkings/:city               # Get all parkings in a city
GET    /api/parkings/detail/:id          # Get single parking spot
POST   /api/parkings                     # Create parking (Admin only)
PUT    /api/parkings/:id                 # Update parking (Admin only)
DELETE /api/parkings/:id                 # Delete parking (Admin only)
```

### **Bookings**
```
POST   /api/bookings                     # Create booking (Protected)
GET    /api/bookings/user/:id            # Get user bookings (Protected)
GET    /api/bookings/:id                 # Get single booking (Protected)
PUT    /api/bookings/:id/cancel          # Cancel booking (Protected)
```

---

## 💡 Usage Guide

### **1. Register/Login**
```
1. Go to Register page
2. Enter: Name, Email, Password
3. Or use test account: user@test.com / user123
```

### **2. Search for Parking**
```
1. Type city name in search box
2. See autocomplete suggestions
3. Click suggestion or press Enter
4. View all parking spots in that city
```

### **3. Book a Parking Spot**
```
1. Click "Book Now" on any parking
2. Enter phone number (supports +91 format)
3. Enter vehicle number (e.g., KA01AB1234)
4. Select From and To date/time
5. See total price calculated
6. Click "Confirm Booking"
```

### **4. View Your Bookings**
```
1. Click "My Bookings" in navbar
2. See all your bookings
3. Click "Get Directions" for Google Maps
4. Cancel active bookings if needed
```

### **5. Toggle Dark Mode**
```
1. Click moon/sun icon in navbar
2. Preference saved automatically
3. Works across all pages
```

---

## 🧪 Testing

### **Test Phone Number Formats**
```javascript
✅ 9876543210
✅ +91 9876543210
✅ +919876543210
✅ 919876543210
✅ +91-9876543210
```

### **Test Vehicle Numbers**
```javascript
✅ KA01AB1234
✅ ka01ab1234 (auto-uppercase)
✅ KA-01-AB-1234
✅ KA 01 AB 1234
```

### **Test Search Typos**
```javascript
Type: "bengaluru" → Find: Bangalore ✅
Type: "bombay" → Find: Mumbai ✅
Type: "madras" → Find: Chennai ✅
Type: "delli" → Find: Delhi ✅
Type: "kozhikode" → Find: Calicut ✅
```

### **Test Time Overlap**
```javascript
1. Book Parking A: 10 AM - 2 PM
2. Try booking Parking B: 11 AM - 1 PM
3. Should show error: "You already have a booking..."
```

---

## 🐛 Troubleshooting

### **Issue 1: MongoDB Connection Error**
```
Error: connect ECONNREFUSED 127.0.0.1:27017
```
**Solution:**
```bash
# Windows
services.msc → Start "MongoDB"

# Mac
brew services start mongodb-community

# Linux
sudo systemctl start mongod
```

### **Issue 2: Port Already in Use**
```
Error: Port 5000 is already in use
```
**Solution:**
```bash
# Kill the process
# Windows: netstat -ano | findstr :5000
# Mac/Linux: lsof -ti:5000 | xargs kill
```

### **Issue 3: CORS Error**
```
Error: CORS policy blocked
```
**Solution:**
- Make sure backend is running on port 5000
- Check `vite.config.js` proxy settings
- Restart both servers

### **Issue 4: Blank My Bookings Page**
```
Blank white page
```
**Solution:**
```
1. Check if you're logged in (see navbar)
2. Login with: user@test.com / user123
3. Make a test booking first
4. Then check My Bookings
5. Check browser console (F12) for errors
```

### **Issue 5: MongoDB Atlas Connection**
```
Error: Authentication failed
```
**Solution:**
```
1. Check username/password in .env
2. Whitelist IP: 0.0.0.0/0 in Network Access
3. Verify connection string format
4. Wait 2-3 minutes after changes
```

---

## 🚀 Deployment

### **Backend (Heroku/Railway/Render)**
```bash
# Set environment variables
PORT=5000
MONGODB_URI=<your-atlas-connection-string>
JWT_SECRET=<your-secret-key>
JWT_EXPIRE=7d
```

### **Frontend (Vercel/Netlify)**
```bash
# Update API URL in api.js
const API_URL = 'https://your-backend-url.com/api';
```

---

## 🎯 Future Enhancements

### **High Priority**
- [ ] Payment integration (Razorpay/Stripe)
- [ ] Email/SMS notifications
- [ ] Map view of all parking spots
- [ ] Advanced filters (price, amenities)
- [ ] Reviews and ratings

### **Medium Priority**
- [ ] Admin dashboard
- [ ] Real-time slot updates
- [ ] Booking history export (PDF/CSV)
- [ ] QR code for bookings
- [ ] Multi-language support

### **Low Priority**
- [ ] Mobile app (React Native)
- [ ] Voice search
- [ ] Social media sharing
- [ ] Loyalty program
- [ ] Dynamic pricing

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👨‍💻 Developer

Built with ❤️ using MERN Stack

### **Contact**
- GitHub: [Your GitHub]
- Email: [Your Email]
- LinkedIn: [Your LinkedIn]

---

## 🙏 Acknowledgments

- MongoDB for database
- Express.js for backend framework
- React.js for frontend library
- Node.js for runtime
- TailwindCSS for styling
- Vite for build tool

---

## 📊 Project Stats

- **Total Lines of Code:** ~5,000+
- **Components:** 15+
- **API Endpoints:** 12
- **Cities Covered:** 8
- **Parking Spots:** 43
- **Total Capacity:** 8,580 slots
- **Features Implemented:** 20+

---

## 🎉 Quick Start Summary

```bash
# 1. Clone repository
git clone <repo-url>
cd parkify

# 2. Backend setup
cd backend
npm install
# Create .env file
node seedData.js
npm start

# 3. Frontend setup (new terminal)
cd frontend
npm install
npm run dev

# 4. Open browser
http://localhost:3000

# 5. Login
Email: user@test.com
Password: user123

# 6. Start booking!
```

---

## ✨ Key Features Highlight

### 🎯 **Smart Search**
- Autocomplete with 42+ typo variations
- Recent searches history
- Alternate city names support

### 📅 **Advanced Booking**
- Past date prevention
- Time overlap detection
- Flexible phone/vehicle formats

### 🌙 **Modern UI**
- Full dark mode
- Smooth animations
- Mobile responsive

### 🔒 **Secure**
- JWT authentication
- Protected routes
- Input validation

### 🚀 **Performance**
- Fast loading
- Optimized queries
- Efficient caching

---

**Made with 💙 using MERN Stack | Parkify © 2024**

---

## 🆘 Need Help?

If you encounter any issues:
1. Check the [Troubleshooting](#-troubleshooting) section
2. Open an [Issue](https://github.com/your-repo/issues)
3. Contact the developer

**Happy Parking! 🅿️🚗**