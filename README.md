# Jarkom-A03

## NO.1 
sebelum memulai soal, connect ke server melalui nc dengan nc yang diberikan. 
- Berapa banyak packet yang terekam pada file pcapng?
> 1089 (packets)
  Dapat dilihat dibawah dengan tulisan 'packet :'
  <img width="156" alt="Screenshot 2024-09-11 at 22 38 08" src="https://github.com/user-attachments/assets/067b0d0d-6f4e-4851-b7e6-750ef3b335d2">

- Ada berapa jenis protocol yang terekam pada traffic?
> 4 (protocol).
  Dapat dilihat dari table **protocol**

- sebutkan secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator dan dalam bentuk uppercase. contoh: PROTOCOL1,PROTOCOL2
> HTTP,MDNS,SSDP,TCP (Lihat pada bagian **protocol** telah disebutkan pada bagian 'protocol')

  <img width="76" alt="Screenshot 2024-09-11 at 22 38 33" src="https://github.com/user-attachments/assets/d2c3f086-f0d9-4bc8-8cc1-d5bdbfda7ba1">

### Jawaban
![WhatsApp Image 2024-09-11 at 18 56 14](https://github.com/user-attachments/assets/f96a675a-8596-44a8-a839-eff072696fc8)
flag : JARKOM24{K4mu_K3r3n_0CHM7NFTA4ZTT7VW9HNWP3VVXURUF50xL4ughafj1pkt52dgrn1hlocj7aa3}

## NO. 2
- Berapa banyak packet berbasis TCP yang memiliki flag [RST, ACK]?
> 411 

Berapa banyak packet berbasis TCP yang hanya memiliki flag [SYN]?
> 412

Berapa banyak packet berbasis TCP yang memiliki flag ack, tapi tidak memiliki syn, dan tidak memiliki rst
> 217

## NO. 3
- Pada port berapa server http terbuka?
> 9282
- Berapa byte file response yang dikirim dari server?
> 427
- Berapa jumlah file yang terdapat pada server?
> 4
TCP contains “file” kalo ditanya isi bisa follow klik kanan.
- sebutkan nama file secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator, contoh: file1,file2
> file.pdf,hello.html,lion.jpg,present.pptx

## NO. 4
Protokol apa yang paling banyak terdapat di file hasil capture traffic?
> FTP

## NO. 5 
Berdasarkan hasil bruteforce, apa user yang tepat dari hasil bruteforce?
> gedagedigedagedao




