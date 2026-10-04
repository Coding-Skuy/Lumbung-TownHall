> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# FSD 10 — Alur Sistem

## Urutan Tulis Lokal Dahulu

1. Perangkat menulis ke basis lokal dahulu dalam kurang dari 200 ms dengan UUID v4, lalu menampilkan sukses tanpa menunggu server.
2. Antrean outbox FIFO diproses saat online dengan retry 1, 5, 15 menit. Batch 25 keranjang kurang dari 100 KB tersinkron kurang dari 30 detik pada 1 Mbps; foto menyusul dan boleh menunggu WiFi bila antrean melebihi 10 MB.
3. Nomor sementara TMP-8-karakter dipakai saat offline untuk lot dan surat jalan, lalu dipetakan ke nomor resmi server SJ-YYYYMMDD-NNN dan L-NNNN saat catch-up maksimal 200 rekaman per request.
4. Resolusi konflik: gudang menang untuk berat dan grade; lapangan menang untuk bukti terima dan posisi. Setiap konflik dicatat di log dan diberi tahu ke pihak kalah.
5. Batas darurat: offline lebih dari 3 kali 24 jam mengunci penerbitan surat jalan baru tetapi tetap mengizinkan timbang dan bukti. Cadangan SQLite diekspor ke flashdisk tiap Jumat sore.

## Urutan Layar Gudang dan Lapangan

- Gudang: Dasbor Hari Ini, Timbang Lot, Hasil Sortir, Cetak Label, Susun Trip, Cetak Surat Jalan, Arsip Kontrak. Bilah atas selalu menampilkan Online atau Offline dan jumlah antrean.
- Sopir: Trip Hari Ini, Titik Aktif, Bukti Terima, Insiden. GPS dicatat tiap 5 menit hanya selama trip aktif.
- Petani: Kontrak Saya, Rencana Setoran, Pembayaran Saya, Papan Harga. Petani tidak dapat mengubah harga.
- Web publik tanpa login: papan harga dan profil. Web admin dengan sesi peran: rekap harian, invoice, mitra, insiden. Web tidak menghitung ulang fee atau grade.

## Batasan

Batasan dokumen ini: hanya urutan sistem dan aturan sinkron. Formula bisnis ada di FSD model data dan kontrak. Di luar batas: desain visual dan merek. Target mutu: cakupan uji navigasi 100 persen untuk alur timbang sampai surat jalan sebelum pilot.
