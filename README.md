<div align="center">

# Klipin — Frontend

**Client aplikasi Klipin**, sistem riset referensi & literatur skripsi: cari jurnal, ringkas otomatis, dan simpan catatan.

[![Status](https://img.shields.io/badge/status-academic%20project-blue?style=flat-square)](#)
[![Next.js](https://img.shields.io/badge/Next.js-15-000000?style=flat-square&logo=next.js&logoColor=white)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)

</div>

---

## Tentang

Antarmuka Klipin — aplikasi bantu mahasiswa mengumpulkan literatur skripsi. Pengguna mencari paper, meminta ringkasan otomatis, lalu menyimpannya ke perpustakaan pribadi dan mencatat ide.

Repo ini adalah **frontend**; API-nya ada di **[`klipin-backend`](https://github.com/Ilhamaji/klipin-backend)**.

## Fitur

Halaman `/` menggabungkan pencarian dan ringkasan: masukkan kata kunci, hasil paper muncul, lalu minta ringkasan tanpa pindah halaman.

Empat halaman lain menampung hasil kerja:

- `/library` — artikel yang disimpan.
- `/notes` — catatan pribadi per artikel (tambah, ubah, hapus).
- `/history` — riwayat query, bisa dihapus per entri.
- `/settings` — pengaturan akun.

Login memakai JWT yang disimpan di cookie lewat `js-cookie`. Tema terang/gelap diatur `ThemeProvider`, dan perpindahan halaman dianimasikan dengan Framer Motion.

## Tech Stack

| Bagian | Teknologi |
| --- | --- |
| Framework | Next.js 15 (App Router) |
| Bahasa | TypeScript |
| Styling | Tailwind CSS 4 |
| Auth | JWT (cookie) |
| Animasi | Framer Motion |
| Ikon | Lucide React |
| Proxy API | `middleware.ts` (rewrite `/api` → backend) |

## Menjalankan

### 1. Prasyarat

- Node.js 18+
- Backend [`klipin-backend`](https://github.com/Ilhamaji/klipin-backend) berjalan

### 2. Clone & install

```bash
git clone https://github.com/Ilhamaji/klipin-frontend.git
cd klipin-frontend
npm install
```

### 3. Environment

```env
API_BASE_URL=http://localhost:3000
```

### 4. Jalankan

```bash
npm run dev
```

Buka [http://localhost:3000](http://localhost:3000).

## Struktur

```
app/
  layout.tsx              # root layout & provider
  login/page.tsx          # halaman login
  (main)/
    layout.tsx            # layout dengan sidebar
    page.tsx              # pencarian & ringkasan
    library/page.tsx      # perpustakaan artikel
    notes/page.tsx        # catatan
    history/page.tsx      # riwayat pencarian
    settings/page.tsx     # pengaturan
components/
  Sidebar.tsx, ThemeProvider.tsx, ConfirmationModal.tsx
lib/
  api.ts                  # seluruh pemanggilan API (login, search, summarize, notes)
  utils.ts
middleware.ts             # proteksi route & proxy /api
```

## Kontrak API

Frontend memanggil endpoint berikut pada backend:

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
Dibuat oleh <a href="https://github.com/Ilhamaji">Ilham Aji</a>
</div>
