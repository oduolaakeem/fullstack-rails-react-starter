# Fullstack Rails + React Starter — Repository Instructions

## 1. Purpose

This repository provides a reusable foundation for applications built with Ruby on Rails, React, TypeScript, PostgreSQL, and Docker Compose.

The starter is intentionally product-agnostic. Do not assume any particular business domain, user journey, AI capability, or product requirement.

Project-specific requirements should be defined by the application built from this starter.

## 2. Engineering Principles

- Build the smallest useful implementation.
- Prefer conventional Rails and React patterns.
- Keep frontend and backend responsibilities separate.
- Use test-driven development for meaningful behavior changes.
- Avoid premature abstraction and unnecessary dependencies.
- Make important behavior observable and testable.
- Document significant architectural decisions.
- Do not invent product requirements.
- Do not implement work outside the agreed scope.

## 3. Development Workflow

For substantive changes, follow:

1. **Plan** — Confirm scope, acceptance criteria, affected components, and risks.
2. **Test** — Write or update relevant tests when introducing or changing behavior.
3. **Implement** — Make the smallest change that satisfies the requirements.
4. **Verify** — Run tests, builds, linting, and other relevant checks.
5. **Review** — Inspect the diff, security implications, and documentation.
6. **Commit** — Create a focused commit with a meaningful message.

Prefer the sequence:

**Fail → Implement → Pass → Refactor**

Do not consider work complete until its acceptance criteria have been verified.

## 4. Technology Stack

### Backend

- Ruby 4.0.7
- Rails 8.1.4, API-only
- PostgreSQL 17
- RSpec
- Docker

### Frontend

- React 19
- TypeScript 6
- Vite 8
- ESLint
- Node.js 24

Use the project's existing dependency files as the authoritative source for installed versions.

Do not introduce additional frameworks or services without a concrete requirement.

## 5. Architecture

The intended application boundary is:

**React + TypeScript → HTTP/JSON → Rails API → PostgreSQL**

The backend owns persistence, server-side validation, authorization, business rules, and API contracts.

The frontend owns presentation, user interactions, client-side state, and communication with the backend API.

Avoid duplicating business rules across both applications.

## 6. Backend Conventions

- Prefer conventional Rails patterns.
- Keep controllers focused.
- Keep domain behavior testable.
- Validate inputs at appropriate boundaries.
- Use RSpec for automated backend testing.
- Maintain predictable API responses.
- Avoid unnecessary abstraction layers.

## 7. Frontend Conventions

- Prefer small, clearly scoped React components.
- Use TypeScript types for application data and API contracts.
- Keep API communication explicit.
- Avoid placing server-side business rules in frontend components.
- Maintain passing TypeScript builds and ESLint checks.
- Add frontend tests when meaningful behavior is introduced.

## 8. Security

Never commit API keys, passwords, tokens, private credentials, production secrets, or sensitive user data.

Use appropriate environment configuration and secret management.

Do not expose sensitive information through logs, API responses, error messages, or test fixtures.

Treat authentication, authorization, external integrations, and user-submitted data as security-sensitive boundaries.

## 9. Git Workflow

Use the repository's established branching conventions.

For work on the starter itself, use:

- `main` — stable releases
- `develop` — integration branch
- `feature/ST-XXX-short-description` — feature branches

Applications generated from this starter may adopt their own branching and ticket conventions.

Keep commits small, focused, and related to one logical change.

## 10. Verification

Run relevant checks before committing.

### Backend

- Rails database preparation
- RSpec test suite
- Rails application boot checks when appropriate

### Frontend

- TypeScript and Vite production build
- ESLint

When verification cannot be performed, explain what remains unverified.

## 11. Starter Maintenance

Keep the starter generic.

Do not introduce product-specific models, interfaces, workflows, integrations, or assumptions into the shared foundation.

Prefer changes that improve reliability, maintainability, documentation, security, or developer experience across multiple projects.

Project initialization, dependency upgrades, and release procedures should follow the starter's documented maintenance process as those capabilities are introduced.
