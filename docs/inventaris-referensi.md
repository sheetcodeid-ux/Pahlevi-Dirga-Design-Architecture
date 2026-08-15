# Inventaris Referensi Client Portal

Dokumen kerja. Diisi bertahap seiring PDF referensi masuk. Tujuannya satu: mencatat
setiap elemen di PDF supaya bisa dicocokkan sebelum dibangun, bukan sesudah.

**Sumber:** PDF 1 (7 halaman) · PDF 2 (9 halaman, 2 di antaranya duplikat PDF 1)
**Status:** struktur 7 halaman portal sudah lengkap. Isi toggle belum terlihat.

---

## Arsitektur

Referensi ini **berpusat pada portal**, bukan pada database.

```
Portal Hub                          ← halaman induk internal studio
 └── Portal Dashboard               ← nama database (dari breadcrumb)
      │   heading di halaman: "Our Client Portals", view Gallery
      ├── Bethania Chapel Portal
      ├── Hill House Portal
      ├── Chestnut House Portal (example)
      ├── Nottage House Portal
      ├── Bryngarw House Portal
      └── Maesteg Children's Library Portal
           └── tiap baris = satu halaman portal berisi 7 sub-halaman:
                Introduction · Brief · Contract · Billing ·
                Directory · Meetings · Feedback
```

Breadcrumb yang terbaca: `Portal Hub / Portal Dashboard / Chestnut House Portal (example)`

Satu project = satu kartu di gallery = satu halaman dashboard dengan tujuh sub-halaman
dan database inline-nya sendiri.

Penomoran section di deck: 1 dashboard · 2 intro · 3 your brief · 4 contract ·
5 track billing · 6 directory · 7 manage meetings · + collect feedback · + portal hub

---

## A. PORTAL HUB

Cover terang krem, wordmark `PORTAL HUB` hitam rata kanan. Icon kotak hijau outline.

- Sidebar: `Resources`, `Provide a Review`
- Heading `Our Client Portals` — merah koral, garis tipis di bawah
- Callout: "This is the Portal Dashboard where we create, store and track all client
  portals for each individual project. Check out the resources and video tutorial to
  familiarise yourself with this system."
- Toggle panduan:
  - `01 - Start Here`
  - `02 - Creating a New Portal`
  - `03 - [Must Read]`
  - `04 - How to Share with Clients`
  - `05 - Switch to Dark/Light Mode`

### Database `Portal Dashboard` — view Gallery

| Properti | Tipe | Catatan |
| --- | --- | --- |
| Nama Portal | Title | pola `<Nama Project> Portal` |
| Client Invited | Checkbox | tampil di muka kartu |
| Contract Signed | Checkbox | tampil di muka kartu |
| Stage | Select | `Stage 2` biru · `Stage 4` hijau · `Stage 5` ungu |
| — | Page cover | foto render/interior, tampil sebagai gambar kartu |

---

## B. DASHBOARD — halaman portal per client

Cover krem, wordmark `DASHBOARD`. Icon lingkaran hijau outline. Judul contoh
`Client Portal v2` / `Chestnut House Portal`.

Properti halaman di bawah judul: `Client Invited` ☑ · `Contract Signed` ☑ ·
`Scope stage` ☑ · `Status` → `Not started`

### Susunan blok

Baris atas — tiga kolom:

| Kolom kiri | Kolom tengah | Kolom kanan |
| --- | --- | --- |
| Jam analog berjalan (`15:33 Monday`) | 3 callout bertumpuk | Heading `Navigation` + 7 tautan |

Callout kolom tengah:
1. `Welcome to your Client Portal!` — "Our central location where we will share,
   collaborate and store documents for the lifetime of your project."
2. `Studio` (icon gedung) — `Mon - Fri · 08.00 - 16.00 (GMT)` / `Address Line 1, City, Postcode`
3. `Contact` (icon orang) — `Ross Hartland` / `yourname@yourpractice.com` / `+441234567890`

Navigation — tiap baris punya icon sendiri:
`Introduction` · `Brief` · `Contract` · `Billing` · `Directory` · `Meetings` · `Feedback`

### Our Journey — 8 kartu, grid 4 kolom × 2 baris

Struktur tiap kartu, dari atas ke bawah:

1. **Blok angka** — gambar, angka besar bercahaya. Tahap berjalan **oranye terang**,
   tahap lain hitam, tahap `07` **putih/krem**
2. **Baris label** — icon + label italic
3. **Callout** — icon info + teks italic
4. **Toggle `Document Vault`** — latar cokelat/rust
5. **Toggle `Key Milestones`** — latar cokelat/rust
6. **To-do `Complete`** — latar hijau

| No | Icon | Label | Teks callout |
| --- | --- | --- | --- |
| `00` | orang | Design Workshop | We've met on site for a design workshop to understand your aims and aspirations. Please see below for the fee proposal and appointment contract we've agreed together. |
| `01` | pensil | Brief & Preparation | Through briefing workshops we work together to refine your project brief. We advise and procure relevant surveys to capture accurate information that sets us off on the right foot. |
| `02` | palet | Concept Design | Working from your brief and survey information, we prepare multiple creative options for your building and establish planning, building regulations and sustainability opportunities/constraints. |
| `03` | pensil garis | Developed Design | Taking forward your chosen design option, this stage is about preparing a co-ordinated design for your planning and/or Listed Building Consent submission and monitoring through to a decision. |
| `04` | dokumen edit | Technical Design | This stage is intensive and involves preparing technical drawings to comply with building regulations, collaborating with our consultants and producing a tender package for construction. |
| `05` | kunci inggris | Construction | We can supervise the site progress, quality and compliance with our design documents during the construction phase, acting as your Contract Administrator. |
| `06` | serah terima | Handover | Construction is complete, but we remain on hand for a year after completion to resolve any contractor defects that may arise. |
| `07` | gedung | Happy Buildings | It's time to enjoy the architecture we've created together. We like to meet for a coffee to reflect on your experience of the completed building and our process. |

> **Koreksi catatan awal:** `Document Vault` dan `Key Milestones` adalah **toggle
> berlatar warna di dalam kartu**, bukan tautan ke database. Isinya belum terlihat.

### Programme & Deliverables

View `Table` + `Timeline`, dikelompokkan per work stage.

| Kolom | Tipe | Opsi |
| --- | --- | --- |
| Name | Title | `Appointment Signed`, `Brief Questionnaire`, `Initial Design Workshop`, `Site Visit`, `Other Relevant Surveys`, `Measured Building Survey`, `Design Workshop 01`, `Design Workshop 02`, `Feasibility Study` |
| Status | Select | `Complete` hijau · `Not Started` abu · `Ongoing` kuning |
| Target Completion | Date | |
| Person | Person | |

Grup terbaca: `Stage 0` · `Stage 1` · `Stage 2`

---

## C. INTRODUCTION

Wordmark `INTRO-`. Icon tiga orang.

- Callout `Working with Us` — "This page introduces our process which is designed to be
  enjoyable, interactive, and inclusive. It encompasses sketches, drawings, digital and
  physical models — developing from experimental to polished — to transform your home or
  building with as much joy and excitement that we can bring."
- Heading `Design Process`
- Callout `3 Key Phases:` — "Detailed below are the phases we will embark on together to
  shape the design and delivery of your project:"
- Tiga callout berwarna, tiap satu berisi toggle `Click to see what's involved`:

| Fase | Warna | Icon |
| --- | --- | --- |
| `Planning` | ungu/maroon lembut | palet |
| `Technical Design` | hijau sage | pensil garis |
| `Construction` | cokelat khaki | kunci inggris |

- Callout `RIBA Plan of Work` + toggle "Click to find a copy of the RIBA Plan of Work
  upon which these stages are designed."
- Heading `Communication` — dua kolom:

Kolom kiri, tiga callout abu:
| Judul | Teks |
| --- | --- |
| `Working Hours` | Our studio is open between 08.00AM - 16:00PM GMT, Monday to Friday excluding bank holidays. As a small practice, any holiday leave is planned in advance and arranged to provide little to no impact to our timeline. |
| `Response Time` | As an architect's role requires site visits, meetings and focused design sessions, we are often pre-occupied for un-scheduled contact. We aim to respond within one working day and appreciate your patience. |
| `Scheduled Calls / Meetings` | This is your project and we believe in instilling a collaborative culture. We do this by scheduling physical meetings and virtual calls at strategic points during each stage, as set out here → Meetings. |

