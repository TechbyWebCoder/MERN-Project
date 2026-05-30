<div align="center">

<img src="https://img.shields.io/badge/FeastRush-Food%20Delivery-F97316?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0tMiAxNWwtNS01IDEuNDEtMS40MUwxMCAxNC4xN2w3LjU5LTcuNTlMMTkgOGwtOSA5eiIvPjwvc3ZnPg==" alt="FeastRush"/>

# 🍔 FeastRush — Food Delivery Platform

**A production-ready, full-stack food delivery web application built with the MERN stack.**

Connect customers with restaurants, empower owners to manage menus and orders, and give administrators full platform oversight — all in one seamless experience.

<br/>

[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://mongodb.com)
[![Express.js](https://img.shields.io/badge/Express.js-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com)
[![React](https://img.shields.io/badge/React_18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://reactjs.org)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Stripe](https://img.shields.io/badge/Stripe-635BFF?style=flat-square&logo=stripe&logoColor=white)](https://stripe.com)
[![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)](https://jwt.io)
[![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev)

<br/>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](CONTRIBUTING.md)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg?style=flat-square)](package.json)

<br/>

<br/>

<a href="https://rzp.io/rzp/mern-5" target="_blank">
  <img src="https://img.shields.io/badge/💳%20Purchase%20Now-FF6B35?style=for-the-badge&logo=buymeacoffee&logoColor=white" />
</a>

<br>

<a href="https://youtu.be/RGnpLhAtONA" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20Demo-FF0000?style=for-the-badge&logo=youtube&logoColor=white" />
</a>

</div>

---

## 📋 Table of Contents

- [✨ Features](#-features)
- [🧱 Tech Stack](#-tech-stack)
- [🏗️ Architecture](#️-architecture)
- [📁 Project Structure](#-project-structure)
- [⚡ Quick Start](#-quick-start)
- [🌱 Seeding Demo Data](#-seeding-demo-data)
- [🔑 Demo Accounts](#-demo-accounts)
- [🛣️ API Reference](#️-api-reference)
- [🗄️ Database Schema](#️-database-schema)
- [👤 User Roles](#-user-roles)
- [🚀 Deployment](#-deployment)
- [⚙️ Environment Variables](#️-environment-variables)
- [📄 License](#-license)

---

## ✨ Features

### 🛒 Customer Experience
- Browse and search restaurants by name, cuisine, or category (Veg / Non-Veg / Both)
- View full restaurant menus with category tabs and vegetarian-only filter
- Smart cart system — server-side persistence, cross-restaurant conflict detection
- Checkout with delivery address and special instructions
- **Stripe online payments** + Cash on Delivery support
- Real-time order status tracker (6-stage pipeline with animated progress bar)
- Full order history with item-level breakdown

### 🍳 Restaurant Owner Tools
- Create and manage restaurant profile (cuisine, location, hours, fees)
- Full menu CRUD — add, edit, delete food items
- Toggle item availability on/off instantly (no delete needed for out-of-stock)
- Mark items as ⭐ Featured (shown on homepage Popular Dishes)
- Incoming orders dashboard with status advancement
- Filter orders by status (Pending → Confirmed → Preparing → Delivered)

### 👑 Admin Panel
- Platform analytics: total users, restaurants, orders, revenue
- Daily revenue chart + top restaurants by earnings
- User management: search, filter by role, block/unblock, delete
- Restaurant approval workflow (new restaurants require admin approval)
- Global order oversight across all restaurants

### 🔐 Security & Auth
- JWT authentication with 7-day expiry
- bcrypt password hashing (salt rounds = 12)
- Role-based route protection (user / owner / admin)
- Blocked users rejected at middleware level
- Admin-only creation via database (not self-registerable)

---

## 🧱 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| **Frontend** | React 18 + Vite | Component UI with HMR dev server |
| **Styling** | Tailwind CSS | Utility-first CSS framework |
| **Routing** | React Router v6 | Client-side routing with protected routes |
| **HTTP** | Axios | API calls with JWT interceptors |
| **State** | React Context API | Global auth and cart state |
| **Notifications** | react-hot-toast | Toast notifications |
| **Backend** | Node.js + Express.js | REST API server |
| **Database** | MongoDB + Mongoose | Document database with ODM |
| **Auth** | jsonwebtoken + bcryptjs | JWT tokens + password hashing |
| **Payments** | Stripe SDK v14 | PaymentIntent-based card payments |
| **Validation** | express-validator | Request body validation |

---

## 🏗️ Architecture

```
┌─────────────────────────┐         HTTPS / JSON          ┌─────────────────────────┐
│                         │  ──────────────────────────►  │                         │
│   React 18 (Vite)       │                               │   Express.js API        │
│   Tailwind CSS          │  ◄──────────────────────────  │   Controllers           │
│   Axios + JWT header    │         REST responses         │   JWT Middleware         │
│   AuthContext           │                               │   Role Guards           │
│   CartContext           │                               │                         │
└─────────────────────────┘                               └────────────┬────────────┘
                                                                       │ Mongoose ODM
                                                                       │
                                                          ┌────────────▼────────────┐
                                                          │                         │
                                                          │   MongoDB               │
                                                          │   Atlas / Local         │
                                                          │   5 Collections         │
                                                          │                         │
                                                          └─────────────────────────┘

External Services
  ├── Stripe       → Payment processing (PaymentIntents)
  ├── MongoDB Atlas → Cloud database hosting
  ├── Vercel       → Frontend deployment
  └── Render       → Backend API deployment
```

---

## 📁 Project Structure

```
feastrush/
├── backend/
│   ├── seed.js                        # 🌱 Run once: creates demo accounts + restaurants
│   ├── .env.example                   # Environment variable template
│   ├── package.json
│   └── src/
│       ├── server.js                  # Express app, middleware, route mounting
│       ├── middleware/
│       │   └── auth.js                # protect() and authorize() guards
│       ├── models/
│       │   ├── User.js                # User schema (name, email, role, isBlocked)
│       │   ├── Restaurant.js          # Restaurant (name, cuisine, location, isApproved)
│       │   ├── Food.js                # Food item (price, category, isVeg, isAvailable)
│       │   ├── Cart.js                # Per-user cart with auto-calculated totalPrice
│       │   └── Order.js               # Order with 6-stage status pipeline + history
│       ├── controllers/
│       │   ├── authController.js      # register, login, getMe, updateProfile
│       │   ├── restaurantController.js
│       │   ├── foodController.js
│       │   ├── cartController.js
│       │   ├── orderController.js
│       │   ├── adminController.js     # stats, users, restaurants, orders
│       │   └── paymentController.js   # Stripe PaymentIntent
│       └── routes/
│           ├── auth.js  restaurants.js  foods.js
│           ├── cart.js  orders.js  admin.js  payments.js
│
└── frontend/
    ├── index.html
    ├── vite.config.js
    ├── tailwind.config.js
    ├── postcss.config.js
    └── src/
        ├── main.jsx                   # React root + BrowserRouter + Toaster
        ├── App.jsx                    # All routes + ProtectedRoute component
        ├── index.css                  # Tailwind directives + custom utilities
        ├── services/
        │   └── api.js                 # Axios instance + authAPI, cartAPI, orderAPI…
        ├── context/
        │   ├── AuthContext.jsx        # JWT login/logout, user state, role flags
        │   └── CartContext.jsx        # Server-synced cart + addToCart logic
        ├── components/
        │   ├── Navbar.jsx             # Responsive nav with cart badge + user menu
        │   ├── Footer.jsx
        │   ├── FoodCard.jsx           # Food item card with Add button
        │   ├── RestaurantCard.jsx     # Restaurant card linking to detail page
        │   ├── LoadingSpinner.jsx
        │   └── EmptyState.jsx
        └── pages/
            ├── HomePage.jsx           # Hero, category filter, restaurants, featured foods
            ├── RestaurantsPage.jsx    # Paginated listing with search + filters
            ├── RestaurantDetailPage.jsx  # Menu with category tabs + veg toggle
            ├── LoginPage.jsx          # Login + demo account quick-fill
            ├── RegisterPage.jsx       # Registration with role selection
            ├── CartPage.jsx           # Cart items + price summary
            ├── CheckoutPage.jsx       # Address, payment method, order placement
            ├── OrdersPage.jsx         # Order history list
            ├── OrderDetailPage.jsx    # Live status tracker + order breakdown
            ├── ProfilePage.jsx        # Profile edit + password change
            ├── owner/
            │   ├── OwnerDashboard.jsx
            │   ├── RestaurantSetupPage.jsx
            │   ├── ManageMenuPage.jsx
            │   ├── AddFoodPage.jsx
            │   └── OwnerOrdersPage.jsx
            └── admin/
                ├── AdminDashboard.jsx
                ├── AdminUsers.jsx
                ├── AdminRestaurants.jsx
                └── AdminOrders.jsx
```

---

## ⚡ Quick Start

### Prerequisites

- **Node.js** >= 18.x
- **npm** >= 9.x
- **MongoDB** — local instance **or** [MongoDB Atlas](https://mongodb.com/atlas) (free tier)
- **Git**
- **Stripe account** *(optional — for payment testing)*

### 1. Clone the repository

```bash
git clone https://github.com/your-username/feastrush.git
cd feastrush
```

### 2. Backend setup

```bash
cd backend
npm install
cp .env.example .env
```

Edit `.env` with your values (see [Environment Variables](#️-environment-variables)), then start:

```bash
npm run dev          # Development with nodemon
# or
npm start            # Production
```

> ✅ Backend runs at **http://localhost:5000**

### 3. Seed demo data *(required for demo accounts)*

```bash
# From the backend directory:
npm run seed
```

This creates 3 demo user accounts, 4 restaurants, and 23+ food items. [More details below ↓](#-seeding-demo-data)

### 4. Frontend setup

Open a **new terminal**:

```bash
cd frontend
npm install
cp .env.example .env
```

Edit `.env`:

```env
VITE_API_URL=http://localhost:5000/api
VITE_STRIPE_PUBLISHABLE_KEY=pk_test_your_key   # optional
```

Start the dev server:

```bash
npm run dev
```

> ✅ Frontend runs at **http://localhost:5173**

---

## 🌱 Seeding Demo Data

The seed script populates your database with everything you need to explore the app:

```bash
cd backend && npm run seed
```

**What gets created:**

| Type | Count | Details |
|---|---|---|
| Users | 3 | Admin, Restaurant Owner, Customer |
| Restaurants | 4 | Spice Garden 🇮🇳, Burger Republic 🍔, Green Leaf Café 🥗, Pizza Piazza 🍕 |
| Food items | 23+ | 5–6 items per restaurant across multiple categories |

**Seed output:**

```
✅ Created admin:  admin@demo.com  / password123
✅ Created owner:  owner@demo.com  / password123
✅ Created user:   user@demo.com   / password123
✅ Created restaurant: Spice Garden (Indian)
✅ Created restaurant: Burger Republic (American)
✅ Created restaurant: Green Leaf Café (Healthy/Veg)
✅ Created restaurant: Pizza Piazza (Italian)
✅ Added food: Butter Chicken → Spice Garden
... (23+ items total)
🎉 Seed complete!
```

> The seed script is **idempotent** — running it multiple times safely skips already-existing records.

---

## 🔑 Demo Accounts

After running `npm run seed`, you can log in with these credentials:

| Role | Email | Password | Redirects To |
|---|---|---|---|
| 👑 Admin | `admin@demo.com` | `password123` | `/admin` |
| 🍳 Restaurant Owner | `owner@demo.com` | `password123` | `/owner` |
| 🛒 Customer | `user@demo.com` | `password123` | `/` |

> **Pro tip:** The Login page has quick-fill buttons for all three demo accounts.

---

## 🛣️ API Reference

**Base URL:** `http://localhost:5000/api`

All responses follow the format:
```json
{ "success": true, "data": {}, "message": "..." }
```

### Authentication

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/auth/register` | Public | Register a new user |
| `POST` | `/auth/login` | Public | Login — returns JWT token |
| `GET` | `/auth/me` | ✅ Any | Get current user (with restaurantId populated) |
| `PUT` | `/auth/update-profile` | ✅ Any | Update name, phone, address |
| `PUT` | `/auth/change-password` | ✅ Any | Change password, re-issues token |

### Restaurants

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/restaurants` | Public | List approved restaurants. Query: `?category=veg&search=pizza&city=NY&page=1&limit=12` |
| `GET` | `/restaurants/:id` | Public | Single restaurant with owner info |
| `GET` | `/restaurants/owner/my-restaurant` | 🍳 Owner | Get authenticated owner's restaurant |
| `POST` | `/restaurants` | 🍳 Owner | Create restaurant (starts as pending) |
| `PUT` | `/restaurants/:id` | 🍳 Owner | Update restaurant details |
| `DELETE` | `/restaurants/:id` | 🍳 Owner | Delete restaurant |

### Food Items

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/foods/featured` | Public | Featured items (up to 8, homepage) |
| `GET` | `/foods/item/:id` | Public | Single food item |
| `GET` | `/foods/:restaurantId` | Public | Restaurant menu. Query: `?category=Pizza&isVeg=true` |
| `POST` | `/foods` | 🍳 Owner | Add food item to menu |
| `PUT` | `/foods/:id` | 🍳 Owner | Update food item |
| `PATCH` | `/foods/:id/toggle` | 🍳 Owner | Toggle `isAvailable` |
| `DELETE` | `/foods/:id` | 🍳 Owner | Delete food item |

### Cart

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/cart` | ✅ Any | Get user's cart (populated) |
| `POST` | `/cart/add` | ✅ Any | Add item. Body: `{ foodId, quantity }`. Detects cross-restaurant conflict → returns `code: "DIFFERENT_RESTAURANT"` |
| `PUT` | `/cart/update/:foodId` | ✅ Any | Update quantity. quantity ≤ 0 removes item |
| `DELETE` | `/cart/remove/:foodId` | ✅ Any | Remove specific item |
| `DELETE` | `/cart/clear` | ✅ Any | Empty entire cart |

### Orders

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/orders` | ✅ Any | Place order from cart. Body: `{ deliveryAddress, specialInstructions, paymentMethod }` |
| `GET` | `/orders/my-orders` | ✅ Any | User's order history (newest first) |
| `GET` | `/orders/:id` | ✅ Any | Single order (accessible to customer, owner, admin) |
| `GET` | `/orders/restaurant/:id` | 🍳 Owner | All orders for a restaurant. Query: `?status=pending&page=1` |
| `PUT` | `/orders/:id/status` | 🍳 Owner | Advance status. Body: `{ status, note }` |

### Admin *(Admin role only)*

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/admin/stats` | Dashboard: users, orders, revenue, ordersByStatus, dailyRevenue, topRestaurants |
| `GET` | `/admin/users` | All users. Query: `?role=owner&search=john&page=1` |
| `PUT` | `/admin/users/:id/block` | Toggle block/unblock (cannot block admins) |
| `DELETE` | `/admin/users/:id` | Permanently delete user (cannot delete admins) |
| `GET` | `/admin/restaurants` | All restaurants. Query: `?approved=false` |
| `PUT` | `/admin/restaurants/:id/approve` | Set `isApproved: true` |
| `GET` | `/admin/orders` | All platform orders. Query: `?status=pending&page=1` |

### Payments

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/payments/create-payment-intent` | ✅ Any | Creates Stripe PaymentIntent for cart total |
| `POST` | `/payments/confirm` | ✅ Any | Confirms payment and marks order as paid |

---

## 🗄️ Database Schema

### User
```js
{
  name:         String,          // required, 2–50 chars
  email:        String,          // required, unique, lowercase
  password:     String,          // bcrypt hashed, select: false
  role:         'user' | 'owner' | 'admin',  // default: 'user'
  phone:        String,
  address:      { street, city, state, zip },
  isBlocked:    Boolean,         // default: false
  restaurantId: ObjectId → Restaurant
}
```

### Restaurant
```js
{
  name:         String,          // required
  description:  String,
  cuisine:      String,          // required (e.g. 'Indian', 'Italian')
  category:     'veg' | 'non-veg' | 'both',
  image:        String,          // URL
  location:     { address, city, state, zip, coordinates: { lat, lng } },
  ownerId:      ObjectId → User, // required
  rating:       Number,          // 0–5
  totalRatings: Number,
  deliveryTime: String,          // e.g. '30-45 min'
  deliveryFee:  Number,          // dollars
  minOrder:     Number,          // dollars
  isOpen:       Boolean,
  isApproved:   Boolean,         // must be true to appear publicly
  openingHours: { open: String, close: String }
}
```

### Food
```js
{
  name:             String,      // required
  description:      String,
  price:            Number,      // required
  discountedPrice:  Number,      // optional — shown struck-through
  image:            String,      // URL
  category:         String,      // e.g. 'Main Course', 'Starters'
  restaurantId:     ObjectId → Restaurant,
  isVeg:            Boolean,
  isAvailable:      Boolean,     // default: true
  isFeatured:       Boolean,     // appears on homepage
  preparationTime:  Number,      // minutes
  spiceLevel:       'mild' | 'medium' | 'hot' | 'extra-hot',
  calories:         Number
}
```

### Cart
```js
{
  userId:       ObjectId → User,  // unique per user
  restaurantId: ObjectId → Restaurant,
  items: [{
    foodId:       ObjectId → Food,
    name:         String,
    price:        Number,
    image:        String,
    quantity:     Number
  }],
  totalPrice:   Number  // auto-calculated via pre-save hook
}
```

### Order
```js
{
  userId:           ObjectId → User,
  restaurantId:     ObjectId → Restaurant,
  restaurantName:   String,
  items: [{ foodId, name, price, image, quantity }],
  subtotal:         Number,
  deliveryFee:      Number,
  tax:              Number,      // 5% of subtotal
  totalAmount:      Number,      // subtotal + deliveryFee + tax
  status:           'pending' | 'confirmed' | 'preparing' | 'out_for_delivery' | 'delivered' | 'cancelled',
  paymentStatus:    'pending' | 'paid' | 'failed' | 'refunded',
  paymentMethod:    'stripe' | 'cod',
  stripePaymentIntentId: String,
  deliveryAddress:  { street, city, state, zip },
  specialInstructions: String,
  estimatedDelivery: Date,       // set to +45 min at order creation
  deliveredAt:      Date,
  statusHistory: [{ status, timestamp, note }]  // full audit trail
}
```

---

## 👤 User Roles

### 🛒 Customer (`role: 'user'`)
- Browse and search approved restaurants
- Add items to cart (one restaurant at a time)
- Checkout with delivery address + payment method
- Track orders via animated status progress bar
- View full order history

### 🍳 Restaurant Owner (`role: 'owner'`)
- Register restaurant (requires Admin approval before going live)
- Full menu management: add, edit, delete, toggle availability
- Mark items as Featured for homepage visibility
- Manage incoming orders: confirm, prepare, dispatch, deliver

### 👑 Admin (`role: 'admin'`)
- Platform analytics dashboard (revenue, users, orders)
- User management: block/unblock, delete accounts
- Restaurant approval workflow
- Global order oversight across all restaurants
- *Admin accounts must be created directly in the database*

---

## 🚀 Deployment

### 1. Database — MongoDB Atlas

```bash
# 1. Create free cluster at mongodb.com/atlas
# 2. Add a database user (readWrite role)
# 3. Whitelist IPs: 0.0.0.0/0
# 4. Copy connection string → set as MONGODB_URI in backend .env
```

### 2. Backend — Render.com

```bash
# 1. Push backend/ folder to GitHub
# 2. New Web Service on render.com → connect repo
# 3. Build Command:  npm install
#    Start Command:  npm start
# 4. Add all environment variables
# 5. After deploy, open Shell tab and run: node seed.js
```

### 3. Frontend — Vercel

```bash
# 1. Push frontend/ folder to GitHub (or same repo)
# 2. Import project on vercel.com
# 3. Framework Preset: Vite
# 4. Add env vars:
#    VITE_API_URL = https://your-render-api.onrender.com/api
#    VITE_STRIPE_PUBLISHABLE_KEY = pk_live_xxx
# 5. Deploy
```

> **Important:** After deploying both, update `CLIENT_URL` in your backend environment variables to match your Vercel frontend URL (fixes CORS).

---

## ⚙️ Environment Variables

### Backend (`backend/.env`)

```env
# Server
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/foodapp
# MongoDB Atlas: mongodb+srv://<user>:<pass>@cluster.mongodb.net/foodapp

# Authentication
JWT_SECRET=your_super_secret_key_at_least_32_chars_long
JWT_EXPIRES_IN=7d

# Stripe (optional for local dev, required for payments)
STRIPE_SECRET_KEY=sk_test_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
STRIPE_WEBHOOK_SECRET=whsec_xxxxxxxxxxxxxxxx

# CORS
CLIENT_URL=http://localhost:5173
```

### Frontend (`frontend/.env`)

```env
VITE_API_URL=http://localhost:5000/api
VITE_STRIPE_PUBLISHABLE_KEY=pk_test_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

| Variable | Required | Description |
|---|---|---|
| `MONGODB_URI` | ✅ Yes | MongoDB connection string |
| `JWT_SECRET` | ✅ Yes | Secret for signing tokens — use a long random string |
| `CLIENT_URL` | ✅ Yes | Frontend origin for CORS (exact URL + port, no trailing slash) |
| `JWT_EXPIRES_IN` | No | Token TTL, e.g. `7d`, `24h`, `30d`. Default: `7d` |
| `STRIPE_SECRET_KEY` | No | Stripe secret key (required only for card payments) |
| `PORT` | No | API server port. Default: `5000` |
| `VITE_API_URL` | ✅ Yes | Full API base URL used by Axios |
| `VITE_STRIPE_PUBLISHABLE_KEY` | No | Stripe publishable key for frontend |

---

## 🔧 Scripts

### Backend

```bash
npm run dev       # Start with nodemon (auto-reload)
npm start         # Start production server
npm run seed      # Seed demo accounts, restaurants, and food items
```

### Frontend

```bash
npm run dev       # Start Vite dev server (http://localhost:5173)
npm run build     # Build for production (outputs to /dist)
npm run preview   # Preview production build locally
```

---

## 📸 Screenshots

| Page | Description |
|---|---|
| **Home Page** | Hero search, category filters, restaurant grid, featured dishes |
| **Restaurant Menu** | Category tabs, veg-only toggle, food cards with Add button |
| **Cart** | Item list with quantity controls, restaurant info, price summary |
| **Checkout** | Delivery address form, payment method selection |
| **Order Tracker** | Animated 6-stage status bar with estimated delivery time |
| **Owner Dashboard** | Stats overview, quick links, recent orders preview |
| **Admin Dashboard** | Platform metrics, orders-by-status chart, top restaurants |

---

## 🐛 Troubleshooting

| Problem | Solution |
|---|---|
| Demo login fails | Run `npm run seed` in the backend folder first |
| CORS error in browser | Set `CLIENT_URL` in backend `.env` to exactly match the frontend URL (including `http://` and port) |
| MongoDB connection refused | Ensure `mongod` is running locally, or verify Atlas Network Access whitelist |
| Stripe payment fails | Use test card `4242 4242 4242 4242`, any future expiry, any CVV |
| Restaurant not appearing publicly | Admin must approve it at `/admin/restaurants` |
| `npm run seed` says "already exists" | This is normal — the script is idempotent and skips existing records |
| JWT expired / redirected to login | Log out and log back in. Extend with `JWT_EXPIRES_IN=30d` in `.env` |

---

## 🗺️ Roadmap

- [ ] Real-time order tracking with **Socket.IO**
- [ ] **Google Maps** delivery tracking integration
- [ ] Ratings and reviews system (customer → restaurant, customer → food)
- [ ] **Push notifications** for order status updates
- [ ] Coupon / promo code system
- [ ] Multi-image support for food items
- [ ] Restaurant analytics dashboard (revenue charts for owners)
- [ ] In-app messaging between customer and restaurant
- [ ] Order scheduling (order in advance)
- [ ] PWA support (installable mobile experience)

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [MongoDB](https://mongodb.com) — Flexible NoSQL database
- [Express.js](https://expressjs.com) — Minimal Node.js framework
- [React](https://reactjs.org) — UI component library
- [Tailwind CSS](https://tailwindcss.com) — Utility-first CSS framework
- [Stripe](https://stripe.com) — Payment processing infrastructure
- [react-hot-toast](https://react-hot-toast.com) — Beautiful toast notifications
- [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) + [DM Sans](https://fonts.google.com/specimen/DM+Sans) — Typography

---

<div align="center">

**Built with ❤️ by the FeastRush Team**

⭐ Star this repo if you found it helpful!

</div>
