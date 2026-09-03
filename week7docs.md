# WEEK 7 Documentation
---

## a) Perbedaan antara Linux Kernel dan Distro
* **Linux Kernel:** Inti dari sistem operasi Linux yang bertugas mengatur komunikasi tingkat rendah antara perangkat keras (*hardware*) dan perangkat lunak (*software*).
* **Linux Distro:** Variasi atau paket lengkap sistem operasi Linux yang menyatukan kernel dengan tambahan perangkat lunak bawaan, pustaka, serta utilitas pendukung (Contoh: Ubuntu, Fedora).

---

## b) Linux FHS (Filesystem Hierarchy Standard) beserta Penjelasan & Contoh Kegunaannya
*Filesystem Hierarchy Standard* (FHS) adalah panduan standar untuk menentukan struktur direktori dan isi file pada sistem operasi Linux:
* **`/` (Root):** Fondasi tertinggi dari seluruh struktur file Linux tempat semua direktori berada. Hanya *root user* yang memiliki izin untuk memodifikasi isinya.
* **`/bin`:** Berisi perintah esensial dan *binary* yang dibutuhkan oleh semua pengguna, termasuk perintah seperti `cp`, `ls`, `ssh`, dan `kill`.
* **`/boot`:** Menyimpan semua file yang diperlukan untuk proses *booting* (menyalakan sistem), termasuk konfigurasi bootloader GRUB dan file *kernel* esensial.
* **`/dev`:** Direktori khusus yang bertindak sebagai antarmuka penghubung antara perangkat keras dan perangkat lunak. 
  * *Contoh:* `/dev/null` sebagai tempat sampah digital untuk membuang *output* yang tidak diperlukan.
* **`/etc`:** Singkatan dari *Editable Text Configuration*, berisi file-file konfigurasi sistem berbasis teks. 
  * *Contoh penggunaan:* `/etc/hostname`.
* **`/home`:** Direktori personal yang disediakan di dalam `/home` untuk setiap *non-root user*. 
  * *Contoh:* `/home/username`.
* **`/lib`:** Menyimpan pustaka bersama (*shared libraries*) dan pustaka dinamis yang dibutuhkan aplikasi selama program berjalan (*runtime*, misal pustaka untuk server Apache).
* **`/media`:** Tempat *mounting* otomatis untuk perangkat media lepas pasang (*removable media*) seperti USB atau *external HDD*.
* **`/mnt`:** Direktori penyimpanan untuk *mounting storage* secara sementara atau manual.
* **`/opt`:** Tempat menyimpan perangkat lunak pihak ketiga (*third-party software*) dan paket di luar instalasi bawaan sistem.
* **`/sbin`:** Berisi perintah *binary* sistem yang umumnya hanya boleh dijalankan oleh administrator *root* untuk keperluan pemeliharaan dan perbaikan.
* **`/var`:** Tempat menyimpan file yang ukurannya terus berubah secara dinamis saat sistem beroperasi. 
  * *Contoh:* Direktori web `/var/www/html`.
* **`/tmp`:** Menyimpan file sementara yang dibuat oleh program berjalan dan akan terhapus otomatis saat komputer dimatikan atau *restart*.
* **`/usr`:** Singkatan dari *User System Resources*, direktori terbesar kedua yang berisi aplikasi, pustaka, dan dokumentasi yang dibagikan antar pengguna (misal file eksekusi di `/usr/bin`).

---

## c) Sistem Permission dan Owner pada Linux
* **System Permission (Hak Akses):**
  * **Read (`r`):** Hak untuk membaca file atau melihat isi direktori.
  * **Write (`w`):** Hak untuk mengedit file atau menambah/menghapus isi direktori.
  * **Execute (`x`):** Hak untuk mengeksekusi file (seperti skrip atau program) dan mengakses direktori.
* **Ownership (Kepemilikan):**
  * **User:** Pengguna yang membuat file atau direktori dan secara default menjadi pemilik utamanya.
  * **Group:** Sekelompok pengguna yang berbagi hak akses terhadap file atau direktori.
  * **Others:** Semua pengguna lain di luar pemilik utama (*user*) dan kelompok (*group*).

