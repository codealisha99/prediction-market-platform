# Prediction Market Platform Roadmap

## Immediate Polish

- Move hardcoded Supabase URL into an environment variable.
- Add `.env.example` files for root, frontend, backend, and database package.
- Add clear loading, empty, and error states for markets, positions, and order history.
- Add frontend form validation for order amount, market selection, and invalid balance.
- Add backend validation errors that map cleanly to frontend messages.
- Add a clear README that explains how to run each workspace app.

## Product Features

- Add market creation with title, description, outcomes, close date, and image.
- Add settlement flow for resolved markets.
- Add clear rules for market status: draft, open, closed, resolved, cancelled.
- Add user portfolio page with open positions and PnL.
- Add transaction or trade history per market.
- Add admin or creator controls for resolving markets.
- Add liquidity and price charts.
- Add watchlist and featured markets.

## Trading and Data Integrity

- Define the exact order matching or pricing model.
- Add server-side checks for balance and position limits.
- Add idempotency keys for order submission.
- Wrap balance, order, and position updates in database transactions.
- Add audit logs for market resolution and user trades.
- Add indexes for market, user, order, and position queries.

## Production Readiness

- Add tests for backend validators and market actions.
- Add tests for database transaction behavior.
- Add frontend tests for order form and market detail flows.
- Add CI for build, lint, typecheck, and Prisma validation.
- Add rate limits for order submission and market creation.
- Add structured logs for API requests and failed trades.
- Add database backups and migration rollback notes.

## UI/UX Improvements

- Make market cards easy to scan with probability, volume, close date, and category.
- Add a guided order ticket with review step before submit.
- Show balance impact before placing an order.
- Use clear status badges for market state.
- Add charts for price movement and volume.
- Improve mobile order placement so it feels native and fast.

## Step-by-Step Priority

1. Lock env configuration and remove hardcoded service values.
2. Define the market and order rules in code and docs.
3. Add transaction-safe backend order handling.
4. Add settlement and admin flows.
5. Improve market detail and order UI.
6. Add tests and CI.
7. Add monitoring, logs, and rate limits.
