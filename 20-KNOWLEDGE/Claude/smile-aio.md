
# CLAUDE.md

  

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

  

## Architecture Overview

  

Smile Solutions is a comprehensive insurance platform monorepo containing multiple applications:

  

### Core Components

- **backend/**: NestJS microservices architecture with 6 apps (auth, smile, backoffice, tracker, wellness, broker)

- **portal/**: Next.js 14.2.4 customer portal (port 11500)

- **backoffice-x/**: Next.js 14.0.4 admin interface (port 11400)

- **frontend/**: Next.js customer web app

- **micro-site/**: Specialized sites (enjoy, flood-risk, survey, web-campaign, find-agent)

- **database/**: MongoDB migrations with environment-specific configs

- **pm2/**: Process management configurations for different environments

  

### Technology Stack

- **Backend**: NestJS v9.4.0, TypeScript v5.0.4, MongoDB/Prisma/TypeORM

- **Frontend**: Next.js 13-15.x, React 18-19.x, TailwindCSS, Radix UI

- **Database**: MongoDB v6.1.0, Redis (caching), MS SQL Server

- **Auth**: JWT, Passport.js, bcrypt

- **Process Management**: PM2 with environment-specific configs

  

## Development Commands

  

### Environment Management

```bash

# Start local development (all services via PM2)

npm run local

  

# Environment-specific startup

yarn mss:sit # SIT environment

yarn mss:uat # UAT environment

yarn mss:prd # Production environment

  

# Process cleanup

yarn del:all # Delete all PM2 processes

yarn del:local # Delete local processes only

yarn del:sit # Delete SIT processes

yarn del:uat # Delete UAT processes

yarn del:prd # Delete PRD processes

```

  

### Docker Infrastructure

```bash

yarn docker # Start infrastructure (MongoDB, Redis, etc.)

yarn sonarqube # Start SonarQube

yarn close:docker # Stop all containers

```

  

### Backend Development (NestJS)

```bash

cd backend

  

# Build all services

npm run build

yarn build

  

# Development mode for specific services

yarn local --only smile # Main application

yarn local --only auth # Authentication service

yarn local --only backoffice # Admin backend

yarn local --only tracker # Tracking service

yarn local --only wellness # Wellness service

yarn local --only broker # Broker service

  

# Individual service development

npm run dev:smile

npm run dev:auth

npm run dev:backoffice

npm run dev:tracker

npm run dev:wellness

npm run dev:broker

  

# Testing and quality

npm run test # Run tests

npm run test:cov # Run with coverage

npm run lint # ESLint

npm run format # Prettier formatting

  

# Prisma

npm run prisma:g # Generate Prisma client

```

  

### Frontend Applications

  

#### Portal (Customer Portal - Port 11500)

```bash

cd portal

npm run dev # Local development

npm run dev:uat # UAT environment

npm run dev:production # Production environment

npm run build # Build for local

npm run build:uat # Build for UAT

npm run build:production # Build for production

npm run lint # Next.js linting

```

  

#### Backoffice-X (Admin Interface - Port 11400)

```bash

cd backoffice-x

npm run dev # Development server

npm run build # Production build

npm run lint # Linting

```

  

#### Frontend (Main Customer App)

```bash

cd frontend

npm run dev # Development

npm run build # Production build

```

  

### Database Operations

```bash

cd database

  

# Run migrations for environments

yarn migrate-mongo up -f mm.sit.config.js

yarn migrate-mongo up -f mm.uat.config.js

yarn migrate-mongo up -f mm.prd.config.js

```

  

### Micro-sites

```bash

# Flood Risk Assessment (React + TypeScript)

cd micro-site/flood-risk

npm run build

  

# Enjoy Platform (Next.js 15.1.3 + React 19)

cd micro-site/enjoy

npm run build

  

# Survey Platform (Vite)

cd micro-site/survey

npm run build

```

  

### Build System (Makefile)

```bash

# Install all dependencies

make install # or make i

  

# Build specific components

make build-step-backend-nestjs

make build-step-portal-nextjs-web

make build-step-backofficex-nextjs-web

make build-step-micro-site-enjoy-nextjs-web

  

# Clean dependencies

make clean

```

  

## Key Architectural Patterns

  

### Backend Services

- Microservices architecture with shared libraries

- JWT-based authentication across services

- Redis caching layer

- MongoDB + Prisma ORM

- OpenTelemetry observability

- Socket.IO for real-time features

  

### Frontend Architecture

- Next.js App Router pattern

- TanStack Query for state management

- Radix UI component library

- TailwindCSS utility-first styling

- React Hook Form + Zod validation

- TypeScript strict mode

  

### Environment Configuration

- Separate PM2 configs for local/SIT/UAT/PRD

- Environment-specific build commands

- Docker Compose for local infrastructure

- Environment variable management via env-cmd

  

## Development Workflow

  

1. Use PM2 configurations for multi-service development

2. Infrastructure services run via Docker Compose

3. Each frontend app has dedicated ports and build processes

4. Database migrations managed per environment

5. Code quality enforced via ESLint/Prettier across all projects

  

## Service Dependencies

- **MongoDB**: Primary database

- **Redis**: Caching and session storage

- **MinIO**: File storage (S3-compatible)

- **Firebase**: Mobile push notifications

- **External APIs**: Insurance systems, payment gateways

  

## Testing Strategy

- Jest for backend unit tests

- Next.js testing for frontend components

- E2E testing capabilities configured

- SonarQube integration for code quality