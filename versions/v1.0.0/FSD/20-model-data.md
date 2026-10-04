> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# FSD 20 — Model Data

## Entitas Inti

- Panen: id UUID, kode petani PTN-NNN, tanggal, komoditas enum cabai, bawang, kangkung, berat kotor gram integer. Contoh: lot L-8812 petani PTN-007 Slamet cabai 6 Okt 2026 kotor 120.000 gram.
- Lot: kode L-NNNN, rujukan panen, status enum BARU, DISORTIR, DIMUAT, DITERIMA. Setiap lot membawa uuid, dibuat_pada dengan offset, dibuat_oleh, versi mulai 1.
- Timbangan: id UUID, lot id, jenis KOTOR atau BERSIH, berat gram integer, petugas, waktu. Aturan: total sortir A ditambah B ditambah C wajib sama dengan kotor dalam 2 persen, contoh sortir L-8812: A 100.000 gram, B 14.000 gram, C 6.000 gram.
- Trip: kode TRIP-RUTE-NNN contoh TRIP-UT-041, rute enum UTARA, SELATAN, KOTA, kendaraan, kas jalan 300.000, status enum DISUSUN, BERJALAN, SELESAI. Titik trip berurutan dengan waktu tiba dan berangkat.
- Fee: id UUID, rujukan pesanan PSO-YYYYMMDD-NNN, berat gram, zona DEKAT atau JAUH, tarif 1.500 atau 2.500 per kg, nominal rupiah integer. Contoh 170.000 gram zona dekat menjadi 170 dikali 1.500 sama dengan 255.000.
- Entitas pendukung: Petani, Kontrak musim 90 hari, Keranjang KRJ-NNN, Pesanan dengan item per grade, Pembayaran H+1, Insiden INS-YYYYMMDD-NNN.

## Aturan Angka

- Berat selalu gram integer, uang selalu rupiah integer, grade enum A, B, C, status pesanan enum BARU, DIKONFIRMASI, DIMUAT, DIANTAR, DITERIMA, SHORT, BATAL.
- Retensi: lot dan pembayaran minimal 2 tahun; foto maksimal 500 KB disimpan 1 tahun lalu hanya metadata.

## Batasan

Batasan dokumen ini: hanya definisi entitas, kunci, enum, dan aturan angka. Serialisasi JSON dan endpoint ada di `30-kontrak.md`. Perubahan skema butuh persetujuan Tech Lead dan migrasi teruji.
