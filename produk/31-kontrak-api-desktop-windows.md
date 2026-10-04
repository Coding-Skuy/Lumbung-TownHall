# Kontrak API untuk Desktop Windows

## Tujuan

Dokumen ini menetapkan kontrak endpoint Lumbung-Backend yang dikonsumsi aplikasi desktop Windows gudang agar operasi timbang-sortir-cetak yang volume datanya besar dan butuh nomor urut server (surat jalan, label) berjalan andal, bisa batch, dan tetap aman saat sinkronisasi mengejar setelah offline lama.

## Pemilik / Peran

- Pemilik dokumen: Tech Lead Lumbung (sisi konsumen); implementasi server di repo `Coding-Skuy/Lumbung-Backend`.
- Konsumen: 1 PC gudang (aplikasi desktop Windows x64 MSIX).
- SLA: batch 25 keranjang tersinkron <30 detik di koneksi 1 Mbps; nomor surat jalan dijamin unik server-side.

## Keputusan Konkret

1. Basis sama dengan mobile (`https://api.lumbung.chefgenie.id/v1`) tetapi memakai kredensial perangkat gudang tetap + PIN operator per shift; contoh login shift: `POST /v1/gudang/masuk` → token shift 12 jam untuk `OPR-SORTIR-1`.
2. Endpoint gudang (7): `POST /v1/lot` (buat lot + timbang kotor), `POST /v1/lot/{id}/sortir` (hasil A/B/C), `POST /v1/keranjang/batch` (maksimal 50 keranjang per request, contoh 25 × @20 kg = 500 kg), `POST /v1/trip` + `POST /v1/trip/{id}/surat-jalan` (server menerbitkan nomor `SJ-YYYYMMDD-NNN`), `GET /v1/stok-lot` (sisa lot per grade untuk alokasi pesanan), `POST /v1/sinkron/batch` (catch-up setelah offline, maksimal 200 rekaman per request berurutan FIFO).
3. Contoh body sortir: `{"uuid":"…","lot_id":"L-8812","grade_a_g":100000,"grade_b_g":14000,"grade_c_g":6000,"petugas":"OPR-SORTIR-1"}` — berat dalam gram integer; server menolak total ≠ berat kotor ±2% dengan kode 422.
4. Nomor urut server: surat jalan dan kode lot resmi diterbitkan server saat sinkron; saat offline desktop memakai nomor sementara `TMP-{uuid8}` yang dipetakan ke nomor resmi saat catch-up, dan cetakan ulang otomatis tersedia bila nomor berubah.
5. Keamanan gudang: token shift tidak boleh keluar dari PC gudang; endpoint `POST /v1/gudang/keluar` wajib dipanggil tiap tutup shift 14.00; tiga gagal PIN mengunci 15 menit dan memberi tahu Kepala Agregasi.

## Tautan ke File Terkait

- `produk/20-model-data.md` — entitas Lot, Sortir, Keranjang, Trip.
- `produk/50-autentikasi-perangkat.md` — kredensial perangkat gudang + PIN shift.
- `platform/30-desktop-windows-gudang.md` — aplikasi yang memanggil endpoint ini.
- `platform/60-offline-sinkron.md` — batch catch-up dan nomor sementara.
- `produk/30-kontrak-api-KMP-mobile.md`, `produk/32-kontrak-api-web-bun.md` — kontrak saudara.
