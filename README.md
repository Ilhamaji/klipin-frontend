<div align="center">

# Klipin — Frontend

**The Klipin client**: a literature-research tool for thesis writing — search journals, summarise automatically, and keep notes.

[![Status](https://img.shields.io/badge/status-academic%20project-blue?style=flat-square)](#)
[![Next.js](https://img.shields.io/badge/Next.js-15-000000?style=flat-square&logo=next.js&logoColor=white)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)

**English** · [Bahasa Indonesia](README.id.md)

</div>

---

## About

The Klipin interface, built for students collecting sources for a thesis. Users search for papers, request a summary, then save the result to a personal library and attach notes.

This is the **frontend**; the API lives in **[`klipin-backend`](https://github.com/Ilhamaji/klipin-backend)**.

## Features

The `/` page combines search and summarisation: enter a keyword, results appear, and you can request a summary without leaving the page.

Four other pages hold the working results:

- `/library` — saved articles.
- `/notes` — personal notes per article (create, edit, delete).
- `/history` — previous queries, deletable one by one.
- `/settings` — account settings.

Login uses a JWT stored in a cookie via `js-cookie`. Light and dark themes are handled by `ThemeProvider`, and page transitions are animated with Framer Motion.

## Tech Stack

| Layer | Technology |
| --- | --- |
| Framework | Next.js 15 (App Router) |
| Language | TypeScript |
| Styling | Tailwind CSS 4 |
| Auth | JWT (cookie) |
| Animation | Framer Motion |
| Icons | Lucide React |
| API proxy | `middleware.ts` (rewrites `/api` to the backend) |

## Getting Started

### 1. Prerequisites

- Node.js 18+
- A running [`klipin-backend`](https://github.com/Ilhamaji/klipin-backend)

### 2. Clone and install

```bash
git clone https://github.com/Ilhamaji/klipin-frontend.git
cd klipin-frontend
npm install
```

### 3. Environment

```env
API_BASE_URL=http://localhost:3000
```

### 4. Run

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Project Layout

```
app/
  layout.tsx              # root layout and providers
  login/page.tsx          # login page
  (main)/
    layout.tsx            # layout with the sidebar
    page.tsx              # search and summarisation
    library/page.tsx      # saved articles
    notes/page.tsx        # notes
    history/page.tsx      # search history
    settings/page.tsx     # settings
components/
  Sidebar.tsx, ThemeProvider.tsx, ConfirmationModal.tsx
lib/
  api.ts                  # every API call (login, search, summarize, notes)
  utils.ts
middleware.ts             # route protection and /api proxying
```

## API Contract

The frontend calls these endpoints on the backend:

```http
POST   /api/auth/login
POST   /api/search
POST   /api/summarize
GET    /api/note
POST   /api/note/add
PUT    /api/note/edit/:id
DELETE /api/note/delete/:id
```

---

<div align="center">
Built by <a href="https://github.com/Ilhamaji">Ilham Aji</a>
</div>
