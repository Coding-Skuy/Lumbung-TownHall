# Model Data Lumbung

## Tujuan

Dokumen ini menetapkan model data kanonis Lumbung yang dipakai identik oleh modul KMP bersama, database lokal SQLDelight, backend, dan web, sehingga satu kilogram cabai punya identitas dan makna yang sama dari timbangan gudang sampai invoice fee.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung.
- Pengguna: engineer backend (repo `Coding-Skuy/Lumbung-Backend`), engineer KMP, engineer web.
- Perubahan skema butuh persetujuan Tech Lead + migrasi SQLDelight teruji.

## Keputusan Konkret

1. Delapan entitas inti dengan kunci UUID v4: Petani (kode `PTN-NNN`, nama, kontak, titik kumpul), Kontrak (petani, musim 90 hari, komitmen kg per komoditas), Lot (kode `L-NNNN`, petani, tanggal, komoditas, berat kotor), Sortir (lot, grade A/B/C kg, petugas, waktu), Keranjang (kode `KRJ-NNN`, lot, grade, berat bersih), Trip (kode `TRIP-{RUTE}-NNN`, rute, kendaraan, kas jalan), Pesanan (kode `PSO-*`, pembeli, item, fee), Pembayaran (pesanan/kontrak, nominal, H+1, status).
2. Contoh rekaman konkret: Lot `L-8812` = petani `PTN-007` (Slamet, cabai), 6 Okt 2026, kotor 120 kg → Sortir: A 100 kg, B 14 kg, C 6 kg → 5 keranjang `KRJ-041` s.d. `KRJ-045` @20 kg Grade A → dimuat ke `TRIP-UT-041` memenuhi pesanan `PSO-20261010-014` (100 kg cabai A).
3. Aturan angka: semua berat disimpan dalam gram (integer, contoh 20.000 g) untuk menghindari galat desimal; semua uang dalam rupiah integer; grade hanya enum `A|B|C`; status pesanan enum `BARU|DIKONFIRMASI|DIMUAT|DIANTAR|DITERIMA|SHORT|BATAL`.
4. Setiap entitas yang dibuat di perangkat membawa `uuid`, `dibuat_pada` (waktu lokal + offset), `dibuat_oleh` (id perangkat/pengguna), dan `versi` (mulai 1, naik tiap sinkron) untuk mendukung resolusi konflik offline (lihat `platform/60-offline-sinkron.md`).
5. Retensi: data lot dan pembayaran disimpan minimal 2 tahun untuk audit keadilan harga; foto bukti terima dikompresi maksimal 500 KB dan disimpan 1 tahun, setelah itu hanya metadata (kode trip, waktu, penerima) yang dipertahankan.

## Tautan ke File Terkait

- `produk/10-alur-pesan-pasok.md` — alur yang memakai entitas ini.
- `produk/40-modul-KMP-bersama.md` — implementasi model di Kotlin.
- `produk/30-kontrak-api-KMP-mobile.md`, `produk/31-kontrak-api-desktop-windows.md`, `produk/32-kontrak-api-web-bun.md` — serialisasi JSON per konsumen.
- `platform/60-offline-sinkron.md` — kolom UUID dan versi untuk sinkron.
- `metrik/10-keadilan-harga.md` — agregasi harga dari data ini.
