# Desktop Windows Gudang (Hari-1 Wajib)

## Tujuan

Dokumen ini menetapkan aplikasi desktop Windows sebagai tulang punggung operasional gudang sejak hari pertama pilot karena hanya PC gudang yang tersambung ke timbangan USB/serial dan printer thermal, sehingga penimbangan, cetak label, dan surat jalan harus bisa jalan penuh meski internet mati total.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung + Kepala Agregasi (bersama).
- Pengguna: Koordinator Timbang-Sortir dan Admin Gudang di 1 PC gudang (spesifikasi minimum Windows 10 x64, RAM 8 GB, SSD 256 GB).
- Teknisi: 1 orang PIC perangkat (timbangan, printer, kabel) yang dihubungi maksimal 4 jam bila alat mati.

## Keputusan Konkret

1. Target build tunggal: Windows x64 via Compose Multiplatform desktop, didistribusikan sebagai installer MSIX versi 1.0.0 mulai hari-1 pilot; update memakai paket MSIX baru yang dipasang manual oleh PIC (belum ada auto-update hari-1).
2. Perangkat wajib tersambung hari-1: 1 timbangan duduk USB/serial 150 kg (protokol bacaan berat per 500 ms, toleransi goyang ±100 gram), 1 printer thermal 80 mm untuk label keranjang dan surat jalan, 1 pemindai barkode USB untuk kode keranjang KRJ-001 s.d. KRJ-120. Contoh ritme kerja: timbang 25 keranjang @20 kg selesai dalam 20 menit termasuk cetak label.
3. Database lokal SQLite via SQLDelight sebagai sumber kebenaran operasional: tabel Lot, Sortir, Keranjang, Trip, SuratJalan tersimpan lokal dulu lalu disinkron ke Lumbung-Backend saat online (lihat `platform/60-offline-sinkron.md`). Batas toleransi offline 3 × 24 jam tanpa kehilangan data.
4. Alur layar desktop (Navigation3): Dasbor Hari Ini → Timbang Lot → Hasil Sortir → Cetak Label → Susun Trip → Cetak Surat Jalan → Arsip Kontrak. Setiap layar menampilkan status koneksi (Online/Offline + antrean sinkron N item) di bilah atas.
5. Cetakan baku: label keranjang 80×50 mm (kode petani, komoditas, grade, berat, tanggal) dan surat jalan A5 rangkap fungsi (cetak 1 lembar, fotokopi untuk penerima). Stok kertas thermal cadangan 10 rol @Rp35.000 selalu tersedia.

## Tautan ke File Terkait

- `platform/10-matriks-KMP-desktop-web.md` — posisi desktop dalam matriks.
- `platform/20-navigasi3.md` — pola navigasi desktop.
- `platform/60-offline-sinkron.md` — antrean sinkron SQLite→backend.
- `produk/31-kontrak-api-desktop-windows.md` — endpoint yang dipakai desktop.
- `produk/20-model-data.md` — skema tabel lokal SQLDelight.
- `agregasi/10-sop-sortir-grading.md` — SOP yang dieksekusi di aplikasi ini.
