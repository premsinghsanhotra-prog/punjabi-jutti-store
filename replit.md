# Workspace

## Overview

Full-stack Punjabi Jutti Store e-commerce web application built with React + Vite frontend, Express.js backend, and PostgreSQL database.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite (artifacts/punjabi-jutti-store)
- **API framework**: Express 5 (artifacts/api-server)
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)
- **Auth**: Session-based (express-session)

## Structure

```text
artifacts-monorepo/
├── artifacts/              # Deployable applications
│   ├── api-server/         # Express API server
│   └── punjabi-jutti-store/ # React + Vite frontend
├── lib/                    # Shared libraries
│   ├── api-spec/           # OpenAPI spec + Orval codegen config
│   ├── api-client-react/   # Generated React Query hooks
│   ├── api-zod/            # Generated Zod schemas from OpenAPI
│   └── db/                 # Drizzle ORM schema + DB connection
├── scripts/                # Utility scripts
├── pnpm-workspace.yaml
├── tsconfig.base.json
├── tsconfig.json
└── package.json
```

## Punjabi Jutti Store Features

- Home page with hero banner and featured products
- Product catalog with search/filter by category
- Product detail page with reviews and ratings
- User registration and login (session-based auth)
- Shopping cart (add, update, remove items)
- Checkout with UPI/bank payment details
- WhatsApp order notification to admin (9988963994)
- Order tracking by Order ID
- Admin dashboard (products, orders, payment settings)
- WhatsApp chat button in footer
- Enquiry number: 9988963994

## Admin Credentials

- Email: admin@punjabijutti.com
- Password: 123 (hash stored as SHA-256)

## Database Schema

Tables: users, products, orders, order_items, reviews, cart, payment_settings

## API Routes

- `GET/POST /api/auth/*` — Authentication
- `GET /api/products` — Products (with search/category filter)
- `GET /api/products/:id` — Product detail with reviews
- `POST/PUT/DELETE /api/products/:id/reviews` — Reviews
- `GET/POST/PUT/DELETE /api/cart` — Cart management
- `GET/POST /api/orders` — Orders
- `GET /api/orders/track/:id` — Public order tracking
- `GET/PUT /api/admin/orders` — Admin order management
- `GET/PUT /api/payment-settings` — Payment settings

## TypeScript & Composite Projects

Every package extends `tsconfig.base.json` which sets `composite: true`. The root `tsconfig.json` lists all packages as project references.

## Root Scripts

- `pnpm run build` — runs `typecheck` first, then recursively runs `build` in all packages
- `pnpm run typecheck` — runs `tsc --build --emitDeclarationOnly`
