# TabunganKu PWA

Aplikasi pencatatan keuangan pribadi berbasis Progressive Web App (PWA).  
Bisa di-install di HP & desktop, bekerja offline, dan sync ke Google Sheets via API Key.

---

## Fitur
- ✅ Catat pemasukan & pengeluaran dengan kategori
- ✅ Simpan lokal di browser (IndexedStorage / localStorage)
- ✅ Sync otomatis ke Google Sheets via API Key
- ✅ Export CSV
- ✅ Laporan grafik (donut & bar chart)
- ✅ Filter riwayat per bulan & kategori
- ✅ Bisa di-install sebagai aplikasi (PWA)
- ✅ Bekerja offline

---

## Deploy ke Vercel (Gratis, 5 Menit)

### Cara 1 — Via Website (Paling Mudah)
1. Buka [vercel.com](https://vercel.com) → Sign up gratis (pakai GitHub/Google)
2. Klik **Add New → Project**
3. Pilih **"Deploy from your computer"** atau drag & drop folder `tabunganku-pwa`
4. Klik **Deploy**
5. Selesai! Kamu dapat URL seperti `https://tabunganku.vercel.app`

### Cara 2 — Via CLI
```bash
npm i -g vercel
cd tabunganku-pwa
vercel
```

---

## Setup Google Sheets Sync

### Langkah 1 — Aktifkan Google Sheets API
1. Buka [console.cloud.google.com](https://console.cloud.google.com)
2. Buat project baru (atau pakai yang sudah ada)
3. Menu → **APIs & Services → Library**
4. Cari **"Google Sheets API"** → klik **Enable**

### Langkah 2 — Buat API Key
1. Menu → **APIs & Services → Credentials**
2. **Create Credentials → API Key**
3. Copy API Key yang muncul
4. (Opsional tapi disarankan) Klik **Edit API Key** → restrict ke Google Sheets API

### Langkah 3 — Siapkan Google Spreadsheet
1. Buka [sheets.google.com](https://sheets.google.com) → buat spreadsheet baru
2. **PENTING**: Klik **Share** → **Anyone with the link → Editor**  
   (agar API Key bisa menulis data)
3. Copy **ID** dari URL:
   ```
   https://docs.google.com/spreadsheets/d/[COPY_BAGIAN_INI]/edit
   ```

### Langkah 4 — Hubungkan di Aplikasi
1. Buka TabunganKu
2. Tap ikon ⚙️ di kanan atas
3. Isi API Key, Spreadsheet ID, dan nama tab (default: `Transaksi`)
4. Klik **Simpan & Hubungkan**

---

## Cara Install sebagai Aplikasi

### Di HP Android (Chrome)
1. Buka URL aplikasi di Chrome
2. Tap menu **⋮** → **"Add to Home Screen"** / **"Install App"**

### Di iPhone (Safari)
1. Buka URL di Safari
2. Tap ikon **Share** → **"Add to Home Screen"**

### Di Desktop (Chrome/Edge)
1. Buka URL di Chrome/Edge
2. Klik ikon **install** (📥) di address bar

---

## Struktur File
```
tabunganku-pwa/
├── index.html      # Aplikasi utama
├── app.js          # Logic lengkap
├── sw.js           # Service Worker (offline)
├── manifest.json   # PWA manifest
├── icons/          # Icon aplikasi (buat sendiri)
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

### Cara Buat Icons
Gunakan [favicon.io](https://favicon.io/favicon-generator/) atau [pwa-image-generator.online](https://pwa-image-generator.online):
- Masukkan emoji 💰 atau teks "TK"
- Download dan rename sesuai yang dibutuhkan

---

## Format Data di Google Sheets

| Tanggal | Tipe | Kategori | Jumlah (Rp) | Catatan | ID |
|---------|------|----------|-------------|---------|-----|
| 2024-01-15 | Pengeluaran | Makan | 50000 | Makan siang | 1705312345 |
| 2024-01-15 | Pemasukan | Gaji | 5000000 | Gaji Januari | 1705312399 |

---

## Troubleshooting

**Sync gagal / 403 error**
→ Pastikan spreadsheet di-share ke "Anyone with the link - Editor"

**Sync gagal / 400 error**
→ Cek nama Tab/Sheet sudah benar (case-sensitive)

**API Key invalid**
→ Pastikan Google Sheets API sudah diaktifkan di project yang sama

**Data hilang**
→ Data tersimpan di localStorage browser. Jangan clear browser data / gunakan mode incognito
→ Selalu sync ke Google Sheets sebagai backup
