# Tindahan ni Aling Nena — Sari-Sari Store POS System

A simple, browser-based Point of Sale (POS) application for a Philippine sari-sari store. Built with vanilla HTML, CSS, and JavaScript — no backend, no database, no build step. All transaction data lives in memory for the current session.

## Project Structure

```
sari-sari-pos/
├── index.html        Main HTML page (structure/layout)
├── css/
│   └── style.css     All styling (fonts, colors, layout, receipt design)
├── js/
│   ├── data.js        Product catalog (50 grocery items)
│   └── app.js         Application logic (cart, checkout, reports)
└── README.md          This file
```

## How to Run

No installation needed.

1. Unzip the project folder.
2. Double-click `index.html` (or right-click → Open With → your browser).

That's it — the app runs entirely client-side.

> Tip: for the best experience, serve it from a local server instead of opening the file directly (some browsers restrict local file access for certain features). For example, from inside the project folder:
> ```
> python3 -m http.server 8000
> ```
> then visit `http://localhost:8000` in your browser.

## Features

**Bilihan (POS) tab**
- Browse and search the 50-item product catalog
- Sort by price or name
- Add items to cart with adjustable quantities
- Automatic 10% discount on orders over ₱1,000
- Enter payment amount and see live change calculation
- Optional customer name field
- Printable-style receipt shown on checkout

**Mga Transaksyon (Transactions) tab**
- Full log of every completed transaction: ID, date/time, customer, items, subtotal, discount, total, amount paid, and change

**Ulat (Reports) tab**
- Total sales for the session
- Number of transactions and average sale amount
- Best-selling product
- Ranked table of all products by units sold and revenue

## Data Model

Each transaction recorded during the session includes:

| Field | Description |
|---|---|
| `transaction_id` | Unique ID (e.g. `TXN-1001`) |
| `date` | Timestamp of the transaction |
| `customer` | Customer name, or "Walk-in" |
| `items` | Array of `{ product_id, product_name, product_price, qty, subtotal }` |
| `subtotal` | Sum of all line items before discount |
| `discount` | Discount amount applied (if any) |
| `total` | Final amount due |
| `amount_paid` | Payment received from customer |
| `change` | Change returned |

## Customizing

- **Add/edit products:** edit the `groceryItems` array in `js/data.js`.
- **Change the discount rule:** edit `DISCOUNT_THRESHOLD` and `DISCOUNT_RATE` at the top of `js/app.js`.
- **Restyle:** all colors and fonts are defined as CSS variables at the top of `css/style.css` (`:root { ... }`).

## Notes

- Data resets when the page is refreshed or closed (in-memory only, as specified — no database).
- Fonts (Baloo 2, Public Sans, JetBrains Mono) load from Google Fonts, so an internet connection is needed for the intended look. Without one, the app still functions using fallback system fonts.
