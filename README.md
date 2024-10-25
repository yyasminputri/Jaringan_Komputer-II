[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1zoHyFGp)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Rafli Raihan Pramudya | 5025221266 | Jaringan Komputer A |
| Yasmin Putri Sujono | 5025221273 | Jaringan Komputer A |

## Put your topology config image here!
<img width="880" alt="Screenshot 2024-10-23 at 01 44 06" src="https://github.com/user-attachments/assets/7fff8f4b-bec5-4813-afdc-ac57dbaf7596">

<br>

> Template testing report: https://docs.google.com/document/d/17T0fsnh_4zZTrG-lELDJ88intrc9mkwCzZ_s-23JLCc/edit?usp=sharing

## Put your testing report here! 
> The report is sent in PDF format, uploaded to Drive, and set to public view.

`put the link here`

## Soal 0

> Pada perlombaan akhir tahun kali ini, semua worker dan client ikut serta di dalamnya sebagai perwakilan dari masing-masing asrama. Persiapan yang dilakukan untuk perlombaan ini adalah dengan setup semua network configuration yang sesuai dengan tabel peran diatas. Khusus untuk client menggunakan konfigurasi dari DHCP Server.

**Answer**

- Dumbledore:

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

    auto eth3
    iface eth3 inet static
	  address 10.4.3.1
	  netmask 255.255.255.0

    auto eth4
    iface eth4 inet static
	  address 10.4.4.1
	  netmask 255.255.255.0

    auto eth5
    iface eth5 inet static
	  address 10.4.5.1
	  netmask 255.255.255.0

    auto eth6
    iface eth6 inet static
	  address 10.4.6.1
	  netmask 255.255.255.0
  
    up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.4.0.0/16
  ```

- SeverusSnape:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.3.2
	netmask 255.255.255.0
	gateway 10.4.3.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- McGonagall:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.3.3
	netmask 255.255.255.0
	gateway 10.4.3.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- Hagrid:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.4.2
	netmask 255.255.255.0
	gateway 10.4.4.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- Voldemort:

  ```
   auto eth0
  iface eth0 inet static
	address 10.4.4.3
	netmask 255.255.255.0
	gateway 10.4.4.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- Dementor:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.4.4
	netmask 255.255.255.0
	gateway 10.4.4.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- HarryPotter:

  ```
    auto eth0
    iface eth0 inet static
  	address 10.4.1.2
  	netmask 255.255.255.0
  	gateway 10.4.1.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- RonWeasley:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.1.3
	netmask 255.255.255.0
	gateway 10.4.1.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- HermioneGranger:

  ```
    auto eth0
    iface eth0 inet static
  	address 10.4.1.4	
    netmask 255.255.255.0
	  gateway 10.4.1.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- LunaLovegood:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.6.4
	netmask 255.255.255.0
	gateway 10.4.6.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- FiliusFlitwick:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.6.3
	netmask 255.255.255.0
	gateway 10.4.6.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- ChoChang:

  ```
  auto eth0
  iface eth0 inet static
	address 10.4.6.2
	netmask 255.255.255.0
	gateway 10.4.6.1

  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- DracoMalfoy:

  ```
  auto eth0 
  iface eth0 inet dhcp
  ```

- AstoriaGreengrass:

  ```
  auto eth0 
  iface eth0 inet dhcp
  ```

- SusanBones:

  ```
  auto eth0 
  iface eth0 inet dhcp
  ```

- HannahAbbott:

  ```
  auto eth0 
  iface eth0 inet dhcp
  ```

## Soal 1

> Melakukan registrasi subdomain untuk PHP worker bernama gryffindor.hogwarts.A03.com yang mengarah ke alamat IP load balancer Voldemort dan untuk laravel worker bernama ravenclaw.hogwarts.A03.com yang mengarah ke alamat IP load balancer Dementor. Seluruh domain ini berkumpul dalam suatu ruang atau folder bernama hogwarts

**Answer:**

- Screenshot 
<img width="652" alt="Screenshot 2024-10-23 at 02 08 31" src="https://github.com/user-attachments/assets/75407503-3444-43aa-aff7-bb4dea02b41b">

- Configuration

1. Pertama, menentukan nameserver dan memperbarui paket dan menginstal BIND9
```
echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update
apt-get install bind9 -y
```

2. Menkonfigurasi Zona DNS dengan membuat file konfigurasi lokal untuk zona gryffindor.hogwarts.A03.com dan ravenclaw.hogwarts.A03.com di /etc/bind/named.conf.local.
```
cat > /etc/bind/named.conf.local << EOF
zone "gryffindor.hogwarts.A03.com" {
        type master;
        file "/etc/bind/hogwarts/gryffindor.hogwarts.A03.com";
};

