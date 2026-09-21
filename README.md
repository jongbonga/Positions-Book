# Positions
A single static page that reads two wallets and prices them as one book: Kamino vaults on Solana and Beefy concentrated-liquidity vaults on BNB Chain.

Everything runs in the browser. No backend, no build step, no dependencies - one `index.html`.

## What it reads

- **Kamino** - `api.kamino.finance` for per-vault user metrics (shares, value, token amount) and vault APY.
- **Beefy** - vault, reward-pool and CLM registries plus LP prices from `api.beefy.finance`, then live share balances, pool composition and range bounds read straight from the contracts through a public BNB Chain RPC.

Nothing is cached: a reload re-reads both chains.

## What it stores

Your two wallet addresses and your per-position cost basis live in this browser's `localStorage` and nowhere else. They are not in this repository, and the page has no server to send them to. Cost basis cannot be derived from any public API, so gain columns stay blank until you enter it under Settings.

## Use

Open the page and paste a Solana address, a BNB Chain address, or both. Settings holds the cost basis fields, an extra-vault list for Kamino, a Beefy rescan and JSON backup/restore.

## Currency

Values are shown in USD, EUR or ZAR — pick one from the dropdown next to Refresh. Conversion rates come from `api.frankfurter.dev` (ECB reference rates, refreshed on every page load); cost basis is still always entered and stored in USD. EUR/ZAR are disabled if that fetch fails — a warning banner explains why and Refresh retries it.

Read-only position tracking built on public data. Not investment advice.
