# LAPORAN PRAKTIKUM SISTEM OPERASI JOBSHEET 2

<h4> Nama : Muhammad Toriq Januarsyah<h4>
<h4> NIM : 254107020075<h4>
<h4> Kelas : 1-H <h4>

## Praktikum 2.1 Identifikasi CPU dan Memori
1. Tampilkan informasi CPU : lscpu <br>
![js2_prak2.1_lscpu_1](image/js2_prak2.1_lscpu_1.png)

2. Tampilkan ringkasan memori : free -h <br>
![js2_prak2.1_ringkasan_memori_2](image/js2_prak2.1_ringkasan_memori_2.png)

3. cek informasi hardware dari DMI/BIOS (butuh sudo) : sudo dmidecode -t system <br>
![js2_prak2.1_informasi_hardware_3](image/js2_prak2.1_informasi_hardware_3.png)

### Latihan 2.1
Catat:
1. jumlah CPU(s), core/thread <br>
2. total RAM
3. total swap. 
Jelaskan perbedaan RAM vs swap dalam 2–3 kalimat.

## Jawaban 
1. informasi CPU : <br>
- CPU(s): 1
- Core per socket: 1
- Thread per core: 1

2. Total RAM <br>
- Total: 2.0 GiB

3. total Swap
- Total: 1.0 GiB

Perbedaan RAM dengan Swap <br>
RAM adalah memori fisik utama yang bekerja sangat cepat untuk menyimpan data aplikasi yang sedang aktif, sedangkan Swap adalah area di dalam hard disk (disk storage) yang digunakan sebagai cadangan saat RAM sudah penuh. Karena Swap berada di hard disk, kecepatannya jauh lebih lambat dibandingkan RAM, sehingga sistem hanya menggunakannya untuk data yang jarang diakses guna mencegah komputer crash.

## Praktikum 2.2 Identifikasi Perangkat PCI/USB dan Driver
1. lihat daftar perangkat PCI : lspci <br>
![js2_prak2.2_lspci_1](image/js2_prak2.2_lspci_1.png)

2. Lihat perangkat PCI beserta driver kernel yang digunakan: lspcu -nnk <br>
![js2_prak2.2_lspci_-nnk_2](image/js2_prak2.2_lspci_-nnk_2.png)

3. Fokus pada NIC (Ethernet) untuk mencari modul driver:  lspci -nnk | grep -A3 -i ethernet <br>
![js2_prak2.2_lspci_-nnk_grep_-A3_-i_ethernet_3](image/js2_prak2.2_lspci_-nnk_-A3_-i_ethernet_3.png)

4. Lihat perangkat USB: lsusb <br>
![js2_prak2.2_lsusb_4](image/js2_prak2.2_lsusb_4.png)

5. Lihat topologi USB (tree) : lsucb -t <br>
![js2_prak2.2_lsusb_-t_5](image/js2_prak2.2_lsusb_-t_5.png)

### latihan 2.2
1. Temukan 1 perangkat PCI (misal NIC) dan tuliskan: Vendor:Device ID (angka heksadesimal), nama driver/modul kernel, dan deskripsi singkat fungsinya.

### Jawaban 
- Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:1000] (rev 02) Subsystem: Intel Corporation PRO/1000 NT Desktop Adapter [8086:001e] Kernel driver in use: e1000 Kernel modules: e1000
- Vendor : Device ID : 8086:100e
- Nama driver/domul kernel : e1000
- fungsi : Perangkat ini merupakan Network Interface Card (NIC) atau kartu jaringan berbasis Intel yang berfungsi sebagai pengontrol komunikasi data (Ethernet), sehingga sistem dapat terhubung ke jaringan lokal maupun internet.

## Praktikum 2.3 Identifikasi Storage dan filesystem
1. Lihat daftar disk/partisi: lsblk -f <br>
![js2_prak2.3_daftar_disk_1](image/js2_prak2.3_daftar_disk_1.png)

2. Tampilkan UUID dan tipe filesystem: sudo blkid <br>
![js2_prak2.3_sudo_blkid_2](image/js2_prak2.3_sudo_blkid_2.png)

3. Lihat mount point untuk root filesystem: findmnt / <br>
![js2_prak2.3_findmnt_3](image/js2_prak2.3_findmnt_3.png)

## Praktikum 2.4 Melihat modul aktif dan informasinya  
1. cek versi kernel : uname -r <br>
![js2_prak2.3_versi_kernel_1](image/js2_prak2.3_versi_kernel_1.png)

