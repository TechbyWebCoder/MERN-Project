<div align="center">

# 💰 Fintrak — Personal Finance Tracker

**A modern, full-stack finance management app built with React, Node.js, and MongoDB**

[![React](https://img.shields.io/badge/React-18.2-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat-square&logo=nodedotjs&logoColor=white)](https://nodejs.org)
[![MongoDB](https://img.shields.io/badge/MongoDB-8.0-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://mongodb.com)
[![Vite](https://img.shields.io/badge/Vite-5.0-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-22C55E?style=flat-square)](LICENSE)

<br/>

<a href="https://rzp.io/rzp/mern-6" target="_blank">
  <img src="https://img.shields.io/badge/💳%20Purchase%20Now-FF6B35?style=for-the-badge&logo=buymeacoffee&logoColor=white" />
</a>

<br>

<a href="https://youtu.be/r38QibVgw3c" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20Demo-FF0000?style=for-the-badge&logo=youtube&logoColor=white" />
</a>

</div>

---

## 📌 Overview

Fintrak is a production-ready personal finance tracker that gives you a complete picture of your money. Record every transaction, set monthly budgets with smart alerts, explore visual spending analytics, and export your data — all wrapped in a clean dark/light UI that works seamlessly on any device.

```
Track every dollar  ·  Visualise your habits  ·  Stay within budget  ·  Export anytime
```

---

## ✨ Features

<table>
<tr>
<td>

**🔐 Authentication**
- JWT-based register & login
- bcrypt password hashing (12 rounds)
- Protected routes, 7-day sessions
- Auto-logout on token expiry

</td>
<td>

**💸 Transaction Tracking**
- Add income & expense transactions
- 20+ predefined categories
- Edit and delete with confirmation
- Recurring transaction support

</td>
</tr>
<tr>
<td>

**📊 Dashboard**
- Total balance & monthly KPIs
- Budget progress bar with alerts
- Income vs expenses bar chart
- Top spending categories

</td>
<td>

**📈 Analytics**
- Pie/donut chart — category breakdown
- Grouped bar chart — monthly comparison
- Area/line chart — savings trend
- Month & year picker

</td>
</tr>
<tr>
<td>

**🎯 Budget Management**
- Monthly spending limits
- Configurable alert threshold (50–99%)
- Real-time progress tracking
- Per-category spend breakdown

</td>
<td>

**🔍 Search & Filters**
- Full-text search by description & category
- Filter by type, category, date range
- Sort by date or amount (asc/desc)
- Paginated results (15 per page)

</td>
</tr>
<tr>
<td>

**📥 CSV Export**
- Download any filtered view
- Compatible with Excel, Google Sheets
- Includes date, type, category, amount

</td>
<td>

**🌙 Dark Mode**
- Full light & dark theme
- System preference detection
- Persists across sessions

</td>
</tr>
</table>

---

## 🛠️ Tech Stack

### Frontend
| Technology | Version | Purpose |
|---|---|---|
| [React](https://react.dev) | 18.2 | UI framework |
| [Vite](https://vitejs.dev) | 5.0 | Build tool & dev server |
| [Tailwind CSS](https://tailwindcss.com) | 3.4 | Utility-first styling |
| [React Router](https://reactrouter.com) | v6.21 | Client-side routing |
| [Recharts](https://recharts.org) | 2.10 | Pie, Bar & Area charts |
| [Axios](https://axios-http.com) | 1.6 | HTTP client |
| [React Hot Toast](https://react-hot-toast.com) | 2.4 | Toast notifications |
| [Lucide React](https://lucide.dev) | 0.303 | Icon library |
| [date-fns](https://date-fns.org) | 3.0 | Date formatting |

### Backend
| Technology | Version | Purpose |
|---|---|---|
| [Node.js](https://nodejs.org) | 18+ | JavaScript runtime |
| [Express.js](https://expressjs.com) | 4.18 | Web framework |
| [Mongoose](https://mongoosejs.com) | 8.0 | MongoDB ODM |
| [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) | 9.0 | JWT auth tokens |
| [bcryptjs](https://github.com/dcodeIO/bcrypt.js) | 2.4 | Password hashing |
| [express-validator](https://express-validator.github.io) | 7.0 | Request validation |
| [cors](https://github.com/expressjs/cors) | 2.8 | CORS middleware |
| [morgan](https://github.com/expressjs/morgan) | 1.10 | HTTP request logging |

### Database & DevOps
| Technology | Purpose |
|---|---|
| [MongoDB](https://mongodb.com) | Primary NoSQL database |
| [MongoDB Atlas](https://cloud.mongodb.com) | Managed cloud database (production) |
| [Vercel](https://vercel.com) | Frontend deployment |
| [Render](https://render.com) | Backend deployment |

---

## 📂 Project Structure

```
finance-tracker/
├── 📁 client/                     # React frontend (Vite)
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/            # Reusable UI (Modal, Badge, StatCard, Spinner...)
│   │   │   ├── charts/            # Recharts wrappers (Pie, Bar, Area)
│   │   │   └── layout/            # Sidebar, AppLayout
│   │   ├── context/
│   │   │   ├── AuthContext.jsx    # JWT auth state management
│   │   │   └── ThemeContext.jsx   # Dark/light mode
│   │   ├── hooks/
│   │   │   └── useFinance.js      # useTransactions, useSummary, useBudget
│   │   ├── pages/
│   │   │   ├── Home.jsx           # Public landing page
│   │   │   ├── Login.jsx          # Login form
│   │   │   ├── Register.jsx       # Registration form
│   │   │   ├── Dashboard.jsx      # Overview + charts
│   │   │   ├── Transactions.jsx   # Full CRUD list
│   │   │   ├── Analytics.jsx      # Deep analytics
│   │   │   └── Budget.jsx         # Budget manager
│   │   ├── services/
│   │   │   └── api.js             # Axios instance + all API methods
│   │   └── utils/
│   │       └── helpers.js         # Formatters, colours, constants
│   ├── tailwind.config.js
│   ├── vite.config.js
│   └── package.json
│
├── 📁 server/                     # Express backend
│   ├── controllers/
│   │   ├── authController.js      # register, login, getMe, updateProfile
│   │   ├── transactionController.js # CRUD, summary, categories, CSV export
│   │   └── budgetController.js    # get, set, delete budget
│   ├── middleware/
│   │   └── auth.js                # JWT protect middleware
│   ├── models/
│   │   ├── User.js                # User schema
│   │   ├── Transaction.js         # Transaction schema
│   │   └── Budget.js              # Budget schema
│   ├── routes/
│   │   ├── auth.js
│   │   ├── transactions.js
│   │   └── budget.js
│   ├── server.js                  # Express entry point
│   ├── seed.js                    # Demo data seeder
│   └── package.json
│
├── package.json                   # Root scripts (dev, install:all)
└── README.md
```

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** v18 or higher — [download](https://nodejs.org)
- **npm** v9 or higher (included with Node.js)
- **MongoDB** running locally, or a free [MongoDB Atlas](https://cloud.mongodb.com) cluster

### 1. Clone the repository

```bash
git clone https://github.com/your-username/finance-tracker.git
cd finance-tracker
```

### 2. Install all dependencies

```bash
npm run install:all
```

This installs packages for the root, server, and client in one command.

### 3. Configure the server

```bash
cp server/.env.example server/.env
```

Edit `server/.env` with your values:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/finance-tracker
JWT_SECRET=your_very_long_random_secret_key_here
JWT_EXPIRES_IN=7d
CLIENT_URL=http://localhost:5173
```

> **MongoDB Atlas users:** Replace `MONGO_URI` with your Atlas connection string:
> `mongodb+srv://username:password@cluster.mongodb.net/finance-tracker`

### 4. Configure the client

```bash
cp client/.env.example client/.env
```

```env
VITE_API_URL=http://localhost:5000/api
```

> **Note:** The Vite dev proxy in `vite.config.js` already forwards `/api` requests to `localhost:5000`, so you can also leave this blank for local development.

### 5. Seed demo data (optional)

```bash
cd server && npm run seed
```

This creates two demo accounts with 6 months of realistic transactions:

| Email | Password | Currency |
|---|---|---|
| alex@demo.com | demo1234 | USD |
| priya@demo.com | demo1234 | INR |

> ⚠️ **The seed script wipes and recreates demo data every run.** Real user accounts are unaffected.

### 6. Start the development servers

```bash
# From the project root — runs both servers simultaneously
npm run dev
```

| Service | URL |
|---|---|
| Frontend | http://localhost:5173 |
| Backend API | http://localhost:5000/api |
| Health check | http://localhost:5000/api/health |

---

## 🌐 API Reference

All API routes are prefixed with `/api`. Protected routes require a `Bearer` token in the `Authorization` header.

### Authentication

| Method | Route | Auth | Description |
|---|---|---|---|
| `POST` | `/auth/register` | No | Register a new user |
| `POST` | `/auth/login` | No | Login, returns JWT token |
| `GET` | `/auth/me` | ✅ | Get current user profile |
| `PUT` | `/auth/me` | ✅ | Update name or currency |

<details>
<summary><strong>POST /auth/register — Request body</strong></summary>

```json
{
  "name":     "Jane Smith",
  "email":    "jane@example.com",
  "password": "mypassword",
  "currency": "USD"
}
```

</details>

<details>
<summary><strong>Successful auth response</strong></summary>

```json
{
  "success": true,
  "token": "eyJhbGciOiJIUzI1NiIsInR...",
  "user": {
    "id": "6579abc123...",
    "name": "Jane Smith",
    "email": "jane@example.com",
    "currency": "USD"
  }
}
```

</details>

---

### Transactions

| Method | Route | Auth | Description |
|---|---|---|---|
| `GET` | `/transactions` | ✅ | List transactions (filter, search, paginate) |
| `POST` | `/transactions` | ✅ | Create a transaction |
| `PUT` | `/transactions/:id` | ✅ | Update a transaction |
| `DELETE` | `/transactions/:id` | ✅ | Delete a transaction |
| `GET` | `/transactions/summary` | ✅ | Monthly stats + chart data |
| `GET` | `/transactions/categories` | ✅ | Get all categories |
| `GET` | `/transactions/export` | ✅ | Download CSV |

<details>
<summary><strong>GET /transactions — Query parameters</strong></summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `type` | string | — | `income` or `expense` |
| `category` | string | — | Filter by category name |
| `startDate` | ISO date | — | From this date |
| `endDate` | ISO date | — | To this date |
| `search` | string | — | Search description & category |
| `page` | number | `1` | Page number |
| `limit` | number | `20` | Results per page |
| `sortBy` | string | `date` | `date` or `amount` |
| `sortOrder` | string | `desc` | `asc` or `desc` |

</details>

<details>
<summary><strong>POST /transactions — Request body</strong></summary>

```json
{
  "type":               "expense",
  "amount":             42.50,
  "category":           "Food & Dining",
  "date":               "2025-04-10",
  "description":        "Weekly groceries",
  "isRecurring":        false,
  "recurringInterval":  null
}
```

</details>

<details>
<summary><strong>GET /transactions/summary — Response</strong></summary>

```json
{
  "success": true,
  "data": {
    "monthly":   { "income": 4800, "expense": 2350, "balance": 2450 },
    "allTime":   { "income": 28000, "expense": 14500, "balance": 13500 },
    "categoryBreakdown": [
      { "_id": "Food & Dining", "total": 640, "count": 12 }
    ],
    "monthlyTrend": [
      { "_id": { "year": 2025, "month": 4, "type": "income" }, "total": 4800 }
    ]
  }
}
```

</details>

---

### Budget

| Method | Route | Auth | Description |
|---|---|---|---|
| `GET` | `/budget` | ✅ | Get budget + live spending status |
| `POST` | `/budget` | ✅ | Create or update a monthly budget |
| `DELETE` | `/budget` | ✅ | Remove budget for a month |

<details>
<summary><strong>POST /budget — Request body</strong></summary>

```json
{
  "monthlyLimit":    3000,
  "alertThreshold":  80,
  "month":           3,
  "year":            2025,
  "categoryLimits": [
    { "category": "Food & Dining", "limit": 500 }
  ]
}
```

</details>

---

## 🗄️ Database Models

<details>
<summary><strong>User</strong></summary>

```js
{
  name:      String,   // required, max 50 chars
  email:     String,   // required, unique, lowercase
  password:  String,   // bcrypt hashed, select: false
  currency:  String,   // default: 'USD'
  createdAt: Date,     // auto (timestamps)
  updatedAt: Date,     // auto (timestamps)
}
```

</details>

<details>
<summary><strong>Transaction</strong></summary>

```js
{
  userId:             ObjectId,  // ref: User
  type:               String,    // 'income' | 'expense'
  amount:             Number,    // min: 0.01
  category:           String,    // from CATEGORIES enum
  description:        String,    // optional, max 200 chars
  date:               Date,      // required
  isRecurring:        Boolean,   // default: false
  recurringInterval:  String,    // 'daily'|'weekly'|'monthly'|'yearly'|null
  tags:               [String],  // optional
}
// Indexes: { userId, date: -1 }, { userId, type }, { userId, category }
```

</details>

<details>
<summary><strong>Budget</strong></summary>

```js
{
  userId:          ObjectId,   // ref: User
  monthlyLimit:    Number,     // required, min: 1
  alertThreshold:  Number,     // default: 80 (percent)
  categoryLimits:  [{ category: String, limit: Number }],
  month:           Number,     // 0-11 (JS month index)
  year:            Number,
}
// Unique index: { userId, month, year }
```

</details>

---

## 📸 Screenshots

| Dashboard | Analytics |
|---|---|
| ![Dashboard](https://placehold.co/440x280/0f172a/22c55e?text=Dashboard&font=mono) | ![Analytics](https://placehold.co/440x280/0f172a/0ea5e9?text=Analytics&font=mono) |

| Transactions | Budget |
|---|---|
| ![Transactions](https://placehold.co/440x280/0f172a/f59e0b?text=Transactions&font=mono) | ![Budget](https://placehold.co/440x280/0f172a/8b5cf6?text=Budget&font=mono) |

---

## ☁️ Deployment

### Frontend → Vercel

1. Push `client/` to GitHub
2. Import the repo on [vercel.com](https://vercel.com)
3. Set the **root directory** to `client/`
4. Set **build command** to `npm run build` and **output directory** to `dist`
5. Add environment variable:
   ```env
   VITE_API_URL=https://your-backend.onrender.com/api
   ```

### Backend → Render

1. Push `server/` to GitHub
2. Create a new **Web Service** on [render.com](https://render.com)
3. Set the **root directory** to `server/`
4. Set **build command**: `npm install`
5. Set **start command**: `node server.js`
6. Add all environment variables:
   ```env
   MONGO_URI=mongodb+srv://...
   JWT_SECRET=long_random_string
   JWT_EXPIRES_IN=7d
   CLIENT_URL=https://your-app.vercel.app
   ```

### Database → MongoDB Atlas

1. Create a free **M0 cluster** at [cloud.mongodb.com](https://cloud.mongodb.com)
2. Create a database user with read/write access
3. Whitelist `0.0.0.0/0` under Network Access (required for Render)
4. Copy your connection string and set it as `MONGO_URI`

> **Important:** Update `CLIENT_URL` on Render to match your Vercel URL to allow CORS correctly.

---

## 📜 Available Scripts

### Root

| Script | Command | Description |
|---|---|---|
| `dev` | `npm run dev` | Run frontend + backend simultaneously |
| `install:all` | `npm run install:all` | Install all dependencies (root + server + client) |
| `server` | `npm run server` | Start backend only (nodemon) |
| `client` | `npm run client` | Start frontend only (vite) |
| `build` | `npm run build` | Production build of the client |

### Server only (`cd server`)

| Script | Command | Description |
|---|---|---|
| `dev` | `npm run dev` | Start with nodemon (auto-restart) |
| `start` | `npm start` | Production start |
| `seed` | `npm run seed` | Load demo data into MongoDB |

---

## 🔧 Environment Variables

### `server/.env`

| Variable | Required | Default | Description |
|---|---|---|---|
| `PORT` | No | `5000` | Express server port |
| `MONGO_URI` | **Yes** | — | MongoDB connection string |
| `JWT_SECRET` | **Yes** | — | Secret for signing tokens — **keep private** |
| `JWT_EXPIRES_IN` | No | `7d` | Token expiry: `1h`, `7d`, `30d`, etc. |
| `CLIENT_URL` | No | `http://localhost:5173` | Allowed CORS origin |

### `client/.env`

| Variable | Required | Default | Description |
|---|---|---|---|
| `VITE_API_URL` | No | `/api` | API base URL (leave blank for local Vite proxy) |

---

## 🌱 Demo Data

The seed script creates two realistic demo accounts with 6 months of data each.

```bash
cd server
npm run seed
```

### Demo Accounts

| Name | Email | Password | Currency |
|---|---|---|---|
| Alex Johnson | alex@demo.com | demo1234 | USD |
| Priya Sharma | priya@demo.com | demo1234 | INR |

### What gets generated (~200 transactions per user)

- ✅ Monthly salary deposit on the 1st
- ✅ Monthly rent on the 1st
- ✅ Weekly grocery shopping (×4/month)
- ✅ 5 recurring bills — electricity, internet, phone, Netflix, Spotify
- ✅ 10–18 random expenses across all categories per month
- ✅ Occasional extra income — freelance, dividends, gifts
- ✅ Monthly budgets with category sub-limits

---

## 🗺️ Roadmap

| Feature | Priority | Status |
|---|---|---|
| Email verification & password reset | High | Planned |
| PDF export | High | Planned |
| AI spending insights (Claude API) | Medium | Planned |
| Multi-currency conversion | Medium | Planned |
| Shared household budgets | Medium | Planned |
| Bank statement import (OFX/CSV) | Medium | Planned |
| React Native mobile app | Low | Planned |

---


## 🐛 Known Issues

- No self-service password reset (admin reset only in current version)
- No email verification on registration
- Sessions are not invalidated across devices on logout

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Recharts](https://recharts.org) — beautiful React charting library
- [Lucide](https://lucide.dev) — clean, consistent icon set
- [Tailwind CSS](https://tailwindcss.com) — utility-first CSS framework
- [MongoDB Atlas](https://cloud.mongodb.com) — free-tier cloud database

---

<div align="center">

Made with ❤️ using **React · Node.js · Express · MongoDB**

⭐ Star this repo if you found it useful!

</div>
