# Engineering & Clean Code Guidelines - Premier One Motorsport

## 1. Aturan Penamaan (Naming Conventions)
- **File Komponen Vue**: Gunakan *PascalCase* (contoh: `HeroSection.vue`, `ContactForm.vue`).
- **File Controller Laravel**: Gunakan *PascalCase* dengan *suffix* Controller (contoh: `PageController.php`).
- **Variabel & Fungsi (Javascript/Vue)**: Gunakan *camelCase* (contoh: `submitForm()`, `driverData`).
- **Route / URL**: Gunakan *kebab-case* (contoh: `/about-us`, `/core-activities`).

## 2. Pedoman Kode Vue 3 (Frontend)
- **Composition API**: Wajib menggunakan `<script setup>` untuk semua komponen baru.
- **Reusability**: Pecah kode UI yang panjang menjadi komponen kecil di dalam `resources/js/Components/` (misal, ekstrak sebuah tombol menjadi `PrimaryButton.vue`).
- **State Management**: Gunakan *props* dan *emits* untuk komunikasi antar komponen. Jika state terlalu global, manfaatkan *composable* function (`useMyState.js`) daripada Vuex/Pinia jika belum terlalu kompleks.

## 3. Pedoman Kode Laravel (Backend)
- **Fat Model, Skinny Controller**: Letakkan logika query database atau format data di dalam Model (atau Service class), biarkan Controller seringkas mungkin hanya untuk menerima request dan me-return response Inertia.
- **Validation**: Selalu validasi data form yang masuk dari user menggunakan FormRequest atau `$request->validate()`.

## 4. Tata Bahasa & Respon AI
- **Fokus pada Kode**: Jangan memberikan penjelasan panjang lebar atau teori yang tidak diminta. Jika user meminta perbaikan, langsung berikan cuplikan kode (*snippet*) perbaikannya.
- **Bahasa Profesional**: Gunakan kalimat singkat, padat, profesional, dan to the point.
- **Tanya Jika Ragu**: Jika ada instruksi *design* atau logika yang saling bertentangan, berhentilah sejenak, jangan menebak (berhalusinasi), dan tanyakan konfirmasi kepada *user*.
