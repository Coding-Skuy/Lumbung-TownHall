# Autentikasi Pengguna & Perangkat

## Tujuan

Dokumen ini menetapkan cara setiap manusia dan setiap perangkat membuktikan identitasnya ke Lumbung-Backend agar petani hanya melihat datanya sendiri, sopir hanya melihat tripnya, dan bila HP hilang atau PC gudang disalahgunakan, akses bisa dicabut dalam hitungan menit tanpa mengganggu operasional yang lain.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung (teknis) + Kepala Agregasi (otorisasi peran).
- Subjek: 40 akun petani, 4 akun sopir/kernet, 3 akun gudang (2 operator + 1 admin), 2 akun admin web; tiap akun terikat ke perangkat terdaftar.
- Penindak pencabutan: Admin Gudang (blokir perangkat), Tech Lead (rotasi kunci API web).

## Keputusan Konkret

1. Tiga lapis kredensial: (a) akun peran (contoh `sopir-02`, `PTN-007`) + PIN 6 digit yang diganti 90 hari; (b) token perangkat berumur 30 hari untuk mobile dan 12 jam (token shift) untuk desktop gudang; (c) kunci API server-ke-server untuk web SvelteKit yang dirotasi 90 hari. Tidak ada yang login hanya dengan nama.
2. Pendaftaran perangkat: petani didaftarkan Admin Gudang saat tanda tangan kontrak (1 akun = maksimal 2 perangkat, contoh HP pribadi + HP anak); sopir 1 akun = 1 HP dinas; PC gudang didaftarkan permanen lewat sidik perangkat + segel fisik (stiker "PC GUDANG-01"). Perangkat baru butuh persetujuan Admin Gudang maksimal 1 × 24 jam.
3. Contoh respons login sopir: `{"token":"…","berlaku_sampai":"+30 hari","peran":"sopir","trip_hari_ini":["TRIP-UT-041"]}` — token hanya membuka endpoint perannya (sopir tidak bisa memanggil endpoint admin gudang; backend menolak dengan 403 dan mencatat percobaan).
4. Kehilangan/keluar: petani lapor via telepon ke Admin Gudang → blokir perangkat dalam 1 jam, PIN baru diterbitkan saat datang ke gudang dengan KTP; sopir keluar → akun dinonaktifkan hari yang sama dan HP dinas direset; 3 salah PIN mengunci akun 15 menit.
5. Audit: setiap login, penerbitan token, dan penolakan 403 tercatat (siapa, perangkat, waktu); log disimpan 1 tahun dan dibuka ke Finance PT ChefGenie saat audit bulanan. Tidak ada akun bersama — 1 orang 1 akun, tanpa kecuali.

## Tautan ke File Terkait

- `produk/30-kontrak-api-KMP-mobile.md` — pemakaian token di mobile.
- `produk/31-kontrak-api-desktop-windows.md` — token shift desktop + PIN.
- `produk/32-kontrak-api-web-bun.md` — kunci API web server-side.
- `platform/40-mobile-KMP.md` — alur login di aplikasi.
- `agregasi/20-kontrak-mini-musim.md` — momen pendaftaran perangkat petani.
