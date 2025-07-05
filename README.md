

# 📂 README - Aplikasi Tracker Investasi Emas ANTM

Hai\! Selamat datang di dokumentasi untuk Aplikasi Tracker Investasi Emas. Aplikasi ini saya buat untuk membantu kamu mencatat dan memantau perkembangan investasi emas dengan mudah, langsung dari Google Sheets yang kamu miliki.

Tujuannya simpel: agar kamu tidak perlu lagi pusing menghitung manual di spreadsheet setiap kali ada transaksi baru atau setiap kali harga emas berubah. Semua serba otomatis dan bisa kamu lihat dalam bentuk dashboard yang menarik.

-----

## ✨ Fitur Utama

Aplikasi ini punya beberapa halaman utama yang akan membantumu:

  * **📊 Dashboard Visual:** Halaman utama yang memberikanmu gambaran besar tentang investasimu. Kamu bisa lihat total aset, total modal, perkiraan nilai jual, sampai floating profit/loss dalam bentuk angka dan grafik yang cantik.
  * **📝 Form Input Mudah:** Gak perlu lagi buka Google Sheet untuk nambah data. Cukup isi form di aplikasi web, klik simpan, dan data akan otomatis masuk ke spreadsheet-mu.
  * **📈 Laporan Detail:** Ingin lihat rincian setiap transaksi investasi? Halaman ini menampilkannya dalam bentuk tabel yang rapi, lengkap dengan perhitungan profit/loss per transaksi. Ada fitur paginasi juga, jadi gak akan berat walaupun datanya sudah banyak.
  * **💰 Manajemen Harga Emas:** Kamu bisa mengatur daftar harga emas (misal: harga Antam per gram) dan yang paling penting, kamu bisa mengatur **harga buyback umum** yang akan jadi patokan untuk semua perhitungan profit di seluruh aplikasi.
  * **🤖 Kalkulasi Otomatis:** Ini bagian terbaiknya. Setiap kali kamu menambah/mengubah data lewat form, atau bahkan saat kamu mengedit langsung di Google Sheet, skrip akan otomatis berjalan untuk menghitung ulang semua profit/loss. Praktis\!

-----

## 🖼️ Tampilan Aplikasi

Supaya kamu ada bayangan, begini kira-kira tampilan setiap halamannya:

### 1\. Halaman Dashboard

Ini adalah pusat komando kamu. Di sini kamu bisa langsung melihat:

  - **Kartu Statistik:** Total gram emas, modal yang sudah dikeluarkan, estimasi nilai jual saat ini, dan floating untung/rugi.
  - **Grafik Garis:** Perbandingan antara modal yang kamu keluarkan dengan estimasi harga jual dari waktu ke waktu.
  - **Grafik Batang:** Perbandingan simpel antara total modal vs total nilai jual.
  - **Progress Bar:** Mengukur sejauh mana kamu sudah mencapai target gram atau target nilai jual yang kamu tetapkan sendiri.

### 2\. Halaman Form Investasi

Halaman ini didesain sesimpel mungkin. Kamu hanya perlu mengisi:

  - Tanggal beli
  - Berat emas (opsinya diambil dari sheet "Harga Emas")
  - Nominal beli (total uang yang kamu keluarkan)
  - Klik simpan, selesai\! Kamu juga bisa mengedit data yang sudah ada dari halaman ini.

### 3\. Halaman Laporan

Semua data investasimu ditampilkan di sini dalam bentuk tabel. Setiap barisnya adalah satu transaksi, lengkap dengan kalkulasi:

  - Harga Pokok Penjualan (HPP) per gram.
  - Estimasi nilai jual berdasarkan harga buyback terkini.
  - Profit/Loss dalam Rupiah dan Persentase.
  - Tombol **Edit** dan **Hapus** untuk setiap baris data.

### 4\. Halaman Harga Emas

Di sini adalah tempat kamu mengatur "master data" harga.

  - **Tabel Harga Emas:** Kamu bisa mengisi daftar berat emas dan harganya. Opsi ini akan muncul di dropdown pada Form Investasi.
  - **Update Harga Buyback Umum:** Harga per gram yang kamu masukkan di sini akan menjadi acuan untuk semua perhitungan profit/loss di halaman Dashboard dan Laporan.

-----

## ⚙️ Cara Kerja & Alur Data

Mungkin kamu bertanya-tanya, "Gimana sih cara kerjanya tanpa database beneran?" Jawabannya simpel: kita manfaatkan kekuatan **Google Sheets** sebagai "database" dan **Google Apps Script** sebagai "otak" atau backend-nya.

Alurnya seperti ini:

1.  **Kamu (User):** Mengakses Aplikasi Web (HTML/CSS/JS) di browser.
2.  **Aplikasi Web:** Semua interaksi seperti klik tombol atau isi form akan memanggil fungsi yang ada di Google Apps Script.
3.  **Google Apps Script (Backend):**
      * Menerima perintah dari Aplikasi Web.
      * Membaca atau menulis data ke Google Sheet (misalnya, menyimpan data investasi baru).
      * Melakukan semua perhitungan rumit (`hitungProfitInvestasi`).
      * Mengirimkan data yang sudah matang kembali ke Aplikasi Web.
