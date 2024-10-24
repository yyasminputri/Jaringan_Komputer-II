[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/99wpTe72)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Rafli Raihan Pramudya  | 5025221266 | Jaringan Komputer A |
| Yasmin Putri Sujono    | 5025221273 | Jaringan Komputer A |

## Put your topology config image here!
<img width="1440" alt="Screenshot 2024-10-04 at 23 20 39" src="https://github.com/user-attachments/assets/a2f75c44-4e9d-4b42-a6d7-c04df595cead">

<br>

## Soal 1

> Topologi terdiri dari node Wortel yang berupa DNS Master*. Selain itu, terdapat pula node Pokcoy sebagai DNS Slave*, yang bertugas sebagai cadangan dari node Wortel.
> <br> </br>
> Selanjutnya terdapat node Tomat dan Taoge yang bekerja sebagai Client*, tiga buah Web Server* yaitu Bayam, Buncis, dan Brokoli, serta Mayur sebagai Router*. Buatlah topologi sesuai dengan pembagian topologi [di sini](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) dan konfigurasi topologi [di sini](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Pastikan bahwa setiap node dapat terhubung ke Internet.

**Answer:**

- Screenshot
<img width="1440" alt="Screenshot 2024-10-04 at 23 20 39" src="https://github.com/user-attachments/assets/a2f75c44-4e9d-4b42-a6d7-c04df595cead">

- Explanation <br>
Pada soal nomor 1, membuat topologi yang sama dengan gambar yang telah diberikan dalam drive.
  - **Pada Node Mayur (Router)** : Berfungsi sebagai router yang menghubungkan semua node di jaringan ini dan juga terhubung ke Internet, dengan IP `10.4.1.1` yang dapat menghubungkan perangkat seperti klien (Tomat dan Taoge) dan web server (Bayam, Buncis, Brokoli) melalui eth1 dan IP `10.4.2.1` dapat menghubungkan perangkat lain yang berada di subnet ini melalui eth2.
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address  10.4.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.4.2.1
	netmask 255.255.255.0

up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.4.0.0/16
```
  - **Pada Node Wortel (DNS Master)** : Bekerja sebagai server DNS utama yang bertugas mengelola dan menyimpan informasi domain, dengan IP `10.4.1.3`.
```
auto eth0
iface eth0 inet static
	address 10.4.1.3
	netmask 255.255.255.0
	gateway 10.4.1.1
```
  - **Pada Node Pokcoy (DNS Slave)** : Bekerja sebagai server DNS sekunder yang berfungsi sebagai cadangan dari node Wortel, dengan IP `10.4.1.2`.
```
auto eth0
iface eth0 inet static
	address 10.4.1.2
	netmask 255.255.255.0
	gateway 10.4.1.1
```
  - **Pada Node Tomat dan Taoge (Client)** : Bekerja dengan melakukan permintaan untuk resolusi nama domain ke server DNS (baik Wortel maupun Pokcoy). Tomat IP `10.4.2.2` dan Tauge IP `10.4.1.4`
Tauge <br>
```
auto eth0
iface eth0 inet static
	address 10.4.1.4
	netmask 255.255.255.0
	gateway 10.4.1.1
```
Tomat <br> 
```
auto eth0
iface eth0 inet static
	address 10.4.2.2
	netmask 255.255.255.0
	gateway 10.4.2.1
```
  - **Pada Web Server (Bayam, Buncis, Brokoli)** : Web server ini dapat terhubung ke node DNS untuk mendapatkan resolusi nama dan dapat diakses oleh klien. Buncis IP `10.4.2.3`, Brokoli `10.4.2.4` dan Bayam IP `10.4.2.5`. <br>
Buncis <br>
```
auto eth0
iface eth0 inet static
	address 10.4.2.3
	netmask 255.255.255.0
	gateway 10.4.2.1
```
Brokoli <br>
```
auto eth0
iface eth0 inet static
	address 10.4.2.4
	netmask 255.255.255.0
	gateway 10.4.2.1
```
Bayam <br>
```
auto eth0
iface eth0 inet static
	address 10.4.2.5
	netmask 255.255.255.0
	gateway 10.4.2.1
```

<br>

## Soal 2

> Menambahkan konfigurasi untuk domain bayam.A03.com yang mengarah ke IP node Bayam `10.4.2.5` di DNS Master. Dengan cara yang sama, buat konfigurasi domain brokoli.A03.com yang mengarah ke IP node Brokoli `10.4.2.4` dan domain buncis.A03.com yang mengarah ke IP node Buncis `10.4.2.3`. Simpan semua konfigurasi dalam folder Jarkom. 
> <br> </br>
> Jangan lupa update konfigurasi kedua client agar dapat berkomunikasi dengan semua domain tersebut.
_

**Answer:**

- Screenshot <br> <br>
**BAYAM** <br>
	- Pada file bayam.A03.com  <br>
  <img width="619" alt="Screenshot 2024-10-05 at 00 33 24" src="https://github.com/user-attachments/assets/7002d6f2-9c52-42e7-8b65-7284cfdc0e7e"> <br>
	- Uji coba <br>
<img width="275" alt="Screenshot 2024-10-05 at 00 33 08" src="https://github.com/user-attachments/assets/24e3138c-c4bb-4b81-9335-507ed6518df8"> <br>

**BROKOLI** <br>
	- Pada file brokoli.A03.com  <br>
<img width="617" alt="Screenshot 2024-10-05 at 00 31 21" src="https://github.com/user-attachments/assets/f4c8c815-da15-4b9b-8770-408f31b980f2"> <br>
	- Uji coba <br>
  <img width="488" alt="Screenshot 2024-10-05 at 00 30 14" src="https://github.com/user-attachments/assets/8b3d7456-348b-4b7d-ba1b-5ca29eb4ac30"> <br>

**BUNCIS**  <br>
	- Pada file brokoli.A03.com <br>
  <img width="627" alt="Screenshot 2024-10-05 at 00 34 19" src="https://github.com/user-attachments/assets/24c7aadc-2112-4f73-8747-a65062450a2a"> <br>
	- Uji coba <br>
<img width="616" alt="Screenshot 2024-10-05 at 00 34 07" src="https://github.com/user-attachments/assets/27105ec1-6578-45db-b05e-6bf01f29d041"> <br>

- Explanation <br>
Langkah-langkah ini menunjukkan mengonfigurasi DNS Server menggunakan BIND9 dan mengatur domain bayam.A03.com, brokoli.A03.com, serta buncis.A03.com yang mengarah ke IP node masing-masing, <br> <br>
**PADA WORTEL** 
1. Melakukan Update dan Instalasi BIND9. <br>
```
apt-get update
apt-get install bind9 -y
```
2. Menyiapkan Konfigurasi Zona di BIND9, pada file **named.conf.local** mengubah dan menambah kode dibawah ini untuk menambahkan tiga zona baru untuk domain bayam.A03.com, brokoli.A03.com, dan buncis.A03.com, masing-masing dengan file zona yang akan disimpan di folder /etc/bind/jarkom/.<br>
```
zone "bayam.A03.com" {
    type master;
    file "/etc/bind/jarkom/bayam.A03.com";
};

zone "brokoli.A03.com" {
    type master;
    file "/etc/bind/jarkom/brokoli.A03.com";
};

zone "buncis.A03.com" {
    type master;
    file "/etc/bind/jarkom/buncis.A03.com";
};
```
3. Membuat Folder dan File Konfigurasi Zona dengan menggunakan **mkdir /etc/bind/jarkom**
<br> Lakukan salinan pada file template zona default db.local ke dalam folder jarkom sebagai file konfigurasi untuk masing-masing domain:
```
cp /etc/bind/db.local /etc/bind/jarkom/bayam.A03.com //untuk bayam
cp /etc/bind/db.local /etc/bind/jarkom/brokoli.A03.com // untuk brokoli
cp /etc/bind/db.local /etc/bind/jarkom/buncis.A03.com // untuk buncis
```
4. Mengedit File Zona untuk Masing-Masing Domain dengan menggunakan **nano /etc/bind/jarkom/XXX.A03.com** <br>
<br> Buncis <br>
 - Mengedit file konfigurasi zona untuk domain buncis.A03.com: `nano /etc/bind/jarkom/buncis.A03.com`
- Ubah isi file :
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     buncis.A03.com. root.buncis.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      buncis.A03.com.
@       IN      A       0.4.2.3 // IP buncis
@       IN      AAAA    ::1
```
<br> Brokoli <br>
- Mengedit file konfigurasi zona untuk domain brokoli.A03.com: `nano /etc/bind/jarkom/brokoli.A03.com`
- Ubah isi file :
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     brokoli.A03.com. root.brokoli.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      brokoli.A03.com.
@       IN      A       0.4.2.4 // IP brokoli
@       IN      AAAA    ::1
```
<br> Bayam <br>
- Mengedit file konfigurasi zona untuk domain bayam.A03.com: `nano /etc/bind/jarkom/bayam.A03.com`
- Ubah isi file :
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     bayam.A03.com. root.bayam.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      bayam.A03.com.
@       IN      A       0.4.2.5 // IP brokoli
@       IN      AAAA    ::1
```
<br>
5. Terakhir, lakukan Restart DNS Server `service bind9 restart` 

<br> **MENCOBA** <br>
Untuk menguji resolusi nama domain
	- Lakukan edit file pada **nano /etc/resolv.conf** mengubah menjadi `nameserver 10.4.1.3 #keWortel` 
 	- Melakukan uji coba dengan perintah ping untuk setiap domain 
```
ping bayam.A03.com 
ping brokoli.A03.com
ping buncis.A03.com
```

<br>

## Soal 3

> Menambahkan domain alias berupa www.bayam.A03.com pada alamat bayam.A03.com dan www.brokoli.A03.com pada alamat brokoli.A03.com dengan mengedit file zona DNS untuk masing-masing domain di server DNS Master (Wortel).

**Answer:**

- Screenshot
**BROKOLI** <br>
	- Pada file brokoli.A03.com, Uji coba <br>
 <img width="615" alt="Screenshot 2024-10-05 at 00 54 12" src="https://github.com/user-attachments/assets/e476d890-8502-4c65-b860-a7cef5607cae"> <br>
**BUNCIS**  <br>
	- Pada file bayam.A03.com, Uji coba <br>
<img width="620" alt="Screenshot 2024-10-05 at 00 53 53" src="https://github.com/user-attachments/assets/8b87e050-9556-4c84-bf41-28b27c4b29bc"> <br>

- Explanation <br> <br>
**PADA BROKOLI** <br> 
- Membuka dan Mengedit File Zona untuk Masing-Masing Domain (bayam dan brokoli) : `nano /etc/bind/jarkom/bayam.A03.com`<br>
- Ubah isi file :
 ```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     bayam.A03.com. root.brokoli.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      bayam.A03.com.
@       IN      A       10.4.2.5
www     IN      CNAME   bayam.A03.com. // Menambah line ini
@       IN      AAAA    ::1
  ```
 **PADA BAYAM** <br>
 - Membuka dan Mengedit File Zona untuk Masing-Masing Domain (bayam dan brokoli) : `nano /etc/bind/jarkom/bayam.A03.com` <br>
- Ubah isi file :
 ```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     bayam.A03.com. root.bayam.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      bayam.A03.com.
@       IN      A       10.4.2.5
www     IN      CNAME   bayam.A03.com. // Menambah line ini
@       IN      AAAA    ::1
  ```
 
<br>

## Soal 4

> Menambahkan reverse domain record pada server DNS untuk domain brokoli.A03.com dan buncis.A03.com dengan membuat file zona reverse lookup (PTR record).

**Answer:**

- Screenshot Hasil 
<img width="622" alt="Screenshot 2024-10-05 at 01 25 44" src="https://github.com/user-attachments/assets/db489f07-82f6-4cce-9a27-bd2f9a794ae3">

- Explanation <br>
**PADA BUNCIS** <br>
1. Menambah Konfigurasi Zona Reverse Lookup 
   	- Membuka dan Mengedit File Zona Reverse Lookup untuk Masing-Masing Domain (buncis dan brokoli) : `nano /etc/bind/named.conf.local`
	- Edit isi file :
```
zone "2.4.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/2.4.10.in-addr.arpa";
};
```

2. Salin Template File Zona Lokal ke Folder jarkom dengan `cp /etc/bind/db.local /etc/bind/jarkom/2.4.10.in-addr.arpa`
	- Ubah isi file :
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     brokoli.A03.com. root.brokoli.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
2.4.10.in-addr.arpa.    IN      NS      brokoli.A03.com.
4                       IN      PTR     brokoli.A03.com.
3                       IN      PTR     buncis.A03.com.
```
<br> 

3. Melakukan `service bind9 restart` untuk merubah penerapan:

<br>

## Soal 5

> Ubah record SOA dari domain bayam.yyy.com sesuai dengan ketentuan berikut:
> - Lama waktu server slave menunggu untuk mengecek salinan baru server master adalah sebesar 2 jam.
> - Field yang mengatur revisi file zona ini diubah menjadi tanggal awal praktikum (format YYYYMMDD) kemudian diikuti dengan nomor kelompok (contoh untuk kelompok A02 maka nomornya 02).
> - Lamanya waktu server harus menunggu untuk meminta pembaruan lagi dari nameserver master yang tidak responsif sebesar 30 menit.
> - Lama waktu nama domain di-cache secara lokal sebelum kadaluarsa dan kembali ke nameserver otoritatif untuk informasi terbaru sebesar 12 jam.
> - Jika server slave tidak mendapatkan respons dari server master dalam waktu 2 minggu, server tersebut harus berhenti merespons kueri untuk zona tersebut.

**Answer:**

- Screenshot
  	- Hasil
<img width="594" alt="Screenshot 2024-10-05 at 01 30 37" src="https://github.com/user-attachments/assets/6e8f241d-605e-4551-ac65-1b258101cd0d">
	- Isi
 <img width="618" alt="Screenshot 2024-10-05 at 01 31 20" src="https://github.com/user-attachments/assets/34499146-8e87-4722-a5c1-c8a9b0f63980">

- Explanation
  1. Membuka File Zona untuk bayam.A03.com dan mengedit Bagian SOA Record pada File Zona
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     bayam.A03.com. root.bayam.A03.com. (
                         2024100103     ; Serial // Mengubah tanggal 1 Oktober 2024
                         7200           ; Refresh // Diubah menjadi 7200 detik (2 jam
                          1800          ; Retry // Diubah menjadi 1800 detik (30 menit)
                        1209600         ; Expire // Diatur menjadi 1209600 detik (2 minggu)
                         43200 )        ; Negative Cache TTL // Diatur menjadi 43200 detik (12 jam).
;
@       IN      NS      bayam.A03.com.
@       IN      A       10.4.2.5
www     IN      CNAME   bayam.A03.com.
@       IN      AAAA    ::1
```
2. Melakukan `service bind9 restart` untuk merubah penerapan

<br>

## Soal 6

> Untuk menangani request yang berlebih dari client ke ketiga alamat yang tadi dibuat, konfigurasikan node Pokcoy sebagai DNS Slave yang bekerja untuk DNS Master Wortel.

**Answer:**

- Screenshot Hasil
<img width="362" alt="Screenshot 2024-10-05 at 01 43 51" src="https://github.com/user-attachments/assets/20a275fa-a10d-45a7-85d8-eeb1046053af">


- Explanation <br>
**PADA WORTEL** <br>
1.Menambah konfigurasi zona untuk ketiga domain.
   	- Membuka dan Mengedit File Zona Reverse Lookup untuk Masing-Masing Domain (buncis, bayam dan brokoli) : `nano /etc/bind/named.conf.local`
	- Edit isi file :
```
zone "bayam.A03.com" {
    type master;
    notify yes;
    also-notify { 10.4.1.2; };
    allow-transfer { 10.4.1.2; };
    file "/etc/bind/jarkom/bayam.A03.com";
};

// Zona untuk domain brokoli.A03.com
zone "brokoli.A03.com" {
    type master;
    notify yes;
    also-notify { 10.4.1.2; };
    allow-transfer { 10.4.1.2; };
    file "/etc/bind/jarkom/brokoli.A03.com";
};

// Zona untuk domain buncis.A03.com
zone "buncis.A03.com" {
    type master;
    notify yes;
    also-notify { 10.4.1.2; };
    allow-transfer { 10.4.1.2; };
    file "/etc/bind/jarkom/buncis.A03.com";
};
```
2. `service bind9 stop` untuk menghentikan layanan bind9 pada server DNS.

**PADA POCKOY** <br>
1.Melakukan Update dan Instalasi BIND9. <br>
```
apt-get update
apt-get install bind9 -y
```
2. Menambahkan definisi zona DNS Slave untuk setiap domain:
```
// Zona Slave untuk domain bayam.A03.com
zone "bayam.A03.com" {
    type slave;
    file "/var/lib/bind/bayam.A03.com";   // Lokasi file cache zona Slave
    masters { 10.4.1.3; };                     // IP DNS Master (Wortel)
};

// Zona Slave untuk domain brokoli.A03.com
zone "brokoli.A03.com" {
    type slave;
    file "/var/lib/bind/brokoli.A03.com"; // Lokasi file cache zona Slave
    masters { 10.4.1.3; };                     // IP DNS Master (Wortel)
};

// Zona Slave untuk domain buncis.A03.com
zone "buncis.A03.com" {
    type slave;
    file "/var/lib/bind/buncis.A03.com";  // Lokasi file cache zona Slave
    masters { 10.4.1.3; };                     // IP DNS Master (Wortel)
};
```
4. Melakukan `service bind9 restart` untuk merubah penerapan:

**MENCOBA**
1. Melakukan pengeditan pada webserver atau client dengan `nano /etc/resolv.conf` rubahlah agar menjadi 
```
nameserver 10.4.1.3
nameserver 10.4.1.2
```
2. Lalu, lakukan uji coba dengan perintah ping XXX.A03.com

<br>

## Soal 7

> Karena membutuhkan tempat untuk menyimpan resep brokoli, buatlah subdomain berupa vitamin.brokoli.A03.com dengan alias www.vitamin.brokoli.yyy.com dengan mendelegasikannya dari Wortel ke Pokcoy dengan alamat IP menuju Brokoli yang diatur di folder Vitamin.

**Answer:**

- Screenshot
  - Isi
<img width="626" alt="Screenshot 2024-10-05 at 02 00 26" src="https://github.com/user-attachments/assets/72957220-9df5-40da-ab79-65efc147ebe5"> <br> 
- Hasil
  <img width="618" alt="Screenshot 2024-10-05 at 02 03 03" src="https://github.com/user-attachments/assets/3e83b39e-ae15-4282-a225-a6da3a53ae92"> <br> 

- Explanation <br> 
Konfigurasi di file named.conf.local untuk subdomain vitamin.brokoli.A03.com:
**PADA WORTEL**
1. Mengedit File Konfigurasi Subdomain pada brokoli.A03.com
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     brokoli.A03.com. root.brokoli.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@              IN      NS      brokoli.A03.com.
@              IN      A       10.4.1.3 
www            IN     CNAME    brokoli.A03.com.
nsl            IN      A       10.4.1.2
vitamin        IN      NS      nsl
@              IN      AAAA    ::1
```
2. Kemudian edit file `/etc/bind/named.conf.options` pada Wortel. Lakukan, comment pada dnssec-validation auto; dan tambahkan baris allow-query{any;};
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable
    // nameservers, you probably want to use them as forwarders.
    // Uncomment the following block, and insert the addresses replacing
    // the all-0's placeholder.        
    // forwarders {
    //      0.0.0.0;
    // };

    //======================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //======================================================================
    //dnssec-validation auto;
    allow-query { any; };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```
3. Melakukan `service bind9 restart` untuk merubah penerapan

**PADA POCKOY**
1. Membuat entry untuk zona baru dengan tipe master dan arahkan ke file zona di folder /etc/bind/vitamin/ dengan `nano named.conf.local`
```
zone "vitamin.brokoli.A03.com" {
    type master;
    file "/etc/bind/vitamin/vitamin.brokoli.A03.com"; // Lokasi file cache zon};
};
``` 
2. Membuat folder /etc/bind/vitamin untuk menyimpan file zona subdomain menggunakan `mkdir -p /etc/bind/vitamin`
3.. Salin template file zona default dari db.local dan modifikasi sesuai dengan domain vitamin.brokoli.A03.com.
Di dalam file zona, tambahkan entri A record untuk mengarahkan subdomain ke IP Brokoli dan buat CNAME untuk alias www.vitamin.brokoli.A03.com.
```
cp /etc/bind/db.local /etc/bind/vitamin/vitamin.brokoli.A03.com // melakukan salinan file 

cat > /etc/bind/vitamin/vitamin.brokoli.A03.com << EOF
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     vitamin.brokoli.A03.com. root.vitamin.brokoli.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      vitamin.brokoli.A03.com.
@       IN      A       10.4.1.2
www     IN      A       10.4.1.2
EOF
```

5. Kemudian edit file `/etc/bind/named.conf.options` pada Wortel. Lakukan, comment pada dnssec-validation auto; dan tambahkan baris allow-query{any;};
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable
    // nameservers, you probably want to use them as forwarders.
    // Uncomment the following block, and insert the addresses replacing
    // the all-0's placeholder.        
    // forwarders {
    //      0.0.0.0;
    // };

    //======================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //======================================================================
    //dnssec-validation auto;
    allow-query { any; };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```
5. Restart BIND9 untuk menerapkan perubahan dengan `service bind9 restart`


<br>

## Soal 8

> Buatlah subdomain khusus untuk kandungan brokoli dengan akses k1.vitamin.brokoli.yyy.com dengan alias www.k1.vitamin.brokoli.yyy.com yang mengarah ke IP brokoli dan diatur di folder k1.  

**Answer:**

- Screenshot
- Hasil 
<img width="558" alt="Screenshot 2024-10-05 at 02 11 06" src="https://github.com/user-attachments/assets/5f309b68-ce5e-414a-8b95-8028b9e42246">
- Isi
<img width="559" alt="Screenshot 2024-10-05 at 02 11 24" src="https://github.com/user-attachments/assets/f930fcaf-8a20-4486-a97b-2c8f6b140f25">

- Explanation
**PADA POKCOY**
1. Menambahkan zona baru di named.conf.local untuk k1.vitamin.brokoli.A03.com.
```
...

zone "k1.vitamin.brokoli.A03.com" {
    type master;
    file "/etc/bind/k1/k1.vitamin.brokoli.A03.com"; // Lokasi file cache zon
};
```
2. Buat folder /etc/bind/k1 dan salin file zona dari template db.local.
   membuat folder menggunakan `mkdir -p /etc/bind/k1` dan menyalin menggunakan `cp /etc/bind/db.local /etc/bind/k1/k1.vitamin.brokoli.A03.com` 
3. Di dalam file zona, tambahkan A record untuk subdomain k1.vitamin.brokoli.A03.com dan CNAME untuk alias www.k1.vitamin.brokoli.A03.com yang diarahkan ke IP Brokoli.
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     localhost. root.k1.vitamin.brokoli.A03.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      k1.vitamin.brokoli.A03.com.
@       IN      A       10.4.1.2
www     IN      CNAME   k1.vitamin.brokoli.A03.com.
k1      IN      A       10.4.2.4
@       IN      AAAA    ::1
```
4. Restart BIND9 untuk memulai konfigurasi. 

<br>

## Soal 9

> Bayam, Brokoli, dan Buncis masing-masing berfungsi sebagai web server nginx yang menyajikan resep khusus untuk jenis sayuran yang mereka tangani. Untuk mengaktifkan web server pada masing-masing worker, lakukan deployment website menggunakan sumber yang tersedia di sayur_webserver_nginx. Tambahkan konfigurasi untuk log error ke file /var/log/nginx/error.log dan log access ke file /var/log/nginx/access.log.

**Answer:**

- Screenshot <br>
**BUNCIS** <br>
<img width="341" alt="Screenshot 2024-10-05 at 02 26 59" src="https://github.com/user-attachments/assets/c83ae0f8-dc2c-49d7-b3cc-05f58c467c9c"> <br>
**BROKOLI** <br>
<img width="316" alt="Screenshot 2024-10-05 at 02 27 57" src="https://github.com/user-attachments/assets/2573195a-92be-42e7-a56b-a5cd5b534bfb"> <br>
**BAYAM** <br>
<img width="336" alt="Screenshot 2024-10-05 at 02 27 45" src="https://github.com/user-attachments/assets/6db83425-ea68-49ce-87f3-58ef80aa1e92"> <br>
**MENCOBA**
<img width="424" alt="Screenshot 2024-10-05 at 02 28 46" src="https://github.com/user-attachments/assets/36d0016a-b64a-4bf0-87dd-2eec65c936c2"> <br>

- Explanation
1. Install Nginx dan PHP pada setiap server worker (Bayam, Brokoli, Buncis).
```
apt-get update
apt-get install nginx
apt-get install php 
apt-get install php7.2-fpm
```
2. Membuat Folder jarkom terlebih dahulu `mkdir -p /var/www/jarkom`
3. Setup direktori web server di /var/www/jarkom dan salin file PHP yang telah diberikan yang berisi resep sesuai dengan sayuran yang di-handle oleh setiap worker. 
- Membuat File Index.php menggunakan `nano index.php`
```
<?php
\$hostname = gethostname();
\$date = date('l, d F Y H:i:s');
\$php_version = phpversion();
\$visitor_ip = \$_SERVER['REMOTE_ADDR'];

echo "<h1>Selamat Datang di Situs Resep Sayuran!</h1>";
echo "<p>Pengunjung dari IP: <strong>\$visitor_ip</strong></p>";
echo "<p>Versi PHP: <strong>\$php_version</strong></p>";
echo "<p>Waktu: <strong>\$date</strong></p>";
echo "<hr>";
echo "<p>Saat ini Anda sedang mengakses resep dari sayur: <strong>\$hostname</strong></p>";

switch (\$hostname) {
    case 'BayamWebServer': //diganti ke masing-masing webserver
        if (!@include 'resep_1.php') {
            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
            error_log("File resep1.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        }
        break;
    case 'BuncisWebServer': //diganti ke masing-masing webserver
        if (!@include 'resep_2.php') {
            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
            error_log("File resep2.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        }
        break;
    case 'BrokoliWebServer': //diganti ke masing-masing webserver
        if (!@include 'resep_3.php') {
            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
            error_log("File resep3.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        }
        break;
    default:
        echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
        error_log("Hostname tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        break;
}
?>
```
- Membuat File resep1.php menggunakan `nano resep1.php`
```
cat > /var/www/jarkom/resep1.php << EOF
<?php
echo "<h2>Resep Spesial: Tumis Bayam Bawang Putih</h2>";
echo "<p>Bahan:</p>";
echo "<ul>";
echo "<li>Bayam segar 200 gram</li>";
echo "<li>Bawang putih 3 siung</li>";
echo "<li>Garam dan merica secukupnya</li>";
echo "<li>Minyak untuk menumis</li>";
echo "</ul>";
echo "<p>Cara Memasak:</p>";
echo "<ol>";
echo "<li>Cuci bersih bayam dan tiriskan.</li>";
echo "<li>Iris tipis bawang putih.</li>";
echo "<li>Tumis bawang putih hingga harum.</li>";
echo "<li>Masukkan bayam, aduk hingga layu.</li>";
echo "<li>Bumbui dengan garam dan merica.</li>";
echo "<li>Sajikan selagi hangat.</li>";
echo "</ol>";
?>
EOF
```
4. Buatlah juga file untuk resep2.php dan resep3.php 
5. Menambahkan file jarkom pada /etc/nginx/sites-available menyesuaikan webserver yang ingin dipakai dan sedang dipakai. Apabila berada pada BrokoliWebserver maka diganti server_name ke brokoli.A03.com dan www.brokoli.A03.com. 
```
server {

        listen 80;

        root /var/www/jarkom;

        index index.php index.html index.htm;
        server_name XXX.A03.com www.XXX.A03.com; //diganti ke sayuran webserver 

        location / {
                        try_files $uri $uri/ /index.php?$query_string;
        }

        # pass PHP scripts to FastCGI server
        location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        }
location ~ /\.ht {
                        deny all;
        }

        error_log /var/log/nginx/jarkom_error.log;
        access_log /var/log/nginx/jarkom_access.log;
}
```
6. Membuat link simbolik dari file konfigurasi yang ada di sites-available ke sites-enabled `ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled`
7. Me-restart layanan Nginx setelah membuat atau mengubah konfigurasi dengan `service nginx restart`
8. Memeriksa konfigurasi Nginx sebelum di-restart menggunakan `nginx -t`
9. Memulai layanan PHP-FPM `service php7.2-fpm start`
    
**MENCOBA**
1. lynx brokoli.A03.com atau lynx www.brokoli.A03.com

<br>

## Soal 10

> Pada masing masing worker nginx, akan terdapat beberapa hal yang perlu diperbaiki pada resource yang diberikan untuk bisa menampilkan resep saat halaman dimuat. Analisis kesalahan yang ada di resource melalui file /var/log/nginx/error.log dan perbaiki hingga halaman bisa menampilkan resep sesuai dengan worker nya.

-

**Answer:**

- Screenshot<br>
**BUNCIS** <br>
<img width="235" alt="Screenshot 2024-10-05 at 02 36 10" src="https://github.com/user-attachments/assets/ceba38c9-964b-4c96-ad23-57623894ce7c"><br>
**BROKOLI** <br>
<img width="279" alt="Screenshot 2024-10-05 at 02 36 36" src="https://github.com/user-attachments/assets/8a6c2a49-3eee-4c25-9e1b-5ed511938ac9"> <br>
**BAYAM** <br>
<img width="326" alt="Screenshot 2024-10-05 at 02 37 09" src="https://github.com/user-attachments/assets/219fbee0-ff1a-4efb-a678-9cbc138e6686"><br>
**MENCOBA** <br>
<img width="362" alt="Screenshot 2024-10-05 at 02 37 25" src="https://github.com/user-attachments/assets/e271d96c-3be0-4451-867c-835b849afa34"><br>

- Explanation
1. Merubah pada index.php yang berada pada /var/www/jarkom
```
<?php
$hostname = gethostname();
$date = date('l, d F Y H:i:s');
$php_version = phpversion();
$visitor_ip = $_SERVER['REMOTE_ADDR'];

echo "<h1>Selamat Datang di Situs Resep Sayuran!</h1>";
echo "<p>Pengunjung dari IP: <strong>$visitor_ip</strong></p>";
echo "<p>Versi PHP: <strong>$php_version</strong></p>";
echo "<p>Waktu: <strong>$date</strong></p>";
echo "<hr>";
echo "<p>Saat ini Anda sedang mengakses resep dari sayur: <strong>$hostname</strong></p>";

switch ($hostname) {
    case 'BayamWebServer': //diganti ke masing-masing webserver
        if (!@include 'resep1.php') {
            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
            error_log("File resep1.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        }
        break;
    case 'BuncisWebServer': //diganti ke masing-masing webserver
        if (!@include 'resep2.php') {
            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
            error_log("File resep2.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        }
        break;
    case 'BrokoliWebServer': //diganti ke masing-masing webserver
        if (!@include 'resep3.php') {
            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
            error_log("File resep3.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        }
        break;
       default:
        echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
        error_log("Hostname tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
        break;
}
?>
```
3. Restart Nginx setelah melakukan perbaikan menggunakan `service nginx restart`
   
**MENCOBA** <br>
1. lynx XXX.A03.com atau lynx www.XXX.A03.com
   
<br>

## Soal 11

> Setelah website berhasil dideploy pada masing-masing worker (Bayam, Brokoli, dan Buncis) dan halaman dapat menampilkan resep sayuran yang sesuai,  buatlah custom access log ke file /var/log/nginx/access.log di masing-masing web server worker menggunakan format log tertentu seperti di bawah:
> - Tanggal dan waktu akses dalam format standar log.
Nama worker yang sedang dilayani (misalnya: Bayam, Brokoli, atau Buncis).
> - Alamat IP klien yang mengakses website.
> - Metode HTTP dan URI yang diakses oleh klien.
> - Status respons HTTP yang diberikan oleh server.
> - Jumlah byte yang dikirimkan dalam respons.
> - Waktu yang dihabiskan oleh server untuk menangani permintaan.
> <br> </br>


**Answer:**

- Screenshot
  **BROKOLI** <br>
<img width="628" alt="Screenshot 2024-10-05 at 02 47 58" src="https://github.com/user-attachments/assets/cde2a5ae-f8d1-42db-93f2-30c04f417703"> <br>
  **BAYAM** <br>
  <img width="626" alt="Screenshot 2024-10-05 at 02 48 34" src="https://github.com/user-attachments/assets/eac52a0d-3791-437b-840e-5d42f2e2dac7"> <br>
  **BUNCIS** <br>
<img width="625" alt="Screenshot 2024-10-05 at 02 48 51" src="https://github.com/user-attachments/assets/3a4858dc-6ba7-4ada-af04-ebf4b42ba530"> <br>

- Explanation <br>
1. Melakukan penambahan pada file jarkom yang berada pada /etc/nginx/sites-available <br>
```
# Definisikan format custom log
    log_format custom_format '[$time_local] Jarkom Node $server_name Access from $remote_addr using method "$request" '
                             'returned status $status with $body_bytes_sent bytes sent in $request_time seconds';

server {

        listen 80;

        root /var/www/jarkom;

        index index.php index.html index.htm;
        server_name brokoli.A03.com www.brokoli.A03.com;

        location / {
                        try_files $uri $uri/ /index.php?$query_string;
        }

        # pass PHP scripts to FastCGI server
        location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        }
location ~ /\.ht {
                        deny all;
        }

        error_log /var/log/nginx/jarkom_error.log;
        access_log /var/log/nginx/jarkom_access.log custom_format; //menambah custom_format
}
```
2. Restart Nginx untuk melakukan penambahan menggunakan `service nginx restart`
4. Lakukan pada Client untuk mengakses website www.brokoli.A03.com menggunakan lynx.
5. Lalu melakukan `cat jarkom_access.log` pada /var/log/nginx. Log ini berfungsi untuk mencatat semua permintaan (request) yang diterima oleh server. Melalui log ini, Anda bisa memantau aktivitas pengguna dan mendeteksi jika ada masalah dalam akses ke situs.
   
<br>

## Soal 12

> Informasi vitamin pada sayur brokoli akan ditampilkan pada subdomain vitamin.brokoli.yyy.com di node brokoli, buatlah DocumentRoot yang disimpan pada /var/www/vitamin.brokoli.yyy. Konfigurasikan webserver dengan nama server vitamin.brokoli.yyy.com dan server alias www.vitamin.brokoli.yyy.com. Lakukan konfigurasi Apache Web Server pada Brokoli dengan menggunakan sumber yang tersedia di [sini](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2).

**Answer:**

- Screenshot <br>
<img width="628" alt="Screenshot 2024-10-05 at 02 49 40" src="https://github.com/user-attachments/assets/518da9b9-8155-457d-8dc5-bea4fb5e751c"> <br>

- Explanation <br>
**PADA BROKOLI**
1. Mengunduh File ZIP `wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1NhsaTLD4Zk06BZJCqdN_oqoxB3uIg2C7' -O sayur_webserver_nginx.zip`
2. Mengekstrak isi file ZIP ke dalam direktori baru bernama sayur_webserver_nginx `unzip -o sayur_webserver_nginx.zip -d sayur_webserver_nginx`
3. Membuat direktori /var/www/vitamin.brokoli.A03 `mkdir -p /var/www/vitamin.brokoli.A03`
4. Menyalin semua isi dari direktori sayur_webserver_nginx ke direktori /var/www/vitamin.brokoli.A03/ `cp -r sayur_webserver_nginx/* /var/www/vitamin.brokoli.A03/`
5. Masuk ke direktori /etc/apache2/sites-available/ lakukan nano vitamin.brokoli.A03.com.conf untuk membuat file baru.
```
<VirtualHost *:80>
    ServerAdmin admin@vitamin.brokoli.A03.com
    ServerName vitamin.brokoli.A03.com
    ServerAlias www.vitamin.brokoli.A03.com

    DocumentRoot /var/www/vitamin.brokoli.A03

    ErrorLog ${APACHE_LOG_DIR}/vitamin.brokoli.A03.error.log
    CustomLog ${APACHE_LOG_DIR}/vitamin.brokoli.A03.access.log combined

    <Directory /var/www/vitamin.brokoli.a02>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
7. Lalu gunakan `a2ensite vitamin.brokoli.A03.com.conf` untuk mengaktifkan konfigurasi situs di apache
8. Lalu lakukan `service apache2 restart` Untuk menerapkan perubahan setelah mengaktifkan situs.

<br>

## Soal 13

> Pada subdomain vitamin.brokoli.yyy.com, terdapat subfolder /nutrisi yang menyediakan informasi tentang berbagai vitamin dalam brokoli, seperti Vitamin A, C, dan K. Aktifkan directory listing untuk folder /nutrisi, dan buatlah rewrite rule di Apache untuk memperbaiki URL agar halaman seperti www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php dapat diakses hanya dengan www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Pastikan setiap halaman vitamin dapat diakses langsung melalui url yang telah disederhanakan.

**Answer:**

- Screenshot
- Hasil 
<img width="623" alt="Screenshot 2024-10-05 at 02 57 54" src="https://github.com/user-attachments/assets/9783ce18-141c-4774-86e3-1733139bdd0f"><br>
<img width="552" alt="Screenshot 2024-10-05 at 02 58 21" src="https://github.com/user-attachments/assets/e2bb3ae4-8f64-41dd-a338-3e4c8fda8f2f"><br>

- Explanation
1. Mengaktifkan Directory Listing di Folder 
2. Rewrite Rule untuk Penyederhanaan URL
   - RewriteEngine On mengaktifkan modul URL Rewrite.
   - RewriteCond %{REQUEST_FILENAME} !-f dan RewriteCond %{REQUEST_FILENAME} !-d memastikan URL hanya diubah jika file atau direktori yang diminta tidak ada.
   - RewriteRule ^([a-zA-Z0-9_-]+)$ /nutrisi/$1.php [L] mengubah URL seperti www.vitamin.brokoli.A03.com/nutrisi/vitamin_a agar diarahkan ke file PHP vitamin_a.php tanpa pengguna perlu menuliskan ekstensi .php.
```
<Directory /var/www/vitamin.brokoli.A03/nutrisi>
    Options +FollowSymLinks -Multiviews
    AllowOverride All
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^([^\.]+)$ $1•php [NC, L]
</Directory>
```

<br>

## Soal 14

> Tambahkan alias untuk folder /public/images/ pada subdomain www.vitamin.brokoli.yyy.com agar folder tersebut dapat diakses langsung melalui url www.vitamin.brokoli.yyy.com/img.

**Answer:**

- Screenshot
- Hasil</br>
<img width="619" alt="Screenshot 2024-10-05 at 02 58 58" src="https://github.com/user-attachments/assets/85e33f58-ed44-47f0-a9d8-9fda62cc0946"><br>
<img width="623" alt="Screenshot 2024-10-05 at 02 59 10" src="https://github.com/user-attachments/assets/fe57499c-b04b-4a85-895b-bce434eb96bf"><br>

- Explanation </br>
1. Pada folder publik (/public/images), Options +Indexes memungkinkan listing file, misalnya untuk memudahkan akses file statis (seperti gambar atau file JavaScript).
- Alias "/img" "/var/www/vitamin.brokoli.A03/public/images": Membuat alias untuk folder /public/images sehingga bisa diakses melalui URL yang lebih pendek, yaitu www.vitamin.brokoli.A03.com/img. Pengguna tidak perlu lagi mengakses folder melalui path asli yang lebih panjang.
```
ServerAdmin webmaster@localhost
DocumentRoot /var/www/vitamin.brokoli.A03
ServerName vitamin.brokoli.A03.com
ServerAlias www.vitamin.brokoli.A03.com

# Alias untuk folder /public/images agar dapat diakses melalui /img
Alias "/img" "/var/www/vitamin.brokoli.A03/public/images"

<Directory /var/www/vitamin.brokoli.A03/public/images>
    Options +Indexes
</Directory
```

<br>

## Soal 15

> Karena terdapat resep rahasia di file /secret/recipe_secret.txt pada subdomain www.vitamin.brokoli.A03.com, konfigurasikan folder /secret agar tidak dapat diakses oleh pengguna (dengan menampilkan 403 Forbidden).

**Answer:**

- Screenshot Hasil <br>
  <img width="617" alt="Screenshot 2024-10-05 at 02 59 27" src="https://github.com/user-attachments/assets/25762e84-374b-490f-ab97-c339b8ebbdc2"> <br>
  <img width="530" alt="Screenshot 2024-10-05 at 02 59 59" src="https://github.com/user-attachments/assets/401b62e1-2179-4d29-9828-8bb0fd9d390f"> <br>

- Explanation </br>
Menggunakan aturan yang membatasi akses untuk mengonfigurasi folder /secret/ agar tidak dapat diakses oleh pengguna dan menampilkan 403 Forbidden.
```
<Directory /var/www/vitamin.brokoli.A03/secret>
    Options -Indexes
</Directory>
```

<br>

## Soal 16

> Karena dinilai terlalu panjang coba ubah konfigurasi www.vitamin.brokoli.A03.com/public/js menjadi www.vitamin.brokoli.A03.com/js

**Answer:**

- Screenshot Hasil <br>
<img width="622" alt="Screenshot 2024-10-05 at 03 00 23" src="https://github.com/user-attachments/assets/2951c643-c368-4880-bfcb-9fe893cf1deb"> <br>
<img width="624" alt="Screenshot 2024-10-05 at 03 00 38" src="https://github.com/user-attachments/assets/c3515887-688f-402e-9179-f2f1dde94617"> <br>

- Explanation </br>
Menambahkan alias untuk mengubah akses folder /public/js agar dapat diakses melalui URL yang lebih pendek, yaitu www.vitamin.brokoli.A03.com/js
```
# Alias untuk folder /public/js agar dapat diakses melalui /js
Alias "/js" "/var/www/vitamin.brokoli.A03/public/js"

<Directory /path/to/your/project/public/js>
    Options +Indexes
</Directory>
```

<br>

## Soal 17

> Supaya Web kita aman terkendali maka ubah konfigurasi www.k1.vitamin.brokoli.A03.com menjadi hanya bisa di akses oleh port 9696 dan 8888

**Answer:**

- Screenshot <br>
<img width="716" alt="Screenshot 2024-10-05 at 04 17 46" src="https://github.com/user-attachments/assets/fc0a6c06-7855-4b43-a9e1-52df2819a0a2"> <br>

- Explanation
1. Mengedit File Virtual Host Apache dengan menyesuaikan konfigurasi virtual host untuk subdomain www.k1.vitamin.brokoli.A03.com, lakukan `sudo nano /etc/apache2/sites-available/k1.vitamin.brokoli.A03.com.conf` untuknya. 
```
<VirtualHost *:9696>
    ServerName www.k1.vitamin.brokoli.A03.com
    DocumentRoot /var/www/www.k1.vitamin.brokoli.A03.com
    
    ErrorLog ${APACHE_LOG_DIR}/k1.vitamin.brokoli.A03.com.error.log
    CustomLog ${APACHE_LOG_DIR}/k1.vitamin.brokoli.A03.com.access.log combined
</VirtualHost>

<VirtualHost *:8888>
    ServerName www.k1.vitamin.brokoli.A03.com
    DocumentRoot /var/www/www.k1.vitamin.brokoli.A03.com
    
    ErrorLog ${APACHE_LOG_DIR}/k1.vitamin.brokoli.A03.com.error.log
    CustomLog ${APACHE_LOG_DIR}/k1.vitamin.brokoli.A03.com.access.log combined
</VirtualHost>
```
2. Mengaktifkan Port yang Diperlukan
```
Listen 9696
Listen 8888
```
3. Lakukan Restart Apache menggunakan `service apache2 restart`

**TESTING**
```
http://www.k1.vitamin.brokoli.yyy.com:9696
http://www.k1.vitamin.brokoli.yyy.com:8888
```


<br>

## Soal 18

> Lanjutkan dari nomor sebelumnya buatlah autentikasi dengan username “Seblak” dan password “sehatyyy” dengan yyy adalah kode kelompok. Letakkan Document Root pada /var/www/k1.vitamin.brokoli.yyy.

> _Continuing from the previous point, create authentication with the username “Seblak” and the password “sehatyyy” where yyy is the group code. Set the Document Root to /var/www/k1.vitamin.brokoli.yyy._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 19

> Konfigurasikan agar setiap kali IP Brokoli diakses dengan lynx, secara otomatis akan dialihkan ke www.brokoli.yyy.com (alias).

> _Configure it so that every time Brokoli's IP is accessed using lynx, it is automatically redirected to www.brokoli.yyy.com (alias)._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 20

> Karena jumlah pengunjung website www.vitamin.brokoli.yyy.com semakin meningkat dan terdapat banyak gambar random, ubah permintaan gambar yang mengandung substring "vitamin" agar diarahkan ke file vitamin.png.

> _Since the number of visitors to www.vitamin.brokoli.yyy.com is increasing and there are many random images, redirect image requests that contain the substring "vitamin" to the file vitamin.png._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Explanation

  `Put your explanation in here`

<br>
  
## Problems
GNS ANEHH, aku bikin script 7-8 gabisa, tapi kalo dimasukin satu2 bisa WHY!!?? kan lelah
## Revisions (if any)
