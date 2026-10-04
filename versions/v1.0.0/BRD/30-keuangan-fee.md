> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# BRD 30 — Keuangan dan Fee

## Konteks

Keuangan Lumbung hanya dari fee logistik murni per kg. Tidak ada margin dari selisih harga. Sumber isi lama: `keuangan/10-model-fee-per-kg.md`, `keuangan/20-papan-harga-mingguan.md`.

## Kebutuhan Bisnis

- BR-301 Tarif dua zona: dekat kurang dari 15 km Rp1.500 per kg, jauh 15 sampai 25 km Rp2.500 per kg, sama untuk tiga komoditas.
- BR-302 Fee ditagih ke pembeli, tidak dipotong dari petani. Invoice mingguan tiap Senin untuk surat jalan minggu sebelumnya, jatuh tempo 7 hari, denda 1 persen per minggu maksimal 4 persen.
- BR-303 Contoh transparansi 1 kg cabai Grade A rute Utara: petani terima Rp32.000, pembeli bayar Rp32.000 ditambah fee Rp1.500 ditambah retribusi Rp500 sama dengan Rp34.000.
- BR-304 Titik impas: biaya tetap Rp18.000.000 per bulan dibagi kontribusi Rp1.000 per kg sama dengan 18.000 kg per bulan atau 600 kg per hari. Target 2 ton per hari memberi surplus sekitar Rp42.000.000 per bulan.
- BR-305 Papan harga dihitung tiap Jumat 15.00: median 3 referensi dikurangi 10 persen buffer, dibulatkan ke bawah kelipatan Rp500. Contoh papan 6 sampai 12 Okt 2026: cabai A Rp31.500 B Rp26.500, bawang A Rp28.000 B Rp23.500, kangkung A Rp6.000 B Rp5.000.
- BR-306 Publikasi tiga jalur maksimal Jumat 17.00: halaman web, cetakan A3 di pintu gudang, siaran grup petani. Penyesuaian tarif maksimal 1 kali per semester maksimal 10 persen dengan pemberitahuan 30 hari.

## Metrik

- Fee tertagih, piutang lewat jatuh tempo, deviasi konsumen, rasio petani. Lembar kerja 3 referensi disimpan 6 bulan.

## Batasan

Batasan segmen ini: hanya fee, papan harga, invoice, dan pembayaran petani H+1. Di luar batas: pembukuan PT induk, pajak, dan pinjaman. Harga papan mengikat sebagai acuan Grade A dan B minggu berjalan; fee dicantumkan terpisah agar tidak tercampur.
