> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# Lumbung-TownHall — Divisi Hulu (Supply & Distribution) PT ChefGenie

## Peran Lumbung

Lumbung adalah divisi hulu PT ChefGenie: agregasi panen hortikultura dari petani mitra dan distribusi ke dapur serta pasar. Fokus Lumbung-first: cabai rawit merah, bawang merah, sayur daun (diwakili kangkung). Skala pilot: 40 petani mitra dalam radius 25 km, serapan 2 ton per hari. Sukses = keadilan harga: adil bagi petani, stabil bagi konsumen. Monetisasi tunggal: fee logistik transparan Rp1.500 per kg untuk rute kurang dari 15 km dan Rp2.500 per kg untuk rute 15 sampai 25 km, ditagih ke pembeli, tidak dipotong dari petani. Susut total ditargetkan di bawah 5 persen rata-rata tertimbang. Basis data: DB lumbung. Autentikasi: JWT akses 15 menit ditambah refresh 7 hari ditambah API key perangkat ditambah service key antar layanan.

## Peta Versi Aktif

- Versi aktif: v1.0.0 (disetujui). Isi beku ada di `versions/v1.0.0/`.
- `versions/v1.0.0/CHANGELOG.md` — ringkasan versi awal.
- `versions/v1.0.0/BRD/` — kebutuhan bisnis BR-001 dan seterusnya.
- `versions/v1.0.0/PRD/` — pengguna dan kriteria US-001 dan seterusnya.
- `versions/v1.0.0/FRD/` — kebutuhan fungsional FR-001 dan seterusnya.
- `versions/v1.0.0/FSD/` — rancangan alur, model data Panen, Lot, Trip, Timbangan, Fee, dan kontrak API.
- `versions/v1.0.0/SNAPSHOT-ROADMAP.md` — salinan beku janji v1.0.0.
- Peta hidup lintas versi ada di `roadmap/`: `TIMELINE.md`, `MILESTONE.md`, `ROADMAP.md`.

## Cara Baca History

1. Mulai dari `versions/v1.0.0/CHANGELOG.md` untuk ringkasan versi.
2. Lanjut ke `versions/v1.0.0/BRD/00-ikhtisar.md` untuk konteks bisnis, lalu `PRD/10-pengguna.md` untuk peran.
3. Untuk janji waktu itu, baca `versions/v1.0.0/SNAPSHOT-ROADMAP.md` yang sudah dibekukan dan tidak diubah lagi.
4. Untuk kondisi terkini lintas versi, baca `roadmap/TIMELINE.md` dan `roadmap/MILESTONE.md`.
5. Riwayat perubahan antar versi dilacak lewat `git log` dan `CHANGELOG.md` tiap versi. File lama sengaja dihapus setelah dipindah dengan `git mv` agar tidak ada dua sumber kebenaran.

## TownHall Lain dan Pedoman Induk

Pedoman induk: https://github.com/Coding-Skuy/ChefGenie-TownHall.

Lima TownHall lain yang meniru pola template emas ini:

- https://github.com/Coding-Skuy/Pawonee-TownHall — dapur dan pengolahan, pembeli utama Lumbung.
- https://github.com/Coding-Skuy/Pasaree-TownHall — pasar dan penjualan.
- https://github.com/Coding-Skuy/Pedaree-TownHall — pengantar dan last-mile.
- https://github.com/Coding-Skuy/TitipO-TownHall — titip dan kemitraan.
- https://github.com/Coding-Skuy/Titeny-TownHall — ketelitian dan audit mutu.

Pola yang ditiru: penamaan `versions/vX.Y.Z/BRD|PRD|FRD|FSD/`, file `NN-nama-kebab.md`, header versi satu baris, dan bagian Batasan di tiap file.

## Batasan

Batasan ruang lingkup repo ini: hanya agregasi hortikultura, distribusi trip, fee per kg, papan harga, dan kontrak API Lumbung. Di luar batas: resep dapur milik Pawonee, harga ecer pasar milik Pasaree, routing last-mile milik Pedaree, skema titip milik TitipO, dan audit independen milik Titeny. Komoditas di luar cabai, bawang, dan sayur daun masuk versi berikutnya setelah pilot lulus.
