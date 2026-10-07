# PROJECT RULES (read before every task)

## Stack

Next.js (App Router) + TypeScript + Tailwind + Supabase + pnpm monorepo (Turborepo).

## Structure

- apps/storefront, apps/seller, apps/admin = screens only
- packages/modules/<name>/ = business logic
  (service, repository, types, validation, cache files)
- packages/db, auth, cache, ui, config = shared engine
- supabase/migrations = every database change

## Hard rules

1. Apps NEVER import from other apps.
2. Packages NEVER import from apps.
3. Pages only display. Logic goes in features/ or packages/modules/.
4. Only \*.repository.ts files talk to the database.
5. Admin-only actions live only in apps/admin and check the role first.
6. NEVER cache stock, payments, or orders.
7. Every table gets Row Level Security (RLS) in the same migration.
8. Never edit an old migration. Add a new numbered file.
9. Secrets only in .env files. Never in code. Never commit .env.

## How to work

- Show a plan first and wait for approval.
- One small task at a time.
- After each task, explain in plain language what changed and which files.
- Use TypeScript. No `any` type.
