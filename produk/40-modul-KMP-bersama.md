# Modul KMP Bersama (shared-core)

## Tujuan

Dokumen ini menetapkan isi dan batas modul Kotlin Multiplatform bersama (`shared-core`) sebagai satu-satunya rumah logika bisnis Lumbung — perhitungan fee, validasi grade, nomor rantai pesanan, dan model data — agar desktop, mobile, dan backend-mock menghitung dengan kode yang sama persis dan tidak pernah berbeda hasil.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung.
- Kontributor: engineer KMP; setiap PR ke `shared-core` butuh 1 reviewer selain penulis.
- Konsumen: aplikasi desktop Windows, aplikasi mobile Android+iOS, dan harness uji backend.

## Keputusan Konkret

1. Struktur paket dikunci: `core.model` (data class 8 entitas + enum Grade/Status, berat gram integer), `core.pricing` (`FeeCalculator` zona dekat/jauh + `PapanHarga` median−10% + pembulatan Rp500), `core.grading` (aturan ambang per komoditas + validasi total sortir ±2%), `core.sync` (UUID, outbox FIFO, pemetaan nomor sementara `TMP-*`), `core.nav` (sealed interface Route untuk Navigation3).
2. Contoh fungsi kanonis: `FeeCalculator.hitung(beratG: Long, zona: Zona): Long` — 170.000 g Zona Dekat → `170 × 1.500 = 255.000`; `PapanHarga.hitung(median: Long)` — median 35.000 → `(35.000 × 0,9) = 31.500` lalu bulatkan ke bawah kelipatan 500. Kedua fungsi pure (tanpa I/O) dan diuji 100% branch.
3. Aturan dependensi: `shared-core` hanya bergantung ke Kotlin stdlib + kotlinx-datetime + kotlinx-serialization; dilarang bergantung ke Compose, SQLDelight, Ktor, atau API platform — adaptor platform tinggal di modul aplikasi masing-masing. Pelanggaran gagal di check build.
4. Versi dan rilis: `shared-core` berversi semantik (mulai 1.0.0 di pilot); perubahan formula fee/papan menaikkan MINOR dan wajib dicatat di `CHANGELOG-shared-core.md` (contoh entri: "1.1.0 — tambah zona jauh 15–25 km Rp2.500/kg").
5. Target mutu: 0 logika harga/grade di luar `shared-core` (diperiksa via review + pencarian kode tiap sprint), cakupan uji unit minimal 85%, dan benchmark `FeeCalculator` 10.000 hitungan <100 ms di HP entry-level.

## Tautan ke File Terkait

- `platform/10-matriks-KMP-desktop-web.md` — mandat "tulis sekali di shared-core".
- `produk/20-model-data.md` — model yang diimplementasikan di `core.model`.
- `keuangan/10-model-fee-per-kg.md` — formula yang dikodekan di `core.pricing`.
- `agregasi/10-sop-sortir-grading.md` — ambang grade di `core.grading`.
- `platform/20-navigasi3.md` — Route di `core.nav`.
