# WanderVista — Travel Website Starter

A responsive, multi-page travel booking website prototype with working client-side destination, hotel and package search/filter/sort, date validation, a demo checkout journey, and a demo admin overview.

## Important: prototype vs production

This project is a front-end prototype, not a live travel agency or production booking system. Listings, prices, hotel names/ratings, itineraries and all commercial content are sample/illustrative. No live hotel inventory, flight inventory, tour supplier, reservation API, database, customer authentication, email delivery, payment gateway, or admin authorization is connected. The checkout explicitly says it does not create a reservation or charge a payment method.

Do not use this version to collect sensitive customer or payment data or to sell travel.

## Run locally

Because this is a static project, you can open `index.html` directly, or serve the folder using any static web server. Example with Python:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000` from the project folder.

## Pages

- `index.html` — homepage
- `destinations.html` — searchable/filterable destination directory
- `destination.html?name=Bali` — destination details template
- `hotels.html` — filterable sample hotel directory
- `hotel.html?name=Azure%20Bay%20Retreat` — hotel detail template
- `packages.html` — filterable holiday package directory
- `package.html?name=Bali%3A%20Island%20%26%20Ubud%20Escape` — package detail template
- `booking.html` — browser-validated demo checkout
- `confirmation.html` — explicitly demo-only result page
- `account.html` — account UI preview only
- `admin.html` — admin dashboard preview only
- `about.html`, `contact.html`, `faqs.html`, `privacy.html`, `terms.html`, `404.html`

## Images and fonts

Destination photography is loaded from Unsplash image URLs and fonts from Google Fonts. This requires an internet connection. Before commercial use, verify the licence and terms for each asset, confirm that hotlinking is permitted, and consider downloading optimized, licensed copies to your own image/CDN pipeline. A background video is not included; the homepage uses a large hero photograph for reliability and performance.

## Production architecture recommendation

For genuine bookings, keep the static UI separate from a secure backend. A practical starting architecture is:

- Frontend: Next.js or another SSR-capable framework for SEO-friendly public pages.
- Backend: Node.js/TypeScript API or equivalent.
- Database: PostgreSQL with migrations and transactional booking logic.
- Authentication: established server-side auth provider or secure session-based implementation.
- Inventory: a contracted hotel/tour supplier API that supports live rates, availability, reservation creation and cancellation.
- Payments: a supported provider such as Razorpay (India) or Stripe where appropriate, using server-created payment orders, signed webhooks and server-side verification.
- Hosting: a full-stack host for the app/API and managed database. GitHub Pages alone cannot securely run a backend or protect payment secrets.

Never put private API keys, payment secrets, database credentials, or supplier tokens in frontend code or a public Git repository.

## Required work before launch

1. Replace `example.com` in `sitemap.xml` and `robots.txt` with the final canonical domain.
2. Implement server-side authentication, role-based authorization and admin route/API protection.
3. Add supplier API credentials and verify inventory/rate rules.
4. Create database schema and migrations for users, inventory references, bookings, payments, and status history.
5. Recalculate all prices on the server; use idempotency keys and prevent duplicate booking/payment requests.
6. Verify payment webhooks/signatures and only confirm bookings after verified payment plus supplier confirmation.
7. Implement transactional email, error monitoring, rate limiting, security headers, backups and privacy-aware logs.
8. Replace illustrative content with accurate, permissioned supplier data and real business/legal details.
9. Have privacy policy, terms, cancellation/refund terms and applicable travel regulations reviewed professionally.
10. Test keyboard accessibility, mobile behavior, Core Web Vitals, metadata, canonical URLs, sitemap, robots and the complete booking journey.

## SEO notes

The public directory and informational pages have page-specific title/description tags. Dynamic detail templates use `noindex` in this starter because they are driven by query strings and sample content; convert them to unique canonical, indexable destination/property/package URLs after implementing server-rendered or pre-rendered real content. The sitemap intentionally contains only a small set of public pages and uses a placeholder domain that must be replaced.

## Known limitations

- No backend, persistent database, live availability, reservation creation, cancellation, payment processing, user login, admin security, or email sending.
- Search and filters work against in-file sample arrays only.
- The contact, newsletter, sign-in and checkout interfaces are demo-only.
- No automated test suite or production security audit has been run.
