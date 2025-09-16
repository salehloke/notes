# Repository Guidelines

  

## Project Structure & Module Organization

- `backend/`: NestJS monorepo with apps `auth`, `smile`, `backoffice`, `tracker`, `wellness`, `broker`.

- `portal/`: Next.js 14 (11500). `backoffice-x/`: Next.js 14 (11400). `frontend/`: Next.js app.

- `micro-site/`: `enjoy` (Next 15), `flood-risk` (React+TS), `survey` (Vite), `web-campaign`, `find-agent`, `maintenance-page`.

- `database/`: MongoDB migrations (migrate-mongo); Prisma client for backend.

- `pm2/`, `container/`, `nginx/`: PM2 configs, Docker Compose infra, Nginx.

- `cypress/`: E2E tests and config.

  

## Build, Test, and Development Commands

- Root (PM2 via yarn)

- `yarn local`: Start all apps via PM2 (`pm2/local.config.js`).

- `yarn local --only backend,auth,backoffice,backoffice-x`: Start a subset (comma-separated app names from `pm2/config.js`).

- Envs: `yarn mss:sit`, `yarn mss:uat`, `yarn mss:prd`.

- Infra: `yarn docker`, `yarn sonarqube`, `yarn close:docker`.

- Makefile: `make install`, key builds (`build-step-backend-nestjs`, `build-step-portal-nextjs-web`), package (`make pack`, `make pack-tar`).

- Cleanup: `yarn del:*`.

- Backend

- Preferred: use PM2 selection (`yarn local --only backend` etc.).

- Direct: `cd backend && yarn dev:smile|dev:auth|dev:backoffice|dev:tracker|dev:wellness|dev:broker`.

- Quality: `yarn test|test:cov|lint|format`; Prisma: `yarn prisma:g`.

- Frontends

- Portal (11500): `cd portal && yarn dev|dev:uat|dev:production`.

- Backoffice-X (11400): Preferred via PM2 (`yarn local`); direct: `cd backoffice-x && yarn dev`.

- Frontend: `cd frontend && yarn dev`; all Next.js apps: `yarn build && yarn start`.

- Cypress

- `cd cypress && yarn && yarn cypress:open` (or `npx cypress run`).

  

## Coding Style & Naming Conventions

- TypeScript-first (strict). Prettier + ESLint (backend: `yarn format|lint`; Next.js apps: `yarn lint`).

- Indentation 2 spaces; camelCase (vars), PascalCase (classes/components), kebab-case (dirs/files). Tests: `*.spec.ts` (unit), `*.cy.ts` (e2e).

  

## Testing Guidelines

- Backend: Jest (`yarn test`, `yarn test:cov`), coverage in `backend/coverage`.

- E2E: Cypress specs under `cypress/cypress/e2e/**`; config via `cypress.config.ts` and `cypress.env.json`.

- SonarQube optional (`yarn sonarqube`). Maintain/raise coverage; prioritize service/controller unit tests and lightweight integrations.

  

## Commit & Pull Request Guidelines

- Commits: Short, imperative subject; include scope/ticket when relevant.

- Examples: `feat(portal): add OTP step [ES-3907]`, `fix: remove base64 log`.

- PRs: Clear description, linked issues/tickets, screenshots (UI), verify steps, and env/PM2 notes. Keep changes focused; ensure lint/builds pass.

  

## Security & Configuration

- Never commit secrets. Use `.env*` per app (portal uses `env-cmd`). PM2 configs under `pm2/*.config.js`.

- Prefer Docker for local infra (`yarn docker`). After schema changes: `cd backend && yarn prisma:g`.

  

## Agent-Specific Instructions

- Primary context: consult [CLAUDE.md](CLAUDE.md) for architecture, environment setup, PM2/Docker commands, and service topology.

- Use this file for contribution rules; defer to CLAUDE.md for how to run/build services locally.

  

## PM2 App Names (--only)

- backend: NestJS main app (`dev:smile`)

- auth: Auth service

- backoffice: Backoffice backend

- tracker: Tracker service

- wellness: Wellness service

- broker: Broker service

- frontend: Legacy Next.js app

- portal: Customer portal (11500)

- backoffice-x: Admin UI (11400)

- enjoy: Micro-site (Next 15)

  

Example: `yarn local --only backend,auth,backoffice,backoffice-x`