# 🔐 AccountHub — Flask Authentication System

AccountHub is a secure authentication system built with **Flask and PostgreSQL**.  
It supports traditional session-based web authentication as well as **JWT-based REST API authentication**, with secure password hashing and protected routes.

---

## 🚀 Features

- **User Registration**
  - Username, email, password and confirmation validation
  - Duplicate username and email prevention

- **Secure Password Storage**
  - Passwords are hashed using Bcrypt
  - Plain-text passwords are never stored in the database

- **Session-Based Authentication**
  - Login and logout using Flask-Login
  - Protected dashboard accessible only to authenticated users

- **JWT Authentication**
  - JWT access tokens generated after successful API login
  - Protected REST API endpoints using Bearer tokens

- **PostgreSQL Integration**
  - User account data stored in PostgreSQL
  - Database interaction handled using SQLAlchemy ORM

- **Environment-Based Configuration**
  - Database credentials and secret keys stored outside the source code using environment variables

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Backend programming language |
| Flask | Web framework |
| PostgreSQL | Relational database |
| SQLAlchemy | ORM and database interaction |
| Flask-Login | Session-based authentication |
| Flask-Bcrypt | Password hashing |
| Flask-JWT-Extended | JWT authentication |
| Flask-WTF | Form handling and validation |
| HTML / CSS | Web interface |
| Postman | REST API testing |
| Git / GitHub | Version control |

---

## 🔐 Authentication Overview

AccountHub implements **two authentication approaches**.

### 🌐 Web Authentication

The browser-based interface uses **Flask-Login** for session authentication.

```text
User enters credentials
        ↓
Account retrieved from PostgreSQL
        ↓
Bcrypt verifies password
        ↓
Flask-Login creates authenticated session
        ↓
User gains access to protected dashboard
```

The `/dashboard` route is protected using `@login_required`.

### 🔑 JWT API Authentication

The REST API uses **JSON Web Tokens (JWT)** for stateless authentication.

```text
Client sends email + password
        ↓
Credentials are verified
        ↓
Server generates JWT access token
        ↓
Client sends token with protected requests
        ↓
Server validates token
        ↓
Protected resource is returned
```

The `/api/profile` endpoint is protected using `@jwt_required()`.

---

## 🌐 API Endpoints

| Method | Endpoint | Description | Authentication |
|---|---|---|---|
| POST | `/api/register` | Register a new user | No |
| POST | `/api/login` | Login and receive JWT | No |
| GET | `/api/profile` | Retrieve current user's profile | JWT Required |

### Example API Login

**Request**

```json
{
    "email": "user@example.com",
    "password": "your-password"
}
```

**Response**

```json
{
    "access_token": "<JWT_ACCESS_TOKEN>"
}
```

The token can then be sent to protected endpoints using:

```text
Authorization: Bearer <JWT_ACCESS_TOKEN>
```

---

## 🛡️ Security Features

- Passwords hashed using **Bcrypt**
- No plain-text password storage
- Protected web routes using `@login_required`
- Protected API routes using `@jwt_required()`
- Duplicate username and email detection
- JWT signing key stored as an environment variable
- PostgreSQL credentials stored outside source code
- `.env` excluded from Git version control

---

## 📊 Database Model

### User

| Field | Type | Constraint |
|---|---|---|
| id | Integer | Primary Key |
| username | String(20) | Unique, Not Null |
| email | String(120) | Unique, Not Null |
| password | String(255) | Not Null |

Passwords stored in the `password` column contain **Bcrypt hashes**, not the original passwords.

---

## 📁 Project Structure

```text
📦 AccountHub
│
├── static/
│   └── style.css
│
├── templates/
│   ├── base.html
│   ├── dashboard.html
│   ├── home.html
│   ├── login.html
│   └── register.html
│
├── app.py
├── forms.py
├── requirements.txt
├── .gitignore
└── README.md
```

> `.env` is intentionally excluded from the repository because it contains sensitive configuration values.

---

## ⚙️ Running Locally

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd accounthub
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the environment

On Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure environment variables

Create a `.env` file containing:

```env
SECRET_KEY=your-secret-key
JWT_SECRET_KEY=your-jwt-secret-key
DATABASE_URL=your-postgresql-database-url
```

### 6. Run AccountHub

```bash
python app.py
```

Then visit:

```text
http://127.0.0.1:5000
```

---

## 🧪 API Testing

The API endpoints were tested using **Postman**.

Test scenarios include:

- Successful user registration
- Duplicate account rejection
- Successful and unsuccessful login
- JWT generation after valid login
- Accessing `/api/profile` without a JWT
- Accessing `/api/profile` with a valid Bearer token

---

## 💡 What I Learned

Building AccountHub provided hands-on experience with:

- Flask backend development
- PostgreSQL integration
- SQLAlchemy ORM
- Secure password hashing
- Session-based authentication
- JWT-based authentication
- REST API design
- HTTP status codes
- API testing with Postman
- Environment variable management
- Git and GitHub version control

---

## 👤 Author

**Zahra Aliabbas**
