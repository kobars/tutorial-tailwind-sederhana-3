# Latihan: Kartu Layanan Responsif

## Deskripsi

Kamu akan membuat halaman **kartu layanan** untuk perusahaan teknologi yang menampilkan:

- Heading responsif yang berubah ukuran di setiap breakpoint
- 4 kartu layanan dalam layout **grid responsif** (1 kolom → 2 kolom → 4 kolom)
- Setiap kartu: area ikon berwarna, judul layanan, dan deskripsi
- Efek **hover lift** dengan translate + shadow pada kartu
- Ikon yang **scale + rotate** saat kartu di-hover menggunakan `group`
- Tombol CTA dengan efek **scale** saat hover dan active
- **Padding responsif** yang bertambah di layar lebih besar

---

## Langkah-Langkah

### 1. Siapkan file HTML

Buat file baru `latihan-kartu-layanan.html` dengan boilerplate HTML dan Play CDN:

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kartu Layanan Responsif</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
</head>
<body>
    <!-- langkah selanjutnya di sini -->
</body>
</html>
```

### 2. Styling body

Pada `<body>`, berikan background abu-abu muda, tinggi minimum selayar penuh, dan **padding responsif** yang bertambah di layar lebih besar:

```html
<body class="bg-gray-50 min-h-screen p-4 md:p-8 lg:p-12">
```

### 3. Container utama

Di dalam body, buat container utama yang membatasi lebar konten dan memusatkannya:

```html
<div class="max-w-6xl mx-auto">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 4. Heading responsif

Di dalam container utama, tambahkan heading dengan ukuran font yang **berubah di setiap breakpoint**:

```html
<h1 class="text-2xl md:text-3xl lg:text-4xl font-bold text-gray-900 tracking-tight text-center mb-3">
    Layanan Kami
</h1>
```

### 5. Subtitle

Di bawah heading, tambahkan paragraf subtitle:

```html
<p class="text-gray-500 text-center max-w-xl mx-auto mb-12">
    Solusi teknologi terdepan untuk membantu bisnis Anda berkembang di era digital.
</p>
```

### 6. Container grid responsif

Buat layout grid yang berubah jumlah kolomnya: 1 kolom di mobile, 2 kolom di `sm`, dan 4 kolom di `lg`:

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 7. Kartu pertama — container dengan group

Buat kartu pertama. Gunakan class `group` agar child element bisa merespons hover pada kartu. Tambahkan efek **hover lift** — kartu terangkat ke atas dan shadow membesar saat hover:

```html
<div class="group bg-white rounded-xl p-6 shadow-md hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <!-- langkah selanjutnya di sini -->
</div>
```

### 8. Kartu pertama — area ikon

Di dalam kartu, buat area ikon berwarna dengan emoji sebagai placeholder. Area ikon akan **scale + rotate** saat kartu di-hover menggunakan `group-hover`:

```html
<div class="w-14 h-14 bg-blue-100 text-blue-600 rounded-lg flex items-center justify-center text-2xl mb-4 group-hover:scale-110 group-hover:rotate-12 transition duration-300">
    💻
</div>
```

### 9. Kartu pertama — judul dan deskripsi

Di bawah area ikon, tambahkan judul layanan dan deskripsi:

```html
<h3 class="text-lg font-semibold text-gray-800 mb-2">Web Development</h3>
<p class="text-sm text-gray-500">Membangun website modern dan responsif dengan teknologi terbaru.</p>
```

### 10. Kartu kedua

Buat kartu kedua dengan warna dan konten berbeda. Strukturnya sama seperti kartu pertama:

```html
<div class="group bg-white rounded-xl p-6 shadow-md hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <div class="w-14 h-14 bg-emerald-100 text-emerald-600 rounded-lg flex items-center justify-center text-2xl mb-4 group-hover:scale-110 group-hover:rotate-12 transition duration-300">
        📱
    </div>
    <h3 class="text-lg font-semibold text-gray-800 mb-2">Mobile App</h3>
    <p class="text-sm text-gray-500">Aplikasi mobile cross-platform untuk iOS dan Android.</p>
</div>
```

### 11. Kartu ketiga

