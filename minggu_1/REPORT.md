# LAPORAN PRAKTIKUM SISTEM OPERASI JOBSHEET 1

<h4> Nama : Muhammad Toriq Januarsyah<h4>
<h4> NIM : 254107020075<h4>
<h4> Kelas : 1-H <h4>

## 1.10 Latihan
### 1.10.1 Latihan Konseptual
#### Latihan 1.1
1. Jelaskan 5 fungsi utama sistem operasi dengan contoh konkret dari minimal 2 OS berbeda (Windows, macOS, atau Linux).

#### Jawaban 
1. Mengatur penjadwalan proses, pembuatan, hingga penghentian proses.
2. Membagi-bagi kapasitas RAM untuk setiap aplikasi yang dibuka agar tidak saling berebut.
3. Mengatur cara menyimpan, menghapus, dan mengelompokkan data dalam folder agar rapi dan aman.
4. Menghubungkan perangkat luar (seperti keyboard, mouse, atau printer) agar bisa dikenali dan dipakai oleh komputer
5. Menjaga data dari akses orang lain yang tidak berhak melalui sistem login dan izin akses.

contoh :
- windows => Penggunaan Task Manager untuk mengakhiri aplikasi yang tidak merespons.
- linux => Penggunaan perintah top atau htop untuk memantau proses yang sedang berjalan di Ubuntu Server.

#### 1.2
1. Kapan sebaiknya menggunakan Windows vs Linux vs macOS? 
   Analisis berdasarkan use case: gaming, development, server, creative work, dan enterprise.

#### Jawaban 
- berdasarkan use case maka penggunaan yang teapt 

### 1.10.2 Latihan Praktikal 
#### latihan 1.3
Install Ubuntu Server 22.04 LTS di VirtualBox dengan langkah berikut:
1. Download Ubuntu Server ISO dari website resmi
2. Create VM baru di VirtualBox (RAM: 2GB, Disk: 25GB)
3. Install dengan automatic partitioning (guided)
4. Buat user account dengan password yang kuat
5. Reboot dan login ke sistem
6. Dokumentasikan proses instalasi dengan screenshot key steps

#### Jawaban 
1. Download Ubuntu Server

![j1(latihan 1.3) instal ubuntu 1](image/j1(latihan 1.3) instal ubuntu 1.png "j1(latihan 1.3) instal ubuntu 1")

2. Login menggunakan user account dan password
minggu_1\image\j1(latihan 1.3) instal ubuntu 2.PNG

3. Tampilan Awal 
minggu_1\image\j1(latihan 1.3) instal ubuntu 3.PNG

#### 1.4 
Setelah instalasi Ubuntu Server, lakukan tasks berikut:
1. Update package list: sudo apt update
2. Upgrade packages: sudo apt upgrade
3. Install neofetch: sudo apt install neofetch
4. Jalankan neofetch dan screenshot hasilnya
5. Check disk usage dengan df -h
6. Check memory dengan free -h
7. Dokumentasikan output dari setiap command

#### Jawaban 
1. Update package list: sudo apt update
minggu_1\image\j1(latihan 1.4) sudo apt update 1.PNG

2. Upgrade packages: sudo apt upgrade
minggu_1\image\j1(latihan 1.4) sudo apt upgrade 2.PNG