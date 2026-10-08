# React + TypeScript Frontend

This directory contains the frontend application for the Fullstack Rails + React Starter.

The frontend uses React 19, TypeScript 6, Vite 8, ESLint, and Node.js 24.

It provides a product-agnostic foundation for building user interfaces that communicate with a Rails API backend.

## Architecture

The frontend is a standalone React application.

Key files and directories:

- `src/App.tsx` — root application component
- `src/main.tsx` — React entry point
- `src/App.css` — application-level styles
- `src/index.css` — global styles
- `public/` — static public assets
- `vite.config.ts` — Vite configuration
- `eslint.config.js` — ESLint configuration

The Rails API backend lives separately in `../backend/`.

## Prerequisites

- Docker Desktop or a compatible Docker Engine
- Docker Compose

The commands below should be run from the **repository root**.

## Build the frontend Docker image

```bash
docker compose build frontend
```

## Start the development server

```bash
docker compose up frontend
```

By default, the frontend is available at:

**http://localhost:5174**

The Vite development server listens on port `5173` inside the container.

The host port defaults to `5174` to reduce conflicts with other local projects.

To use a different host port, set `FRONTEND_PORT` before starting the service.

For example, on Git Bash:

```bash
FRONTEND_PORT=5180 docker compose up frontend
```

The frontend will then be available at `http://localhost:5180`.

## Run the production build

```bash
docker compose run --rm --no-deps frontend npm run build
```

This command runs TypeScript validation and builds optimized production assets with Vite.

## Run ESLint

```bash
docker compose run --rm --no-deps frontend npm run lint
```

ESLint checks the frontend source code for violations of the configured linting rules.

## Dependencies

Frontend dependencies are declared in:

- `package.json`
- `package-lock.json`

The Docker image installs dependencies using `npm ci` for reproducible installation.

Do not manually edit `package-lock.json`. Use npm commands when adding, removing, or updating packages.

## Backend integration

The frontend and backend are separate applications.

Communication between them should use explicit HTTP/JSON API contracts.

This starter does not yet provide application-specific endpoints, API clients, authentication flows, or business logic.

Configure API integration according to the needs of the application created from this starter.

## Starter interface

The initial frontend includes a basic Vite/React interface and demonstration assets.

These are placeholders and can be replaced with the application's own components, styles, and branding.

## Stop the frontend

If the frontend is running in the foreground, press `Ctrl+C`.

To stop the project's Docker Compose services, run:

```bash
docker compose down
```

This preserves the project's named PostgreSQL volume.