---

## d) Perbedaan antara Bash, Sh, dan Jenis-Jenis Shell Lain
* **Sh (Bourne Shell):** Shell standar yang sangat ringan, portabel, dan biasa digunakan pada sistem operasi *Unix-like*.
* **Bash (Bourne Again Shell):** Shell standar (*default*) di hampir semua distribusi Linux; modifikasi dari *sh* dengan tambahan fitur seperti *tab completion* dan riwayat perintah.
* **Zsh (Z-Shell):** Shell interaktif modern yang populer, menjadi *default* di macOS dan beberapa distro Linux seperti Manjaro.
* **Fish (Friendly Interactive Shell):** Shell interaktif modern yang ramah pemula dengan fitur saran otomatis (*autosuggestions*) instan saat mengetik.

| Fitur / Karakteristik | Sh (Bourne) | Bash | Zsh | Fish |
| :--- | :--- | :--- | :--- | :--- |
| **Status Default** | Jarang (Sistem Lama) | Mayoritas Linux | macOS / Manjaro | Harus Install Manual |
| **Kemudahan Pemula** | Sangat Rendah | Tinggi | Tinggi | Sangat Tinggi |
| **Kustomisasi Tema** | Tidak Bisa | Terbatas | Sangat Luas (Oh My Zsh) | Mudah (Bawaan) |
| **Saran Otomatis** | Tidak Ada | Standar (Tab) | Cerdas (Tab/Plugin) | Instan (Saat Mengetik) |
| **Kesesuaian Skrip** | Standar POSIX | Standar Industri | Kompatibel Bash | Berbeda (Sintaks Sendiri) |

---

## e) Prinsip Enkripsi pada SSH
SSH (*Secure Shell*) adalah program dan protokol untuk mengoperasikan komputer melalui jaringan dengan menerapkan dua prinsip utama:
* **Encrypted Communication (Komunikasi Menggunakan Enkripsi):** Seluruh data yang dikirimkan antara klien dan server (perintah terminal, *password*, dan data sistem) dienkripsi sehingga aman dan tidak dapat dibaca meskipun lalu lintas jaringan disadap .
* **Public-Key Exchange (Pertukaran Kunci Publik):** Mekanisme pertukaran kunci kriptografi antara server dan klien untuk mengamankan koneksi, melibatkan komponen seperti `known_hosts` dan `authorized_keys` guna memastikan klien terhubung ke server yang sah .

---

## f) Perbedaan antara HTTP dan HTTPS
* **HTTP (Hypertext Transfer Protocol):** Protokol komunikasi web standar yang mengirimkan data dalam bentuk teks biasa (*plaintext*) sehingga tidak memiliki enkripsi dan rentan disadap (berjalan di port 80).
* **HTTPS (Hypertext Transfer Protocol Secure):** Versi aman dari HTTP yang menggunakan lapisan tambahan SSL/TLS (*Secure Sockets Layer / Transport Layer Security*) untuk mengenkripsi pertukaran data secara menyeluruh dari inspeksi publik .

---

## g) Docker OCI Compliance Standard
* Standar kepatuhan *Open Container Initiative* (OCI) memastikan bahwa format *image* di Docker mengikuti aturan standar terbuka agar dapat berjalan kompatibel di software kontainerisasi lain seperti Kubernetes, OpenShift, Podman, dan Rancher .

---

## h) Perbedaan antara Container dan VM
* **Definisi:** 
  * *Kontainer* adalah paket kode perangkat lunak berisi kode aplikasi, pustaka, dan dependensi untuk menjalankan lingkungan aplikasi .
  * *Mesin Virtual (VM)* adalah replika digital mesin fisik yang mempartisi perangkat keras fisik ke dalam beberapa lingkungan .
