# Mellow storefront parity and handoff

The actual customer-facing implementation is mapped below against the code-verified appendix of the supplied theme.md. This is a static design package. “Implemented” describes HTML/CSS and browser-local interaction; live tenant/auth/payment/database operations remain integration work.

## Global shell

Implemented in `js/store.js`, `js/data.js`, `css/theme.css`: configurable store wordmark/logo/favicon, brand colours, currency format, nested menu data, search/results link, category links, customer account, cart/wishlist counters, cart preview with items/subtotal/total, mobile drawer, contact details/hours/socials/policies, back-to-top, locale direction. Native dialogs provide close/Escape/focus behavior. Image errors have a local fallback. Customer account pages are retained; merchant editing/customization is excluded.

## Homepage data surfaces

`index.html` and `js/home.js`: reference three-column hero with banner controls, message strip, store story/contact photos, categories, featured/trending/latest/best-selling/offerable/random products, category and brand product collections, featured brands, promotions, optional newsletter/social imagery. Category tabs filter the featured collection. Optional section flags and query fixtures cover missing banners/categories/brands and product collection loading/error/empty/retry. Real collection JSON responses replace sample arrays.

## Listing contexts

`shop.html`, `category.html`, `brand.html`, `search.html`, `trending.html`, `best-sales.html`, `js/catalog.js`: preserve shared listing semantics with photographic context mastheads, horizontal category/brand/price and data-driven attribute filters, stock/sale/rating preferences, active filter removal, sort, page size, pagination and grid/list view. Mobile filters expand with a close toggle. An expanded panel serves the existing Mellow mobile filtering function; this is not styled as a full-screen drawer. Category/brand metadata can be expanded with tenant data; the current Mellow code itself reuses the shop view.

## Product/media/options

`product.html`, `js/product.js`, `js/store.js`: product media gallery, thumbnails, swipe, lightbox, price/regular price, stock/SKU, categories/brand, descriptions, product information, delivery/return links, related products, previous/next links, share, wishlist and quantity-limited add to cart. Arbitrary product `attributeGroups` and single/multiple `options` support labels, required validation, disabled options, fixed and percentage additions, optional packaging, reset and variant price/media/stock. Affiliate products open the configured partner; digital products follow no-shipping delivery. Recipe/ingredient/allergen copy is a tenant-content concern, not supplied medical or dietary advice.

Reviews use stored sample and preview submissions, authenticated-profile prompt/read-only name/email, stars/comment, pagination and empty state. Actual review moderation, server validation and throttling come from Mellow. Product video, review images/Q&A, comparison and quick view are optional unsupported additions rather than silently claimed parity.

## Bag and wishlist

`cart.html`, `wishlist.html`, `js/cart.js`, `js/store.js`: session-like browser storage, line items and selected option labels, unit/line amounts, quantity limits, removal, clear confirmation, empty state, coupon success/invalid/expired/remove, tax/discount/total, continue shopping and checkout. Quantity editing is an intentional design enhancement over Mellow’s original cart quantity display. Wishlist uses product-level entries like the audited platform.

## Checkout and payment

`checkout.html`, `js/checkout.js`: returning-customer prompt, guest/contact fields, optional profile creation/password, delivery location-dependent methods/fees/address, pickup/digital no-address branches, configured customer fee exemption, notes, item/options summary, tax/discount/shipping/total, legal consent, cart link, enabled-method selection and disabled submission/handoff state. Fields differ by store type. No customer can enable free shipping using an admin/debug checkbox.

`payment/*.html` and `js/payment.js`: named provider handoff areas plus external-provider fallback, no-order state, simulated success/failure/pending designs. Successful simulation clears the bag; failure retains it and checkout can display error feedback. Provider-owned fields/redirects and transaction verification must be mounted by the live integration. Mellow’s normal success→thanks and failure→checkout contracts are retained as supported return patterns; standalone result designs are additional surfaces.

`thanks.html` renders customer/reference, payment/delivery details, purchased items and totals, order link, continue shopping and support. Actual confirmation emails and WhatsApp order-receipt redirects are server workflows and are not simulated as delivered messages.

## Customer account and tracking

`account/*.html`, `tracking.html`, `js/account.js`, `css/account.css`: login/register, native/inline validation, password mismatch and show/hide controls, remember-me surface, reset request/expired token, customer dashboard/settings/logout, paginated photo-based order history, status badges/details/timeline, conditional downloads for paid completed orders, invoice print/PDF, guest reference success/miss and unknown order. Preview identities are explicitly not real authentication. Actual password-reset pages currently live outside tenant theme folders in Mellow, so the integration must choose their visual shell.

## Custom content and errors

`pages/*.html`, `404.html`: store story/contact/FAQ/policies, rich text, images, table, accordion, CTA, long content and page-not-found. Merchant-written content is displayed to customers without any merchant editor UI. Product/order/search/collection empty/error conditions also have their own display surfaces.

## Explicit limits and alternatives

- All 830 source checklist entries are recorded; this includes duplicates and evaluation forms, not 830 distinct live Mellow features.
- Aspirational checklist items without verified Mellow support have conditional/optional dispositions. Backend-dependent behavior needs integration verification; a static design cannot prove live identity, payment or file authorization.
- Price filtering uses min/max fields; no draggable price slider. Mobile filters use an expandable panel with a close toggle. Pagination is used instead of infinite-scroll/load-more for catalog/reviews/orders. The no-video/no-autocomplete/no-quick-view choices follow the source audit.
- Separate billing/shipping identities, address books, alternate phone fields, express wallets, chat, advanced recommendation bundles, social login, compare, product video, review images/Q&A, blog/app downloads, cookie consent and dark mode were not verified as Mellow storefront behavior and require explicit scope if desired.
- Real merchant fixtures must verify long names/images/prices, optional missing fields, full option groups, locale translations and all live provider outcomes after integration.

## Account layout review

All eight customer account page structures were rebuilt for Buttercup. Authentication/recovery use photography paired with forms; customer navigation is horizontal; the overview combines latest-order and saved-cake imagery; order history uses photo rows; order details use an editorial receipt; and profile settings use numbered sections. Desktop/mobile screenshots for each account page and qa-account-results.json record this separate structural review.

## Full storefront layout audit

All 40 page compositions were checked for inherited main-layout wrappers. The remaining generic page-head, centred auth/success, left-sidebar listing, boxed rich-content and sticky summary layouts were replaced. New page families are implemented in css/storefront.css with their HTML and existing IDs/data hooks. Shared product cards, search dialog, bag preview and footer also received dedicated presentation. The Mellow fields/actions remain present; qa-storefront-results.json contains 34 desktop/mobile checks with populated buying and order states, and structure-audit.json records all 40 pages.
