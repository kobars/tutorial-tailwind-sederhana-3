# Latihan: Dashboard Interaktif

## Deskripsi

Kamu akan membuat halaman **dashboard interaktif** yang menampilkan:

- Navbar dengan `select-none` dan link smooth-scroll
- Stats bar dengan 3 kartu: indikator **pulse**, titik **ping**, dan panah **bounce**
- **Scroll-snap carousel** horizontal yang bisa di-drag dengan efek scale + rotate saat hover
- Form interaktif dengan **caret color**, **accent color**, dan **resize** pada textarea
- **Custom animation** (`fade-in`, `slide-up`) menggunakan `@theme` dan `@keyframes`
- Loading spinner dengan `animate-spin`

---

## Langkah-Langkah

### 1. Siapkan file HTML

Buat file baru `latihan-dashboard-interaktif.html` dengan boilerplate HTML dan Play CDN. Tambahkan `scroll-smooth` pada tag `<html>` agar smooth-scroll aktif:

```html
<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Interaktif</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
</head>
<body>
    <!-- langkah selanjutnya di sini -->
</body>
</html>
```

### 2. Custom animations

Di dalam `<head>`, sebelum penutup `</head>`, tambahkan block `<style type="text/tailwindcss">` untuk mendefinisikan custom animation menggunakan `@theme` dan `@keyframes`:

```html
<style type="text/tailwindcss">
    @theme {
        --animate-fade-in: fade-in 0.8s ease-out;
        --animate-slide-up: slide-up 0.6s ease-out;
    }
    @keyframes fade-in {
        from { opacity: 0; }
        to { opacity: 1; }
    }
    @keyframes slide-up {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }
</style>
```

### 3. Styling body

Pada `<body>`, berikan background abu-abu gelap dan tinggi minimum selayar penuh:

```html
<body class="bg-gray-900 min-h-screen text-white">
```

### 4. Navbar

Buat navbar dengan `select-none` agar teks tidak bisa diseleksi. Link menggunakan `href="#id"` untuk smooth-scroll:

```html
<nav class="bg-gray-800 border-b border-gray-700 select-none">
    <div class="max-w-6xl mx-auto px-6 flex justify-between items-center h-14">
        <span class="text-lg font-bold text-white">Dashboard</span>
        <div class="flex gap-6">
            <a href="#stats" class="text-sm text-gray-400 hover:text-white transition-colors duration-200">Stats</a>
            <a href="#projects" class="text-sm text-gray-400 hover:text-white transition-colors duration-200">Projects</a>
            <a href="#form" class="text-sm text-gray-400 hover:text-white transition-colors duration-200">Form</a>
        </div>
    </div>
</nav>
```

### 5. Container utama dengan fade-in

Buat container utama dengan padding dan custom animation `animate-fade-in`:

```html
<div class="max-w-6xl mx-auto px-6 py-8 animate-fade-in">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 6. Stats bar — heading

Di dalam container utama, tambahkan heading section dengan `id` untuk smooth-scroll:

```html
<h2 id="stats" class="text-2xl font-bold mb-6 animate-slide-up">Overview</h2>
```

### 7. Stats bar — grid 3 kartu

Buat grid 3 kolom untuk menampung kartu-kartu stats:

```html
<div class="grid grid-cols-3 gap-6 mb-12">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 8. Stats — kartu pertama (animate-pulse)

Buat kartu stats pertama. Angka revenue menggunakan `animate-pulse` yang berkedip pelan, menandakan data sedang di-update:

```html
<div class="bg-gray-800 rounded-xl p-6 border border-gray-700">
    <p class="text-sm text-gray-400 mb-1">Total Revenue</p>
    <p class="text-3xl font-bold animate-pulse">Rp 124.5jt</p>
    <p class="text-sm text-emerald-400 mt-2">+12.5% bulan ini</p>
</div>
```

### 9. Stats — kartu kedua (animate-ping dot)

Buat kartu stats kedua. Di sebelah label, tambahkan titik kecil dengan `animate-ping` yang memberikan efek radar/gelombang, menandakan "live":

```html
<div class="bg-gray-800 rounded-xl p-6 border border-gray-700">
    <div class="flex items-center gap-2 mb-1">
        <p class="text-sm text-gray-400">Active Users</p>
        <span class="relative flex h-3 w-3">
            <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
            <span class="relative inline-flex rounded-full h-3 w-3 bg-emerald-500"></span>
        </span>
    </div>
    <p class="text-3xl font-bold">1,847</p>
    <p class="text-sm text-emerald-400 mt-2">Online sekarang</p>
</div>
```

### 10. Stats — kartu ketiga (animate-bounce arrow)

