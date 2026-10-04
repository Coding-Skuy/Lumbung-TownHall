# Lumbung-TownHall 🌾

Ruang diskusi terbuka Divisi Lumbung — hulu PT ChefGenie: agregasi panen hortikultura dari petani mitra dan distribusi ke dapur serta pasar. Satu PT ChefGenie, Lumbung adalah divisi hulu; monetisasi tunggal berupa fee logistik murni per kg/trip dengan harga transparan. Komoditas hari-1: cabai rawit merah, bawang merah, kangkung. Sukses = keadilan harga: adil bagi petani, stabil bagi konsumen.

## Peta Folder (Varian 1: folder = sub-segmen kerja)

- `agregasi/` — piagam, SOP sortir-grading, kontrak mini musim.
  - `agregasi/00-piagam-agregasi.md`, `agregasi/10-sop-sortir-grading.md`, `agregasi/20-kontrak-mini-musim.md`
- `distribusi/` — desain rute-trip, SOP trip harian, armada-kemasan.
  - `distribusi/10-desain-rute-trip.md`, `distribusi/20-sop-trip-harian.md`, `distribusi/30-armada-kemasan.md`
- `keuangan/` — model fee per kg, papan harga mingguan.
  - `keuangan/10-model-fee-per-kg.md`, `keuangan/20-papan-harga-mingguan.md`
- `platform/` — matriks KMP-desktop-web, Navigation3, desktop Windows gudang, mobile KMP, web Bun+Svelte, offline-sinkron.
  - `platform/10-matriks-KMP-desktop-web.md`, `platform/20-navigasi3.md`, `platform/30-desktop-windows-gudang.md`, `platform/40-mobile-KMP.md`, `platform/50-web-bun-svelte.md`, `platform/60-offline-sinkron.md`
- `produk/` — alur pesan-pasok, model data, kontrak API per konsumen, modul KMP bersama, autentikasi perangkat.
  - `produk/10-alur-pesan-pasok.md`, `produk/20-model-data.md`, `produk/30-kontrak-api-KMP-mobile.md`, `produk/31-kontrak-api-desktop-windows.md`, `produk/32-kontrak-api-web-bun.md`, `produk/40-modul-KMP-bersama.md`, `produk/50-autentikasi-perangkat.md`
- `metrik/` — keadilan harga, susut dan SLA.
  - `metrik/10-keadilan-harga.md`, `metrik/20-susut-dan-sla.md`
- `roadmap/` — pilot hortikultura 90 hari.
  - `roadmap/10-pilot-hortikultura.md`

Mulai dari `agregasi/00-piagam-agregasi.md`, lalu `roadmap/10-pilot-hortikultura.md` untuk gambaran pilot.

## Stack Terkunci

- Mobile + Desktop: Kotlin Multiplatform + Compose Multiplatform + Navigation3. Desktop target Windows x64 (MSIX, offline-first SQLite/SQLDelight, printer thermal, timbangan USB/serial) wajib hari-1; mobile Android + iOS.
- Web: Bun 1.4.x + Svelte 5 + SvelteKit 2 + TypeScript 5.9.x.
- Backend tunggal: [Lumbung-Backend](https://github.com/Coding-Skuy/Lumbung-Backend) — kontrak API dipisah per konsumen (`produk/30-*`, `produk/31-*`, `produk/32-*`).

## TownHall Lain (PT ChefGenie)

- [ChefGenie-TownHall](https://github.com/Coding-Skuy/ChefGenie-TownHall) — induk PT ChefGenie.
- [Pawonee-TownHall](https://github.com/Coding-Skuy/Pawonee-TownHall) — dapur/pengolahan (pembeli utama Lumbung).
- [Pasaree-TownHall](https://github.com/Coding-Skuy/Pasaree-TownHall) — pasar/penjualan.
- [Pedaree-TownHall](https://github.com/Coding-Skuy/Pedaree-TownHall) — pengantar/last-mile.
- [TitipO-TownHall](https://github.com/Coding-Skuy/TitipO-TownHall) — titip dan kemitraan.

## Kontribusi

Repo terbuka: usulan bisnis maupun koreksi kecil dipersilakan via pull request ke `main`. Setiap dokumen mencantumkan pemilik, keputusan konkret berangka, dan tautan ke file terkait — tanpa placeholder.
