> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# PRD 10 — Pengguna Lumbung

## Daftar Peran

- Koordinator tani: merekrut petani, memverifikasi kontrak mini 90 hari, menindaklanjuti keterlambatan setor lebih dari 3 kali semusim, dan memimpin uji petik 5 keranjang per hari. Kebutuhan: daftar 40 petani, status kontrak, riwayat setoran.
- Admin gudang: mengonfirmasi pesanan maksimal 2 jam, menyusun trip H-1 sore, menerbitkan surat jalan, menagih fee mingguan, menerbitkan papan harga Jumat, dan memblokir perangkat hilang dalam 1 jam. Kebutuhan: dasbor hari ini, stok lot per grade, antrean sinkron.
- Sopir: menjalankan trip berurutan, mencatat tiba dan berangkat per titik, mengunggah foto dan tanda tangan bukti terima, melaporkan insiden. Kebutuhan: daftar trip hari ini, navigasi titik, mode offline penuh dengan sinkron maksimal 2 jam.
- Vendor: dapur Pawon dan pedagang lapak pasar sebagai pembeli. Kebutuhan: memesan H-1 pukul 15.00, menerima H pukul 09.00, melihat fee terpisah dari harga papan, membayar invoice 7 hari, dan mendapat prioritas muat bila short melebihi 10 persen volume mingguan.

## Hak Akses

- Petani hanya melihat kontrak, rencana setoran, pembayaran, dan papan harganya sendiri. Sopir hanya melihat tripnya hari itu. Admin gudang melihat seluruh lot, trip, dan log konflik. Admin keuangan melihat invoice dan rekap. Tidak ada akun bersama: 1 orang 1 akun.
- Autentikasi: JWT akses 15 menit, refresh 7 hari, PIN 6 digit diganti 90 hari, API key perangkat terdaftar maksimal 2 per petani dan 1 per sopir, service key untuk web server-ke-server dirotasi 90 hari. Tiga salah PIN mengunci 15 menit.

## Batasan

Batasan dokumen ini: hanya peran, kebutuhan pandang, dan hak akses. Aturan bisnis rinci ada di BRD, langkah sistem ada di FSD. Di luar batas: peran dapur pengolah dan kasir pasar yang diatur TownHall masing-masing.
