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

# SESI 3 - MODEL DAN TAMPIL DATA MAHASISWA

## Tujuan
Membuat model Mahasiswa, menambahkan data dummy, dan menampilkan data mahasiswa ke dalam tabel.

---

## Langkah Pengerjaan

### 1. Membuat Model Mahasiswa
Membuat file:

```bash
app/models/Mahasiswa.php
```

Model digunakan untuk mengambil data mahasiswa dari database menggunakan PDO.

Method yang dibuat:

```php
getAll()
```

Method ini menjalankan query:

```sql
SELECT * FROM mahasiswa ORDER BY id DESC
```

---

### 2. Menambahkan Data Dummy
Menambahkan minimal 5 data mahasiswa ke database menggunakan SQL.

Data berisi:
- NPM
- Nama Lengkap
- Fakultas
- Jurusan
- Tempat Lahir
- Tanggal Lahir
- Jenis Kelamin

---

### 3. Membuat MahasiswaController
Membuat file:

```bash
app/controllers/MahasiswaController.php
```

Method:

```php
index()
```

Method ini digunakan untuk:
- memanggil model Mahasiswa
- mengambil seluruh data mahasiswa
- mengirim data ke view

---

### 4. Membuat View Mahasiswa
Membuat file:

```bash
app/views/mahasiswa/index.php
```

Data mahasiswa ditampilkan dalam bentuk tabel HTML.

Kolom tabel:
- No
- NPM
- Nama Lengkap
- Fakultas
- Jurusan
- Tempat Lahir
- Tanggal Lahir
- Jenis Kelamin
- Status

---

## Hasil Sesi 3

- Model Mahasiswa berhasil dibuat
- Data dummy berhasil ditambahkan
- Data mahasiswa berhasil ditampilkan
- Tabel mahasiswa tampil di browser

---

# Screenshot

## Tabel Data Mahasiswa

![Mahasiswa](docs/sesi3_model_dan_tampil_data.jpeg)

---

# URL Testing

```bash
http://localhost/mvc_mahasiswa_kelompok7/public/mahasiswa
```

---

# Commit GitHub

```bash
git add .
git commit -m "Sesi 3 - model dan tampil data"
git push origin main
```
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

![Home](docs/home.jpeg)

---

# Commit GitHub

```bash
git add .
git commit -m "Sesi 2 - routing dan base controller"
git push origin main
```

# SESI 4 - TAMBAH DATA MAHASISWA (CREATE)

## Tujuan
Membuat fitur tambah data mahasiswa menggunakan konsep MVC.

---

## Langkah Pengerjaan

### 1. Membuat Method create()
Menambahkan method `create()` pada file:

```bash
app/controllers/MahasiswaController.php
```

Method ini digunakan untuk menampilkan form tambah mahasiswa.

---

### 2. Membuat Method store()
Menambahkan method `store()` untuk:
- menerima data dari form
- validasi input
- menyimpan data ke database
- menampilkan flash message

---

### 3. Membuat Method create() pada Model
Menambahkan method:

```php
create($data)
```

pada file:

```bash
app/models/Mahasiswa.php
```

Method ini digunakan untuk menyimpan data mahasiswa menggunakan PDO.

---

### 4. Membuat Form Tambah Mahasiswa
Membuat file:

```bash
app/views/mahasiswa/create.php
```

Form berisi:
- npm
- nama lengkap
- fakultas
- jurusan
- tempat lahir
- tanggal lahir
- jenis kelamin

---

### 5. Menambahkan Tombol Tambah Mahasiswa
Menambahkan tombol:

```text
Tambah Mahasiswa
```

pada halaman data mahasiswa.

---

# Hasil Sesi 4

- Form tambah mahasiswa berhasil dibuat
- Data berhasil disimpan ke database
- Validasi berhasil berjalan
- Data baru berhasil tampil pada tabel mahasiswa

---

# Screenshot

## Form Tambah Mahasiswa

