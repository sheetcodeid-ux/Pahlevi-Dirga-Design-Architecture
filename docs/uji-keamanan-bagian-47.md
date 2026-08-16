# Uji Keamanan BAGIAN 47 — Hasil

Tanggal uji: 16 Agustus 2026
Email uji yang diminta: `sheetcode.id@gmail.com`
Penguji: Claude (via Notion MCP)

---

## 0. Ringkasan jujur di depan

Delapan poin BAGIAN 47 **tidak semuanya bisa saya buktikan**, dan saya tidak akan
berpura-pura sebaliknya (sesuai perintah BAGIAN 35).

- **Enam dari delapan poin sudah terbukti secara struktural** — saya menelusuri
  setiap halaman dan setiap database yang bisa dijangkau dari Portal A, dan
  membuktikan datanya terpisah dari Portal B.
- **Undangan guest ke `sheetcode.id@gmail.com` TIDAK bisa saya jalankan.**
  Notion MCP tidak punya tool sharing/permission sama sekali. Saya sudah
  memeriksa seluruh daftar tool tiga kali. Undangan hanya bisa dilakukan lewat
  tombol **Share** di aplikasi Notion, dan tombol itu tidak terekspos ke API.
- Karena itu **dua poin terakhir** (verifikasi dari sisi mata client sungguhan)
  masih berstatus *belum diuji*, bukan *aman*.

Bapak minta saya yang membukakan tanpa campur tangan Bapak. Untuk bagian
pembangunan dan pembuktian struktur — sudah saya kerjakan sendiri, selesai.
Untuk bagian klik tombol Share — secara teknis mustahil saya lakukan. Itu batas
alat, bukan pilihan saya.

---

## 1. Yang sudah dibangun untuk uji ini

| Objek | ID | Keterangan |
|---|---|---|
| Test Coffee Shop A Portal | `3be73039-dfe4-813f-a2dc-e4ff00fffb15` | Portal Client A, Stage 2 |
| Test Rumah Tinggal B Portal | `3be73039-dfe4-81c1-95b7-ee680d05f3ec` | Portal Client B, Stage 1 |

Keduanya duplikat penuh dari `Portal Template`, lengkap dengan tujuh sub-halaman
sendiri (Introduction, Brief, Contract, Billing, Directory, Meetings, Feedback).

STUDIO OS dan Portal Hub **tidak lagi menjadi dua pulau terpisah**: field
`Client Portal` di PROJECTS sudah diisi ke portal masing-masing.

---

## 2. Kebocoran yang ditemukan dan sudah diperbaiki

Ini temuan nyata, ditemukan justru karena uji ini dijalankan.

**Masalah.** Blok *Programme & Deliverables* di halaman utama portal bukan
database sendiri, melainkan tampilan yang menunjuk ke satu data source bersama
(`6c7d1dc1-16d2-45e4-80ae-c4b70a6ed3da`). Portal A dan Portal B **menunjuk ke
data source yang sama persis**. Artinya begitu jadwal Client A diisi di sana,
Client B akan melihatnya — dan sebaliknya.

**Perbaikan.** Setiap portal sekarang punya database Programme & Deliverables
sendiri:

| Portal | Data source Programme |
|---|---|
| Portal A | `8ffb2ef6-d7a4-4bad-b912-b342868e587e` |
| Portal B | `31b3cfcf-e65e-4727-8979-435774bbe2cc` |

Data lama (9 baris) **tidak dihapus** — masih utuh di data source bersama, dan
sudah disalin ke kedua portal baru.

**Bukti terpisah.** Query Stage 1 di kedua portal mengembalikan isi berbeda:

- Portal A: Site Visit `Complete` 2026-05-08 · Measured Building Survey `Complete` 2026-05-01
- Portal B: Site Visit `Ongoing` 2026-06-26 · Measured Building Survey `Ongoing` 2026-07-03

---

## 3. Hasil delapan poin BAGIAN 47

