# LAPORAN PRAKTIKUM SISTEM OPERASI JOBSHEET 4

<h4> Nama : Muhammad Toriq Januarsyah<h4>
<h4> NIM : 254107020075<h4>
<h4> Kelas : TI 1-H <h4>

## Tugas Pendahuluan 
- Jawablah pertanyaan-pertanyaan di bawah ini :
    1. Apa yang dimkasud perintah-perintah direktory : pwd, cd, mkdir, rmdir.
    2. Apa yang dimaksud perintah-perintah manipulasi file : cp, mv, dan rm (sertakan format yang digunakan)
    3. Jelaskan perbedaan symbolic link menggunakan hard link (direct) dan soft link (indirect)
    4. Tuliskan maksud perintah-perintah : file, find, which, locate dan grep
  
### Jawaban Tugas Pendahuluan :
1. direktori : 
    - pwd: Print Working Directory - Menampilkan direktori aktual (lokasi dimana user berada saat ini)
    - cd: Change Directory - Berpindah dari satu direktori ke direktori lain
    - mkdir: Make Directory - Membuat direktori baru
    - rmdir: Remove Directory - Menghapus direktori yang kosong

2. perintah :
    - cp: Copy - Mengkopi file atau direktori
        format penggunaan: 
        cp file_sumber file_tujuan     # copy file
        cp -r dir_sumber dir_tujuan    # copy direktori beserta isinya
    - mv: Move - Memindahkan atau me-rename file/direktori
        format penggunaan:               
        mv file_lama file_baru         # rename file
        mv file /path/tujuan/          # pindahkan file ke direktori lain
        mv dir_lama dir_baru           # rename direktori 
    - rm: Remove - Menghapus file atau direktori
        format pengguanaan : 
        rm file.txt             # Hapus file
        rm -i file.txt          # Hapus file dengan konfirmasi
        rm -r direktori/        # Hapus direktori beserta isinya 
        rm -rf direktori/       # Hapus paksa direktori tanpa konfirmasi
        
3.  Perbedaan Symbolic Link: Hard Link vs Soft Link
Aspek,**Hard Link**,**Soft Link (Symbolic Link)**
**Perintah**,`ln file_asli file_link`,`ln -s file_asli file_link`
**Tipe file**,`-` (file biasa),`l` (link)
**Link count**,Bertambah (terlihat di `ls -l`),Tidak berubah
**Cross-partisi**,❌ Tidak bisa (harus 1 partisi),✅ Bisa antar partisi
**File asli dihapus**,Data masih ada (link masih valid),Link rusak (broken link)
**Direktori**,❌ Tidak bisa di-hard link,✅ Bisa di-soft link
**Pointer**,Pointer ke **inode** (data fisik),Pointer ke **nama file/path**
**Ukuran**,Sama dengan file asli,Kecil (hanya path string)

4. Penjelasan Perintah: file, find, which, locate, grep


## Percobaan 1 : Direktory
1. melihat direktori home 
```
$ pwd
$ echo $HOME
```
![js4_percobaan1_1](image)

2. Melihat direktori aktual dan parent direktori
```
$ pwd
$ cd .
$ pwd
$ cd ..
$ pwd
$ cd
```
![js4_percobaan1_2](image)

3. Membuat satu direktori, lebih dari satu direktori atau sub direktori
```
$ pwd
$ mkdir A B C A/D/ A/E B/F A/D/A
$ ls -l
$ ls -l A
$ ls -l A/D
```
![js4_percobaan1_3](image)

4. Menghapus satu atau lebih direktori hanya dapat dilakukan pada direktori kosong dan hanya dapat dihapus oleh pemiliknya kecuali bila diberikan ijin aksesnya
```
$ rmdir B
```
![js4_percobaan1_4.1](image)
- Terdapat pesan error, mengapa?
    - 
```
$ ls -l B
$ rmdir B/F B
$ ls -l B
```
- Terdapat pesan error, mengapa?
    - 

5. Navigasi direktori dengan instruksi cd untuk pindah dari sau direktori ke direktori lain.
```
$ pwd
$ ls -l
$ cd A
$ pwd
$ cd ..
$ cd /home/<user>/C
$ pwd
$ cd /<user>/C 
```
- Terdapat pesan error, mengapa?
    - 
```
$ pd
```

## Percobaan 2  : Manipulasi file
1. Perintah cp untuk mengkopi file atau seluruh direktori
```
$ cat > contoh
Membuat sebuah file 
[Ctrl-d]
$ cp contoh contoh1
$ ls -l
$ mv contoh A
$ ls -l A
cp contoh contoh1 A/D
$ ls -l A/D
```
