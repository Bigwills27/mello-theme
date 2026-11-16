# Buttercup: Wix 2214 versus Mellow storefront requirements

Reviewed 16 November 2026. Reference: https://www.wix.com/website-template/view/html/2214 and its Hanna Bakes demo at https://www.wix.com/demone2/celebrations-cakes.

## Finding

The reference is a suitable visual starting point with substantial Mellow storefront additions. It is not a complete Mellow theme as supplied. No claim that all functionality is present can be made from this preview. All checklist rows are recorded in checklist-ledger.md; the build must implement and verify the required additions before sign-off.

Scope is the storefront customers see, including their account, orders, settings and tracking. Merchant dashboards, store editors, customization modals, theme selectors and admin links are excluded by the user's explicit instruction.

## What was actually observed

- Desktop homepage: white canvas, charcoal text, thin horizontal rules, letterspaced serif wordmark, a three-column hero with cake photography either side of a pale blush text/CTA panel, lavender message strip, two large story/contact photo links, newsletter and social links.
- Navigation: Home, About, Menu, Order Online, Contact; login button and shopping-bag affordance.
- About page: chef/store story with long text and imagery.
- Menu page: Wedding Cakes and Celebration Cakes sections, named products and $70 prices. This is a Wix menu presentation, not proof of a Mellow product/variant/stock detail flow.
- Contact page: phone/email and name, email and message fields.
- Online ordering page: an empty-items message in the live browser. The HTML also contains delivery/pickup/dine-in and location/time/cart scaffolding, but not a populated flow that could be verified.
- Clicking the login trigger did not expose a usable login form in the inspected browser session. Login/register/account behavior remains unverified.
- Browser interactions used read-only navigation and opening controls. No contact/newsletter forms, orders or payments were submitted.

## Required additions for Mellow parity

| Area | Reference gap | Buttercup requirement |
|---|---|---|
| Global shell | No confirmed product search, wishlist, nested merchant menus, locale/RTL or full cart preview | Add search dialog/results, wishlist/counters, configurable menu/category nesting, responsive drawer, cart preview with subtotal/total, currency, supported locale and direction |
| Homepage collections | Reference mainly presents photos/story/contact | Add dynamic categories, featured brands, trending/latest/best sellers/offers/random/category/brand collections, promotional banners and section-level loading/empty/error states |
| Listing | No verified Mellow shop/filter/sort/pagination flow | Add shop, category, brand, search, trending and best-selling contexts; category/brand/price/dynamic attribute filters, result count, available sort options and pagination |
| Product detail | Menu listing does not establish purchasing options | Add gallery/lightbox, media fallback, SKU/price/discount/stock, dynamic attributes and required single/multiple paid options, quantity boundaries, affiliate action, cart/wishlist feedback, related/latest products, authenticated reviews and review pagination |
| Cart/wishlist | Bag trigger alone is insufficient evidence | Add full cart, cart preview, wishlist, selected options, removal/clear confirmation, coupons and calculated totals; empty/error states. Quantity editing is an intentional enhancement, not existing parity established by the source audit |
| Checkout | Empty ordering menu prevents verification | Add guest/returning customer, contact and optional account creation, store-type conditional delivery, location-dependent methods/fees, configured customer shipping exemption, notes, enabled payment methods and validation/processing/error states |
| Payments | Wix ordering widgets do not supply Mellow gateway views | Include Stripe/Paystack/Razorpay/Squad handoff designs and configurable external-provider fallback, success/failure/pending states. Mellow success normally reaches thank-you; failure normally returns to checkout |
| Customer account | Usable account flow not verified | Login/register/recovery, dashboard, paginated order history, order details/statuses, eligible downloads, profile/password updates and logout |
| Tracking | No confirmed reference surface | Guest order-reference flow and customer order-detail flow, found/not-found/invalid states |
| Confirmation/content | Not verified beyond about/contact | Confirmation with order content, support, policy/rich custom pages, long content/tables/media/accordions and error page |
| Responsive/accessibility | Desktop page alone cannot establish this | Independently verify narrow mobile/tablet/laptop/desktop, labels, keyboard/focus, dialog close/Escape, reduced motion, RTL, long text/currencies and missing optional content |

## Dynamic options are not cake-only features

Use cakes to demonstrate flavour, serving size, finish and optional paid decorations. Labels and choices must come from product attributes/options so non-bakery merchants can use the same theme. Backend validation, stock and price remain authoritative. The design must fit many options, unavailable options, single/multiple selections and required-option errors.

## Optional checklist features and reference-only additions

The code-verified appendix in theme.md explicitly distinguishes existing Mellow behavior from a broad template wishlist. Quick view, autocomplete/history, compare, product video/review images/Q&A, express wallets, cookie consent, dark mode, dedicated blog/app sections and other unsupported features must not be silently declared present. The ledger marks these as conditional or optional; unsupported backend features require separate implementation scope.

The reference's newsletter/social feed, event/cake tailoring copy, pickup-time scheduler and dine-in options are not proof Mellow implements those services. Keep optional visual areas configurable. Do not add restaurant scheduling, reservations or dine-in order behavior without a Mellow backend contract.

Customer shipping-fee exemptions are supplied by the customer/backend configuration; customers must not be given a control to grant themselves free shipping.

## Source hierarchy and completeness gate

1. The user's storefront-only correction overrides the old theme.md discussion of merchant edit-mode UI.
2. Use theme.md's code-verified appendix for existing Mellow capabilities and route behavior.
3. Use the 830-row checklist ledger for coverage tracking, including duplicate review/scorecard entries; these are not 830 unique live features.
4. Reference observation is design evidence, not proof a backend operation works.
5. Before handoff, each required route/state must point to a real HTML/CSS/JS implementation and meaningful verification evidence. Optional/conditional entries must have explicit decisions. Backend-dependent authentication, payment and downloads must be labelled as integration work in a static package.

## Recommended implementation direction

Name: Buttercup. Folder: `/Users/Wills/Desktop/Ogaranya Projects/mello-theme ideas/buttercup`.

Recommended: reproduce the reference's visual composition, then extend that system across Mellow's complete customer journey. Keep the airy white/blush/lavender palette, delicate rules and cake photography while adding the missing navigation, collections, buying, account and state surfaces.

Alternative: copy only the reference's visible homepage/menu pages. This would require less work but would leave major Mellow storefront requirements uncovered, so it does not meet this brief.

The proposal was approved and the static storefront is implemented. See mellow-parity.md for the post-build capability map and verification.md for fresh checks; the original reference observations above remain unchanged.
