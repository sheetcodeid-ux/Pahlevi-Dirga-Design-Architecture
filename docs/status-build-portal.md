# Status Build — Client Portal

Dibangun mengikuti dua PDF referensi. Dokumen ini memisahkan tiga hal: apa yang
**replika persis**, apa yang **saya karang** karena tidak terlihat di PDF, dan apa yang
**tidak bisa dibangun lewat API**.

---

## Struktur yang berdiri

```
Portal Hub                                    🟩
 ├── Resources                                ✏️
 ├── Provide a Review                         👍
 └── Portal Dashboard  (database · Gallery)
      └── Portal Template                     🟢
           ├── Introduction                   👥
           ├── Brief                          📄
           │    └── Programme + Budget Worksheet
           ├── Contract                       📝
           ├── Billing                        💳
           │    └── Drawdown Schedule
           ├── Directory                      📒
           ├── Meetings                       👥
           │    ├── Meeting Schedule
           │    ├── Meeting Agendas
           │    └── Meeting Minutes
           ├── Feedback                       💬
           └── Programme & Deliverables  (Table + Timeline)
```

**7 database · 11 halaman · 8 gambar tahap · 6 view.**

---

## Replika persis dari PDF

| Elemen | Catatan |
| --- | --- |
| Teks pre-loaded Introduction | Working with Us, 3 Key Phases, tiga fase, RIBA, enam callout Communication — disalin kata per kata |
| Delapan deskripsi Our Journey | Disalin kata per kata dari PDF 2 halaman 5 |
| Struktur kartu Our Journey | gambar angka → label italic → callout → toggle `Document Vault` cokelat → toggle `Key Milestones` cokelat → to-do `Complete` hijau |
| Teks Brief, Contract, Directory, Feedback | Disalin kata per kata |
| Opsi dropdown + warnanya | `Type` worksheet 5 opsi · `Status` drawdown 3 opsi · `Status` meeting · `Stage` |
| Kolom tabel | Space/Type/SQM/Est. Cost per SQM/Est. Cost excl. VAT/Notes · Status/Value/Due · Work Stage/Meeting/Date/Status/Participant/Link/Virtual/Physical |
| Formula `Est. Cost excl. VAT` | SQM × Est. Cost per SQM, dengan SUM di footer |
| Gambar angka 00–07 | Dibuat ulang: 00 oranye, 01–06 hitam bercahaya, 07 putih |
| Nama view | `All Notes` gallery + `Table` · `Timeline` |
| Toggle panduan Portal Hub | 01 Start Here … 05 Switch to Dark/Light Mode |

---

## Yang saya karang — periksa dan koreksi

Seluruh isi toggle tidak pernah terlihat di PDF karena semua screenshot menampilkannya
tertutup. Ini yang saya tulis:

| Lokasi | Isi karangan |
| --- | --- |
| Toggle tiap fase desain | 5 poin lingkup kerja per fase |
| Toggle RIBA Plan of Work | penjelasan + tautan ke situs RIBA |
| Enam jawaban FAQ | jawaban penuh, ditulis dari sudut pandang studio |
| Lima toggle Brief Questionnaire | 6–7 pertanyaan per toggle |
| Dua toggle Resources di Brief | daftar dokumen yang diminta |
| 16 toggle Document Vault & Key Milestones | daftar dokumen + milestone per tahap |
| Empat toggle Directory | tabel kontak dengan baris peran |
| Toggle Feedback Form | tujuh pertanyaan evaluasi |
| Toggle Payment Terms di Billing | lima ketentuan pembayaran |
| Isi Portal Hub, Resources, Provide a Review | panduan internal studio |

---

## Dua keputusan yang saya ambil sendiri

**Mata uang → Rupiah.** PDF memakai GBP karena studionya di Inggris. Nilai mata uang
adalah data, bukan elemen desain, dan portal yang menagih client Indonesia dalam pound
tidak terpakai. Satu perintah untuk mengubahnya kembali ke GBP.

**Agendas dan Minutes → dua database terpisah.** Dugaan awal saya satu database dengan
dua view terfilter. Setelah dicoba, hasilnya meninggalkan database sumber yang
menggantung di halaman dan filter harus dipasang dua kali. Dua database terpisah
tampil persis seperti di PDF dan lebih bersih.

