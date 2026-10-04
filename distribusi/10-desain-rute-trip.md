# Desain Rute & Trip Distribusi

## Tujuan

Dokumen ini menetapkan desain rute dan pola trip distribusi harian Lumbung dari gudang ke dapur Pawon dan titik pasar agar setiap kilogram terangkut dengan biaya per kg terendah yang masih memenuhi SLA kesegaran, dengan pola hub-spoke satu gudang yang bisa diulang setiap hari oleh Mandor Trip tanpa perencanaan ulang dari nol.

## Pemilik / Peran

- Pemilik dokumen: Mandor Trip.
- Pelaksana: Sopir dan kernet armada; Koordinator Timbang-Sortir menyiapkan muatan per rute.
- Penyetuju perubahan rute: Kepala Agregasi.

## Keputusan Konkret

1. Pola hub-spoke satu gudang dengan 3 rute tetap hari-1:
   - Rute Utara (12 km pulang-pergi): gudang → 2 dapur Pawon → 1 lapak pasar. Muatan tipikal 500 kg, waktu tempuh 45 menit.
   - Rute Selatan (22 km pulang-pergi): gudang → 1 dapur Pawon → 2 lapak pasar. Muatan tipikal 650 kg, waktu tempuh 70 menit.
   - Rute Kota (8 km pulang-pergi): gudang → 3 lapak pasar. Muatan tipikal 350 kg, waktu tempuh 40 menit.
2. Frekuensi: Rute Utara dan Kota jalan setiap hari; Rute Selatan jalan Senin, Rabu, Jumat karena volume bawang yang dipanen 2 kali seminggu. Total kapasitas mingguan = (500 × 7) + (350 × 7) + (650 × 3) = 7.900 kg.
3. Biaya per trip dihitung terbuka: contoh Rute Utara memakai pickup (BBM Rp60.000 + sopir/kernet Rp150.000 + depresiasi Rp40.000 = Rp250.000 per trip). Dengan muatan 500 kg, biaya Rp500/kg; fee yang ditagih Rp1.500/kg sehingga margin kontribusi Rp1.000/kg atau Rp500.000 per trip.
4. Aturan muat: sayur daun (kangkung) selalu di atas, cabai di tengah, bawang di bawah; maksimal 2 susun keranjang 20 kg; terpal wajib bila hujan. Waktu muat maksimal 30 menit per rute.
5. Titik kumpul petani jemput (collection point) 2 lokasi di jalur Rute Selatan agar petani radius >15 km cukup mengantar ke titik kumpul; insentif antar ke titik kumpul Rp200/kg dibayar tunai di tempat.

## Tautan ke File Terkait

- `distribusi/20-sop-trip-harian.md` — SOP eksekusi tiap trip.
- `distribusi/30-armada-kemasan.md` — spesifikasi armada dan kemasan.
- `keuangan/10-model-fee-per-kg.md` — fee Rp1.500/Rp2.500 per kg per zona.
- `metrik/20-susut-dan-sla.md` — SLA waktu tempuh dan suhu.
- `produk/10-alur-pesan-pasok.md` — pesanan yang diterjemahkan jadi muatan trip.
