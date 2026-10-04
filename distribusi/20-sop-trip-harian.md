# SOP Trip Harian

## Tujuan

Dokumen ini mengatur urutan kerja harian setiap trip distribusi mulai dari serah-terima muatan di gudang sampai bukti terima di titik tujuan, agar tidak ada kilogram yang hilang tanpa catatan dan setiap keterlambatan terpantau dalam hitungan menit, bukan hari.

## Pemilik / Peran

- Pemilik dokumen: Mandor Trip.
- Pelaksana: Sopir (kemudi + bukti foto), Kernet (muat/bongkar + cek keranjang).
- Penerima: Penanggung jawab dapur Pawon dan pedagang lapak pasar.

## Keputusan Konkret

1. Timeline baku trip pagi (contoh Rute Utara): 05.30 apel + cek kendaraan, 06.00–06.30 muat 25 keranjang @20 kg, 06.30 berangkat, 07.15 tiba dapur Pawon 1 (bongkar 100 kg), 07.45 tiba dapur Pawon 2 (bongkar 150 kg), 08.15 tiba lapak pasar (bongkar 250 kg), 09.00 kembali gudang + setoran bukti terima.
2. Dokumen wajib tiap trip: surat jalan rangkap 2 (1 arsip gudang, 1 penerima) berisi nomor trip, daftar keranjang per komoditas-grade, berat total, dan fee yang ditagih. Surat jalan dicetak dari aplikasi desktop gudang sebelum muat.
3. Bukti terima berupa tanda tangan + foto keranjang terbongkar di aplikasi mobile KMP sopir; bila offline, foto dan tanda tangan digital tersimpan lokal lalu tersinkron maksimal 2 jam setelah kembali ke area sinyal (lihat `platform/60-offline-sinkron.md`).
4. Toleransi keterlambatan 30 menit per titik; lebih dari itu sopir wajib menelepon penerima dan Mandor Trip mencatat insiden. Tiga insiden terlambat dalam seminggu memicu review rute oleh Kepala Agregasi.
5. Kehilangan/rusak di jalan dilaporkan saat itu juga; ganti rugi ke pembeli maksimal 1× nilai fee trip tersebut, sedangkan susut alami >2% per trip diinvestigasi (lihat `metrik/20-susut-dan-sla.md`).
6. Kas jalan per trip Rp300.000 (BBM + parkir + tak terduga); sisa wajib disetor kembali ke admin gudang hari yang sama dengan struk.

## Tautan ke File Terkait

- `distribusi/10-desain-rute-trip.md` — rute tetap dan kapasitas mingguan.
- `distribusi/30-armada-kemasan.md` — standar kendaraan dan keranjang.
- `metrik/20-susut-dan-sla.md` — batas susut dan SLA keterlambatan.
- `platform/40-mobile-KMP.md` — aplikasi mobile sopir untuk bukti terima.
- `platform/60-offline-sinkron.md` — sinkronisasi bukti saat offline.
