# SOP Sortir & Grading

## Tujuan

Dokumen ini mengatur alur kerja standar penimbangan, sortir, dan grading setiap lot panen yang masuk gudang Lumbung agar keputusan Grade A/B/C seragam antar petugas dan antar hari, sehingga pembayaran ke petani dapat dipertanggungjawabkan dan susut selama penyimpanan serta pengiriman stays dalam batas yang disepakati.

## Pemilik / Peran

- Pemilik dokumen: Koordinator Timbang-Sortir.
- Pelaksana: 2 Petugas Sortir dan 1 Petugas Timbang per shift pagi; Mandor Trip memverifikasi hasil sortir sebelum muat.
- Pengawas mutu: Kepala Agregasi melakukan uji petik 5 keranjang per hari.

## Keputusan Konkret

1. Setiap lot ditimbang dua kali (timbang kotor saat bongkar, timbang bersih setelah sortir) memakai timbangan USB yang tersambung ke aplikasi desktop gudang; selisih timbang kotor-bersih dicatat otomatis sebagai susut sortir hari itu.
2. Standar grade per komoditas:
   - Cabai rawit merah: Grade A panjang >7 cm, merah penuh, tangkai utuh, busuk 0%; Grade B panjang 5–7 cm atau belang hijau-merah maksimal 20% per keranjang, busuk maksimal 2%; selain itu Grade C (tolak).
   - Bawang merah: Grade A diameter >2,5 cm, kering, kulit utuh, busuk 0%; Grade B diameter 1,5–2,5 cm, kulit terkelupas maksimal 15%, busuk maksimal 2%; selain itu Grade C (tolak).
   - Kangkung: Grade A ikat 250 gram, daun hijau segar, batang renyah, layu 0%; Grade B layu maksimal 10% daun per ikat; selain itu Grade C (tolak).
3. Contoh angka kerja: dari 500 kg cabai kotor, hasil sortir tipikal 420 kg Grade A (84%), 55 kg Grade B (11%), 25 kg Grade C/tolak (5%). Target susut sortir maksimal: cabai 6%, bawang 4%, kangkung 8%.
4. Lot Grade C tidak dibuang: ditawarkan kembali ke petani untuk dijual sendiri ke pasar lokal tunai, atau dibeli Lumbung Rp5.000/kg untuk kanal olahan (sambal Pawon) bila dapur membutuhkan hari itu.
5. Label tiap keranjang lolos sortir wajib memuat: kode petani, tanggal, komoditas, grade, berat bersih. Label dicetak dari printer thermal desktop gudang (lihat `platform/30-desktop-windows-gudang.md`).
6. Sengketa grade diselesaikan di tempat oleh Koordinator Timbang-Sortir dengan menimbang ulang 1 keranjang contoh; keputusannya final dan dicatat di log harian.

## Tautan ke File Terkait

- `agregasi/00-piagam-agregasi.md` — piagam dan skala operasi agregasi.
- `agregasi/20-kontrak-mini-musim.md` — konsekuensi grade terhadap pembayaran kontrak.
- `distribusi/30-armada-kemasan.md` — jenis keranjang dan kemasan per grade.
- `keuangan/20-papan-harga-mingguan.md` — harga papan acuan pembayaran Grade A/B.
- `metrik/20-susut-dan-sla.md` — batas susut dan SLA mutu.
- `platform/30-desktop-windows-gudang.md` — aplikasi desktop timbang-cetak label.
