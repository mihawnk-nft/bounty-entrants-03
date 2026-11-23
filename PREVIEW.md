# PREVIEW — bounty-entrants-03 (TIDAK DI-SUBMIT)

Bounty: **bounty-entrants-03** — "Bring the most entrants to the bounties you make on make.fun"
Kategori: Growth · Reward: $1.000 (top 50) · Deadline: **2026-11-26 16:22 UTC (23:22 WIB 26 Nov)**
Entry fee kompetisi ini: gratis · Kuota: can_submit=true, day cap tersisa 6 · Akun: make.fun `mihawnk-50569`, GitHub `mihawnk-nft`
Dibangun: 2026-11-24 ~01:00 WIB (sesi dibuka setelah bounty buka 2026-11-23 16:22 UTC)

## Apa yang dibangun

Entry ini BUKAN repo kode biasa. Sesuai kit (`RULES.txt` + `competition.yaml` + `starter/AGENT.md`):
**entrinya adalah bounty sponsor buatan sendiri di make.fun** — repo hanya menyerahkan daftar bounty itu lewat `BOUNTY.json`, dan house menghitung entrant-nya dari database make.fun sendiri. Tempat ditentukan oleh jumlah entrant yang dihitung dari bounty-bounty yang dinamai, terbanyak pertama; seri → pot lebih tinggi, lalu receipt lebih awal. Setiap entrant dihitung, bayar atau tidak.

Yang sudah selesai di run ini:

- Kit diunduh ke `~/workspace/makefun/bounty-entrants-03-kit/` (13 file terverifikasi).
- Repo entry dibuat di `~/workspace/makefun/bounty-entrants-03-dev/`:
  - `main.ts` — Node 22, pure stdlib, menyalin `BOUNTY.json` ke `/output/BOUNTY.json` (satu-satunya tugas program). Satu perbaikan dari starter: komentar yang menyebut "entry fee minimal $0.50" diperbaiki — di bounty -03 ini bounty boleh **gratis** (starter menyalin teks -02 yang sudah kedaluwarsa).
  - `BOUNTY.json` — masih placeholder kit `{"bounties": ["https://make.fun/bounty/<slug>"]}` (lihat blocker di bawah).
  - `README.md` — ditulis ulang dengan 3 badge make.fun (badge kompetisi + rank + reward), status, dan cara kerja.
  - `AGENT.md`, `LICENSE` (MIT) — dari starter kit.
- Repo GitHub baru (public): **https://github.com/mihawnk-nft/bounty-entrants-03**
  - Commit `43ae2bd1c6073ba756e32cadd23fa3816b2c2dd9` sudah di-push ke `main`.
  - Dibuat 2026-11-23T18:01:06Z — setelah bounty buka (16:22Z) ✓.
  - About sudah diset: website `https://make.fun/bounty/bounty-entrants-03`, topik `makefun` ✓.
- `main.ts` dites lokal: `mkdir -p out && MAKEFUN_BOT_DIR=. MAKEFUN_OUTPUT_DIR=out node main.ts` → exit 0, `out/BOUNTY.json` identik byte-per-byte. Node di VM: v24.22.1 (≥ 22.18 ✓).
- Sponsor terms dibaca lewat `GET /api/sponsor/terms` (2026-11-23): hadiah minimum **$5** per bounty, maks **3 bounty terbuka sekaligus**, maks **3 proposal per hari UTC**, auto-list lead 5 menit, review ~5 menit, run maks 168 jam, entry fee minimum $0.10 (kalau memungut fee), fee house 15%, creator share 15–50%.

## Hasil kit check (terakhir: 2026-11-23 18:01 UTC)

Perintah: `node cli/makefun.mjs check --kit <kit> --repo <dev> --transcripts /tmp/transcripts-placeholder.tar.gz`

- **4 PASS**: `competition_open` (masih dalam window s.d. 26 Nov 16:22 UTC), `snapshot` (5 file, 23.616 byte — dalam batas), `license_osi` (MIT), `entrypoint` (main.ts → node22).
- **1 FAIL**: `transcripts_present` — hanya karena file transcripts yang dipakai cek ini adalah placeholder kosong (tanpa `manifest.json`). Bundle transcripts ASLI belum dibuat: harus dibuat oleh top-level agent setelah semua subagent selesai, dengan `--muse-usage` (usage rows subagent baru ditulis setelah run selesai) + `--provider meta --model muse-spark-1.3 --effort default --mcp none` + prompt-file dari task cron (origin: scheduled). `bundle --dry-run` sudah dites: menemukan 3 sesi Muse app (parent + subagent ini + 1 sesi lain).
- **3 SKIP**: `prerequisites` (butuh dompet Solana berisi USDC — lihat blocker), `strategy_note`, `committed_secret`.
- **5 "at submission"** (baru bisa diverifikasi situs saat submit; semua sudah dipenuhi dari sisi kita): `repo_public` ✓ (public), `repo_owner` (owner `mihawnk-nft` — sama dengan login GitHub akun; kalau situs menolak, tambahkan `.makefun/owner.json` berisi wallet entry), `repo_created_after_open` ✓, `commit_in_repo` ✓ (commit sudah di-push), `duplicate_snapshot` (file sudah beda dari starter: README + komentar main.ts diubah).

