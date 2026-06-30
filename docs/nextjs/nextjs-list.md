---
date:
  created: 2026-06-30
---

# Comprehensive Next.js

> App Router-first, targeting **Next.js 15**. The legacy Pages Router is noted where it
> still matters, but the App Router is the default throughout.

## {++0. About This Section++}

- {==What this covers==}
      - Modern Next.js (15) with the App Router and React Server Components
      - Builds on the React and TypeScript sections of this guide
      - Practical, runnable TypeScript examples

## {++1. Introduction to Next.js & Setup++}

- {==What is Next.js?==}
      - A full-stack React framework — what it adds over plain React
      - Why use it (routing, rendering, data, optimizations, deployment)
- {==Rendering strategies recap==}
      - CSR vs SSR vs SSG vs ISR (and where Next.js fits)
- {==App Router vs Pages Router==}
      - Why the App Router is the default/recommended model
- {==Creating a project==}
      - `create-next-app` with TypeScript
      - Project structure & file conventions (`app/`, `public/`, special files)
      - Dev / build / start scripts and Turbopack

## {++2. Routing (App Router)++}

- {==File-based routing in `app/`==}
      - Pages (`page.tsx`) and Layouts (`layout.tsx`)
      - Nested routes & nested layouts
- {==Dynamic routes==}
      - `[id]`, catch-all `[...slug]`, optional catch-all `[[...slug]]`
- {==Advanced routing==}
      - Route groups `(group)`
      - Parallel routes (`@slot`) & intercepting routes `(.)`
- {==Navigation==}
      - `<Link>`, `useRouter`, `redirect`, `usePathname`, `useSearchParams`
- {==Special files==}
      - `loading.tsx`, `error.tsx`, `not-found.tsx`, `template.tsx`
      - Route segment config

## {++3. Rendering: Server & Client Components++}

- {==The React Server Components model==}
- {==Server vs Client Components==}
      - Defaults, when to use each
      - The `"use client"` boundary & composition patterns
      - Passing serializable props, interleaving server/client
- {==Static vs Dynamic rendering==}
- {==Streaming & Suspense==}
- {==Runtimes==}
      - Node.js vs Edge runtime (overview)

## {++4. Data Fetching & Caching++}

- {==Fetching in Server Components==}
      - `async`/`await` + `fetch`
- {==The Next.js caching model==}
      - Next 15 defaults (uncached `fetch`), `force-cache`, `revalidate`
      - Request Memoization, Data Cache, Full Route Cache, Router Cache
- {==Revalidation==}
      - Time-based and on-demand (`revalidatePath` / `revalidateTag`)
- {==Static generation==}
      - `generateStaticParams` (SSG) and ISR
      - `unstable_cache` / the `'use cache'` direction
- {==Client-side fetching==}
      - When to reach for SWR / TanStack Query
- {==Error & not-found handling==}

## {++5. Server Actions & Mutations++}

- {==What are Server Actions?==}
      - `"use server"`, forms, progressive enhancement
- {==Form state & UX==}
      - `useActionState`, `useFormStatus`, `useOptimistic`
- {==Validation & errors==}
      - Zod validation, returning typed errors
- {==After a mutation==}
      - Revalidation and `redirect`
- {==Security==}
      - Auth checks, never trusting input
- {==Calling actions from Client Components==}

## {++6. Route Handlers (API)++}

- {==`route.ts` basics==}
      - HTTP methods, `NextRequest` / `NextResponse`
- {==Request data==}
      - Dynamic segments, query params, body, cookies, headers
- {==Caching & dynamic behavior==}
- {==Cross-cutting==}
      - CORS, streaming responses, webhooks
- {==Route Handlers vs Server Actions==} — when to use which

## {++7. Styling & Fonts++}

- {==CSS in Next.js==}
      - CSS Modules, global CSS, Sass
- {==Tailwind CSS==}
      - Setup in a Next.js project
- {==CSS-in-JS with the App Router==}
      - styled-components / Emotion caveats in RSC
- {==Fonts==}
      - `next/font` (Google & local), automatic optimization

## {++8. Optimizations (Image, Metadata/SEO, Scripts)++}

- {==Images==}
      - `next/image` — responsive, `sizes`, `priority`, formats
- {==Metadata & SEO==}
      - Metadata API (static & `generateMetadata`), Open Graph
      - `sitemap.ts`, `robots.ts`
- {==Scripts & lazy loading==}
      - `next/script`, `next/dynamic`
- {==Performance==}
      - Bundle analysis, Core Web Vitals (INP)

## {++9. Database Integration++}

- {==Choosing an ORM==}
      - Prisma vs Drizzle
- {==Setting up Prisma==}
      - Schema, the client singleton, migrations, seeding
- {==Querying data==}
      - In Server Components and Server Actions
      - The data-access-layer pattern
- {==Serverless caveats==}
      - Connection pooling

## {++10. Authentication (Auth.js v5)++}

- {==Auth.js (NextAuth) v5 setup==}
      - `auth.ts`, handlers, middleware
- {==Providers==}
      - OAuth and credentials
- {==Sessions==}
      - Accessing the session on the server and client
- {==Protecting routes==}
      - Middleware + server-side checks, role-based access
- {==Alternatives==}
      - Clerk, Lucia

## {++11. Middleware & Edge++}

- {==`middleware.ts`==}
      - The `matcher`, redirects/rewrites, headers, cookies
      - Auth in middleware
- {==The Edge runtime==}
      - Constraints and trade-offs
- {==`next.config` networking==}
      - `redirects`, `rewrites`, `headers`

## {++12. State Management in Next.js++}

- {==Server state vs client state==}
- {==URL as state==}
      - `searchParams`, the `nuqs` pattern
- {==Client state==}
      - Context and Zustand with RSC (provider setup)
- {==Server-data caching on the client==}
      - TanStack Query / SWR in the App Router
- {==Crossing the server/client boundary==}

## {++13. Testing Next.js Apps++}

- {==Unit & component testing==}
      - Vitest + React Testing Library (async Server Component caveats)
      - Mocking `next/navigation`
- {==API & data==}
      - Testing Route Handlers and Server Actions, MSW
- {==End-to-end==}
      - Playwright (recommended), Cypress

## {++14. Deployment++}

- {==Vercel==}
      - Zero-config deploys, env vars, preview deployments
- {==Build output==}
      - `standalone` output
- {==Self-hosting==}
      - Node server, Docker, ISR on self-host
- {==Environment & operations==}
      - `NEXT_PUBLIC_` vars, caching/CDN, monitoring & analytics
