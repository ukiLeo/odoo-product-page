# AyurVeda Naturals Shop

A responsive React + TypeScript + Vite presentation catalogue for the AyurVeda Naturals Odoo store. The page intentionally does not implement checkout or collect customer/payment data: Odoo remains the system of record for products, cart, payment and order processing.

## Run locally

```bash
npm install
npm run dev
```

Create a production build with `npm run build` and preview it with `npm run preview`.

## Deploy to Vercel

1. Push this project to a Git provider and import the repository at [vercel.com/new](https://vercel.com/new).
2. Vercel detects Vite automatically. Use **Build Command** `npm run build` and **Output Directory** `dist`.
3. Deploy. No environment variables are required for this presentation page.

## Connect this catalogue to Odoo

The structured product data lives in [`src/products.ts`](./src/products.ts). For each product, replace the sample `odooUrl: '#'` with the public Odoo product URL, for example:

```ts
odooUrl: 'https://ayurvedic-product-e-commerce-website.odoo.com/shop/amla-hair-oil'
```

The **View product** links then open the real Odoo product page, where Odoo can show live availability, variants and the **Add to Cart** action. For a smooth in-tab experience, keep normal anchor links. Use `target="_blank"` only if the catalogue is embedded in a context where leaving the parent page is preferred.

Do not build a second cart in this frontend. Odoo's product pages and `/shop/cart` should handle the real cart and `/shop/checkout` should handle checkout. If you add a top-level cart link later, point it directly to:

`https://ayurvedic-product-e-commerce-website.odoo.com/shop/cart`

Keep the product `id` aligned with your Odoo `product.template` or external ID when syncing this file from a future API/CMS integration.

## Embedding

The page supports a chrome-free mode for an Odoo iframe or website embed:

`https://your-vercel-domain.vercel.app/?embed=true`

This hides the custom header and footer while preserving the collection, filters and product links. In normal mode, the small **Hide chrome** control in the header and **View in embed mode** footer action provide the same setting. The page itself does not store customer information.
