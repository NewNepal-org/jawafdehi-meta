# Technology Stack

## Backend Services

### Nepal Entity Service (NES)
- **Language**: Python 3.12+
- **Package Manager**: Poetry
- **Framework**: FastAPI (optional API extra)
- **Database**: File-based JSON storage with optional in-memory caching
- **CLI**: Click
- **Testing**: pytest, pytest-asyncio, hypothesis
- **Code Quality**: black, isort, flake8

### Jawafdehi API (JDS)
- **Language**: Python 3.12+
- **Package Manager**: Poetry
- **Framework**: Django 5.2+, Django REST Framework
- **Database**: PostgreSQL (via psycopg2-binary)
- **Admin**: Jazzmin (Bootstrap 4)
- **API Docs**: drf-spectacular (OpenAPI)
- **Permissions**: django-rules
- **Testing**: pytest, pytest-django, hypothesis
- **Server**: Gunicorn

## Frontend Services

### Jawafdehi Frontend
- **Language**: TypeScript
- **Runtime**: Node.js
- **Package Manager**: npm
- **Framework**: React 18, Vite
- **Routing**: react-router-dom
- **UI Components**: Radix UI, shadcn/ui
- **Styling**: Tailwind CSS
- **Forms**: react-hook-form, zod
- **State**: @tanstack/react-query
- **i18n**: i18next, react-i18next
- **Testing**: Vitest, jsdom

### Tundikhel
- **Language**: TypeScript
- **Runtime**: Node.js
- **Package Manager**: npm
- **Framework**: React 19, Vite (rolldown-vite)
- **Routing**: react-router-dom
- **Markdown**: react-markdown

## Infrastructure

### Deployment
- **Platform**: Google Cloud Platform
- **IaC**: Terraform
- **Container Registry**: GCR
- **Compute**: Cloud Run
- **Database**: Cloud SQL PostgreSQL 18
- **CI/CD**: Cloud Build
- **Load Balancer**: Global HTTPS with managed SSL

### Containerization
- **Base Images**: python:3.12-slim
- **Build Tool**: Docker

## Common Commands

### Nepal Entity Service
```bash
# Install with all extras
poetry install --extras all

# Run API server
poetry run nes-api

# Run CLI
poetry run nes --help

# Run tests
poetry run pytest

# Format code
poetry run black .
poetry run isort .

# Lint
poetry run flake8
```

### Jawafdehi API
```bash
# Install dependencies
poetry install

# Run development server
poetry run python manage.py runserver

# Run migrations
poetry run python manage.py migrate

# Create superuser
poetry run python manage.py createsuperuser

# Collect static files
poetry run python manage.py collectstatic

# Run tests
poetry run pytest

# Run with Gunicorn (production)
poetry run gunicorn config.wsgi:application --bind 0.0.0.0:8080
```

### Frontend Services (Jawafdehi & Tundikhel)
```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Lint
npm run lint

# Preview production build
npm run preview

# Deploy (GitHub Pages)
npm run deploy
```

### Infrastructure
```bash
# Initialize Terraform
cd gcp-infra/terraform
terraform init

# Plan changes
terraform plan

# Apply changes
terraform apply

# Destroy infrastructure
terraform destroy
```

## Environment Configuration

### NES
- `NES_DB_URL`: Database path (file:// or file+memcached://)

### JDS
- `SECRET_KEY`: Django secret key
- `DEBUG`: Debug mode (True/False)
- `ALLOWED_HOSTS`: Comma-separated hostnames
- `CSRF_TRUSTED_ORIGINS`: Comma-separated origins
- `DATABASE_URL`: PostgreSQL connection string
- `NES_API_URL`: Nepal Entity Service API URL
- `EXPOSE_CASES_IN_REVIEW`: Feature flag (True/False)

## Code Quality Standards

### Python
- **Formatter**: black (line length: 88)
- **Import Sorter**: isort (black profile)
- **Linter**: flake8
- **Type Hints**: Encouraged but not enforced
- **Testing**: pytest with hypothesis for property-based testing

### TypeScript/JavaScript
- **Linter**: ESLint
- **Type Checking**: TypeScript strict mode
- **Testing**: Vitest
