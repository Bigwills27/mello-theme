# Aurelle Implementation Plan

**Goal:** Deliver the approved complete static beauty theme in aurelle.
**Architecture:** Semantic HTML page content, shared CSS tokens and responsive layouts; browser-local catalog/cart/wishlist state with separate modules for catalog, store, product, checkout and account interactions. Backend-dependent actions are explicit integration demonstrations.
**Tech Stack:** HTML5, CSS, vanilla JavaScript, local imagery.
**Spec:** docs/design.md

## Global Constraints
- Plain HTML, CSS and JavaScript in dedicated folders.
- Preserve Mellow customer-facing content and buying-flow coverage.
- Exclude merchant dashboards, store editors and customization controls.
- Keep merchant branding/configuration data separate from layout.
- Do not submit credentials or payments to a fake service.

## Tasks
- [x] Foundation: create local image assets, shared layout/styles, configuration/catalog data, navigation/drawers, accessible dialogs and browser-local state.
- [x] Discovery: homepage, shop, category, brand, search, trending/best-sales, sorting, filtering and pagination.
- [x] Buying: product gallery/options/reviews, cart, wishlist, conditional checkout, thank-you, payment/result screens.
- [x] Customer/content: account forms/dashboard/orders/details/settings, password recovery, tracking, customer-facing custom pages.
- [x] Review: check every local link/asset, JavaScript syntax, desktop/mobile interactions where browser tooling is available, and document coverage/integration limits.

Inline execution is authorized by the user's “okay proceed please”.
