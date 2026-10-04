> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# CHANGELOG v1.0.0 — Versi Awal Lumbung

## Ringkasan Isi

v1.0.0 adalah versi awal TownHall Lumbung yang dibekukan sebagai template emas. Seluruh isi lama dari folder `agregasi/`, `distribusi/`, `keuangan/`, `platform/`, `produk/`, `metrik/`, dan `roadmap/` dipecah dan dipindah dengan `git mv` ke struktur versi ini, lalu folder lama dihapus agar hanya ada satu sumber kebenaran.

## Isi per Direktori

- BRD: `00-ikhtisar.md` memuat piagam, skala 40 petani dan 2 ton per hari, dan prinsip fee murni. `10-agregasi.md` memuat sortir grading cabai, bawang, kangkung dan kontrak mini 90 hari. `20-distribusi.md` memuat 3 rute tetap, pola hub-spoke, dan armada. `30-keuangan-fee.md` memuat tarif Rp1.500 dan Rp2.500 per kg, papan harga Jumat, dan titik impas 600 kg per hari.
- PRD: `10-pengguna.md` memuat 4 peran: koordinator tani, admin gudang, sopir, vendor. `20-alur.md` memuat alur pesan sampai bayar H+1. `30-kriteria.md` memuat US-001 dan seterusnya, acceptance, dan non-goals.
- FRD: `10-fungsional.md` memuat FR-001 dan seterusnya per segmen agregasi, distribusi, keuangan, tanpa cara implementasi.
- FSD: `10-alur.md` memuat urutan sistem, `20-model-data.md` memuat entitas Panen, Lot, Trip, Timbangan, Fee, `30-kontrak.md` memuat kontrak API per konsumen, event, error, dan autentikasi JWT 15 menit, refresh 7 hari, API key perangkat, service key.
- `SNAPSHOT-ROADMAP.md` memuat salinan beku janji pilot 90 hari.

## Sumber Pemindahan

- `agregasi/00-piagam-agregasi.md` menjadi BRD ikhtisar. `agregasi/10-sop-sortir-grading.md` menjadi BRD agregasi. `distribusi/10-desain-rute-trip.md` menjadi BRD distribusi. `keuangan/10-model-fee-per-kg.md` menjadi BRD keuangan.
- `platform/30-desktop-windows-gudang.md` dan `metrik/10-keadilan-harga.md` menjadi PRD pengguna dan kriteria. `produk/10-alur-pesan-pasok.md` dan `produk/20-model-data.md` menjadi FSD alur dan model data. Kontrak API tiga konsumen digabung ke FSD kontrak.

## Batasan

Batasan versi ini: hanya hortikultura cabai, bawang, dan sayur daun untuk radius 25 km. Perubahan setelah ini wajib masuk v1.1.0 atau v2.0.0 dan dicatat di `roadmap/` living, bukan dengan mengubah file beku ini.