![Create](docs/sesi4_tambah_data_mahasiswa.jpeg)

---

# URL Testing

```bash
http://localhost/mvc_mahasiswa_kelompok7/public/mahasiswa/create
```

---

# Commit GitHub

```bash
git add .
git commit -m "Sesi 4 - create mahasiswa"
git push origin main
```


# SESI 5 - EDIT DAN HAPUS DATA (UPDATE & DELETE)

## Tujuan
Menyelesaikan fitur CRUD dengan menambahkan edit dan hapus data mahasiswa.

---

## Langkah Pengerjaan

### 1. Membuat Method edit()
Menambahkan method:

```php
edit($id)
```

pada file:

```bash
app/controllers/MahasiswaController.php
```

Method ini digunakan untuk mengambil data mahasiswa berdasarkan id dan menampilkan form edit.

---

### 2. Membuat Method update()
Menambahkan method:

```php
update($id)
```

Method ini digunakan untuk:
- menerima data dari form edit
- validasi data
- memperbarui data mahasiswa di database

---

### 3. Membuat Method delete()
Menambahkan method:

```php
delete($id)
```

Method ini digunakan untuk menghapus data mahasiswa dari database.

---

### 4. Menambahkan Method pada Model
Menambahkan method:
- `find($id)`
- `update($id, $data)`
- `delete($id)`

pada file:

```bash
app/models/Mahasiswa.php
```

Method digunakan untuk mengambil, memperbarui, dan menghapus data mahasiswa menggunakan PDO.

---

### 5. Membuat View Edit
Membuat file:

```bash
app/views/mahasiswa/edit.php
```

Form edit berisi data lama yang dapat diperbarui.

---

### 6. Menambahkan Tombol Aksi
Menambahkan tombol:
- Edit
- Hapus

pada tabel data mahasiswa.

---

# Hasil Sesi 5

- Edit data mahasiswa berhasil berjalan
- Hapus data mahasiswa berhasil berjalan
- Data berhasil diperbarui
- Data berhasil dihapus dari database

---

# Screenshot

## Update Data Mahasiswa

![Update](docs/sesi5_update.jpeg)

---

# Commit GitHub

```bash
git add .
git commit -m "Sesi 5 - update dan delete mahasiswa"
git push origin main
```

# SESI 6 - PENCARIAN DAN FILTER DATA

## Tujuan
Menambahkan fitur pencarian dan filter data mahasiswa berdasarkan nama, NPM, dan jurusan.

---

## Langkah Pengerjaan

### 1. Modifikasi Method index()
Memodifikasi method:

```php
index()
```

pada file:

```bash
app/controllers/MahasiswaController.php
```

Method digunakan untuk menerima parameter:
- search
- jurusan

menggunakan metode GET.

---

### 2. Membuat Method searchAndFilter()
Menambahkan method:

```php
searchAndFilter($search, $jurusan)
```

pada file:

```bash
app/models/Mahasiswa.php
```

Method digunakan untuk:
- mencari data berdasarkan nama atau NPM
- memfilter data berdasarkan jurusan
- menjalankan query dinamis menggunakan PDO

---

### 3. Membuat Form Pencarian
Menambahkan form pencarian pada halaman mahasiswa.

Form berisi:
- input pencarian
- dropdown jurusan
- tombol cari
- tombol reset

---

### 4. Menampilkan Hasil Filter
Data mahasiswa akan berubah sesuai:
- kata kunci pencarian
- jurusan yang dipilih

---

# Hasil Sesi 6

- Fitur pencarian berhasil berjalan
- Filter jurusan berhasil berjalan
- Data tabel berubah sesuai pencarian
- Tombol reset berhasil mengembalikan data awal

---

# Screenshot

## Pencarian dan Filter Data

![Pencarian](docs/sesi6_pencarian.jpeg)

---

# Commit GitHub

```bash
git add .
git commit -m "Sesi 6 - pencarian dan filter data"
git push origin main
```
