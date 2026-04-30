# Installation Guide

This guide walks you through setting up MyApp on your local machine for development or testing.

## Prerequisites

Before you begin, make sure you have the following installed:

| Tool | Minimum Version | Download |
|---|---|---|
| Node.js | 18.x | https://nodejs.org |
| npm | 9.x | Included with Node.js |
| PostgreSQL | 14.x | https://www.postgresql.org |
| Git | 2.x | https://git-scm.com |

---

## 1. Clone the Repository

```bash
git clone https://github.com/zhfrann/myapp.git
cd myapp
```

---

## 2. Install Dependencies

```bash
npm install
```

---

## 3. Configure Environment Variables

Copy the example environment file and fill in your values:

```bash
cp .env.example .env
```

Open `.env` and set the following variables:

```env
# Application
APP_PORT=3000
APP_ENV=development
APP_SECRET=your-super-secret-key

# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=myapp_dev
DB_USER=postgres
DB_PASSWORD=your-db-password

# Email (for notifications)
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=notifications@example.com
SMTP_PASS=your-smtp-password
```

---

## 4. Set Up the Database

Create the database and run migrations:

```bash
# Create the database
createdb myapp_dev

# Run migrations
npm run db:migrate

# (Optional) Seed with sample data
npm run db:seed
```

---

## 5. Start the Development Server

```bash
npm run dev
```

The application will be available at `http://localhost:3000`.

---

## 6. Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Generate coverage report
npm run test:coverage
```

---

## Troubleshooting

### Port already in use

```bash
# Find the process using port 3000
lsof -i :3000

# Kill it
kill -9 <PID>
```

### Database connection refused

Make sure PostgreSQL is running:

```bash
# macOS (Homebrew)
brew services start postgresql

# Ubuntu / Debian
sudo service postgresql start

# Windows
net start postgresql-x64-14
```

### Dependency errors after pulling changes

```bash
npm clean-install
npm run db:migrate
```

---

## Next Steps

- Read [docs/USAGE.md](USAGE.md) to learn how to use the application
- Check [docs/API.md](API.md) for the full API reference
