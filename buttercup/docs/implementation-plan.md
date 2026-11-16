# Buttercup implementation plan

**Goal:** Build the approved cake-shop storefront and account for Mellow customer flows.
**Spec:** ../DESIGN.md and reference-audit.md.
**Architecture:** Standalone semantic HTML pages with shared CSS, plain JS modules and local assets. Reuse customer interaction patterns from Aurelle as independent Buttercup files; provide bakery-specific catalog content and a new visual layout. Browser state is namespaced buttercup. No merchant/admin UI.
**Execution:** Inline in this session, authorized by the user's “proceed please”.

- [x] Foundation: independent customer page files, local cake photography and fonts, shared shell, mobile/search/bag dialogs and footer.
- [x] Discovery: three-column reference hero, story/contact blocks, Mellow categories/brands/promotions/product collections, product cards, filters/sorting/pagination, missing/loading/error states.
- [x] Product: arbitrary labelled attributes and required single/multiple paid options, variant stock/price/media, gallery, quantity boundaries, wishlist/cart feedback, affiliate/digital branches, paginated reviews and related/latest products.
- [x] Buying: coupon/cart states, guest/customer checkout, address/location/shipping branches, configured customer shipping exemption, payments/handoffs/results and complete order confirmation.
- [x] Customer/content: customer auth/recovery/settings states, paginated orders/statuses/downloads/tracking, rich pages and policies; remove all merchant controls.
- [x] Verification/handoff: syntax, links/assets, responsive page coverage and meaningful interaction tests; update all 830 ledger dispositions with file/state evidence, preserve honest backend/optional boundaries, create matching ZIP.

- [x] Account correction: rebuilt all eight page structures and customer order rendering with dedicated css/account.css; checked desktop/mobile and retained interactions.

- [x] Whole-storefront correction: rebuilt remaining listing, buying, product, payment, tracking and content page-family structures, including shared cards/footer/dialogs; preserved IDs/data hooks and checked populated desktop/mobile states.
