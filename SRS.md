# Software Requirement System
## 1. Sistem Apa yang Akan Dibangun
Sistem yang dibangun adalah Website Event Ticketing Sederhana.

Sistem ini berfungsi untuk:
- Pembeli (User): Melihat daftar event, memesan tiket secara online, dan mendapatkan E-Ticket berisi kode unik.
- Panitia (Admin): Menginput data event, melihat sisa kuota tiket secara real-time, dan mengecek keabsahan kode tiket di lokasi acara.

## 2. Dengan Apa Sistem Ini Akan Dibangun
Sistem dibangun menggunakan teknologi dasar web:
- Frontend (Tampilan): HTML, CSS, JavaScript (menggunakan framework sederhana seperti Bootstrap/Tailwind).
- Backend (Logika Sistem): Laravel.
- Database (Penyimpanan Data): MySQL.
- Tools Pendukung: Visual Studio Code, XAMPP, dan Web Browser (Google Chrome).

## 3. Rancangan Alur Sistem & Alur Data
## A. Alur Sistem Per Fitur
1. Fitur Login & Register: Pengguna masuk atau mendaftar akun menggunakan email dan password.
2. Fitur Lihat & Pilih Event: Pembeli memilih event yang ingin dibeli dan melihat detail informasi serta sisa kuotanya.
3. Fitur Pemesanan & Simulasi Bayar:
- Pembeli mengisi jumlah tiket.
- Sistem mengecek kuota (jika habis, pesanan ditolak).
- Jika kuota ada, pembeli melakukan simulasi pembayaran.
4. Fitur E-Ticket: Setelah pembayaran berhasil, sistem secara otomatis mengurangi kuota dan membuat Kode Unik Tiket.
5. Fitur Kelola Event (Admin): Admin dapat menambah, mengubah, atau menghapus data event.
6. Fitur Validasi Tiket (Admin): Panitia memasukkan kode tiket pengunjung di lokasi acara. Sistem mengecek apakah kode cocok dan belum pernah digunakan.

## B. Alur Data (Data Flow)
1. Input: User memasukkan data pesanan  Sistem memproses data.
2. Proses: Sistem mengecek dan memperbarui data di Database MySQL (mengurangi kuota event).
3. Output: Sistem menghasilkan E-Ticket + Kode Unik ke layar User.
4. Validasi: Admin memasukkan Kode Unik  Sistem mencocokkan dengan Database  Status tiket berubah menjadi "Terpakai".

## 4. Input dan Output Sistem
Berikut adalah rincian input dan output untuk setiap fitur dalam sistem:
1. Registrasi / Login
- Input: Nama, Email, Password
- Output: Akses masuk ke sistem / Session akun
2. Katalog Event
- Input: Kata kunci pencarian / Filter event
- Output: Daftar gambar & informasi detail event
3. Pemesanan Tiket
- Input: Jumlah tiket & data diri pembeli
- Output: Konfirmasi pesanan & Total harga pembayaran
4. Pembayaran & E-Ticket
- Input: Pilihan metode bayar (Simulasi)
- Output: E-Ticket resmi + Kode Tiket Unik
5. Kelola Event (Admin)
- Input: Nama event, tanggal, lokasi, harga, jumlah kuota
- Output: Data event baru tampil di katalog website
6. Validasi Tiket (Admin)
- Input: Kode Tiket Unik pengunjung
- Output: Status Tiket (Valid, Tidak Valid, atau Sudah Terpakai)