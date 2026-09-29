# Business Requirements Management (BRD)
# Event Ticketing - Website pemesanan Tiket

## Latar belakang masalah
Banyak penyelenggara event skala kecil hingga menengah masih menggunakan sistem penjualan tiket manual. Hal ini menimbulkan beberapa masalah utama:  
1. Human Error: Pencatatan data pembeli rawan salah, hilang, atau tidak terorganisir.   
2. Kuota Tidak Akurat: Sisa tiket tidak terbarui secara real-time, berisiko terjadi pemesanan ganda (double booking).   
3. Validasi Lambat: Pengecekan tiket di lokasi butuh waktu lama dan memicu antrean panjang.   
4. Informasi Minim: Calon pembeli sulit mendapatkan detail acara yang resmi dan terpusat.  

Oleh karena itu, dibutuhkan website ticketing terintegrasi untuk mempermudah transaksi, memantau kuota secara otomatis, dan mempercepat validasi tiket.

# Alur yang ada saat ini
Berikut adalah gambaran alur kerja operasional yang masih berjalan secara manual di lapangan saat ini:
## 2.1 Alur pemesanan tiket
1. Pencarian Informasi: Calon pembeli mencari informasi event melalui media sosial atau pesan singkat tanpa adanya landing page resmi.
2. Pemesanan: Calon pembeli menghubungi panitia melalui obrolan langsung (chat) atau datang ke lokasi penjualan offline.
3. Pengecekan Kuota Manual: Panitia memeriksa sisa tiket secara manual di buku catatan atau lembar kerja (spreadsheet).
4. Pembayaran & Konfirmasi: Pembeli melakukan pembayaran (transfer/tunai), lalu mengirimkan bukti transfer secara manual ke panitia.
5. Pencatatan Data: Panitia mencatat nama dan kontak pembeli satu per satu ke dalam file rekapitulasi.
6. Penyerahan Tiket: Panitia menyerahkan bukti fisik berupa nota, kuitansi, atau file flyer melalui obrolan digital.

## 2.2 Alur validasi tiket dilokasi acara (Manual)
1. Kedatangan Pengunjung: Pengunjung datang ke lokasi event dan menunjukkan bukti bayar/nota fisik kepada panitia di pintu masuk.
2. Pengecekan Manual: Panitia mencari nama pengunjung di dalam lembaran daftar hadir cetak atau tabel spreadsheet.
3. Verifikasi Status: Panitia memberi tanda centang/mencoret nama pengunjung yang sudah masuk.
4. Kendala: Proses memakan waktu lama per orang, menyebabkan antrean mengular, dan rentan terhadap pemalsuan tiket fisik.

## 2.3 Alur pengelolaan event & rekapitulasi (Manual)
1. Update Kuota: Panitia harus terus mencocokkan jumlah uang masuk dengan jumlah lembar cetak tiket secara manual.
2. Pelaporan: Rekapitulasi penjualan baru bisa dihitung di akhir hari, sehingga pemantauan penjualan tidak bersifat real-time.

# Alur Yang Diinginkan (To-Be Process):
Sistem berbasis web yang dikembangkan akan mengotomatisasi dan menyederhanakan seluruh alur kerja menjadi lebih efisien.
## 3.1 Alur Pemesanan Tiket Online (Pembeli / User)
1. Membuka Website & Autentikasi: User mengakses website, melakukan Login atau Register akun.
2. Eksplorasi Event: User melihat daftar event yang tersedia pada Dashboard atau halaman Daftar Event, lalu memilih event yang diinginkan untuk melihat detail (nama, tanggal, lokasi, harga, deskripsi).
3. Pengisian Form Pembelian: User menekan tombol "Beli", memilih jumlah tiket, dan mengisi data diri.
4. Pengecekan Otomatis Kuota Sistem:
- Jika Kuota Habis: Sistem langsung menolak transaksi dan menampilkan notifikasi "Tiket Habis".
- Jika Kuota Masih Ada: Sistem melanjutkan proses ke tahap pembayaran.
5. Pembayaran (Simulasi): User memilih metode pembayaran (Transfer Bank / E-Wallet) dan menyelesaikan proses pembayaran.
6. Generate Kode Unik & E-Ticket: Sistem secara otomatis menghasilkan (generate) Kode Tiket Unik berupa kombinasi acak huruf dan angka.
7. Penyimpanan Data & Penerbitan Tiket: Sistem menyimpan data pemesanan, mengurangi kuota event secara otomatis, dan menampilkan E-Ticket yang memuat kode unik untuk diunduh/disimpan oleh pembeli.

## 3.2 Alur Validasi Tiket di Lokasi Acara (Panitia / Admin)
1. Pemeriksaan E-Ticket: Pengunjung menunjukkan E-Ticket (kode unik) di lokasi acara.
2. Input/Pengecekan Kode: Panitia membuka menu Cek & Validasi Tiket pada halaman Admin.
3. Verifikasi Sistem: Sistem memeriksa keabsahan kode tiket dan memastikan tiket tersebut belum pernah digunakan sebelumnya (target proses validasi < 5 detik).
4. Pembaruan Status: Jika valid, sistem memperbarui status tiket menjadi "Terpakai" (used) secara otomatis untuk mencegah penggunaan berulang.
3.3 Alur Pengelolaan Event & Pemantauan (Panitia / Admin)
1. Manajemen Event: Admin melakukan Login ke Dashboard Admin untuk menambah event baru, mengedit deskripsi, serta menentukan jumlah alokasi kuota tiket.
2. Monitoring Real-Time: Admin dapat memantau pergerakan kuota tiket, rekapitulasi data penjualan, dan status transaksi secara real-time melalui dashboard tanpa perhitungan manual.