4.  **Aplikasi Web:** Menerima data matang dari Apps Script dan menampilkannya dengan cantik ke kamu.

Semua terjadi di belakang layar, jadi kamu tinggal pakai saja dengan nyaman\!

-----

## 🚀 Panduan Instalasi & Penggunaan

Oke, sekarang bagian paling penting. Ikuti langkah-langkah ini secara berurutan ya.

### Langkah 1: Siapkan Google Sheet Kamu

Aplikasi ini butuh struktur Google Sheet yang spesifik. Kamu tidak perlu membuatnya dari nol, cukup buat salinan dari template yang sudah ada.

1.  Buka link Google Sheet template berikut: **[Link ke Google Sheet Template Kamu]** *(Catatan: Kamu perlu membuat sheet-nya terlebih dahulu dan membagikan link-nya di sini)*.
2.  Klik **File** -\> **Make a copy**. Beri nama sesukamu, misalnya "Tracker Emas Pribadi".
3.  Sekarang kamu punya spreadsheet-mu sendiri yang siap digunakan.

### Langkah 2: Dapatkan ID Spreadsheet

Setiap Google Sheet punya ID unik.

1.  Lihat URL spreadsheet yang baru saja kamu salin.
2.  URL-nya akan terlihat seperti ini: `https://docs.google.com/spreadsheets/d/XXXXXXXXXXXXXXXXXXXXXXXXXXXX/edit`
3.  Salin bagian `XXXXXXXXXXXXXXXXXXXXXXXXXXXX` itu. Itulah **ID Spreadsheet** kamu. Simpan di notepad dulu.

### Langkah 3: Siapkan Google Apps Script

Ini adalah tempat untuk menaruh kode "backend" aplikasi.

1.  Di file Google Sheet kamu, klik **Extensions** -\> **Apps Script**.
2.  Kamu akan masuk ke editor skrip. Hapus semua kode contoh yang ada di file `Code.gs`.
3.  Salin **semua isi** dari file `code.gs.txt` yang kamu punya, lalu tempel ke editor Apps Script.
4.  **PENTING:** Cari baris ini di bagian paling atas kode:
    ```javascript
    const SPREADSHEET_ID = '1hEl9tIuaHpw_RhtNDq30Q_dJ01PbjgzImU-HDvs69I0';
    ```
5.  Ganti nilai ID di dalam tanda kutip (`'...'`) dengan **ID Spreadsheet** yang sudah kamu salin di Langkah 2.
6.  Klik ikon **Save project** (gambar disket).

### Langkah 4: Deploy sebagai Aplikasi Web

Agar bisa diakses lewat browser, skrip ini harus di-"deploy".

1.  Di kanan atas editor Apps Script, klik tombol biru **Deploy** -\> **New deployment**.
2.  Klik ikon gerigi di sebelah "Select type", lalu pilih **Web app**.
3.  Isi konfigurasinya:
      * **Description:** (Opsional) Isi saja, misal "Versi pertama tracker emas".
      * **Execute as:** Pilih **Me**.
      * **Who has access:** Pilih **Anyone with Google account** (hanya yang login Google bisa akses) atau **Anyone** (siapa pun dengan link bisa akses). Untuk pemakaian pribadi, **Anyone with Google account** lebih aman.
4.  Klik **Deploy**.
5.  Google mungkin akan meminta izin (otorisasi). Klik **Authorize access**, pilih akun Google-mu, klik **Advanced**, lalu **Go to (unsafe)**. Tenang saja, ini aman karena skrip ini buatanmu sendiri.
6.  Setelah sukses, kamu akan mendapatkan **Web app URL**. **Salin URL ini\!** Inilah alamat aplikasi web-mu. Kamu bisa bookmark atau bagikan ke dirimu sendiri.

**Selesai\! Aplikasi web-mu sekarang sudah aktif dan siap digunakan.**

### Langkah 5 (Opsional): Atur Trigger Otomatis

Secara default, perhitungan akan berjalan saat kamu mengedit sheet atau menyimpan data dari form. Jika kamu ingin ada perhitungan ulang secara berkala (misal setiap pagi), kamu bisa atur trigger:

1.  Di editor Apps Script, klik ikon **Triggers** (gambar jam alarm) di sebelah kiri.
2.  Klik tombol **+ Add Trigger** di kanan bawah.
3.  Atur seperti ini:
      * **Choose which function to run:** `hitungProfitInvestasi`
      * **Choose which deployment should run:** `Head`
      * **Select event source:** `Time-driven`
      * **Select type of time based trigger:** `Day timer`
      * **Select time of day:** Pilih jam yang kamu mau, misal `6am to 7am`.
4.  Klik **Save**. Sekarang, skrip akan otomatis menghitung ulang setiap hari pada jam tersebut.

-----

## 📂 Struktur File & Penjelasannya

