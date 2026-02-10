
# TUGAS UAS 
# Nama : Farid Hidayatulloh Tambunan
# Nim  : 220320009


# Sistem Peminjaman Inventaris Sekolah Berbasis Web
Aplikasi ini adalah **sistem peminjaman inventaris sekolah berbasis web** yang dibangun menggunakan **Laravel** sebagai backend framework dan **Filament Admin Panel** sebagai antarmuka admin (petugas). Sistem ini dirancang agar **mudah digunakan**, **terstruktur**, dan **cocok untuk lingkungan sekolah**.

---

## 1. Gambaran Umum Sistem

Sistem ini digunakan untuk mengelola:

* Data inventaris sekolah
* Proses peminjaman barang
* Proses pengembalian barang
* Riwayat peminjaman

**Aktor utama:**

* **Petugas** (Admin)

> Catatan: Versi ini hanya fokus pada petugas (tidak ada login siswa/guru).

---

## 2. Teknologi yang Digunakan

* **Laravel 10+** – Backend framework
* **Filament** – Admin panel (CRUD otomatis & rapi)
* **MySQL** – Database
* **PHP 8.1+**
* **Composer & Node.js**

---

## 3. Arsitektur Sistem

Alur kerja sistem secara sederhana:

1. Petugas membuka browser
2. Petugas login ke sistem Filament
3. Filament mengakses Controller & Model Laravel
4. Laravel berkomunikasi dengan Database MySQL
5. Data ditampilkan kembali ke petugas

**Arsitektur:**

Petugas → Browser → Filament Admin → Laravel → Database MySQL

---

## 4. Fitur Utama Sistem

### 4.1 Login Petugas

* Autentikasi menggunakan sistem login Laravel + Filament

### 4.2 Manajemen Data Inventaris

* Tambah barang
* Edit barang
* Hapus barang
* Lihat stok barang

### 4.3 Peminjaman Barang

* Input data peminjaman
* Pilih barang
* Tentukan jumlah
* Sistem otomatis mengurangi stok

### 4.4 Pengembalian Barang

* Input pengembalian
* Update status peminjaman
* Stok barang otomatis bertambah

### 4.5 Riwayat Peminjaman

* Melihat daftar peminjaman
* Filter berdasarkan tanggal & status

---

## 5. Struktur Folder Penting

```
app/
 ├── Models/
 │    ├── User.php
 │    ├── Barang.php
 │    ├── Peminjaman.php
 │    └── Pengembalian.php
 │
 ├── Filament/
 │    └── Resources/
 │         ├── BarangResource.php
 │         ├── PeminjamanResource.php
 │         └── PengembalianResource.php

database/
 ├── migrations/
 └── seeders/

routes/
 └── web.php
```

---

## 6. Desain Database (Sederhana)

### Tabel `users`

* id
* name
* email
* password
* role (petugas)

### Tabel `barangs`

* id
* nama_barang
* jumlah
* kondisi

### Tabel `peminjamans`

* id
* user_id
* barang_id
* jumlah_pinjam
* tanggal_pinjam
* status

### Tabel `pengembalians`

* id
* peminjaman_id
* tanggal_kembali
* kondisi_barang

---

## 7. Alur Sistem Peminjaman

1. Petugas login
2. Petugas memilih menu **Peminjaman**
3. Petugas mengisi form peminjaman
4. Sistem menyimpan data
5. Data muncul di riwayat peminjaman

---

## 8. Sequence Diagram (Penjelasan)

**Petugas → Sistem:**

* Login
* Input peminjaman
* Sistem validasi data
* Sistem simpan ke database
* Sistem tampilkan hasil

---

## 9. Class Diagram (Penjelasan)

* **User**
* **Barang**
* **Peminjaman**
* **Pengembalian**

Relasi:

* User memiliki banyak Peminjaman
* Barang memiliki banyak Peminjaman
* Peminjaman memiliki satu Pengembalian

---

## 10. Cara Menjalankan Project

### 10.1 Clone Repository

```
git clone https://github.com/username/inventaris-sekolah.git
cd inventaris-sekolah
```

### 10.2 Install Dependency

```
composer install
npm install
npm run build
```

### 10.3 Konfigurasi Environment

```
cp .env.example .env
php artisan key:generate
```

Atur database di file `.env`

### 10.4 Migrasi Database

```
php artisan migrate
```

### 10.5 Buat User Petugas

```
php artisan make:filament-user
```

### 10.6 Jalankan Server

```
php artisan serve
```

Akses:

```
http://localhost:8000/admin
```

---

## 11. Penutup

Sistem ini dibuat untuk membantu sekolah dalam mengelola inventaris secara **efisien, terstruktur, dan aman**. Dengan Laravel dan Filament, pengelolaan data menjadi lebih cepat dan mudah dipahami bahkan oleh pengguna awam.

---
