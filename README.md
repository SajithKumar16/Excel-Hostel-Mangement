# Hostel Management System

A complete, production-quality Hostel Management System as a full-stack web application.

## Features

- **Role-based Dashboards:** Separate experiences for Students, Parents, and Wardens.
- **Authentication:** JWT-based authentication with `bcryptjs` password hashing.
- **Student Portal:** View attendance, room details, apply for leaves, and file complaints.
- **AI Complaint Classification:** Automatically suggests Category and Priority based on the complaint description using a rule-based engine.
- **Warden Portal:** Real-time analytics, room allocation, student management, and issue resolution.
- **Responsive Design:** Mobile, tablet, and desktop friendly layout using Tailwind CSS.
- **Emergency SOS:** Integrated quick-alert mechanism for critical situations.

## Technology Stack

**Frontend:**
- React 19
- TypeScript
- Vite
- Tailwind CSS v4
- React Router v7
- Axios
- Lucide React
- Recharts (Analytics)
- React Hook Form + Zod

**Backend:**
- Node.js
- Express.js
- TypeScript
- `better-sqlite3` (SQLite Database)
- JSON Web Tokens (JWT)
- bcryptjs

## Folder Structure

```
hostel-management-system/
│
├── frontend/             # React Vite Application
│   ├── src/
│   │   ├── components/   # Reusable UI (Sidebar, Layout, ProtectedRoute)
│   │   ├── context/      # AuthContext
│   │   ├── pages/        # Login, Dashboards, Complaints
│   │   ├── services/     # Axios API configuration
│   │   └── index.css     # Tailwind v4 configuration
│   └── package.json
│
└── backend/              # Express Node Application
    ├── src/
    │   ├── controllers/  # Route handlers (auth, students, rooms, etc.)
    │   ├── middleware/   # JWT authentication & Role validation
    │   ├── routes/       # Express route definitions
    │   ├── db.ts         # SQLite connection & Schema initialization
    │   └── seed.ts       # Demo data generation
    ├── database/         # SQLite database file location
    └── package.json
```

## Installation & Setup

1. **Clone the repository.**

2. **Backend Setup:**
   ```bash
   cd backend
   npm install
   npm run dev
   ```
   *Note: The backend will automatically create the `hostel.db` file and seed the initial demo data.*

3. **Frontend Setup:**
   ```bash
   cd frontend
   npm install
   npm run dev
   ```

4. Open your browser and navigate to `http://localhost:5173/`.

## Environment Variables

**Backend (`backend/.env`):**
```env
PORT=5000
JWT_SECRET=change_this_secret
DATABASE_PATH=./database/hostel.db
```

**Frontend (`frontend/.env`):**
```env
VITE_API_URL=http://localhost:5000/api
```

## Demo Credentials

You can use the following credentials to test the different role-based views immediately:

| Role | Email | Password |
|---|---|---|
| **Warden** | `warden@hostel.com` | `Warden@123` |
| **Student** | `student@hostel.com` | `Student@123` |
| **Parent** | `parent@hostel.com` | `Parent@123` |

## API Overview

The REST API is strictly protected by JWT and role-based middleware.

- `POST /api/auth/login`
- `GET /api/auth/me`
- `GET/POST/PUT/DELETE /api/students` (Warden)
- `GET/POST/PUT/DELETE /api/rooms` (Warden)
- `POST /api/complaints` (Student)
- `GET /api/analytics/dashboard` (Warden)

## Future Enhancements
- Integration with external LLM APIs (OpenAI/Gemini) for the AI Hostel Assistant.
- Push Notifications using Firebase Cloud Messaging or WebSockets.
- Payment Gateway integration for Hostel Fees.