Buat kartu stats ketiga. Panah menggunakan `animate-bounce` yang melompat ke atas-bawah:

```html
<div class="bg-gray-800 rounded-xl p-6 border border-gray-700">
    <p class="text-sm text-gray-400 mb-1">Growth Rate</p>
    <p class="text-3xl font-bold">23.8%</p>
    <p class="text-sm text-emerald-400 mt-2">
        <span class="inline-block animate-bounce">↑</span> Trending up
    </p>
</div>
```

### 11. Carousel — heading

Di bawah stats bar, tambahkan heading section untuk carousel:

```html
<h2 id="projects" class="text-2xl font-bold mb-6">Recent Projects</h2>
```

### 12. Carousel — scroll-snap container

Buat container carousel horizontal dengan **scroll-snap**. Gunakan `cursor-grab` (tangan terbuka) dan `active:cursor-grabbing` (tangan mencengkeram) untuk menunjukkan bahwa area ini bisa di-drag:

```html
<div class="flex gap-6 overflow-x-auto snap-x snap-mandatory pb-4 cursor-grab active:cursor-grabbing mb-12">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 13. Carousel — slide pertama

Di dalam carousel, buat slide pertama. Setiap slide harus memiliki `snap-center` dan ukuran minimum. Tambahkan efek **scale + rotate** saat hover:

```html
<div class="snap-center shrink-0 w-72 bg-gray-800 rounded-xl p-6 border border-gray-700 hover:scale-105 hover:-rotate-1 transition duration-300">
    <div class="w-full h-32 bg-blue-500/20 rounded-lg mb-4"></div>
    <h3 class="font-semibold mb-1">E-Commerce Platform</h3>
    <p class="text-sm text-gray-400">React, Node.js, PostgreSQL</p>
</div>
```

### 14. Carousel — slide kedua sampai kelima

Tambahkan 4 slide lagi dengan warna dan konten berbeda:

```html
<div class="snap-center shrink-0 w-72 bg-gray-800 rounded-xl p-6 border border-gray-700 hover:scale-105 hover:-rotate-1 transition duration-300">
    <div class="w-full h-32 bg-emerald-500/20 rounded-lg mb-4"></div>
    <h3 class="font-semibold mb-1">Analytics Dashboard</h3>
    <p class="text-sm text-gray-400">Vue.js, D3.js, Firebase</p>
</div>
<div class="snap-center shrink-0 w-72 bg-gray-800 rounded-xl p-6 border border-gray-700 hover:scale-105 hover:-rotate-1 transition duration-300">
    <div class="w-full h-32 bg-violet-500/20 rounded-lg mb-4"></div>
    <h3 class="font-semibold mb-1">Social Media App</h3>
    <p class="text-sm text-gray-400">Flutter, Dart, Supabase</p>
</div>
<div class="snap-center shrink-0 w-72 bg-gray-800 rounded-xl p-6 border border-gray-700 hover:scale-105 hover:-rotate-1 transition duration-300">
    <div class="w-full h-32 bg-amber-500/20 rounded-lg mb-4"></div>
    <h3 class="font-semibold mb-1">IoT Monitoring</h3>
    <p class="text-sm text-gray-400">Python, MQTT, InfluxDB</p>
</div>
<div class="snap-center shrink-0 w-72 bg-gray-800 rounded-xl p-6 border border-gray-700 hover:scale-105 hover:-rotate-1 transition duration-300">
    <div class="w-full h-32 bg-rose-500/20 rounded-lg mb-4"></div>
    <h3 class="font-semibold mb-1">AI Chatbot</h3>
    <p class="text-sm text-gray-400">Python, LangChain, OpenAI</p>
</div>
```

### 15. Form — heading

Di bawah carousel, tambahkan heading section untuk form:

```html
<h2 id="form" class="text-2xl font-bold mb-6">Create Project</h2>
```

### 16. Form — container

Buat container form dengan background gelap:

```html
<div class="bg-gray-800 rounded-xl p-6 border border-gray-700 mb-12">
    <form class="space-y-5">
        <!-- langkah selanjutnya di sini -->
    </form>
</div>
```

### 17. Form — input teks dengan caret color

Di dalam form, buat field input teks. Gunakan `caret-violet-500` untuk mengubah warna kursor teks:

```html
<div>
    <label class="block text-sm text-gray-400 mb-2">Project Name</label>
    <input type="text" placeholder="Masukkan nama project..."
        class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2.5 text-white placeholder-gray-500 caret-violet-500 focus:outline-none focus:border-violet-500 transition duration-200">
