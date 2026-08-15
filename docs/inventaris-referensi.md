# Inventaris Referensi Client Portal

Dokumen kerja. Diisi bertahap seiring PDF referensi masuk. Tujuannya satu: mencatat
setiap elemen di PDF supaya bisa dicocokkan sebelum dibangun, bukan sesudah.

Status: **PDF 1 dari sekian — belum lengkap.**

---

## Arsitektur yang terbaca

Referensi ini **berpusat pada portal**, bukan pada database.

```
PORTAL HUB                      ← halaman induk internal studio
 └── Our Client Portals         ← database, tampil sebagai Gallery
      ├── Bethania Chapel Portal
      ├── Hill House Portal
      ├── Chestnut House Portal
      ├── Nottage House Portal
      ├── Bryngarw House Portal
      └── Maesteg Children's Library Portal
           └── tiap baris = satu halaman portal berisi 7 sub-halaman:
                1. Dashboard   (halaman portal itu sendiri)
                2. Introduction
                3. Brief
                4. Contract
                5. Billing
                6. Directory
                7. Meetings
                +  Feedback    (muncul di sidebar, di luar penomoran 1-7)
```

Satu project = satu baris di database portal = satu halaman lengkap dengan sub-halaman
dan database inline-nya sendiri.

---

## 1. PORTAL HUB

Halaman induk. Cover terang krem dengan wordmark `PORTAL HUB` rata kanan. Icon kotak
hijau outline.

- Sidebar: `Resources`, `Provide a Review`
- Heading `Our Client Portals` — merah/koral
- Callout: "This is the Portal Dashboard where we create, store and track all client
  portals for each individual project. Check out the resources and video tutorial to
  familiarise yourself with this system."
- Toggle list panduan:
  - `01 - Start Here`
  - `02 - Creating a New Portal`
  - `03 - [Must Read]`
  - `04 - How to Share with Clients`
  - `05 - Switch to Dark/Light Mode`

### Database: Our Client Portals — view Gallery

Kartu menampilkan cover foto project + properti berikut di muka kartu:

| Properti | Tipe | Catatan |
| --- | --- | --- |
| Nama Portal | Title | pola `<Nama Project> Portal` |
| Client Invited | Checkbox | tampil di kartu |
| Contract Signed | Checkbox | tampil di kartu |
| Stage | Select | `Stage 2` biru · `Stage 4` hijau · `Stage 5` ungu |
| Cover | Page cover | foto render/interior project |

---

## 2. DASHBOARD — halaman portal per client

Cover terang krem, wordmark `DASHBOARD` rata kanan. Icon lingkaran hijau outline.
Judul contoh: `Client Portal v2`.

Properti halaman yang terlihat di bawah judul:
`Client Invited` ☑ · `Contract Signed` ☑ · `Scope stage` ☑ · `Status` → `Not started`

Susunan blok:

1. **Jam analog** — widget jam berjalan, menampilkan hari (`19:53 Tuesday`)
2. **Callout `Welcome to your Client Portal`** — "Our central location where we will
   share, collaborate and store documents for the lifetime of your project."
3. **Blok Studio** — `Mon - Fri · 08:00 - 16:00 (GMT)` · `Address Line 1, City, Postcode`
4. **Blok Contact** — nama · email · nomor telepon
5. **Navigation** — 7 tautan: Introduction · Brief · Contract · Billing · Directory ·
   Meetings · Feedback
6. **Our Journey** — 8 kartu besar bernomor
7. **Programme & Deliverables** — database, view Table + Timeline

### Our Journey — 8 kartu tahap RIBA

Angka besar sebagai judul kartu. Kartu tahap berjalan disorot oranye; tahap akhir putih.

| No | Judul | Isi kartu |
| --- | --- | --- |
| `00` | Design Workshop | teks + `Document Vault` + `Key Milestones` + checkbox `Complete` |
| `01` | Brief & Preparation | idem |
| `02` | Concept Design | idem |
| `03` | Developed Design | idem |
| `04` | Technical Design | idem |
| `05` | Construction | idem |
| `06` | Handover | idem |
| `07` | Happy Buildings | idem |

Tiap kartu memuat dua tautan berulang — `Document Vault` dan `Key Milestones` —
menunjuk ke database yang difilter untuk tahap itu.

### Programme & Deliverables

View: `Table`, `Timeline`. Dikelompokkan per Work Stage.

| Kolom | Tipe | Opsi terbaca |
| --- | --- | --- |
| Name | Title | mis. `Appointment Signed`, `Brief Questionnaire`, `Initial Design Workshop`, `Site Visit`, `Other Relevant Surveys`, `Measured Building Survey`, `Design Workshop 01/02`, `Feasibility Study` |
| Status | Select | `Complete` hijau · `Not Started` abu · `Ongoing` kuning |
| Target Completion | Date | |
| Person | Person | |

Grup terbaca: `Stage 0`, `Stage 1`, `Stage 2`

---

## 3. INTRODUCTION

Wordmark `INTRO-`. Icon tiga orang.

- Callout `Working with Us` — "This page introduces our process which is designed to be
  enjoyable, interactive, and inclusive. It encompasses sketches, drawings, digital and
  physical models — developing from experimental to polished — to transform your home or
  building with as much joy and excitement that we can bring."
- Heading `Design Process` (merah)
- Callout `3 Key Phases:` — "Detailed below are the phases we will embark on together to
  shape the design and delivery of your project:"
- Tiga callout berwarna, masing-masing berisi toggle `Click to see what's involved`:

| Fase | Warna callout | Icon |
| --- | --- | --- |
| `Planning` | ungu/maroon lembut | palet warna |
| `Technical Design` | hijau sage | pensil/garis |
| `Construction` | cokelat/khaki | kunci inggris |

- Callout `RIBA Plan of Work` — toggle "Click to find a copy of the RIBA Plan of Work
  upon which these stages are designed."
- Heading `Communication` — dua kolom:

**Kolom kiri** — tiga callout:
| Judul | Isi |
| --- | --- |
| `Working Hours` | "Our studio is open between 08.00AM - 16:00PM GMT, Monday to Friday excluding bank holidays. As a small practice, any holiday leave is planned in advance and arranged to provide little to no impact to our timeline." |
| `Response Time` | "As an architect's role requires site visits, meetings and focused design sessions, we are often pre-occupied for un-scheduled contact. We aim to respond within one working day and appreciate your patience." |
| `Scheduled Calls / Meetings` | "This is your project and we believe in instilling a collaborative culture. We do this by scheduling physical meetings and virtual calls at strategic points during each stage, as set out here → Meetings." |

**Kolom kanan** — tiga callout judul merah:
| Judul | Isi |
| --- | --- |
| `Studio Hours` | Monday - Friday 08:00-16:00 GMT |
| `Contact` | Email · Mobile |
| `Meetings` | Virtual – Microsoft Teams · Physical – Link Google Map to Practice Address |

- Heading `Frequently Asked Questions` — daftar toggle:
  - When will the work stages be completed?
  - Can I request additional services?
  - Is it possible to pause at the end of each work stage?
  - What is your availability on a daily basis?
  - How long will my planning application take?
  - Do you have a refund policy?

---

## 4. BILLING

Wordmark `BILLING`. Heading `Drawdown Schedule` (merah).

### Database: Drawdown Schedule — view Table

| Kolom | Tipe | Opsi |
| --- | --- | --- |
| Status | Select | `Paid` hijau · `Awaiting` merah muda · `Not Issued` abu |
| Value | Number, format GBP | |
| Due | Date | |

Baris footer: `SUM £16,650.00` pada kolom Value.

Nilai contoh terbaca: £1,000 · £1,500 · £900 · £1,350 · £1,900 · £1,900 · £1,900 ·
£1,550 · £1,550 · £1,550 · £1,550

Blok tambahan di halaman: `Payment Method` — via Bank Transfer, Bank Name, Account Name,
Account Number, Sort Code.

**Catatan penting:** skema penagihan referensi adalah **drawdown bertahap** mengikuti work
stage, bukan DP/pelunasan dua termin.

---

## 5. MEETINGS

Wordmark `MEETINGS`. Icon tiga orang.

- Callout `Our Meetings` — "On this page we can schedule, track and view our meetings and
  notes throughout your project work stages."

### Database: Meeting Schedule — view Table

| Kolom | Tipe | Opsi terbaca |
| --- | --- | --- |
| Work Stage | Select | `Stage 0` oranye · `Stage 1` merah muda |
| Meeting | Title | |
| Date | Date + time | format `19/02/2024 12:00` |
| Status | Select | `Done` hijau · `Scheduled` abu |
| Participant | Person | |
| Link | URL | mis. `meet.google.com/...`, atau teks `Studio` |
| Virtual | Checkbox | |
| Physical | Checkbox | |

### Database: Meeting Agendas — view `All Notes` (gallery) + `Table`

Kartu: `Stage 1 Design Review Agenda` · tag `Meeting Agenda` **biru**

### Database: Meeting Minutes — view `All Notes` (gallery) + `Table`

Kartu: `Stage 1 Design Review Minutes` · tag `Meeting Minutes` **hijau**

> Dugaan yang perlu dikonfirmasi dari PDF berikutnya: Agendas dan Minutes kemungkinan
> **satu database Notes** dengan properti tipe (`Meeting Agenda` / `Meeting Minutes`),
> ditampilkan sebagai dua linked view terfilter. Nama view yang sama-sama `All Notes` di
> kedua blok adalah petunjuk kuat ke arah itu.

---

## Bahasa visual

| Unsur | Nilai |
| --- | --- |
| Mode | Gelap. Ada tombol `Switch to Dark/Light Mode` di Portal Hub |
| Cover halaman | Krem terang, wordmark hitam rata kanan, huruf besar rapat |
| Heading section | Merah koral, garis horizontal tipis di bawahnya |
| Callout | Abu gelap; berwarna hanya untuk tiga fase desain |
| Aksen fase | ungu/maroon · hijau sage · cokelat khaki |
| Aksen deck | Oranye terang — nomor tahap berjalan, penomoran section |
| Icon | Icon garis Notion, bukan emoji |

---

## Belum terlihat — perlu PDF berikutnya

- Halaman **Brief** — terlihat memuat `Brief Questionnaire`, `Programme + Budget
  Worksheet`, `Resources`, `The Project Brief`, dan tabel ruang (Living, Kitchen,
  Bedroom 01, Bathroom 01 …) dengan kolom berwarna
- Halaman **Contract** — `Our Contract`, `Client Contact Details`, `Contract Design`
- Halaman **Directory** — tabel konsultan/kontraktor
- Halaman **Feedback**
- Halaman **Resources** dan **Provide a Review** di Portal Hub
- Database **Document Vault** dan **Key Milestones** — dirujuk dari tiap kartu Our Journey
- Isi toggle tiap fase desain
- Automasi dan tombol, kalau ada