2. Tampilkan daftar modul aktif: lsmod | head <br>
![js2_prak2.3_daftar_modul_2](image/js2_prak2.3_daftar_modul_2.png)

3. Pilih salah satu modul (contoh aman: loop) dan lihat detailnya: modinfo loop <br>
![js2_prak2.3_modul_loop_3](image/js2_prak2.3_modul_loop_3.png)

4. Muat modul (jika belum aktif), lalu verifikasi: sudo modprobe loop, lsmod | grep -i loop <br>
 ![js2_prak2.3_muat_modul_4](image/js2_prak2.3_muat_modul_4.png)

5. (Opsional) lihat pesan kernel terbaru: dmesg -T | tail -n 20 <br>
![js2_prak2.3_pesan kernal_5](image/js2_prak2.3_pesan%20kernal_5.png)
 
 ## Praktikum 2.5 Konfigurasi auto-load dan blacklist
1. Buat file auto-load: echo " loop " | sudo tee /etc/modules-load.d/loop.conf <br>
![js2_prak2.5_file_auto_load_1](image/js2_prak2.5_file_auto_load_1.png)

2. Simulasikan verifikasi (tanpa reboot) dengan memastikan modul sudah aktif: lsmod | grep -i loop <br>
![js2_prak2.5_simulasi_verivikasi_2](image/js2_prak2.5_simulasi_verivikasi_2.png)

3. (Opsional, konsep) blacklist modul: # echo "blacklist loop" | sudo tee /etc/modprobe.d/ blacklist-loop.conf <br>
![js2_prak2.5_blacklist_modul_3](image/js2_prak2.5_blacklist_modul_3.png)

## Praktikum 2.6 Mengenlasi block vs Character Device
1. Lihat detail salah satu disk (sesuaikan dengan perangkat Anda, misal sda): ls -l /dev/sda <br>
![js2_prak2.6_detail_disk_1](image/js2_prak2.6_detail_disk_1.png)

2. Lihat detail device terminal: ls -l /dev/tty <br>
![js2_prak2.6_detail_device_2](image/js2_prak2.6_detail_device_2.png)

3. Lihat disk dan partisi untuk mengaitkan dengan /dev: lsblk <br>
![js2_prak2.6_disk_partisi_3](image/js2_prak2.6_disk_partisi_3.png)

### Latihan 2.3 
1. Dari output ls -l, jelaskan perbedaan penanda file untuk block device dan
character device. (Hint: karakter pertama pada permission string)

### Jawaban 
- Berdasarkan pengamatan pada output perintah ls -l di direktori /dev, perbedaan antara block device dan character device dapat dilihat secara langsung pada karakter pertama dari deretan permission string-nya:

- Block Device (Ditandai dengan huruf b)
Jika karakter pertama adalah b, maka perangkat tersebut adalah block device. Perangkat ini mengelola data dalam bentuk blok-blok besar (seperti satu paket data) dan biasanya memiliki kemampuan penyimpanan.

- Character Device (Ditandai dengan huruf c)
Jika karakter pertama adalah c, maka perangkat tersebut adalah character device. Perangkat ini mengirim atau menerima data satu per satu karakter secara berurutan dalam aliran data yang terus-menerus.

- Kesimpulan:
Cukup dengan melihat huruf paling depan pada hasil ls -l, kita bisa tahu bagaimana sistem berkomunikasi dengan perangkat tersebut: b untuk perangkat penyimpanan (paket data besar) dan c untuk perangkat input/output (aliran karakter).

## Praktikum 2.7 Melihat Informasi udev
1. Cek atribut udev untuk disk: udevadm info --query=all --name=/dev/sda | head -n 30  <br>
![js2_prak2.7_atribut_udev_1](image/js2_prak2.7_atribut_udev_1.png)

2. (Opsional) monitor event udev (jalankan, lalu colok/lepas USB pada mesin
fisik): sudo udevadm monitor <br>
![js2_prak2.7_monitor_event_2](image/js2_prak2.7_monitor_event_2.png)

## Praktikum 2.8 membuat workspace praktikum 
1. Buat direktori praktikum dan masuk ke dalamnya:  <br>
```
1. mkdir -p ~/praktikum- os/week02
2. cd ~/praktikum-os/week02
3. pwd
```

