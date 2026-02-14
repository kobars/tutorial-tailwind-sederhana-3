# Latihan: Landing Page Event Teknologi

## Deskripsi

- **Custom styles:** `@theme` untuk custom animation, `@keyframes`, dan `@layer components` dengan `@apply` untuk reusable button classes
- **Responsive navbar:** horizontal di desktop (`hidden md:flex`), ikon hamburger di mobile (`md:hidden`), teks `select-none`
- **Hero section:** layout responsif `flex-col md:flex-row`, ukuran font responsif, tombol custom `.btn-event`, indikator scroll `animate-bounce`
- **Speakers section:** grid responsif `grid-cols-1 sm:grid-cols-2 lg:grid-cols-4`, kartu dengan `hover:-translate-y-2`, ikon `group-hover:rotate-6 group-hover:scale-110`
- **Schedule section:** background miring (`skew-y-2` / `-skew-y-2`), layout responsif `flex-col md:flex-row`, aksen `border-l`
- **Sponsors carousel:** `snap-x snap-mandatory`, `cursor-grab active:cursor-grabbing`, `hover:scale-105`
- **Registration form:** `caret-color`, `accent-color`, `resize-y`, tombol loading dengan `animate-spin` + `cursor-not-allowed pointer-events-none`
- **Footer:** grid responsif `grid-cols-1 md:grid-cols-2 lg:grid-cols-4`, copyright `select-none`

---

## Langkah-Langkah

### 1. Siapkan file HTML

Buat file baru `latihan-landing-page-event.html` dengan boilerplate HTML dan Play CDN. Tambahkan `scroll-smooth` pada tag `<html>`:

```html
<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechFest 2026</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
</head>
<body>
    <!-- langkah selanjutnya di sini -->
</body>
</html>
```

### 2. Custom styles — @theme dan @keyframes

Di dalam `<head>`, tambahkan `<style type="text/tailwindcss">` untuk mendefinisikan custom animation:

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
        from { opacity: 0; transform: translateY(30px); }
        to { opacity: 1; transform: translateY(0); }
    }
</style>
```

### 3. Custom styles — @layer components dengan @apply

Di dalam block `<style>` yang sama, tambahkan `@layer components` untuk membuat reusable button classes menggunakan `@apply`:

```css
@layer components {
    .btn-event {
        @apply inline-block bg-violet-600 text-white font-semibold px-6 py-3 rounded-lg hover:bg-violet-700 hover:scale-105 active:scale-95 transition duration-200;
    }
    .btn-event-outline {
        @apply inline-block border-2 border-white text-white font-semibold px-6 py-3 rounded-lg hover:bg-white hover:text-violet-900 hover:scale-105 active:scale-95 transition duration-200;
    }
}
```

### 4. Styling body

Pada `<body>`, berikan background putih, font anti-aliased, dan custom animation:

```html
<body class="bg-white antialiased animate-fade-in">
```

### 5. Navbar — container

Buat navbar responsif. Di mobile hanya tampil logo dan ikon hamburger, di desktop tampil menu horizontal:

```html
<nav class="bg-white/80 backdrop-blur-md border-b border-gray-200 sticky top-0 z-50 select-none">
    <div class="max-w-6xl mx-auto px-4 md:px-6 flex justify-between items-center h-16">
        <!-- langkah selanjutnya di sini -->
    </div>
</nav>
```

### 6. Navbar — logo

Di dalam container navbar, tambahkan logo:

```html
<span class="text-xl font-bold text-violet-700 tracking-tight">TechFest 2026</span>
```

### 7. Navbar — menu desktop

Di sebelah kanan, tambahkan menu navigasi yang hanya tampil di `md` ke atas. Gunakan `hidden md:flex`:

```html
<div class="hidden md:flex gap-6">
    <a href="#speakers" class="text-sm text-gray-600 hover:text-violet-700 transition-colors duration-200">Speakers</a>
    <a href="#schedule" class="text-sm text-gray-600 hover:text-violet-700 transition-colors duration-200">Schedule</a>
    <a href="#sponsors" class="text-sm text-gray-600 hover:text-violet-700 transition-colors duration-200">Sponsors</a>
    <a href="#register" class="text-sm text-gray-600 hover:text-violet-700 transition-colors duration-200">Register</a>
