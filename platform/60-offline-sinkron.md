# Offline-First & Sinkronisasi

## Tujuan

Dokumen ini menetapkan aturan main offline-first untuk desktop gudang dan mobile lapangan agar operasional tidak pernah berhenti saat internet mati — data selalu ditulis ke database lokal dulu — dan saat sinyal kembali semua pihak konvergen ke keadaan yang sama tanpa duplikat pembayaran atau kehilangan bukti terima.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung.
- Pelaksana: engineer KMP (mekanisme antrean), Admin Gudang (memantau antrean sinkron), Mandor Trip (menindaklanjuti konflik).
- Batas tanggung jawab: backend Lumbung-Backend menyediakan endpoint idempoten (lihat kontrak API per konsumen).

## Keputusan Konkret

1. Prinsip tulis-lokal-dulu: setiap timbang, sortir, bukti terima, dan rencana setoran tersimpan ke SQLDelight lokal dalam <200 ms dan mendapat UUID v4 saat dibuat; tidak ada tombol yang menunggu respons server untuk menampilkan sukses ke pengguna.
2. Antrean sinkron satu arah per perangkat (outbox table) diproses FIFO saat online dengan retry backoff 1, 5, 15 menit; contoh: 25 label keranjang (total <100 KB JSON) tersinkron dalam <30 detik di koneksi 1 Mbps, sedangkan 6 foto bukti terima (±3 MB) menyusul dan boleh menunggu WiFi.
3. Idempotensi wajib: setiap request sinkron membawa UUID; backend menolak duplikat dengan respons sukses yang sama. Contoh: tombol cetak label yang ditekan 2 kali saat offline hanya menghasilkan 1 lot di server karena UUID lot sama.
4. Resolusi konflik: data gudang (desktop) menang atas data lapangan (mobile) untuk berat dan grade; data lapangan menang untuk bukti terima dan posisi. Setiap konflik yang dimenangkan salah satu pihak dicatat di log konflik yang bisa dibuka Admin Gudang dan diberi tahu ke pihak yang kalah via notifikasi dalam aplikasi.
5. Batas darurat: bila perangkat offline >3 × 24 jam, aplikasi mengunci aksi baru yang butuh nomor urut server (surat jalan baru) tetapi tetap mengizinkan timbang dan bukti terima; Admin Gudang wajib mengekspor cadangan SQLite ke flashdisk tiap Jumat sore.

## Tautan ke File Terkait

- `platform/30-desktop-windows-gudang.md` — database lokal desktop.
- `platform/40-mobile-KMP.md` — perilaku offline mobile.
- `produk/30-kontrak-api-KMP-mobile.md`, `produk/31-kontrak-api-desktop-windows.md`, `produk/32-kontrak-api-web-bun.md` — endpoint idempoten.
- `produk/20-model-data.md` — kolom UUID dan versi per entitas.
- `distribusi/20-sop-trip-harian.md` — batas 2 jam sinkron bukti terima.
