# Metrik Keadilan Harga

## Tujuan

Dokumen ini mendefinisikan apa arti "sukses = keadilan harga" dalam angka yang bisa diukur tiap minggu — adil bagi petani yang menanam dan stabil bagi konsumen yang membeli — sehingga klaim keberhasilan Lumbung bukan slogan melainkan skor yang dilaporkan terbuka dan bisa diverifikasi dari data lot dan papan harga.

## Pemilik / Peran

- Pemilik dokumen: Kepala Keuangan Lumbung (penghitung) + Kepala Agregasi (penindaklanjut).
- Diaudit oleh: Finance PT ChefGenie tiap akhir bulan; ringkasan dipublikasi ke petani tiap awal bulan.
- Sumber data: tabel Lot/Sortir/Pembayaran (lihat `produk/20-model-data.md`) dan lembar survei pasar mingguan.

## Keputusan Konkret

1. Tiga indikator utama dengan ambang lulus pilot: (a) Rasio harga petani terhadap median pasar ≥85% (contoh: median cabai Rp35.000 → petani Grade A terima minimal Rp29.750; papan aktual Rp31.500 = 90% → lulus); (b) Deviasi harga konsumen (harga bayar termasuk fee) terhadap median pasar ≤10% (contoh: bayar Rp34.000 vs median Rp35.000 = −2,9% → lulus); (c) Keterlambatan bayar ke petani H+1 tepat waktu ≥95% lot per minggu.
2. Contoh skor minggu 41/2026: 62 lot terbayar, rata-rata rasio petani 89%, deviasi konsumen +4%, ketepatan H+1 97% (60/62 lot, 2 lot telat 1 hari karena Minggu libur bank dengan kompensasi denda 0,5% terbayar) → status minggu: ADIL.
3. Aturan eskalasi: 2 minggu berturut-turut rasio petani <85% untuk satu komoditas memicu review formula papan (buffer 10% diturunkan ke 7% untuk komoditas itu selama 4 minggu); 2 minggu deviasi konsumen >10% memicu review tarif fee zona terkait.
4. Transparansi: setiap awal bulan Admin Gudang menempel rekap 1 halaman di pintu gudang (rata-rata rasio, deviasi, ketepatan bayar per komoditas) dan membagikan ke grup petani; petani boleh meminta rincian lotnya sendiri kapan pun gratis.
5. Anti-manipulasi: survei 3 harga pasar referensi dilakukan 2 orang berbeda (Admin + 1 petani bergilir tiap minggu) dan difoto (papan harga pasar + struk); selisih usulan >5% antara keduanya diselesaikan Kepala Agregasi sebelum Jumat 15.00.

## Tautan ke File Terkait

- `keuangan/20-papan-harga-mingguan.md` — sumber harga papan yang diukur.
- `keuangan/10-model-fee-per-kg.md` — komponen fee dalam deviasi konsumen.
- `agregasi/20-kontrak-mini-musim.md` — janji H+1 yang diukur ketepatannya.
- `produk/20-model-data.md` — tabel sumber perhitungan.
- `roadmap/10-pilot-hortikultura.md` — kapan skor pertama dilaporkan.