</div>
```

### 8. Navbar — ikon hamburger mobile

Setelah menu desktop, tambahkan ikon hamburger yang hanya tampil di mobile. Gunakan `md:hidden`:

```html
<div class="md:hidden text-2xl text-gray-600 cursor-pointer">☰</div>
```

### 9. Hero section — container

Di bawah navbar, buat section hero dengan background gradient dan layout responsif `flex-col md:flex-row`:

```html
<section class="bg-gradient-to-br from-violet-900 via-purple-800 to-indigo-900 py-16 md:py-24 px-4 md:px-6">
    <div class="max-w-6xl mx-auto flex flex-col md:flex-row items-center gap-8 md:gap-12">
        <!-- langkah selanjutnya di sini -->
    </div>
</section>
```

### 10. Hero — konten teks (kiri)

Di dalam flex container hero, buat kolom teks yang memenuhi separuh lebar di desktop:

```html
<div class="flex-1 text-center md:text-left animate-slide-up">
    <p class="text-violet-300 text-sm md:text-base font-semibold uppercase tracking-widest mb-4">15 — 17 Agustus 2026 • Jakarta</p>
    <h1 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-bold text-white tracking-tight mb-6">
        The Future of<br>Technology
    </h1>
    <p class="text-base md:text-lg text-white/70 leading-relaxed mb-8 max-w-lg mx-auto md:mx-0">
        3 hari konferensi teknologi terbesar di Indonesia. Workshop, keynote, dan networking dengan para pemimpin industri.
    </p>
    <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start">
        <a href="#register" class="btn-event">Daftar Sekarang</a>
        <a href="#schedule" class="btn-event-outline">Lihat Jadwal</a>
    </div>
</div>
```

### 11. Hero — visual placeholder (kanan)

Di sebelah kanan, buat area visual placeholder:

```html
<div class="flex-1 flex justify-center">
    <div class="w-64 h-64 md:w-80 md:h-80 bg-gradient-to-br from-violet-500 to-fuchsia-500 rounded-3xl rotate-6 shadow-2xl shadow-violet-500/30"></div>
</div>
```

### 12. Hero — indikator scroll bounce

Di bawah flex container hero (tapi masih di dalam section), tambahkan indikator scroll:

```html
<div class="text-center mt-8">
    <span class="inline-block animate-bounce text-white/50 text-2xl">↓</span>
</div>
```

> **Catatan:** Letakkan `<div>` ini **setelah** penutup `</div>` container flex, tapi **sebelum** penutup `</section>`.

### 13. Speakers section — heading

Di bawah hero, buat section speakers:

```html
<section id="speakers" class="py-16 md:py-20 px-4 md:px-6">
    <div class="max-w-6xl mx-auto">
        <h2 class="text-2xl md:text-3xl font-bold text-gray-900 text-center tracking-tight mb-3">Speakers</h2>
        <p class="text-gray-500 text-center max-w-xl mx-auto mb-12">
            Para ahli dan visioner yang akan berbagi pengetahuan di TechFest 2026.
        </p>
        <!-- langkah selanjutnya di sini -->
    </div>
</section>
```

### 14. Speakers — grid responsif

Buat grid responsif yang berubah dari 1 kolom di mobile, 2 kolom di `sm`, hingga 4 kolom di `lg`:

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 15. Speakers — kartu pertama

Buat kartu speaker pertama dengan `group`. Avatar placeholder menggunakan `group-hover:rotate-6 group-hover:scale-110`. Kartu terangkat saat hover:

```html
<div class="group bg-white rounded-xl p-6 shadow-md text-center hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <div class="w-20 h-20 bg-violet-100 rounded-full mx-auto mb-4 flex items-center justify-center text-3xl group-hover:rotate-6 group-hover:scale-110 transition duration-300">
        👩‍💻
    </div>
    <h3 class="font-semibold text-gray-800">Sarah Chen</h3>
    <p class="text-sm text-violet-600">AI & Machine Learning</p>
    <p class="text-xs text-gray-400 mt-1">CTO, TechVision</p>