![js2_prak2.8_direktori_praktikum_1](image/js2_prak2.8_direktori_praktikum_1.png)

2. buat beberapa file contoh : <br>
```
1. touch notes.txt data.log config.txt
2. ls -lah
```

![js2_prak2.8_buat_file_2](image/js2_prak2.8_buat_file_2.png)

3. isi file log contoh (simulasi): <br>
```
1. echo "INFO: service started' >> data.log
2. echo "WARN: disk usage high" >> data.log
3. echo "ERROR: failed to connect" >> data.log
4. cat data.log
```

![js2_prak2.8_isi_file_log_3](image/js2_prak2.8_isi_file_log_3.png)

4. Baca file dengan less: less data.log <br>

![js2_prak2.8_baca_file_4](image/js2_prak2.8_baca_file_4.png)

## Praktikum 2.9 Pencarian pola dengan grep
1. Cari baris yang mengandung ERROR pada data.log: grep " ERROR " data.log <br>
![Js2_prak2.9_CariBarisERROR_1](image/Js2_prak2.9_CariBarisERROR_1.png)

2. Cari tanpa memperhatikan huruf besar/kecil: grep -i "error" data.log <br>
![Js2_prak2.9_CariTnpaBesarKecil_2](image/Js2_prak2.9_CariTnpaBesarKecil_2.png)

3. tampiilkan nomor baris : grep -n "WARN" data.log <br>
![Js2_prak2.9_ShowNoBaris_3](image/Js2_prak2.9_ShowNoBaris_3.png)

4. Tampilkan baris yang tidak cocok (invert match): grep -v "INFO" data.log <br>
![Js2_prak2.9_tampilBarisTakCocok_4](image/Js2_prak2.9_tampilBarisTakCocok_4.png)

### Latihan 2.4 
1. Gunakan grep untuk menampilkan hanya baris yang mengandung INFO atau
WARN dari data.log. (Hint: gunakan grep -E dengan pola alternatif)

### Jawaban 
![latihan2.4](image/latihan2.4.png)

## Praktikum 2.10 substisui dengan sed (Aman di File Latihan)
1.Siapkan file konfigurasi latihan: <br>
```
1. cat > config.txt << 'EOF'
2. PORT=800
3. MODE=dev
4. SERVICE_NAME=myserever
5. EOF
6. cat congi.txt
```

![js2_prak2.10_FileLatihan_1](image/js2_prak2.10_FileLatihan_1.png)

2. Ganti dev menjadi prod (tanpa mengubah file asli): sed 's/MODE=dev/MODE=prod/'  config.txt <br>

![js2_prak2.10_devToprod_2](image/js2_prak2.10_devToprod_2.png)

3. Terapkan perubahan langsung ke file (-i):
```
1. sed -i 's/MODE=dev/MODE=prod/' config.txt
2. cat config.txt
```

![js2_prak2.10_perubahan_langsung_3](image/js2_prak2.10_perubahan_langsung_3.png)

4. Ganti semua kemunculan kata (g untuk global), contoh ubah myserver menjadi
node:
```
1. sed -i 's/myserver/node/g' config.txt
2.cat config.txt
```

![js2_prak2.10_ganti_kata_4](image/js2_prak2.10_ganti_kata_4.png)

## Praktikum 2.11 Ekstraksi kolom dengan awk
1. lihat output df -h : df -h <br>
![js2_prak2.11_output_df_1](image/js2_prak2.11_output_df_1.png)

2. Ambil kolom filesystem dan persentase pemakaian: df -h | awk 'NR==1 {print $1, $5, $6} NR>1 {print $5, $6}'
![js2_prak2.11_ambil_kolom_2](image/js2_prak2.11_ambil_kolom_2.png)

3. Filter hanya yang pemakaian disk di atas 80%: df -h | awk 'NR==1 || ($5+0) > 80 {print $1, $5, $6}'
 ![js2_prak2.11_filter_pemakaian_3](image/js2_prak2.11_filter_pemakaian_3.png)

 ## Praktikum 2.12 MElihat Proses dengan ps
 1. Tampilkan semua proses (format BSD): ps aux |head <br>
 ![js2_prak2.12_all_proses_1](image/js2_prak2.12_all_proses_1.png)

 2. Cari proses tertentu (misal sshd): ps aux | grep -i sshd <br>
 ![js2_prak2.12_proses_sshd_2](image/js2_prak2.12_proses_sshd_2.PNG)

