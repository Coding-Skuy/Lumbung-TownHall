# Navigasi 3 (Navigation3)

## Tujuan

Dokumen ini menetapkan pola navigasi Navigation3 yang dipakai di seluruh aplikasi Compose Multiplatform Lumbung (mobile dan desktop) agar alur layar bersifat state-driven dan bisa diuji tanpa emulator: setiap perpindahan layar adalah perubahan data backstack yang eksplisit, bukan panggilan imperatif tersebar.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung (khusus KMP/Compose).
- Pengguna: engineer mobile dan desktop; reviewer memastikan tidak ada `navigate()` imperatif di luar NavDisplay.
- Contoh acuan: modul `shared-core` dan aplikasi contoh di repo Lumbung-Backend tidak menyentuh navigasi (navigasi murni sisi klien).

## Keputusan Konkret

1. Setiap aplikasi mendefinisikan sealed interface `Route` per alur (contoh gudang: `Timbang`, `Sortir(lotId)`, `CetakLabel(lotId)`, `SuratJalan(tripId)`; contoh sopir: `TripAktif(tripId)`, `BuktiTerima(titikId)`), dan satu `SnapshotStateList<Route>` sebagai backstack tunggal per jendela.
2. Seluruh transisi memakai `NavDisplay(backstack, onBack)`; tombol kembali Android dan tombol tutup desktop memanggil `backstack.removeLastOrNull()` yang sama sehingga perilaku konsisten. Dilarang memakai NavController lama atau startActivity/intent manual untuk pindah layar utama.
3. Contoh alur gudang: `Timbang → Sortir(lot-8812) → CetakLabel(lot-8812) → SuratJalan(trip-UT-041)` setara dengan backstack berisi 4 entry; bila timbangan USB terputus di tengah, entry teratas diganti `GangguanAlat(pesan)` tanpa menghancurkan data timbang yang sudah masuk.
4. Deep link terbatas dua skema: `lumbung://trip/{tripId}` (dibuka sopir dari pesan) dan `lumbung://lot/{lotId}` (dibuka petugas gudang dari hasil pindai), masing-masing diterjemahkan menjadi 1–2 entry backstack awal, bukan tumpukan penuh.
5. Pengujian: tiap perubahan backstack wajib punya unit test di `shared-core` memakai daftar biasa (tanpa Compose) yang menegaskan urutan entry; target cakupan navigasi 100% untuk alur timbang-sampai-surat-jalan sebelum pilot.

## Tautan ke File Terkait

- `platform/10-matriks-KMP-desktop-web.md` — di mana Navigation3 dipakai.
- `platform/30-desktop-windows-gudang.md` — alur layar desktop gudang.
- `platform/40-mobile-KMP.md` — alur layar mobile sopir/petani.
- `produk/40-modul-KMP-bersama.md` — lokasi definisi Route bersama.
- `produk/20-model-data.md` — entitas Lot dan Trip yang dirujuk Route.
