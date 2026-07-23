# Prediction Market Platform

A full-stack prediction market platform for browsing markets, placing orders, tracking positions, and managing user balances.

![Bun](https://img.shields.io/badge/Bun-000000)
![Turborepo](https://img.shields.io/badge/Turborepo-EF4444)
![React](https://img.shields.io/badge/React-19-61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E)
![Prisma](https://img.shields.io/badge/Prisma-2D3748)

## Project Preview

This project is organized as a Bun and Turborepo monorepo with a Vite frontend, Express backend, shared UI package, and Prisma database package.

Screenshots can be added in a future `screenshots/` folder:

- Market list
- Market detail and order form
- Positions and order history

## Features

- Market browsing and market detail screens.
- Order form for trading outcomes.
- User balances and positions.
- Order history.
- Split and merge market actions.
- Express backend service.
- Shared Prisma database package.
- Supabase integration for backend and frontend data needs.
- Shared UI, TypeScript, and ESLint packages.

## Tech Stack

- Bun
- Turborepo
- React
- Vite
- TypeScript
- Express
- Supabase
- Prisma
- PostgreSQL
- Zod

## Repository Structure

```text
apps/frontend/       Vite React frontend
apps/backend/        Express backend service
packages/db/         Prisma schema, migrations, and database client
packages/ui/         Shared UI components
packages/eslint-config/
packages/typescript-config/
```

## Getting Started

Install dependencies:

```bash
bun install
```

Set required environment variables:

```bash
DATABASE_URL=
SUPABASE_SECRET_KEY=
```

Generate Prisma client:

```bash
cd packages/db
bunx prisma generate
```

Run the full workspace:

```bash
bun run dev
```

Build all apps and packages:

```bash
bun run build
```

## Documentation

- [Project Overview](./OVERVIEW.md)
- [Deployment Guide](./DEPLOYMENT.md)
- [Improvement Roadmap](./ROADMAP.md)

## Status

The project has the main frontend screens, backend structure, shared packages, and database foundation in place. The next major step is hardening order matching, settlement, auth rules, and production observability.