## Praktikum 2.13 Monitoring Real-time dengan top
1. Jalankan top: top <br>
![js2_prak2.13_top_1](image/js2_prak2.13_top_1.png)

## Praktikum 2.14 menghentikan proses dengan kill
1. Jalankan proses dummy di background: 
```
sleep 300 & 
``` 

![js2_prak2.14_dummy_1](image/js2_prak2.14_dummy_1.png)

2. Cari PID proses sleep: 
``` 
ps aux | grep -E "sleep 300" | grep -v grep 
```

![js2_prak2.14_cari_PID_2](image/js2_prak2.14_cari_PID_2.png)

3. Hentikan dengan SIGTERM: 
``` 
kill <PID_PANDA> 
```

![js2_prak2.14_sigterm_3](image/js2_prak2.14_sigterm_3.png)

4. Verifikasi proses berhenti:
```
ps aux | grep -E "sleep 300" | grep -v grep
```

![js2_prak2.14_verivikasi_4](image/js2_prak2.14_verivikasi_4.png)

5. (Opsional) Jika proses sulit untuk dihentikan dan Anda membutukan untuk
menghentikan proses tersebut, gunakan SIGKILL:
```
kill -9 <PID_ANDA>
```

## Praktikum 2.15 Cek Disk, Load, dan Service 
1. cek penggunaan disk : df -h <br>
![js2_prak2.15_cek_disk_1](image/js2_prak2.15_cek_disk_1.png)

2. Cari direktori yang besar (contoh pada /var): sudo du -sh /var/* 2>/dev/null | sort -h | tail -n 10 <br>
![js2_prak2.15_cari_direktori_2](image/js2_prak2.15_cari_direktori_2.png)

3. cek load uptime: Uptime <br>
![js2_prak2.15_uptime_3](image/js2_prak2.15_uptime_3.png)

4. Cek service yang gagal: systemctl --failed <br>
![js2_prak2.15_cek_service_ggl_4](image/js2_prak2.15_cek_service_ggl_4.png)

5. Ambil log error terbaru (jika ada indikasi masalah): journalctl -xe | tail -n 50

## Praktikum 2.16 Monitoring Port dan Koneksi
(Network Basics)
1. Lihat interface dan IP: ip a <br>
![js2_prak2.16_interface_IP_1](image/js2_prak2.16_interface_IP_1.png)

2. Lihat routing table: ip r <br>
![js2_prak2.16._routing_table_2](image/js2_prak2.16._routing_table_2.png)

3. Lihat port yang sedang listening: sudo ss -tulpn <br>
![js2_prak2.16._port_3](image/js2_prak2.16._port_3.png)

### Latihan 2.5 
1. Pilih satu port yang listening dari output ss -tulpn(misal port 22), lalu
tuliskan service/proses yang membukanya. Jelaskan kegunaan port tersebut
secara singkat.

### Jawaban 
- Port yang Dipilih : 22
- Service/Proses : sshd (OpenSSH Daemon)
- Kegunaan Port : Port 22 digunakan untuk protokol SSH (Secure Shell) yang berfungsi untuk melakukan koneksi jarak jauh (remote login) ke server secara aman dan terenkripsi.

## Latihan 
### Latihan 2A
- Jalankan lspci -nnk. Pilih 1 perangkat PCI dan tuliskan: nama perangkat,
ID vendor:device, dan kernel driver in use.

### jawaban 2A
![js2_lat2A](image/js2_lat2A.png)
1. nama perangkat : Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller.
2. ID vendor:device => 8086:100e
3. kernel driver : e1000

### Latihan 2B
1. Tentukan device root filesystem dengan findmnt /. Lalu cocokkan dengan
lsblk -f dan tuliskan tipe filesystem serta UUID-nya.

### jawaban 2B
- findmnt /. <br>
![js2_lat2B_1](image/js2_lat2B_1.png)
- lsblk -f <br>
![js2_lat2B_2](image/js2_lat2B_2.png)
- Device Root: /dev/mapper/ubuntu--vg-ubuntu--lv
- Tipe Filesystem: ext4
- UUID: 70478099-b196-4874-8451-419998064b55

### Latihan 2C
1.   Buat file server.log berisi minimal 10 baris dengan variasi kata: INFO,
WARN, ERROR. Gunakan grep untuk menampilkan hanya baris ERROR.

### Jawaban 2C 
![js2_lat2C](image)