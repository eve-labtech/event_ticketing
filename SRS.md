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
A. Alur Sistem Per Fitur
1. Fitur Login & Register: Pengguna masuk atau mendaftar akun menggunakan email dan password.
2. Fitur Lihat & Pilih Event: Pembeli memilih event yang ingin dibeli dan melihat detail informasi serta sisa kuotanya.
3. Fitur Pemesanan & Simulasi Bayar:
- Pembeli mengisi jumlah tiket.
- Sistem mengecek kuota (jika habis, pesanan ditolak).
- Jika kuota ada, pembeli melakukan simulasi pembayaran.
4. Fitur E-Ticket: Setelah pembayaran berhasil, sistem secara otomatis mengurangi kuota dan membuat Kode Unik Tiket.
5. Fitur Kelola Event (Admin): Admin dapat menambah, mengubah, atau menghapus data event.
6. Fitur Validasi Tiket (Admin): Panitia memasukkan kode tiket pengunjung di lokasi acara. Sistem mengecek apakah kode cocok dan belum pernah digunakan.