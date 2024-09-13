[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/8b_y5Av8)
| Name                   | NRP        | Kelas               |
| -----------------------| -----------| --------------------|
| Rafli Raihan Pramudya  | 5025221273 | Jaringan Komputer A |
| Yasmin Putri Sujono    | 5025221273 | Jaringan Komputer A |

## Task 1

> a. Berapa banyak packet yang terekam pada file pcapng?
**Answer: 1089 (packets)**
- Flag <br>
Nomor 1 di bagian a menunjukkan jumlah total paket yang terekam dalam file pcapng, yaitu 1089 packets. Flag yang ditemukan pada nomor 1 di bagian a adalah : <br>
`JARKOM24{K4mu_K3r3n_0CHM7NFTA4ZTT7VW9HNWP3VVXURUF50xL4ughafj1pkt52dgrn1hlocj7aa3}`
  
- Explanation <br>
Untuk menemukan jawaban ini, hanya dengan melihat bagian bawah Wireshark di area status bar yang menunjukkan jumlah total paket yang ada, dengan tulisan 'Packets:'. Ini langsung    menjawab mengenai jumlah paket yang ada di file pcapng tanpa perlu filter tambahan.
  
- Output result <br>
  Percobaan: <br>
  <img width="156" alt="Screenshot 2024-09-11 at 22 38 08" src="https://github.com/user-attachments/assets/067b0d0d-6f4e-4851-b7e6-750ef3b335d2">
  
<br>
<br>

> b. Ada berapa jenis protocol yang terekam pada traffic
**Answer: 4 (protocol)**
- Flag <br>
Nomor 1 di bagian b menunjukkan jumlah total jenis protocol yang ada. Flag yang ditemukan pada nomor 1 : <br>
  `JARKOM24{K4mu_K3r3n_0CHM7NFTA4ZTT7VW9HNWP3VVXURUF50xL4ughafj1pkt52dgrn1hlocj7aa3}`
  
- Explanation <br>
  Untuk menjawab pertanyaan ini, Anda dapat langsung melihat tabel Protocol. Tabel ini memperlihatkan semua protokol yang terdeteksi dalam traffic yang ditangkap tanpa perlu  filter tambahan.

