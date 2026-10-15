# Kaziniya DDSS — Antigravity CLI Project Context

## Project Overview
Kaziniya Digital Drug Store Solution (DDSS) — a high-reliability pharmacy management, inventory, and clinical compliance system for community drug stores in Ethiopia.

## Tech Stack
- **Frontend**: React 19, TypeScript, TailwindCSS 4, Vite 6, Lucide Icons
- **Backend**: Express + Bun runtime, TypeScript
- **Database**: PostgreSQL (Docker) + SQLite (auth via Better Auth)
- **Auth**: Better Auth with RBAC (SUPER_ADMIN, STORE_OWNER, PHARMACIST, CUSTOMER)
- **Testing**: Bun test runner + Puppeteer for UI workflows
- **Build**: Vite (frontend) + esbuild (server bundle)

## Project Structure
- `src/` — React frontend (components, hooks, context, services, utils)
- `src/server/` — Express API routes and server logic
- `server.ts` — Entry point for Bun dev server
- `api/` — API definitions
- `tests/` — Test suites (coreWorkflow, browserUiWorkflow)
- `scripts/` — Utility/automation scripts
- `docker/` — Docker configs for PostgreSQL
- `mobile/` — Mobile-responsive views
- `docs/` + `documentation/` — Project documentation

## Key Commands (always use Bun, not npm)
- Dev server: `bun server.ts` (run manually in a separate terminal)
- Build: `bun run build`
- Tests: `bun test`
- Core workflow tests: `bun test tests/coreWorkflow.test.ts`
- UI tests: `bun test tests/browserUiWorkflow.test.ts`
- DB up: `docker compose up -d`
- DB down: `docker compose down`
- Lint (type-check): `bun run lint`

## User Roles
1. **SUPER_ADMIN** — System governance, EFDA regulatory oversight, multi-store federation
2. **STORE_OWNER** — Business metrics, revenue, staff, purchase orders, compliance
3. **PHARMACIST** — Prescription dispensing, batch tracking, FEFO stock handling
4. **CUSTOMER** — Product lookup, prescription upload, store locator

## Core Business Logic
- **FEFO** (First-Expired, First-Out): Always prioritize batches by earliest expiration date
- **Batch tracking**: Every drug unit must be traceable to its batch and expiry
- **EFDA compliance**: Ethiopian Food & Drug Authority licensing and traceability
- **Payment**: Telebirr, CBE POS, and cash

## Design Rules (CRITICAL — never violate)
- Color palette: Deep Emerald (`#047857`) and Medical Teal (`#0f766e`) — NO purple/neon/AI gradients
- Status badges: emerald=valid, amber=expiry warning, rose=expired/critical, sky=cold-chain
- NO gray text on colored backgrounds (use `text-emerald-950` not `text-slate-900` on colored bg)
- NO bounce/elastic animations (`animate-bounce` is forbidden) — use `ease-out` smooth transitions
- NO decorative border accents on rounded cards — use `border border-slate-200` only
- Typography: tabular `font-mono` for batch numbers, prices, EFDA IDs

## Durable Constraints
- Clinical safety and stock count accuracy must NEVER be compromised
- High-contrast UI suitable for busy dispensary counter environments
- Offline-resilient, low-latency POS counter workflows

## Windows / PowerShell Rules
- Use `pwsh -c <command>` for all terminal commands
- Package manager is **Bun** — never substitute npm/yarn
- Never run dev servers autonomously — ask the user to run them in a separate terminal
- Paths use backslash `\`
