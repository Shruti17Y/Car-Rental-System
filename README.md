# 🚗 Car Rental System (MERN Stack)

A modern, full-stack Car Rental web application built using **React 19**, **Vite**, **Tailwind CSS**, **Node.js**, **Express**, **MongoDB Atlas**, and **ImageKit**.

🔗 **Live Demo:** [https://car-rental-system-blue-seven.vercel.app](https://car-rental-system-blue-seven.vercel.app)

---

## 📌 Features

### 👤 For Customers (Users)
- **Car Catalog**: Browse available vehicles with images, specs, seat capacity, transmission, and pricing.
- **Search & Filters**: Filter vehicles by location, category, and date availability.
- **Easy Booking**: Select pickup and return dates with dynamic price calculation.
- **My Bookings**: View current and past booking history and status.
- **User Authentication**: Secure signup and login using JWT (JSON Web Tokens).

### 🏢 For Car Owners & Admins
- **Admin Dashboard**: Real-time analytics for total bookings, revenue, and listed vehicles.
- **Vehicle Management**: Add new cars with multi-image upload (powered by ImageKit), edit, or remove listings.
- **Booking Management**: Confirm, reject, or mark bookings as completed.

---

## 🛠️ Tech Stack

| Layer | Technologies |
|---|---|
| **Frontend** | React 19, Vite, Tailwind CSS v4, React Router DOM v7, Axios, React Hot Toast, Motion |
| **Backend** | Node.js, Express 5, Mongoose |
| **Database** | MongoDB Atlas |
| **File Storage** | ImageKit |
| **Authentication** | JWT (jsonwebtoken) & bcrypt |
| **Hosting** | Vercel (Frontend & Serverless Backend) |

---

## 📁 Project Structure

```text
Car-Rental-System/
├── client/                     # Frontend (React + Vite)
│   ├── src/
│   │   ├── components/         # Reusable UI components (Navbar, Footer, etc.)
│   │   ├── context/            # React Context (AppContext.jsx)
│   │   ├── pages/              # Client & Owner pages (Home, Cars, Dashboard)
│   │   └── App.jsx
│   ├── .env                    # Frontend environment variables
│   ├── vercel.json             # SPA routing rewrite rule
│   └── package.json
│
└── server/                     # Backend (Node.js + Express API)
    ├── configs/                # MongoDB & ImageKit configurations
    ├── controllers/            # Route logic (User, Owner, Booking)
    ├── middleware/             # Auth verification & Multer upload
    ├── models/                 # Mongoose models (User, Car, Booking)
    ├── routes/                 # Express API routes
    ├── .env                    # Backend environment variables
    ├── server.js               # Express entrypoint
    ├── vercel.json             # Serverless deployment configuration
    └── package.json
```

---

## ⚙️ Environment Variables

### 1. Server Environment (`server/.env`)
```env
PORT=3000
MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.xxxx.mongodb.net
JWT_SECRET=your_jwt_secret_key

IMAGEKIT_PUBLIC_KEY=your_imagekit_public_key
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
IMAGEKIT_URL_ENDPOINT=your_imagekit_url_endpoint
```

> ⚠️ **Important for MongoDB URI:** Do not include a trailing slash `/` at the end of the MongoDB URI.

### 2. Client Environment (`client/.env`)
```env
VITE_CURRENCY=₹
VITE_BASE_URL=http://localhost:3000
```
*(In production, set `VITE_BASE_URL` to your deployed backend Vercel URL).*

---

## 🚀 Running Locally

### Step 1: Start the Backend Server
```bash
cd server
npm install
npm run server
```
- Server will run at: `http://localhost:3000`

### Step 2: Start the Frontend Client
In a new terminal window:
```bash
cd client
npm install
npm run dev
```
- Client will run at: `http://localhost:5173`

---

## 🌐 Deploying to Vercel

Because this is a full-stack monorepo, deploy it as **two separate projects** in Vercel:

### 1. Deploy the Backend (`server`)
1. In Vercel, click **Add New...** ➔ **Project** and import your repository.
2. In project configuration:
   - **Framework Preset**: `Other`
   - **Root Directory**: `server`
3. Add Environment Variables:
   - `MONGODB_URI`
   - `JWT_SECRET`
   - `IMAGEKIT_PUBLIC_KEY`
   - `IMAGEKIT_PRIVATE_KEY`
   - `IMAGEKIT_URL_ENDPOINT`
4. Click **Deploy**. Copy your deployed backend URL (e.g., `https://car-rental-system-knee.vercel.app`).

### 2. Deploy the Frontend (`client`)
1. In Vercel, click **Add New...** ➔ **Project** and import the same repository.
2. In project configuration:
   - **Framework Preset**: `Vite`
   - **Root Directory**: `client`
3. Add Environment Variables:
   - `VITE_BASE_URL` = Your backend Vercel URL
   - `VITE_CURRENCY` = `₹`
4. Click **Deploy**.

---

## 📡 API Endpoints Reference

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | Backend health check |
| `POST` | `/api/user/register` | Register a new user |
| `POST` | `/api/user/login` | Login user & return JWT token |
| `GET` | `/api/user/data` | Get authenticated user data |
| `GET` | `/api/user/cars` | Get all available rental cars |
| `POST` | `/api/owner/add-car` | Add vehicle listing with images |
| `GET` | `/api/owner/cars` | List cars owned by logged-in owner |
| `GET` | `/api/owner/dashboard` | Get owner revenue & booking stats |
| `POST` | `/api/bookings/create` | Create a car booking |
| `GET` | `/api/bookings/user` | Fetch bookings for current user |
| `GET` | `/api/bookings/owner` | Fetch bookings for owner's cars |
| `POST` | `/api/bookings/status` | Update booking status (confirmed/rejected/completed) |

---

## 📄 License
This project is open-source and available under the [ISC License](LICENSE).
