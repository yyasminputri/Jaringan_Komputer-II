## Task 1

> a. Berapa banyak packet yang terekam pada file pcapng?

**Answer: 1089 (packets)**

- Flag <br>
Nomor 1 di bagian a menunjukkan jumlah total paket yang terekam dalam file pcapng, yaitu 1089 packets. Flag yang ditemukan pada nomor 1 di bagian a adalah : 
`JARKOM24{K4mu_K3r3n_0CHM7NFTA4ZTT7VW9HNWP3VVXURUF50xL4ughafj1pkt52dgrn1hlocj7aa3}`
  
- Explanation
  Untuk menemukan jawaban ini, hanya dengan melihat bagian bawah Wireshark di area status bar yang menunjukkan jumlah total paket yang ada, dengan tulisan 'Packets:'. Ini langsung    menjawab mengenai jumlah paket yang ada di file pcapng tanpa perlu filter tambahan.
  
- Output result
  Hasil dari nomor 1: 
  <img width="156" alt="Screenshot 2024-09-11 at 22 38 08" src="https://github.com/user-attachments/assets/067b0d0d-6f4e-4851-b7e6-750ef3b335d2">

<br>
<br>

> b. Ada berapa jenis protocol yang terekam pada traffic

**Answer: 4 (protocol)**

- Flag
  Flag yang ditemukan pada bagian ini tetap sama:
  `JARKOM24{K4mu_K3r3n_0CHM7NFTA4ZTT7VW9HNWP3VVXURUF50xL4ughafj1pkt52dgrn1hlocj7aa3}`
  
- Explanation
  Untuk menjawab pertanyaan ini, Anda dapat langsung melihat tabel Protocol. Tabel ini memperlihatkan semua protokol yang terdeteksi dalam traffic yang ditangkap tanpa perlu  filter tambahan.

- Output result
    Hasil dari nomor 1: 
    <img width="76" alt="Screenshot 2024-09-11 at 22 38 33" src="https://github.com/user-attachments/assets/d2c3f086-f0d9-4bc8-8cc1-d5bdbfda7ba1">

<br>
<br>

> c. Sebutkan secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator, contoh: protocol1,protocol2

**Answer: HTTP,MDNS,SSDP,TCP**

- Flag
  `JARKOM24{K4mu_K3r3n_0CHM7NFTA4ZTT7VW9HNWP3VVXURUF50xL4ughafj1pkt52dgrn1hlocj7aa3}`
  
- Explanation
  Perhatikan daftar protokol yang disebutkan di bagian 'protocol'. Urutkan protokol-protokol tersebut secara alfabet dari A hingga Z untuk mendapatkan hasil akhir yang benar.

- Output result
  Hasil dari nomor 1: 
    <img width="76" alt="Screenshot 2024-09-11 at 22 38 33" src="https://github.com/user-attachments/assets/d2c3f086-f0d9-4bc8-8cc1-d5bdbfda7ba1">

## Task 2

> a. Berapa banyak packet berbasis TCP yang memiliki flag [RST, ACK]

**Answer: 411(packets)**

- Flag
  `JARKOM24{W0w_4nother_Sh0t_OYDHKUUZWAH0mptyaskunvbqdlbxgpquztpcM4r146395034977909808867}`

- Filter expression
  `tcp.flags == 0x14`
  
- Explanation
  Untuk menjawab soal ini saya menggunakan filter 'tcp.flags == 0x14'. Filter ini mencari paket TCP dengan flag [RST, ACK]. Dengan angka 0x14 mewakili kombinasi bit untuk flag RST    (0x04) dan ACK (0x10). Setelah filter diterapkan, didalamnya hanya akan menampilkan semua paket yang sesuai dengan filter yang diinginkan. Maka, kita bisa melihat berapa banyak     paket yang ada melalui kolom [Packets]

