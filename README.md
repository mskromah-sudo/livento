# Lavent v3 — MVP Scaffold (Prisma, Migrations, CI, Tests)

This scaffold includes:
- lavent-auth-service (Express + Postgres + Prisma) — /services/auth-service
- lavent-crm-service (Express + Postgres) — /services/crm-service
- web client (placeholder) — /apps/web-client
- docker-compose.yml to run everything locally (Postgres + services + web)
- GitHub Actions CI pipeline that runs on every push (build, migrate, seed, run tests)

## Quick start (local)

1. Copy `.env.example` to `.env` and adjust if needed.
2. Run:
   ```
   docker compose up --build
   ```
   The auth service's Dockerfile runs `npx prisma migrate deploy` and attempts to run the seed script at container start.
3. Visit the web client at http://localhost:3000 (placeholder)
4. Use the Register form (if you build the web client) or use API endpoints directly.

## Running tests locally (example for auth-service)
1. Enter the auth service container:
   ```
   docker compose run --rm lavent-auth-service sh
   ```
2. From inside container:
   ```
   npm test
   ```

## GitHub Actions CI (.github/workflows/ci.yml)
- Runs on every push to any branch.
- Installs Node, runs migrations, seeds DB, runs tests for services, and builds Docker images.