```html
<div class="group bg-white rounded-xl p-6 shadow-md hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <div class="w-14 h-14 bg-violet-100 text-violet-600 rounded-lg flex items-center justify-center text-2xl mb-4 group-hover:scale-110 group-hover:rotate-12 transition duration-300">
        ☁️
    </div>
    <h3 class="text-lg font-semibold text-gray-800 mb-2">Cloud Service</h3>
    <p class="text-sm text-gray-500">Infrastruktur cloud yang scalable dan aman untuk bisnis Anda.</p>
</div>
```

### 12. Kartu keempat

```html
<div class="group bg-white rounded-xl p-6 shadow-md hover:-translate-y-2 hover:shadow-xl transition duration-300">
    <div class="w-14 h-14 bg-amber-100 text-amber-600 rounded-lg flex items-center justify-center text-2xl mb-4 group-hover:scale-110 group-hover:rotate-12 transition duration-300">
        🔒
    </div>
    <h3 class="text-lg font-semibold text-gray-800 mb-2">Cyber Security</h3>
    <p class="text-sm text-gray-500">Proteksi data dan keamanan sistem dari ancaman siber.</p>
</div>
```

### 13. Tombol CTA

Di bawah container grid (masih di dalam container utama), tambahkan tombol CTA yang **membesar saat hover** dan **mengecil saat active**:

```html
<div class="text-center mt-12">
    <button class="bg-blue-600 text-white font-semibold px-8 py-3 rounded-lg hover:scale-105 active:scale-95 transition duration-200">
        Konsultasi Gratis
    </button>
</div>
```

---

## Hasil yang Diharapkan

```
                                                          ← p-4 (mobile)
                                                          ← md:p-8 (tablet)
                                                          ← lg:p-12 (desktop)
                Layanan Kami                               ← text-2xl / md:3xl / lg:4xl
    Solusi teknologi terdepan...

  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ 💻       │  │ 📱       │  │ ☁️       │  │ 🔒       │ ← ikon scale+rotate
  │ Web Dev  │  │ Mobile   │  │ Cloud    │  │ Security │   saat hover kartu
  │ desc...  │  │ desc...  │  │ desc...  │  │ desc...  │
  └──────────┘  └──────────┘  └──────────┘  └──────────┘
        ↑ hover: -translate-y-2 + shadow-xl

              [Konsultasi Gratis]                         ← hover:scale-105
                                                            active:scale-95
```

**Tampilan responsif:**
```
Mobile (< 640px):           sm (≥ 640px):          lg (≥ 1024px):
┌──────────────┐         ┌───────┐ ┌───────┐      ┌────┐ ┌────┐ ┌────┐ ┌────┐
│   Kartu 1    │         │   1   │ │   2   │      │ 1  │ │ 2  │ │ 3  │ │ 4  │
├──────────────┤         ├───────┤ ├───────┤      └────┘ └────┘ └────┘ └────┘
│   Kartu 2    │         │   3   │ │   4   │
├──────────────┤         └───────┘ └───────┘
│   Kartu 3    │
├──────────────┤
│   Kartu 4    │
└──────────────┘
```

---

## Checklist Penyelesaian

### Responsive
- [ ] Body memiliki padding responsif: `p-4 md:p-8 lg:p-12`
- [ ] Heading menggunakan ukuran responsif: `text-2xl md:text-3xl lg:text-4xl`
- [ ] Grid menggunakan kolom responsif: `grid-cols-1 sm:grid-cols-2 lg:grid-cols-4`

### Kartu Layanan
- [ ] Ada 4 kartu layanan dengan ikon, judul, dan deskripsi
- [ ] Setiap kartu menggunakan `group` untuk mengendalikan child saat hover
- [ ] Kartu memiliki `shadow-md` dan `rounded-xl`
- [ ] Area ikon menggunakan `group-hover:scale-110 group-hover:rotate-12` dengan `transition duration-300`

### Transition & Transform
- [ ] Kartu memiliki efek hover lift: `hover:-translate-y-2 hover:shadow-xl transition duration-300`
- [ ] Tombol CTA memiliki `hover:scale-105` dan `active:scale-95` dengan `transition duration-200`

### Umum
- [ ] File HTML memiliki boilerplate lengkap dan Play CDN Tailwind CSS v4
- [ ] Layout berubah sesuai breakpoint saat browser di-resize

---
