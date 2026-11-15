# ShopLedger

## Stack

- Node.js CommonJS application.
- Express 4 with `body-parser` for the HTTP API.
- Vanilla HTML, CSS, and browser JavaScript in `public/` for the UI.
- JSON-file persistence in `data/db.json`, accessed through `lib/store.js`.
- The package manifest is `package.json`; dependency versions are pinned in `package-lock.json`.

## Module map

- `server.js` creates the Express app, serves `public/`, mounts the API routers, and renders printable invoices.
- `routes/` defines HTTP endpoints for products and coupons, orders, customers and settlements, reports, pricing preview, and admin export.
- `lib/store.js` reads and writes `data/db.json` and appends audit entries.
- `lib/inventory.js` checks, reserves, releases, and summarizes stock.
- `lib/orders.js` creates, finds, lists, and cancels orders.
- `lib/pricing.js`, `lib/tax.js`, and `lib/coupons.js` calculate totals, GST, and discounts.
- `lib/ledger.js` handles customer balances, Khata charges, reversals, and settlements.
- `lib/reports.js` builds dashboard and GST-reconciliation data; `lib/invoice.js` builds printable invoice HTML.
- `lib/dates.js` provides date and fiscal-year helpers.
- `config.js` contains the port, shop details, tax slabs, inventory defaults, and coupon configuration.
- `public/` contains the browser UI; `docs/` contains the architecture diagram.

## Commands

```text
npm install       Install dependencies from package.json/package-lock.json
npm start         Start the server on PORT or http://localhost:3000
npm test          Currently exits with "Error: no test specified"
node server.js    Start the server directly
```

## Working rules

- Write characterization tests before changing behaviour.
- Change only the module the ticket is about.
- Tests never touch `data/db.json`.
- Add no dependencies.
