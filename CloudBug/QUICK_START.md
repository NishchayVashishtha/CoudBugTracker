# 🚀 CloudBug - Quick Start Guide

## Live Demo
**URL:** [https://bug-tracker-app-ndtk.onrender.com](https://bug-tracker-app-ndtk.onrender.com)

---

## ⚡ 5-Minute Testing Guide

### Step 1: Login as Admin (1 min)
1. Go to: https://bug-tracker-app-ndtk.onrender.com
2. Login with:
   - **Email:** `admin@app.com`
   - **Password:** `password`
3. ✅ You're now on the admin dashboard!

### Step 2: Create a Project (1 min)
1. On dashboard, find "Create New Project" section
2. Fill in:
   - **Name:** `Test Project`
   - **Description:** `My first test project`
3. Click "Create Project"
4. ✅ Project created!

### Step 3: Register a New User (1 min)
1. Click "Logout"
2. Click "Register"
3. Fill form:
   - **Username:** `testdev`
   - **Email:** `testdev@test.com`
   - **Password:** `Test@123`
4. Click "Register"
5. ✅ User registered (pending approval)

### Step 4: Approve User (1 min)
1. Login back as Admin
2. Go to "User Management"
3. Find `testdev` user
4. Change:
   - **Role:** Developer
   - **Status:** Approved
5. Click "Update User"
6. ✅ User approved!

### Step 5: Create a Bug Ticket (1 min)
1. Click on "Test Project"
2. Fill "Submit New Ticket":
   - **Title:** `Login button not working`
   - **Description:** `Button doesn't respond on click`
3. Click "Submit"
4. ✅ Ticket created!

---

## 🎯 What to Test Next?

### Basic Features (10 mins)
- [ ] Create 2-3 more projects
- [ ] Register 3-4 users with different roles
- [ ] Submit 5-10 tickets
- [ ] Assign developers to tickets
- [ ] Update ticket status
- [ ] Add comments to tickets

### Advanced Features (20 mins)
- [ ] Test all 4 user roles (Admin, Manager, Developer, Submitter)
- [ ] Check dashboard analytics (pie chart, bar chart)
- [ ] View system logs
- [ ] Test role-based access control
- [ ] Try unauthorized access

### Full Testing (1 hour)
- [ ] Follow complete [TESTING_GUIDE.md](TESTING_GUIDE.md)
- [ ] Test all features systematically
- [ ] Document any bugs found
- [ ] Test on different browsers/devices

---

## 👥 Test User Accounts

Create these test accounts for comprehensive testing:

| Username | Email | Role | Purpose |
|----------|-------|------|---------|
| `manager1` | `manager1@test.com` | Project Manager | Manage projects |
| `dev1` | `dev1@test.com` | Developer | Work on tickets |
| `dev2` | `dev2@test.com` | Developer | Work on tickets |
| `submitter1` | `submitter1@test.com` | Submitter | Submit bugs |

**Password for all:** `Test@123`

---

## 🔑 Key Features to Test

### 1. User Management
- Register → Approve → Login → Delete

### 2. Projects
- Create → View → Assign Team → Manage

### 3. Tickets
- Submit → Assign → Update Status → Comment → Close

### 4. Dashboard
- View statistics
- Check pie chart (bugs by status)
- Check bar chart (bugs by project)

### 5. System Logs
- View all changes
- Check audit trail

---

## 🐛 Common Issues & Solutions

### Issue: App is slow to load
**Solution:** Free tier sleeps after 15 mins. First request takes ~30 seconds. Just wait and refresh.

### Issue: Can't login
**Solution:** 
- Check email/password spelling
- Ensure user status is "Approved" (not "Pending")
- Try default admin credentials

### Issue: Can't see projects
**Solution:** 
- Ensure you're assigned to the project
- Only Admin can see all projects
- Other roles see only assigned projects

### Issue: Can't create project
**Solution:** 
- Only Admin can create projects
- Login as admin@app.com

---

## 📚 Documentation

- **Full README:** [README.md](README.md)
- **Complete Testing Guide:** [TESTING_GUIDE.md](TESTING_GUIDE.md)
- **Live Demo:** [https://bug-tracker-app-ndtk.onrender.com](https://bug-tracker-app-ndtk.onrender.com)

---

## 🎉 Ready to Test!

1. Open: https://bug-tracker-app-ndtk.onrender.com
2. Login: `admin@app.com` / `password`
3. Start testing!

**Happy Testing! 🚀**