</div>
```

### 16. Speakers — kartu kedua sampai keempat

Tambahkan 3 kartu speaker lagi:

```html
<div class="group bg-white rounded-xl p-6 shadow-md text-center hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <div class="w-20 h-20 bg-emerald-100 rounded-full mx-auto mb-4 flex items-center justify-center text-3xl group-hover:rotate-6 group-hover:scale-110 transition duration-300">
        👨‍🔬
    </div>
    <h3 class="font-semibold text-gray-800">Budi Santoso</h3>
    <p class="text-sm text-violet-600">Cloud Architecture</p>
    <p class="text-xs text-gray-400 mt-1">VP Engineering, CloudID</p>
</div>
<div class="group bg-white rounded-xl p-6 shadow-md text-center hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <div class="w-20 h-20 bg-amber-100 rounded-full mx-auto mb-4 flex items-center justify-center text-3xl group-hover:rotate-6 group-hover:scale-110 transition duration-300">
        👩‍🎨
    </div>
    <h3 class="font-semibold text-gray-800">Lisa Wijaya</h3>
    <p class="text-sm text-violet-600">UI/UX Design</p>
    <p class="text-xs text-gray-400 mt-1">Design Lead, Kreativa</p>
</div>
<div class="group bg-white rounded-xl p-6 shadow-md text-center hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <div class="w-20 h-20 bg-rose-100 rounded-full mx-auto mb-4 flex items-center justify-center text-3xl group-hover:rotate-6 group-hover:scale-110 transition duration-300">
        👨‍💼
    </div>
    <h3 class="font-semibold text-gray-800">Andi Pratama</h3>
    <p class="text-sm text-violet-600">Cybersecurity</p>
    <p class="text-xs text-gray-400 mt-1">Founder, SecureNusa</p>
</div>
```

### 17. Schedule section — container dengan skew

Di bawah speakers, buat section schedule dengan **background miring** menggunakan `skew-y-2`. Konten di dalam perlu di-counter dengan `-skew-y-2` agar teks tetap lurus:

```html
<section id="schedule" class="bg-violet-900 py-20 md:py-24 px-4 md:px-6 skew-y-2">
    <div class="-skew-y-2">
        <div class="max-w-6xl mx-auto">
            <h2 class="text-2xl md:text-3xl font-bold text-white text-center tracking-tight mb-3">Schedule</h2>
            <p class="text-violet-300 text-center max-w-xl mx-auto mb-12">
                Tiga hari penuh inspirasi dan pembelajaran.
            </p>
            <!-- langkah selanjutnya di sini -->
        </div>
    </div>
</section>
```

### 18. Schedule — layout 3 hari responsif

Di dalam container, buat layout responsif `flex-col md:flex-row` untuk menampilkan 3 hari:

```html
<div class="flex flex-col md:flex-row gap-6">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 19. Schedule — hari pertama

Buat card hari pertama. Setiap item menggunakan `border-l` berwarna sebagai aksen:

```html
<div class="flex-1 bg-white/10 backdrop-blur-sm rounded-xl p-6 border border-white/10">
    <h3 class="text-lg font-bold text-white mb-4">Hari 1 — 15 Agustus</h3>
    <div class="space-y-4">
        <div class="border-l-4 border-violet-400 pl-4">
            <p class="text-sm text-violet-300">09:00 - 10:00</p>
            <p class="text-white font-medium">Opening Keynote</p>
        </div>
        <div class="border-l-4 border-violet-400 pl-4">
            <p class="text-sm text-violet-300">10:30 - 12:00</p>
            <p class="text-white font-medium">Workshop: AI Fundamentals</p>
        </div>
        <div class="border-l-4 border-violet-400 pl-4">
            <p class="text-sm text-violet-300">13:00 - 15:00</p>
            <p class="text-white font-medium">Panel: Future of Tech</p>
        </div>
    </div>
</div>
```

### 20. Schedule — hari kedua dan ketiga

Tambahkan 2 hari lagi:

