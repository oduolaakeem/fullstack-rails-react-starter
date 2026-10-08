# Rails API Backend

This directory contains the Ruby on Rails API application for the Fullstack Rails + React Starter.

The backend uses Rails 8.1.4, Ruby 4.0.7, PostgreSQL 17, and RSpec. It provides a product-agnostic foundation for implementing application-specific APIs and business logic.

## Architecture

The backend is an API-only Rails application.

- `app/controllers/` — HTTP request handling
- `app/models/` — Active Record models and application data
- `config/` — Rails configuration
- `db/` — database schema, migrations, and seeds
- `spec/` — automated RSpec tests

The React frontend lives separately in `../frontend/`.

## Prerequisites

- Docker Desktop or a compatible Docker Engine
- Docker Compose

Run the commands below from the **repository root**, not from this directory.

## Build the backend

```bash
docker compose build app
```

## Start PostgreSQL

```bash
docker compose up -d db
```

Check that PostgreSQL is ready:

```bash
docker compose exec db pg_isready -U postgres
```

## Prepare the databases

The default database names are:

- `starter_app_development`
- `starter_app_test`

Prepare the development database:

```bash
docker compose run --rm -w /app/backend app bin/rails db:prepare
```

Prepare the test database:

```bash
docker compose run --rm -w /app/backend -e RAILS_ENV=test app bin/rails db:prepare
```

**Windows Git Bash:** Prefix commands using the container working directory with `MSYS_NO_PATHCONV=1` to prevent unwanted path conversion.

For example:

```bash
MSYS_NO_PATHCONV=1 docker compose run --rm -w /app/backend app bin/rails db:prepare
```

## Run automated tests

```bash
docker compose run --rm -w /app/backend -e RAILS_ENV=test app bundle exec rspec
```

The initial integration test verifies that Rails connects to the `starter_app_test` PostgreSQL database.

## Verify Rails boots

```bash
docker compose run --rm -w /app/backend app bin/rails runner 'puts "Starter Rails API booted: #{Rails.version}"'
```

Expected output includes:

```text
Starter Rails API booted: 8.1.4
```

## Rails credentials

Do not copy credentials or master keys from another application.

The starter does not include a shared Rails master key or encrypted credentials file.

If your application requires Rails encrypted credentials, generate and manage them for that application. Never commit the master key or production secrets.

## Application development

The starter does not define product-specific models, endpoints, authentication, authorization, or business rules.

Implement those features according to the requirements of the application created from this foundation.

## Stop the database

```bash
docker compose down
```

This stops the project's containers and removes its Compose network while preserving the PostgreSQL named volume.

Do not use `docker compose down -v` unless you intentionally want to delete the project's database data.
