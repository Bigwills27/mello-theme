# Buttercup — a Mellow cake-shop storefront

A complete static customer storefront design inspired by Wix Cake Shop template 2214 (Hanna Bakes). Buttercup uses white space, blush panels, lavender accents, delicate rules and cake photography. It lives beside Aurelle in its own independent folder.

**Scope:** customers only: browsing, products, buying, payment states, customer accounts and order tracking. No merchant dashboard, store editor, owner modal or administrative controls.

## Preview

From this folder:

```sh
python3 -m http.server 8767 --bind 127.0.0.1
```

Open http://127.0.0.1:8767/. Use HTTP for SVG icons and consistent browser storage. No installation, build step or external runtime assets are required.

## Package

- 40 HTML pages, with CSS in `css/`, JavaScript in `js/` and local photography/icons/font in `images/`.
- Root pages cover home, shop, category, brand, search, trending, best sellers, product, cart, wishlist, checkout, confirmation, tracking and 404.
- `account/`: distinct photographic sign-in/registration and recovery layouts; horizontal customer navigation; editorial overview, photo-based paginated order history, receipt-style details and numbered profile sections.
- `css/storefront.css`: dedicated Buttercup collection, product, bag, checkout, payment, confirmation, tracking, content and shared footer compositions.
- `css/account.css`: Buttercup’s dedicated customer layouts; these do not use Aurelle’s centered forms, account sidebar, stats cards or order table.
- `payment/`: Stripe, Paystack, Squad, Razorpay, transfer and generic external-provider handoffs plus success/failure/pending layouts.
- `pages/`: story, contact, FAQ, shipping, returns, terms, privacy, accessibility and flexible rich content.
- `DESIGN.md`: approved visual/functional direction.
- `docs/checklist-ledger.md` and `.json`: all 830 entries from the supplied theme.md, preserving source line numbers and reference-audit findings, with implementation dispositions.
- `docs/mellow-parity.md`: the actual Mellow capabilities, files and verification boundaries.
- `docs/qa-results.json`, `qa-edge-results.json`, screenshots and `verification.md`: browser/static review evidence.

## Useful review paths

- `product.html?id=rose-garden`: required single-choice finish, optional multiple decorations, variant price/image/stock and unavailable flavour.
- `product.html?id=confetti-dream`: required multiple-choice decorations and percentage pricing.
- `product.html?id=vanilla-cloud`: another configurable attribute group, independent of flavour/size.
- `product.html?id=golden-wedding`: sold out.
- `product.html?id=baking-guide`: digital product.
- `product.html?id=cake-stand`: affiliate product.
- `product.html?reviews=empty`: no reviews. Reviews and orders have pagination.
- `shop.html?state=loading`, `shop.html?state=error`: request states; retry restores the sample collection.
- `search.html?src=missing-product`: no results.
- `index.html?state=empty`, `?state=error`, `?state=loading`, `?state=no-banners`, `?state=no-categories`, `?state=no-brands`: section and optional-content states.
- `account/orders.html?state=empty` or `?state=error`; `account/reset-password.html?state=expired`; `account/login.html?state=error`.
- Coupon `BAKE10` demonstrates 10% discount. `EXPIRED` demonstrates expired-code feedback; other unknown codes show an error.
- Tracking reference `BTC-DEMO-001` shows a paid/completed sample with an eligible digital download. Unknown references show not-found.

## Tenant and product data

`js/data.js` separates store configuration from layout: name/logo/favicon, colours, nested navigation, contact/social details, locale/currency, enabled gateways and optional homepage sections. Product examples show category/brand, prices, media, stock, variants, arbitrary labelled attributes and single/multiple paid options. Flavour and serving-size labels are demonstrations; products are not restricted to cakes by the underlying layout.

`js/store.js` handles shared shell/dialogs, cart/wishlist, option pricing, stock limits and totals. `product.js`, `catalog.js`, `checkout.js`, `payment.js`, `account.js` and `home.js` own their respective surfaces. Browser keys begin with `buttercup.` and do not share Aurelle state.

## Static preview versus Mellow integration

This package demonstrates designs and browser-local flows. It does not activate a Laravel theme or connect to live Mellow endpoints. Customer profiles/orders/reviews stay in this browser. Passwords are not saved or submitted. Payment buttons explicitly simulate provider outcomes and collect no payment credentials. Contact/newsletter forms do not send messages.

Replace demo data/state with tenant endpoints, CSRF/auth/session handling, authoritative stock/pricing, delivery rules, order creation, review/order pagination, payment verification, email/WhatsApp receipts and authorized download URLs. Shipping exemptions come from customer configuration; there is no customer-facing fee waiver switch. The actual payment methods are supplied by the enabled gateway registry, including a generic external handoff for additional providers.

Sample catalog prices, tax/delivery rules, ingredients/diet labels and policy copy need real store content. Optional checklist wishes beyond existing Mellow support have explicit dispositions in the ledger; they are not represented as finished backend features.

## Assets

- Photography/reference: [Wix Cake Shop 2214](https://www.wix.com/website-template/view/html/2214) and its [Hanna Bakes demo](https://www.wix.com/demone2/celebrations-cakes). Included for this requested visual reference. Replace with merchant-owned or licensed imagery for production; this package grants no rights to Wix assets.
- DM Sans: locally hosted, SIL Open Font License, see `docs/licenses/DM-Sans-OFL.txt`.
- Tabler icons: local sprite, MIT, see `docs/licenses/Tabler-MIT.txt`.
- The Buttercup wordmark is live text and uses the system serif stack. No Hanna Bakes/Wix logo is used.

To reset the preview, remove localStorage keys starting with `buttercup.` in browser developer tools.

## Whole-storefront layout review

Every customer page was reviewed against Aurelle. Buttercup uses a horizontal collection filter bar, full-width bag sheet and bottom totals, numbered checkout with expandable order review, photographic payment/result layouts, a new confirmation receipt, tracking banner, editorial contact/story pages, a contents rail for rich/policy pages and numbered FAQs. Product title/price sit above a thumbnail-rail gallery and purchase area, with details below; the shared footer is centred with horizontal link groups. See docs/structure-audit.json and the review-<page>-1440.png / review-<page>-375.png screenshots.
