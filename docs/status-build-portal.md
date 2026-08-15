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
