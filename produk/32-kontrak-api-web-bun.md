# Kontrak API untuk Web Bun

## Tujuan

Dokumen ini menetapkan kontrak endpoint Lumbung-Backend yang dikonsumsi aplikasi web Bun+Svelte agar halaman publik papan harga dan dasbor admin selalu menampilkan angka yang sama dengan gudang, dengan pola baca read-only yang bisa di-cache dan pola tulis admin yang terbatas dan beraudit.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung (sisi konsumen); implementasi server di repo `Coding-Skuy/Lumbung-Backend`.
- Konsumen: SvelteKit SSR di VPS (server-side fetch, bukan dari browser langsung untuk data sensitif).
- SLA: halaman `/harga` p95 <600 ms (cache 15 menit); halaman admin p95 <1,2 detik.

## Keputusan Konkret

1. Endpoint publik tanpa login (2, boleh di-cache CDN 15 menit): `GET /v1/publik/papan-harga` (berlaku Senin–Minggu, contoh respons memuat `cabai:{a:31500,b:26500}`, `bawang:{a:28000,b:23500}`, `kangkung:{a:6000,b:5000}`, `fee:{dekat:1500,jauh:2500}`, `berlaku:"2026-10-06 s.d. 2026-10-12"`) dan `GET /v1/publik/profil` (profil Lumbung + kontak kemitraan).
2. Endpoint admin baca (4, butuh sesi peran): `GET /v1/admin/rekap-harian?tanggal=2026-10-10` (kg masuk per komoditas, fee tertagih, susut %), `GET /v1/admin/invoice?minggu=2026-W41` (daftar invoice fee + status), `GET /v1/admin/mitra` (40 petani + status kontrak), `GET /v1/admin/insiden` (log keterlambatan/konflik sinkron).
3. Endpoint admin tulis (3, semua beraudit nama + waktu): `POST /v1/admin/papan-harga` (terbitkan papan Jumat 15.00, contoh 3 komoditas × 2 grade + 2 zona fee), `POST /v1/admin/invoice/{id}/lunas` (tandai bayar), `POST /v1/admin/mitra/{id}/status` (aktifkan/nonaktifkan kontrak). Setiap tulis mengembalikan `audit_id` (contoh `AUD-20261009-003`) yang tampil di dasbor.
4. Web tidak pernah menerima berat dalam gram dari pengguna — input admin memakai kg desimal (contoh 20,5 kg) dan server SvelteKit mengonversi ke gram integer sebelum ke backend agar konsisten dengan `produk/20-model-data.md`.
5. Kunci API web disimpan sebagai variabel lingkungan server (`LUMBUNG_API_KEY`, rotasi 90 hari) dan tidak pernah dikirim ke browser; bila bocor, Tech Lead mencabut dalam 1 jam dan menerbitkan kunci baru sebelum Jumat publikasi harga.

## Tautan ke File Terkait

- `produk/20-model-data.md` — entitas yang dirender web.
- `platform/50-web-bun-svelte.md` — halaman yang memanggil endpoint ini.
- `keuangan/20-papan-harga-mingguan.md` — konten papan harga publik.
- `keuangan/10-model-fee-per-kg.md` — konten invoice admin.
- `produk/30-kontrak-api-KMP-mobile.md`, `produk/31-kontrak-api-desktop-windows.md` — kontrak saudara.
