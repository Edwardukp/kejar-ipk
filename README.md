# Kejar IPK

Kalkulator sederhana untuk mahasiswa yang ingin tahu **IP minimal yang harus didapat tiap semester** supaya IPK tembus target, misalnya cumlaude.

**Link demo:** https://USERNAME.github.io/kejar-ipk/ *(ganti USERNAME dengan username GitHub kamu)*

---

## Daftar isi

1. [Masalah yang diselesaikan](#masalah-yang-diselesaikan)
2. [Solusi dan fitur](#solusi-dan-fitur)
3. [Kebutuhan](#kebutuhan)
4. [Cara menjalankan aplikasi](#cara-menjalankan-aplikasi)
5. [Cara pakai](#cara-pakai)
6. [Rumus yang dipakai](#rumus-yang-dipakai)
7. [Proses AI](#proses-ai)
8. [Keputusan teknis](#keputusan-teknis)
9. [Batasan dan pengembangan berikutnya](#batasan-dan-pengembangan-berikutnya)
10. [Struktur project](#struktur-project)

---

## Masalah yang diselesaikan

Banyak mahasiswa punya target IPK, misalnya lulus cumlaude (3,51) atau minimal 3,00 untuk syarat beasiswa dan melamar kerja. Tapi mereka tidak tahu:

- IP berapa yang harus dikejar semester depan,
- apakah targetnya masih mungkin dicapai sebelum lulus,
- dan nilai seperti apa yang dibutuhkan (berapa SKS harus dapat A).

Menghitungnya manual dengan rumus IPK cukup membingungkan, jadi banyak yang hanya menebak-nebak. Akibatnya ada yang terlalu santai padahal targetnya sudah hampir tidak terkejar, dan ada juga yang stres mengejar target yang sebenarnya sudah aman.

## Solusi dan fitur

Kejar IPK cukup meminta 5 angka dari KHS (Kartu Hasil Studi), lalu langsung menampilkan:

- **IP minimal per semester** yang dibutuhkan, beserta status: *Sudah aman*, *Realistis*, *Kerja keras*, *Hampir sempurna*, atau *Tidak terkejar*.
- **Saran singkat** sesuai status, termasuk kapan target paling cepat bisa dicapai kalau saat ini belum terkejar.
- **Contoh kombinasi nilai**, misalnya "13 SKS nilai A + 7 SKS nilai AB/B+", supaya angkanya mudah dibayangkan.
- **Pilihan jalur**: target dicapai semester depan, beberapa semester lagi, atau saat lulus.
- **IPK tertinggi yang masih mungkin dicapai** kalau semua nilai A.
- **Skala IPK** dengan zona predikat kelulusan (Memuaskan, Sangat memuaskan, Pujian/cumlaude).
- **Cara hitung** yang transparan, sehingga hasilnya bisa dicek manual.

## Kebutuhan

### Kebutuhan untuk menjalankan

| Kebutuhan | Keterangan |
|---|---|
| Browser modern | Chrome, Firefox, Edge, atau Safari versi terbaru (laptop maupun HP) |
| Koneksi internet | Opsional. Hanya dipakai untuk memuat font dari Google Fonts. Tanpa internet, aplikasi tetap berjalan dengan font bawaan |
| Instalasi | Tidak ada. Tidak perlu Node.js, Python, server, database, atau akun |

### Kebutuhan fungsional

Yang harus bisa dilakukan aplikasi:

1. Menerima input IPK sekarang, SKS lulus, target IPK, SKS per semester, dan sisa semester.
2. Menerima angka desimal dengan koma (format Indonesia, `3,21`) maupun titik (`3.21`).
3. Menghitung IP minimal per semester untuk setiap jalur waktu (1 semester sampai sisa semester).
4. Memberi tahu apakah target realistis, berat, atau tidak mungkin dicapai (IP di atas 4,00).
5. Menampilkan IPK tertinggi yang masih bisa dicapai.
6. Memvalidasi input dan menampilkan pesan yang jelas kalau ada isian yang salah.
7. Mengingat isian terakhir pengguna di browser.

### Kebutuhan non-fungsional

- Hasil langsung muncul saat mengetik, tanpa tombol "Hitung".
- Nyaman dipakai di layar HP.
- Mendukung mode gelap.
- Data pengguna tidak dikirim ke mana pun (privasi terjaga).

## Cara menjalankan aplikasi

### Opsi 1: Buka langsung di komputer

1. Download repository ini (tombol **Code → Download ZIP**), lalu ekstrak. Atau clone:
   ```bash
   git clone https://github.com/USERNAME/kejar-ipk.git
   ```
2. Buka folder `kejar-ipk`.
3. Klik dua kali `index.html`. Aplikasi akan terbuka di browser.

### Opsi 2: Buka versi online

Buka link demo di bagian atas README dari browser laptop atau HP.

### Opsi 3: Deploy sendiri gratis dengan GitHub Pages

1. Fork atau upload project ini ke repository GitHub milikmu.
2. Buka **Settings → Pages**.
3. Pada bagian *Branch*, pilih `main` dan folder `/ (root)`, lalu klik **Save**.
4. Tunggu 1–2 menit. Situs akan tersedia di `https://USERNAME.github.io/kejar-ipk/`.

## Cara pakai

1. Buka KHS atau transkrip terakhirmu di SIAKAD kampus.
2. Isi **IPK sekarang** dan **SKS yang sudah lulus**.
3. Isi **Target IPK**, atau klik salah satu pilihan cepat (3,01 / 3,51 Cumlaude / 3,75).
4. Isi **SKS per semester** yang kamu rencanakan dan **sisa semester** sampai lulus.
5. Lihat hasil IP minimal di panel kanan (atau di bawah form kalau dibuka di HP).
6. Klik jalur lain di bagian **"Kapan target harus tercapai?"** untuk membandingkan.

Angka yang muncul saat pertama kali dibuka adalah contoh. Klik **"Kembalikan angka contoh"** untuk mengulang.

## Rumus yang dipakai

```
Mutu sekarang = IPK sekarang × SKS lulus
Mutu target   = Target IPK × (SKS lulus + jumlah semester × SKS per semester)
IP minimal    = (Mutu target − Mutu sekarang) ÷ (jumlah semester × SKS per semester)
IPK maksimal  = (Mutu sekarang + 4 × SKS tersisa) ÷ total SKS
```

**Contoh:** IPK 3,21 dengan 80 SKS, target 3,51 dalam 4 semester @ 20 SKS
→ (3,51 × 160 − 3,21 × 80) ÷ 80 = **3,81 per semester**.

Bobot nilai: A 4,00 · AB/B+ 3,50 · B 3,00 · BC/C+ 2,50 · C 2,00 · D 1,00 · E 0,00.
Batas predikat: Memuaskan 2,76–3,00 · Sangat memuaskan 3,01–3,50 · Pujian 3,51–4,00.

> Skala nilai dan syarat predikat bisa berbeda di tiap kampus. Beberapa kampus juga mensyaratkan lulus tepat waktu dan tanpa nilai D/E untuk cumlaude. Cek buku pedoman akademik kampusmu.

## Proses AI

Project ini dibuat dengan bantuan **Claude (Anthropic), model Claude Opus 5.5**, melalui claude.ai. Berikut alurnya:

| Tahap | Yang saya lakukan | Yang dibantu AI |
|---|---|---|
| 1. Menentukan masalah | Memberikan brief challenge: "buat aplikasi sederhana untuk membantu mahasiswa" | Memilih satu masalah yang spesifik dan sering dialami: menghitung IP yang dibutuhkan untuk mencapai target IPK |
| 2. Merancang fitur | Menyetujui arah aplikasi | Menentukan input yang dibutuhkan (5 angka dari KHS) dan output yang berguna (IP minimal, status, contoh nilai, jalur waktu, skala predikat) |
| 3. Desain tampilan | Meninjau hasil | Membuat konsep visual "kertas kotak-kotak dan stabilo" yang dekat dengan dunia mahasiswa, termasuk mode gelap dan tampilan HP |
| 4. Menulis kode | Meminta file HTML-nya | Menulis seluruh kode HTML, CSS, dan JavaScript dalam satu file |
| 5. Verifikasi | Mencoba aplikasi | Mengecek sintaks JavaScript dan menguji rumus dengan contoh angka |
| 6. Dokumentasi & deploy | Meminta README, upload ke GitHub, dan deploy ke GitHub Pages | Menulis README dan memberikan langkah deploy gratis |

**Contoh prompt yang dipakai:**

- *"Buat aplikasi sederhana untuk membantu mahasiswa. Pilih satu masalah mahasiswa, lalu buat solusi yang bisa dicoba. Sederhana saja, tidak perlu yang kompleks."*
- *"Bisa tolong berikan saya filenya."*
- *"Isi README dengan masalah yang diselesaikan dan cara menjalankan aplikasi."*
- *"Cara deploy webnya gimana? Secara sederhana dan gratis."*

**Yang saya pelajari:** AI sangat cepat untuk membuat versi pertama yang sudah berjalan, tapi hasilnya tetap perlu dicek. Rumus perhitungan saya cocokkan manual dengan angka dari KHS, dan batas predikat saya cek ulang dengan pedoman kampus.

## Keputusan teknis

| Keputusan | Alasan |
|---|---|
| **Satu file `index.html`** (HTML + CSS + JS jadi satu) | Paling mudah dijalankan dan di-deploy. Cukup klik dua kali atau upload satu file ke GitHub Pages |
| **JavaScript murni, tanpa framework** (tanpa React/Vue) | Aplikasinya kecil. Framework hanya menambah langkah build dan instalasi tanpa manfaat berarti |
| **Tanpa backend dan database** | Semua perhitungan bisa dilakukan di browser. Hosting jadi gratis, dan data nilai mahasiswa tidak pernah dikirim ke server |
| **`localStorage` untuk menyimpan isian** | Pengguna tidak perlu mengetik ulang saat membuka lagi. Dibungkus `try/catch` supaya aplikasi tetap jalan kalau penyimpanan browser diblokir (misalnya mode incognito) |
| **Input teks dengan `inputmode="decimal"`, bukan `type="number"`** | Orang Indonesia menulis desimal dengan koma (`3,21`). Input `type="number"` sering menolak koma di beberapa browser. Aplikasi menerima koma maupun titik, dan keyboard angka tetap muncul di HP |
| **IP minimal dibulatkan ke atas** (contoh 3,805 → 3,81) | Supaya mahasiswa tidak kurang sedikit dari target. Sebaliknya, IPK maksimal dibulatkan ke bawah supaya tidak memberi harapan berlebihan |
| **Contoh nilai dihitung dengan pembulatan ke atas jumlah SKS nilai tinggi** | Kombinasi nilai yang disarankan selalu menghasilkan IP yang memenuhi target, bukan sedikit di bawahnya |
| **Hasil dihitung ulang setiap kali mengetik** | Lebih cepat dan intuitif dibanding tombol "Hitung". Pengguna bisa langsung mencoba "bagaimana kalau" dengan angka berbeda |
| **Ambang status** (≤ 3,50 realistis, ≤ 3,85 kerja keras, ≤ 4,00 hampir sempurna, > 4,00 tidak terkejar) | Dipilih berdasarkan skala nilai: di atas 3,50 berarti mayoritas nilai harus A, dan di atas 4,00 secara matematis tidak mungkin |
| **Warna dari variabel CSS dan `prefers-color-scheme`** | Mode gelap mengikuti pengaturan perangkat tanpa perlu kode tambahan |
| **Validasi rentang input** (IPK 0–4, SKS per semester 1–30, sisa semester 1–14) | Mencegah hasil aneh dari salah ketik, dengan pesan error yang menjelaskan cara memperbaikinya |
| **Atribut aksesibilitas** (`aria-live`, `aria-pressed`, label untuk tiap input) | Hasil perhitungan bisa dibacakan pembaca layar, dan semua kontrol bisa dipakai dengan keyboard |

## Batasan dan pengembangan berikutnya

**Batasan saat ini:**

- Skala bobot nilai dibuat tetap (A = 4,00, AB/B+ = 3,50, dan seterusnya), sedangkan beberapa kampus memakai skala lain seperti A− = 3,75.
- Belum memperhitungkan mata kuliah yang diulang (nilai lama diganti nilai baru).
- Data hanya tersimpan di satu browser, tidak tersinkron antar perangkat.

**Ide pengembangan:**

- Pilihan skala nilai sesuai kampus.
- Mode simulasi per mata kuliah: masukkan daftar mata kuliah semester depan beserta perkiraan nilainya.
- Fitur mengulang mata kuliah untuk melihat dampaknya ke IPK.

## Struktur project

```
kejar-ipk/
├── index.html   # seluruh aplikasi (tampilan, gaya, dan logika)
└── README.md    # dokumentasi ini
```
