> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# FRD 10 — Kebutuhan Fungsional

Dokumen ini menyatakan apa yang wajib dilakukan sistem, tanpa menyatakan cara implementasi.

## Agregasi

- FR-001 Sistem wajib mencatat lot panen dengan kode petani, tanggal, komoditas, dan berat kotor.
- FR-002 Sistem wajib mencatat hasil sortir per lot dalam grade A, B, C dengan toleransi total 2 persen terhadap berat kotor.
- FR-003 Sistem wajib menolak Grade C masuk rantai dingin dan mencatat alihnya ke pasar lokal atau kanal olahan.
- FR-004 Sistem wajib mencetak label keranjang berisi kode petani, komoditas, grade, berat bersih, dan tanggal.
- FR-005 Sistem wajib mengelola kontrak mini 90 hari berisi komitmen per komoditas dan realisasi serapan.

## Distribusi

- FR-101 Sistem wajib mengelola 3 rute tetap beserta titik berurutan, jarak zona, dan kapasitas.
- FR-102 Sistem wajib menyusun muatan trip dari stok lot per grade dan menerbitkan surat jalan bernomor unik.
- FR-103 Sistem wajib mencatat tiba, berangkat, bukti foto dan tanda tangan per titik, serta insiden keterlambatan.
- FR-104 Sistem wajib mencatat kas jalan Rp300.000 per trip dan sisa setor hari yang sama.
- FR-105 Sistem wajib mengelola stok keranjang berkode permanen KRJ-001 sampai KRJ-120 dan status cuci serta pensiun.

## Keuangan

- FR-201 Sistem wajib menghitung fee per pesanan: Rp1.500 per kg zona dekat dan Rp2.500 per kg zona jauh.
- FR-202 Sistem wajib menerbitkan papan harga mingguan per komoditas per grade dengan tanggal berlaku Senin sampai Minggu.
- FR-203 Sistem wajib menerbitkan invoice fee mingguan per pembeli dengan jatuh tempo 7 hari dan denda 1 persen per minggu maksimal 4 persen.
- FR-204 Sistem wajib menghitung pembayaran petani H+1 dari berat bersih per grade dikali harga papan minggu berjalan.
- FR-205 Sistem wajib menghitung metrik keadilan harga: rasio petani, deviasi konsumen, ketepatan H+1, dan susut.

## Lintas Segmen

- FR-301 Sistem wajib memberi nomor rantai tunggal PSO-YYYYMMDD-NNN dari pesan sampai bayar.
- FR-302 Sistem wajib mencatat setiap aksi dengan pembuat, waktu, dan versi untuk resolusi konflik offline.
- FR-303 Sistem wajib menegakkan hak peran: petani hanya datanya sendiri, sopir hanya tripnya, admin melihat operasional, keuangan melihat invoice.

## Batasan

Batasan dokumen ini: hanya kebutuhan fungsional. Bahasa pemrograman, pustaka, basis data lokal, dan pola navigasi tidak diatur di sini dan hanya boleh muncul di FSD. Setiap kebutuhan di atas wajib punya uji penerimaan di PRD/30-kriteria.md.
