<div align="center">

<img src="https://img.shields.io/badge/EstateHub-Real%20Estate%20Platform-0EA5E9?style=for-the-badge&logo=home-assistant&logoColor=white" alt="EstateHub" />

# 🏠 EstateHub — Full-Stack Real Estate Platform

**A modern, production-ready real estate marketplace built for the Indian market.**  
Search, list, and manage properties for rent and sale with role-based access, JWT authentication, and Google Maps integration.

<br/>

[![React](https://img.shields.io/badge/React-18.2-61DAFB?style=flat-square&logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-68A063?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-8.0-00ED64?style=flat-square&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Express](https://img.shields.io/badge/Express-4.18-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.4-38BDF8?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![JWT](https://img.shields.io/badge/JWT-Auth-000000?style=flat-square&logo=json-web-tokens&logoColor=white)](https://jwt.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)

<br/>

<a href="https://rzp.io/rzp/mern-3" target="_blank">
  <img src="https://img.shields.io/badge/💳%20Purchase%20Now-FF6B35?style=for-the-badge&logo=buymeacoffee&logoColor=white" />
</a>

<br>

<a href="https://youtu.be/hRL3JFl4U7w" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20Demo-FF0000?style=for-the-badge&logo=youtube&logoColor=white" />
</a>


</div>

---

## 📋 Table of Contents

- [✨ Features](#-features)
- [🛠 Tech Stack](#-tech-stack)
- [🚀 Quick Start](#-quick-start)
- [⚙️ Environment Variables](#️-environment-variables)
- [📁 Project Structure](#-project-structure)
- [🗄️ Database Models](#️-database-models)
- [📡 API Reference](#-api-reference)
- [👤 User Roles](#-user-roles)
- [🌐 Deployment](#-deployment)
- [📄 License](#-license)

---

## ✨ Features

### 🔐 Authentication & Security
- JWT-based stateless authentication with 30-day token expiry
- bcrypt password hashing (12 salt rounds)
- Role-based access control (RBAC) enforced on every protected route
- Axios interceptors for automatic token attachment and global 401 handling

### 🏘️ Property Listings
- Full CRUD for property listings (create, read, update, delete)
- 8 property types: apartment, house, villa, studio, commercial, plot, penthouse
- Dual categories: For Rent and For Sale
- Image gallery with multiple URLs, amenities checklist, and floor details
- Admin approval workflow — listings start as `pending` and go live after approval
- Featured listings highlighted on the homepage
- View counter per listing

### 🔍 Search & Discovery
- Full-text search across title, description, city, and address
- 8+ filter parameters: price range, city, type, category, bedrooms, bathrooms, furnishing
- URL-synced filters — shareable search results
- Grid view (1–4 column responsive) and Map view (split panel)
- Google Maps API with custom markers and InfoWindow property cards
- Pagination with smart ellipsis

### ❤️ Favourites
- Toggle save/unsave from any property card or detail page
- Persistent across sessions (stored server-side per user)
- Dedicated Saved Properties page

### 💬 Inquiry System
- Buyers send messages directly to property owners
- Owners reply via the platform — full conversation thread
- Status tracking: pending → replied → closed
- Role-scoped: buyers see sent; owners see received

### 🛡️ Admin Panel
- Real-time analytics dashboard (users, properties, inquiries by status and role)
- Approve / reject / delete any property listing
- Activate, deactivate, or delete any user account
- Recent activity feed for properties and user registrations

---

## 🛠 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| **Frontend** | React 18 + Vite 5 | UI with fast HMR development server |
| **Styling** | Tailwind CSS 3.4 | Utility-first CSS with custom design tokens |
| **Routing** | React Router v6 | Client-side routing with protected & guest route wrappers |
| **HTTP** | Axios | API calls with request/response interceptors |
| **Maps** | @react-google-maps/api | Google Maps with markers and InfoWindows |
| **Icons** | lucide-react | Lightweight, consistent SVG icon set |
| **Toasts** | react-hot-toast | Non-blocking notifications |
| **Backend** | Node.js + Express.js | REST API server |
| **Database** | MongoDB + Mongoose | Document database with ODM schemas and validation |
| **Auth** | jsonwebtoken + bcryptjs | Stateless JWT auth with secure password hashing |
| **Build** | Vite 5 | Lightning-fast frontend build tool |

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** 18+ — [nodejs.org](https://nodejs.org)
- **MongoDB** — [local install](https://www.mongodb.com/try/download/community) or [Atlas free cluster](https://cloud.mongodb.com)
- **npm** (bundled with Node.js)

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/real-estate-app.git
cd real-estate-app
```

### 2. Configure & Install the Backend

```bash
cd server
cp .env.example .env
# Edit .env with your MongoDB URI and JWT secret (see Environment Variables below)
npm install
```

### 3. Seed Demo Data *(recommended)*

```bash
node seed.js
```

This creates **3 demo accounts** and **8 sample property listings** across Indian cities.

### 4. Configure & Install the Frontend

```bash
cd ../client
cp .env.example .env
# Optionally add your Google Maps API key
npm install
```

### 5. Start Both Servers

**Terminal 1 — Backend:**
```bash
cd server
npm run dev
# ✅ Server running on http://localhost:5000
```

**Terminal 2 — Frontend:**
```bash
cd client
npm run dev
# ✅ App running on http://localhost:5173
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

---

## 🔑 Demo Accounts

After running `node seed.js`, use these accounts to explore every role:

| Role | Email | Password | Access |
|---|---|---|---|
| 🛡️ **Admin** | `admin@demo.com` | `password123` | Full platform control |
| 🏷️ **Owner** | `owner@demo.com` | `password123` | List & manage properties |
| 🏠 **Buyer** | `buyer@demo.com` | `password123` | Search & save listings |

> These credentials are also available as quick-fill buttons on the **Login page**.

---

## ⚙️ Environment Variables

### `server/.env`

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/realestate
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
CLIENT_URL=http://localhost:5173
NODE_ENV=development
```

| Variable | Required | Description |
|---|---|---|
| `PORT` | No | Express server port (default: 5000) |
| `MONGO_URI` | **Yes** | MongoDB connection string (local or Atlas) |
| `JWT_SECRET` | **Yes** | Secret key for signing JWT tokens — use a long random string in production |
| `CLIENT_URL` | **Yes** | Frontend URL for CORS allowlist |
| `NODE_ENV` | No | `development` or `production` |

### `client/.env`

```env
VITE_API_URL=http://localhost:5000
VITE_GOOGLE_MAPS_API_KEY=YOUR_GOOGLE_MAPS_API_KEY_HERE
```

| Variable | Required | Description |
|---|---|---|
| `VITE_API_URL` | **Yes** | Backend API base URL |
| `VITE_GOOGLE_MAPS_API_KEY` | No | Google Maps JavaScript API key — app works without it (shows placeholder) |

> **Getting a Google Maps API Key:**
> 1. Go to [Google Cloud Console](https://console.cloud.google.com)
> 2. Enable **Maps JavaScript API**
> 3. Create an API Key under **Credentials**
> 4. Restrict it to your domain in production

---

## 📁 Project Structure

```
real-estate-app/
├── package.json                    ← Root scripts
├── README.md
│
├── server/                         ← Node.js / Express backend
│   ├── server.js                   ← App entry point, DB connection, middleware
│   ├── seed.js                     ← Demo data seeder
│   ├── package.json
│   ├── .env.example
│   │
│   ├── controllers/
│   │   ├── authController.js       ← register, login, getMe
│   │   ├── propertyController.js   ← CRUD + search + my-listings
│   │   ├── favoriteController.js   ← toggle, list, check
│   │   ├── inquiryController.js    ← create, list, reply, delete
│   │   └── adminController.js      ← stats, users, property status
│   │
│   ├── models/
│   │   ├── User.js                 ← name, email, password, role, isActive
│   │   ├── Property.js             ← title, price, location, images, amenities
│   │   ├── Favorite.js             ← userId + propertyId (unique compound index)
│   │   └── Inquiry.js              ← userId, propertyId, ownerId, message, reply
│   │
│   ├── routes/
│   │   ├── auth.js                 ← /api/auth/*
│   │   ├── properties.js           ← /api/properties/*
│   │   ├── favorites.js            ← /api/favorites/*
│   │   ├── inquiries.js            ← /api/inquiries/*
│   │   ├── admin.js                ← /api/admin/*
│   │   └── users.js                ← /api/users/*
│   │
│   └── middleware/
│       └── auth.js                 ← protect + authorize(roles)
│
└── client/                         ← React / Vite frontend
    ├── index.html
    ├── vite.config.js              ← Proxy /api → localhost:5000
    ├── tailwind.config.js
    ├── postcss.config.js
    ├── .env.example
    │
    └── src/
        ├── main.jsx                ← React DOM entry point
        ├── App.jsx                 ← Routes + ProtectedRoute + GuestRoute
        ├── index.css               ← Global styles, design system classes
        │
        ├── context/
        │   └── AuthContext.jsx     ← Global auth state (login, register, logout)
        │
        ├── services/
        │   └── api.js              ← Axios instance + all API call functions
        │
        ├── components/
        │   ├── common/
        │   │   ├── LoadingSpinner.jsx
        │   │   └── Pagination.jsx
        │   ├── layout/
        │   │   ├── Navbar.jsx
        │   │   └── Footer.jsx
        │   └── property/
        │       ├── PropertyCard.jsx      ← Listing card with favourite toggle
        │       ├── SearchFilters.jsx     ← Filter form (basic + advanced)
        │       ├── PropertyMap.jsx       ← Google Maps with markers
        │       └── PropertyForm.jsx      ← Shared Add/Edit form (5 sections)
        │
        └── pages/
            ├── public/
            │   ├── HomePage.jsx          ← Hero, categories, featured, latest
            │   ├── PropertiesPage.jsx    ← Search page (grid + map view)
            │   └── PropertyDetailPage.jsx ← Full detail, gallery, inquiry form
            ├── auth/
            │   ├── LoginPage.jsx
            │   └── RegisterPage.jsx
            ├── buyer/
            │   ├── FavoritesPage.jsx
            │   └── InquiriesPage.jsx
            ├── owner/
            │   ├── AddPropertyPage.jsx
            │   ├── EditPropertyPage.jsx
            │   └── ManageListingsPage.jsx
            └── admin/
                ├── AdminDashboard.jsx
                ├── AdminUsers.jsx
                └── AdminListings.jsx
```

---

## 🗄️ Database Models

### User
```js
{
  name:     String,   // required
  email:    String,   // required, unique
  password: String,   // bcrypt hashed, select: false
  role:     enum['buyer', 'owner', 'admin'],  // default: 'buyer'
  phone:    String,
  avatar:   String,
  isActive: Boolean   // default: true
}
```

### Property
```js
{
  title:       String,   // required
  description: String,   // required, max 5000 chars
  price:       Number,   // required
  priceType:   enum['total', 'per_month'],
  category:    enum['rent', 'sale'],          // required
  type:        enum['apartment', 'house', 'villa', 'studio', 'commercial', 'plot', 'penthouse'],
  status:      enum['pending', 'approved', 'rejected', 'sold', 'rented'],  // default: 'pending'
  location: {
    address: String, city: String, state: String,
    country: String, zipCode: String,
    coordinates: { lat: Number, lng: Number }
  },
  bedrooms:    Number,
  bathrooms:   Number,
  area:        Number,
  areaUnit:    String,
  floor:       Number,
  totalFloors: Number,
  yearBuilt:   Number,
  furnishing:  enum['unfurnished', 'semi-furnished', 'fully-furnished'],
  amenities:   [String],
  images:      [String],
  ownerId:     ObjectId → User,  // required
  isFeatured:  Boolean,
  views:       Number
}
```

### Favorite
```js
{
  userId:     ObjectId → User,      // required
  propertyId: ObjectId → Property   // required
  // Unique compound index: { userId, propertyId }
}
```

### Inquiry
```js
{
  userId:     ObjectId → User,      // buyer — required
  propertyId: ObjectId → Property,  // required
  ownerId:    ObjectId → User,      // owner — required
  message:    String,               // required, max 2000 chars
  status:     enum['pending', 'replied', 'closed'],  // default: 'pending'
  reply:      String,               // owner's reply
  repliedAt:  Date
}
```

---

## 📡 API Reference

### Base URL
- **Local:** `http://localhost:5000/api`
- **Production:** `https://your-backend.onrender.com/api`

### Authentication
All protected routes require `Authorization: Bearer <token>` in the request header.

---

### 🔐 Auth Routes

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/auth/register` | Public | Register new user |
| `POST` | `/auth/login` | Public | Login, receive JWT |
| `GET` | `/auth/me` | Any | Get current user profile |

**POST `/auth/register`**
```json
{ "name": "Rahul Sharma", "email": "rahul@example.com", "password": "secret123", "role": "buyer" }
```

**POST `/auth/login`**
```json
{ "email": "rahul@example.com", "password": "secret123" }
```

---

### 🏘️ Property Routes

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/properties` | Public | Search/list properties |
| `GET` | `/properties/:id` | Public | Get single property |
| `GET` | `/properties/my-listings` | Owner/Admin | Owner's own listings |
| `POST` | `/properties` | Owner/Admin | Create listing |
| `PUT` | `/properties/:id` | Owner/Admin | Update listing |
| `DELETE` | `/properties/:id` | Owner/Admin | Delete listing |

**GET `/properties` — Query Parameters**

| Param | Type | Example | Description |
|---|---|---|---|
| `search` | String | `Bandra` | Full-text search |
| `category` | String | `rent` | `rent` or `sale` |
| `type` | String | `apartment` | Property type |
| `city` | String | `Mumbai` | City name (case-insensitive) |
| `minPrice` | Number | `10000` | Minimum price |
| `maxPrice` | Number | `100000` | Maximum price |
| `bedrooms` | Number | `2` | Minimum bedrooms |
| `bathrooms` | Number | `1` | Minimum bathrooms |
| `furnishing` | String | `fully-furnished` | Furnishing status |
| `featured` | Boolean | `true` | Featured only |
| `status` | String | `approved` | Default: `approved` |
| `page` | Number | `1` | Page number |
| `limit` | Number | `12` | Results per page |

---

### ❤️ Favorites Routes

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/favorites` | Any logged-in | Get saved properties |
| `POST` | `/favorites` | Any logged-in | Toggle favourite |
| `GET` | `/favorites/check/:id` | Any logged-in | Check if property is saved |

---

### 💬 Inquiry Routes

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/inquiries` | Any logged-in | Send inquiry to owner |
| `GET` | `/inquiries` | Any logged-in | Get inquiries (role-scoped) |
| `PUT` | `/inquiries/:id/reply` | Owner/Admin | Reply to inquiry |
| `DELETE` | `/inquiries/:id` | Any logged-in | Delete inquiry |

---

### 🛡️ Admin Routes

> All admin routes require `Authorization: Bearer <admin-token>`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/admin/stats` | Platform analytics |
| `GET` | `/admin/users` | Paginated user list |
| `PUT` | `/admin/users/:id` | Activate/deactivate or change role |
| `DELETE` | `/admin/users/:id` | Delete user permanently |
| `GET` | `/admin/properties` | All properties (any status) |
| `PUT` | `/admin/properties/:id/status` | Approve / reject listing |

---

### Response Format

All endpoints return a consistent JSON structure:

```json
// Success
{ "success": true, "data": { ... } }

// Error
{ "success": false, "message": "Human-readable error description" }
```

---

## 👤 User Roles

| Feature | Buyer | Owner | Admin |
|---|:---:|:---:|:---:|
| Browse properties | ✅ | ✅ | ✅ |
| Search & filter | ✅ | ✅ | ✅ |
| View property details | ✅ | ✅ | ✅ |
| Save to favourites | ✅ | ✅ | ✅ |
| Send inquiry | ✅ | ❌ | ❌ |
| View sent inquiries | ✅ | ❌ | ❌ |
| List a property | ❌ | ✅ | ✅ |
| Edit own property | ❌ | ✅ | ✅ |
| Delete own property | ❌ | ✅ | ✅ |
| Reply to inquiries | ❌ | ✅ | ✅ |
| Approve / reject listings | ❌ | ❌ | ✅ |
| Manage all users | ❌ | ❌ | ✅ |
| View platform analytics | ❌ | ❌ | ✅ |
| Delete any content | ❌ | ❌ | ✅ |

---

## 🌐 Deployment

### Frontend → Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)

1. Push the `client/` directory to GitHub
2. Import the repository on [vercel.com](https://vercel.com)
3. Set **Root Directory** to `client`
4. Set **Framework Preset** to `Vite`
5. Add environment variables:
   ```
   VITE_API_URL=https://your-backend.onrender.com
   VITE_GOOGLE_MAPS_API_KEY=your_key
   ```
6. Deploy — auto-deploys on every push to `main`

### Backend → Render

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)

1. Push the `server/` directory to GitHub
2. Create a **Web Service** on [render.com](https://render.com)
3. Set **Build Command**: `npm install`
4. Set **Start Command**: `node server.js`
5. Add environment variables:
   ```
   MONGO_URI=mongodb+srv://...
   JWT_SECRET=your_long_random_secret
   CLIENT_URL=https://your-app.vercel.app
   NODE_ENV=production
   ```

### Database → MongoDB Atlas

1. Create a free **M0 cluster** at [cloud.mongodb.com](https://cloud.mongodb.com)
2. Create a database user with read/write access
3. Under **Network Access**, allow `0.0.0.0/0` (all IPs for Render)
4. Copy the connection string and set it as `MONGO_URI`

---

## 🗺️ Roadmap

- [ ] File upload via Cloudinary (replace URL input)
- [ ] Real-time chat with Socket.io
- [ ] Email notifications (Nodemailer + SendGrid)
- [ ] AI price prediction endpoint
- [ ] Saved search alerts
- [ ] Multi-language support (Hindi, Marathi)
- [ ] Property comparison view
- [ ] Mortgage calculator widget

---


## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

```
MIT License — free to use, modify, and distribute for personal and commercial projects.
Attribution appreciated but not required.
```

---

## 🙏 Acknowledgements

- [React](https://reactjs.org/) — UI library
- [Tailwind CSS](https://tailwindcss.com/) — Styling
- [Mongoose](https://mongoosejs.com/) — MongoDB ODM
- [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) — JWT implementation
- [bcryptjs](https://github.com/dcodeIO/bcrypt.js) — Password hashing
- [@react-google-maps/api](https://react-google-maps-api-docs.netlify.app/) — Maps integration
- [lucide-react](https://lucide.dev/) — Icon system
- [react-hot-toast](https://react-hot-toast.com/) — Toast notifications
- [Unsplash](https://unsplash.com/) — Demo property images

---

<div align="center">

Made with ❤️ for the Indian real estate market

**[⬆ Back to top](#-estatehub--full-stack-real-estate-platform)**

</div>
