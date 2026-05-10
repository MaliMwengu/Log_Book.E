# Student Logbook System

This repository contains a full-stack Student Logbook application with separate backend and frontend projects. The system supports four user roles (admin, student, supervisor, assessor) and provides:

- Role-based dashboards with a unified layout and topbar
- User registration/login with JWT authentication
- CRUD operations for students, supervisors, assessors, logbook entries, feedback and assessments
- Profile management including avatar upload, password change, and light/dark mode toggle
- File uploads via Multer and static serving for profile pictures
- SQLite database managed with Prisma ORM

## Technology Stack

| Layer     | Technology                     |
|-----------|--------------------------------|
| Backend   | Node.js, Express, Prisma       |
| Frontend  | React, React Router, Axios     |
| Database  | SQLite (via Prisma)            |
| Auth      | JWT, bcryptjs                  |
| Uploads   | Multer                         |
| Styling   | CSS (custom, variables)        |

## Getting Started

### Prerequisites

- Node.js 18+ (or compatible)
- npm

### Installation

1. Clone the repository.
2. Install dependencies for both projects:
   ```bash
   cd d:\Student-Logbook-System
   npm install        # installs backend and frontend deps via workspaces
   ```
3. Initialize the database and generate Prisma client:
   ```bash
   npx prisma migrate dev --name init
   npx prisma generate
   ```
4. Start the development servers (backend and frontend run concurrently):
   ```bash
   npm run dev
   ```
5. Open [http://localhost:3000](http://localhost:3000) in your browser.

### Environment

The project uses a `.env` file in the root for configuration. Example contents:
```
DATABASE_URL="file:./dev.db"
JWT_SECRET="your_jwt_secret"
```

## Usage

1. Register a new account (default role `student`) or login as an existing user.
2. After authentication you will be redirected to the dashboard corresponding to your role.
3. Click your avatar in the top-right to open the profile modal where you can:
   - Upload/change your profile picture
   - Update your name, email or password
   - Toggle between light and dark modes
   - Logout from the application
4. Admin users can manage other users through the sidebar navigation.
5. Students, supervisors, and assessors have simplified dashboards tailored to their role.

## Project Structure

```
backend/             # Express API
  routes/            # Route handlers
  controllers/       # Business logic
  middleware/        # Auth, file upload, etc.
  prisma/            # Schema and migrations
frontend/            # React application
  src/
    pages/           # Dashboard and login pages
    components/      # Shared UI components (ProfileModal, etc.)
    services/        # Axios instance
    styles/          # CSS files
```

## Notes

- Mode preference (light/dark) is stored in local storage and applied globally.
- Profile pictures are saved in the `backend/uploads` folder and served at `/uploads`.
- Logout clears localStorage values and redirects to the login page.

## Deployment

This project can be deployed by running the backend and frontend separately on any Node.js hosting provider. Ensure environment variables are set and the SQLite file is accessible.

---

This README has been updated to reflect the current architecture and features of the Student Logbook System. Feel free to extend it further with deployment steps or additional documentation.