* **Virtualisasi & Enkapsulasi:** Kontainer memvirtualisasikan sistem operasi di atasnya, sedangkan VM memvirtualisasikan infrastruktur fisik beserta sistem operasi penuh via *hypervisor* .
* **Ukuran:** Kontainer jauh lebih ringan (dalam skala MB), sedangkan VM berukuran lebih besar (dalam skala GB) .
* **Fleksibilitas & Skalabilitas:** Kontainer sangat fleksibel untuk dimigrasikan dan mudah diskalakan melalui layanan mikro; sementara VM memiliki tantangan migrasi dan biaya penskalaan yang lebih tinggi .

---

## i) Definisi dan Manfaat dari Image Layer pada Docker
* **Definisi:** Lapisan-lapisan filesystem terpisah yang ditumpuk bersama secara virtual untuk membuat sebuah *docker image* yang utuh .
* **Karakteristik & Manfaat:**
  * Setiap layer bersifat *read-only* (tidak dapat diubah setelah dibuat) .
  * Berbasis instruksi di mana setiap baris perintah di dalam `Dockerfile` menghasilkan satu layer baru .
  * *Ilustrasi Penumpukan:*
    ```text
    ┌──────────────────────────────────────────────────────────┐
    │ Layer 4: WORKDIR & CMD (Konfigurasi & perintah jalankan) │
    ├──────────────────────────────────────────────────────────┤
    │ Layer 3: COPY . /app (File aplikasi dari komputer Anda)  │
    ├──────────────────────────────────────────────────────────┤
    │ Layer 2: RUN apk add... (Instalasi Node.js & NPM)        │
    ├──────────────────────────────────────────────────────────┤
    │ Layer 1: FROM alpine:3.18 (Sistem operasi dasar / Base)  │
    └──────────────────────────────────────────────────────────┘
    ```

---

## j) Kegunaan dari Penggunaan Docker Volume dan Network beserta Contohnya
* **1. Docker Volume:**
  * *Kegunaan:* Menyimpan data secara permanen (*persistent*) di luar siklus hidup kontainer yang bersifat sementara (*ephemeral*). Berguna untuk menyimpan data database (MySQL/PostgreSQL) agar tidak terhapus saat kontainer di-restart, serta mempermudah *sharing* data dan *backup* .
  * *Contoh Penggunaan:*
    ```bash
    # Membuat volume baru
    docker volume create my_db_data

    # Menjalankan kontainer MySQL dengan volume tersebut
    docker run -d --name my-mysql -v my_db_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=secret mysql
    ```
* **2. Docker Network:**
  * *Kegunaan:* Menghubungkan dan mengisolasi komunikasi antar kontainer atau dengan jaringan luar. Memungkinkan kontainer saling berkomunikasi menggunakan nama kontainer sebagai *hostname* tanpa bergantung pada IP dinamis, serta meningkatkan keamanan .
  * *Contoh Penggunaan:*
    ```bash
    # Membuat network baru
    docker network create app-net

    # Menjalankan database di dalam network tersebut
    docker run -d --name mydb --network app-net -e MYSQL_ROOT_PASSWORD=secret mysql

    # Menjalankan aplikasi web di network yang sama agar bisa mengakses 'mydb'
    docker run -d --name myweb --network app-net -p 8080:80 my-web-app
    ```

---

## k) Definisi dan Tujuan dari Penggunaan Web Server dan Reverse Proxy
* **1. Web Server:**
  * *Definisi:* Sistem yang melayani permintaan dari pengguna melalui protokol HTTP atau HTTPS, bertugas mengambil file website (HTML, gambar, video) dan mengirimkannya ke perangkat pengguna (Contoh: Nginx, Apache, Microsoft IIS) .
  * *Tujuan:* Menyediakan konten statis/dinamis, menampung file web, serta mengatur otorisasi akses direktori dasar .
* **2. Reverse Proxy:**
  * *Definisi:* Server perantara yang berada di sisi server, di mana klien tidak pernah berkomunikasi langsung dengan server utama melainkan melalui *reverse proxy* ini terlebih dahulu .
  * *Tujuan:* Keamanan server (menyembunyikan IP asli), *load balancing* pembagian beban lalu lintas, *caching* konten agar akses lebih cepat, serta pengelolaan *SSL Termination* enkripsi HTTPS .
