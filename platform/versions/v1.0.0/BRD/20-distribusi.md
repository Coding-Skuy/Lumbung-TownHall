> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# BRD 20 — Distribusi Trip

## Konteks

Distribusi mencakup rute tetap, eksekusi trip harian, armada, dan kemasan. Sumber isi lama: `distribusi/10-desain-rute-trip.md`, `distribusi/20-sop-trip-harian.md`, `distribusi/30-armada-kemasan.md`.

## Kebutuhan Bisnis

- BR-201 Pola hub-spoke satu gudang dengan 3 rute tetap: Utara 12 km pulang-pergi muatan tipikal 500 kg 45 menit, Selatan 22 km muatan 650 kg 70 menit, Kota 8 km muatan 350 kg 40 menit.
- BR-202 Frekuensi: Utara dan Kota tiap hari; Selatan Senin, Rabu, Jumat. Kapasitas mingguan 7.900 kg.
- BR-203 Biaya per trip terbuka. Contoh Utara: BBM Rp60.000 ditambah sopir dan kernet Rp150.000 ditambah depresiasi Rp40.000 sama dengan Rp250.000 per trip. Dengan 500 kg maka biaya Rp500 per kg; fee Rp1.500 per kg memberi kontribusi Rp1.000 per kg.
- BR-204 Aturan muat: kangkung di atas, cabai di tengah, bawang di bawah; maksimal 2 susun keranjang 20 kg; terpal wajib bila hujan; muat maksimal 30 menit.
- BR-205 Surat jalan rangkap 2 memuat nomor trip, keranjang per komoditas grade, berat total, dan fee. Bukti terima berupa tanda tangan dan foto, tersinkron maksimal 2 jam setelah sinyal kembali. Toleransi telat 30 menit per titik.
- BR-206 Armada hari pertama: 1 pickup 800 kg, 1 motor roda tiga 350 kg, 1 pickup sewa cadangan Rp350.000 per hari. Utilisasi minimal 70 persen. Keranjang 20 kg 120 unit, karung jaring 10 kg 200 unit, kode permanen KRJ-001 sampai KRJ-120.

## Metrik

- Ketepatan tiba, jumlah insiden telat, susut jalan maksimal 2 persen, short pesanan. Tiga telat seminggu memicu review rute.

## Batasan

Batasan segmen ini: hanya angkut gudang ke penerima dalam radius 25 km. Di luar batas: last-mile ke konsumen akhir milik Pedaree dan penjualan ecer milik Pasaree. Belum ada cold chain aktif hari pertama; pengganti berupa keberangkatan maksimal 06.30 dan kain basah untuk kangkung.