```html
<div class="flex-1 bg-white/10 backdrop-blur-sm rounded-xl p-6 border border-white/10">
    <h3 class="text-lg font-bold text-white mb-4">Hari 2 — 16 Agustus</h3>
    <div class="space-y-4">
        <div class="border-l-4 border-fuchsia-400 pl-4">
            <p class="text-sm text-violet-300">09:00 - 11:00</p>
            <p class="text-white font-medium">Workshop: Cloud Native</p>
        </div>
        <div class="border-l-4 border-fuchsia-400 pl-4">
            <p class="text-sm text-violet-300">11:30 - 12:30</p>
            <p class="text-white font-medium">Talk: Design Systems</p>
        </div>
        <div class="border-l-4 border-fuchsia-400 pl-4">
            <p class="text-sm text-violet-300">14:00 - 16:00</p>
            <p class="text-white font-medium">Hackathon Kickoff</p>
        </div>
    </div>
</div>
<div class="flex-1 bg-white/10 backdrop-blur-sm rounded-xl p-6 border border-white/10">
    <h3 class="text-lg font-bold text-white mb-4">Hari 3 — 17 Agustus</h3>
    <div class="space-y-4">
        <div class="border-l-4 border-indigo-400 pl-4">
            <p class="text-sm text-violet-300">09:00 - 11:00</p>
            <p class="text-white font-medium">Hackathon Final</p>
        </div>
        <div class="border-l-4 border-indigo-400 pl-4">
            <p class="text-sm text-violet-300">11:30 - 12:30</p>
            <p class="text-white font-medium">Talk: Cybersecurity</p>
        </div>
        <div class="border-l-4 border-indigo-400 pl-4">
            <p class="text-sm text-violet-300">14:00 - 16:00</p>
            <p class="text-white font-medium">Closing & Awards</p>
        </div>
    </div>
</div>
```

### 21. Sponsors section — heading

Di bawah schedule, buat section sponsors:

```html
<section id="sponsors" class="py-16 md:py-20 px-4 md:px-6">
    <div class="max-w-6xl mx-auto">
        <h2 class="text-2xl md:text-3xl font-bold text-gray-900 text-center tracking-tight mb-3">Sponsors</h2>
        <p class="text-gray-500 text-center max-w-xl mx-auto mb-12">
            Didukung oleh perusahaan teknologi terkemuka.
        </p>
        <!-- langkah selanjutnya di sini -->
    </div>
</section>
```

### 22. Sponsors — scroll-snap carousel

Buat carousel horizontal dengan scroll-snap:

```html
<div class="flex gap-6 overflow-x-auto snap-x snap-mandatory pb-4 cursor-grab active:cursor-grabbing">
    <div class="snap-center shrink-0 w-48 h-24 bg-gray-100 rounded-xl flex items-center justify-center text-gray-400 font-bold hover:scale-105 transition duration-300">Sponsor 1</div>
    <div class="snap-center shrink-0 w-48 h-24 bg-gray-100 rounded-xl flex items-center justify-center text-gray-400 font-bold hover:scale-105 transition duration-300">Sponsor 2</div>
    <div class="snap-center shrink-0 w-48 h-24 bg-gray-100 rounded-xl flex items-center justify-center text-gray-400 font-bold hover:scale-105 transition duration-300">Sponsor 3</div>
    <div class="snap-center shrink-0 w-48 h-24 bg-gray-100 rounded-xl flex items-center justify-center text-gray-400 font-bold hover:scale-105 transition duration-300">Sponsor 4</div>
    <div class="snap-center shrink-0 w-48 h-24 bg-gray-100 rounded-xl flex items-center justify-center text-gray-400 font-bold hover:scale-105 transition duration-300">Sponsor 5</div>
    <div class="snap-center shrink-0 w-48 h-24 bg-gray-100 rounded-xl flex items-center justify-center text-gray-400 font-bold hover:scale-105 transition duration-300">Sponsor 6</div>
</div>
```

### 23. Registration section — heading

Di bawah sponsors, buat section registrasi:

```html
<section id="register" class="bg-gray-50 py-16 md:py-20 px-4 md:px-6">
    <div class="max-w-xl mx-auto">
        <h2 class="text-2xl md:text-3xl font-bold text-gray-900 text-center tracking-tight mb-3">Register</h2>
        <p class="text-gray-500 text-center mb-10">
            Amankan tempatmu di TechFest 2026. Kuota terbatas!
        </p>
        <!-- langkah selanjutnya di sini -->
    </div>
</section>
```

### 24. Registration — form container

Buat form container:

```html
<div class="bg-white rounded-xl shadow-md p-6 md:p-8">
    <form class="space-y-5">
        <!-- langkah selanjutnya di sini -->
    </form>
</div>
```

### 25. Registration — input nama dan email

Di dalam form, buat field input. Gunakan `caret-violet-500` untuk warna kursor:

```html
<div>
    <label class="block text-sm font-medium text-gray-700 mb-1">Nama Lengkap</label>
    <input type="text" placeholder="Masukkan nama lengkap..."
        class="w-full border border-gray-300 rounded-lg px-4 py-2.5 text-gray-800 placeholder-gray-400 caret-violet-500 focus:outline-none focus:border-violet-500 transition duration-200">
</div>
<div>
    <label class="block text-sm font-medium text-gray-700 mb-1">Email</label>
    <input type="email" placeholder="email@example.com"
        class="w-full border border-gray-300 rounded-lg px-4 py-2.5 text-gray-800 placeholder-gray-400 caret-violet-500 focus:outline-none focus:border-violet-500 transition duration-200">
</div>
```

### 26. Registration — checkbox dengan accent color

Tambahkan checkbox pilihan workshop menggunakan `accent-violet-500`:

```html
<div>
    <label class="block text-sm font-medium text-gray-700 mb-2">Pilih Workshop</label>
    <div class="space-y-2">
        <label class="flex items-center gap-2">
            <input type="checkbox" class="w-4 h-4 accent-violet-500">
            <span class="text-sm text-gray-600">AI & Machine Learning</span>
        </label>
        <label class="flex items-center gap-2">
            <input type="checkbox" class="w-4 h-4 accent-violet-500">
            <span class="text-sm text-gray-600">Cloud Native Development</span>
        </label>
        <label class="flex items-center gap-2">
            <input type="checkbox" class="w-4 h-4 accent-violet-500">
            <span class="text-sm text-gray-600">UI/UX Design Workshop</span>
        </label>
    </div>
</div>
```

### 27. Registration — textarea dengan resize-y

Tambahkan textarea untuk pesan. Gunakan `resize-y` agar hanya bisa di-resize vertikal:

```html
<div>
    <label class="block text-sm font-medium text-gray-700 mb-1">Pesan (Opsional)</label>
    <textarea rows="3" placeholder="Ada yang ingin ditanyakan?"
        class="w-full border border-gray-300 rounded-lg px-4 py-2.5 text-gray-800 placeholder-gray-400 caret-violet-500 resize-y focus:outline-none focus:border-violet-500 transition duration-200"></textarea>
</div>
```

### 28. Registration — tombol submit loading state

Buat tombol submit dengan state loading: spinner `animate-spin`, `cursor-not-allowed`, dan `pointer-events-none`:

```html
<button type="button"
    class="w-full bg-violet-400 text-white font-semibold py-3 rounded-lg cursor-not-allowed pointer-events-none flex items-center justify-center gap-2">
    <svg class="animate-spin h-5 w-5" viewBox="0 0 24 24" fill="none">
        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4z"></path>
    </svg>
    Mendaftar...
</button>
```

### 29. Footer — container dan grid responsif

Di bawah registrasi, buat footer dengan grid responsif:

```html
<footer class="bg-gray-900 py-12 px-4 md:px-6">
    <div class="max-w-6xl mx-auto">
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
            <!-- langkah selanjutnya di sini -->
        </div>
    </div>
</footer>
```

### 30. Footer — 4 kolom konten

Di dalam grid footer, buat 4 kolom:

```html
<div>
    <h3 class="text-lg font-bold text-white mb-3">TechFest 2026</h3>
    <p class="text-sm text-white/50 leading-relaxed">
        Konferensi teknologi terbesar di Indonesia. 3 hari penuh inspirasi.
    </p>
</div>
<div>
    <h3 class="text-lg font-bold text-white mb-3">Quick Links</h3>
    <div class="space-y-2">
        <a href="#speakers" class="block text-sm text-white/50 hover:text-white transition-colors duration-200">Speakers</a>
        <a href="#schedule" class="block text-sm text-white/50 hover:text-white transition-colors duration-200">Schedule</a>
        <a href="#register" class="block text-sm text-white/50 hover:text-white transition-colors duration-200">Register</a>
    </div>
</div>
<div>
    <h3 class="text-lg font-bold text-white mb-3">Venue</h3>
    <div class="space-y-2">
        <p class="text-sm text-white/50">Jakarta Convention Center</p>
        <p class="text-sm text-white/50">Jl. Jenderal Gatot Subroto</p>
        <p class="text-sm text-white/50">Jakarta Selatan, 12930</p>
    </div>
</div>
<div>
    <h3 class="text-lg font-bold text-white mb-3">Contact</h3>
    <div class="space-y-2">
        <p class="text-sm text-white/50">info@techfest2026.id</p>
        <p class="text-sm text-white/50">021-555-2026</p>
        <p class="text-sm text-white/50">@techfest2026</p>
    </div>
</div>
```

### 31. Footer — copyright

Di bawah grid footer (masih di dalam container), tambahkan copyright dengan `select-none`:

```html
<div class="border-t border-gray-700 mt-8 pt-8 text-center select-none">
    <p class="text-sm text-white opacity-40">2026 TechFest. All rights reserved.</p>
</div>
```

---

## Hasil yang Diharapkan

```
┌───────────────────────────────────────────────────────┐
│  TechFest 2026    Speakers Schedule Sponsors Register │  ← hidden md:flex
│                                               ☰       │  ← md:hidden (mobile)
├───────────────────────────────────────────────────────┤
│▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│▓ 15-17 Agustus 2026              ┌─────────────┐   ▓│
│▓ The Future of                   │             │   ▓│  ← flex-col md:flex-row
│▓ Technology                      │   rotate-6  │   ▓│     responsive font sizes
│▓ 3 hari konferensi...            │             │   ▓│
│▓ [Daftar Sekarang] [Lihat Jadwal]└─────────────┘   ▓│  ← .btn-event, @apply
│▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ ↓ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│  ← animate-bounce
├─────────────────────────────────────────────────────┤
│                   Speakers                          │
│  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐     │
│  │  👩‍💻    │  │  👨‍🔬    │  │  👩‍🎨    │  │  👨‍💼    │     │  ← grid-cols-1/2/4
│  │ Sarah  │  │ Budi   │  │ Lisa   │  │ Andi   │     │     hover:-translate-y-2
│  │ AI/ML  │  │ Cloud  │  │ UI/UX  │  │ Cyber  │     │     group-hover:rotate+scale
│  └────────┘  └────────┘  └────────┘  └────────┘     │
├──────────╱──────────────────────────────╲───────────┤
│▓▓▓▓▓▓▓▓▓           Schedule           ▓▓▓▓▓▓▓▓▓▓▓▓▓▓│  ← skew-y-2 / -skew-y-2
│▓ ┌──────────┐  ┌──────────┐  ┌──────────┐          ▓│
│▓ │ Hari 1   │  │ Hari 2   │  │ Hari 3   │          ▓│  ← flex-col md:flex-row
│▓ │▎09:00    │  │▎09:00    │  │▎09:00    │          ▓│     border-l-4 accents
│▓ │▎Keynote  │  │▎Cloud    │  │▎Hackathon│          ▓│
│▓ └──────────┘  └──────────┘  └──────────┘          ▓│
├──────────╲──────────────────────────────╱───────────┤
│                   Sponsors                          │
│  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐ ──→   │  ← snap-x, cursor-grab
│  │ Sp 1 │ │ Sp 2 │ │ Sp 3 │ │ Sp 4 │ │ Sp 5 │       │     hover:scale-105
│  └──────┘ └──────┘ └──────┘ └──────┘ └──────┘       │
├─────────────────────────────────────────────────────┤
│░░░░░░░░░░░░░░░ Register ░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
│░░ ┌─────────────────────────────────────────────┐ ░░│
│░░ │ Nama: [_________________]                   │ ░░│  ← caret-violet-500
│░░ │ Email: [________________]                   │ ░░│
│░░ │ ☑ AI/ML  ☑ Cloud  ☐ UI/UX                   │ ░░│  ← accent-violet-500
│░░ │ Pesan: [                 ]                  │ ░░│  ← resize-y
│░░ │ [⟳ Mendaftar...]                            │ ░░│  ← spin + cursor-not-allowed
│░░ └─────────────────────────────────────────────┘ ░░│
├─────────────────────────────────────────────────────┤
│▓ TechFest │ Quick    │ Venue    │ Contact          ▓│  ← grid-cols-1/2/4
│▓ 2026     │ Links    │ JCC      │ email            ▓│
│▓ desc..   │ Speakers │ Jl. Gatot│ 021-555-2026     ▓│
│▓ ───────────────────────────────────────────────── ▓│
│▓           2026 TechFest. All rights reserved.     ▓│  ← select-none
└─────────────────────────────────────────────────────┘
```