- Output result <br>
    Percobaan : <br>
  <img width="76" alt="Screenshot 2024-09-11 at 22 38 33" src="https://github.com/user-attachments/assets/d2c3f086-f0d9-4bc8-8cc1-d5bdbfda7ba1">
  <br>
  Hasil dari nomor 1: <br>
   ![WhatsApp Image 2024-09-11 at 18 56 17](https://github.com/user-attachments/assets/512599ad-28be-4acd-9104-7ee4ffdeb0c1)
<br>
<br>

> c. Sebutkan secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator, contoh: protocol1,protocol2
**Answer: HTTP,MDNS,SSDP,TCP**
- Flag <br>
Nomor 1 di bagian c mengurutkan sesuai alfabet jenis protocol yang ada. Flag yang ditemukan pada nomor 1 : <br>
  `JARKOM24{K4mu_K3r3n_0CHM7NFTA4ZTT7VW9HNWP3VVXURUF50xL4ughafj1pkt52dgrn1hlocj7aa3}`
  
- Explanation <br>
  Perhatikan daftar protokol yang disebutkan di bagian 'protocol'. Urutkan protokol-protokol tersebut secara alfabet dari A hingga Z untuk mendapatkan hasil akhir yang benar. <br>

- Output result <br>
  Percobaan : <br>
  <img width="76" alt="Screenshot 2024-09-11 at 22 38 33" src="https://github.com/user-attachments/assets/d2c3f086-f0d9-4bc8-8cc1-d5bdbfda7ba1">
  <br>
  Hasil dari nomor 1: <br>
  ![WhatsApp Image 2024-09-11 at 18 56 17](https://github.com/user-attachments/assets/512599ad-28be-4acd-9104-7ee4ffdeb0c1)
  
## Task 2

> a. Berapa banyak packet berbasis TCP yang memiliki flag [RST, ACK]
**Answer: 411(Packets)**

- Flag <br>
Nomor 2 di bagian 1 menunujukan total keseluruhan jumlah paket berbasis TCP yang memiliki flag [RST, ACK]. Flag yang ditemukan pada nomor 2 : <br>
`JARKOM24{W0w_4nother_Sh0t_OYDHKUUZWAH0mptyaskunvbqdlbxgpquztpcM4r146395034977909808867}`

- Filter expression <br>
  `tcp.flags == 0x14`
  
- Explanation <br>
  Untuk menjawab nomor ini, perlu mengaplikasikan filter diatas, yaitu `tcp.flags == 0x14`. Dengan filter ini akan mencari paket TCP dengan flag [RST, ACK]. Angka 0x14 mewakili kombinasi bit untuk flag RST (0x04) dan ACK (0x10). Setelah filter diterapkan, nantinya hanya akan menampilkan semua paket yang sesuai dengan filter [RST, ACK].Untuk mengetahui jumlah paket yang ditampilkan, lihat angka di status bar di bagian bawah, yang menunjukkan jumlah total paket yang sesuai dengan filter, seperti 1a.

- Output result <br>
  Percobaan : <br>

  <br>
  Hasil dari nomor 2: <br>
  ![WhatsApp Image 2024-09-11 at 19 05 43](https://github.com/user-attachments/assets/a0ab76c7-a2c5-4347-9128-b9b9b6079827)

<br>
<br>

> b. How many TCP based packets have only the [SYN] flag?

**Answer: 412(Packets)**

- Flag <br>
Nomor 2 di bagian b menunujukan total keseluruhan jumlah paket berbasis TCP yang memiliki flag RST. Flag yang ditemukan pada nomor 2 : <br>
`JARKOM24{W0w_4nother_Sh0t_OYDHKUUZWAH0mptyaskunvbqdlbxgpquztpcM4r146395034977909808867}`

- Filter expression <br>
  `tcp.flags.syn == 1 && tcp.flags.ack == 0`
  
- Explanation <br>
  Untuk menjawab nomor ini, perlu mengaplikasikan filter diatas, yaitu `tcp.flags.syn == 1 && tcp.flags.ack == 0`. Dengan filter ini mencari paket TCP yang memiliki flag SYN aktif (tcp.flags.syn == 1) dan flag ACK tidak aktif (tcp.flags.ack == 0), sehingga hanya paket SYN yang akan muncul. Setelah filter diterapkan, nantinya akan menampilkan semua paket yang hanya memiliki flag [SYN]. Untuk mengetahui jumlah paket yang ditampilkan, lihat angka di status bar di bagian bawah, yang menunjukkan jumlah total paket yang sesuai dengan filter, seperti 1a.
 
- Output result <br>
  Percobaan : <br>

  <br>
  Hasil dari nomor 2: <br>
  ![WhatsApp Image 2024-09-11 at 19 05 43](https://github.com/user-attachments/assets/a0ab76c7-a2c5-4347-9128-b9b9b6079827)

<br>
<br>

> c. How many TCP based packets have the ACK flag but do not have SYN or RST?

**Answer: 217(Packets)**

- Flag <br>
Nomor 2 di bagian c menunujukan total keseluruhan jumlah paket berbasis TCP yang memiliki flag ACK. Flag yang ditemukan pada nomor 2 : <br>
`JARKOM24{W0w_4nother_Sh0t_OYDHKUUZWAH0mptyaskunvbqdlbxgpquztpcM4r146395034977909808867}`

- Filter expression <br>
  `tcp.flags.ack == 1 && tcp.flags.syn == 0`
  
- Explanation <br>
    Untuk menjawab nomor ini, saya menghitung secara manual. Pengaplikasian filter `tcp.flags.ack == 1 && tcp.flags.syn == 0` yang menghasilkan 628 packets. Filter ini mencari paket TCP yang memiliki flag ACK aktif (tcp.flags.ack == 1) dan flag SYN serta RST tidak aktif (tcp.flags.syn == 0 dan tcp.flags.rst == 0). Setelah memasukkan filter, hanya akan menampilkan semua paket yang sesuai dengan kriteria yang diberikan (ACK aktif, tetapi SYN dan RST tidak aktif).Dengan itu bisa menghitung dengan mengurangi filter 2a, yaitu `tcp.flags == 0x14` yang menghitung kedua flag ACK dan RST. Maka dari itu didapatkan angka 217 packets dengan cara (628 - 411).  


- Output result <br>
 Percobaan : <br>

  <br>
  Hasil dari nomor 2: <br>
  ![WhatsApp Image 2024-09-11 at 19 05 43](https://github.com/user-attachments/assets/a0ab76c7-a2c5-4347-9128-b9b9b6079827)

<br>
<br>

## Task 3

> a. Pada port berapa server http terbuka?

**Answer: 9282**

- Flag <br>
Nomor 3 di bagian a menunujukan port berapa yang membuka server http. Flag yang ditemukan pada nomor 3 : <br>
`JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`
  
- Explanation <br>
  Dengan mengetik `http` menggunakan apply filter, maka akan memperlihatkan 2 server HTTP. Dibagian bawah kiri, dapat dilihat pada bagian detail paket di bawah "Transmission Control Protocol," di mana tertulis Source Port: 53866 (port klien) dan Destination Port: 9282 (port server HTTP). Sehingga, server HTTP terbuka pada port 9282 dalam contoh yang Anda berikan.

- Output result <br>
 Percobaan : <br>
<img width="1440" alt="Screenshot 2024-09-13 at 14 57 11" src="https://github.com/user-attachments/assets/cd1b9c7a-0fe6-4999-8ce7-d3f81c96a2d1">

  <br>
  Hasil dari nomor 3: <br>
<img width="1136" alt="Screenshot 2024-09-13 at 14 56 40" src="https://github.com/user-attachments/assets/65655150-1a79-4bb8-ac88-d1254aeba816">

<br>
<br>

> b. Berapa byte file response yang dikirim dari server
**Answer: 427**
- Flag <br>
Nomor 3 di bagian b menunujukan berapa byte file yang berasal dari server http. Flag yang ditemukan pada nomor 3 : <br>
  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`
  
- Explanation <br>
  Dengan mengetik `http` menggunakan apply filter, maka akan memperlihatkan 2 server HTTP. Pada paket nomor 970, protokol HTTP menunjukkan respons dengan status "HTTP/1.0 200 OK".
Ukuran data yang dikirim dari server bisa dilihat di kolom Length, yang menunjukkan 427 bytes. Sehingga, file respons yang dikirim dari server berukuran 427 byte.

- Output result <br>
 Percobaan : <br>
<img width="1440" alt="Screenshot 2024-09-13 at 14 57 11" src="https://github.com/user-attachments/assets/cd1b9c7a-0fe6-4999-8ce7-d3f81c96a2d1">

  <br>
  Hasil dari nomor 3: <br>
<img width="1136" alt="Screenshot 2024-09-13 at 14 56 40" src="https://github.com/user-attachments/assets/65655150-1a79-4bb8-ac88-d1254aeba816">

<br>
<br>

> c. Berapa jumlah file yang terdapat pada server?
**Answer: 4**
- Flag <br>
 Nomor 3 di bagian c menunujukan total file yang terdapat di server http. Flag yang ditemukan pada nomor 3 : <br>
  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`

- Filter expression <br>
  `tcp contains "file"`
  
- Explanation <br>
  Untuk menjawab soal ini, dibutuhkan filter `tcp contains "file"` dengan begitu, maka output yang dikeluarkan hanya satu yaitu (text/html). Setelah itu, klik kanan pada bagian server lalu dilanjutkan memencet `follow` dengan `HTTP Stream` nantinya akan menampilkan isi dari text-server tersebut. File terdiri dari 4 file :
  ```
  <li><a href="file.pdf">file.pdf</a></li>
  <li><a href="hello.html">hello.html</a></li>
  <li><a href="lion.jpg">lion.jpg</a></li>
  <li><a href="present.pptx">present.pptx</a></li>
  ```. 

- Output result <br>
 Percobaan : <br>
<img width="1366" alt="Screenshot 2024-09-13 at 14 52 08" src="https://github.com/user-attachments/assets/0a038836-bd47-481c-afc4-088e6664c2e9">
  <br>
  Hasil dari nomor 3: <br>
<img width="1136" alt="Screenshot 2024-09-13 at 14 56 40" src="https://github.com/user-attachments/assets/65655150-1a79-4bb8-ac88-d1254aeba816">

<br>
<br>

> d. Sebutkan nama file secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator, contoh: file1,file2
**Answer: file.pdf,hello.html,lion.jpg,present.pptx**
- Flag <br>
  Nomor 3 di bagian d mengurutkan file yang terdapat di server http. Flag yang ditemukan pada nomor 3 : <br>
  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`
  
- Explanation <br>
  Setelah itu, maka akan terbuka isi file-server tersebut, 
   ```
  <li><a href="file.pdf">file.pdf</a></li>
  <li><a href="hello.html">hello.html</a></li>
  <li><a href="lion.jpg">lion.jpg</a></li>
  <li><a href="present.pptx">present.pptx</a></li>
  ```
  <br> Setelah mendapatkan file-file tersebut maka melanjutkan dengan mengurutkan sesuai alfabet dan applying dengan tanda koma sebagai pemisah.

- Output result <br>
 Percobaan : <br>
<img width="1440" alt="Screenshot 2024-09-13 at 14 53 47" src="https://github.com/user-attachments/assets/dbbaa16f-3fac-437e-8266-1b855036c9e9">

  <br>
  Hasil dari nomor 3: <br>
<img width="1136" alt="Screenshot 2024-09-13 at 14 56 40" src="https://github.com/user-attachments/assets/65655150-1a79-4bb8-ac88-d1254aeba816">
  
<br>
<br>

## Task 4

> Protokol apa yang paling banyak terdapat di file hasil capture traffic?
**Answer: FTP**
- Flag <br>

- Filter expression <br>

  `Put your filter expression here (if any)`
  
- Explanation <br>

  `Describe how you solve the questions`

- Output result <br>
 Percobaan : <br>

  <br>
  Hasil dari nomor 1: <br>


<br>
<br>

## Task 5

> Berdasarkan hasil bruteforce, apa user yang tepat dari hasil bruteforce?

**Answer: gedagedigedagedao**

- Flag <br>

  `Put your flag in here`

- Filter expression <br>

  `Put your filter expression here (if any)`
  
- Explanation <br>

  `Describe how you solve the questions`

- Output result <br>
 Percobaan : <br>

  <br>
  Hasil dari nomor 1: <br>
  ![WhatsApp Image 2024-09-11 at 19 13 05](https://github.com/user-attachments/assets/f892b39e-11b8-4a21-8740-92896b23cc4f)

<br>
<br>


## Task 6

> Apa password yang tepat?

> _What is the correct password?_


**Answer:**

- Flag

  `JARKOM24{h1s_fr1end_1s_g3d4g3d1g3d4g3d03_CBT3849SKSyksnUmmdoqmzesqfB4Sur1ZYQFBKAZZQ}`

- Filter expression

  `tcp contains "success"`
  
- Explanation

  Pada packet pcap yang diberikan sedang terjadi percobaan brute force dan pada beberapa stream terdapat user, pass dan pesan sukses.
  kita hanya perlu mencari pesan yang mengeluarkan pesan sukses
  
- Output result

  ![Flag No 6](<No 6.jpg>)

<br>
<br>

## Task 7

> Pada port berapa telnet yang bisa diakses?

> _On which port is Telnet accessible?_


**Answer:**

- Flag

  `JARKOM24{Gr34t_Sn1ff3r_WPLYVyksnUmqvy9l0n0zoT3t0t0B3HABAWu5}`

- Filter expression

  `tcp contains "telnet"`
  
- Explanation

![exp no 7](image.png)

pada saat packet tcp tersebut di follow, dapat dilihat bahwa user sedang mengakses telnet. dan kita hanya perlu melihat portnya

- Output result

  ![flag no 7](<no 7.jpg>)

<br>
<br>

## Task 8

> Ada berapa file di dalam server?

> _How many files are on the server?_


**Answer:**

- Flag

  `JARKOM24{P4ck3t_4n4lyz3r_PXWyUkzaeu3112dyrjovtkxvS1SQFYOTEBMYL}`

- Filter expression

  `-`
  
- Explanation

  Pada stream terakhir setelah login telnet, dapat di lihat aktivitas user. salah satu command yang dilakukan user adalah ls yang menampilkan semua file yang ada. dimana terdapat 7 file

- Output result

  ![no 8 flag](<no 8.jpg>)

<br>
<br>

## Task 9

> Apa nama file yang dieksekusi oleh user?

> _What is the name of the file executed by the user?_


**Answer:**

- Flag

  `JARKOM24{333ch000_us3r_056087718812udRCvjhzjcd33d3O8NX71REU}`

- Filter expression

  `-`
  
- Explanation

  Sama seperti sebelumnya, semua yang dilakukan user di terminal dapat dilihat di wireshark. user menjalankan perintah ./echo untuk mengeluarkan isi dari file 

- Output result

  ![flag no 9](<no 9.jpg>)

<br>
<br>

## Task 10

> Apa output dari file dalam bentuk base64 decode?

> _What is the output of the file in base64-decoded form?_


**Answer:**

- Flag

  `JARKOM24{tH4ts_1t_w3ll_d0n3_971099060413378esesagp1u1231421421DZ23Q3OVM4PTJAL}`

- Filter expression

  `-`
  
- Explanation

  Sama seperti sebelumnya, user menjalankan program echo yang mengeluarkan kalimat yang dienskripsi dengan metode base64 (dapat dilihat dari akhir string terdapat tanda =). setelah di decrypt, flag terakhir telah didapatkan

- Output result

  ![flag no 10](<no 10.jpg>)

<br>
<br>

## Summary

Alhamdulilah lancar

## Problems

Tim kami tidak mengalami masalah yang rumit, kecuali laman web ctf yang kurang responsif karena diakses banyak tim