Agar kamu lebih paham atau jika suatu saat ingin memodifikasi aplikasi ini, penting untuk tahu fungsi dari masing-masing file. Berikut adalah penjelasannya:

### `Code.gs`

Ini adalah **otak** atau **mesin utama** dari keseluruhan aplikasi. File ini berjalan di server Google, bukan di browser kamu. Semua logika penting ada di sini.

  * **Fungsi Utama**:
      * Menghubungkan aplikasi web dengan Google Sheet-mu.
      * Menangani semua permintaan data dari aplikasi web, seperti menyimpan, membaca, mengubah, dan menghapus data investasi.
      * Melakukan semua kalkulasi otomatis, seperti menghitung HPP (Harga Pokok Penjualan) per gram, estimasi nilai jual, serta profit/loss dalam bentuk Rupiah dan persentase.
      * Menyediakan data yang sudah matang untuk ditampilkan di halaman Dashboard, Laporan, dan Form.
      * Menjalankan *trigger*, baik itu saat ada editan langsung di sheet (`onEdit`) maupun trigger berbasis waktu (misalnya, setiap hari).

### `index.html`

File ini adalah **rumah** atau **kerangka utama** dari aplikasi web-mu. Isinya bukan halaman spesifik seperti dashboard atau form, melainkan komponen dasar yang selalu ada.

  * **Fungsi Utama**:
      * Menampilkan struktur dasar aplikasi, yaitu sidebar navigasi di sebelah kiri dan area konten utama di sebelah kanan.
      * Memuat konten halaman lain (`dashboard.html`, `form.html`, dll.) secara dinamis ke dalam area konten utama tanpa perlu me-refresh seluruh halaman.
      * Mengatur menu navigasi mana yang sedang aktif (misalnya, memberi warna berbeda pada menu "Dashboard" saat kamu berada di halaman itu).
      * Menyediakan elemen global seperti *loader* (animasi "memuat...") dan modal konfirmasi ("Apakah Anda yakin?") yang bisa digunakan oleh semua halaman.

### `dashboard.html`

Ini adalah **wajah** dari aplikasi web-mu, halaman pertama yang paling informatif.

  * **Fungsi Utama**:
      * Menampilkan ringkasan performa investasi dalam bentuk kartu-kartu statistik yang mudah dibaca (Total Aset, Modal, Floating Untung/Rugi, dll.).
      * Memvisualisasikan data historis melalui **Grafik Garis** untuk membandingkan estimasi harga jual vs. nominal beli dari waktu ke waktu.
      * Menyajikan **Grafik Batang** untuk perbandingan langsung antara total modal yang sudah kamu keluarkan dengan total nilai jual asetmu saat ini.
      * Terdapat **Progress Bar** untuk membantumu melacak pencapaian target investasi, baik dalam satuan gram maupun Rupiah, yang targetnya bisa kamu atur sendiri.

### `form.html`

Ini adalah halaman untuk **input data**. Di sinilah kamu berinteraksi untuk menambah atau mengubah catatan investasimu.

  * **Fungsi Utama**:
      * Menyediakan form sederhana untuk mencatat transaksi baru, yang berisi kolom tanggal beli, berat emas, dan nominal beli (modal).
      * Form ini juga digunakan untuk **mengedit data**. Jika kamu mengklik tombol "Edit" di halaman Laporan, kamu akan dibawa ke sini dengan data yang sudah terisi dan siap diubah.
      * Pilihan berat emas pada form ini tidak diketik manual, melainkan diambil secara otomatis dari daftar yang sudah kamu siapkan di sheet "Harga Emas", sehingga lebih konsisten.

### `laporan.html`

Halaman ini berfungsi sebagai **buku besar** atau **catatan rinci** dari semua investasimu.

  * **Fungsi Utama**:
      * Menampilkan semua data transaksi dalam format tabel yang terstruktur dan mudah dibaca.
      * Tidak hanya menampilkan data input, tabel ini juga menyajikan data hasil olahan dari `Code.gs`, seperti HPP/gram, estimasi jual saat ini, dan profit/loss untuk setiap transaksi.
      * Dilengkapi fitur **paginasi** (pengelompokan per halaman), sehingga aplikasi tetap ringan meskipun data investasimu sudah mencapai ratusan baris.
      * Setiap baris data memiliki tombol **Aksi** (Edit dan Hapus) untuk mengelola data secara langsung.

### `hargaemas.html`

Ini adalah halaman **pengaturan** atau **master data**. Data yang kamu atur di sini akan memengaruhi halaman lain, terutama Form dan Laporan.

  * **Fungsi Utama**:
      * Kamu bisa mengelola daftar berat emas beserta harganya. Daftar inilah yang akan menjadi opsi di dropdown 'Berat Emas' pada halaman Form Investasi.
      * Terdapat input khusus untuk memperbarui **Harga Buyback Umum**. Angka yang kamu masukkan di sini adalah acuan utama yang digunakan oleh `Code.gs` untuk menghitung semua profit/loss di seluruh aplikasi. Jadi, saat harga buyback di pasaran berubah, kamu cukup update di sini saja.
