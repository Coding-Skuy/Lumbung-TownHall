> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# FSD 30 — Kontrak API, Event, dan Galat

## Basis dan Autentikasi

- Basis: `https://api.lumbung.chefgenie.id/v1` dengan header `X-Perangkat-Id`. Sehat: `GET /v1/kesehatan` kembali status ok dan waktu server.
- Autentikasi dikunci: JWT akses 15 menit, refresh 7 hari, API key perangkat terdaftar, service key server-ke-server untuk web. Login shift gudang `POST /v1/gudang/masuk` memberi token shift 12 jam untuk operator contoh OPR-SORTIR-1. Tiga gagal PIN mengunci 15 menit.
- Kunci web disimpan sebagai variabel lingkungan server LUMBUNG_API_KEY rotasi 90 hari dan tidak pernah dikirim ke browser.

## Kontrak per Konsumen

- Mobile sopir 5 endpoint: `GET /v1/trip-hari-ini`, `POST /v1/titik/{id}/tiba`, `POST /v1/titik/{id}/berangkat`, `POST /v1/bukti-terima` dengan UUID lalu foto via `POST /v1/unggah-foto` maksimal 500 KB JPEG maksimal 4 foto, `POST /v1/insiden`. Contoh tiba membawa trip TRIP-UT-041 titik PWN-1 waktu dan lat lng.
- Mobile petani 4 endpoint: `GET /v1/kontrak-saya`, `POST /v1/rencana-setoran`, `GET /v1/pembayaran-saya`, `GET /v1/papan-harga` read-only dan difilter server per id petani.
- Desktop gudang 7 endpoint: `POST /v1/lot`, `POST /v1/lot/{id}/sortir` berat gram integer, `POST /v1/keranjang/batch` maksimal 50 per request, `POST /v1/trip` dan `POST /v1/trip/{id}/surat-jalan` terbit SJ-YYYYMMDD-NNN, `GET /v1/stok-lot`, `POST /v1/sinkron/batch` maksimal 200 FIFO.
- Web publik 2 endpoint cache 15 menit: `GET /v1/publik/papan-harga` memuat cabai, bawang, kangkung per grade ditambah fee dekat 1500 jauh 2500 dan tanggal berlaku, `GET /v1/publik/profil`. Web admin baca 4 dan tulis 3 beraudit dengan `audit_id` contoh AUD-20261009-003. Web memakai kg desimal di input dan server mengonversi ke gram.

## Event dan Galat

- Event: `lot.disortir`, `trip.dimuat`, `titik.tiba`, `bukti.diterima`, `fee.ditagih`, `petani.dibayar`, `konflik.dicatat`. Setiap event membawa UUID, waktu, dan versi.
- Idempotensi: semua POST membawa UUID klien; kirim ulang sama kembali 200 dengan flag duplikat true tanpa rekaman ganda.
- Galat baku: 401 token kedaluwarsa refresh 1 kali lalu login ulang, 403 peran ditolak dan dicatat, 409 konflik versi tampil pesan data gudang lebih baru, 422 validasi contoh berat negatif atau total sortir di luar 2 persen, 429 maksimal 60 request per menit per perangkat.

## Batasan

Batasan dokumen ini: hanya kontrak, event, dan galat. Implementasi server ada di repo Lumbung-Backend. Konsumen dilarang menghitung fee, grade, atau papan di klien; semua wajib memakai angka server.
