# Web Bun + Svelte (Publikasi & Admin)

## Tujuan

Dokumen ini menetapkan aplikasi web sebagai wajah publik dan konsol admin Lumbung — papan harga yang bisa dibuka siapa pun di browser dan dasbor rekap untuk manajemen — tanpa mengulang logika bisnis yang sudah ada di modul KMP, sehingga web tetap ringan, cepat, dan murah dihosting.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung (khusus web).
- Pengguna: publik (papan harga), Kepala Keuangan dan Direktur Operasi (dasbor admin), Admin Gudang (rekap dan ekspor).
- Hosting: 1 VPS kecil (2 vCPU, 4 GB RAM) + domain lumbung.chefgenie.id.

## Keputusan Konkret

1. Stack dikunci: Bun 1.4.x sebagai runtime dan package manager, Svelte 5 (runes) + SvelteKit 2 sebagai framework, TypeScript 5.9.x strict, adapter-node untuk deploy VPS. Contoh perintah baku: `bun install`, `bun run dev`, `bun run build`.
2. Halaman publik hari-1 (tanpa login): `/harga` papan harga minggu berjalan (3 komoditas × 2 grade + fee 2 zona + tanggal berlaku), `/tentang` profil Lumbung dan cara jadi mitra. Target muat <1,5 detik di koneksi 3G dan bisa dicetak rapi 1 halaman A4.
3. Halaman admin (login peran): `/admin/rekap` ringkasan harian (kg masuk per komoditas, fee tertagih, susut %), `/admin/keuangan` invoice fee mingguan dan status bayar, `/admin/mitra` daftar 40 petani dan status kontraknya. Data diambil dari Lumbung-Backend via kontrak di `produk/32-kontrak-api-web-bun.md`; tidak ada query langsung ke database dari browser.
4. Perhitungan di web hanya presentasi: web tidak menghitung fee, grade, atau papan — ia menampilkan angka yang dihitung backend/modul KMP. Contoh: invoice fee dirender dari endpoint, bukan dihitung ulang di TypeScript.
5. Rilis: setiap Jumat pukul 16.00 WIB berbarengan publikasi papan harga; bila deploy gagal, halaman statis cadangan (1 file HTML papan harga minggu lalu + banner tanggal) ditayangkan manual maksimal 30 menit.

## Tautan ke File Terkait

- `platform/10-matriks-KMP-desktop-web.md` — posisi web dalam matriks.
- `produk/32-kontrak-api-web-bun.md` — endpoint yang dipakai web.
- `keuangan/20-papan-harga-mingguan.md` — konten halaman `/harga`.
- `keuangan/10-model-fee-per-kg.md` — konten halaman invoice.
- `produk/20-model-data.md` — model yang dirender web (read-only).
