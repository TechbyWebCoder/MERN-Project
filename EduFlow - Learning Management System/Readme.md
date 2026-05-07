<div align="center">

# 🎓 EduFlow — Learning Management System

[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18.x-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.x-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://mongodb.com/)
[![Express](https://img.shields.io/badge/Express-4.x-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-3.x-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Socket.io](https://img.shields.io/badge/Socket.IO-4.x-010101?style=for-the-badge&logo=socketdotio&logoColor=white)](https://socket.io/)

**A full-stack, production-ready Learning Management System built with the MERN stack.**
Connect students and instructors on one modern platform — with role-based dashboards, real-time notifications, video lessons, and admin analytics.

<a href="https://rzp.io/rzp/mern-2" target="_blank">
  <img src="https://img.shields.io/badge/💳%20Purchase%20Now-FF6B35?style=for-the-badge&logo=buymeacoffee&logoColor=white" />
</a>

<br>

<a href="https://youtu.be/FU0Z2NmU7eg" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20Demo-FF0000?style=for-the-badge&logo=youtube&logoColor=white" />
</a>

</div>

---

## 📋 Table of Contents

- [✨ Features](#-features)
- [🛠 Tech Stack](#-tech-stack)
- [🗂 Project Structure](#-project-structure)
- [⚡ Quick Start](#-quick-start)
- [🔧 Environment Variables](#-environment-variables)
- [🌱 Seeding Demo Data](#-seeding-demo-data)
- [🌐 API Reference](#-api-reference)
- [🗄 Database Schema](#-database-schema)
- [📱 Frontend Pages](#-frontend-pages)
- [🔐 Authentication & Roles](#-authentication--roles)
- [🚀 Deployment](#-deployment)
- [📄 Documentation](#-documentation)
- [🗺️ Roadmap](#-roadmap)
- [📝 License](#-license)

---

## ✨ Features

### 🎓 For Students
- Browse and search courses with filters (category, level, price, rating, sort)
- One-click enrollment in free and paid courses
- Video course player with lesson-by-lesson progress tracking
- Mark lessons complete — progress auto-saves in real time
- Rate and review courses (enrolled students only)
- Personal dashboard with learning stats and continue-learning grid
- Real-time notifications via Socket.IO

### 👨‍🏫 For Instructors
- Create and publish multi-lesson courses with thumbnails
- Upload video lessons via Cloudinary or paste an external URL
- Set free preview lessons to attract enrollments
- Submit courses for admin review — receive instant notification on approval
- Track enrollments, revenue, and average ratings per course
- Full course and lesson CRUD with a modal-based lesson editor

### 🛡️ For Admins
- Approve or reject instructor-submitted courses
- Manage all platform users — block, unblock, change roles, delete
- Platform analytics: monthly enrollment bar chart + revenue line chart
- Real-time stat cards: users, courses, enrollments, total revenue
- Pending approval alert banner with direct action link
- Recent users table and top courses leaderboard

### 🔧 Platform-Wide
- JWT authentication with bcrypt password hashing (12 salt rounds)
- Role-based access control (Student / Instructor / Admin)
- Fully responsive dark-themed UI with custom animations
- Cloudinary integration for image and video storage
- Socket.IO real-time event system for notifications
- Search & filtering with MongoDB text indexes and aggregation pipeline

---

## 🛠 Tech Stack

| Layer | Technology | Version | Purpose |
|-------|-----------|---------|---------|
| **Frontend** | React | 18.x | Component-based UI |
| **Frontend** | Vite | 5.x | Fast dev server & bundler |
| **Frontend** | Tailwind CSS | 3.x | Utility-first styling |
| **Frontend** | React Router | 6.x | Client-side routing |
| **Frontend** | Axios | 1.x | HTTP client with interceptors |
| **Frontend** | Recharts | 2.x | Admin analytics charts |
| **Frontend** | Lucide React | 0.29x | SVG icon library |
| **Frontend** | Socket.IO Client | 4.x | Real-time events |
| **Frontend** | React Hot Toast | 2.x | Toast notifications |
| **Backend** | Node.js | 18.x | JavaScript runtime |
| **Backend** | Express.js | 4.x | Web framework |
| **Backend** | Mongoose | 7.x | MongoDB ODM |
| **Backend** | jsonwebtoken | 9.x | JWT auth |
| **Backend** | bcryptjs | 2.x | Password hashing |
| **Backend** | Socket.IO | 4.x | WebSocket server |
| **Backend** | Multer + Cloudinary | 1.x | File uploads |
| **Backend** | express-validator | 7.x | Input validation |
| **Database** | MongoDB | 7.x | NoSQL document store |

---

## 🗂 Project Structure

```
eduflow-lms/
│
├── backend/
│   ├── config/
│   │   ├── db.js                   # MongoDB connection
│   │   └── cloudinary.js           # Cloudinary + Multer config
│   ├── controllers/
│   │   ├── authController.js       # Register, login, profile
│   │   ├── courseController.js     # CRUD + instructor stats
│   │   ├── lessonController.js     # Add, update, delete lessons
│   │   ├── enrollmentController.js # Enroll, progress, completion
│   │   ├── adminController.js      # Users, approvals, analytics
│   │   └── reviewController.js     # Course ratings & reviews
│   ├── middleware/
│   │   ├── auth.js                 # JWT protect + authorize + generateToken
│   │   └── validate.js             # express-validator rules
│   ├── models/
│   │   ├── User.js                 # User schema with bcrypt pre-save hook
│   │   ├── Course.js               # Course + embedded Lesson schema
│   │   ├── Enrollment.js           # Progress tracking schema
│   │   └── Review.js               # Ratings with post-save avg hook
│   ├── routes/
│   │   ├── auth.js
│   │   ├── courses.js
│   │   ├── lessons.js
│   │   ├── enrollment.js
│   │   ├── admin.js
│   │   └── reviews.js
│   ├── seed.js                     # Demo user seeder
│   ├── server.js                   # Entry point (dotenv must be first)
│   ├── package.json
│   └── .env.example
│
├── frontend/
│   ├── src/
│   │   ├── components/common/
│   │   │   ├── Navbar.jsx          # Role-aware sticky navbar
│   │   │   ├── Footer.jsx
│   │   │   ├── CourseCard.jsx      # Reusable course card component
│   │   │   └── UI.jsx              # LoadingSpinner, EmptyState, Modal, StatCard, ProgressBar
│   │   ├── context/
│   │   │   └── AuthContext.jsx     # Global JWT auth state + helpers
│   │   ├── pages/
│   │   │   ├── public/             # Home, Courses, CourseDetail
│   │   │   ├── auth/               # Login, Register
│   │   │   ├── student/            # Dashboard, MyCourses, CoursePlayer, Profile
│   │   │   ├── instructor/         # Dashboard, CreateCourse, EditCourse, ManageLessons
│   │   │   └── admin/              # Dashboard, UserManagement, CourseManagement
│   │   ├── services/
│   │   │   └── api.js              # Axios instance + authAPI, courseAPI, enrollmentAPI, adminAPI, reviewAPI
│   │   ├── App.jsx                 # Router + ProtectedRoute + GuestRoute guards
│   │   ├── main.jsx
│   │   └── index.css               # Tailwind directives + custom design tokens
│   ├── index.html
│   ├── vite.config.js              # Vite config with /api proxy to :5000
│   ├── tailwind.config.js          # Custom colors: primary, accent, surface
│   ├── postcss.config.js
│   ├── package.json
│   └── .env.example
│
├── package.json                    # Root-level install:all + dev scripts
└── README.md
```

---

## ⚡ Quick Start

### Prerequisites

| Tool | Version | Download |
|------|---------|----------|
| Node.js | 18+ | [nodejs.org](https://nodejs.org) |
| MongoDB | 7.x Community | [mongodb.com/try/download/community](https://www.mongodb.com/try/download/community) |
| Git | Any | [git-scm.com](https://git-scm.com) |

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/eduflow-lms.git
cd eduflow-lms
```

### 2. Install Dependencies

```bash
# Backend
cd backend && npm install

# Frontend
cd ../frontend && npm install
```

### 3. Set Up Environment Variables

```bash
# Backend
cd backend
cp .env.example .env
# → Edit .env with your MongoDB URI, JWT secret, and Cloudinary keys

# Frontend
cd ../frontend
cp .env.example .env
# → Already set to http://localhost:5000/api for local dev
```

### 4. Start MongoDB

```bash
# Windows (MongoDB installed as a service)
net start MongoDB

# macOS / Linux
mongod
```

### 5. Seed Demo Users

```bash
cd backend
npm run seed
```

```
✅ Demo users created:
   admin@demo.com      / demo123
   instructor@demo.com / demo123
   student@demo.com    / demo123
```

### 6. Run Both Servers

```bash
# Terminal 1 — Backend API (port 5000)
cd backend && npm run dev

# Terminal 2 — Frontend (port 5173)
cd frontend && npm run dev
```

**Open [http://localhost:5173](http://localhost:5173) in your browser** 🎉

> The Vite dev server automatically proxies `/api/*` to `http://localhost:5000` — no CORS issues in development.

---

## 🔧 Environment Variables

### `backend/.env`

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/lms_db
JWT_SECRET=YourSuperSecretKey1234567890AbcdefghijKlmn
JWT_EXPIRE=7d
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
CLIENT_URL=http://localhost:5173
```

> ⚠️ **Critical:** `require('dotenv').config()` must be the **first line** of `server.js`. No quotes around values. No spaces around `=`.

### `frontend/.env`

```env
VITE_API_URL=http://localhost:5000/api
```

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `MONGO_URI` | ✅ Yes | — | MongoDB connection string |
| `JWT_SECRET` | ✅ Yes | — | Minimum 32-character secret key |
| `JWT_EXPIRE` | No | `7d` | Token expiry duration |
| `CLOUDINARY_*` | For uploads | — | Cloud Name, API Key, API Secret |
| `CLIENT_URL` | No | `http://localhost:5173` | CORS allowed origin |
| `VITE_API_URL` | No | `/api` (proxied) | Backend API base URL |

---

## 🌱 Seeding Demo Data

### Demo Accounts (run `npm run seed`)

| Role | Email | Password | Redirects To |
|------|-------|----------|-------------|
| 👑 Admin | `admin@demo.com` | `demo123` | `/admin` |
| 👨‍🏫 Instructor | `instructor@demo.com` | `demo123` | `/instructor` |
| 🎓 Student | `student@demo.com` | `demo123` | `/dashboard` |

### 20 Demo Courses

```bash
# Run from the backend/ directory
node -e "
require('dotenv').config();
const mongoose=require('mongoose'),Course=require('./models/Course'),User=require('./models/User');
const courses=[
  {title:'Complete React Developer Bootcamp',category:'Web Development',level:'Beginner',price:999},
  {title:'Node.js & Express REST API Masterclass',category:'Web Development',level:'Intermediate',price:1299},
  {title:'Python for Data Science & Machine Learning',category:'Data Science',level:'Beginner',price:1499},
  {title:'Full Stack MERN Development',category:'Web Development',level:'Advanced',price:1999},
  {title:'UI/UX Design with Figma',category:'Design',level:'Beginner',price:799},
  {title:'DevOps with Docker & Kubernetes',category:'DevOps',level:'Advanced',price:1799},
  {title:'Deep Learning with TensorFlow',category:'Machine Learning',level:'Advanced',price:1699},
  {title:'Flutter Mobile App Development',category:'Mobile Development',level:'Intermediate',price:1199},
  {title:'Digital Marketing Fundamentals',category:'Marketing',level:'Beginner',price:699},
  {title:'Photography Masterclass',category:'Photography',level:'Beginner',price:599},
  {title:'TypeScript Complete Guide',category:'Web Development',level:'Intermediate',price:899},
  {title:'AWS Cloud Practitioner to Solutions Architect',category:'DevOps',level:'Intermediate',price:1599},
  {title:'React Native for iOS & Android',category:'Mobile Development',level:'Intermediate',price:1099},
  {title:'Graphic Design Bootcamp',category:'Design',level:'Beginner',price:749},
  {title:'Business Analytics with Excel & Power BI',category:'Business',level:'Beginner',price:849},
  {title:'Ethical Hacking & Cybersecurity',category:'DevOps',level:'Intermediate',price:1399},
  {title:'Music Production with FL Studio',category:'Music',level:'Beginner',price:649},
  {title:'Vue.js 3 Complete Course',category:'Web Development',level:'Intermediate',price:999},
  {title:'SQL & PostgreSQL for Beginners',category:'Data Science',level:'Beginner',price:0},
  {title:'Entrepreneurship & Startup Fundamentals',category:'Business',level:'Beginner',price:499},
];
async function run(){
  await mongoose.connect(process.env.MONGO_URI);
  const inst=await User.findOne({role:'instructor'});
  if(!inst){console.error('Run npm run seed first');process.exit(1);}
  await Course.deleteMany({instructor:inst._id});
  const res=await Course.insertMany(courses.map(c=>({...c,
    description:'Learn '+c.title+' with hands-on projects.',
    shortDescription:'Master '+c.title.split(' ')[0]+' from scratch.',
    instructor:inst._id,isPublished:true,isApproved:true,
    enrollmentCount:Math.floor(Math.random()*500)+10,
    averageRating:+(3.5+Math.random()*1.5).toFixed(1),
    totalRatings:Math.floor(Math.random()*200)+5,
    lessons:[
      {title:'Introduction',videoUrl:'',duration:300,isFree:true,order:0},
      {title:'Setup',videoUrl:'',duration:600,isFree:true,order:1},
      {title:'Core Concepts 1',videoUrl:'',duration:1200,isFree:false,order:2},
      {title:'Core Concepts 2',videoUrl:'',duration:1200,isFree:false,order:3},
      {title:'Final Project',videoUrl:'',duration:1800,isFree:false,order:4},
    ],
  })));
  console.log('Seeded '+res.length+' courses for: '+inst.name);
  process.exit(0);
}
run().catch(e=>{console.error(e.message);process.exit(1);});
"
```

---

## 🌐 API Reference

All endpoints are prefixed with `/api`. Protected routes require:
```
Authorization: Bearer <jwt_token>
```

### Auth Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/auth/register` | Public | Create account (student or instructor) |
| `POST` | `/api/auth/login` | Public | Login, returns JWT token |
| `GET` | `/api/auth/me` | Required | Get authenticated user profile |
| `PUT` | `/api/auth/profile` | Required | Update name, bio, avatar (multipart) |
| `PUT` | `/api/auth/change-password` | Required | Change account password |

### Course Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/api/courses` | Public | List with `?search=&category=&level=&sort=&page=&limit=` |
| `GET` | `/api/courses/:id` | Optional | Full course detail + enrollment status |
| `POST` | `/api/courses` | Instructor | Create course (multipart/form-data) |
| `PUT` | `/api/courses/:id` | Instructor | Update course fields or thumbnail |
| `DELETE` | `/api/courses/:id` | Instructor | Delete course + all enrollments |
| `GET` | `/api/courses/instructor/my-courses` | Instructor | Own courses list |
| `GET` | `/api/courses/instructor/stats` | Instructor | Stats: revenue, enrollments, ratings |

### Lesson Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/lessons/:courseId` | Instructor | Add lesson (video upload or URL) |
| `PUT` | `/api/lessons/:courseId/:lessonId` | Instructor | Update lesson details or video |
| `DELETE` | `/api/lessons/:courseId/:lessonId` | Instructor | Remove lesson |
| `PUT` | `/api/lessons/:courseId/reorder` | Instructor | Reorder by `{ lessonOrder: [id, id, ...] }` |

### Enrollment Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/enrollment/:courseId` | Student | Enroll in course |
| `GET` | `/api/enrollment/my-courses` | Student | All enrolled courses with progress |
| `GET` | `/api/enrollment/:courseId` | Student | Single enrollment details |
| `POST` | `/api/enrollment/:courseId/lesson/:lessonId/complete` | Student | Mark lesson complete, recalculate % |
| `DELETE` | `/api/enrollment/:courseId` | Student | Unenroll from course |

### Admin Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/api/admin/stats` | Admin | Platform analytics + monthly chart data |
| `GET` | `/api/admin/users` | Admin | Paginated users with `?search=&role=&page=` |
| `DELETE` | `/api/admin/users/:id` | Admin | Delete user + cascade data |
| `PUT` | `/api/admin/users/:id/block` | Admin | Toggle isBlocked |
| `PUT` | `/api/admin/users/:id/role` | Admin | Change role (student/instructor) |
| `GET` | `/api/admin/courses` | Admin | List with `?status=pending|approved|draft` |
| `PUT` | `/api/admin/courses/:id/approve` | Admin | Approve + notify instructor |
| `PUT` | `/api/admin/courses/:id/reject` | Admin | Reject + notify instructor |

### Review Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/api/reviews/:courseId` | Public | Get all reviews for a course |
| `POST` | `/api/reviews/:courseId` | Student (enrolled) | Submit rating + comment |
| `PUT` | `/api/reviews/:reviewId` | Owner | Edit own review |
| `DELETE` | `/api/reviews/:reviewId` | Owner / Admin | Delete review |

---

## 🗄 Database Schema

### User Model
```javascript
{
  name:            String,        // required, max 100
  email:           String,        // required, unique, lowercase
  password:        String,        // required, bcrypt hashed, select: false
  role:            String,        // enum: 'student' | 'instructor' | 'admin'
  avatar:          String,        // Cloudinary URL
  bio:             String,        // max 500 chars
  enrolledCourses: [ObjectId],    // ref: Course
  isBlocked:       Boolean,       // default: false
  notifications:   [{ message: String, read: Boolean, createdAt: Date }],
  createdAt:       Date,
  updatedAt:       Date
}
```

### Course Model (with embedded Lessons)
```javascript
{
  title:            String,       // required, max 200
  description:      String,       // required
  shortDescription: String,       // max 500
  price:            Number,       // 0 = free
  category:         String,       // enum: 11 categories
  level:            String,       // 'Beginner' | 'Intermediate' | 'Advanced'
  language:         String,
  instructor:       ObjectId,     // ref: User
  lessons: [{
    title:     String,
    videoUrl:  String,            // Cloudinary or external
    duration:  Number,            // seconds
    isFree:    Boolean,           // free preview toggle
    order:     Number,
  }],
  thumbnail:        String,       // Cloudinary URL
  isPublished:      Boolean,      // instructor submits → true
  isApproved:       Boolean,      // admin approves → true
  enrollmentCount:  Number,       // auto-incremented
  averageRating:    Number,       // auto-updated by Review post-save hook
  totalRatings:     Number,
  totalDuration:    Number,       // sum of lesson durations
  tags:             [String],
  requirements:     [String],
  whatYouWillLearn: [String],
  createdAt:        Date,
  updatedAt:        Date
}
```

### Enrollment Model
```javascript
{
  user:             ObjectId,     // ref: User  ─┐ unique compound index
  course:           ObjectId,     // ref: Course ─┘
  completedLessons: [ObjectId],   // lesson _ids
  progress:         Number,       // 0–100 (auto-calculated)
  isCompleted:      Boolean,
  completedAt:      Date,
  lastAccessedAt:   Date,
  paymentStatus:    String,       // 'free' | 'paid' | 'pending'
  amountPaid:       Number,
  createdAt:        Date,
  updatedAt:        Date
}
```

### Review Model
```javascript
{
  user:      ObjectId,            // ref: User  ─┐ unique compound index
  course:    ObjectId,            // ref: Course ─┘
  rating:    Number,              // 1–5
  comment:   String,              // max 1000 chars
  createdAt: Date,
  updatedAt: Date
  // post('save') hook auto-updates Course.averageRating + Course.totalRatings
}
```

---

## 📱 Frontend Pages

### Public Routes
| Route | Component | Description |
|-------|-----------|-------------|
| `/` | `HomePage` | Hero section, category grid, featured courses, CTA |
| `/courses` | `CoursesPage` | Searchable, filterable course catalog with pagination |
| `/courses/:id` | `CourseDetailPage` | Full detail, lesson list, reviews, enroll CTA |

### Auth Routes (guests only)
| Route | Component | Description |
|-------|-----------|-------------|
| `/login` | `LoginPage` | Email/password form + demo quick-fill buttons |
| `/register` | `RegisterPage` | Role selector + registration form with password strength |

### Student Routes
| Route | Component | Description |
|-------|-----------|-------------|
| `/dashboard` | `StudentDashboard` | Stats cards + continue-learning grid |
| `/my-courses` | `MyCoursesPage` | Filter by all/in-progress/completed/not-started |
| `/learn/:courseId` | `CoursePlayerPage` | Video player + collapsible lesson sidebar |
| `/profile` | `ProfilePage` | Edit profile, change avatar, change password |

### Instructor Routes
| Route | Component | Description |
|-------|-----------|-------------|
| `/instructor` | `InstructorDashboard` | Stats + course rows with status badges |
| `/instructor/create-course` | `CreateCoursePage` | Multi-section course creation form |
| `/instructor/courses/:id/edit` | `ManageCoursePage` | Edit course + publish/unpublish toggle |
| `/instructor/courses/:id/lessons` | `ManageLessonsPage` | Drag-ordered lesson list + add/edit modal |

### Admin Routes
| Route | Component | Description |
|-------|-----------|-------------|
| `/admin` | `AdminDashboard` | 8 stat cards + Recharts + recent tables |
| `/admin/users` | `UserManagementPage` | Search/filter table with block/role/delete |
| `/admin/courses` | `CourseManagementPage` | Status tabs + approve/reject actions |

---

## 🔐 Authentication & Roles

### Authentication Flow

```
Client                          Server
  │                               │
  ├─ POST /api/auth/login ────────►│
  │  { email, password }          │
  │                               ├─ bcryptjs.compare(password, hash)
  │                               ├─ jwt.sign({ id }, JWT_SECRET, { expiresIn })
  │◄─ { token, user } ────────────┤
  │                               │
  ├─ GET /api/courses (+ Bearer)─►│
  │                               ├─ jwt.verify(token, JWT_SECRET)
  │                               ├─ User.findById(decoded.id)
  │                               ├─ authorize('instructor') → check role
  │◄─ { courses } ────────────────┤
```

### Role-Permission Matrix

| Permission | Student | Instructor | Admin |
|-----------|---------|------------|-------|
| Browse public courses | ✅ | ✅ | ✅ |
| Enroll in courses | ✅ | ❌ | ❌ |
| Track learning progress | ✅ | ❌ | ❌ |
| Write reviews | ✅ (enrolled) | ❌ | ❌ |
| Create / edit courses | ❌ | ✅ (own) | ✅ |
| Upload video lessons | ❌ | ✅ (own) | ✅ |
| Submit for review | ❌ | ✅ | N/A |
| Approve / reject courses | ❌ | ❌ | ✅ |
| Manage all users | ❌ | ❌ | ✅ |
| View platform analytics | ❌ | Own only | ✅ |
| Block / delete users | ❌ | ❌ | ✅ |

### Security Measures

```
✅ bcryptjs password hashing — 12 salt rounds
✅ password field has select:false — never returned in API responses
✅ JWT tokens expire after 7 days (configurable)
✅ Admin role cannot be assigned via /api/auth/register
✅ Blocked users receive HTTP 403 on every protected request
✅ CORS restricted to CLIENT_URL environment variable
✅ express-validator on all auth input fields
✅ No plaintext credentials stored anywhere
```

---

## 🚀 Deployment

### Frontend → Vercel

```bash
# Push frontend/ to GitHub, then on vercel.com:
# 1. Import project → set Root Directory: frontend/
# 2. Add environment variable:
VITE_API_URL=https://your-backend.onrender.com/api
# 3. Deploy — Vercel auto-detects Vite, zero config needed
```

### Backend → Render

```
Service Type:   Web Service
Root Directory: backend/
Build Command:  npm install
Start Command:  node server.js
```

Add all `backend/.env` variables in the Render **Environment** tab.

### Database → MongoDB Atlas (Free)

```
1. cloud.mongodb.com → Create free M0 cluster
2. Database Access → Add user (username + password)
3. Network Access → Add 0.0.0.0/0 (allow all IPs)
4. Connect → Drivers → Copy the URI
5. Replace <password> in URI → set as MONGO_URI on Render
```

### Media → Cloudinary (Free)

```
1. cloudinary.com → Register (25 GB free tier)
2. Dashboard → Copy Cloud Name, API Key, API Secret
3. Set as CLOUDINARY_CLOUD_NAME, CLOUDINARY_API_KEY, CLOUDINARY_API_SECRET on Render
```

### Deployment Architecture

```
Browser (React SPA)
     │
     ▼
Vercel CDN
  frontend/dist/
     │  HTTPS
     ▼
Render Web Service          MongoDB Atlas
  backend/server.js  ─────► lms_db cluster
     │
     ▼
Cloudinary CDN
  Images + Videos
```

---

## 📄 Documentation

| Document | Description |
|----------|-------------|
| 📖 **User Manual** | Complete guide for all three user roles with step-by-step instructions |
| 📋 **Technical Docs** | Full API reference, DB schema, architecture diagrams |
| 🎤 **Presentation** | 14-slide project overview (Problem → Architecture → Features → Deployment) |

---

## 🗺️ Roadmap

- [ ] **Razorpay / Stripe** payment integration for paid courses
- [ ] **Quizzes & Assignments** per lesson with auto-grading
- [ ] **PDF Certificates** generated on course completion
- [ ] **Discussion Forum** per course for Q&A
- [ ] **AI learning paths** — personalized course recommendations
- [ ] **Email Verification** + password reset via OTP (Nodemailer)
- [ ] **React Native** mobile app sharing the same API
- [ ] **2FA** for admin accounts
- [ ] **Coupon codes** and limited-time discounts
- [ ] **Advanced Search** with MongoDB Atlas Search or Elasticsearch

---

## 🐛 Known Issues

| Issue | Workaround |
|-------|-----------|
| Video upload requires valid Cloudinary credentials | Use **Video URL** field instead during local development |
| Course approval resets when title/description is edited | Re-submit for review after editing approved courses |
| CORS errors when deploying | Ensure `CLIENT_URL` matches exact frontend origin including protocol and port |

---


## 📝 License

This project is licensed under the **MIT License**.

---

<div align="center">

**Built with ❤️ using React · Node.js · MongoDB · Tailwind CSS**

If this project helped you, please consider giving it a ⭐

</div>
