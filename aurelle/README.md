# Aurelle — Mellow beauty storefront theme

A customer-facing storefront theme only, with no merchant dashboard, store editor, or merchant customization controls.

A plain HTML, CSS and JavaScript design package inspired by the supplied Wix **Beauty Store (Bold)** reference. The theme lives in `/Users/Wills/Desktop/Ogaranya Projects/mello-theme ideas/aurelle`.

## Preview

Run from this folder:

```sh
python3 -m http.server 8766 --bind 127.0.0.1
```

Open **http://127.0.0.1:8766/**. Use an HTTP server so external SVG icons and browser storage behave consistently. No build or dependency installation is required. All runtime assets are local.

## Files

- `index.html`: complete homepage with banners, products, categories, promotional areas, brands and optional editorial/newsletter areas.
- `shop.html`, `category.html`, `brand.html`, `search.html`, `trending.html`, `best-sales.html`: collection contexts sharing filter/sort/pagination logic.
- `product.html?id=solar-mist`: product gallery, variants, paid options, stock, reviews, related items and affiliate/digital branches.
- `cart.html`, `wishlist.html`, `checkout.html`, `thanks.html`, `tracking.html`: buying journey and guest tracking.
- `account/`: login, registration, password recovery/reset, dashboard, orders, order details and profile/password settings.
- `payment/`: Paystack, Squad, Stripe, Razorpay, transfer handoffs and success/failure/pending layouts.
- `pages/`: merchant story, support/contact, FAQ, policies, accessibility, flexible custom content, customer information pages.
- `css/theme.css`: shared tokens, layout, responsive states, RTL direction and reduced-motion/print styles.
- `js/data.js`: sample tenant configuration, currency, catalog and reviews.
- `js/store.js`: shared shell, drawers/dialogs, product cards, browser-local cart/wishlist and totals.
- Other `js/` files own home, discovery, product, cart, checkout, payments and account behavior.
- `docs/coverage.md`: scope, Mellow integration map, conditional states and explicit limits.
- `docs/qa-results.json`: browser check results; screenshots are included beside it.

## Review scenarios

- Product options: `product.html?id=solar-mist`; sold out: `product.html?id=body-shield`; affiliate: `product.html?id=beauty-tool`; digital: `product.html?id=ritual-guide`.
- Coupon: `GLOW10`; expired-code demonstration: `EXPIRED`; any other code shows invalid feedback.
- Search with no results: `search.html?src=no-such-product`.
- Listing failure/loading previews: `shop.html?state=error`, `shop.html?state=loading`.
- Empty orders: `account/orders.html?state=empty`; invalid reset: `account/reset-password.html?state=expired`.
- Tracking example: `AUR-DEMO-001`; any unknown reference demonstrates not-found feedback.
- Add a product to the bag, then complete checkout. Provider pages offer explicit simulated success/failure buttons. A successful simulation clears the bag; failure retains it.
- Preview account forms store only name/email/phone. They never store passwords, send reset emails, verify identity or create real accounts.
- The language control in the footer previews RTL layout direction. Text translation is supplied by Mellow during integration.

## Backend handoff

This is the requested **static design package**, not an activated Laravel theme. Replace sample data and local state with Mellow tenant data, authenticated customer endpoints, stock validation, order creation and gateway handlers. Preserve server-side tenant isolation, CSRF/auth validation and payment verification. Provider-owned card forms must be mounted by the official gateway integration; the preview collects no payment credentials.

The demo currency, tax, stock and shipping rules are sample values and must be replaced by the merchant configuration. Product photographs/catalog copy demonstrate capacity rather than reproducing the live Starshop catalog. Merchant policy copy is labeled sample content.

The optional newsletter/editorial sections and additional payment-result screens are design additions; they can be hidden. Missing optional tenant content should hide the relevant section. See the coverage document before implementation to avoid treating optional additions as existing Mellow behavior.

## Asset provenance

- Reference and imagery: [Wix Beauty Store (Bold)](https://www.wix.com/website-template/view/html/wh-1046) / [demo](https://www.wix.com/demone2/wh-beautystore). Bundled for this requested design reference. Replace with merchant-owned or appropriately licensed imagery for production; this package does not grant rights to Wix template assets.
- Typography: DM Sans by Colophon Foundry, SIL Open Font License, sourced from Google Fonts. Bundled locally.
- Icons: Tabler Icons 3.36.0, MIT, bundled as `images/icons.svg`.
- The Aurelle wordmark is live text; no Wix/dreama logo is used.

## Reset the demonstration

In browser developer tools, remove localStorage keys beginning with `aurelle.`. The static preview does not write to Mellow or contact a live payment service.
