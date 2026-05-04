# 🔨 BidHub — Real-Time Online Auction Platform

<div align="center">


[![React](https://img.shields.io/badge/React-18.2-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org)
[![MongoDB](https://img.shields.io/badge/MongoDB-8.0-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://mongodb.com)
[![Socket.IO](https://img.shields.io/badge/Socket.IO-4.7-010101?style=for-the-badge&logo=socket.io&logoColor=white)](https://socket.io)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

**A full-stack, production-ready real-time auction platform where every second counts.**

## 🚀 Live Demo & Purchase

<div align="center">

<a href="https://rzp.io/rzp/mern-1" target="_blank">
  <img src="https://img.shields.io/badge/💳%20Purchase%20Now-FF6B35?style=for-the-badge&logo=buymeacoffee&logoColor=white" />
</a>

<br>

<a href="https://youtu.be/lK_ry36ByAs" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20Demo-FF0000?style=for-the-badge&logo=youtube&logoColor=white" />
</a>

</div>

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Database Seeding](#database-seeding)
  - [Running Locally](#running-locally)
- [API Reference](#-api-reference)
- [Socket.IO Events](#-socketio-events)
- [User Roles](#-user-roles)
- [Screenshots](#-screenshots)
- [Deployment](#-deployment)
- [Roadmap](#-roadmap)
- [License](#-license)

---

## 🌟 Overview

BidHub is a **real-time online auction platform** that enables users to list items for auction, place live competitive bids, and automatically determine winners when auctions close. Built with a modern full-stack architecture, it features role-based access for three distinct user types — Bidders, Sellers, and Administrators.

Every bid is broadcast instantly to all connected viewers via **Socket.IO WebSockets**, making BidHub feel like a live, in-person auction from anywhere in the world.

---

## ✨ Features

### 🔴 Core
- **Real-time bidding** — Socket.IO pushes every new bid to all viewers on a listing instantly
- **Live countdown timers** — colour-coded urgency: white → amber (< 1hr) → red + pulse (< 5min)
- **Auto auction close** — background job closes expired auctions and selects winners every 30 seconds
- **Automatic winner selection** — highest bidder wins; in-app notification sent immediately
- **Bid validation** — server-side checks prevent invalid, low, duplicate, or self-bids

### 👤 User Experience
- Browse and search auctions without an account
- Full-text search across title and description
- Filter by category, status, and sort by price / popularity / end time
- Paginated results (12 per page)
- Toast notification system — 5 types: success, error, warning, info, bid
- Quick-bid buttons (+min, +$10, +$50)
- Image gallery with multi-photo support per listing
- Responsive dark-mode UI — works on desktop, tablet, and mobile

### 🏷️ Seller Tools
- Create auction listings with title, description, images, category, pricing, and end time
- Quick duration presets (1hr, 6hr, 1 day, 3 days, 7 days)
- Edit listings while zero bids exist (locked once bidding starts)
- Seller dashboard with revenue tracking, bid counts, and view counts

### 🛡️ Admin Panel
- Platform statistics dashboard (users, auctions, bids, revenue)
- Category breakdown chart
- User management — change roles, activate/deactivate, delete
- Auction management — feature/unfeature, delete, filter by status
- Recent activity feeds for users and auctions

### 🔐 Security
- JWT authentication (HS256, 7-day expiry)
- bcrypt password hashing (12 salt rounds)
- Role-based access control on every protected route
- CORS restricted to configured `CLIENT_URL`
- Sellers cannot bid on their own auctions
- Auctions with bids are edit-locked (prevents manipulation)
- Inactive accounts blocked server-side even with valid tokens

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | React 18 + Vite | Component-based SPA with fast HMR |
| **Styling** | Tailwind CSS v3 | Utility-first dark-mode design |
| **Routing** | React Router v6 | Client-side routing + protected routes |
| **HTTP Client** | Axios | API calls with JWT interceptors |
| **WebSocket** | Socket.IO client v4 | Real-time bid broadcasts |
| **Backend** | Node.js + Express | RESTful API + middleware chain |
| **Real-time** | Socket.IO server v4 | Bidding events + auto-end job |
| **Database** | MongoDB + Mongoose | Document store with schemas |
| **Auth** | JWT + bcryptjs | Stateless auth + password hashing |
| **Deploy FE** | Vercel | Edge-hosted React app |
| **Deploy BE** | Render | Node.js server hosting |
| **Deploy DB** | MongoDB Atlas | Managed cloud database |

---

## 📁 Project Structure

```
auction-app/
├── client/                          # React + Vite frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx           # Sticky nav, role-aware links, mobile menu
│   │   │   ├── Footer.jsx           # Platform links + live status indicator
│   │   │   ├── AuctionCard.jsx      # Card with timer, badge, price, bids
│   │   │   ├── BidForm.jsx          # Bid input, quick buttons, validation
│   │   │   ├── CountdownTimer.jsx   # Urgency-aware live countdown
│   │   │   ├── Notification.jsx     # Toast provider + 5-type system
│   │   │   └── ProtectedRoute.jsx   # Auth + role guard wrapper
│   │   ├── context/
│   │   │   └── AuthContext.jsx      # JWT state, login/logout/register
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── Auctions.jsx
│   │   │   ├── AuctionDetail.jsx    # Live bidding + Socket.IO
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── MyBids.jsx
│   │   │   ├── WonAuctions.jsx
│   │   │   ├── seller/
│   │   │   │   ├── CreateAuction.jsx
│   │   │   │   ├── ManageAuctions.jsx
│   │   │   │   └── EditAuction.jsx
│   │   │   └── admin/
│   │   │       ├── Dashboard.jsx
│   │   │       ├── UserManagement.jsx
│   │   │       └── AuctionManagement.jsx
│   │   ├── services/
│   │   │   └── api.js               # Axios instance + all API helpers
│   │   └── socket/
│   │       └── socket.js            # Socket.IO singleton
│   ├── .env.example
│   ├── tailwind.config.js
│   └── vite.config.js
│
├── server/                          # Node.js + Express backend
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── auctionController.js
│   │   ├── bidController.js
│   │   └── adminController.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Auction.js
│   │   └── Bid.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── auctions.js
│   │   ├── bids.js
│   │   └── admin.js
│   ├── middleware/
│   │   ├── auth.js                  # protect + optionalAuth
│   │   └── roleCheck.js             # role-based guard factory
│   ├── socket/
│   │   └── bidSocket.js             # Socket rooms + 30s auto-end job
│   ├── server.js                    # Entry point
│   ├── seed.js                      # Demo data seeder
│   └── .env.example
│
├── package.json                     # Root scripts (concurrently)
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** v18 or higher — [Download](https://nodejs.org)
- **npm** v9+ (bundled with Node.js)
- **MongoDB** — [Community Server](https://www.mongodb.com/try/download/community) (local) or free [Atlas](https://cloud.mongodb.com) cluster

---

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/yourusername/bidhub-auction-platform.git
cd bidhub-auction-platform
```

**2. Install all dependencies**

```bash
# Backend
cd server && npm install

# Frontend
cd ../client && npm install
```

---

### Environment Variables

**Backend — create `server/.env`:**

```bash
cp server/.env.example server/.env
```

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/auctiondb
JWT_SECRET=your_super_secret_jwt_key_minimum_32_characters
CLIENT_URL=http://localhost:5173
NODE_ENV=development
```

| Variable | Required | Description |
|----------|----------|-------------|
| `PORT` | Yes | Express server port |
| `MONGO_URI` | Yes | MongoDB connection string |
| `JWT_SECRET` | Yes | Secret for signing JWTs — keep private, min 32 chars |
| `CLIENT_URL` | Yes | Frontend origin for CORS — must match exactly |
| `NODE_ENV` | No | `development` or `production` |

**Frontend — create `client/.env`:**

```bash
cp client/.env.example client/.env
```

```env
VITE_API_URL=http://localhost:5000
VITE_SOCKET_URL=http://localhost:5000
```

> ⚠️ Never commit `.env` files. Both are listed in `.gitignore`.

---

### Database Seeding

Populate MongoDB with demo users and auction listings:

```bash
cd server
node seed.js
```

**Demo accounts created:**

| Role | Email | Password |
|------|-------|----------|
| 🔴 Admin | `admin@demo.com` | `password123` |
| 🟢 Seller | `seller@demo.com` | `password123` |
| 🔵 Bidder | `user@demo.com` | `password123` |
| 🔵 Bidder | `bob@demo.com` | `password123` |

Plus **7 sample auctions** across multiple categories with realistic bids.

---

### Running Locally

**Start the backend** (from `server/`):

```bash
npm run dev      # development — nodemon auto-reload
npm start        # production
```

> Server runs at `http://localhost:5000`

**Start the frontend** (from `client/`):

```bash
npm run dev
```

> App runs at `http://localhost:5173`

**Run both simultaneously** (from root):

```bash
npm install      # installs concurrently
npm run dev
```

---

## 📡 API Reference

Base URL: `http://localhost:5000`  
Protected routes require: `Authorization: Bearer <jwt_token>`

### Auth

| Method | Endpoint | Access | Body |
|--------|----------|--------|------|
| `POST` | `/api/auth/register` | Public | `{ name, email, password, role }` |
| `POST` | `/api/auth/login` | Public | `{ email, password }` |
| `GET` | `/api/auth/me` | Private | — |
| `PUT` | `/api/auth/profile` | Private | `{ name, avatar }` |

### Auctions

| Method | Endpoint | Access | Notes |
|--------|----------|--------|-------|
| `GET` | `/api/auctions` | Public | Supports `?status,category,search,sort,page,limit` |
| `GET` | `/api/auctions/:id` | Public | Increments view count |
| `GET` | `/api/auctions/seller/my` | Seller+ | Authenticated seller's listings |
| `POST` | `/api/auctions` | Seller+ | Create listing |
| `PUT` | `/api/auctions/:id` | Seller+ | Edit — only if `totalBids === 0` |
| `DELETE` | `/api/auctions/:id` | Seller+ | Deletes auction + all bids |

**Sort options:** `newest` · `ending` · `price-low` · `price-high` · `popular`

**Categories:** `Electronics` · `Art` · `Jewelry` · `Vehicles` · `Fashion` · `Collectibles` · `Real Estate` · `Sports` · `Other`

### Bids

| Method | Endpoint | Access | Notes |
|--------|----------|--------|-------|
| `POST` | `/api/bids` | Private | Body: `{ auctionId, amount }` |
| `GET` | `/api/bids/:auctionId` | Public | Newest bid first |
| `GET` | `/api/bids/user/history` | Private | Full user bid history |
| `GET` | `/api/bids/user/won` | Private | User's won auctions |

### Admin

All routes require `role: "admin"`.

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/stats` | Platform stats + recent activity |
| `GET` | `/api/admin/users` | All users — `?search,role,page,limit` |
| `PUT` | `/api/admin/users/:id` | Update `{ role, isActive }` |
| `DELETE` | `/api/admin/users/:id` | Permanently delete user |
| `GET` | `/api/admin/auctions` | All auctions — `?status,page,limit` |
| `PUT` | `/api/admin/auctions/:id/feature` | Toggle featured flag |

---

## ⚡ Socket.IO Events

Each auction has a dedicated room named by its MongoDB `_id`.

### Client → Server

| Event | Payload | Description |
|-------|---------|-------------|
| `join_auction` | `auctionId: string` | Subscribe to live updates |
| `leave_auction` | `auctionId: string` | Unsubscribe (on unmount) |
| `check_auction` | `auctionId: string` | Request current bid + time left |

### Server → Client

| Event | Payload | When |
|-------|---------|------|
| `new_bid` | `{ auctionId, bid, currentBid, highestBidder }` | Bid accepted |
| `auction_ended` | `{ auctionId, winner, finalBid, message }` | Auto-close fires |
| `joined_auction` | `{ auctionId, message }` | Room join confirmed |
| `auction_status` | `{ auctionId, timeLeft, status, currentBid }` | Response to `check_auction` |

> **Auto-end job:** `setInterval` every **30 seconds** — finds expired active auctions, closes them, sets winner, pushes win notification, broadcasts `auction_ended`.

---

## 👥 User Roles

| Permission | Bidder | Seller | Admin |
|-----------|--------|--------|-------|
| Browse & search auctions | ✅ | ✅ | ✅ |
| Place bids | ✅ | ✅ | ✅ |
| View bid history & wins | ✅ | ✅ | ✅ |
| Create auction listings | ❌ | ✅ | ✅ |
| Edit / delete own listings | ❌ | ✅ | ✅ |
| Seller revenue dashboard | ❌ | ✅ | ✅ |
| Admin dashboard & analytics | ❌ | ❌ | ✅ |
| Manage all users | ❌ | ❌ | ✅ |
| Feature / moderate auctions | ❌ | ❌ | ✅ |

---

## 📸 Screenshots

| Home Page | Auction Detail |
|-----------|---------------|
| Hero with live auction grid | Real-time bid form + countdown |

| Seller Dashboard | Admin Panel |
|-----------------|-------------|
| Revenue + listing management | Stats, users, auction controls |

> Replace placeholder text above with actual screenshots by adding images to a `/docs/screenshots/` folder.

---

## 🌐 Deployment

### 1. MongoDB Atlas

```
1. Create free M0 cluster → cloud.mongodb.com
2. Network Access → Add IP 0.0.0.0/0
3. Create database user
4. Copy URI: mongodb+srv://<user>:<pw>@cluster.mongodb.net/auctiondb
```

### 2. Render (Backend)

```
1. Push server/ to GitHub
2. New Web Service → connect repo
3. Root directory: server
4. Build command:  npm install
5. Start command:  node server.js
6. Add all .env variables
```

### 3. Vercel (Frontend)

```
1. Push client/ to GitHub
2. New Project → import repo
3. Framework preset: Vite
4. Add env vars:
   VITE_API_URL    → your Render URL
   VITE_SOCKET_URL → your Render URL
5. Deploy
```

---

## 🗺️ Roadmap

- [ ] **Auto-bidding** — set a max bid; server auto-outbids on your behalf (`Bid.autoBid` field exists)
- [ ] **Stripe payments** — checkout flow triggered on winner selection
- [ ] **Email notifications** — Nodemailer + SendGrid on bid/win events
- [ ] **Watchlist** — save auctions for later (`User.watchlist` array already in schema)
- [ ] **Image file uploads** — S3/Cloudinary replacing URL fields
- [ ] **Reserve price enforcement** — minimum sale price (`Auction.reservePrice` field exists)
- [ ] **Rate limiting on bids** — `express-rate-limit` on `POST /api/bids`
- [ ] **Profile settings page** — self-service name + avatar update
- [ ] **SMS notifications** — Twilio integration for outbid alerts

---

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for full terms.

---

## 🙏 Acknowledgements

[Socket.IO](https://socket.io) · [Mongoose](https://mongoosejs.com) · [bcryptjs](https://github.com/dcodeIO/bcrypt.js) · [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) · [Tailwind CSS](https://tailwindcss.com) · [React Router](https://reactrouter.com) · [Vite](https://vitejs.dev)

---

<div align="center">

**Built with ❤️ using React · Node.js · Socket.IO · MongoDB**

⭐ Star this repo if you found it helpful!

</div>
