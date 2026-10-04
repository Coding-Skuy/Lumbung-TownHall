> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# PRD 30 — Kriteria Keberhasilan

## Cerita Pengguna dan Acceptance

- US-001 Sebagai koordinator tani saya mencatat hasil sortir lot sehingga pembayaran petani akurat. Acceptance: total A ditambah B ditambah C sama dengan berat kotor dalam toleransi 2 persen; label memuat kode petani, tanggal, komoditas, grade, berat; sengketa diputus lewat timbang ulang 1 keranjang contoh.
- US-002 Sebagai admin gudang saya menyusun trip sehingga muatan memenuhi pesanan. Acceptance: utilisasi pickup minimal 70 persen; surat jalan memuat nomor trip, keranjang per grade, berat, fee; nomor resmi server SJ-YYYYMMDD-NNN terbit dan nomor sementara TMP dipetakan ulang otomatis.
- US-003 Sebagai sopir saya mengunggah bukti terima sehingga titik dinyatakan selesai. Acceptance: 2 foto maksimal 500 KB per foto; tersimpan lokal kurang dari 200 ms; tersinkron maksimal 2 jam; konflik dimenangkan gudang untuk berat dan lapangan untuk bukti dengan notifikasi.
- US-004 Sebagai vendor saya memesan H-1 sehingga tiba H pukul 09.00. Acceptance: konfirmasi maksimal 2 jam; toleransi telat 30 menit per titik; short dicatat alasan dan ditawari substitusi B diskon 15 persen.
- US-005 Sebagai kepala keuangan saya menerbitkan papan Jumat 15.00 sehingga semua pihak bertransaksi dengan acuan sama. Acceptance: publikasi tiga jalur maksimal 17.00; lembar kerja 3 referensi tersimpan 6 bulan; rasio petani minimal 85 persen dan deviasi konsumen maksimal 10 persen.
- US-006 Sebagai petani saya menerima bayar H+1 sehingga adil dan tepat waktu. Acceptance: ketepatan minimal 95 persen lot per minggu; denda 0,5 persen per hari otomatis bila telat.

## Non-Goals v1.0.0

- Tanpa cold chain aktif; tanpa auto-update MSIX; tanpa perhitungan harga di klien web; tanpa perluasan komoditas keempat; tanpa pengiriman di luar radius 25 km.

## Batasan

Batasan dokumen ini: hanya kriteria produk yang dapat diuji. Rincian teknis API dan skema ada di FSD. Klaim sukses tanpa skor mingguan rasio, deviasi, ketepatan, dan susut dinyatakan tidak berlaku.
