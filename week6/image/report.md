# Laporan Jobsheet 6 Minggu ke-6

#### Nama  : Muhammad Daviq Naufal Haqqul Adam
#### NIM   : 254107020010
#### Kelas : TI-1H



## Latihan 6.A: Eksplorasi Proses Sistem

### 1. Proses dengan PID 1
![Hasil tugas 1](image/1.JPG.)
* **Perintah:**
    ```bash
    ps aux --forest | grep "^root          1 "
    ```
* **Nama Proses:** `systemd` (atau `init` pada sistem lama).
* **Fungsi:** Merupakan proses pertama yang dijalankan oleh kernel saat booting. Ia berfungsi sebagai *parent* (induk) dari semua proses lainnya di sistem Linux modern dan bertugas mengelola layanan (*services*) sistem.


### 2. Perbandingan Jumlah Proses Root dan User
* **Menghitung Proses Root:**
    ```bash
    ps aux | grep "^root" | count
    ```
* **Menghitung Proses User:**
    ```bash
    ps aux | grep "^$(whoami)" | count
    ```
* **Analisis:** User `root` memiliki lebih banyak proses karena bertanggung jawab menjalankan layanan sistem (*daemons*), manajemen memori, *driver* perangkat, dan tugas-tugas administratif di balik layar agar sistem operasi tetap stabil.

### 3. Proses dalam Kondisi S (Sleeping)
* **Perintah:**
    ```bash
    ps aux | awk '$8 ~ /S/'
    ```
* **Analisis:** Mayoritas proses berada dalam kondisi *Sleeping* (S) karena mereka tidak sedang membutuhkan CPU secara aktif. Mereka menunggu *event* atau interupsi tertentu (seperti input dari pengguna atau data dari jaringan) sebelum kembali aktif, guna menghemat daya dan sumber daya sistem.


