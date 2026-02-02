# Setup Guide - Enterprise SaaS ERP

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Local Development Setup](#local-development-setup)
3. [Docker Setup](#docker-setup)
4. [Database Configuration](#database-configuration)
5. [Running the Application](#running-the-application)
6. [Testing](#testing)
7. [Troubleshooting](#troubleshooting)

---

## Prerequisites

### Required Software

- **PHP**: 8.3 or higher
- **Composer**: 2.5 or higher
- **Node.js**: 20.x or higher
- **npm**: 10.x or higher
- **PostgreSQL**: 16 or higher (or Docker)
- **Redis**: 7 or higher (or Docker)
- **Git**: Latest version

### Optional Software

- **Docker**: 24+ and Docker Compose 2+
- **VS Code** or **PHPStorm**: Recommended IDEs

---

## Local Development Setup

### 1. Clone the Repository

```bash
git clone https://github.com/kasunvimarshana/enterprise-saas-erp.git
cd enterprise-saas-erp
```

### 2. Backend Setup (Laravel)

```bash
cd backend

# Install PHP dependencies
composer install

# Copy environment file
cp .env.example .env

# Generate application key
php artisan key:generate

# Configure database in .env
# DB_CONNECTION=pgsql
# DB_HOST=127.0.0.1
# DB_PORT=5432
# DB_DATABASE=erp_saas
# DB_USERNAME=your_username
# DB_PASSWORD=your_password

# Run migrations
php artisan migrate

# Seed database (optional)
php artisan db:seed

# Install Laravel Sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"

# Run migrations for Sanctum
php artisan migrate

# Generate Swagger documentation
php artisan l5-swagger:generate
```

### 3. Frontend Setup (Vue.js)

```bash
cd frontend

# Install Node dependencies
npm install

# Copy environment file
cp .env.example .env

# Configure API endpoint in .env
# VITE_API_URL=http://localhost:8000/api
```

---

## Docker Setup

### Using Docker Compose (Recommended)

```bash
# From project root
docker-compose up -d

# Backend is available at: http://localhost:8000
# Frontend is available at: http://localhost:3000
# PostgreSQL is available at: localhost:5432
# Redis is available at: localhost:6379

# Run migrations in Docker
docker-compose exec app php artisan migrate

# Seed database
docker-compose exec app php artisan db:seed
```

### Docker Compose Services

- **app**: Laravel application (PHP 8.3 + Nginx)
- **postgres**: PostgreSQL 16 database
- **redis**: Redis 7 cache and queue
- **frontend**: Vue.js 3 application (Vite dev server)
- **queue**: Laravel queue worker
- **scheduler**: Laravel task scheduler

---

## Database Configuration

### Create Database

```bash
# Using psql
psql -U postgres
CREATE DATABASE erp_saas;
CREATE USER erp_user WITH ENCRYPTED PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE erp_saas TO erp_user;
\q
```

### Run Migrations

```bash
cd backend
php artisan migrate
```

### Seed Database

```bash
# Seed all seeders
php artisan db:seed

# Seed specific seeder
php artisan db:seed --class=TenantSeeder
```

---

## Running the Application

### Backend (Laravel)

```bash
cd backend

# Development server
php artisan serve
# Available at: http://localhost:8000

# Queue worker (separate terminal)
php artisan queue:work

# Schedule runner (separate terminal)
php artisan schedule:work
```

### Frontend (Vue.js)

```bash
cd frontend

# Development server
npm run dev
# Available at: http://localhost:3000

# Build for production
npm run build

# Preview production build
npm run preview
```

---

## Testing

### Backend Tests

```bash
cd backend

# Run all tests
php artisan test

# Run specific test suite
php artisan test --testsuite=Feature
php artisan test --testsuite=Unit

# Run with coverage
php artisan test --coverage

# Run specific test file
php artisan test tests/Feature/Auth/LoginTest.php
```

### Frontend Tests

```bash
cd frontend

# Run unit tests
npm run test:unit

# Run component tests
npm run test:component

# Run E2E tests
npm run test:e2e

# Run with coverage
npm run test:coverage
```

### Code Quality

```bash
cd backend

# Run PHPStan
./vendor/bin/phpstan analyse

# Run Laravel Pint (formatting)
./vendor/bin/pint

# Run security checks
composer audit
```

```bash
cd frontend

# Run ESLint
npm run lint

# Fix ESLint issues
npm run lint:fix

# Run Prettier
npm run format

# Type check
npm run type-check
```

---

## Environment Variables

### Backend (.env)

```env
APP_NAME="Enterprise SaaS ERP"
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_TIMEZONE=UTC
APP_URL=http://localhost:8000

# Database
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=erp_saas
DB_USERNAME=erp_user
DB_PASSWORD=your_password

# Redis
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

# Cache
CACHE_STORE=redis
CACHE_PREFIX=erp_cache

# Queue
QUEUE_CONNECTION=redis

# Session
SESSION_DRIVER=redis
SESSION_LIFETIME=120

# Mail
MAIL_MAILER=smtp
MAIL_HOST=mailhog
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="noreply@erp.local"
MAIL_FROM_NAME="${APP_NAME}"

# Sanctum
SANCTUM_STATEFUL_DOMAINS=localhost:3000,127.0.0.1:3000

# Multi-tenancy
TENANT_ROUTE_PREFIX=tenant
TENANT_DATABASE_PREFIX=tenant_
```

### Frontend (.env)

```env
VITE_APP_NAME="Enterprise SaaS ERP"
VITE_API_URL=http://localhost:8000/api
VITE_API_VERSION=v1
VITE_APP_LOCALE=en
VITE_APP_FALLBACK_LOCALE=en
```

---

## IDE Setup

### VS Code Extensions

Install the following extensions:

- PHP Intelephense
- Laravel Extra Intellisense
- Laravel Blade Snippets
- Volar (Vue Language Features)
- TypeScript Vue Plugin (Volar)
- ESLint
- Prettier - Code formatter
- Tailwind CSS IntelliSense
- GitLens
- Docker

### VS Code Settings

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[php]": {
    "editor.defaultFormatter": "bmewburn.vscode-intelephense-client"
  },
  "php.suggest.basic": false,
  "intelephense.files.maxSize": 5000000,
  "typescript.tsdk": "frontend/node_modules/typescript/lib"
}
```

### PHPStorm Configuration

1. Enable Laravel plugin
2. Configure PHP interpreter (PHP 8.3+)
3. Configure Composer
4. Configure Node.js and npm
5. Enable Tailwind CSS support
6. Configure Vue.js support

---

## Troubleshooting

### Common Issues

#### 1. Composer Install Fails

```bash
# Clear composer cache
composer clear-cache

# Update composer
composer self-update

# Try install again
composer install --ignore-platform-reqs
```

#### 2. Migration Errors

```bash
# Reset database
php artisan migrate:fresh

# Rollback and re-migrate
php artisan migrate:rollback
php artisan migrate
```

#### 3. Permission Errors

```bash
# Fix storage permissions
chmod -R 775 storage bootstrap/cache
chown -R www-data:www-data storage bootstrap/cache
```

#### 4. Frontend Build Errors

```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install

# Clear Vite cache
rm -rf frontend/.vite
```

#### 5. Docker Issues

```bash
# Rebuild containers
docker-compose down
docker-compose build --no-cache
docker-compose up -d

# View logs
docker-compose logs -f app

# Execute command in container
docker-compose exec app bash
```

### Database Connection Issues

1. Verify PostgreSQL is running
2. Check database credentials in .env
3. Ensure database exists
4. Check firewall rules
5. Verify pg_hba.conf settings

### Redis Connection Issues

1. Verify Redis is running: `redis-cli ping`
2. Check Redis credentials in .env
3. Verify Redis port is not blocked
4. Clear Redis cache: `redis-cli FLUSHALL`

---

## Development Workflow

### 1. Create Feature Branch

```bash
git checkout -b feature/my-feature
```

### 2. Make Changes

- Write code following coding standards
- Write tests for new features
- Update documentation

### 3. Run Tests and Checks

```bash
# Backend
php artisan test
./vendor/bin/phpstan analyse
./vendor/bin/pint

# Frontend
npm run test
npm run lint
npm run type-check
```

### 4. Commit Changes

```bash
git add .
git commit -m "feat: add new feature"
```

Follow [Conventional Commits](https://www.conventionalcommits.org/):
- `feat:` for new features
- `fix:` for bug fixes
- `docs:` for documentation
- `refactor:` for code refactoring
- `test:` for tests
- `chore:` for maintenance

### 5. Push and Create Pull Request

```bash
git push origin feature/my-feature
```

Then create a Pull Request on GitHub.

---

## Production Deployment

See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed production deployment instructions.

---

## Getting Help

### Resources

- **Documentation**: [/docs](../docs)
- **API Documentation**: http://localhost:8000/api/documentation
- **GitHub Issues**: https://github.com/kasunvimarshana/enterprise-saas-erp/issues
- **Discussions**: https://github.com/kasunvimarshana/enterprise-saas-erp/discussions

### Community

- Join our Discord server
- Follow on Twitter
- Subscribe to our YouTube channel

---

## Next Steps

After setting up the development environment:

1. Review [ARCHITECTURE.md](ARCHITECTURE.md) to understand the system architecture
2. Read [IMPLEMENTATION_ROADMAP.md](IMPLEMENTATION_ROADMAP.md) for the development plan
3. Check [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines
4. Explore the [API documentation](http://localhost:8000/api/documentation)
5. Run the test suite to verify everything works

---

**Document Version**: 1.0  
**Last Updated**: 2026-02-02  
**Maintainer**: enterprise-saas-erp Development Team
