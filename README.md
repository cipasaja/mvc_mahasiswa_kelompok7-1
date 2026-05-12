# SESI 1 - PERSIAPAN PROYEK

## Tujuan
Memahami konsep dasar MVC dan menyiapkan struktur awal project PHP MVC.

---

# Struktur Folder

```bash
mvc_mahasiswa_kelompok7/
│
├── app/
│   ├── controllers/
│   ├── models/
│   ├── views/
│
├── config/
├── core/
├── public/
├── .htaccess
└── README.md
```

---

# Langkah Pengerjaan

## 1. Membuat Struktur Folder
Membuat folder MVC sesuai modul praktikum:
- controllers
- models
- views
- config
- core
- public

---

## 2. Membuat File .htaccess
Digunakan untuk URL rewriting agar routing berjalan dengan baik.

### Root .htaccess

```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ public/index.php?url=$1 [QSA,L]
```

### Public .htaccess

```apache
Options -MultiViews
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?url=$1 [QSA,L]
```

---

## 3. Membuat Koneksi Database

Database yang digunakan:

```sql
uniska_latihan_mvc_2026
```

Menggunakan PDO untuk koneksi database MySQL.

---

## 4. Membuat Tabel Mahasiswa

Tabel utama bernama:

```sql
mahasiswa
```

Berisi data:
- npm
- nama_lengkap
- fakultas
- jurusan
- tempat_lahir
- tanggal_lahir
- jenis_kelamin

---

## 5. Testing Database

Membuat file:

```bash
public/test_db.php
```

Untuk mengecek apakah koneksi database berhasil.

Hasil yang tampil di browser:

```text
Koneksi berhasil
```

---

# Hasil Sesi 1

- Struktur folder berhasil dibuat
- Database berhasil dibuat
- Koneksi database berhasil
- Project berhasil dijalankan di localhost

---

# Screenshot

## Struktur Folder VSCode

![Struktur Folder](docs/sesi1_folder.jpeg)

## Test Database

![Test Database](docs/sesi1_koneksi.jpeg)

---

# Commit GitHub

```bash
git add .
git commit -m "Sesi 1 - persiapan proyek"
git push origin main
```

# SESI 2 - ROUTING DAN BASE CONTROLLER

## Tujuan
Memahami cara kerja routing pada arsitektur MVC dan membuat Base Controller yang digunakan oleh seluruh controller.

---

## Langkah Pengerjaan

### 1. Membuat Router
Membuat file `core/Router.php` untuk membaca URL, menentukan controller, method, dan parameter.

Contoh URL:

```bash
http://localhost/mvc_mahasiswa_kelompok7/public/home/index
```

---

### 2. Membuat Base Controller
Membuat file `core/Controller.php` yang digunakan untuk memanggil view dan model.

---

### 3. Membuat Database Core
Membuat file `core/Database.php` untuk koneksi database menggunakan PDO.

---

### 4. Modifikasi index.php
File `public/index.php` digunakan sebagai front controller untuk menjalankan routing aplikasi.

---

### 5. Membuat HomeController
Membuat file `app/controllers/HomeController.php` dengan method:

```php
index()
```

Method ini digunakan untuk menampilkan halaman utama aplikasi.

---

### 6. Membuat View Home
Membuat file `app/views/home/index.php`.

Isi halaman:

```text
Selamat datang di Aplikasi MVC Mahasiswa. Kelompok kami siap belajar!
```

---

## Hasil Sesi 2

- Routing berhasil berjalan
- URL berhasil memanggil controller dan method
- Halaman home berhasil ditampilkan
- Tidak terjadi error 404

---

# Screenshot

## Halaman Home

![Home](docs/sesi2-home.jpeg)

---

# Commit GitHub

```bash
git add .
git commit -m "Sesi 2 - routing dan base controller"
git push origin main
```