- Output result
  Percobaan Filter :
  <img width="1072" alt="Screenshot 2024-09-13 at 11 11 57" src="https://github.com/user-attachments/assets/a24cc847-2b74-4722-b704-417713605ca0">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 17 10](https://github.com/user-attachments/assets/ba870a65-a6b6-4518-bdfa-5e668b257398)

<br>
<br>

> b. How many TCP based packets have only the [SYN] flag?

**Answer: 412(packets)**

- Flag
  `JARKOM24{W0w_4nother_Sh0t_OYDHKUUZWAH0mptyaskunvbqdlbxgpquztpcM4r146395034977909808867}`

- Filter expression

  `tcp.flags.syn == 1 && tcp.flags.ack == 0'`
  
- Explanation
  Untuk menjawab soal ini saya menggunakan filter 'tcp.flags.syn == 1 && tcp.flags.ack == 0'. Pertama, apply filter pada bagian atas aplikasi. Lalu, gunakan filter yang telah dibuat. Dengan filter ini hanya akan mencari paket TCP yang memiliki flag SYN aktif (tcp.flags.syn == 1)   dan flag ACK tidak aktif (tcp.flags.ack == 0), sehingga hanya paket SYN yang akan muncul.

- Output result
  Percobaan Filter :
  <img width="1440" alt="Screenshot 2024-09-13 at 11 19 29" src="https://github.com/user-attachments/assets/081e8ef8-10e7-463c-952f-deb74bd4b89b">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 17 10](https://github.com/user-attachments/assets/ba870a65-a6b6-4518-bdfa-5e668b257398)

<br>
<br>

> c. Berapa banyak packet berbasis TCP yang memiliki flag ack, tapi tidak memiliki syn, dan tidak memiliki rst
**Answer: 217(packets)**

- Flag
  Nomor 2 di bagian c menunjukkan jumlah total paket yang berbasis TCP yang memiliki flag hanya ack. Flag yang ditemukan pada nomor 2 adalah : 
  `JARKOM24{W0w_4nother_Sh0t_OYDHKUUZWAH0mptyaskunvbqdlbxgpquztpcM4r146395034977909808867}`
  
- Explanation
   Untuk bagian ini saya menghitung secara manual, dengan menghitung berapa banyak yang dimiliki paket ack sebesar 628 tanpa syn dengan rumus 'tcp.flags.ack == 1 && tcp.flags.syn == 0 ' dikurangi banyak paket rst dan ack sebesar 411. Maka menghasilkan 217 paket. (628 - 217).

- Output result
  Percobaan Filter :
  <img width="1440" alt="Screenshot 2024-09-13 at 13 09 22" src="https://github.com/user-attachments/assets/e352b37f-55b1-4466-bd15-39672f213410">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 17 10](https://github.com/user-attachments/assets/ba870a65-a6b6-4518-bdfa-5e668b257398)

<br>
<br>

## Task 3

> a. Pada port berapa server http terbuka?
**Answer: 9282**

- Flag
  Nomor 3 di bagian 1 menunjukkan port berapa server http akan terbuka. Flag yang ditemukan pada nomor 3 adalah : 
  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`

- Filter expression
  `http`
  
- Explanation
  Untuk menjawab soal ini, klik pada bagian atas applu filter dengan menulis 'http'. Jawaban ini dapat dilihat pada bagian detail paket di bawah "Transmission Control Protocol," di mana tertulis, Source Port: 53866 (port klien) dan Destination Port: 9282 (port server HTTP).

- Output result
 Percobaan Filter :
  <img width="1440" alt="Screenshot 2024-09-13 at 12 14 41" src="https://github.com/user-attachments/assets/0b9dc8ba-5b4f-4646-ae67-757970d0c64d">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 42 48](https://github.com/user-attachments/assets/7902d4f4-2e42-4d89-8683-191def86370f)

<br>
<br>

> b. Berapa byte file response yang dikirim dari server

**Answer: 427**

- Flag
  Nomor 3 di bagian b menunjukkan byte file response (HTTP) yang dikirim dari server. Flag yang ditemukan pada nomor 3 adalah : 
  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`

- Filter expression
  `Put your filter expression here (if any)`
  
- Explanation
  Pada soal ini, kita dapat melihat ukuran file respons yang dikirim dari server berdasar pada paket nomor 970, protokol HTTP yang menunjukkan respons dengan status "HTTP/1.0 200 OK". Ukuran data yang dikirim dari server bisa dilihat di kolom Length, yang menunjukkan 427 bytes.

- Output result
   Percobaan Filter :
  <img width="1440" alt="Screenshot 2024-09-13 at 12 14 41" src="https://github.com/user-attachments/assets/0b9dc8ba-5b4f-4646-ae67-757970d0c64d">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 42 48](https://github.com/user-attachments/assets/7902d4f4-2e42-4d89-8683-191def86370f)

<br>
<br>

> c. Berapa jumlah file yang terdapat pada server?

**Answer: 4**

- Flag
 Nomor 3 di bagian c mencari total file yang terdapat pada server (HTTP). Flag yang ditemukan pada nomor 3 adalah : 
  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`
  
- Filter expression
  `tcp contains "file"`

- Explanation
  Pada bagian ini, tulis sesuai filter yang dibuat 'tcp contains "file"'. Setelah didapat, hanya terdapat satu file yang bersifat file.text, maka setelah itu klik kanan, lalu di bagian follow, pencet bagian HTTP Stream. Setelah itu nanti akan terdapat file yang ada di dalam server tersebut. Hitung total file yang terdapat server tersebut.
  
- Output result
   Percobaan Filter :
  <img width="1440" alt="Screenshot 2024-09-13 at 13 26 20" src="https://github.com/user-attachments/assets/ac9e07de-ef0f-4935-b365-c5115accba7d">
  
  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 42 48](https://github.com/user-attachments/assets/7902d4f4-2e42-4d89-8683-191def86370f)

<br>
<br>

> d. Sebutkan nama file secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator, contoh: file1,file2

**Answer: file.pdf,hello.html,lion.jpg,present.pptx**

- Flag
  Nomor 3 di bagian c mengurutkan file yang terdapat pada server (HTTP). Flag yang ditemukan pada nomor 3 adalah : 
  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_NTA5TL1ts5e3x6pfnpn11huonfyabtc}`
  
- Explanation
  Setelah masuk ke server tersebut yang bersifat file/html. Maka akan mendapatkan isi dari server tersebut, bisa dilihat terdapat 4 file yang ada, seperti dibawah ini. 
```
<li><a href="file.pdf">file.pdf</a></li>
<li><a href="hello.html">hello.html</a></li>
<li><a href="lion.jpg">lion.jpg</a></li>
<li><a href="present.pptx">present.pptx</a></li>
```
Lalu, lanjutkan saja mengurutkan file yang ada, maka setelah itu terdapatlah jawaban dari soal ini.  

- Output result
   Percobaan Filter :
  <img width="1440" alt="Screenshot 2024-09-13 at 13 31 05" src="https://github.com/user-attachments/assets/05d60322-0fc7-4119-a6d4-06efe27264ee">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 42 48](https://github.com/user-attachments/assets/7902d4f4-2e42-4d89-8683-191def86370f)

<br>
<br>

## Task 4

> Protokol apa yang paling banyak terdapat di file hasil capture traffic?

**Answer: FTP**

- Flag

  `Put your flag in here`

- Filter expression

  `Put your filter expression here (if any)`
  
- Explanation
Masuk ke Statistic → Protocol Hierary 
FTP berada di TCP, hanya ada FTP dibawah TCP

- Output result
  Percobaan :
  <img width="1440" alt="Screenshot 2024-09-13 at 13 31 05" src="https://github.com/user-attachments/assets/05d60322-0fc7-4119-a6d4-06efe27264ee">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 42 48](https://github.com/user-attachments/assets/7902d4f4-2e42-4d89-8683-191def86370f)


<br>
<br>

## Task 5

> Berdasarkan hasil bruteforce, apa user yang tepat dari hasil bruteforce?

**Answer: gedagedigedagedao**

- Flag

  `Put your flag in here`

- Filter expression

  `Put your filter expression here (if any)`
  
- Explanation
Memulai pencarian, yaitu menggunakan 'tcp contains “Successful” “Correct” “Login”' lalu bisa dilihat apabila terdapat kata-kata tersebut.
bisa terlihat dari paket yang telah tersedia, paket yang berhasil, yaitu 257 - 262. 
```
257	314.639257	::1	::1	FTP	88	Request: USER gedagedigedagedao
260	333.513467	::1	::1	FTP	87	Response: 230 Login successful.
```

- Output result
  Percobaan Filter :
  <img width="1440" alt="Screenshot 2024-09-13 at 13 31 05" src="https://github.com/user-attachments/assets/05d60322-0fc7-4119-a6d4-06efe27264ee">

  Hasil dari jawaban :
  ![WhatsApp Image 2024-09-13 at 10 42 48](https://github.com/user-attachments/assets/7902d4f4-2e42-4d89-8683-191def86370f)

<br>
<br>
