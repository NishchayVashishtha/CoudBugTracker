# CloudBug - Bug Tracking System

A comprehensive bug tracking and project management web application built with Flask, designed to help teams manage software development issues efficiently.

![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-3.0.3-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## 🌐 Live Demo

**Try it now:** [https://bug-tracker-app-ndtk.onrender.com](https://bug-tracker-app-ndtk.onrender.com)

**Default Login Credentials:**
- Email: `admin@app.com`
- Password: `password`

⚠️ **Note:** Please change the password after first login!

## 📋 Table of Contents

- [Live Demo](#-live-demo)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [User Roles](#user-roles)
- [Deployment](#deployment)
- [Testing](#testing)
- [API Endpoints](#api-endpoints)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### Core Functionality
- **User Authentication & Authorization**
  - Secure registration and login system
  - Password hashing with bcrypt
  - Role-based access control (Admin, Project Manager, Developer, Submitter)
  - Account approval workflow

- **Project Management**
  - Create and manage multiple projects
  - Assign team members to projects
  - Project-specific ticket tracking
  - Team collaboration features

- **Ticket/Bug Tracking**
  - Create, view, and update bug tickets
  - Assign developers to tickets
  - Track ticket status (New, In Progress, Resolved, Closed)
  - Add comments to tickets
  - Complete ticket history tracking

- **Dashboard & Analytics**
  - Visual statistics with pie charts (bugs by status)
  - Bar charts showing bugs by project
  - Role-based dashboard views
  - Real-time ticket counts

- **System Administration**
  - User management interface
  - Role and status management
  - System-wide activity logs
  - Audit trail for all ticket changes

## 🛠️ Tech Stack

### Backend
- **Flask 3.0.3** - Web framework
- **SQLAlchemy 2.0.44** - ORM for database operations
- **Flask-Login 0.6.3** - User session management
- **Flask-Bcrypt 1.0.1** - Password hashing
- **Gunicorn 23.0.0** - WSGI HTTP server for production

### Database
- **SQLite** - Development database
- **PostgreSQL** - Production database (via psycopg2-binary)

### Frontend
- **Jinja2 3.1.6** - Template engine
- **HTML5/CSS3** - UI structure and styling
- **Chart.js** - Data visualization (assumed from dashboard features)

## 📁 Project Structure

```
CloudBug/
├── app.py                          # Main application file
├── requirements.txt                # Python dependencies
├── render.yaml                     # Render deployment configuration
├── README.md                       # Project documentation
├── instance/
│   └── test.db                     # SQLite database (development)
└── templates/
    ├── index.html                  # Dashboard/home page
    ├── login.html                  # Login page
    ├── register.html               # Registration page
    ├── project_detail.html         # Project details and tickets
    ├── ticket_detail.html          # Individual ticket view
    ├── assigned_tickets.html       # User's assigned tickets
    ├── user_management.html        # Admin user management
    └── system_logs.html            # System activity logs
```

## 🚀 Installation

### Prerequisites
- Python 3.11 or higher
- pip (Python package manager)
- Git

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/cloudbug.git
   cd cloudbug/CloudBug
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate

   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Initialize the database**
   ```bash
   python app.py create
   ```
   This creates the database tables and a default admin user.

5. **Run the application**
   ```bash
   python app.py
   ```

6. **Access the application**
   - Open your browser and navigate to: `http://127.0.0.1:5000`
   - Login with default credentials:
     - **Email:** `admin@app.com`
     - **Password:** `password`
   - ⚠️ **Important:** Change the admin password immediately after first login!

## ⚙️ Configuration

### Environment Variables

The application uses the following environment variables:

| Variable | Description | Default |
|----------|-------------|---------|
| `DATABASE_URL` | Database connection string | `sqlite:///test.db` |
| `SECRET_KEY` | Flask secret key for sessions | `a_very_secret_key_change_this` |

### Setting Environment Variables

**Development (Windows):**
```bash
set SECRET_KEY=your-secret-key-here
set DATABASE_URL=sqlite:///test.db
```

**Development (macOS/Linux):**
```bash
export SECRET_KEY=your-secret-key-here
export DATABASE_URL=sqlite:///test.db
```

**Production:**
Environment variables are automatically configured via `render.yaml` when deploying to Render.

## 📖 Usage

### User Roles

CloudBug implements a role-based access control system with four distinct roles:

#### 1. **Admin**
- Full system access
- Manage all users (approve, edit roles, delete)
- Create and manage all projects
- View all tickets across all projects
- Access system logs and audit trails
- Assign team members to projects

#### 2. **Project Manager**
- Manage assigned projects
- View and update tickets in their projects
- Assign developers to tickets
- Add comments to tickets
- View project-specific statistics

#### 3. **Developer**
- View tickets assigned to them
- Update ticket status
- Add comments to tickets
- View projects they're assigned to
- Track their workload

#### 4. **Submitter**
- Create new bug tickets
- View tickets they've submitted
- Add comments to their tickets
- View project details
- Track ticket progress

### Common Workflows

#### Creating a New Project (Admin)
1. Login as Admin
2. On the dashboard, find the "Create New Project" section
3. Enter project name and description
4. Select team members to assign
5. Click "Create Project"

#### Submitting a Bug Ticket
1. Navigate to the project page
2. Click "Submit New Ticket"
3. Enter ticket title and description
4. Submit the form
5. Ticket is created with "New" status

#### Assigning Developers to a Ticket
1. Open the ticket detail page
2. Select developers from the team dropdown
3. Update ticket status if needed
4. Click "Update Ticket"
5. Changes are logged in ticket history

#### Approving New Users (Admin)
1. Navigate to "User Management"
2. Find users with "Pending" status
3. Select appropriate role
4. Change status to "Approved"
5. Click "Update User"

## 🌐 Deployment

### Deploy to Render (Recommended)

CloudBug is pre-configured for deployment on Render with the included `render.yaml` file.

**Live Example:** [https://bug-tracker-app-ndtk.onrender.com](https://bug-tracker-app-ndtk.onrender.com)

#### Step 1: Prepare Your Repository
```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit changes
git commit -m "Initial commit - CloudBug ready for deployment"

# Create main branch
git branch -M main

# Add remote repository
git remote add origin https://github.com/yourusername/cloudbug.git

# Push to GitHub
git push -u origin main
```

#### Step 2: Deploy on Render
1. Go to [render.com](https://render.com) and sign up/login
2. Click **"New"** → **"Blueprint"**
3. Connect your GitHub account
4. Select your CloudBug repository
5. Render will automatically detect `render.yaml`
6. Review the configuration:
   - **Database:** PostgreSQL (Free tier)
   - **Web Service:** Python app with Gunicorn
   - **Environment Variables:** Auto-configured
7. Click **"Apply"** to start deployment
8. Wait 5-10 minutes for deployment to complete

#### Step 3: Post-Deployment
1. Render will provide a URL (e.g., `https://bug-tracker-app.onrender.com`)
2. Visit the URL and login with default credentials
3. **Immediately change the admin password!**
4. Start creating projects and inviting users

### Render Free Tier Limitations
- ⏱️ Service spins down after 15 minutes of inactivity
- 🔄 Takes ~30 seconds to wake up on first request
- 💾 Database has 90-day expiration (renewable for free)
- 📊 750 hours/month of runtime

### Alternative Deployment Options

#### Heroku
```bash
# Install Heroku CLI and login
heroku login

# Create new app
heroku create your-app-name

# Add PostgreSQL addon
heroku addons:create heroku-postgresql:mini

# Set environment variables
heroku config:set SECRET_KEY=$(python -c 'import secrets; print(secrets.token_hex(32))')

# Deploy
git push heroku main

# Initialize database
heroku run python app.py create
```

#### PythonAnywhere
1. Upload your code to PythonAnywhere
2. Create a new web app with Flask
3. Configure WSGI file to point to `app.py`
4. Set up virtual environment
5. Install requirements
6. Initialize database

## 🧪 Testing

### Complete Testing Guide

A comprehensive testing guide is available in [TESTING_GUIDE.md](TESTING_GUIDE.md) that covers:

- ✅ Initial setup and admin login
- ✅ User management testing
- ✅ Project creation testing
- ✅ Ticket submission and updates
- ✅ Role-based access control testing
- ✅ Dashboard and analytics testing
- ✅ System logs verification
- ✅ Security testing (SQL injection, XSS)
- ✅ Performance testing

### Quick Test Steps

1. **Access the live app:** [https://bug-tracker-app-ndtk.onrender.com](https://bug-tracker-app-ndtk.onrender.com)

2. **Login as Admin:**
   - Email: `admin@app.com`
   - Password: `password`

3. **Test Core Features:**
   - Create a new project
   - Register new users and approve them
   - Submit bug tickets
   - Assign developers to tickets
   - Update ticket status
   - Add comments
   - View dashboard analytics
   - Check system logs

4. **Test Different Roles:**
   - Create users with different roles (Admin, Project Manager, Developer, Submitter)
   - Login as each role and verify access permissions
   - Ensure role-based restrictions work correctly

For detailed testing procedures, see [TESTING_GUIDE.md](TESTING_GUIDE.md)

## 🔌 API Endpoints

### Authentication Routes

| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET/POST | `/login` | User login | Public |
| GET/POST | `/register` | User registration | Public |
| GET | `/logout` | User logout | Authenticated |

### Application Routes

| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/` | Dashboard/Home | Authenticated |
| POST | `/project/create` | Create new project | Admin |
| GET/POST | `/project/<id>` | Project details | Team Members |
| GET/POST | `/ticket/<id>` | Ticket details | Team Members |
| POST | `/ticket/update/<id>` | Update ticket | Team Members |
| GET | `/assigned_tickets` | View assigned tickets | Authenticated |
| GET | `/user_management` | Manage users | Admin |
| POST | `/user/update/<id>` | Update user | Admin |
| POST | `/user/delete/<id>` | Delete user | Admin |
| GET | `/system_logs` | View system logs | Admin |

## 📊 Database Schema

### User Table
- `id` (Primary Key)
- `username` (Unique)
- `email` (Unique)
- `password_hash`
- `role` (Admin/ProjectManager/Developer/Submitter)
- `status` (Pending/Approved/Locked)

### Project Table
- `id` (Primary Key)
- `name`
- `description`
- `created_at`

### Bug/Ticket Table
- `id` (Primary Key)
- `title`
- `description`
- `status` (New/In Progress/Resolved/Closed)
- `created_at`
- `user_id` (Foreign Key → User)
- `project_id` (Foreign Key → Project)

### Comment Table
- `id` (Primary Key)
- `body`
- `created_at`
- `user_id` (Foreign Key → User)
- `bug_id` (Foreign Key → Bug)

### TicketHistory Table
- `id` (Primary Key)
- `field` (Changed field name)
- `old_value`
- `new_value`
- `changed_at`
- `user_id` (Foreign Key → User)
- `bug_id` (Foreign Key → Bug)

### Association Tables
- `project_users` (Many-to-Many: Projects ↔ Users)
- `ticket_developers` (Many-to-Many: Tickets ↔ Developers)

## 🔒 Security Features

- ✅ Password hashing with bcrypt
- ✅ Session management with Flask-Login
- ✅ CSRF protection (Flask built-in)
- ✅ SQL injection prevention (SQLAlchemy ORM)
- ✅ Role-based access control
- ✅ Account approval workflow
- ✅ Secure secret key generation in production

## 🐛 Troubleshooting

### Common Issues

**Issue:** Database not found
```bash
# Solution: Initialize the database
python app.py create
```

**Issue:** Import errors
```bash
# Solution: Reinstall dependencies
pip install -r requirements.txt
```

**Issue:** Port already in use
```bash
# Solution: Change the port in app.py or kill the process
# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# macOS/Linux
lsof -ti:5000 | xargs kill -9
```

**Issue:** Can't login after deployment
- Ensure database was initialized properly
- Check that environment variables are set
- Verify the admin user was created

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow PEP 8 style guide for Python code
- Add comments for complex logic
- Update documentation for new features
- Test thoroughly before submitting PR

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Authors

- **Your Name** - *Initial work* - [YourGitHub](https://github.com/yourusername)

## 🙏 Acknowledgments

- Flask documentation and community
- SQLAlchemy for excellent ORM
- Render for free hosting
- All contributors and testers

## 📧 Contact

For questions or support, please open an issue on GitHub or contact:
- Email: your.email@example.com
- GitHub: [@yourusername](https://github.com/yourusername)

## 🗺️ Roadmap

Future enhancements planned:
- [ ] Email notifications for ticket updates
- [ ] File attachments for tickets
- [ ] Advanced search and filtering
- [ ] Export reports to PDF/CSV
- [ ] REST API for mobile apps
- [ ] Real-time updates with WebSockets
- [ ] Two-factor authentication
- [ ] Dark mode theme
- [ ] Ticket priority levels
- [ ] Sprint/milestone management

---

**Made with ❤️ using Flask**