</div>
```

### 18. Form — checkbox dengan accent color

Tambahkan checkbox dengan `accent-pink-500` untuk mengubah warna centang:

```html
<div class="flex items-center gap-3">
    <input type="checkbox" id="priority" class="w-4 h-4 accent-pink-500">
    <label for="priority" class="text-sm text-gray-300">High Priority</label>
    <input type="checkbox" id="public" class="w-4 h-4 accent-pink-500" checked>
    <label for="public" class="text-sm text-gray-300">Public Project</label>
</div>
```

### 19. Form — textarea dengan resize

Tambahkan textarea dengan `resize-y` agar hanya bisa di-resize secara vertikal:

```html
<div>
    <label class="block text-sm text-gray-400 mb-2">Description</label>
    <textarea rows="3" placeholder="Deskripsi project..."
        class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2.5 text-white placeholder-gray-500 caret-violet-500 resize-y focus:outline-none focus:border-violet-500 transition duration-200"></textarea>
</div>
```

### 20. Form — tombol submit dengan loading spinner

Tambahkan tombol submit. Di sebelah teks, tambahkan ikon spinner menggunakan `animate-spin`:

```html
<button type="button"
    class="bg-violet-600 text-white font-semibold px-6 py-2.5 rounded-lg hover:bg-violet-700 active:scale-95 transition duration-200 flex items-center gap-2">
    <svg class="animate-spin h-4 w-4" viewBox="0 0 24 24" fill="none">
        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4z"></path>
    </svg>
    Saving...
</button>
```

---

## Hasil yang Diharapkan

```
┌─────────────────────────────────────────────────────┐
│  Dashboard              Stats  Projects  Form       │  ← navbar, select-none
├─────────────────────────────────────────────────────┤
│                                                     │
│  Overview                                           │  ← animate-slide-up
│                                                     │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐│
│  │ Total Revenue│ │ Active Users │ │ Growth Rate  ││
│  │ Rp 124.5jt  │ │ 1,847    ●   │ │ 23.8%       ││  ← pulse, ping, bounce
│  │ +12.5%      │ │ Online      │ │ ↑ Trending   ││
│  └──────────────┘ └──────────────┘ └──────────────┘│
│                                                     │
│  Recent Projects                                    │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌──→ │
│  │ E-Com  │ │ Analyt │ │ Social │ │ IoT    │ │ AI │  ← snap-x, snap-center
│  │ React..│ │ Vue... │ │ Flutt..│ │ Pyth...│ │ Py │     cursor-grab
│  └────────┘ └────────┘ └────────┘ └────────┘ └──→ │     hover: scale+rotate
│                                                     │
│  Create Project                                     │
│  ┌─────────────────────────────────────────────────┐│
│  │ Project Name: [__________________|]             ││  ← caret-violet-500
│  │ ☑ High Priority  ☑ Public Project              ││  ← accent-pink-500
│  │ Description: [                    ]             ││  ← resize-y
│  │ [⟳ Saving...]                                  ││  ← animate-spin
│  └─────────────────────────────────────────────────┘│
│                                                     │
└─────────────────────────────────────────────────────┘
```

---

## Checklist Penyelesaian

### Custom Animation
- [ ] Ada block `<style type="text/tailwindcss">` dengan `@theme` dan `@keyframes`
- [ ] Mendefinisikan `animate-fade-in` dan `animate-slide-up`
- [ ] Container utama menggunakan `animate-fade-in`
- [ ] Heading stats menggunakan `animate-slide-up`

### Navbar & Smooth Scroll
- [ ] Tag `<html>` memiliki `scroll-smooth`
- [ ] Navbar menggunakan `select-none`
- [ ] Link navbar menggunakan `href="#id"` untuk smooth-scroll

### Stats Bar
- [ ] Ada 3 kartu stats dalam `grid grid-cols-3 gap-6`
- [ ] Kartu pertama menggunakan `animate-pulse` pada angka
- [ ] Kartu kedua memiliki titik dengan `animate-ping`
- [ ] Kartu ketiga memiliki panah dengan `animate-bounce`

### Scroll-Snap Carousel
- [ ] Container menggunakan `snap-x snap-mandatory` dan `overflow-x-auto`
- [ ] Setiap slide menggunakan `snap-center` dan `shrink-0`
- [ ] Container menggunakan `cursor-grab active:cursor-grabbing`
- [ ] Slide memiliki `hover:scale-105 hover:-rotate-1` dengan `transition duration-300`

### Form Interaktif
- [ ] Input teks menggunakan `caret-violet-500`
- [ ] Checkbox menggunakan `accent-pink-500`
- [ ] Textarea menggunakan `resize-y`
- [ ] Tombol submit memiliki spinner `animate-spin` (SVG)

### Umum
- [ ] File HTML memiliki boilerplate lengkap dan Play CDN Tailwind CSS v4
- [ ] Semua transisi menggunakan `transition duration-*`

---
