# Tugas Besar Komputasi Awan - Kasir El-Maknyuso
## Deskripsi Singkat
Aplikasi El-Maknyuso adalah sistem kasir retail berbasis web yang dapat merekam transaksi pelanggan, menghitung total pesanan, dan menampilkan riwayat secara *real-time*.

## Arsitektur Sistem 3 Virtual Machine
Proyek ini mengimplementasikan konsep *Infrastructure as Code* (IaC) menggunakan Vagrant & Ansible dengan pembagian:
1. **VM Database (192.168.56.21):** Server MySQL. Bertugas menyimpan persisten data transaksi tabel `pesanan`.
2. **VM Backend (192.168.56.20):** Server Aplikasi API menggunakan Python Flask. Bertugas menjembatani logika penyimpanan dari antarmuka pengguna menuju database.
3. **VM Frontend (192.168.56.22):** Web Server menggunakan Nginx. Menyajikan halaman UI HTML/JS kepada user (Kasir).

## Tools & Teknologi
- **Virtualisasi:** VirtualBox, Vagrant
- **Konfigurasi:** Ansible Local Provisioner
- **Stack Aplikasi:** Nginx, HTML5, Bootstrap 5, JS Fetch API, Python3, Flask, MySQL

## Cara Instalasi
1. Clone repositori ini.
2. Buka terminal di folder direktori dan jalankan `vagrant up`.
3. Tunggu proses otomatisasi selesai.
4. Akses aplikasi melalui browser di `http://192.168.56.22`.