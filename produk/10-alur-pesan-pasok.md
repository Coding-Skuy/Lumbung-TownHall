# Alur Pesan–Pasok (Order to Supply)

## Tujuan

Dokumen ini menetapkan alur pesan-pasok ujung ke ujung dari permintaan dapur Pawon dan pedagang pasar sampai pembayaran petani, agar setiap kilogram yang dipesan bisa ditelusur balik ke lot sortir dan kontrak petani yang memasoknya dalam satu nomor rantai yang sama.

## Pemilik / Peran

- Pemilik dokumen: Kepala Agregasi.
- Pelaku alur: Pembeli (dapur Pawon/pedagang membuat pesanan), Admin Gudang (mengonfirmasi dan menyusun trip), Petugas Sortir (memenuhi dari stok lot), Sopir (mengantar + bukti terima), Kepala Keuangan (invoice fee + bayar petani).
- SLA alur penuh: pesan H-1 pukul 15.00 → terima H pukul 09.00.

## Keputusan Konkret

1. Lima tahap baku dengan nomor rantai tunggal `PSO-YYYYMMDD-NNN` (contoh `PSO-20261010-014`): (1) Pesan masuk via web/telepon, (2) Konfirmasi Admin maksimal 2 jam (stok lot dicek), (3) Alokasi lot + susun trip H-1 sore, (4) Antar + bukti terima H pagi, (5) Invoice fee mingguan + bayar petani H+1.
2. Contoh alur konkret: dapur Pawon 1 memesan Jumat 14.00 untuk Sabtu: 100 kg cabai A + 50 kg bawang A + 20 kg kangkung A (total 170 kg, Zona Dekat → fee Rp255.000). Admin mengonfirmasi pukul 15.30 dari lot L-8812/L-8813, dimuat di Rute Utara Sabtu 06.00, diterima 07.15 dengan foto, petani dibayar H+1 Senin (karena Minggu libur bank, diumumkan di muka).
3. Batas pesan: minimal 20 kg per titik per hari agar trip tidak rugi; di bawah itu digabung ke trip hari berikutnya atau diambil sendiri di gudang tanpa fee antar (hanya fee sortir Rp500/kg).
4. Pembatalan gratis sampai H-1 pukul 17.00; setelah itu pembeli menanggung 50% fee trip (contoh: batalkan 170 kg Zona Dekat pagi H → denda Rp127.500) karena muatan sudah disusun.
5. Setiap pesanan yang tidak terpenuhi penuh (short) dicatat alasannya (gagal panen, susut sortir, armada) dan pembeli ditawari substitusi grade B dengan diskon 15% sebelum dialihkan ke pemasok luar.

## Tautan ke File Terkait

- `produk/20-model-data.md` — entitas Pesanan, Lot, Trip, Pembayaran.
- `distribusi/10-desain-rute-trip.md` — trip yang membawa pesanan.
- `keuangan/10-model-fee-per-kg.md` — fee yang dihitung per pesanan.
- `produk/30-kontrak-api-KMP-mobile.md`, `produk/31-kontrak-api-desktop-windows.md`, `produk/32-kontrak-api-web-bun.md` — endpoint tiap tahap.
- `metrik/20-susut-dan-sla.md` — SLA pemenuhan pesanan.
