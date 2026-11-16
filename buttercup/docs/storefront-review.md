# Buttercup whole-storefront review

Every customer page was checked against the original Aurelle structures. Page families now have their own Buttercup compositions, while form IDs, data, controls and customer flows are preserved.

| Page family | Buttercup composition |
|---|---|
| Homepage | Three-panel photographic banner, tailored strip, story/contact imagery, category links and Mellow product collections |
| Shop/category/brand/search/trending/best sellers | Photographic masthead, horizontal dropdown refinement bar, full-width shelves and new card captions |
| Product | Full-width title/price masthead, side thumbnail rail, separate purchase area, descriptive/review content below, paired collection rows |
| Cart | Full-width selection sheet, quantity/subtotal columns, discount section and bottom order-total area |
| Wishlist | Editorial saved-items masthead and dedicated saved collection |
| Checkout | Numbered form chapters below an expandable order review, without the old boxed form/sidebar composition |
| Payment handoffs | Photography and a transaction workspace with return navigation |
| Payment results | Horizontal status ribbon, editorial message, photographic transaction detail |
| Confirmation | Thank-you photo composition with an order receipt below |
| Tracking | Photographic tracking banner, inline reference search and receipt-style results |
| About | Story/photo opening, editorial letter and full-width table imagery |
| Contact | Contact information bar, photo and unboxed note form |
| FAQ | Numbered questions alongside a photographic help panel |
| Policy/custom pages | Contents rail, numbered sections, rich media and tables |
| 404 | Oversized error number, photography and product search |
| Customer accounts | Photographic authentication/recovery, horizontal navigation, overview, photo order history, receipt details and numbered settings |
| Shared UI | New card captions, centered contact footer with horizontal link groups, wide search dialog and styled bag preview |

`structure-audit.json` maps all 40 pages to their new composition markers and confirms absence of inherited main-layout wrappers. `qa-storefront-results.json` includes 34 desktop/mobile checks of representative populated states. `qa-account-results.json` covers all eight account pages at desktop/mobile widths. The other QA reports cover the buying/customer flows and dialogs. Screenshots named `review-<page>-1440.png` and `review-<page>-375.png` show the reviewed surfaces.

This is a static design and browser-local verification record. Live Mellow tenant data, identity and payment integrations remain separate work as explained in mellow-parity.md.
