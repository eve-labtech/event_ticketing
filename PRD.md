# Product Requirement Document (PRD)
# 1. Apa yang Akan Dibangun?
Website Event Ticketing adalah sebuah platform berbasis web yang dirancang untuk menyederhanakan seluruh proses manajemen tiket event (seperti festival atau acara skala kecil-menengah).

Platform ini menghubungkan dua pihak utama:
- Pembeli Tiket: Memudahkan dalam mencari informasi event, melakukan pemesanan tiket, hingga menerima E-Ticket resmi secara online.
- Panitia Event: Membantu dalam mengelola data acara, memantau alokasi kuota secara real-time, serta melakukan verifikasi/validasi tiket fisik di lokasi acara secara cepat.

# 2. Apa Saja yang Dibutuhkan untuk Membangun?
## 2.1 Kebutuhan Perangkat Lunak & Teknologi (Tech Stack)
- Frontend: HTML, CSS / Framework CSS (misal: Tailwind CSS / Bootstrap), JavaScript.
- Backend: Laravel.
- Database: MySQL (untuk menyimpan data pengguna, event, transaksi, dan kode tiket).
- Environment & Tools: Code Editor (VS Code), Web Server (XAMPP / Node Environment), Git & GitHub (version control).

## 2.2 Kebutuhan Non-Fungsional System
- Responsif: Tampilan UI dapat menyesuaikan layar HP (Mobile) maupun Komputer/Laptop (Desktop) dengan rapi.
- Performa & Kecepatan Validasi: Proses pengecekan keabsahan kode tiket di lokasi acara oleh panitia wajib selesai dalam waktu kurang dari 5 detik per tiket.

## 2.3 Batasan Sistem 
1. Pembayaran menggunakan Simulasi Pembayaran (belum menggunakan API Payment Gateway riil).
2. Sistem digunakan terbatas pada cakupan satu regional.
3. Penjualan difokuskan untuk acara jenis festival atau event sederhana.

# 3. Fitur Apa Saja yang Akan Dibangun?
## 3.1 Fitur Pengguna (Pembeli / User)
1. Autentikasi (Register & Login): Pendaftaran akun baru dan akses masuk pengguna.
2. Katalog & Pencarian Event: Menampilkan daftar event beserta fitur pencarian dan kategori acara.
3. Detail Event & Form Pemesanan: Menampilkan detail event (poster, tanggal, lokasi, harga, deskripsi) dan form input jumlah tiket.
4. Simulasi Pembayaran: Pemilihan metode pembayaran (Bank Transfer / E-Wallet) dan konfirmasi pembayaran.
5. E-Ticket & Kode Tiket Unik: Penerbitan tiket elektronik yang memuat kode acak unik setelah pemesanan berhasil.

## 3.2 Fitur Panitia (Admin)
1. Dashboard Admin: Ringkasan statistik penjualan, sisa kuota, dan total pendapatan.
2. Manajemen Event (CRUD Event): Tambah, lihat, ubah, dan hapus data event.
3. Manajemen Tiket & Kuota: Pengaturan batas kuota tiket yang terintegrasi secara otomatis saat transaksi terjadi.
4. Verifikasi & Validasi Tiket: Fitur pencarian/scan kode tiket unik untuk mengecek keabsahan dan status tiket di pintu masuk acara.

# 4. Siapa Saja yang Akan Menggunakan Sistem Ini
Sistem ini dirancang untuk 2 jenis pengguna (Aktor) dengan hak akses yang berbeda:
1. Pembeli (User / Publik):
- Peran: Calon pengunjung acara.
- Tujuan: Mencari event, memesan tiket, melakukan pembayaran simulasi, dan mendapatkan bukti E-Ticket.
2. Panitia / Admin:
- Peran: Pengelola acara di balik layar dan petugas gate di lokasi event.
- Tujuan: Menginput data event, memantau penjualan kuota tiket, dan memvalidasi E-Ticket pengunjung saat hari pelaksanaan acara.

# 5. Bagaimana Alur Sistem Berjalan pada Setiap Fitur
Berikut alur teknis langkah demi langkah untuk setiap fitur utama:
## 5.1 Alur Registrasi & Login (User & Admin)
1. Pengguna membuka halaman Login/Register.
2. Pengguna memasukkan data diri (Email & Password).
3. Sistem memvalidasi kelengkapan data.
4. Jika data sesuai, sistem menyimpan akun ke database dan mengarahkan pengguna ke Dashboard sesuai dengan peran (role) masing-masing.

## 5.2 Alur Pencarian & Detail Event (User)
1. User masuk ke halaman Daftar Event.
2. User dapat mengetikkan kata kunci pada bilah pencarian atau memilih kategori event.
3. Sistem menampilkan daftar event yang cocok.
4. User memilih salah satu event untuk masuk ke halaman Detail Event (menampilkan tanggal, lokasi, harga, dan sisa kuota).

## 5.3 Alur Pemesanan Tiket & Pengecekan Kuota (User)
1. Dari halaman detail event, User menekan tombol Pesan / Beli Tiket.
2. User mengisi form pemesanan (jumlah tiket dan data pemesan).
3. Pengecekan Kuota Otomatis oleh Sistem:
- Jika Sisa Kuota < Jumlah Tiket yang Dipesan: Sistem membatalkan proses dan menampilkan pesan "Tiket Habis / Kuota Tidak Cukup".
- Jika Kuota Masuk Akal: Sistem melanjutkan ke halaman pembayaran.

## 5.4 Alur Pembayaran & Generate E-Ticket (User)
1. User memilih opsi metode pembayaran simulasi (Bank Transfer / E-Wallet).
2. User menekan tombol Bayar Sekarang.
3. Sistem memproses simulasi pembayaran.
4. Setelah transaksi berstatus berhasil:
- Sistem mengurangi kuota event secara otomatis.
- Sistem membuat (generate) Kode Tiket Unik berupa kombinasi acak huruf dan angka (contoh: TKT-8X91A).
5. Sistem menerbitkan E-Ticket yang menampilkan informasi event, nama pembeli, jumlah tiket, dan kode acak tiket.

## 5.5 Alur Manajemen Data Event (Admin)
1. Admin mengakses Dashboard Admin dan memilih menu Kelola Event.
2. Admin mengisi form tambah event (Nama, Poster, Tanggal, Lokasi, Harga, Deskripsi, Jumlah Kuota Awal).
3. Admin menekan tombol simpan.
4. Sistem memperbarui database dan langsung menampilkan event tersebut pada katalog publik.

## 5.6 Alur Cek & Validasi Tiket di Lokasi Acara (Admin)
1. Pengunjung datang ke pintu masuk dan memperlihatkan E-Ticket.
2. Admin/Panitia membuka menu Validasi Tiket pada halaman Admin.
3. Admin memasukkan/menginput Kode Tiket Unik milik pengunjung.
4. Pengecekan Keabsahan oleh Sistem (< 5 Detik):
- Jika Kode Tidak Ditemukan: Tampil status "Tiket Tidak Valid / Palsu".
- Jika Kode Ditemukan & Status 'Sudah Terpakai': Tampil peringatan "Tiket Sudah Pernah Digunakan".
- Jika Kode Ditemukan & Status 'Belum Terpakai': Tampil pesan "Tiket Valid", lalu sistem mengubah status tiket tersebut menjadi 'Terpakai' agar tidak bisa digunakan ulang.