**Kesimpulan check: repo siap secara teknis; yang belum ada adalah isi entrinya (bounty sponsor) + bundle transcripts asli.**

## ⛔ BLOCKER — entry ini TIDAK BISA di-submit dulu

`BOUNTY.json` masih placeholder, dan gate akan menolak entry tanpa bounty sponsor yang nyata. Yang dibutuhkan sebelum submit:

1. **Satu atau beberapa bounty sponsor dari akun `mihawnk-50569`** lewat sponsor flow (form https://make.fun/sponsor/new atau API `POST /api/sponsor/proposals`), masing-masing **buka di dalam window** bounty-entrants-03 (23 Nov 16:22 UTC – 26 Nov 16:22 UTC) dan **listed + public** saat submit.
2. **Dana + tanda tangan user**: tiap bounty butuh deposit hadiah **minimal $5 USDC** dari dompet Solana yang terhubung ke akun make.fun (+ sedikit SOL untuk fee). Deposit ditandatangani user — agent tidak boleh dan tidak bisa menandatanganinya. Tanpa USDC di dompet Solana, tidak ada bounty yang bisa dibuat.
3. Setelah bounty listed, isi slug-nya ke `BOUNTY.json`, commit, push, buat bundle transcripts asli, lalu submit.

**Catatan keuangan:** user tercatat hampir tidak punya dana cair (~$4,39). Hadiah minimum $5 per bounty berarti sponsor 1 bounty saja sudah butuh dana yang belum tentu tersedia. Keputusan sponsor (berapa bounty, hadiah berapa) adalah keputusan user — ini uang sungguhan, bukan entri gratis.

## Usulan bounty sponsor (kalau user memutuskan lanjut)

Prinsip: gratis dimasuki (entry fee $0 — semua entrant dihitung, dan gratis paling mudah menarik orang), tugas gampang + cepat selesai, hadiah kecil tapi nyata. Ambil opsi `auto_list` dari `POST /api/sponsor/suggestions` supaya listing seketika setelah deposit (lead 5 menit), bukan custom brief (nunggu setup scoring make.fun).

1. **"Funniest one-line AI agent mishap"** — teks 1 baris, format yang sudah terbukti ramai di make.fun; hadiah $5–$10, gratis dimasuki.
2. **"Best 15-second TikTok ad for a made-up product"** — video pendek, setup self (lead teks 35 / gambar 65 menit); hadiah $10, gratis dimasuki.
3. **"Smallest working Python game"** — kode stdlib, gampang dinilai; hadiah $5, gratis dimasuki.

Maks 3 proposal/hari dan maks 3 terbuka sekaligus — jadi paling banyak 3 bounty di window ini (sisa waktu ~3 hari). Tiap bounty yang ditambah = submit ulang seluruh daftar BOUNTY.json; submit terakhir sebelum deadline yang dihitung.

## Perintah submit YANG AKAN dipakai nanti (JANGAN dijalankan dari run ini)

Setelah blocker di atas selesai (bounty sponsor listed + BOUNTY.json terisi + bundle transcripts asli dibuat top-level agent):

```sh
cd ~/workspace/makefun/bounty-entrants-03-kit/bounty-entrants-03-kit
node cli/makefun.mjs submit --competition bounty-entrants-03 \
  --repo-url https://github.com/mihawnk-nft/bounty-entrants-03 \
  --commit <sha-baru-setelah-BOUNTY.json-terisi> \
  --title "<judul entry>" \
  --bundle transcripts.tar.gz \
  --keypair ~/.makefun/keypairs/https_make.fun.json
```

Submit HANYA atas lampu hijau eksplisit user di chat, setelah preview ini dia baca. Keypair di atas hanya dipakai saat submit nanti, bukan di run ini.

## Ringkasan status

| Item | Status |
|---|---|
| Kit dibaca & dipahami | ✅ |
| Repo entry (main.ts + README + LICENSE) | ✅ dibuat & di-push |
| main.ts dites lokal | ✅ lolos (exit 0, output identik) |
| Kit check | ⚠️ 4 pass / 1 fail (transcripts placeholder) / 3 skip / 5 at-submission |
| Bounty sponsor (isi entry yang sebenarnya) | ⛔ BELUM ADA — butuh USDC + tanda tangan user |
| Submit | ⛔ TIDAK dilakukan (menunggu user) |
