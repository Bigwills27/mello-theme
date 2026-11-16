# Aurelle content and interaction coverage

Scope: customer-facing storefront only. Merchant dashboards, editors and customization interfaces are excluded. Customer accounts, orders and profile settings are part of the storefront.

This file is the design handoff for the requested Mellow theme. **Designed** means an HTML/CSS surface and browser behavior exist. **Integration** means the live platform must provide tenant data, authenticated behavior or provider results. It does not mean a live transaction was tested.

## Page map

| Mellow route/surface | Theme file | Coverage and handoff |
|---|---|---|
| `/` | `index.html` | Hero banners with controls; category discovery; featured, trending, offers, best sellers, arrivals; brand links; promotion/story/footer. Wire Mellow section collections and banner metadata. |
| `/shop` | `shop.html` | Responsive product grid, category/brand/price/stock/rating/sale filters, sorting, active-context chips and pagination. Mobile filter expand/collapse. |
| `/category/{slug}/{id}` | `category.html` | Category title, matching products and filters. `?category=Hydrate`. |
| `/brand/{slug}/{id}` | `brand.html` | Brand context and filtered product listing. `?brand=Aurelle`. Add real brand metadata if provided. |
| `/shop?src=…` | `search.html` | Query heading, results, filters, sorting and no-results feedback. No autocomplete dependency. |
| `/trending`, `/best-sales` | `trending.html`, `best-sales.html` | Matching collection contexts with shared listing controls. |
| `/product/{slug}/{id}` | `product.html` | Gallery, thumbnails, lightbox, name, category/brand, price/discount, SKU, stock, formula/size choices, paid gift option, quantity limits, cart/wishlist, affiliate CTA, description/info/delivery/reviews sections and related products. |
| `/cart` | `cart.html` | Line items/options, quantity, remove/clear confirmation, coupon apply/remove, tax/discount/total and checkout. Quantity editing is a deliberate addition to the old static cart display. |
| `/wishlist` | `wishlist.html` | Saved cards, wishlist toggle/removal, add to bag and empty state. Browser-local guest behavior. |
| `/checkout` | `checkout.html` | Returning customer prompt, guest data, account-creation password reveal, delivery/pickup/digital modes, location-dependent methods, shipping fees derived from the customer configuration, notes, configurable payment choices, legal consent and totals. |
| `/thanks` | `thanks.html` | Name/reference, payment/delivery status, order totals, view order, continue shopping and support. Real confirmation email comes from backend. |
| `/user/login`, `/user/register` | `account/login.html`, `account/register.html` | Form fields, required validation, password matching, remember-me surface, recovery links and explicit preview profile. Live auth must replace demo state. |
| Password recovery | `account/forgot-password.html`, `account/reset-password.html` | Request/reset forms and expired-token state. The real platform currently renders these outside tenant theme folders; choose integration ownership. |
| `/user/dashboard` | `account/dashboard.html` | Personal greeting, order/wishlist/cart summary, recent order and navigation. |
| `/user/orders` | `account/orders.html` | Order table, payment/status/total, order links, mobile horizontal scroll, explicit empty state. Fetch/pagination from server during integration. |
| `/user/order/view/{id}` | `account/order.html` | Status timeline, delivery/contact/payment info, item/option totals, invoice print/PDF surface, conditional digital download and support. |
| `/user/settings` | `account/settings.html` | Name/email, current/new/confirm password fields and validation/success feedback. Backend must verify current password. |
| `/user/track/order/{id}` and `/tracking` | `tracking.html` and `account/order.html` | Guest reference lookup, found/not-found and shared order details. Authenticated ownership and safe lookup come from server. |
| Gateway intermediate views | `payment/paystack.html`, `squad.html`, `stripe.html`, `razorpay.html`, `bank.html` | Order reference/amount, provider handoff area, explicit simulated outcomes and no-order state. Mount real provider widgets/redirects via Mellow. |
| Payment success/failure/processing | `payment/success.html`, `failed.html`, `processing.html` | Explicit result layouts. Current Mellow success routes to `/thanks`, failure back to checkout; additional standalone result pages are optional. Checkout also supports failed-payment feedback. |
| `/page/{slug}/{id}` | `pages/custom.html` and policy/story pages | Rich headings/text/media/table/accordion/links/CTA. Merchant content replaces samples. |
| Error | `404.html` | Missing-page surface; hosting must map errors to it. Invalid product/order/reference also have in-page feedback. |

