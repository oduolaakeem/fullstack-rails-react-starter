# Fullstack Rails + React Starter

A reusable, product-agnostic fullstack application foundation built with Ruby on Rails, React, TypeScript, PostgreSQL, and Docker Compose.

This repository provides a working starting point for new projects without repeating the initial backend, frontend, database, and testing setup.

## Technology Stack

| Component | Technology |
|---|---|
| Backend | Ruby 4.0.7, Rails 8.1.4 (API-only) |
| Frontend | React 19, TypeScript 6, Vite 8 |
| Database | PostgreSQL 17 |
| Backend testing | RSpec |
| Frontend code quality | TypeScript, ESLint |
| Runtime | Docker Compose |

## Repository Structure

```text
fullstack-rails-react-starter/
├── backend/          # Rails API application
├── frontend/         # React + TypeScript application
├── Dockerfile        # Backend Docker image
├── compose.yaml      # Application services
├── AGENTS.md         # Repository engineering instructions
└── README.md         # Main project documentation
```

## Prerequisites

Install:

- Docker Desktop or a compatible Docker Engine
- Docker Compose
- Git

Ruby, Rails, Node.js, and PostgreSQL run inside Docker, so separate local installations are not required for the documented workflow.

## Quick Start

Run these commands from the repository root.

### 1. Build the application images

```bash
docker compose build
```

### 2. Start PostgreSQL

```bash
docker compose up -d db
```

Verify that PostgreSQL is ready:

```bash
docker compose exec db pg_isready -U postgres
```

### 3. Prepare the Rails databases

```bash
docker compose run --rm -w /app/backend app bin/rails db:prepare
```

The default databases are:

- `starter_app_development`
- `starter_app_test`

### 4. Start the React development server

```bash
docker compose up frontend
```

Open **http://localhost:5174**.

The frontend uses port `5173` inside Docker and port `5174` on the host by default.

To change the host port:

```bash
FRONTEND_PORT=5180 docker compose up frontend
```

The frontend will then be available at **http://localhost:5180**.

## Verification

### Backend tests

```bash
docker compose run --rm -w /app/backend -e RAILS_ENV=test app bundle exec rspec
```

### Rails boot check

```bash
docker compose run --rm -w /app/backend app bin/rails runner 'puts "Starter Rails API booted: #{Rails.version}"'
```

### Frontend production build

```bash
docker compose run --rm --no-deps frontend npm run build
```

### Frontend linting

```bash
docker compose run --rm --no-deps frontend npm run lint
```

**Windows Git Bash:** Prefix commands that use `-w /app/backend` with `MSYS_NO_PATHCONV=1` to prevent Windows path conversion.

For example:

```bash
MSYS_NO_PATHCONV=1 docker compose run --rm -w /app/backend app bin/rails db:prepare
```

## Architecture

The starter follows an API-first architecture:

**React + TypeScript → HTTP/JSON → Rails API → PostgreSQL**

The frontend and backend are separate applications.

The Rails API provides the foundation for persistence, validation, business logic, and HTTP endpoints.

The React frontend provides the foundation for user interfaces and API communication.

Application-specific API endpoints and frontend integration must be implemented by each project.

## Configuration and Customization

The starter currently uses generic database names and Docker Compose defaults.

Project-specific naming, automated initialization, and template upgrade tooling are planned enhancements and are not yet implemented.

Until those capabilities are available, applications created from this foundation require manual customization.

The starter is not a complete production deployment configuration.

## Security

Do not commit private credentials, API keys, master keys, environment secrets, or sensitive application data.

The starter intentionally excludes the source application's encrypted Rails credentials.

Generate and manage application-specific credentials when needed.

The PostgreSQL credentials in the development Compose configuration are intended for local development only. Replace them with appropriately managed secrets for any deployed environment.

## Documentation

- `backend/README.md` — Rails setup, database preparation, and testing
- `frontend/README.md` — React development, builds, and linting
- `AGENTS.md` — engineering principles and development workflow

## Development Workflow

Changes to this starter follow:

**Plan → Test → Implement → Verify → Review → Commit → Pull Request → Merge**

The repository uses `main` for stable releases, `develop` for integration, and `feature/ST-XXX-*` branches for starter development.

## Project Status

The starter foundation is under development.

The initial milestone establishes an independently buildable and testable Rails + React foundation.

Upcoming work includes project initialization, continuous integration, dependency maintenance, template upgrades, and release validation.

## Stopping the Environment

```bash
docker compose down
```

This stops the Compose services while preserving PostgreSQL data.

Avoid `docker compose down -v` unless you intentionally want to delete the database volume.
