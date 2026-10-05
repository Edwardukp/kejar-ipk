# Kejar IPK

Kalkulator sederhana untuk mahasiswa yang ingin tahu **IP minimal yang harus didapat tiap semester** supaya IPK tembus target, misalnya cumlaude.

**Link demo:** https://Edwardukp.github.com/kejar-ipk/ 

Masalah yang diselesaikan

Banyak mahasiswa punya target IPK (lulus cumlaude 3,51, minimal 3,00 untuk syarat beasiswa atau melamar kerja), tapi tidak tahu:

* IP berapa yang harus dikejar semester depan,
* apakah targetnya masih mungkin dicapai sebelum lulus,
* dan nilai seperti apa yang dibutuhkan (berapa SKS harus dapat A).

Menghitungnya manual dengan rumus IPK cukup membingungkan, jadi banyak yang hanya menebak-nebak.

## Solusi

Kejar IPK cukup meminta 5 angka dari KHS (Kartu Hasil Studi):

1. IPK sekarang
2. SKS yang sudah lulus
3. Target IPK
4. Rencana SKS per semester
5. Sisa semester sampai lulus

Lalu aplikasi langsung menampilkan:

* **IP minimal per semester** yang dibutuhkan, beserta status: *Realistis*, *Kerja keras*, *Hampir sempurna*, atau *Tidak terkejar*.
* **Contoh kombinasi nilai**, misalnya "13 SKS nilai A + 7 SKS nilai AB/B+", supaya angkanya mudah dibayangkan.
* **Pilihan jalur**: target dicapai semester depan, beberapa semester lagi, atau saat lulus.
* **IPK tertinggi yang masih mungkin dicapai** kalau target ternyata tidak terkejar.
* **Skala IPK** dengan zona predikat kelulusan (Memuaskan, Sangat memuaskan, Pujian/cumlaude).
* **Cara hitung** yang transparan, sehingga hasilnya bisa dicek manual.

Data yang diisi tersimpan otomatis di browser (localStorage), jadi tidak perlu mengetik ulang.

## Cara menjalankan

Aplikasi ini hanya satu file HTML. Tidak perlu instalasi, server, atau akun.

**Langsung di komputer**

1. Download atau clone repository ini.
2. Klik dua kali `index.html` untuk membukanya di browser (Chrome, Firefox, Edge, atau Safari).

**Online**

Buka link demo di atas dari browser laptop atau HP.

