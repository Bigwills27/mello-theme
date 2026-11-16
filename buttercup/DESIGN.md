# Buttercup storefront proposal

## Intent

Create the second standalone Mellow customer storefront theme, in its own folder beside Aurelle, inspired by Wix Cake Shop template 2214 (Hanna Bakes). Preserve Mellow's content and buying flows while changing layout, typography and positioning. No merchant/admin/editor interfaces.

## Visual system

White background, charcoal typography, blush hero panel, muted lavender accent, thin dark rules, generous gutters, delicate letterspaced serif wordmark, restrained sans body/headings. The desktop homepage opens with the reference's cake photograph / centered headline and CTA / cake photograph composition. On mobile, recompose into readable stacked content and use touch-sized controls. Retain editorial story/contact photography below; add Mellow category/product/brand collections in the same visual system.

## Files and surfaces

Plain HTML page content, CSS in css/, JavaScript in js/, local imagery in images/, handoff evidence in docs/. No runtime build dependencies. Catalog and tenant configuration remain separate from presentation. Browser-local interactions demonstrate the static package; actual Mellow endpoints handle authenticated/server operations.

- Root: index, shop, category, brand, search, trending, best-sales, product, cart, wishlist, checkout, thanks, tracking and 404 pages.
- account/: customer login, register, forgot-password, reset-password, dashboard, orders, order and settings.
- payment/: provider handoff designs (Stripe, Paystack, Squad, Razorpay, bank/external fallback), success, failed and processing states.
- pages/: story, contact, FAQ, shipping, returns, terms, privacy, accessibility and rich custom content.
- No theme-guide link, owner modal, merchant dashboard, store editor or customer-facing administrative controls.

## Behaviors

Shared navigation/search/cart/mobile dialogs, nested categories, wishlist/counters, dynamic catalog filtering and pagination, product gallery, arbitrary attribute/options groups, stock and purchase branches, coupon/cart feedback, conditional checkout, customer form validation and order views. Provide explicit loading, empty, success, failure, unknown-product/order, logged-out and invalid-option states. Support required multi/single-select add-ons and review/order pagination. Customer delivery-fee eligibility must come from configuration.

## Content compatibility

Store logo/name, colors, locale/RTL, currency, nested menus, optional banners, brands/categories, product media and descriptions, many options and long prices/names must fit. Digital/affiliate products and eligible order files need appropriate customer surfaces. For supported providers beyond the named examples, offer a generic external-payment handoff layout rather than hard-coding a closed provider list.

## Error handling and verification

No real credentials/payment data submitted by the static preview. Show backend validation/error placeholders clearly, avoid claiming live auth/payment works, and preserve the cart after failed payment. Verify local links/assets and JS syntax, then browser-check representative responsive widths and all material interaction/state branches. Map required code-audited Mellow capabilities to files and state evidence in the final ledger.

## Pre-build audit

See docs/reference-audit.md and docs/checklist-ledger.md. The reference alone does not cover Mellow. Approval of this proposal authorizes building the missing Mellow surfaces in the reference's design language.

## Customer account design

Authentication uses photo/form compositions with underline fields and separate recovery layouts. Signed-in pages use horizontal account navigation, an overview led by the latest order and saved-cake imagery, paginated photograph-based order rows, a split order receipt with delivery/payment information, and numbered profile/password sections. These are structural designs specific to Buttercup, not recoloured Aurelle templates.

## Storefront page compositions

Collections use a photographic masthead and horizontal dropdown filter bar above full-width product shelves. The bag is a full-width item sheet with discount and totals beneath. Checkout is a numbered form with an expandable order review above. Payment handoffs/results pair photography with transaction details. Confirmation and tracking have separate editorial compositions. Content pages use a contents rail and numbered sections, contact uses a photo/note layout, and FAQs use numbered questions. The product page separates the title/price masthead from its image and purchase sections and moves descriptive content below. All page families and the shared footer have dedicated Buttercup structures.
