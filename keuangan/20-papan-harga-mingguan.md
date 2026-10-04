# Papan Harga Mingguan

## Tujuan

Dokumen ini mengatur cara Lumbung menetapkan dan mengumumkan harga papan mingguan per komoditas per grade agar petani, dapur, dan pasar bertransaksi dengan acuan yang sama, diperbarui rutin, dan bisa diaudit siapa pun tanpa perlu bertanya lewat pesan pribadi.

## Pemilik / Peran

- Pemilik dokumen: Kepala Keuangan Lumbung (penetap akhir).
- Penyusun: Admin Gudang (mengumpulkan 3 harga pasar referensi tiap Jumat), Kepala Agregasi (memverifikasi).
- Penerima: seluruh petani mitra, dapur Pawon, pedagang pasar (via web, cetakan gudang, dan pesan siaran).

## Keputusan Konkret

1. Harga papan dihitung tiap Jumat pukul 15.00 dengan formula: median 3 harga pasar referensi (Pasar Induk, pasar kota, harga eceran daring) dikurangi 10% buffer logistik, dibulatkan ke bawah ke kelipatan Rp500. Contoh: referensi cabai Rp36.000, Rp34.000, Rp35.000 → median Rp35.000 − 10% = Rp31.500 → papan Rp31.500/kg.
2. Contoh papan minggu 6–12 Oktober 2026: cabai rawit merah Grade A Rp31.500/kg (B Rp26.775 → dibulatkan Rp26.500), bawang merah Grade A Rp28.000/kg (B Rp23.800 → Rp23.500), kangkung Grade A Rp6.000/kg (B Rp5.100 → Rp5.000). Berlaku Senin–Minggu, tidak berubah di tengah minggu kecuali bencana.
3. Publikasi tiga jalur serentak maksimal pukul 17.00 Jumat: halaman web papan harga (lihat `platform/50-web-bun-svelte.md`), cetakan A3 ditempel di pintu gudang, dan siaran pesan ke grup petani. Keterlambatan publikasi >2 jam dicatat sebagai insiden SLA.
4. Sengketa harga diselesaikan dengan menunjukkan lembar kerja perhitungan (3 referensi + tanggal survei) yang disimpan Admin Gudang minimal 6 bulan; petani boleh meminta salinan fotokopi gratis 1 kali per bulan.
5. Harga papan mengikat kontrak mini musim sebagai acuan pembayaran Grade A/B minggu berjalan, sedangkan fee logistik dicantumkan terpisah di bawah papan (Zona Dekat Rp1.500/kg, Zona Jauh Rp2.500/kg) agar tidak tercampur.

## Tautan ke File Terkait

- `keuangan/10-model-fee-per-kg.md` — tarif fee yang diumumkan bersama papan.
- `agregasi/20-kontrak-mini-musim.md` — kontrak yang mengacu ke papan ini.
- `agregasi/10-sop-sortir-grading.md` — definisi grade A/B di papan.
- `platform/50-web-bun-svelte.md` — halaman web papan harga publik.
- `metrik/10-keadilan-harga.md` — metrik deviasi harga terhadap pasar.
