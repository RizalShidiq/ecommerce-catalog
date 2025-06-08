# Proyek Katalog E-Commerce

Proyek ini adalah aplikasi web katalog e-commerce yang dibangun menggunakan framework Laravel dan Vue.js. Aplikasi ini menampilkan daftar produk yang dapat di-filter berdasarkan kategori, memungkinkan pengguna untuk melakukan pencarian produk, dan menyediakan halaman detail untuk setiap produk.

## 🌟 Fitur Utama

  - **Tampilan Produk**: Menampilkan produk dalam format *grid* yang responsif.
  - **Pencarian Produk**: Fungsi pencarian *real-time* untuk menemukan produk berdasarkan nama.
  - **Filter Kategori**: Memfilter produk berdasarkan kategori yang tersedia.
  - **Halaman Detail Produk**: Halaman khusus untuk setiap produk yang menampilkan gambar, deskripsi, harga, dan informasi lainnya.
  - **Keranjang Belanja**: Fungsionalitas untuk menambah produk ke keranjang belanja.
  - **Desain Responsif**: Tampilan yang dapat beradaptasi dengan baik di perangkat desktop maupun mobile.

## 💻 Teknologi yang Digunakan

Proyek ini dibangun dengan *tech stack* berikut:

  - **Backend**: Laravel
  - **Frontend**: Vue.js
  - **Styling**: Tailwind CSS
  - **Server**: PHP
  - **Database**: Menggunakan sistem database yang kompatibel dengan Laravel (misalnya MySQL, PostgreSQL).
  - **Manajemen Dependensi**: Composer (untuk PHP) dan NPM (untuk JavaScript).

## 🚀 Instalasi dan Setup

Ikuti langkah-langkah berikut untuk menjalankan proyek ini di lingkungan lokal Anda.

### Prasyarat

  - PHP \>= 8.0
  - Composer
  - Node.js & NPM
  - Database (misalnya, MySQL)

### Langkah-langkah Instalasi

1.  **Clone Repositori**
    Clone repositori ini ke mesin lokal Anda:

    ```bash
    git clone https://github.com/RizalShidiq/ecommerce-catalog.git
    ```

2.  **Masuk ke Direktori Proyek**

    ```bash
    cd ecommerce-catalog/ecommerce
    ```

3.  **Instal Dependensi PHP**
    Instal semua *package* yang dibutuhkan oleh Laravel menggunakan Composer:

    ```bash
    composer install
    ```

4.  **Instal Dependensi JavaScript**
    Instal semua *package* yang dibutuhkan oleh Vue.js menggunakan NPM:

    ```bash
    npm install
    ```

5.  **Konfigurasi Lingkungan**
    Salin file `.env.example` menjadi `.env`:

    ```bash
    cp .env.example .env
    ```

    Buat kunci aplikasi baru:

    ```bash
    php artisan key:generate
    ```

6.  **Konfigurasi Database**
    Buka file `.env` dan atur koneksi database Anda (nama database, username, password):

    ```env
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=nama_database_anda
    DB_USERNAME=user_database_anda
    DB_PASSWORD=password_database_anda
    ```

7.  **Jalankan Migrasi Database**
    Jalankan migrasi untuk membuat tabel-tabel yang diperlukan di database Anda. Gunakan *seeder* untuk mengisi data awal (produk dan kategori).

    ```bash
    php artisan migrate --seed
    ```

8.  **Compile Aset Frontend**
    Compile file-file JavaScript dan CSS:

    ```bash
    npm run dev
    ```

    Atau untuk produksi:

    ```bash
    npm run build
    ```

9.  **Jalankan Server Development**
    Jalankan server pengembangan Laravel:

    ```bash
    php artisan serve
    ```

    Aplikasi Anda sekarang akan berjalan di `http://127.0.0.1:8000`.

## Struktur Proyek

Berikut adalah gambaran singkat tentang struktur direktori utama:

```
ecommerce/
├── app/                # Logika utama aplikasi (Models, Controllers)
├── config/             # File-file konfigurasi Laravel
├── database/           # Migrations, Seeders, Factories
├── public/             # Aset publik (CSS, JS, images)
├── resources/
│   ├── js/             # Komponen-komponen Vue.js
│   ├── views/          # Blade templates
│   └── css/            # File CSS
├── routes/             # Definisi rute (web.php, api.php)
└── ...
```

## Kontributor

  * **Rizal Shidiq** - [RizalShidiq](https://www.google.com/search?q=https://github.com/RizalShidiq)