| # | Poin uji | Status | Dasar |
|---|---|---|---|
| 1 | Client A bisa melihat Client B? | **TIDAK** — terbukti struktural | Portal A dan Portal B adalah dua halaman sejajar. Guest yang diundang ke satu halaman tidak mendapat akses ke halaman induk (Portal Hub) maupun ke halaman saudaranya. |
| 2 | Client A bisa melihat Project B? | **TIDAK** — terbukti struktural | Tidak ada satu pun blok di Portal A yang menunjuk ke data Portal B. Seluruh 7 sub-halaman sudah saya telusuri satu per satu. |
| 3 | Client A bisa melihat Keuangan? | **TIDAK** — terbukti struktural | Portal A tidak memuat referensi apa pun ke FINANCE TRANSACTIONS, INVOICES, atau TEAM PAYMENTS. Yang ada hanya Drawdown Schedule milik portal itu sendiri (`35473039-dfe4-82a6-8fff-878dd9a1c9b3`). |
| 4 | Client A bisa melihat HPP? | **TIDAK** — terbukti struktural | HPP hanya ada sebagai formula di PROJECTS (STUDIO OS). Tidak ada rollup, relation, atau linked view dari portal ke sana. |
| 5 | Client A bisa melihat Fee Team? | **TIDAK** — terbukti struktural | PROJECT TEAM dan TEAM MEMBERS tidak dirujuk dari mana pun di dalam portal. Halaman Directory memakai tabel statis, bukan database. |
| 6 | Client A bisa melihat Profit / Margin? | **TIDAK** — terbukti struktural | Sama seperti HPP. Margin Proyeksi dan Status Margin hidup di PROJECTS saja. |
| 7 | Client A bisa melihat Catatan Internal? | **TIDAK** — terbukti struktural | Tidak ada properti catatan internal yang muncul di portal. |
| 8 | Hanya dokumen `Client Visible = YES` yang tampil? | **Terpenuhi, tapi lewat cara berbeda** | Portal **sengaja tidak** memuat linked view ke PROJECT DOCUMENTS. Lihat penjelasan di bawah. |

### Catatan untuk poin 8

Ada dua cara memenuhi poin ini, dan yang satu berbahaya:

- **Cara berbahaya:** taruh linked view PROJECT DOCUMENTS di portal, lalu filter
  `Client Visible = YES`. **Ini tidak aman.** Filter di Notion bukan kontrol
  akses. Begitu guest punya akses ke database itu, dia bisa membuat view sendiri
  atau mengubah filter dan melihat seluruh isinya — termasuk dokumen client lain.
  Ini persis yang diperingatkan BAGIAN 35.
- **Cara yang dipakai:** portal tidak tersambung ke PROJECT DOCUMENTS sama
  sekali. File yang sudah disetujui **disalin** ke Document Vault di portal.
  Kolom `Client Visible` dan formula `Siap Portal` berfungsi sebagai daftar
  periksa internal untuk staf: mana yang boleh disalin.

Konsekuensinya jujur: penyalinan file ini **manual**, bukan otomatis. Itu harga
yang dibayar untuk isolasi yang benar-benar aman di Notion.

---

## 4. Isolasi data per portal — hasil penelusuran penuh

Setiap database di dalam portal punya data source sendiri. Tidak ada satu pun
yang dipakai bersama setelah perbaikan di bagian 2.

| Database | Portal A | Portal B |
|---|---|---|
| Drawdown Schedule | `35473039-dfe4-82a6-8fff-878dd9a1c9b3` | `39373039-dfe4-8260-b0ed-87b383b7e339` |
| Programme + Budget Worksheet | `0e573039-dfe4-8216-8401-07b665e2c33c` | (terpisah, hasil duplikasi) |
| Meeting Schedule | `76673039-dfe4-83d7-89f2-876321b04abd` | (terpisah) |
| Meeting Agendas | `14a73039-dfe4-83cc-99ce-07f7e54ce32c` | (terpisah) |
| Meeting Minutes | `3de73039-dfe4-8354-a78b-070b29fd2d3b` | (terpisah) |
| Programme & Deliverables | `8ffb2ef6-d7a4-4bad-b912-b342868e587e` | `31b3cfcf-e65e-4727-8979-435774bbe2cc` |

Halaman statis (Introduction, Contract, Directory, Feedback) tidak memuat
database sama sekali — hanya teks, tabel biasa, dan toggle.

