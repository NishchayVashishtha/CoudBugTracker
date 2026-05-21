# 🧪 CloudBug Testing Guide

Complete step-by-step guide to test all features of CloudBug Bug Tracking System.

**Live Demo:** [https://bug-tracker-app-ndtk.onrender.com](https://bug-tracker-app-ndtk.onrender.com)

---

## 📋 Table of Contents
1. [Initial Setup & Admin Login](#1-initial-setup--admin-login)
2. [User Management Testing](#2-user-management-testing)
3. [Project Creation Testing](#3-project-creation-testing)
4. [Ticket/Bug Submission Testing](#4-ticketbug-submission-testing)
5. [Ticket Assignment & Updates](#5-ticket-assignment--updates)
6. [Role-Based Access Testing](#6-role-based-access-testing)
7. [Dashboard & Analytics Testing](#7-dashboard--analytics-testing)
8. [System Logs Testing](#8-system-logs-testing)
9. [Security Testing](#9-security-testing)
10. [Performance Testing](#10-performance-testing)

---

## 1. Initial Setup & Admin Login

### Test 1.1: First Time Access
**Steps:**
1. Open browser and go to: `https://bug-tracker-app-ndtk.onrender.com`
2. Wait for page to load (first request may take 30 seconds if app was sleeping)
3. You should see the login page

**Expected Result:**
- ✅ Login page loads successfully
- ✅ No errors in browser console
- ✅ Form has email and password fields

### Test 1.2: Admin Login
**Steps:**
1. Enter credentials:
   - **Email:** `admin@app.com`
   - **Password:** `password`
2. Click "Login" button

**Expected Result:**
- ✅ Redirects to dashboard
- ✅ Shows "Login successful!" message
- ✅ Dashboard displays admin features

### Test 1.3: Change Admin Password (CRITICAL!)
**Steps:**
1. Go to "User Management" from navigation
2. Find "Admin" user in the list
3. Click "Edit" or update button
4. Change password to something secure
5. Save changes
6. Logout and login with new password

**Expected Result:**
- ✅ Password updated successfully
- ✅ Can login with new password
- ✅ Cannot login with old password

---

## 2. User Management Testing

### Test 2.1: Register New Users
**Steps:**
1. Logout from admin account
2. Click "Register" link
3. Fill registration form:
   - **Username:** `testuser1`
   - **Email:** `testuser1@test.com`
   - **Password:** `Test@123`
4. Click "Register"

**Expected Result:**
- ✅ Shows "Account created! Please wait for admin approval" message
- ✅ Redirects to login page
- ✅ Cannot login yet (status is "Pending")

### Test 2.2: Create Multiple Test Users
Repeat Test 2.1 with these users:

| Username | Email | Role (to be assigned) |
|----------|-------|----------------------|
| `manager1` | `manager1@test.com` | Project Manager |
| `dev1` | `dev1@test.com` | Developer |
| `dev2` | `dev2@test.com` | Developer |
| `submitter1` | `submitter1@test.com` | Submitter |

### Test 2.3: Approve Users (Admin)
**Steps:**
1. Login as Admin
2. Go to "User Management"
3. Find `testuser1` with status "Pending"
4. Change role to "Developer"
5. Change status to "Approved"
6. Click "Update User"
7. Repeat for all test users with appropriate roles

**Expected Result:**
- ✅ User status changes to "Approved"
- ✅ Success message appears
- ✅ Users can now login

### Test 2.4: Test User Login
**Steps:**
1. Logout from admin
2. Login as `dev1@test.com` with password `Test@123`

**Expected Result:**
- ✅ Login successful
- ✅ Dashboard shows developer view
- ✅ Limited features compared to admin

### Test 2.5: Delete User (Admin)
**Steps:**
1. Login as Admin
2. Go to "User Management"
3. Find a test user
4. Click "Delete" button
5. Confirm deletion

**Expected Result:**
- ✅ User deleted successfully
- ✅ User removed from list
- ✅ Cannot login with deleted user credentials

---

## 3. Project Creation Testing

### Test 3.1: Create First Project (Admin)
**Steps:**
1. Login as Admin
2. On dashboard, find "Create New Project" section
3. Fill form:
   - **Project Name:** `E-Commerce Website`
   - **Description:** `Bug tracking for our e-commerce platform`
   - **Team Members:** Select `manager1`, `dev1`, `dev2`, `submitter1`
4. Click "Create Project"

**Expected Result:**
- ✅ Success message: "New project created successfully!"
- ✅ Project appears on dashboard
- ✅ Selected team members are assigned

### Test 3.2: Create Multiple Projects
Create these additional projects:

| Project Name | Description | Team Members |
|--------------|-------------|--------------|
| `Mobile App` | iOS and Android app bugs | manager1, dev1, submitter1 |
| `API Backend` | REST API bug tracking | manager1, dev2 |
| `Admin Dashboard` | Internal admin panel issues | dev1, dev2 |

### Test 3.3: View Project Details
**Steps:**
1. Click on "E-Commerce Website" project
2. Verify project details page loads

**Expected Result:**
- ✅ Project name and description displayed
- ✅ Team members list shown
- ✅ "Submit New Ticket" form visible
- ✅ Empty ticket list (no tickets yet)

---

## 4. Ticket/Bug Submission Testing

### Test 4.1: Submit Ticket as Submitter
**Steps:**
1. Logout and login as `submitter1@test.com`
2. Click on "E-Commerce Website" project
3. Fill "Submit New Ticket" form:
   - **Title:** `Login button not working on mobile`
   - **Description:** `When clicking login button on mobile devices, nothing happens. Console shows JavaScript error.`
4. Click "Submit"

**Expected Result:**
- ✅ Success message: "New ticket submitted!"
- ✅ Ticket appears in project ticket list
- ✅ Ticket status is "New"
- ✅ Submitter name shown as creator

### Test 4.2: Submit Multiple Tickets
Create these additional tickets in different projects:

**E-Commerce Website:**
- `Payment gateway timeout error`
- `Product images not loading`
- `Cart total calculation incorrect`

**Mobile App:**
- `App crashes on iOS 17`
- `Push notifications not working`

**API Backend:**
- `GET /users endpoint returns 500 error`
- `Authentication token expires too quickly`

### Test 4.3: View Ticket Details
**Steps:**
1. Click on any ticket from the list
2. Verify ticket detail page loads

**Expected Result:**
- ✅ Ticket title and description displayed
- ✅ Status, creator, and creation date shown
- ✅ Comment section visible
- ✅ Update form visible (if user has permission)

---

## 5. Ticket Assignment & Updates

### Test 5.1: Assign Developers to Ticket (Project Manager)
**Steps:**
1. Logout and login as `manager1@test.com`
2. Go to "E-Commerce Website" project
3. Click on "Login button not working on mobile" ticket
4. In "Update Ticket" section:
   - **Assigned Developers:** Select `dev1` and `dev2`
   - **Status:** Change to "In Progress"
5. Click "Update Ticket"

**Expected Result:**
- ✅ Success message: "Ticket updated successfully"
- ✅ Developers assigned to ticket
- ✅ Status changed to "In Progress"
- ✅ Change logged in ticket history

### Test 5.2: Add Comment to Ticket
**Steps:**
1. On same ticket detail page
2. Scroll to "Add Comment" section
3. Enter comment: `I've assigned this to our mobile team. They'll investigate the JavaScript error.`
4. Click "Add Comment"

**Expected Result:**
- ✅ Comment added successfully
- ✅ Comment appears in comments list
- ✅ Commenter name and timestamp shown
- ✅ History entry created

### Test 5.3: Update Ticket as Developer
**Steps:**
1. Logout and login as `dev1@test.com`
2. Go to "My Assigned Tickets" from navigation
3. Click on assigned ticket
4. Add comment: `Found the issue - missing event listener. Working on fix.`
5. Change status to "Resolved"
6. Click "Update Ticket"

**Expected Result:**
- ✅ Status updated to "Resolved"
- ✅ Comment added
- ✅ Changes reflected immediately
- ✅ History updated

### Test 5.4: Close Ticket (Project Manager)
**Steps:**
1. Login as `manager1@test.com`
2. Open the resolved ticket
3. Verify fix is complete
4. Change status to "Closed"
5. Add comment: `Verified fix in production. Closing ticket.`
6. Update ticket

**Expected Result:**
- ✅ Ticket status is "Closed"
- ✅ Final comment added
- ✅ Complete history visible

---

## 6. Role-Based Access Testing

### Test 6.1: Admin Access
**Steps:**
1. Login as Admin
2. Check available features

**Expected Result:**
- ✅ Can see all projects
- ✅ Can create projects
- ✅ Can access User Management
- ✅ Can access System Logs
- ✅ Can view all tickets
- ✅ Can update any ticket

### Test 6.2: Project Manager Access
**Steps:**
1. Login as `manager1@test.com`
2. Check available features

**Expected Result:**
- ✅ Can see only assigned projects
- ✅ Cannot create projects
- ✅ Cannot access User Management
- ✅ Cannot access System Logs
- ✅ Can view tickets in their projects
- ✅ Can assign developers
- ✅ Can update ticket status

### Test 6.3: Developer Access
**Steps:**
1. Login as `dev1@test.com`
2. Check available features

**Expected Result:**
- ✅ Can see assigned projects
- ✅ Can view "My Assigned Tickets"
- ✅ Cannot create projects
- ✅ Cannot access User Management
- ✅ Cannot access System Logs
- ✅ Can update assigned tickets
- ✅ Can add comments

### Test 6.4: Submitter Access
**Steps:**
1. Login as `submitter1@test.com`
2. Check available features

**Expected Result:**
- ✅ Can see assigned projects
- ✅ Can submit new tickets
- ✅ Can view "Tickets I Submitted"
- ✅ Cannot create projects
- ✅ Cannot access User Management
- ✅ Cannot assign developers
- ✅ Can add comments to own tickets

### Test 6.5: Unauthorized Access Test
**Steps:**
1. Login as `submitter1@test.com`
2. Try to access: `https://bug-tracker-app-ndtk.onrender.com/user_management`

**Expected Result:**
- ✅ Access denied
- ✅ Error message: "You do not have permission to access this page"
- ✅ Redirected to dashboard

---

## 7. Dashboard & Analytics Testing

### Test 7.1: View Dashboard Statistics (Admin)
**Steps:**
1. Login as Admin
2. View dashboard

**Expected Result:**
- ✅ Pie chart showing bugs by status (New, In Progress, Resolved, Closed)
- ✅ Bar chart showing bugs by project
- ✅ All projects listed
- ✅ Statistics are accurate

### Test 7.2: Dashboard for Different Roles
**Steps:**
1. Login as each role (Manager, Developer, Submitter)
2. Compare dashboard views

**Expected Result:**
- ✅ Each role sees only relevant data
- ✅ Charts show only their accessible tickets
- ✅ Project list filtered by assignment

### Test 7.3: Real-time Updates
**Steps:**
1. Open dashboard in one browser
2. In another browser, create a new ticket
3. Refresh first browser

**Expected Result:**
- ✅ New ticket appears in list
- ✅ Charts update with new data
- ✅ Counts are accurate

---

## 8. System Logs Testing

### Test 8.1: View System Logs (Admin)
**Steps:**
1. Login as Admin
2. Click "System Logs" in navigation
3. Review log entries

**Expected Result:**
- ✅ All ticket changes logged
- ✅ Shows: field changed, old value, new value
- ✅ Shows user who made change
- ✅ Shows timestamp
- ✅ Logs sorted by most recent first

### Test 8.2: Verify Audit Trail
**Steps:**
1. Create a ticket
2. Assign developers
3. Change status multiple times
4. Add comments
5. Check system logs

**Expected Result:**
- ✅ Every change is logged
- ✅ Complete audit trail visible
- ✅ No missing entries
- ✅ Accurate timestamps

---

## 9. Security Testing

### Test 9.1: Password Security
**Steps:**
1. Try to register with weak password: `123`
2. Try to login with wrong password
3. Verify passwords are hashed in database

**Expected Result:**
- ✅ Weak passwords accepted (consider adding validation)
- ✅ Wrong password shows error
- ✅ Passwords stored as hashes (not plain text)

### Test 9.2: Session Management
**Steps:**
1. Login to application
2. Close browser
3. Reopen and try to access dashboard

**Expected Result:**
- ✅ Session persists (or requires re-login based on config)
- ✅ Logout works properly
- ✅ Cannot access protected pages without login

### Test 9.3: SQL Injection Test
**Steps:**
1. In login form, try: `admin@app.com' OR '1'='1`
2. In ticket title, try: `'; DROP TABLE users; --`

**Expected Result:**
- ✅ Login fails (SQLAlchemy prevents injection)
- ✅ Ticket created with literal text (no SQL execution)
- ✅ No database damage

### Test 9.4: XSS (Cross-Site Scripting) Test
**Steps:**
1. Create ticket with title: `<script>alert('XSS')</script>`
2. Add comment: `<img src=x onerror=alert('XSS')>`

**Expected Result:**
- ✅ Scripts are escaped/sanitized
- ✅ No alert popup appears
- ✅ Text displayed as-is (Jinja2 auto-escapes)

---

## 10. Performance Testing

### Test 10.1: Page Load Speed
**Steps:**
1. Open browser DevTools (F12)
2. Go to Network tab
3. Load dashboard
4. Check load time

**Expected Result:**
- ✅ Initial load: < 3 seconds
- ✅ Subsequent loads: < 1 second
- ✅ No failed requests

### Test 10.2: Multiple Users Simulation
**Steps:**
1. Open 5 different browser tabs
2. Login as different users in each
3. Perform actions simultaneously

**Expected Result:**
- ✅ All users can work independently
- ✅ No conflicts or errors
- ✅ Data remains consistent

### Test 10.3: Large Data Test
**Steps:**
1. Create 50+ tickets across projects
2. Add multiple comments to each
3. Check dashboard performance

**Expected Result:**
- ✅ Dashboard loads without lag
- ✅ Charts render correctly
- ✅ Pagination works (if implemented)

---

## 📊 Test Results Checklist

Use this checklist to track your testing progress:

### Authentication & Users
- [ ] Admin login works
- [ ] User registration works
- [ ] User approval works
- [ ] Role assignment works
- [ ] User deletion works
- [ ] Logout works

### Projects
- [ ] Project creation works
- [ ] Project listing works
- [ ] Project details page works
- [ ] Team assignment works

### Tickets
- [ ] Ticket creation works
- [ ] Ticket listing works
- [ ] Ticket details page works
- [ ] Ticket assignment works
- [ ] Status updates work
- [ ] Comments work
- [ ] Ticket history works

### Role-Based Access
- [ ] Admin has full access
- [ ] Project Manager has correct access
- [ ] Developer has correct access
- [ ] Submitter has correct access
- [ ] Unauthorized access blocked

### Dashboard & Analytics
- [ ] Pie chart displays correctly
- [ ] Bar chart displays correctly
- [ ] Statistics are accurate
- [ ] Role-based filtering works

### System Logs
- [ ] All changes logged
- [ ] Audit trail complete
- [ ] Timestamps accurate

### Security
- [ ] Passwords hashed
- [ ] SQL injection prevented
- [ ] XSS prevented
- [ ] Sessions secure

### Performance
- [ ] Pages load quickly
- [ ] Multiple users supported
- [ ] Large data handled well

---

## 🐛 Bug Reporting

If you find any issues during testing:

1. **Document the bug:**
   - What you did (steps to reproduce)
   - What you expected
   - What actually happened
   - Screenshots (if applicable)

2. **Create a ticket in the app** (dogfooding!)

3. **Or report on GitHub:**
   - Go to repository issues
   - Click "New Issue"
   - Provide detailed information

---

## 🎯 Testing Tips

1. **Test in different browsers:**
   - Chrome
   - Firefox
   - Safari
   - Edge

2. **Test on different devices:**
   - Desktop
   - Tablet
   - Mobile

3. **Test edge cases:**
   - Empty forms
   - Very long text
   - Special characters
   - Concurrent actions

4. **Test error scenarios:**
   - Network disconnection
   - Invalid data
   - Unauthorized access

---

## ✅ Final Verification

Before considering testing complete:

- [ ] All core features tested
- [ ] All user roles tested
- [ ] Security tests passed
- [ ] Performance acceptable
- [ ] No critical bugs found
- [ ] Documentation accurate

---

**Happy Testing! 🚀**

For questions or issues, contact the development team or create a ticket in the system.

**Live App:** [https://bug-tracker-app-ndtk.onrender.com](https://bug-tracker-app-ndtk.onrender.com)
