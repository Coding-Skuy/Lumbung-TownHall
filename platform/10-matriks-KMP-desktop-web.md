# Matriks KMP + Desktop + Web

## Tujuan

Dokumen ini menjadi matriks keputusan tunggal yang menjawab pertanyaan di mana setiap fitur Lumbung dibangun: logika bersama di Kotlin Multiplatform, aplikasi desktop Windows untuk gudang, aplikasi mobile untuk lapangan, atau web Bun+Svelte untuk publikasi dan admin, sehingga tidak ada fitur yang dibangun dua kali di dua platform berbeda.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung.
- Pengguna: seluruh engineer KMP, desktop, dan web; Kepala Agregasi untuk prioritas.
- Review tiap awal sprint 2 mingguan.

## Keputusan Konkret

1. Prinsip pembagian: semua aturan bisnis dan model data tinggal di modul KMP bersama (`shared-core`, lihat `produk/40-modul-KMP-bersama.md`); desktop Windows mengonsumsi modul itu untuk operasional gudang offline-first; mobile KMP untuk sopir dan petani lapangan; web Bun+Svelte hanya untuk yang butuh browser (papan harga publik, dashboard admin, laporan).
2. Matriks alokasi fitur hari-1:
   - Timbang + cetak label + surat jalan → Desktop Windows saja (butuh USB/serial dan printer thermal).
   - Bukti terima foto + tanda tangan + posisi trip → Mobile KMP saja (butuh kamera dan GPS).
   - Papan harga publik + dashboard admin + rekap keuangan → Web Bun+Svelte saja.
   - Validasi grade, hitung fee, kontrak mini → modul KMP bersama dipakai ketiga konsumen.
3. Contoh konkret: perhitungan fee Zona Dekat Rp1.500/kg ditulis sekali di `shared-core/pricing/FeeCalculator.kt` dan dipanggil oleh desktop (cetak surat jalan), mobile (tampilkan fee ke sopir), dan web (tampilkan di invoice) — sehingga perubahan tarif tidak perlu diubah di tiga tempat.
4. Bahasa dan versi dikunci: Kotlin 2.x + Compose Multiplatform + Navigation3 untuk mobile dan desktop; Bun 1.4.x + Svelte 5 + SvelteKit 2 + TypeScript 5.9.x untuk web; backend tunggal Lumbung-Backend di repo `Coding-Skuy/Lumbung-Backend`.
5. Larangan: tidak ada logika harga, fee, atau grade yang ditulis langsung di kode web atau kode UI desktop/mobile — semuanya wajib memanggil modul bersama; pelanggaran ditolak saat code review.

## Tautan ke File Terkait

- `platform/20-navigasi3.md` — pola navigasi di KMP.
- `platform/30-desktop-windows-gudang.md` — peran desktop Windows.
- `platform/40-mobile-KMP.md` — peran mobile KMP.
- `platform/50-web-bun-svelte.md` — peran web Bun+Svelte.
- `produk/40-modul-KMP-bersama.md` — isi modul bersama.
- `produk/30-kontrak-api-KMP-mobile.md`, `produk/31-kontrak-api-desktop-windows.md`, `produk/32-kontrak-api-web-bun.md` — kontrak backend per konsumen.
