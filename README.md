# Proyek Nginx dengan Rute /v1 dan /v2

Proyek ini mendemonstrasikan cara menjalankan server Nginx dengan konfigurasi rute khusus, yaitu `/v1` dan `/v2`, menggunakan Docker Compose.

## Struktur Direktori

```sh
.
├── docker-compose.yml
├── nginx/
│   └── nginx.conf
└── html/
    ├── v1/
    │   └── index.html
    └── v2/
        └── index.html
```

* `docker-compose.yml`: File konfigurasi Docker Compose untuk menjalankan kontainer Nginx.
* `nginx/nginx.conf`: Konfigurasi Nginx yang menentukan rute `/v1` dan `/v2`.
* `html/v1/index.html`: File HTML untuk rute `/v1`.
* `html/v2/index.html`: File HTML untuk rute `/v2`.

## Prasyarat

* Docker dan Docker Compose terpasang di sistem Anda.

## Cara Menjalankan

1.  Buka terminal dan arahkan ke direktori proyek `my-nginx`.
2.  Jalankan perintah berikut untuk memulai kontainer:

    ```bash
    docker-compose up -d
    ```

    Opsi `-d` menjalankan kontainer di latar belakang (detached mode).

3.  Buka browser dan akses URL berikut:

    * `http://localhost:81/v1/index.html`
    * `http://localhost:81/v2/index.html`

    Anda akan melihat halaman HTML yang berbeda untuk setiap rute.

## Penjelasan

* **`docker-compose.yml`**:
    * Mendefinisikan layanan `web` yang menggunakan image Nginx terbaru.
    * Memetakan port 80 di host ke port 80 di kontainer.
    * Memasang volume untuk mengganti konfigurasi Nginx default dan menyediakan konten HTML kustom.
* **`nginx/nginx.conf`**:
    * Mengkonfigurasi server Nginx untuk mendengarkan di port 80.
    * Menentukan rute `/v1/` dan `/v2/` menggunakan direktif `location`.
    * Menggunakan direktif `alias` untuk memetakan rute ke direktori HTML yang sesuai.
    * Menggunakan direktif `index` untuk menentukan file `index.html` sebagai file indeks.
* **`html/v1/index.html` dan `html/v2/index.html`**:
    * File HTML sederhana yang ditampilkan ketika rute masing-masing diakses.

## Cara Menghentikan

Untuk menghentikan kontainer, jalankan perintah berikut di direktori proyek:

```bash
docker-compose down
```