# Metrik Susut & SLA Operasional

## Tujuan

Dokumen ini menetapkan batas susut yang ditoleransi di setiap tahap dan SLA waktu operasional harian agar mutu hortikultura yang mudah layu tetap terjaga dari panen sampai diterima pembeli, dengan angka yang realistis untuk tiga komoditas hari-1 dan konsekuensi yang jelas bila dilampaui.

## Pemilik / Peran

- Pemilik dokumen: Mandor Trip (SLA waktu) + Koordinator Timbang-Sortir (susut), dilaporkan ke Kepala Agregasi tiap Senin pagi.
- Pengukur: Admin Gudang merekap dari data lot, trip, dan bukti terima.
- Penerima laporan: dapur Pawon dan perwakilan petani tiap awal bulan.

## Keputusan Konkret

1. Batas susut per tahap (persen dari berat masuk tahap itu): sortir gudang maksimal cabai 6%, bawang 4%, kangkung 8%; susut jalan (gudang→penerima) maksimal 2% per trip untuk semua komoditas; susut total panen→terima maksimal cabai 8%, bawang 6%, kangkung 10%. Contoh: 500 kg cabai kotor → minimal 460 kg diterima pembeli.
2. SLA waktu harian: terima panen tutup 10.00, sortir selesai 12.00, muat selesai 12.30 (Utara/Kota) dan 13.00 (Selatan), tiba titik terjauh maksimal 09.00 untuk trip pagi; publikasi papan harga Jumat maksimal 17.00; pembayaran petani H+1 maksimal 16.00 (kecuali Minggu/libur bank, diumumkan di muka + denda 0,5% otomatis).
3. Contoh evaluasi minggu: susut sortir kangkung 9,2% (lewat 1,2 poin) → tindakan: majukan jam terima kangkung ke 08.00 dan tambah kain basah penutup (lihat `distribusi/30-armada-kemasan.md`); 2 trip Utara telat >30 menit → review muat (target muat 30→20 menit).
4. Konsekuensi: susut jalan >2% sebanyak 3 trip berturut-turut memicu inspeksi keranjang dan kendaraan; keterlambatan bayar H+1 >2 hari memberi kompensasi otomatis 1% ke petani; short pesanan >10% volume mingguan memicu permintaan maaf tertulis + prioritas muat minggu berikutnya untuk pembeli terdampak.
5. Pencatatan: setiap insiden (telat, susut lewat, short) wajib masuk log harian dengan kode `INS-YYYYMMDD-NNN`, foto bila relevan, dan status tindak lanjut; log terbuka untuk audit Finance dan tidak boleh dihapus — hanya ditutup dengan catatan penyelesaian.

## Tautan ke File Terkait

- `agregasi/10-sop-sortir-grading.md` — praktik yang menentukan susut sortir.
- `distribusi/20-sop-trip-harian.md` — eksekusi SLA waktu trip.
- `distribusi/30-armada-kemasan.md` — perangkat penekan susut.
- `metrik/10-keadilan-harga.md` — ketepatan bayar sebagai bagian keadilan.
- `roadmap/10-pilot-hortikultura.md` — target susut/SLA per fase pilot.
