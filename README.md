# NestJS Authentication Service

A robust authentication service built with NestJS that implements secure user authentication, password recovery, and email verification workflows.

## Features

- 🔐 Secure JWT-based authentication
- 📧 Email-based password recovery flow
- 🔒 Rate limiting and brute force protection
- 📝 Password reset with secure tokens
- 🛡️ Security headers and best practices
- 📋 Validation and sanitization
- 🔄 Session management
- 📱 Device-aware authentication

## Tech Stack

- NestJS 11.x
- PostgreSQL (via TypeORM)
- Node.js 23.x
- Docker & Docker Compose
- NodeMailer for email services
- JWT for token management
- bcrypt for password hashing

## Prerequisites

- Node.js 23.x or higher
- Docker and Docker Compose
- PostgreSQL instance
- SMTP email service

## Getting Started

1. Clone the repository
2. Copy `demo.env` to `.env` and configure your environment variables:

```sh
cp demo.env .env
```

3. Install dependencies:

```sh
npm install
```

4. Start the services using Docker:

```sh
docker-compose up
```

## Environment Configuration

Key environment variables needed in `.env`:

```env
# Database
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=your_username
DB_PASSWORD=your_password
DB_DATABASE=your_database

# JWT
JWT_SECRET=your_secret_key
JWT_EXPIRATION=1h

# SMTP
SMTP_HOST=your_smtp_host
SMTP_PORT=587
SMTP_USER=your_smtp_username
SMTP_PASS=your_smtp_password
SMTP_FROM=your_sender_email
```

## Authentication Flow

### 1. Login Flow
- POST `/auth/login`
- Validates credentials
- Returns JWT token
- Implements rate limiting and brute force protection

### 2. Password Recovery Flow
- POST `/auth/recover`
  - User requests password reset
  - System sends email with reset token
- POST `/auth/verify`
  - User submits token and new password
  - System validates token and updates password

## Security Features

- Rate limiting on authentication endpoints
- Account lockout after failed attempts
- Secure password hashing with bcrypt
- JWT token expiration
- Security headers (HSTS, XSS Protection, etc.)
- Input validation and sanitization
- Session management and tracking

## API Endpoints

### Authentication
```typescript
POST /auth/login
Body: {
  "email": string,
  "password": string
}

POST /auth/recover
Body: {
  "email": string
}

POST /auth/verify
Body: {
  "token": string,
  "password": string
}
```

## Development

### Running Tests

```sh
# Unit tests
npm run test

# e2e tests
npm run test:e2e

# Test coverage
npm run test:cov
```

### Development Server

```sh
# Development
npm run start:dev

# Production
npm run start:prod
```

## Docker Support

Build and run using Docker:

```sh
# Build the container
docker-compose build

# Start services
docker-compose up

# Stop services
docker-compose down
```

## Future Enhancements

- [ ] Two-factor authentication (2FA)
- [ ] OAuth2 integration
- [ ] Remember me functionality
- [ ] Account activity logging
- [ ] IP-based security

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.