---

## Tidak bisa lewat API — perlu Anda 10 menit

| Hal | Kenapa | Cara |
| --- | --- | --- |
| **Cover halaman** | Notion hanya menerima URL eksternal untuk cover, bukan file upload | 9 file PNG sudah saya kirim. Buka tiap halaman → Add cover → Upload |
| **Icon halaman** | Set icon bawaan Notion tidak tersedia di API; sementara pakai emoji terdekat | Klik icon → Icons → pilih icon garis |
| **Jam analog** | Widget pihak ketiga | Di Dashboard, ganti callout `Studio Clock` → `/embed` → tempel tautan widget jam Indify |
| **Database template** | Tidak ada endpoint-nya | Untuk portal baru: duplikat kartu `Portal Template` |
| **Automasi & tombol** | Tidak ada endpoint-nya, dan fitur paket berbayar | Menyusul setelah paket Notion dipastikan |

---

## Belum dikerjakan

- Halaman **Billing** baru terlihat potongan mobile di PDF — tata letak penuhnya belum
  pernah saya lihat
- Isi toggle asli dari template referensi, kalau ternyata ada di PDF berikutnya
- **PDF pertama dari client + prompt-nya** — belum diterima. Tanpa itu saya tidak bisa
  memisahkan mana replika dan mana tambahan yang diminta client
- Bahasa portal: sekarang **Inggris**, mengikuti referensi. Client studio berbahasa
  Indonesia — satu perintah untuk menerjemahkan seluruh portal

---

## Revisi — emoji, navigasi, cover

**Emoji dihapus seluruhnya.** Semua icon halaman dan icon callout sekarang memakai icon
garis bawaan Notion lewat format `/icons/<nama>_<warna>.svg`. Nama icon diverifikasi
satu per satu terhadap `notion.so/icons/` sebelum dipakai — API memang menolak nama yang
tidak ada, jadi tidak akan ada icon kosong.

| Halaman | Icon |
| --- | --- |
| Portal Hub | `square_green` |
| Portal Template | `circle_green` |
| Introduction · Meetings | `people_gray` |
| Brief | `document_gray` |
| Contract | `pencil_gray` |
| Billing | `credit-card_gray` |
| Directory | `book_gray` |
| Feedback | `chat_gray` |
| Resources | `snippet_gray` |
| Provide a Review | `thumbs-up_gray` |

Icon kartu Our Journey: `people` · `pencil` · `compass` · `ruler` · `document` ·
`wrench` · `key` · `home`. Callout deskripsi memakai `reference_gray`, icon ⓘ milik Notion.

**Navigasi dipindah keluar kolom.** Tujuh sub-halaman sekarang jadi blok halaman di level
halaman, di bawah heading `Navigation`, bukan di dalam kolom kanan. Ini juga yang membuat
ketujuhnya bersarang benar di sidebar Notion.

**Cover dipasang otomatis.** Notion hanya menerima URL eksternal untuk cover, bukan file
upload. Karena repo ini publik, kesembilan cover di-commit ke `assets/` lalu dipasang
lewat `raw.githubusercontent.com`. Delapan gambar angka tahap juga dipindah ke sana, jadi
tidak lagi bergantung pada URL S3 Notion yang kedaluwarsa. Tidak ada upload manual.

**Semua database dibuat inline** — tampil sebagai tabel di halaman, bukan tautan sub-halaman.

---

## Dua bug yang ditemukan saat verifikasi

**Urutan blok terbalik.** `replace_content` dengan banyak blok sekaligus menyimpan blok
dalam urutan terbalik — heading `Programme & Deliverables` naik ke atas, kartu 04–07
mendahului 00–03. Solusinya: `replace_content` seminimal mungkin, lalu `insert_content`
bertahap yang terbukti menjaga urutan.

**Database ikut terhapus.** `allow_deleting_content: true` pada `replace_content` ikut
membuang database `Programme & Deliverables`. Data sourcenya selamat dengan 9 baris utuh,
jadi dipasang ulang sebagai linked view ke sumber yang sama. Pelajaran: flag itu hanya
boleh dipakai kalau setiap database dan sub-halaman ikut disebut di konten baru.
