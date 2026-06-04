# Next.js APP ROUTER CHEATSHEET
*Everything you need to build modern apps with Next.js App Router.*

---

## 1. APP ROUTER FOLDER STRUCTURE

```text
app/
├── layout.tsx         # Root Layout (required)
├── page.tsx           # Home Page
├── about/
│   └── page.tsx       # /about route
├── dashboard/
│   ├── layout.tsx     # Dashboard Layout
│   ├── page.tsx       # /dashboard
│   ├── analytics/
│   │   └── page.tsx   # /dashboard/analytics
│   └── settings/
│       └── page.tsx   # /dashboard/settings
├── loading.tsx        # Loading UI
├── error.tsx          # Error UI
├── not-found.tsx      # 404 UI
├── (auth)/            # Route Group (does not affect URL)
│   ├── login/
│   │   └── page.tsx   # /login
│   └── register/
│       └── page.tsx   # /register
└── api/               # API Routes
```

> 💡 **Key Rules:**
> - Folders are routes. `page.tsx` is required to make a route public.
> - Use parentheses `( )` for Route Groups (does not affect the URL path).

---

## 2. CORE CONCEPTS

### Server Components
* Default in App Router.
* Runs on the server.
* Better performance.

```tsx
// app/page.tsx
export default function Page() {
  return <h1>Hello</h1>;
}
```

### Client Components
* Use `'use client'` for interactivity, hooks, state.

```tsx
'use client'
import { useState } from 'react'

export default function Counter() {
  const [count, setCount] = useState(0)
  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  )
}
```

### Layouts
* UI shared across routes.
* Preserves state & UI.

```tsx
// app/dashboard/layout.tsx
export default function DashboardLayout({
  children
}: { children: React.ReactNode }) {
  return (
    <div>
      <Sidebar />
      <div>{children}</div>
    </div>
  )
}
```

### Pages
* Unique UI for a route.

```tsx
// app/about/page.tsx
export default function Page() {
  return <div>About Page</div>;
}
```

### Templates
* Similar to layouts but create a new instance on navigation (re-mounts on every visit).

```tsx
// app/dashboard/template.tsx
export default function Template({
  children
}: { children: React.ReactNode }) {
  return <div>{children}</div>
}
```

### Route Groups
* Organize routes without affecting the URL path.

```text
app/
├── (marketing)/
│   └── page.tsx     ──> /
└── (shop)/
    └── page.tsx     ──> /

*(marketing) and (shop) won't show in the URL.
```

---

## 3. DATA FETCHING

### Fetch (Recommended)
Server-side data fetching with caching by default.

```tsx
// app/page.tsx
async function getData() {
  const res = await fetch(
    'https://api.vercel.app/blog',
    { next: { revalidate: 60 } }
  );
  return res.json();
}

export default async function Page() {
  const data = await getData();
  return <pre>{JSON.stringify(data)}</pre>;
}
```

### Dynamic Data
Opt-out of caching.

* **No cache:**
  ```tsx
  fetch(url, { cache: 'no-store' })
  ```
* **Revalidate immediately:**
  ```tsx
  fetch(url, { next: { revalidate: 0 } })
  ```

### Route Segment Config
Control caching, runtime, etc.

```tsx
// app/blog/page.tsx
export const revalidate = 60
export const dynamic = 'force-dynamic'
export const dynamicParams = false
export const runtime = 'edge'
export const fetchCache = 'force-cache'

export default function Page() {
  return <div>Blog</div>;
}
```

### Search Params
Get search params in a Server Component.

```tsx
// app/search/page.tsx
export default function Page({
  searchParams,
}: { searchParams: { q?: string } }) {
  const q = searchParams.q;
  return <div>Search: {q}</div>;
}
```

---

## 4. ROUTE HANDLERS (API ROUTES)

Create API endpoints inside the app directory.

```text
app/
└── api/
    └── users/
        └── route.ts
```

```typescript
// app/api/users/route.ts
import { NextResponse } from 'next/server'

export async function GET() {
  return NextResponse.json({ users: [] })
}

export async function POST(req: Request) {
  const data = await req.json()
  return NextResponse.json({ success: true, data })
}
```

---

## 5. SPECIAL FILES

* **`loading.tsx`**: Instant loading UI for a route segment.
* **`error.tsx`**: Error boundary for a route segment.
* **`not-found.tsx`**: 404 UI for unmatched routes.
* **`global-error.tsx`**: Catch-all error UI (root level).
* **`template.tsx`**: New instance of UI on navigation.

---

## 6. NAVIGATION

* **`<Link />`** (Client-side navigation):
  ```tsx
  <Link href="/dashboard">Dashboard</Link>
  ```
* **`useRouter()`** (Programmatic navigation):
  ```tsx
  const router = useRouter()
  router.push('/dashboard')
  ```
* **`usePathname()`** (Get current pathname):
  ```tsx
  const pathname = usePathname()
  ```
* **`useSearchParams()`** (Read search params in Client Component):
  ```tsx
  const searchParams = useSearchParams()
  const q = searchParams.get('q')
  ```

---

## 7. GOOD TO KNOW

* 🟩 Server Components are default. Use `'use client'` only when needed.
* 🟩 Layouts preserve state and do not re-render on navigation.
* 🟩 Data is cached by default. Control with revalidate and cache options.
* 🟩 `( )` Route Groups help organize your app without affecting the URL.
* 🟩 Place providers in `layout.tsx` to share across pages.

---

## 8. BEST PRACTICES

* ⭐ Fetch data on the server whenever possible.
* ⭐ Keep Client Components small and focused.
* ⭐ Use `loading.tsx` for better UX.
* ⭐ Handle errors with `error.tsx`.
* ⭐ Use Route Groups for a clean and scalable structure.
* ⭐ Leverage caching for performance.
