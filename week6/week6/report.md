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


### Latihan 6.B: Simulasi Manajemen Job

**1. Menjalankan Perintah di Background**
![Hasil tugas 2](image/2.JPG.)
Menjalankan tiga proses `sleep` dengan durasi berbeda di latar belakang dan melakukan verifikasi menggunakan perintah `jobs`.
```bash
sleep 120 &
jobs

**2. Manipulasi Foreground dan Background**
Membawa job nomor 2 ke depan (foreground), menghentikannya sementara, lalu mengirimnya kembali ke latar belakang.

Pindah ke Foreground: fg %2

Pindah ke Background: bg %2 (status kembali menjadi 'Running' di latar belakang).


### Latihan 6.C: Prioritas dan Sinyal (Implementasi)

**1. Verifikasi Nilai Nice Awal**
Berdasarkan hasil perintah `ps -l`, terlihat dua proses sleep berjalan dengan nilai NI (Nice) yang berbeda:
* PID 451021 memiliki NI 5.
* PID 451248 memiliki NI 10.

**2. Mengubah Prioritas dengan Renice**
Dilakukan pengubahan nilai nice pada proses pertama (PID 451021) menjadi +10:
```bash
renice +10 -p 451021


![Hasil tugas 2.2](image/2.2.JPG.)



