# 🚀 QUICK START GUIDE

## Student Logbook System - 5 Minute Setup

### Prerequisites
- ✅ Node.js installed
- ✅ PostgreSQL installed and running

---

## STEP 1: Create Database (1 minute)

```bash
# Windows (PostgreSQL Command Prompt)
createdb student_logbook_db

# Or in PostgreSQL CLI
psql -U postgres
CREATE DATABASE student_logbook_db;
\q
```

---

## STEP 2: Setup Backend (2 minutes)

```bash
# Terminal 1
cd d:\Student-Logbook-System\backend

# Install dependencies
npm install

# Edit .env file with your PostgreSQL connection
# DATABASE_URL="postgresql://postgres:password@localhost:5432/student_logbook_db"
# JWT_SECRET="mysecretkey123"
# PORT=5000

# Run migrations
npx prisma migrate dev --name init

# Start backend server
npm run dev
```

**✅ Backend running on** http://localhost:5000

---

## STEP 3: Setup Frontend (1 minute)

```bash
# Terminal 2
cd d:\Student-Logbook-System\frontend

# Install dependencies
npm install

# Start frontend server
npm start
```

**✅ Frontend running on** http://localhost:3000

---

## STEP 4: Test the System

### Login at: http://localhost:3000

Create a test account using the **Register** option:
- Email: test@example.com
- Password: password123
- Role: Select student/admin/supervisor/assessor

---

## 📱 Quick Feature Tour

### **Admin** (administer system)
1. Click "Manage Students" → Add a student
2. Click "Manage Supervisors" → Add supervisor
3. View dashboard stats

### **Student** (create logbook entries)
1. Click "Add Entry" → Fill form with daily activities
2. Click "Upload Evidence" → Upload photos/documents
3. View feedback from supervisor (once approved)

### **Supervisor** (review entries)
1. Click "Pending Reviews" → See student entries
2. Click "Review & Provide Feedback" modal
3. Add comments and approve/reject

### **Assessor** (evaluate students)
1. Click "Monitor Students" → See all students
2. Click "Assess" → Submit score (0-100) and comments
3. View "My Assessments" to see submitted evaluations

---

## 🔧 Useful Commands

```bash
# Stop servers (Ctrl+C in both terminals)

# Reset database (delete all data)
cd backend
npx prisma migrate reset

# View database GUI
npx prisma studio

# Kill port if stuck
# Windows PowerShell:
Get-Process -Name node | Stop-Process -Force
```

---

## 📊 API Testing (Optional)

Use Postman to test API:

```bash
# Register User
POST http://localhost:5000/api/auth/register
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123",
  "role": "student"
}

# Login
POST http://localhost:5000/api/auth/login
{
  "email": "john@example.com",
  "password": "password123"
}

# Get Students (Admin only, needs token)
GET http://localhost:5000/api/students
Headers: Authorization: Bearer <token_from_login>
```

---

## 🎯 Demo Workflow

Here's a complete demo flow:

1. **Admin logs in** → Creates a student account → Assigns supervisor
2. **Student logs in** → Creates logbook entry → Uploads evidence file
3. **Supervisor logs in** → Reviews entry → Provides feedback
4. **Assessor logs in** → Evaluates student → Submits score
5. **Student logs in again** → Views supervisor feedback + assessment score

---

## ❌ Troubleshooting

| Problem | Solution |
|---------|----------|
| **Database connection error** | Check DATABASE_URL in .env, ensure PostgreSQL is running |
| **Port 3000/5000 already in use** | Kill process: `Get-Process -Name node \| Stop-Process -Force` |
| **npm install fails** | Delete node_modules, try `npm cache clean --force`, then `npm install` |
| **Prisma error** | Run `npx prisma generate` then `npx prisma migrate dev --name init` |
| **File upload not working** | Ensure `backend/uploads` folder exists |

---

## 📁 File Locations

- **Backend code**: `d:\Student-Logbook-System\backend\`
- **Frontend code**: `d:\Student-Logbook-System\frontend\`
- **Database config**: `backend\.env`
- **API routes**: `backend\routes\`
- **UI components**: `frontend\src\pages\`

---

## ✅ Success Checklist

- ✅ Both servers running (no red errors)
- ✅ Can load http://localhost:3000 in browser
- ✅ Can register new user
- ✅ Can login successfully
- ✅ Dashboard loads according to user role

**If all checkboxes are ✅, you're ready to use the system!**

---

## 🎓 Next Steps

1. Create multiple users with different roles
2. Test each role's capabilities
3. Try uploading files as a student
4. Test supervisor feedback workflow
5. Submit assessments as assessor

---

## 💡 Pro Tips

- Use Ctrl+Shift+K to open browser DevTools to see logs
- Check backend terminal for API errors
- All passwords are case-sensitive
- Emails must be unique across the system
- Files are stored in `backend/uploads` folder

---

## 📞 Need Help?

Check the main README.md for:
- Complete API documentation
- Database schema details
- Deployment instructions
- Architecture overview

---

**Happy Testing! 🎉**