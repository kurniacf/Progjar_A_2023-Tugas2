# Tugas 2 Pemrograman Jaringan
- Nama: Kurnia Cahya Febryanto
- NRP: 5025201073
- Kelas: Pemrograman Jaringan A

## Daftar Isi
- [Deskripsi](#deskripsi)
- [Penjelasan file server](#penjelasan-file-server)
- [Capture Hasil Running Server](#capture-hasil-running-server)

## Deskripsi
Buatlah sebuah program time server dengan ketentuan sebagai berikut
### 1. Membuka port di port 45000 dengan transport TCP
- Jalankan environment lalu menuju lokasi folder progjar3
- Buka file server_thread.py di folder progjar 3
- Kemudian, ubahlah port di bagian socket bind menjadi 45000 sesuai ketentuan </br>
<img src="https://user-images.githubusercontent.com/70510279/226313209-3ff35e2b-46c3-4fb5-9f32-4110c644f953.png" width="500"/>

### 2. Server harus dapat melayani request yang concurrent
- Pada bagian main, ubah Server() menjadi TimeServer() karena kita akan membuat sebuah program time server. </br>
<img src="https://user-images.githubusercontent.com/70510279/226315179-358b2ab8-d7e7-47e5-85b9-8e77a8ef172f.png" width="500"/>

### 3. Ketentuan Request
- Diawali dengan string “TIME” dan diakhiri dengan karakter 13 dan karakter 10.
- Penambahan string “TIME” dilakukan pada bagian startswitch().
- Pada bagian endswitch() bisa ditambahkan (‘\r’ ‘\n’) sesuai dengan ketentuan soal. </br>
<img src="https://user-images.githubusercontent.com/70510279/226315396-609b282c-9ae9-406a-b8f4-4aab39d22bce.png" width="500"/>

### 4. Ketentuan Respon Server
- Dalam bentuk string (UTF-8). Bisa dilakukan deklarasi ‘utf-8’ pada saat melakukan send response. </br>
<img src="https://user-images.githubusercontent.com/70510279/226316040-2b2456b5-3685-410e-aa8a-35dc5456ad77.png" width="300"/>
- Diawali dengan JAM `<spasi>` `<jam>`. Response pada server diubah sesuai dengan ketentuan seperti berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/226316592-234550da-73fe-4edd-8907-7aff66426185.png" width="300"/>
- `<jam>` berisikan info jam dalam format “hh:mm:ss” dan diakhiri dengan karakter 13 dan karakter 10. Response current_time diubah sesuai dengan ketentuan sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/226324570-ce9481d2-b322-469f-bd84-73b1fdf3a866.png" width="300"/>
- Adapun keseluruhan code untuk ketentuan respon server sesuai soal adalah sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/226325041-80b0674a-61cb-4de2-a3e6-988e7576517a.png" width="700"/>

## Penjelasan file server
- File server menggunakan library socket, threading, logging, time, dan sys.
- Class ProcessTheClient digunakan untuk menangani koneksi dari tiap klien secara terpisah dalam sebuah thread.
- Server akan memeriksa apakah request diawali dengan string “TIME” dan diakhiri dengan karakter 13 dan 10. Jika aman, maka server akan mengirimkan waktu saat ini dalam format “JAM HH:MM:SS\r\n”.
- Class TimeServer digunakan untuk membuat dan mengelola server.
- Pada Class TimeServer, terdapat fungsi untuk menyimpan objek dari ProcessTheClient, membuat socket server, dan menjalankan server.

## Capture Hasil Running Server
<img src="https://user-images.githubusercontent.com/70510279/226325348-a3d22d0f-e253-46c1-a6a4-b6b8d2262865.png" width="700"/>