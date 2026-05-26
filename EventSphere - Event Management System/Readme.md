# 🎪 EventSphere — Full-Stack Event Management System

<div align="center">


[![React](https://img.shields.io/badge/React-18.2-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Express](https://img.shields.io/badge/Express-4.18-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.3-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![JWT](https://img.shields.io/badge/JWT-Auth-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)](https://jwt.io/)

**A production-ready platform to discover, create, and book events — with role-based access, Razorpay payments, real-time seat tracking, and QR e-tickets.**

<br/>

<a href="https://rzp.io/rzp/mern-4" target="_blank">
  <img src="https://img.shields.io/badge/💳%20Purchase%20Now-FF6B35?style=for-the-badge&logo=buymeacoffee&logoColor=white" />
</a>

<br>

<a href="https://youtu.be/uaH5pZGZUek" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20Demo-FF0000?style=for-the-badge&logo=youtube&logoColor=white" />
</a>

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Screenshots](#-screenshots)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Database Seeding](#database-seeding)
  - [Running the App](#running-the-app)
- [Project Structure](#-project-structure)
- [API Reference](#-api-reference)
- [User Roles](#-user-roles)
- [Database Models](#-database-models)
- [Payment Integration](#-payment-integration)
- [Deployment](#-deployment)
- [License](#-license)

---

## 🌟 Overview

EventSphere is a **full-stack event management web application** built with the MERN stack. It enables attendees to discover and book events, organizers to create and manage listings, and administrators to maintain platform integrity — all in one polished interface.

### Why EventSphere?

- 🎯 **End-to-end solution** — from event creation to ticket scanning
- 🔐 **Role-based access control** — separate dashboards for Users, Organizers & Admins
- ⚡ **Real-time seat updates** via Socket.IO — zero overbooking
- 💳 **Razorpay integration** — supports cards, UPI, net banking & wallets
- 📱 **Fully responsive** — works perfectly on mobile, tablet, and desktop
- 🎨 **Modern dark UI** — built with Tailwind CSS utility classes

---

## ✨ Features

### 👤 Attendees
- Browse, search, and filter events by category, city, date, and price range
- Book tickets with seat selection (1–10 seats per booking)
- Secure Razorpay checkout (or instant booking for free events)
- Auto-generated **QR code e-tickets** with unique Booking IDs
- View and cancel bookings from a personal dashboard
- Manage profile and password

### 🎪 Organizers
- Create events with images, pricing, seat capacity, and rich descriptions
- Upload up to 5 event images (Cloudinary CDN or local storage)
- Edit and manage event listings
- Track bookings per event with a full attendee table and revenue summary
- All events go through **admin approval** before going live

### 🛡️ Administrators
- Approve or reject submitted events
- Manage users — block/unblock, delete, or change roles
- View platform analytics — total users, events, bookings, and revenue
- Recent bookings feed and top-events leaderboard on the dashboard

### ⚡ Platform
- Real-time seat availability updates via **Socket.IO**
- HMAC-SHA256 payment signature verification
- JWT authentication with role-based route protection
- Full-text search with MongoDB text indexes
- Pagination, sorting, and multi-field filtering

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18, Vite, Tailwind CSS, React Router v6 |
| **HTTP Client** | Axios with JWT interceptors |
| **Backend** | Node.js, Express.js, express-validator |
| **Database** | MongoDB, Mongoose ODM |
| **Authentication** | JWT (jsonwebtoken), bcryptjs |
| **Payments** | Razorpay (with mock mode for dev) |
| **Image Uploads** | Cloudinary + Multer |
| **QR Codes** | `qrcode` npm package |
| **Real-time** | Socket.IO |
| **Email** | Nodemailer |

---

## 📸 Screenshots

<details>
<summary>Click to expand screenshots</summary>

### Homepage
> Hero section with search, featured events grid, and category filters

### Events Listing
> Searchable, filterable paginated grid with sidebar filters

### Event Details + Booking
> Full event details with image gallery, seat selector, and Razorpay checkout

### My Bookings
> Booking history with QR code modal for e-ticket access

### Organizer — Create Event
> Multi-section form with image upload preview

### Admin Dashboard
> Stats cards, recent bookings panel, and top-events ranking

</details>

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- **Node.js** v18 or higher — [Download](https://nodejs.org/)
- **npm** v8+ (bundled with Node.js)
- **MongoDB** running locally **or** a [MongoDB Atlas](https://www.mongodb.com/atlas) connection string
- **Git** — [Download](https://git-scm.com/)

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/your-username/event-management-system.git
cd event-management-system
```

**2. Install backend dependencies**

```bash
cd server
npm install
```

**3. Install frontend dependencies**

```bash
cd ../client
npm install
```

### Environment Variables

**Backend** — create `server/.env` from the example:

```bash
cd server
cp .env.example .env
```

Then edit `server/.env`:

```env
# Server
PORT=5000
NODE_ENV=development

# Database
MONGO_URI=mongodb://localhost:27017/eventmanagement
# For Atlas: mongodb+srv://<user>:<password>@cluster.mongodb.net/eventmanagement

# Authentication
JWT_SECRET=replace_with_a_long_random_secret_string_here
JWT_EXPIRE=7d

# CORS
CLIENT_URL=http://localhost:5173

# Cloudinary (optional — images stored locally if not set)
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Razorpay (optional — mock mode used if not set)
RAZORPAY_KEY_ID=rzp_test_xxxxxxxxxxxx
RAZORPAY_KEY_SECRET=your_key_secret

# Email / Nodemailer (optional)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password
```

> **Note:** Variables marked optional have graceful fallbacks. The app works in full development mode with only `MONGO_URI` and `JWT_SECRET` configured.

**Frontend** — create `client/.env` (optional):

```bash
cd client
cp .env.example .env
```

```env
# Only needed for production builds or if not using the Vite proxy
VITE_API_URL=http://localhost:5000/api
```

> In development, the Vite proxy automatically forwards `/api/*` requests to port 5000, so this variable is optional.

### Database Seeding

Populate the database with demo users and 6 sample events:

```bash
cd server
node seed.js
```

This creates:

| Role | Email | Password |
|------|-------|----------|
| 🛡️ Admin | `admin@eventms.com` | `Admin@123` |
| 🎪 Organizer | `organizer@eventms.com` | `Organizer@123` |
| 👤 User | `user@eventms.com` | `User@123` |

### Running the App

**Start the backend** (from `/server`):

```bash
npm run dev        # Development — auto-restarts with nodemon
npm start          # Production
```

API server starts at → **http://localhost:5000**
Health check → **http://localhost:5000/api/health**

**Start the frontend** (from `/client`, in a new terminal):

```bash
npm run dev
```

React app starts at → **http://localhost:5173**

---

## 📁 Project Structure

```
event-management-system/
│
├── client/                          # React + Vite frontend
│   ├── index.html
│   ├── vite.config.js               # Dev proxy: /api → localhost:5000
│   ├── tailwind.config.js
│   └── src/
│       ├── main.jsx                 # App entry point
│       ├── App.jsx                  # Router + auth-gated routes
│       ├── index.css                # Tailwind imports + global styles
│       │
│       ├── context/
│       │   └── AuthContext.jsx      # Global auth state (user, token, roles)
│       │
│       ├── services/
│       │   └── api.js               # All Axios calls + JWT interceptor
│       │
│       ├── components/
│       │   ├── Navbar.jsx           # Responsive nav with role-aware links
│       │   ├── Footer.jsx
│       │   ├── EventCard.jsx        # Reusable event card with seat bar
│       │   └── LoadingSpinner.jsx
│       │
│       └── pages/
│           ├── Home.jsx             # Hero, featured events, upcoming events
│           ├── Events.jsx           # Searchable, filterable event grid
│           ├── EventDetails.jsx     # Event detail + Razorpay booking widget
│           ├── Login.jsx
│           ├── Register.jsx         # Role toggle (User / Organizer)
│           ├── MyBookings.jsx       # Booking history + QR modal
│           ├── Profile.jsx          # Edit profile + change password
│           ├── CreateEvent.jsx      # Multi-section event creation form
│           ├── EditEvent.jsx        # Pre-filled event edit form
│           ├── ManageEvents.jsx     # Organizer's event list
│           ├── BookingOverview.jsx  # Per-event booking analytics
│           └── admin/
│               ├── Dashboard.jsx    # Stats + recent bookings + top events
│               ├── UserManagement.jsx
│               └── EventApproval.jsx
│
└── server/                          # Node.js + Express backend
    ├── server.js                    # Entry: Express, Socket.IO, MongoDB
    ├── seed.js                      # Demo data seeder
    │
    ├── models/
    │   ├── User.js                  # name, email, password, role, isBlocked
    │   ├── Event.js                 # title, location, price, seats, status
    │   ├── Booking.js               # bookingId, qrCode, status, paymentStatus
    │   └── Payment.js               # Razorpay order/payment tracking
    │
    ├── controllers/
    │   ├── authController.js        # register, login, getMe, updateProfile
    │   ├── eventController.js       # CRUD, search, filter, pagination
    │   ├── bookingController.js     # createBooking, cancel, QR generation
    │   ├── adminController.js       # stats, user mgmt, event approval
    │   └── paymentController.js     # Razorpay order + signature verify
    │
    ├── routes/
    │   ├── auth.js                  # /api/auth/*
    │   ├── events.js                # /api/events/*
    │   ├── bookings.js              # /api/bookings/*
    │   ├── admin.js                 # /api/admin/* (admin only)
    │   └── payments.js             # /api/payments/*
    │
    └── middleware/
        ├── auth.js                  # protect (JWT) + authorize (role)
        └── upload.js                # Multer + Cloudinary storage
```

---

## 📡 API Reference

All endpoints are prefixed with `/api`. Protected routes require the `Authorization: Bearer <token>` header.

### Auth

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `POST` | `/auth/register` | Register new user or organizer | Public |
| `POST` | `/auth/login` | Login and receive JWT | Public |
| `GET` | `/auth/me` | Get current user | ✅ JWT |
| `PUT` | `/auth/profile` | Update name & phone | ✅ JWT |
| `PUT` | `/auth/change-password` | Change password | ✅ JWT |

### Events

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `GET` | `/events` | List events with search/filter/pagination | Public |
| `GET` | `/events/featured` | Featured events for homepage | Public |
| `GET` | `/events/upcoming` | Upcoming events for homepage | Public |
| `GET` | `/events/my` | Organizer's own events | 🎪 Organizer+ |
| `GET` | `/events/:id` | Single event details | Public |
| `GET` | `/events/:id/bookings` | All bookings for an event | 🎪 Organizer+ |
| `POST` | `/events` | Create event (multipart/form-data) | 🎪 Organizer+ |
| `PUT` | `/events/:id` | Update event | 🎪 Organizer+ |
| `DELETE` | `/events/:id` | Delete event | 🎪 Organizer+ |

**Query parameters for `GET /events`:**

```
search    — full-text search (title, description, city)
category  — music | sports | tech | business | arts | food | education | other
city      — regex city filter
minPrice  — minimum ticket price (₹)
maxPrice  — maximum ticket price (₹)
date      — filter events on a specific date (YYYY-MM-DD)
sort      — -createdAt | date | price | -price
page      — page number (default: 1)
limit     — results per page (default: 12)
```

### Bookings

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `POST` | `/bookings` | Book tickets | ✅ JWT |
| `GET` | `/bookings/my` | Get current user's bookings | ✅ JWT |
| `GET` | `/bookings/:id` | Get single booking | ✅ JWT |
| `DELETE` | `/bookings/:id` | Cancel booking | ✅ JWT |

### Payments

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `POST` | `/payments/create-order` | Create Razorpay order | ✅ JWT |
| `POST` | `/payments/verify` | Verify HMAC signature | ✅ JWT |
| `GET` | `/payments/history` | User's payment history | ✅ JWT |

### Admin

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `GET` | `/admin/stats` | Platform-wide statistics | 🛡️ Admin |
| `GET` | `/admin/users` | List all users (search/filter) | 🛡️ Admin |
| `PUT` | `/admin/users/:id/block` | Block or unblock user | 🛡️ Admin |
| `PUT` | `/admin/users/:id/role` | Change user role | 🛡️ Admin |
| `DELETE` | `/admin/users/:id` | Delete user | 🛡️ Admin |
| `GET` | `/admin/events` | List all events (filter by status) | 🛡️ Admin |
| `PUT` | `/admin/events/:id/status` | Approve or reject event | 🛡️ Admin |

---

## 👥 User Roles

```
┌─────────────────────────────────────────────────────────────────┐
│                        Permission Matrix                        │
├────────────────────────────────┬────────┬───────────┬───────────┤
│ Permission                     │  User  │ Organizer │   Admin   │
├────────────────────────────────┼────────┼───────────┼───────────┤
│ Browse events                  │   ✅   │    ✅     │    ✅     │
│ Book tickets                   │   ✅   │    ✅     │    ✅     │
│ Cancel own bookings            │   ✅   │    ✅     │    ✅     │
│ View QR e-tickets              │   ✅   │    ✅     │    ✅     │
│ Manage own profile             │   ✅   │    ✅     │    ✅     │
│ Create events                  │   ❌   │    ✅     │    ✅     │
│ Edit own events                │   ❌   │    ✅     │    ✅     │
│ Delete own events              │   ❌   │    ✅     │    ✅     │
│ View event bookings            │   ❌   │    ✅     │    ✅     │
│ Approve / reject events        │   ❌   │    ❌     │    ✅     │
│ Block / delete users           │   ❌   │    ❌     │    ✅     │
│ Change user roles              │   ❌   │    ❌     │    ✅     │
│ View admin analytics           │   ❌   │    ❌     │    ✅     │
└────────────────────────────────┴────────┴───────────┴───────────┘
```

---

## 🗄 Database Models

<details>
<summary><strong>User</strong></summary>

```js
{
  name:             String (required),
  email:            String (required, unique),
  password:         String (required, bcrypt hashed, salt 12),
  role:             'user' | 'organizer' | 'admin'  (default: 'user'),
  phone:            String,
  avatar:           String,
  isBlocked:        Boolean (default: false),
  isEmailVerified:  Boolean (default: false),
  timestamps:       true
}
```
</details>

<details>
<summary><strong>Event</strong></summary>

```js
{
  title:          String (required),
  description:    String (required),
  category:       'music'|'sports'|'tech'|'business'|'arts'|'food'|'education'|'other',
  date:           Date (required),
  endDate:        Date,
  time:           String (required),
  location: {
    address:      String (required),
    city:         String (required),
    state:        String,
    country:      String (default: 'India'),
    coordinates:  { lat: Number, lng: Number }
  },
  images:         [String],
  price:          Number (min: 0),
  totalSeats:     Number (required),
  availableSeats: Number (required),
  organizer:      ObjectId → User,
  status:         'pending'|'approved'|'rejected'|'cancelled' (default: 'pending'),
  isFeatured:     Boolean (default: false),
  tags:           [String],
  refundPolicy:   String,
  timestamps:     true
}
```
</details>

<details>
<summary><strong>Booking</strong></summary>

```js
{
  bookingId:      String (auto-generated: 'BK-XXXXXXXX'),
  user:           ObjectId → User,
  event:          ObjectId → Event,
  seatsBooked:    Number (min: 1),
  totalAmount:    Number,
  status:         'pending'|'confirmed'|'cancelled'|'refunded',
  paymentStatus:  'pending'|'paid'|'failed'|'refunded',
  paymentId:      String,
  qrCode:         String (base64 data URL),
  attendeeDetails: { name, email, phone },
  cancelledAt:    Date,
  cancellationReason: String,
  timestamps:     true
}
```
</details>

<details>
<summary><strong>Payment</strong></summary>

```js
{
  user:                ObjectId → User,
  booking:             ObjectId → Booking,
  amount:              Number (INR),
  currency:            String (default: 'INR'),
  status:              'pending'|'success'|'failed'|'refunded',
  provider:            'razorpay'|'stripe'|'manual',
  razorpayOrderId:     String,
  razorpayPaymentId:   String,
  razorpaySignature:   String,
  timestamps:          true
}
```
</details>

---

## 💳 Payment Integration

EventSphere integrates **Razorpay** for secure payment processing.

### Payment Flow

```
User clicks Pay
      │
      ▼
POST /api/bookings          ── Booking created (status: pending, seats reserved)
      │
      ▼
POST /api/payments/create-order  ── Razorpay order created
      │
      ▼
Razorpay checkout modal opens in browser
      │
      ▼
User completes payment
      │
      ▼
POST /api/payments/verify   ── HMAC-SHA256 signature verified server-side
      │
      ▼
Booking confirmed + QR e-ticket generated
```

### Setting Up Razorpay

1. Create an account at [razorpay.com](https://razorpay.com)
2. Go to **Dashboard → Settings → API Keys**
3. Generate test keys (prefix `rzp_test_`)
4. Add to `server/.env`:
   ```
   RAZORPAY_KEY_ID=rzp_test_xxxxxxxxxxxx
   RAZORPAY_KEY_SECRET=your_secret_here
   ```

### Mock Mode

> **No Razorpay account?** No problem.

If `RAZORPAY_KEY_ID` is not set, the app runs in **mock payment mode** automatically. The entire booking flow works — bookings are created, confirmed, and QR codes are generated — without any real payment credentials.

---

## 🚢 Deployment

### Frontend → [Vercel](https://vercel.com)

```bash
cd client
npm run build    # Output: dist/
```

| Setting | Value |
|---------|-------|
| Root Directory | `client` |
| Build Command | `npm run build` |
| Output Directory | `dist` |
| Environment Variable | `VITE_API_URL=https://your-api.onrender.com/api` |

### Backend → [Render](https://render.com)

| Setting | Value |
|---------|-------|
| Root Directory | `server` |
| Build Command | `npm install` |
| Start Command | `node server.js` |
| Environment Variables | All keys from `server/.env` |

### Database → [MongoDB Atlas](https://www.mongodb.com/atlas)

1. Create a free M0 cluster
2. Create a database user with read/write permissions
3. Whitelist `0.0.0.0/0` (or your server IP)
4. Copy the connection string and set as `MONGO_URI` on Render

### Production Checklist

- [ ] Set `JWT_SECRET` to a strong 32+ character random string
- [ ] Set `NODE_ENV=production`
- [ ] Update `CLIENT_URL` to your Vercel domain
- [ ] Switch Razorpay keys from `rzp_test_` to `rzp_live_`
- [ ] Configure Cloudinary for persistent image storage
- [ ] Restrict MongoDB Atlas IP allowlist
- [ ] Run `node seed.js` once on the production database

---

### Commit Convention

This project uses [Conventional Commits](https://www.conventionalcommits.org/):

```
feat:     New feature
fix:      Bug fix
docs:     Documentation changes
style:    Code formatting (no logic change)
refactor: Code refactor (no feature/fix)
test:     Adding or updating tests
chore:    Build process or auxiliary tool changes
```

---

## 🐛 Troubleshooting

| Problem | Likely Cause | Fix |
|---------|-------------|-----|
| `MongoDB connection error` | `mongod` not running or wrong URI | Start MongoDB locally or check `MONGO_URI` in `.env` |
| `Port already in use` | Another process on 5000 or 5173 | Change `PORT` in `.env` or `port` in `vite.config.js` |
| `JWT invalid` after server restart | `JWT_SECRET` changed | Use a fixed string in `.env`, not a generated value |
| Images not uploading | Cloudinary not configured | Add Cloudinary vars to `.env` or create `server/uploads/` |
| CORS errors in browser | `CLIENT_URL` mismatch | Set exact frontend origin in `server/.env` |
| Seed script fails | MongoDB not connected | Check `MONGO_URI`; seed.js clears existing data first |
| Razorpay modal not opening | No API keys configured | App falls back to mock mode automatically |
| `Cannot GET /api/health` | Server not running | Start server with `npm run dev` in `server/` |

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [React](https://reactjs.org/) — UI library
- [Vite](https://vitejs.dev/) — Next-generation frontend tooling
- [Tailwind CSS](https://tailwindcss.com/) — Utility-first CSS framework
- [Express.js](https://expressjs.com/) — Node.js web framework
- [Mongoose](https://mongoosejs.com/) — MongoDB object modeling
- [Razorpay](https://razorpay.com/) — Payment gateway
- [Cloudinary](https://cloudinary.com/) — Image CDN
- [Socket.IO](https://socket.io/) — Real-time communication
- [qrcode](https://www.npmjs.com/package/qrcode) — QR code generation
- [react-hot-toast](https://react-hot-toast.com/) — Toast notifications

---

<div align="center">

Made with ❤️ using the MERN Stack

**[⬆ Back to Top](#-eventsphere--full-stack-event-management-system)**

</div>
