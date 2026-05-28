# KeuanganKu 💰
**Aplikasi pencatatan keuangan pribadi** — React + Vite + Tailwind CSS

---

## 📦 Instalasi & Menjalankan

### Prasyarat
- Node.js v18 atau lebih baru
- npm v9+

### Langkah instalasi

```bash
# 1. Masuk ke folder project
cd keuanganku

# 2. Install semua dependency
npm install

# 3. Jalankan development server
npm run dev
```

Buka browser di **http://localhost:5173**

### Build untuk produksi

```bash
npm run build       # Menghasilkan folder dist/
npm run preview     # Preview hasil build
```

---

## 📁 Struktur File

```
keuanganku/
├── index.html                  # Entry HTML
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
└── src/
    ├── main.jsx                # Entry React
    ├── App.jsx                 # Root component & routing
    ├── index.css               # Tailwind + custom CSS
    │
    ├── constants/
    │   ├── categories.js       # Daftar CoA default (23 kategori)
    │   └── months.js           # Nama bulan & helper fungsi
    │
    ├── utils/
    │   ├── format.js           # formatRp, formatDate, generateId
    │   └── storage.js          # Adapter localStorage (mudah diganti API)
    │
    ├── hooks/
    │   ├── useTransactions.js  # State & logic semua transaksi
    │   └── useCategories.js    # State & logic kategori
    │
    ├── components/
    │   ├── Layout/
    │   │   ├── Sidebar.jsx     # Navigasi desktop
    │   │   └── BottomNav.jsx   # Navigasi mobile (bottom tab)
    │   ├── UI/
    │   │   ├── Modal.jsx       # Base modal + ConfirmDialog
    │   │   ├── StatCard.jsx    # Kartu metrik dashboard
    │   │   └── Toast.jsx       # Notifikasi toast + useToast hook
    │   └── Transaction/
    │       ├── TransactionRow.jsx    # Baris transaksi (list item)
    │       └── TransactionModal.jsx  # Form tambah / edit transaksi
    │
    └── pages/
        ├── Dashboard.jsx       # Halaman dashboard
        ├── Transactions.jsx    # Halaman daftar & filter transaksi
        ├── Categories.jsx      # Halaman manajemen kategori (CoA)
        └── Reports.jsx         # Halaman laporan & grafik tren
```

---

## ✨ Fitur Lengkap

| Fitur | Status |
|---|---|
| Dashboard: saldo, pemasukan, pengeluaran | ✅ |
| Grafik bar pemasukan vs pengeluaran (6 bulan) | ✅ |
| Ringkasan transaksi terbaru | ✅ |
| Tambah / Edit / Hapus transaksi | ✅ |
| Validasi form (nominal, kategori, tanggal) | ✅ |
| Filter: bulan, jenis, kategori, pencarian teks | ✅ |
| CoA default 23 kategori | ✅ |
| Tambah / Hapus kategori sendiri | ✅ |
| Laporan tren bulanan (line chart) | ✅ |
| Breakdown pengeluaran per kategori | ✅ |
| Tabel ringkasan bulanan | ✅ |
| Penyimpanan localStorage (persisten) | ✅ |
| Export CSV | ✅ |
| Export JSON | ✅ |
| Import JSON | ✅ |
| Responsive: desktop, tablet, mobile | ✅ |
| Format mata uang Rupiah (Rp) | ✅ |
| Notifikasi toast | ✅ |
| Animasi transisi | ✅ |

---

## 🔧 Migrasi ke Backend / Database

Semua operasi penyimpanan dipusatkan di **`src/utils/storage.js`**.  
Untuk pindah ke API (Express, Laravel, Supabase, dll.):

1. Ganti isi fungsi `getTransactions`, `saveTransactions`, `getCategories`, `saveCategories` dengan `fetch` / `axios`.
2. Hook `useTransactions` dan `useCategories` tidak perlu diubah.
3. Tambahkan loading state dan error handling di hook jika diperlukan.

---

## 🛠️ Tech Stack

- **React 18** — UI library
- **Vite 5** — Build tool & dev server
- **Tailwind CSS 3** — Utility-first styling
- **Recharts** — Grafik interaktif
- **Lucide React** — Icon set
- **Plus Jakarta Sans** — Font utama
- **localStorage** — Penyimpanan sisi browser

---

## 📝 Catatan

- Data tersimpan di localStorage browser — tidak hilang meski halaman ditutup.
- Gunakan fitur **Export JSON** untuk backup berkala.
- Gunakan **Import JSON** untuk memindahkan data antar browser/perangkat.