Kolom kanan, tiga callout judul merah:
| Judul | Isi |
| --- | --- |
| `Studio Hours` | Monday - Friday 08:00-16:00 GMT |
| `Contact` | **Email** youremail@yourpractice.com · **Mobile** +44123456789 |
| `Meetings` | **Virtual** – Microsoft Teams · **Physical** – Link Google Map to Practice Address |

- Heading `Frequently Asked Questions` — toggle:
  - When will the work stages be completed?
  - Can I request additional services?
  - Is it possible to pause at the end of each work stage?
  - What is your availability on a daily basis?
  - How long will my planning application take?
  - Do you have a refund policy?

---

## D. BRIEF

Icon dokumen.

### Heading `Brief Questionnaire`

- Callout `Fill in the questionnaire` (icon lapisan) — "Our design process is tailored
  specifically to you, your family, and your lifestyle. To inform this, we have prepared
  a set of targeted questions below which we will use to prepare your brief."
- Lima toggle judul merah: `Space` · `Function` · `Aspiration` · `Pinterest Board` · `Budget`

### Heading `Programme + Budget Worksheet`

- Callout (icon uang) — "As design options emerge, we will use this budget worksheet as a
  means of testing high-level costs."
- Database, view `Table`:

| Kolom | Tipe | Catatan |
| --- | --- | --- |
| Space | Title | |
| Type | Select | lihat opsi di bawah |
| SQM | Number | footer `SUM 57` |
| Est. Cost per SQM | Number GBP | |
| Est. Cost excl. VAT | **Formula** (ikon Σ) | = SQM × Est. Cost per SQM · footer `SUM £125,500.00` |
| Notes | Text | |

Opsi `Type` beserta warna:
`Extension` ungu · `Minor Refurbishment` kuning · `Moderate Refurbishment` abu ·
`Extensive Refurbishment` merah bata · `Provisional Lump Sum` cokelat

Baris contoh:
| Space | Type | SQM | per SQM | excl. VAT |
| --- | --- | --- | --- | --- |
| Living | Extension | 30 | £2,500.00 | £75,000.00 |
| Hallway | Minor Refurbishment | 6 | £500.00 | £3,000.00 |
| Bedroom 01 | Moderate Refurbishment | 15 | £1,000.00 | £15,000.00 |
| Bathroom 01 | Extensive Refurbishment | 5 | £1,500.00 | £7,500.00 |
| Kitchen Fit-Out | Provisional Lump Sum | 1 | £25,000.00 | £25,000.00 |

### Heading `Resources`

- Callout (icon dokumen) — "Below is a space for you to attach any key documents,
  surveys, red line boundaries etc that will assist us with our design process."
- Dua toggle merah: `Existing Site Information` · `Existing Property Information`

---

## E. CONTRACT

Wordmark `CONTRACT`. Icon dokumen-pensil.

- Callout `Our Appointment` (icon orang) — "The purpose of our contract is to agree a
  clear basis for working together. It includes our scope of work, fee, responsibilities,
  your client rights, our PII insurance statement and what you can do in the (unlikely)
  event of a complaint. Please do not hesitate to contact us if you have any queries."
- Heading `Our Contract` — dua kolom:

**Kolom kiri — `Contract Details`** (judul merah, icon dokumen)
"We'll use the information below to complete the contract details, please let us know if
there are any errors. If all is correct, you can download the draft contract for review."

**Client Contact Details**
- Responsible Person Name
- Address Line 1
- Address Line 2
- Town
- County
- Post Code

`Mobile:` · `Email:`

**Kolom kanan — `Signed Contract`** (judul merah, icon centang)
"Please download the draft contract from the link, complete the highlighted details and
upload the signed version below. As always, if you have any queries please just let us know."

- `Draft Contract` → blok file "Upload or embed a file"
- `Signed Contract` → blok file "Upload or embed a file"
- `Signed by :` → tiga to-do: `Your Name` · `Client Name` · `Witness Name (if required)`

---

## F. BILLING

Wordmark `BILLING`. Heading `Drawdown Schedule`.

### Database `Drawdown Schedule` — view Table

| Kolom | Tipe | Opsi |
| --- | --- | --- |
| Status | Select | `Paid` hijau · `Awaiting` merah muda · `Not Issued` abu |
| Value | Number GBP | footer `SUM £16,650.00` |
| Due | Date | |

