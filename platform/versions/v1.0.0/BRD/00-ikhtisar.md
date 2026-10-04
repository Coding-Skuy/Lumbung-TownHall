> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# BRD 00 — Ikhtisar Lumbung

## Konteks

Divisi Lumbung adalah hulu PT ChefGenie. Tugasnya mengumpulkan panen hortikultura dari petani mitra dan menyalurkannya ke dapur Pawon serta pasar. Komoditas hari pertama: cabai rawit merah, bawang merah, kangkung sebagai wakil sayur daun. Prinsip Lumbung-first: petani menerima harga adil, konsumen membayar harga stabil. Basis data tunggal: DB lumbung.

## Kebutuhan Bisnis

- BR-001 Lumbung wajib menyerap 2 ton per hari dari 40 petani mitra radius 25 km pada akhir pilot 90 hari.
- BR-002 Harga ke petani mengacu papan harga mingguan ditambah premi grade: Grade A 100 persen, Grade B 85 persen, Grade C ditolak dari rantai dingin.
- BR-003 Pendapatan Lumbung hanya fee logistik transparan: Rp1.500 per kg rute kurang dari 15 km dan Rp2.500 per kg rute 15 sampai 25 km, ditagih ke pembeli.
- BR-004 Sukses diukur sebagai keadilan harga: rasio harga petani terhadap median pasar minimal 85 persen, deviasi harga konsumen maksimal 10 persen, ketepatan bayar H+1 minimal 95 persen.
- BR-005 Susut total rata-rata tertimbang di bawah 5 persen, dengan pagu sortir cabai 6 persen, bawang 4 persen, kangkung 8 persen, dan susut jalan maksimal 2 persen per trip.
- BR-006 Operasional gudang 04.00 sampai 14.00, batas terima panen pukul 10.00, kecuali kangkung maju ke pukul 08.00 bila susut lewat pagu.
- BR-007 Autentikasi lixo: JWT akses 15 menit, refresh 7 hari, API key perangkat, service key antar layanan, tanpa akun bersama.

## Metrik

- Serapan harian kilogram per komoditas. Fee tertagih per minggu. Rasio petani, deviasi konsumen, ketepatan H+1. Susut sortir dan susut jalan. Antrean sinkron tidak pernah melebihi 200 item.

## Batasan

Batasan dokumen ini: hanya menyatakan kebutuhan bisnis dan angka ambang. Cara pemenuhan diatur di PRD, FRD, dan FSD. Di luar batas: penentuan resep, penjualan ecer, dan audit independen yang menjadi milik TownHall lain.
