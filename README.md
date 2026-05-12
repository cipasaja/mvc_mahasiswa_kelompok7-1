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