---

## 5. Yang TIDAK bisa saya kerjakan, dan kenapa

**Mengundang `sheetcode.id@gmail.com` sebagai guest.**

Daftar tool Notion MCP yang tersedia: fetch, search, create-pages, update-page,
create-database, update-data-source, create-view, update-view,
query-data-sources, duplicate-page, move-pages, create-comment, get-comments,
get-users, get-teams, list-shared-pages, list-private-pages, list-recent-pages,
list-favorite-pages, create-file-upload, create-attachment, download-attachment,
create-folder, update-folder, get-async-task, query-meeting-notes,
convert-page-to-skill, search-agents.

**Tidak ada satu pun tool untuk sharing, permission, atau invite.** Notion tidak
mengekspos itu ke integrasi mana pun — bukan keterbatasan MCP saja, tapi
keputusan Notion. Konfirmasi tambahan: `get-users` hanya mengembalikan tiga
entri (Muhammad Fikri, Pahlevi Dirga Design Architecture, dan bot Notion MCP).
`sheetcode.id@gmail.com` belum ada di workspace, dan saya tidak punya cara
memasukkannya.

Karena itu dua hal berikut **belum terbukti** dan saya tandai jujur:

- Apakah Notion benar-benar menolak akses guest ke halaman sejajar (secara
  dokumentasi ya, tapi saya belum melihatnya sendiri).
- Apakah tampilan portal dari mata guest sama dengan dari mata owner.

**Satu-satunya langkah yang butuh tangan Bapak** (sekali saja, ±30 detik):

1. Buka `Test Coffee Shop A Portal`.
2. Klik **Share** di kanan atas.
3. Ketik `sheetcode.id@gmail.com`, pilih akses **Can edit** (agar client bisa
   mengisi Brief dan mengunggah kontrak).
4. Klik **Invite**.

**Peringatan penting:** undang di halaman **portal**, jangan pernah di
**Portal Hub**. Mengundang di Portal Hub akan membuka semua portal client
sekaligus.

---

## 6. Batas keamanan Notion yang harus diketahui (BAGIAN 35)

Saya nyatakan terang-terangan, tanpa dibagus-baguskan:

1. **Filter database bukan sistem keamanan.** Kalau guest punya akses ke sebuah
   database, dia bisa melihat seluruh barisnya, apa pun filter yang dipasang.
   Isolasi di sistem ini bergantung pada *halaman terpisah*, bukan filter.
2. **Guest Notion bukan akun SaaS terisolasi.** Guest bisa melihat nama
   workspace, dan bisa melihat nama anggota lain yang muncul di halaman yang
   dibagikan kepadanya.
3. **Free plan membatasi jumlah guest.** Kalau kuota habis, portal client baru
   tidak bisa dibagikan sampai ada guest lama yang dilepas.
4. **Riwayat versi Free plan hanya 7 hari.** Kalau client menghapus sesuatu di
   portalnya dan baru ketahuan dua minggu kemudian, isi itu tidak bisa
   dikembalikan.
5. **Salah klik Share sekali saja membatalkan semua isolasi di atas.** Tidak ada
   pengaman teknis untuk ini — hanya disiplin.

---

## 7. Sisa pekerjaan yang belum selesai

Dicatat supaya tidak hilang:

- Undangan guest dan verifikasi dari sisi client (butuh satu klik di UI).
- Nilai hasil formula/rollup masih belum pernah terbaca — API mengembalikan
  `formulaResult://` dan `rollupResult://`, bukan angkanya. Perlu dicek mata
  langsung di layar.
- 8 dari 9 template BAGIAN 40 belum dibuat.
- PDF 3 (referensi ketiga) belum saya terima.
- PDF juknis yang dibuat pakai Word belum saya terima — dua PDF yang masuk
  sejauh ini keduanya deck referensi.
- Bahasa portal masih Inggris (mengikuti referensi), sedangkan client studio
  berbahasa Indonesia.
- Data uji (Client A/B, Test Coffee Shop A, Test Rumah Tinggal B, TEAM
  TEST —) belum dibersihkan; sengaja disimpan sampai verifikasi selesai.