Nilai contoh: £1,000 · £1,500 · £900 · £1,350 · £1,900 · £1,900 · £1,900 · £1,550 ×4

Blok `Payment Method` — via Bank Transfer · Bank Name · Account Name · Account Number ·
Sort Code

**Catatan:** penagihan referensi adalah **drawdown bertahap mengikuti work stage**, bukan
DP/pelunasan dua termin.

---

## G. DIRECTORY

Wordmark `DIRECTORY`.

- Callout `People` (icon orang) — "No project is completed by an individual, but is
  instead a creative collaboration between our clients ourselves and our key consultants.
  Below you'll find our project directory that'll continue to grow as we progress through
  the stages"
- Heading `Project Directory`
- Empat toggle merah: `Client Team` · `Design Team` · `Contractor Team` · `Statutory Officers`

---

## H. MEETINGS

Wordmark `MEETINGS`. Icon tiga orang.

- Callout `Our Meetings` — "On this page we can schedule, track and view our meetings and
  notes throughout your project work stages."

### Database `Meeting Schedule` — view Table

| Kolom | Tipe | Opsi |
| --- | --- | --- |
| Work Stage | Select | `Stage 0` oranye · `Stage 1` merah muda |
| Meeting | Title | |
| Date | Date + time | `19/02/2024 12:00` |
| Status | Select | `Done` hijau · `Scheduled` abu |
| Participant | Person | |
| Link | URL | `meet.google.com/…` atau teks `Studio` |
| Virtual | Checkbox | |
| Physical | Checkbox | |

### `Meeting Agendas` — view `All Notes` (gallery) + `Table`
Kartu `Stage 1 Design Review Agenda` · tag `Meeting Agenda` **biru**

### `Meeting Minutes` — view `All Notes` (gallery) + `Table`
Kartu `Stage 1 Design Review Minutes` · tag `Meeting Minutes` **hijau**

> Masih dugaan: kemungkinan **satu database Notes** dengan properti tipe, ditampilkan
> sebagai dua linked view terfilter. Petunjuk: nama view sama-sama `All Notes`.

---

## I. FEEDBACK

- Callout `Thank you.` (icon senyum):
  "It's been a pleasure working with you, and please do keep in touch!
  As a small design studio we'd be very grateful if you could leave us a review that we
  can use as a testimonial for future work.
  Stay in touch with us on social media."
  Bullet: `Instagram` · `X` · `TikTok`
- Toggle `Google Review` → berisi callout latar merah gelap (icon tulis):
  "Leave us a Google Review here:" + placeholder italic "Paste your Google Review Link
  from your Google Business Account here."
- Toggle `Feedback Form`

---

## Bahasa visual

| Unsur | Nilai |
| --- | --- |
| Mode | Gelap. Ada tombol `Switch to Dark/Light Mode` di Portal Hub |
| Cover halaman | Krem terang, wordmark hitam rata kanan, huruf besar rapat |
| Heading section | Merah koral + garis horizontal tipis |
| Callout netral | Abu gelap |
| Callout berwarna | Tiga fase desain · Document Vault & Key Milestones cokelat · Complete hijau · Google Review merah gelap |
| Aksen tahap berjalan | Oranye terang |
| Tahap akhir `07` | Putih/krem |
| Icon | Icon garis Notion, bukan emoji |
| Teks kartu | Italic |

---

## Belum terlihat — perlu materi berikutnya

- Isi toggle `Space`, `Function`, `Aspiration`, `Pinterest Board`, `Budget` di Brief
- Isi toggle `Document Vault` dan `Key Milestones` di tiap kartu Our Journey
- Isi toggle `Client Team`, `Design Team`, `Contractor Team`, `Statutory Officers`
- Isi toggle tiap fase desain (`Click to see what's involved`)
- Isi toggle `Feedback Form` dan enam toggle FAQ
- Halaman `Resources` dan `Provide a Review` di Portal Hub
- Tata letak penuh halaman Billing (baru terlihat potongan mobile)
- Automasi dan tombol, kalau ada
- **PDF pertama dari client + prompt-nya** — belum diterima, dibutuhkan untuk memisahkan
  mana replika dan mana tambahan
