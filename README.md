# AccountHub

AccountHub is a Flask-based authentication system that implements secure user registration, login, session management, and JWT-based API authentication. User data is stored in a PostgreSQL database, with passwords securely hashed using Bcrypt.

## Features

- User registration with form validation
- Secure login and logout
- Password hashing using Bcrypt
- PostgreSQL database integration
- Session-based authentication using Flask-Login
- Protected dashboard accessible only to authenticated users
- REST API for user registration and login
- JWT-based stateless authentication
- JWT-protected API endpoints
- Duplicate username and email prevention
- Environment variables for sensitive configuration

## Tech Stack

- Python
- Flask
- PostgreSQL
- SQLAlchemy
- Flask-SQLAlchemy
- Flask-Login
- Flask-Bcrypt
- Flask-JWT-Extended
- Flask-WTF
- HTML
- CSS
- Postman

## Authentication

AccountHub supports two authentication approaches.

### Web Authentication

The web interface uses Flask-Login for session-based authentication.

After a user logs in successfully, a session is created and protected pages such as the dashboard can only be accessed by authenticated users.

### API Authentication

The REST API uses JSON Web Tokens (JWT) for stateless authentication.

After successful API login, the server returns an access token. The token can then be supplied as a Bearer token when accessing protected API endpoints.

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/register` | Register a new user |
| POST | `/api/login` | Authenticate a user and receive a JWT |
| GET | `/api/profile` | Retrieve the authenticated user's profile |

The `/api/profile` endpoint requires a valid JWT access token.

Example authorization header:

```text
Authorization: Bearer <access_token>

```markdown
## Security

- Passwords are hashed using Bcrypt before being stored
- Protected web routes require an authenticated session
- Protected API routes require a valid JWT
- Sensitive credentials and secret keys are stored in environment variables

AccountHub
├── Short description
├── Features
├── Tech Stack
├── Authentication
│   ├── Web Authentication
│   └── API Authentication
├── API Endpoints
└── Security