---

## Checklist Penyelesaian

### Custom Styles (@theme, @apply, @layer)
- [ ] Ada `<style type="text/tailwindcss">` di `<head>`
- [ ] `@theme` mendefinisikan `animate-fade-in` dan `animate-slide-up`
- [ ] `@keyframes` untuk `fade-in` dan `slide-up` didefinisikan
- [ ] `@layer components` membuat `.btn-event` dan `.btn-event-outline` menggunakan `@apply`
- [ ] Tombol hero menggunakan class `.btn-event` dan `.btn-event-outline`

### Responsive Navbar
- [ ] Menu desktop menggunakan `hidden md:flex`
- [ ] Ikon hamburger menggunakan `md:hidden`
- [ ] Navbar menggunakan `select-none` dan `sticky top-0`
- [ ] Link navbar menggunakan `href="#id"` untuk smooth-scroll
- [ ] Tag `<html>` memiliki `scroll-smooth`

### Hero Section
- [ ] Layout menggunakan `flex-col md:flex-row`
- [ ] Heading menggunakan ukuran responsif: `text-3xl sm:text-4xl md:text-5xl lg:text-6xl`
- [ ] Ada indikator scroll dengan `animate-bounce`
- [ ] Body atau konten menggunakan `animate-fade-in`

### Speakers Section
- [ ] Grid responsif: `grid-cols-1 sm:grid-cols-2 lg:grid-cols-4`
- [ ] Kartu menggunakan `group` dengan `hover:-translate-y-2 hover:shadow-xl`
- [ ] Avatar menggunakan `group-hover:rotate-6 group-hover:scale-110`

### Schedule Section
- [ ] Section menggunakan `skew-y-2` dan konten menggunakan `-skew-y-2`
- [ ] Layout menggunakan `flex-col md:flex-row`
- [ ] Item jadwal menggunakan `border-l-4` sebagai aksen

### Sponsors Carousel
- [ ] Container menggunakan `snap-x snap-mandatory` dan `overflow-x-auto`
- [ ] Setiap item menggunakan `snap-center` dan `shrink-0`
- [ ] Container menggunakan `cursor-grab active:cursor-grabbing`
- [ ] Item memiliki `hover:scale-105`

### Registration Form
- [ ] Input menggunakan `caret-violet-500`
- [ ] Checkbox menggunakan `accent-violet-500`
- [ ] Textarea menggunakan `resize-y`
- [ ] Tombol submit menampilkan spinner `animate-spin`
- [ ] Tombol submit menggunakan `cursor-not-allowed` dan `pointer-events-none`

### Footer
- [ ] Grid responsif: `grid-cols-1 md:grid-cols-2 lg:grid-cols-4`
- [ ] Copyright menggunakan `select-none`
- [ ] Ada `border-t border-gray-700` sebagai pemisah

---
