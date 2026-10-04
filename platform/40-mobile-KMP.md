# Mobile KMP (Android + iOS)

## Tujuan

Dokumen ini menetapkan aplikasi mobile Kotlin Multiplatform untuk dua pengguna lapangan — sopir trip dan petani mitra — agar bukti terima, posisi trip, dan setoran panen tercatat di tempat kejadian dengan kamera dan GPS ponsel, tanpa membawa laptop ke lapangan.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung (khusus mobile).
- Pengguna: 4 sopir/kernet (Android, minimal versi 10) dan 40 petani mitra (Android dan iOS, 1 aplikasi KMP dua target).
- Dukungan: Admin Gudang membantu instalasi dan login perangkat petani saat penandatanganan kontrak.

## Keputusan Konkret

1. Satu basis kode KMP untuk Android dan iOS dengan UI Compose Multiplatform; platform iOS memakai target arm64 dan diuji di 2 perangkat nyata (iPhone SE dan satu Android entry-level Rp1.500.000-an) sebelum tiap rilis agar performa di HP murah terpantau.
2. Fitur sopir hari-1: daftar trip hari ini, navigasi titik berurutan, tombol tiba/berangkat per titik, foto + tanda tangan bukti terima, dan laporan insiden (mogok, macet, susut). Contoh: bukti terima 1 titik = 2 foto (keranjang terbongkar + tanda tangan) ukuran maksimal 500 KB per foto setelah kompresi.
3. Fitur petani hari-1: lihat kontrak mini musimnya, catat rencana setoran besok (komoditas + estimasi kg), lihat riwayat pembayaran H+1, dan terima siaran papan harga Jumat. Petani tidak bisa mengubah harga — hanya melihat.
4. Semua aksi lapangan wajib bisa offline: bukti terima, rencana setoran, dan posisi tersimpan di SQLDelight lokal lalu tersinkron maksimal 2 jam setelah sinyal kembali; konflik (misalnya admin mengubah trip saat sopir offline) dimenangkan oleh data gudang dengan notifikasi ke sopir.
5. Baterai dan data: sinkronisasi foto hanya lewat WiFi/koneksi manual bila ukuran antrean >10 MB; pelacakan GPS dicatat tiap 5 menit selama trip aktif saja, bukan sepanjang hari.

## Tautan ke File Terkait

- `platform/10-matriks-KMP-desktop-web.md` — posisi mobile dalam matriks.
- `platform/20-navigasi3.md` — rute layar sopir dan petani.
- `platform/60-offline-sinkron.md` — aturan sinkronisasi mobile.
- `produk/30-kontrak-api-KMP-mobile.md` — endpoint yang dipakai mobile.
- `produk/50-autentikasi-perangkat.md` — login dan kunci perangkat.
- `distribusi/20-sop-trip-harian.md` — SOP yang dieksekusi sopir di aplikasi ini.
