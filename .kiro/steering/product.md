# Product Overview

This is a civic tech platform ecosystem for promoting transparency and accountability in Nepali governance.

## Core Services

### Nepal Entity Service (NES)
Open-source entity management system for Nepali public entities (politicians, organizations, locations). Provides a Python package with optional API and scraping capabilities. Licensed under Hippocratic License 3.0.

### Jawafdehi API (JDS)
Django-based public accountability platform for tracking allegations of corruption, misconduct, and broken promises by public entities in Nepal. Features a revision system, role-based permissions (Admin/Moderator/Contributor), and integration with NES.

### Jawafdehi Frontend
React-based public-facing web application for browsing cases, entity profiles, and submitting allegations. Bilingual support (English/Nepali).

### Tundikhel
React-based documentation and exploration interface for Nepal Entity Service.

## Key Principles

- **Open Data**: All entity data is open and accessible
- **Transparency**: Complete audit trails and version history
- **Nepali Context**: Use authentic Nepali names, organizations, and locations in examples and documentation
- **Ethical Source**: Licensed under Hippocratic License 3.0 (NES) and MIT (others)
- **Civic Tech**: Built by Let's Build Nepal (LBN) and NewNepal.org

## Infrastructure

Deployed on Google Cloud Platform with:
- Cloud Run for containerized services
- Cloud SQL PostgreSQL for relational data
- Cloud Build for CI/CD
- Global HTTPS load balancers with managed SSL
