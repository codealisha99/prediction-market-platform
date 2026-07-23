# Prediction Market Platform Deployment

## Production Targets

Recommended setup:

- **Frontend**: Vercel or Netlify as a static Vite app.
- **Backend**: Render, Railway, Fly.io, or Vercel Functions after adapting the Express entrypoint if needed.
- **Database**: Supabase PostgreSQL, Neon PostgreSQL, or another managed PostgreSQL provider.
- **Auth/Data service**: Supabase, based on the current package usage.

Before using Vercel CLI, upgrade it:

```bash
npm i -g vercel@latest
```

## Required Environment Variables

Backend:

```bash
DATABASE_URL=
SUPABASE_SECRET_KEY=
```

Frontend variables should be added once the frontend has public Supabase or API URL configuration. If exposed to the browser, use non-secret public keys only.

Recommended frontend variables:

```bash
VITE_API_URL=
VITE_SUPABASE_URL=
VITE_SUPABASE_ANON_KEY=
```

## Local Setup

1. Install Bun.

2. Install dependencies from the repo root:

```bash
bun install
```

3. Configure database env:

```bash
DATABASE_URL="postgresql://USER:PASSWORD@HOST:5432/DB?schema=public"
SUPABASE_SECRET_KEY="YOUR_SUPABASE_SECRET_KEY"
```

4. Generate Prisma client:

```bash
cd packages/db
bunx prisma generate
```

5. Run migrations:

```bash
bunx prisma migrate dev
```

6. Start the workspace:

```bash
bun run dev
```

## Supabase Setup

1. Create a Supabase project.
2. Copy the project URL and anon key for frontend use if needed.
3. Copy the service role key only for backend use.
4. Set `SUPABASE_SECRET_KEY` on the backend host.
5. Never expose the service role key in Vite frontend variables.

The current backend references a Supabase URL directly in code. Before production, move that URL to an environment variable:

```bash
SUPABASE_URL=
```

## Database Deployment

1. Create a PostgreSQL database.
2. Set `DATABASE_URL` in backend and migration environments.
3. Run migrations from `packages/db`:

```bash
bunx prisma migrate deploy
```

4. Generate the Prisma client during build or install:

```bash
bunx prisma generate
```

## Frontend Deployment On Vercel

1. Import the repository.
2. Set root directory to `apps/frontend`.
3. Install command:

```bash
bun install
```

4. Build command:

```bash
bun run build
```

5. Output directory:

```text
dist
```

6. Add public frontend env vars:

```bash
VITE_API_URL=
VITE_SUPABASE_URL=
VITE_SUPABASE_ANON_KEY=
```

## Backend Deployment

For Render or Railway:

- Root directory: `apps/backend`
- Install command: `bun install`
- Start command: `bun index.ts`
- Add `DATABASE_URL` and `SUPABASE_SECRET_KEY`

If deploying as serverless functions, refactor the Express server into request handlers and document the route mapping.

## External Services And API Keys

- Supabase is used by the current backend and frontend packages.
- `SUPABASE_SECRET_KEY` must stay backend-only.
- PostgreSQL is required for the Prisma database package.
- Neon can be used as the PostgreSQL provider if Supabase PostgreSQL is not used.
- Anthropic and OpenAI keys are not used by the current code.

## Deployment Checklist

- `bun run build` passes from the root.
- `bun run check-types` passes.
- Prisma migrations are deployed.
- Supabase service role key is backend-only.
- Frontend points to the production API URL.
- CORS allows the production frontend domain only.
- Market create, order submit, balance, and position flows work after deployment.
