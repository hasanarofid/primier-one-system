# Software Architecture & Tech Stack - Premier One Motorsport

## 1. Tech Stack Utama
Proyek website Premier One Motorsport dikembangkan menggunakan teknologi modern yang berfokus pada kecepatan, reaktivitas antarmuka, dan kemudahan _maintenance_:
- **Backend Framework**: Laravel 13 (PHP)
- **Frontend Framework**: Vue 3 (Composition API, `<script setup>`)
- **SPA Bridge**: Inertia.js v2
- **Styling**: Tailwind CSS v4 (Utility-first)

## 2. Struktur Proyek
Karena ini merupakan arsitektur monorepo (Laravel + Vue), ikuti struktur direktori berikut:

- `app/` & `routes/`: Tempat meletakkan logika backend, *Controllers*, dan definisi routing (API maupun Web).
- `resources/js/Pages/`: Komponen Vue yang berfungsi sebagai halaman utama (Page level) yang di-render melalui Inertia.
- `resources/js/Components/`: Komponen Vue *reusable* (seperti Navbar, Footer, Button, Card).
- `resources/js/Layouts/`: Layout utama yang membungkus *Pages* (misal: `MainLayout.vue`).
- `resources/css/app.css`: Konfigurasi dan *custom styling* Tailwind CSS.
- `public/`: Aset statis seperti gambar, ikon, dan logo (misal: `public/images/`).

## 3. Komunikasi Data (Inertia)
- Backend Laravel harus mereturn data melalui `Inertia::render('PageName', [...data])`.
- Hindari pembuatan API terpisah (melalui `routes/api.php`) jika data hanya dibutuhkan saat inisialisasi halaman. Gunakan *props* dari Inertia.
- Jika ada *action* asinkron (misal form kontak), gunakan helper bawaan Inertia seperti `router.post()` atau `useForm()`.

## 4. Tailwind & Styling Rule
- Manfaatkan *utility classes* milik Tailwind v4 semaksimal mungkin.
- Untuk animasi dinamis (micro-animations), gunakan utility seperti `transition`, `duration-300`, `hover:scale-105`, dll.
- Hindari menulis CSS manual (custom CSS di `.css`) kecuali untuk *glassmorphism* kompleks atau styling spesifik yang tidak tercover oleh utility Tailwind (harus di-comment dengan jelas tujuannya).
