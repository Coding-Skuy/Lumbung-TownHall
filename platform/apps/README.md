> Versi: v1.0.0 | Status: disetujui | Menggantikan: -

# Platform ~ Aplikasi (Lumbung)

Folder ini adalah **indeks aplikasi** divisi Lumbung: tujuh repo kode yang hidup di
organisasi Coding-Skuy ([tim Lumbung](https://github.com/orgs/Coding-Skuy/teams/lumbung/repositories)),
ditautkan ke repo ini sebagai **git submodule**.

- `platform/versions/` — dokumen formal beku (BRD/PRD/FRD/FSD/SRS).
- `platform/apps/` — kode aplikasi (submodule, repo terpisah).

## Repo aplikasi

| Submodule | Repo | Peran | Stack |
|---|---|---|---|
| `app-kmp/` | [lumbung-app-kmp](https://github.com/Coding-Skuy/lumbung-app-kmp) | KMP+CMP: gudang desktop (USB/serial + thermal) dan lapangan mobile | Kotlin MPP / CMP |
| `web/` | [lumbung-web](https://github.com/Coding-Skuy/lumbung-web) | Web ops: rute & papan harga | Bun + SvelteKit + TS |
| `backend-service/` | [lumbung-backend-service](https://github.com/Coding-Skuy/lumbung-backend-service) | Layanan API & logika bisnis fee/kg | Rust |
| `ai-models/` | [lumbung-ai-models](https://github.com/Coding-Skuy/lumbung-ai-models) | Prediksi susut & harga hortikultura | Python (training) + Rust (serving) |
| `data-pipeline/` | [lumbung-data-pipeline](https://github.com/Coding-Skuy/lumbung-data-pipeline) | Ingest timbangan, trip, pasar induk ke DB lumbung | — |
| `design/` | [lumbung-design](https://github.com/Coding-Skuy/lumbung-design) | Token, flow gudang, struk fee | Figma |
| `infra-devops/` | [lumbung-infra-devops](https://github.com/Coding-Skuy/lumbung-infra-devops) | CI KMP MSIX/APK, Rust, web, runner gudang | CI/CD |

## Cara pakai

```bash
# clone beserta submodule
git clone --recurse-submodules https://github.com/Coding-Skuy/Lumbung-TownHall.git
# bila repo sudah ter-clone tanpa submodule:
git submodule update --init --recursive
# perbarui ke commit main terbaru tiap repo app:
git submodule update --remote
```

## Batasan

Indeks ini hanya menautkan repo. Kode dan riwayatnya tetap milik repo app masing-masing;
keputusan versi di tulis di `platform/versions/vX.Y.Z/`, bukan di sini.