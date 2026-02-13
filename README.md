# 🏛️ CivicLink — AI-Powered Smart Civic Issue Reporting Platform

> Scalable smart-city civic engagement platform aligned with **SDG 11** (Sustainable Cities & Communities), designed to improve transparency, response time, and citizen participation in urban governance.

![Tech Stack](https://img.shields.io/badge/React-Vite-blue) ![Backend](https://img.shields.io/badge/Node.js-Express-green) ![AI](https://img.shields.io/badge/AI-Classification-purple) ![Docker](https://img.shields.io/badge/Docker-Ready-blue)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 📸 **AI Image Classification** | Upload issue photos → AI auto-classifies (pothole, garbage, streetlight, water leakage, drainage) with confidence scores |
| 📍 **Smart Geolocation** | Auto-capture GPS + reverse geocode to address via OpenStreetMap Nominatim |
| 📊 **Real-Time Dashboard** | Pie charts, line graphs, status breakdown, user statistics |
| 🗺️ **Interactive Map** | Leaflet + CARTO dark tiles with color-coded status markers |
| 🔐 **Role-Based Access** | Citizens, Admins, Field Officers — JWT authentication |
| 🐳 **Docker Ready** | One-command deployment with PostgreSQL |

## 👤 User Roles

- **Citizen** — Report issues (photo + GPS), track complaint status, view history
- **Admin** — Dashboard analytics, manage all issues, assign field officers, map view
- **Field Officer** — View assigned issues, update status, upload resolution proof

---

## 🚀 Quick Start (Local Development)

### Prerequisites
- **Node.js** 18+ and **npm**

### 1. Clone & Setup

```bash
git clone <repo-url>
cd civiclink
```

### 2. Start Backend

```bash
cd server
npm install
npm run seed    # Seeds database with sample data
npm run dev     # Starts on http://localhost:5000
```

### 3. Start Frontend

```bash
cd client
npm install
npm run dev     # Starts on http://localhost:5173
```

### 4. Open `http://localhost:5173`

### Demo Credentials (all passwords: `password123`)

| Role | Email |
|------|-------|
| Admin | admin@civiclink.com |
| Officer | rajesh@civiclink.com |
| Officer | priya@civiclink.com |
| Citizen | arun@example.com |
| Citizen | meera@example.com |

---

## 🐳 Docker Deployment

```bash
docker-compose up --build
```

- Frontend: `http://localhost:3000`
- Backend API: `http://localhost:5000`
- PostgreSQL: `localhost:5432`

---

## 📂 Project Structure

```
civiclink/
├── server/                     # Backend (Node.js + Express)
│   ├── src/
│   │   ├── config/database.js  # Sequelize connection
│   │   ├── controllers/        # Auth, Issues, Classify
│   │   ├── middleware/          # Auth, RoleGuard, Upload, ErrorHandler
│   │   ├── models/             # User, Issue (Sequelize)
│   │   ├── routes/             # API route definitions
│   │   ├── services/           # AI classifier service
│   │   ├── index.js            # Express entry point
│   │   └── seedData.js         # Database seeder
│   ├── Dockerfile
│   └── package.json
├── client/                     # Frontend (React + Vite + TailwindCSS)
│   ├── src/
│   │   ├── components/         # Navbar
│   │   ├── context/            # AuthContext
│   │   ├── pages/
│   │   │   ├── admin/          # Dashboard, ManageIssues, Map
│   │   │   ├── citizen/        # ReportIssue, MyIssues
│   │   │   └── officer/        # AssignedIssues
│   │   ├── services/api.js     # Axios instance
│   │   ├── App.jsx             # Router + Auth
│   │   └── index.css           # Design system
│   ├── Dockerfile
│   └── nginx.conf
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## 🔌 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login |
| GET | `/api/auth/profile` | Get current user profile |

### Issues
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| POST | `/api/issues` | Citizen | Create new issue (multipart) |
| GET | `/api/issues` | Admin/Officer | Get all issues (filtered) |
| GET | `/api/issues/mine` | Citizen | Get my issues |
| GET | `/api/issues/assigned` | Officer | Get assigned issues |
| GET | `/api/issues/:id` | Any | Get single issue |
| PATCH | `/api/issues/:id/status` | Admin/Officer | Update status |
| PATCH | `/api/issues/:id/assign` | Admin | Assign officer |
| GET | `/api/issues/dashboard/stats` | Admin | Dashboard statistics |
| GET | `/api/issues/officers` | Admin | List all officers |

### AI Classification
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/classify` | Classify uploaded image |

---

## 🛠️ Tech Stack

- **Frontend**: React 18, Vite, TailwindCSS 4, React Router, Chart.js, Leaflet, Lucide Icons
- **Backend**: Node.js, Express, Sequelize ORM, JWT, bcrypt, Multer
- **Database**: SQLite (local dev) / PostgreSQL (Docker/production)
- **AI**: Simulated classification service (production-ready architecture for real model integration)
- **Maps**: Leaflet + OpenStreetMap + CARTO dark tiles
- **Deployment**: Docker, docker-compose, nginx

---

## 🌍 SDG Alignment

CivicLink is designed to support **UN Sustainable Development Goal 11**: Make cities and human settlements inclusive, safe, resilient, and sustainable.

---

## 📜 License

MIT License © 2026 CivicLink