zone "ravenclaw.hogwarts.A03.com" {
        type master;
        file "/etc/bind/hogwarts/ravenclaw.hogwarts.A03.com";
};
EOF
```

3. Membuat direktori untuk zona : `mkdir /etc/bind/hogwarts`
4. Menyalin dan Menkonfigurasi file zona untuk gryffindor.hogwarts.A03.com. dan ravenclaw.hogwarts.A03.com.
```
cp /etc/bind/db.local /etc/bind/hogwarts/gryffindor.hogwarts.A03.com
cat > /etc/bind/hogwarts/gryffindor.hogwarts.A03.com << EOF

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     gryffindor.hogwarts.A03.com. root.gryffindor.hogwarts.A03.com. (
                        2024111301      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL
;
@               IN      NS      gryffindor.hogwarts.A03.com.
@               IN      A       10.4.4.3 ; IP Load Balancer Voldemort
www     IN      CNAME   gryffindor.hogwarts.A03.com
EOF

cp /etc/bind/db.local /etc/bind/hogwarts/ravenclaw.hogwarts.A03.com
cat > /etc/bind/hogwarts/ravenclaw.hogwarts.A03.com << EOF

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ravenclaw.hogwarts.A03.com. root.ravenclaw.hogwarts.A03.com. (
                        2024111301      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL
;
@               IN      NS      ravenclaw.hogwarts.A03.com.
@               IN      A       10.4.4.4 ; IP Load Balancer Dementor
www     IN      CNAME   ravenclaw.hogwarts.A03.com
EOF 
```
5. Mengatur Opsi BIND dengan mengedit file /etc/bind/named.conf.options untuk mengatur opsi seperti direktori cache dan forwarders.
```
cat > /etc/bind/named.conf.options << EOF
options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
EOF
```
6. Restart Layanan BIND `service named restart`

<br>

## Soal 2 & 4

> Memberikan ketentuan khusus untuk DracoMalfoy dan AstoriaGreengrass yang mendapat range IP dari 10.4.2.64 - 10.4.2.65 dan 10.4.2.100 - 10.4.2.101

> Selain itu, untuk HannahAbbott dan SusanBones mendapat range IP dari 10.4.5.50 - 10.4.5.51 dan 10.4.5.155 - 10.4.5.156.

**Answer:**

- Screenshot <br>
DracoMalfoy mendapatkan IP '10.4.2.65' <br>
![WhatsApp Image 2024-10-23 at 18 04 47](https://github.com/user-attachments/assets/bd57b3c9-c25e-4b09-b5c1-85dd48c40c1f)
<br>
HannahAbbott mendapatkan IP '10.4.5.51' <br> 
![WhatsApp Image 2024-10-23 at 18 06 01](https://github.com/user-attachments/assets/ed20f684-7bf5-4f0e-ac5f-65a40c7f0640) <br>

- Configuration & Explanation
  1. Pada **DUMBLEDORE** Sebagai Router (DHCP Relay),
  - Pertama, menentukan nameserver dan memperbarui paket dan menginstal paket DHCP relay:
```
echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start
```
  - Mengedit pada file konfigurasi di bagian /etc/default/isc-dhcp-relay menjadi
  ```
  SERVERS="10.4.3.2"
  INTERFACES="eth1 eth2 eth3 eth4 eth5 eth6"
  OPTIONS=""
  ```
  - Mengaktifkan IP forwarding untuk meneruskan paket antar antarmuka jaringan pada bagian /etc/sysctl.conf menjadi
    ```
    net.ipv4.ip_forward=1
    ```
  - Merestart layanan DHCP relay dengan `service isc-dhcp-relay restart`
  2. Pada **SEVERUS SNAPE** Sebagai DHCP Server,
  - Pertama, menentukan nameserver dan memperbarui paket dan menginstal DHCP server:
```
echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update
apt-get install bind9 -y
```
  - Mengedit file konfigurasi antarmuka DHCP server pada /etc/default/isc-dhcp-server menjadi
    ` INTERFACESv4="eth0"`
  - Mengedit file konfigurasi DHCP:
```
# Range IP untuk Draco Malfoy dan Astoria Greengrass
subnet 10.4.2.0 netmask 255.255.255.0 {
    range 10.4.2.64 10.4.2.65;  # Draco Malfoy
    range 10.4.2.100 10.4.2.101; # Astoria Greengrass

    option routers 10.4.2.1;
    option broadcast-address 10.4.2.255;
    option domain-name-servers 10.4.3.3;

    default-lease-time 300;  
    max-lease-time 6000;
}
```
Dalam subnet ini, Draco Malfoy akan mendapatkan rentang IP 10.4.2.64 - 10.4.2.65, sedangkan Astoria Greengrass mendapat rentang IP 10.4.2.100 - 10.4.2.101. Parameter lain seperti routers, broadcast-address, dan domain-name-servers juga diatur untuk subnet ini. Dan sudah ditambah untuk menetapkan batasan waktu untuk DHCP server pada switch 2 selama 5 menit. 

```
# Range IP untuk Hannah Abbott dan Susan Bones
     subnet 10.4.5.0 netmask 255.255.255.0 {
    range 10.4.5.50 10.4.5.51;  
    range 10.4.5.155 10.4.5.156;  

    option routers 10.4.5.1;
    option broadcast-address 10.4.5.255;
    option domain-name-servers 10.4.3.3;

    default-lease-time 1200;  
    max-lease-time 6000;
}   
```
Di subnet ini, Hannah Abbott akan mendapatkan rentang IP 10.4.5.50 - 10.4.5.51, dan Susan Bones akan menerima IP dalam rentang 10.4.5.155 - 10.4.5.156. Konfigurasi DHCP diatur serupa dengan subnet lain. Dan sudah ditambah untuk menetapkan batasan waktu untuk DHCP server pada switch 5 selama 20 menit.
- Merestart layanan DHCP server dengan `service isc-dhcp-server restart`
<br>

## Soal 3 & 4

> Khusus untuk HermioneGranger yang berada di switch 1 mendapat range IP dari
[Prefix IP].1.10 - [Prefix IP].1.15 dan [Prefix IP].1.20 - [Prefix IP].1.25

> Khusus untuk ChoChang yang berada di switch 6 mendapat range IP dari 
[Prefix IP].6.10 - [Prefix IP].6.15 dan [Prefix IP].6.20 - [Prefix IP].6.25

**Answer:**

- Screenshot <br>
HermioneGranger mendapatkan IP '10.4.1.10' <br>
![WhatsApp Image 2024-10-23 at 18 19 57](https://github.com/user-attachments/assets/0c9b4185-dceb-49a6-8da4-7b395da333c1) <br>
ChoChang mendapatkan IP '10.4.6.10' <br>
![WhatsApp Image 2024-10-23 at 18 23 52](https://github.com/user-attachments/assets/e42fa7ce-404d-44c6-9a89-b99dd2631265) <br>

- Configuration & Explanation
  - Mengedit file konfigurasi DHCP:
  ```
    subnet 10.4.1.0 netmask 255.255.255.0 {
    range 10.4.1.10 10.4.1.15;
    range 10.4.1.20 10.4.1.25;

    option routers 10.4.1.1;
    option broadcast-address 10.4.1.255;
    option domain-name-servers 10.4.3.3;

    default-lease-time 600;  # Switch 6: 10 minutes
    max-lease-time 6000;
   }
  ```
  Di subnet ini, Hermione Granger akan mendapatkan rentang IP, 10.4.1.10 - 10.4.1.15 dan 10.4.1.20 - 10.4.1.25. Konfigurasi DHCP diatur serupa dengan subnet lain, yaitu memberikan IP dalam dua rentang yang ditentukan untuk perangkat yang terhubung ke Switch 1. Dan sudah ditambah untuk menetapkan batasan waktu untuk DHCP server pada Switch 1 memiliki batas waktu 10 menit dengan waktu maksimal 100 menit.
```
subnet 10.4.6.0 netmask 255.255.255.0 {
    range 10.4.6.10 10.4.6.15;  # Cho Chang
    range 10.4.6.20 10.4.6.25;  # Cho Chang

    option routers 10.4.6.1;
    option broadcast-address 10.4.6.255;
    option domain-name-servers 10.4.3.3;

    default-lease-time 600;  # Lease 10 minutes
    max-lease-time 6000;
}
```
Di subnet ini, Cho Chang akan menerima IP dalam rentang 10.4.6.10 - 10.4.6.15 dan 10.4.6.20 - 10.4.6.25. Konfigurasi DHCP diatur serupa dengan subnet lain, yaitu menetapkan dua rentang IP untuk perangkat yang terhubung ke Switch 6. Dan sudah ditambah untuk menetapkan batasan waktu untuk DHCP server pada Switch 6 memiliki batas waktu 10 menit dengan waktu maksimal 100 menit.
- Merestart layanan DHCP server `service isc-dhcp-server restart`
<br>

## Soal 5

> Memastikan bahwa semua CLIENT, HermioneGranger, dan ChoChang harus menggunakan konfigurasi dari DHCP server, menerima DNS dari Professor McGonagall dan dapat akses internet. Khusus untuk HermioneGranger dan ChoChang mendapatkan IP Statis dari DHCP dengan 10.1.x.14. hint: fixed address

**Answer:**

- Screenshot
HermioneGranger mendapatkan IP '10.4.1.14' <br>
![WhatsApp Image 2024-10-24 at 19 46 32](https://github.com/user-attachments/assets/44b0f531-2e45-4aca-a1c6-7e45ab1b325a) <br>
ChoChang mendapatkan IP '10.4.6.14' <br>
![WhatsApp Image 2024-10-24 at 19 46 57](https://github.com/user-attachments/assets/eb1c5d8e-9ab0-4f62-b01d-cd864a6818d1)

- Configuration & Explanation
  1. Pada **HermioneGranger**, lihat link/ether pada eth0 melalui `ip a` lalu salin ke dalam `nano /etc/network/interfaces` untuk fiksasi address, maka dihasilkan
```
auto eth0
iface eth0 inet dhcp
hwaddress ether a2:5f:97:4c:8e:f3
```
2. Pada **ChoChang**, lihat link/ether pada eth0 melalui `ip a` lalu salin ke dalam `nano /etc/network/interfaces` untuk fiksasi address, maka dihasilkan
```
auto eth0
iface eth0 inet dhcp
hwaddress ether 9e:f4:36:0c:a0:54
```
3. Pada **Severus Snape**,
  - Mengedit dan menambahkan file konfigurasi DHCP pada `nano /etc/dhcp/dhcpd.conf`
```
host HermioneGranger {
	hardware ethernet a2:5f:97:4c:8e:f3;
	fixed-address 10.4.1.14;
}

host ChoChang{
	hardware ethernet 9e:f4:36:0c:a0:54;
	fixed-address 10.4.6.14;
}
```
- Merestart layanan DHCP server `service isc-dhcp-server restart`
<br>

## Soal 6

> Dimulai dari asrama Gryffindor yang menjadi PHP worker, mereka harus melakukan deployment untuk website berikut menggunakan PHP 7.4.

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration & Explanation
 - Pertama, menentukan nameserver dan memperbarui paket dan menginstal paket
   ```
	echo nameserver 192.168.122.1 > /etc/resolv.conf
	apt-get update
	apt-get install nginx -y
	apt-get install wget -y
	apt-get install unzip -y
	apt-get install lynx -y
	apt-get install apache2-utils -y
	apt-get install php7.4-fpm php7.4-common php7.4-mysql php7.4-gmp php7.4-curl php7.4-intl php7.4-mbstring php7.4-xmlrpc php7.4-gd php7.4-xml php7.4-cli php7.4-zip -y
   ```
	- Mengunduh dan Mengekstrak Website, Website diunduh dalam format ZIP dari Google Drive :
 ```
wget -O '/var/www/gryffindor.hogwarts.A03.com.zip' 'https://drive.google.com/uc?export=download&id=17R4Zcxm3emHq21WdMJzSfCxO8FHqvATM'
unzip -o /var/www/gryffindor.hogwarts.A03.com.zip -d /var/www/
rm /var/www/gryffindor.hogwarts.A03.com.zip
 ```
Mengekstrak ke dalam direktori /var/www/ dan kemudian struktur direktori diatur agar berada di folder yang tepat :
```
mkdir /var/www/gryffindor.hogwarts.A03.com
mv /var/www/php /var/www/gryffindor.hogwarts.A03.com/php
mv /var/www/index.php /var/www/gryffindor.hogwarts.A03.com
```
  - Mengatur Hak Akses, agar user www-data (default user untuk Nginx) memiliki akses penuh ke direktori website :
```
chown -R www-data:www-data /var/www/gryffindor.hogwarts.A03.com
chmod -R 755 /var/www/gryffindor.hogwarts.A03.com
```
- Membuat file konfigurasi Nginx untuk website:
```
cp /etc/nginx/sites-available/default /etc/nginx/sites-available/gryffindor.hogwarts.A03.com
ln -s /etc/nginx/sites-available/gryffindor.hogwarts.A03.com /etc/nginx/sites-enabled/
rm /etc/nginx/sites-enabled/default
```
- Mengonfigurasi virtual host untuk gryffindor.hogwarts.A03.com pada `/etc/nginx/sites-available/gryffindor.hogwarts.A03.com`
```
echo 'server {
    listen 80;
    server_name gryffindor.hogwarts.A03.com;

    root /var/www/gryffindor.hogwarts.A03.com;
    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    error_log /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;
}' > /etc/nginx/sites-available/gryffindor.hogwarts.A03.com
```
- Start PHP-FPM dan Restart Nginx
```
service php7.4-fpm start
service nginx restart
```
- Menambahkan entri ke file hosts `nano /etc/hosts` agar domain gryffindor.hogwarts.A03.com dapat diakses melalui localhost dengan `127.0.0.1 gryffindor.hogwarts.A03.com`
- Menggunakan browser berbasis teks lynx untuk memverifikasi bahwa website sudah berjalan `lynx localhost`
  
<br>

## Soal 7

> Khusus perlombaan ini, Voldemort sudah jinak dan dia menjadi load balancer untuk para penghuni asrama Gryffindor yang menjadi worker PHP. Aturlah agar Voldemort dapat membagi pekerjaan kepada worker PHP secara optimal. Sebagai pengetesan awal, terapkan algoritma round robin dan lakukan test index.php menggunakan apache benchmark dengan 1000 request dan 100 request/second. Lakukan test sebanyak 3 kali lalu hitung rata-rata dan standar deviasi dari time/request

**Answer:**

- Screenshot<br>
![WhatsApp Image 2024-10-24 at 21 04 40 (1)](https://github.com/user-attachments/assets/6f67edec-120b-4ad3-a464-21b2e8f8ec92) <br>
![WhatsApp Image 2024-10-24 at 21 04 40](https://github.com/user-attachments/assets/a5460156-8f13-4742-81aa-7445f41a87d1)

- **Configuration & Explanation**
- Konfigurasi Nginx sebagai Load Balancer (Voldemort) pada `/etc/nginx/sites-available/load_balancer`
```
echo '
upstream backend {
    server 10.4.1.2;
    server 10.4.1.3;
    server 10.4.1.4;
}

server {
    listen 80;
    server_name gryffindor.hogwarts.A03.com;

    location / {
        proxy_pass http://backend;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
    }

    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}
' > /etc/nginx/sites-available/load_balancer
```
- Mengaktivasi Konfigurasi Load Balancer
```
unlink /etc/nginx/sites-enabled/default
ln -s /etc/nginx/sites-available/load_balancer /etc/nginx/sites-enabled/
```
- Merestart Nginx untuk menerapkan konfigurasi menggunakan `service nginx restart`
<br>

## Soal 8

> Dalam penilaian akhir tahun ini, dibutuhkan algoritma terbaik, cobalah tes 3 algoritma load balancer dengan menggunakan jmeter. Jmeter perlu melakukan login, akses home, dan terakhir logout. Lakukan test dengan 300 thread dan 3 sec ramp up period. Lakukan test sebanyak 3 kali per algoritma, lalu hitung rata-rata dan standar deviasi dari response time. (username: wingardium, password: leviosa)

**Answer:**

- Screenshot <br>

  `Put your screenshot in here`

- Configuration & Explanation
1. Pada **Voldemort**,
   - Menginstall Java Runtime dengan menggunakan `apt-get install openjdk-11-jre -y`
   - Mendownload dan mengekstrak JMeter
```
wget https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-5.6.3.zip
sudo apt install unzip -y
unzip apache-jmeter-5.6.3.zip
cd apache-jmeter-5.6.3/bin
 ```
2. Pada **JMeter**, membuat konfigurasi JMeter untuk tes algoritma Load Balancer
   - Pertama, pada Test Plan menambahkan Thread Group dengan mengeset Number of Threads (users) = 300 dan Ramp-Up Period = 3 detik.
   - Menambahkan 3 HTTP Requests,
   	- Login <br>
   	  Method : POST <br>
          Path : php/login.php <br>
   	  Parameter: username=wingardium, password=leviosa <br>
   	  Port : 80 <br>
	- Home <br>
	  Method : GET <br>
          Path : php/home.php <br>
   	  Port : 80 <br>
	- Logout <br>
          Method : GET <br>
          Path : php/home.php <br>
   	  Port : 80 <br>
3. Kembali pada **Voldemort**, untuk menjalankan tes
	- Membuat folder output untuk menyimpan hasil tes dengan `mkdir ../../XXX` yang dilanjut membuat file pada apache-jmeter-5.6.3/bin XXX.jmx menggunakan `nano XXX.jmx`
	- Menjalankan Tes dengan Mode Non-GUI dengan perintah, `./jmeter -n -t XXX.jmx -l XXX.csv -e -o ../../XXX`
	- Mengompresi Hasil Tes yang tadi dibuat file menggunakan `zip -r XXX.zip XXX`
	- Menggunakan curl untuk mengirim file hasil ke webhook `curl -X POST -F "file=@./XXX.zip" https://webhook.site/2139224d-9e77-44a2-a26c-5312480d4993`
<br>

## Soal 9

> Tidak semua IP dapat akses asrama Gryffindor melalui IP Load balancer Voldemort. Untuk itu, berikan akses pada load balancer Voldemort. Autentikasi akan memerlukan username: “jarkom” dan password: “modul3”. Simpan file autentikasi pada  /etc/nginx/secretchamber 

**Answer:**

- Screenshot <br>
![WhatsApp Image 2024-10-24 at 22 41 14](https://github.com/user-attachments/assets/fc366c1b-b519-4242-99ee-0e4767051f5f) <br>
![WhatsApp Image 2024-10-24 at 22 41 24](https://github.com/user-attachments/assets/ce77453b-ae6b-4527-82dd-2d21afae7dce)

- Configuration & Explanation
 - Mengonfigurasi NGINX sebagai Load Balancer, dengan pertama membuat File htpasswd untuk Autentikasi Dasar dengan `sudo htpasswd -bc /etc/nginx/secretchamber jarkom modul3`
 - Membuat konfigurasi di /etc/nginx/sites-available/load_balancer dengan perintah
```
echo '
upstream backend {
    server 10.4.1.2;
    server 10.4.1.3;
    server 10.4.1.4;
}

server {
    listen 80;
    server_name gryffindor.hogwarts.A03.com;

    auth_basic "Restricted Access to Gryffindor";
    auth_basic_user_file /etc/nginx/secretchamber;

    location / {
        proxy_pass http://backend;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
    }

    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}
' /etc/nginx/sites-available/load_balancer
```
  - Merestart NGINX untuk Menerapkan Perubahan `sudo service nginx restart`

<br>

## Soal 10

> Setelah menambahkan autentikasi ke Gryffindor, coba testing ulang dengan menggunakan JMeter (algoritma round robin) serta skenario, thread, dan ramp up period yang sama seperti no 8 (300 thread, 3 sec ramp up period, login-home-logout). Kali ini, coba juga jumlah worker yang berbeda: 3 worker, 2 worker, dan 1 worker. 

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration & Explanation
- 
<br>

## Soal 11

> Hogwarts juga bekerjasama dengan ITS dalam perlombaan ini. Untuk itu, setiap request pada Voldemort yang mengandung /informatika pada akhir url akan di proxy passing menuju halaman https://www.its.ac.id/informatika/id/beranda/ 

**Answer:**

- Screenshot <br>
![WhatsApp Image 2024-10-24 at 22 55 12](https://github.com/user-attachments/assets/7a835414-d343-4945-bb45-44ae7feaa715)

- Configuration & Explanation
 - Mengedit Konfigurasi Load Balancer di NGINX, Gunakan perintah echo untuk membuat konfigurasi dan simpan di /etc/nginx/sites-available/load_balancer
```
echo '
upstream backend {
    server 10.4.1.2;
    server 10.4.1.3;
    server 10.4.1.4;
}

server {
    listen 80;
    server_name gryffindor.hogwarts.A03.com;

    auth_basic "Restricted Access to Gryffindor";
    auth_basic_user_file /etc/nginx/secretchamber;

    location /informatika {
        proxy_pass https://www.its.ac.id/informatika/id/beranda/;
        proxy_set_header Host www.its.ac.id/informatika/id/beranda/;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}
' /etc/nginx/sites-available/load_balancer
```
- Merestart NGINX menggunakan `sudo service nginx restart`

<br>

## Soal 12

> Selain butuh autentikasi dalam pengaksesan asrama Gryffindor melalui LB Voldemort, juga perlu dibatasi dengan pembatasan IP.  LB Voldemort hanya boleh diakses oleh client dengan IP [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, dan [Prefix IP].5.155. hint: (fixed in dulu clientnya) 

**Answer:**

- Screenshot <br>
![WhatsApp Image 2024-10-24 at 23 36 12](https://github.com/user-attachments/assets/c338d96d-9aef-4282-896e-46d3e2b9262e)

- Configuration & Explanation
- Membuat File Autentikasi Dasar menggunakan htpasswd untuk membuat file autentikasi di /etc/nginx/secretchamber `sudo htpasswd -bc /etc/nginx/secretchamber jarkom modul3`
- Membuat Konfigurasi Load Balancer di NGINX, membuat konfigurasi berikut di /etc/nginx/sites-available/load_balancer
```
echo '
upstream backend {
    server 10.4.1.2;
    server 10.4.1.3;
    server 10.4.1.14;
}

server {
    listen 80;
    server_name gryffindor.hogwarts.A03.com;

    auth_basic "Restricted Access to Gryffindor";
    auth_basic_user_file /etc/nginx/secretchamber;

    location /informatika {
        proxy_pass https://www.its.ac.id/informatika/id/beranda/;
        proxy_set_header Host www.its.ac.id/informatika/id/beranda/;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location / {
        proxy_pass http://backend;
        allow 10.4.2.64;
        allow 10.4.2.100;
        allow 10.4.5.50;
        allow 10.4.5.155;
        deny all;
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}
' /etc/nginx/sites-available/load_balancer
```
 - Menonaktifkan Konfigurasi Default dengan menggunakan `unlink /etc/nginx/sites-enabled/default`
 - Mengaktifkan Konfigurasi Load Balancer menggunakan `ln -s /etc/nginx/sites-available/load_balancer /etc/nginx/sites-enabled/`
- Merestart NGINX untuk Menerapkan Perubahan `sudo service nginx restart`

<br>

## Soal 13

> Pengaturan database yang dibutuhkan dalam perlombaan ini wajib diatur di Hagrid. Pastikan pengaturan database tersebut dapat diakses oleh Lunalovegood, FiliusFlitwick, dan ChoChang dengan menggunakan username: kelompokyyy dan password: passwordyyy 

**Answer:**

- Screenshot
![WhatsApp Image 2024-10-25 at 00 17 08](https://github.com/user-attachments/assets/c425aa50-0860-424b-8d0c-92f28576126d)

- Configuration & Explanation
  - Menyetel DNS Resolver, menambahkan konfigurasi nameserver dengan alamat IP DNS yang diperlukan dengan `echo 'nameserver 10.4.3.3' > /etc/resolv.conf`
  - Perbarui Paket dan Instal MariaDB dan mengaktifkan MariaDB setelah instalasi
```
apt-get update
apt-get install mariadb-server -y
service mysql start
```
 - Mengedit file konfigurasi my.cnf untuk mengizinkan MariaDB mendengarkan permintaan jaringan
```
echo '# This group is read both by the client and the server
# use it for options that affect everything
[client-server]

# Import all .cnf files from configuration directory
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mariadb.conf.d/

# Options affecting the MySQL server (mysqld)
[mysqld]
skip-networking=0
skip-bind-address
' > /etc/mysql/my.cnf
```
 - Mengedit bind-address di 50-server.cnf, mengubah bind-address di /etc/mysql/mariadb.conf.d/50-server.cnf untuk mengizinkan akses dari seluruh jaringan dengan `nano /etc/mysql/mariadb.conf.d/50-server.cnf` pada baris bind-address mengubah nilainya menjadi 0.0.0.0:
 - Restart layanan MariaDB untuk menerapkan perubahan menggunakan `sudo service mysql restart`
 - Masuk ke MariaDB sebagai root dengan `mysql -u root -p`
 - Membuat pengguna baru dengan akses jaringan dan lokal dengan
```
CREATE USER 'kelompoka03'@'%' IDENTIFIED BY 'passworda03';
CREATE USER 'kelompoka03'@'localhost' IDENTIFIED BY 'passworda03';
```
- Membuat database baru untuk pengguna tersebut dengan `CREATE DATABASE dbkelompoka03;`
- Memberikan semua hak akses kepada pengguna
```
GRANT ALL PRIVILEGES ON *.* TO 'kelompoka03'@'%';
GRANT ALL PRIVILEGES ON *.* TO 'kelompoka03'@'localhost';
FLUSH PRIVILEGES;
```
- Uji Koneksi MariaDB dari Host Lain, Verifikasi apakah konfigurasi berhasil dengan menguji koneksi menggunakan perintah `mariadb --host=10.4.4.2 --port=3306 --user=kelompoka03 --password=passworda03 dbkelompoka03 -e "SHOW DATABASES;"`. Maka, MariaDB akan dikonfigurasi untuk menerima koneksi jaringan, dan pengguna kelompoka03 akan memiliki akses penuh ke semua database dari alamat IP apa pun.

<br>

## Soal 14

> Selain itu, untuk Lunalovegood, FiliusFlitwick, dan ChoChang memiliki website sesuai dengan https://github.com/lodaogos/laravel-jarkom-modul-3/tree/main  berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer! Pastikan database di Hagrid sudah ada isinya sekarang dan server Laravel sudah running di localhost!

**Answer:**

- Screenshot
![WhatsApp Image 2024-10-25 at 19 26 17](https://github.com/user-attachments/assets/2f66b373-043a-418d-ae78-5225aa4311c6)

- Configuration & Explanation
  - Perbarui Sistem dan Instal Dependensi Dasar dan juga paket-paket
```
sudo apt-get update
sudo apt-get install -y software-properties-common
sudo apt-get install -y php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-fpm
sudo apt-get install nginx -y
```
  - Tambahkan Repository untuk PHP 8.0
```
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
```
  - Menginstall Composer & Git
```
wget https://getcomposer.org/download/2.0.13/composer.phar
chmod +x composer.phar
sudo mv composer.phar /usr/local/bin/composer
sudo apt-get install git -y
```
- Mengclone Repository Proyek
```
cd /var/www
git clone https://github.com/lodaogos/laravel-jarkom-modul-3.git
```
- Memindah ke Direktori Proyek dan Jalankan Composer
```
cd /var/www/laravel-jarkom-modul-3
sudo composer update
```
- Menyalin dan Konfigurasi File .env
```
cp .env.example .env
nano .env
```
- Membuat file konfigurasi untuk proyek Laravel di Nginx,
```
echo '
server {
    listen 8001;

    root /var/www/laravel-jarkom-modul-3/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
}
' /etc/nginx/sites-available/laravel-jarkom-modul-3-worker
```
- Mengaktifkan Konfigurasi Nginx untuk Laravel dengan menggunakan `sudo ln -s /etc/nginx/sites-available/laravel-jarkom-modul-3-worker /etc/nginx/sites-enabled/`
- Memulai Layanan PHP-FPM dan Restart Nginx
```
 service php8.0-fpm start
 service nginx restart
```
- Untuk menjalankan server Laravel pada port 8000
```
cd /var/www/laravel-jarkom-modul-3
php artisan serve --host=0.0.0.0 --port=8000
```
<br>

## Soal 15

> Lakukan testing endpoint /register sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Kenapa failed 99x? Jelaskan! 

> _Test the /register endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Why did 99 tests fail? Explain!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 16

> Lakukan juga testing pada endpoint /login sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Dapatkan token melalui responsenya juga!

> _Test the /login endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Collect the token from the response!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 17

> Coba testing pada endpont /me sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Periksa responsenya apakah sudah sesuai dengan yang diloginkan? 

> _Test the /me endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Check if the response matches the logged-in user!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 18

> Mendekati tugas akhir perlombaan ini, mari seimbangkan kekuatan LunaLovegood, FiliusFlitwick, dan ChoChang untuk bekerja sama secara adil! Buatkan load balancer Laravel dengan Dementor dan implementasikan Proxy Bind untuk mengaitkan IP dari ketiga worker tersebut!

> _As the competition nears its end, balance the workload of LunaLovegood, FiliusFlitwick, and ChoChang! Create a Laravel load balancer using Dementor and implement Proxy Bind to link the IPs of the three workers!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 19

> Untuk menguatkan para Laravel Worker, coba implementasikan PHP-FPM pada LunaLovegood, FiliusFlitwick, dan ChoChang. Untuk testing kinerja naikkan: 
pm.max_children
pm.start_servers
pm.min_spare_servers
pm.max_spare_servers
sebanyak tiga percobaan dan lakukan analisis testing menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _To strengthen the Laravel workers, implement PHP-FPM on LunaLovegood, FiliusFlitwick, and ChoChang. For performance testing, adjust: pm.max_children, pm.start_servers, pm.min_spare_servers, pm.max_spare_servers. Run the tests three times and analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 20

> Yey terakhir. Menurut Professor Dumbledore, sepertinya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa worker-worker. Implementasikan Least-Conn pada Dementor. Lakukan analisis pada testing kinerja menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _Finally, Professor Dumbledore suggests that PHP-FPM might not be enough to improve the workers' performance. Implement the Least-Conn algorithm on Dementor. Analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>
  
## Problems

## Revisions (if any)
