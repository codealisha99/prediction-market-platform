# Prediction Market Platform Overview

## What This Project Does

Prediction Market Platform is a monorepo for creating markets, placing orders, tracking balances, viewing positions, and managing market outcomes. It uses a Vite React frontend, an Express backend, shared packages, and a Prisma-backed database package.

## Main Features

- Market list and market detail screens.
- Order form for trading market outcomes.
- User balance display.
- Position tracking.
- Order history.
- Split and merge style market actions.
- Backend API for market and order behavior.
- Supabase client usage for user-facing auth or data access.
- Shared database package for Prisma access.

## Technology Stack

- **Bun**: Package manager and runtime target for the workspace.
- **Turborepo**: Monorepo task runner.
- **React 19**: Frontend UI.
- **Vite**: Frontend development and build tooling.
- **TypeScript**: Shared typing across apps and packages.
- **Express**: Backend HTTP service.
- **Supabase**: Client and secret-key integrations.
- **Prisma**: Database schema, migrations, and generated client in `packages/db`.
- **PostgreSQL**: Main database target.
- **Zod**: Runtime validation in the backend.
- **Shared packages**: UI, database, ESLint config, and TypeScript config.

## Workspace Structure

- `apps/frontend`: Vite React application.
- `apps/backend`: Express API service.
- `packages/db`: Prisma schema, migrations, and database client.
- `packages/ui`: Shared React UI components.
- `packages/eslint-config`: Shared lint config.
- `packages/typescript-config`: Shared TypeScript config.
- `turbo.json`: Workspace task pipeline.

## Data Flow

1. The frontend loads markets and user data through API calls.
2. Users submit orders or market actions from the frontend.
3. The backend validates request payloads.
4. Backend handlers use the shared database package to read and write market data.
5. Supabase is used where auth or external data access is required.
6. The frontend updates balances, positions, order history, and market details.

## Current State

The project has a good monorepo shape for a full prediction market product. The frontend has the core trading screens, the backend has API structure, and the database package contains schema and migrations. The main work left is tightening market settlement, auth rules, order matching, and production observability.
