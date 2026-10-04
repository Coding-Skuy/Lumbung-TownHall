# Kontrak API untuk Mobile KMP

## Tujuan

Dokumen ini menetapkan kontrak endpoint Lumbung-Backend yang dikonsumsi aplikasi mobile KMP sopir dan petani agar kedua peran lapangan mendapat data yang minim, cepat, dan hemat kuota, dengan jaminan idempotensi untuk setiap aksi yang dibuat saat offline.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung (sisi konsumen); implementasi server di repo `Coding-Skuy/Lumbung-Backend`.
- Konsumen: aplikasi mobile KMP Android+iOS (sopir dan petani).
- SLA: respons p95 <800 ms di koneksi 3G untuk endpoint daftar; upload foto terpisah dari JSON.

## Keputusan Konkret

1. Basis URL dan versi: `https://api.lumbung.chefgenie.id/v1` dengan header `X-Perangkat-Id` dan token perangkat (lihat `produk/50-autentikasi-perangkat.md`); contoh sehat: `GET /v1/kesehatan` → `{"status":"ok","waktu_server":"2026-10-04T10:00:00+07:00"}`.
2. Endpoint sopir (5): `GET /v1/trip-hari-ini` (daftar trip + titik berurutan), `POST /v1/titik/{id}/tiba`, `POST /v1/titik/{id}/berangkat`, `POST /v1/bukti-terima` (JSON metadata + UUID, foto diunggah terpisah via `POST /v1/unggah-foto`), `POST /v1/insiden` (jenis, catatan, foto opsional). Contoh body tiba: `{"uuid":"…","trip_id":"TRIP-UT-041","titik_id":"PWN-1","waktu":"2026-10-10T07:15:00+07:00","lat":-7.79,"lng":110.36}`.
3. Endpoint petani (4): `GET /v1/kontrak-saya` (komitmen vs realisasi kg musim berjalan), `POST /v1/rencana-setoran` (komoditas, estimasi kg, tanggal), `GET /v1/pembayaran-saya` (riwayat H+1 + status), `GET /v1/papan-harga` (papan minggu berjalan, read-only). Petani hanya melihat datanya sendiri; filter server-side per id petani.
4. Idempotensi: semua POST menerima `uuid` klien; pengiriman ulang dengan `uuid` sama mengembalikan hasil pertama (kode 200 + flag `duplikat:true`) tanpa membuat rekaman ganda. Batas unggah foto 500 KB per file, format JPEG, maksimal 4 foto per bukti terima.
5. Kode galat baku: 401 token kedaluwarsa (mobile refresh otomatis 1 kali lalu minta login ulang), 409 konflik versi (mobile menampilkan pesan "data gudang lebih baru"), 422 validasi (contoh berat negatif), 429-edisi hemat (maksimal 60 request/menit per perangkat).

## Tautan ke File Terkait

- `produk/20-model-data.md` — entitas yang diserialisasi endpoint ini.
- `produk/50-autentikasi-perangkat.md` — token perangkat dan refresh.
- `platform/40-mobile-KMP.md` — fitur yang memanggil endpoint ini.
- `platform/60-offline-sinkron.md` — antrean dan retry saat offline.
- `produk/31-kontrak-api-desktop-windows.md`, `produk/32-kontrak-api-web-bun.md` — kontrak saudara untuk konsumen lain.
