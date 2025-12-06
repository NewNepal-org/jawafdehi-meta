# Project Structure

## Repository Layout

```
/
├── gcp-infra/              # Infrastructure as Code
│   ├── terraform/          # Terraform configuration
│   └── misc/               # Build configs and scripts
│
└── services/               # All application services
    ├── NepalEntityService/     # Core entity management service
    ├── NepalEntityService-assets/  # Static assets (Jekyll site)
    ├── NepalEntityService-tundikhel/  # Documentation UI
    ├── JawafdehiAPI/       # Django accountability API
    └── Jawafdehi/          # React public frontend
```

## Nepal Entity Service Structure

```
services/NepalEntityService/
├── nes/                    # Main package
│   ├── api/               # FastAPI server
│   ├── cli/               # Click CLI commands
│   ├── core/              # Core business logic
│   ├── database/          # Database implementations
│   ├── models/            # Pydantic models
│   ├── services/          # Service layer
│   └── config.py          # Configuration
├── tests/                 # Test suite
│   ├── api/              # API tests
│   ├── cli/              # CLI tests
│   ├── core/             # Core logic tests
│   ├── database/         # Database tests
│   ├── services/         # Service tests
│   ├── fixtures/         # Test fixtures
│   └── conftest.py       # Pytest configuration
├── docs/                  # Documentation
│   ├── contributors/     # Contributor guides
│   ├── consumers/        # API consumer guides
│   └── templates/        # Doc templates
├── migrations/            # Database migrations
├── examples/              # Usage examples
├── nes-db/               # Database storage
│   └── v2/               # Version 2 schema
└── pyproject.toml        # Poetry configuration
```

## Jawafdehi API Structure

```
services/JawafdehiAPI/
├── config/                # Django project settings
│   ├── settings.py       # Main settings
│   ├── urls.py           # URL routing
│   └── wsgi.py           # WSGI application
├── cases/                 # Main Django app
│   ├── models.py         # Data models
│   ├── serializers.py    # DRF serializers
│   ├── api_views.py      # API views
│   ├── admin.py          # Admin interface
│   ├── rules/            # Permission rules
│   ├── migrations/       # Database migrations
│   ├── static/           # Static files
│   └── templates/        # HTML templates
├── tests/                 # Test suite
│   ├── api/              # API tests
│   ├── e2e/              # End-to-end tests
│   ├── conftest.py       # Pytest configuration
│   └── strategies.py     # Hypothesis strategies
├── docs/                  # Documentation
├── static/                # Project-wide static files
├── staticfiles/           # Collected static files
├── tmp/                   # Temporary scripts
└── pyproject.toml        # Poetry configuration
```

## Frontend Structure (Jawafdehi & Tundikhel)

```
services/Jawafdehi/  (or NepalEntityService-tundikhel/)
├── src/
│   ├── components/       # React components
│   │   └── ui/          # Reusable UI components (shadcn)
│   ├── pages/           # Page components
│   ├── hooks/           # Custom React hooks
│   ├── services/        # API services
│   ├── api/             # API client code
│   ├── types/           # TypeScript types
│   ├── utils/           # Utility functions
│   ├── i18n/            # Internationalization
│   │   ├── config.ts    # i18n configuration
│   │   └── locales/     # Translation files
│   ├── App.tsx          # Main app component
│   └── main.tsx         # Entry point
├── public/              # Static assets
├── tests/               # Test files
├── docs/                # Documentation
├── package.json         # npm configuration
├── tsconfig.json        # TypeScript config
├── vite.config.ts       # Vite config
└── tailwind.config.ts   # Tailwind config
```

## Infrastructure Structure

```
gcp-infra/
├── terraform/
│   ├── main.tf          # Main infrastructure
│   ├── variables.tf     # Variable definitions
│   ├── outputs.tf       # Output values
│   ├── versions.tf      # Provider versions
│   ├── terraform.tfvars # Variable values (gitignored)
│   └── terraform.tfvars.example  # Example values
└── misc/
    ├── nes-config.yaml  # NES Cloud Build config
    ├── jds-config.yaml  # JDS Cloud Build config
    └── manage-triggers.sh  # Trigger management script
```

## Key Conventions

### Python Services
- **Package Structure**: Flat module structure under main package name
- **Tests**: Mirror source structure in `tests/` directory
- **Config**: Environment-based configuration with `.env` files
- **Database**: File-based storage for NES, PostgreSQL for JDS
- **Migrations**: Versioned migration system

### Frontend Services
- **Components**: Organized by feature/page, with shared UI components
- **Routing**: File-based routing with react-router-dom
- **State**: React Query for server state, React hooks for local state
- **Styling**: Tailwind utility classes, shadcn components
- **i18n**: Separate locale files for English and Nepali

### Testing
- **Python**: pytest with fixtures in `conftest.py`
- **Property Testing**: hypothesis for Python, vitest for TypeScript
- **Test Data**: Authentic Nepali names and entities in fixtures
- **Coverage**: Unit, integration, and E2E tests

### Documentation
- **Location**: `docs/` directory in each service
- **Format**: Markdown
- **Categories**: Contributors, consumers, templates
- **Examples**: Separate `examples/` directory with runnable code

### Deployment
- **Containerization**: Dockerfile in each service root
- **Environment**: `.env` files (gitignored), `.env.example` committed
- **Static Files**: Collected to `staticfiles/` or `dist/`
- **Port Conventions**: 8195 (NES), 8080 (JDS), 5173 (Vite dev)