## Shared shell and hidden states

| UI | Demonstrated state/trigger |
|---|---|
| Main navigation | Desktop nested shop menu, category links, mobile drawer and close/Escape |
| Search | Header search dialog and query submission |
| Cart preview | Bag trigger, populated/empty state, totals and removal |
| Counters | Cart/wishlist counters update after actions and persist between pages |
| Wishlist | Selected/unselected heart, removal and empty collection |
| Product gallery | Thumbnail selection and image dialog; Escape/native focus behavior |
| Options | Required radio selection, size/gift price changes, stock-limited quantity |
| Reviews | Existing review list, login prompt, preview-profile review form, stars/comment, local submitted review |
| Filters | Accordion groups, mobile reveal, sort, pagination, filters and empty results |
| Listing request states | `?state=loading` and `?state=error`; retry restores sample data |
| Cart clear | Confirmation dialog with cancel and clear outcomes |
| Coupons | Success, invalid, expired, remove, totals update |
| Checkout account | Checkbox reveals password; customer profile prefill |
| Delivery | Location populates methods, calculated shipping, pickup/digital hide address, configured customer fee exemption |
| Order button | Required fields/legal checks, disabled processing state, handoff |
| Payment | Success clears cart, failure retains cart and returns feedback, pending layout |
| Account | Browser-local preview profile, password mismatch, sign out, recovery/expired token |
| Order files | Download action appears only on completed, paid digital orders |
| Content | FAQ accordion, contact form validation/status, flexible custom text/media/table |
| Language/RTL | Footer selector toggles direction; actual translations/locale come from Mellow |
| Accessibility | Skip link, native dialogs, input labels, live feedback, focus states, reduced motion and responsive tables |

## Tenant data to connect

- Domain/template resolution; store name, logo, favicon, merchant colors and currency format.
- Dynamic/nested menus and custom page links; contact details and configured socials.
- Hero/banner/bump-ad metadata, collection placement and enabled/disabled homepage sections.
- Product media, metadata, regular/sale price, options/attributes and stock validation.
- Listing endpoints, filters/sort/pagination; review aggregates/list/create responses.
- Cart, wishlist and coupon responses/totals, including server validation errors.
- Shop type, enabled locations/methods, customer shipping-fee setting, tax and gateways.
- Checkout order creation, customer registration/login/reset/settings, order ownership/status and file authorization.
- Provider callbacks, payment verification, email/WhatsApp order-receipt behavior and return URLs.

## Additional or optional scope

The broad original `theme.md` contains aspirations beyond the current platform. Newsletter/marketing blocks, review imagery, questions and answers, compare, express wallets, product video, separate SEO brand/category layouts, cookie consent, dark mode, and automatic translations are not silently assumed to be live features. This design includes optional newsletter/editorial layouts and additional payment result pages. Remaining items need explicit feature scope if wanted.

There is no product quick-view feature in the audited Mellow themes, and this theme keeps product options in the full detail view. Product gallery lightbox, search and cart dialogs cover the implemented overlay needs.

## Review boundaries

The HTML package preserves the content surfaces and conditional flows through sample data. Production tenant switching, server responses, gateway verification, email/WhatsApp delivery, authenticated downloads, account ownership and real inventory must be checked again after integration. Long/missing merchant content should be exercised with real tenant fixtures. The static package does not declare the Laravel theme installed or ready to accept real orders.
