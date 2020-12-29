# Jarkom_Modul5_Lapres_B12

1. 05111840000057 - Maisie Chiara Salsabila
2. 05111840000062 - Geizka Wahyu Fahriza

## Daftar Isi
  1. [Soal A](#A)
  2. [Soal B](#B)
  3. [Soal C](#C)
  4. [Soal D](#D)

  5. [Nomor 1](#1)
  6. [Nomor 2](#2)
  7. [Nomor 3](#3)
  8. [Nomor 4](#4)
  9. [Nomor 5](#5)
  10. [Nomor 6](#6)
  11. [Nomor 7](#7)
  </br></br></br>

<a name="A"></a>
## SOAL A
### Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Bibah seperti dibawah ini :
![testestes](https://user-images.githubusercontent.com/48936125/102958243-0ecbdf00-450f-11eb-8571-442615416370.png)
Berdasarkan gambar topologi di atas, dibuatlah file topologi.sh:
![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-a.png)
</br></br></br>


<a name="B"></a>
## SOAL B
### karena kalian telah mempelajari Subnetting dan Routing, Bibah meminta kalian untuk membuat topologi tersebut menggunakan teknik CIDR atau VLSM. Setelah melakukan subnetting,
- Lakukan setting pada file ```/etc/network/interfaces``` pada setiap UML sebagai berikut:
  **SURABAYA (Router)**
  ```
  auto eth0
  iface eth0 inet static
  address 10.151.74.54
  netmask 255.255.255.252
  gateway 10.151.74.53

  auto eth1
  iface eth1 inet static
  address 192.168.0.1
  netmask 255.255.255.252

  auto eth2
  iface eth2 inet static
  address 192.168.0.5
  netmask 255.255.255.252
  ```
  **KEDIRI (Router)**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.0.6
  netmask 255.255.255.252
  gateway 192.168.0.5

  auto eth1
  iface eth1 inet static
  address 192.168.0.9
  netmask 255.255.255.248

  auto eth2
  iface eth2 inet static
  address 192.168.2.1
  netmask 255.255.255.0
  ```
  **BATU (Router)**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.252
  gateway 192.168.0.1

  auto eth1
  iface eth1 inet static
  address 10.151.83.105
  netmask 255.255.255.248

  auto eth2
  iface eth2 inet static
  address 192.168.4.1
  netmask 255.255.255.0
  ```
  **MALANG (DNS Server)**
  ```
  auto eth0
  iface eth0 inet static
  address 10.151.83.106
  netmask 255.255.255.252
  gateway 10.151.83.105
  ```
  **MOJOKERTO (DHCP Server)**
  ```
  auto eth0
  iface eth0 inet static
  address 10.151.83.107
  netmask 255.255.255.248
  gateway 10.151.83.105
  ```
  **MADIUN (Web Server)**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.0.11
  netmask 255.255.255.248
  gateway 192.168.0.9
  ```
  **PROBOLINGGO (Web Server)**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.0.10
  netmask 255.255.255.248
  gateway 192.168.0.9
  ```
- Lakukan restart network dengan perintah ```service networking``` pada setiap UMLnya
</br></br></br>


<a name="C"></a>
## SOAL C
### kalian juga diharuskan melakukan routing agar setiap perangkat pada jaringan tersebut dapat terhubung.
![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-c.png)
</br></br></br>


<a name="D"></a>
## SOAL D
### Tugas berikutnya adalah memberikan ip pada subnet SIDOARJO dan GRESIK secara dinamis menggunakan bantuan DHCP SERVER (Selain subnet tersebut menggunakan ip static). Kemudian kalian mengingat bahwa kalian harus setting DHCP RELAY pada router yang menghubungkannya, seperti yang kalian telah pelajari di masa lalu.
**MOJOKERTO**
- Lakukan install ```apt-get install isc-dhcp-server```
- Edit file dengan perintah ```/etc/dhcp/dhcpd.conf``` seperti pada gambar berikut:
  ![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-d-1.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-d-2.png)
- Lakukan restart dengan perintah ```service isc-dhcp-server restart```
</br>

**KEDIRI**
- Lakukan install ```apt-get install isc-dhcp-relay```
- Lakukan edit pada file ```/etc/default/isc-dhcp-relay```</br>
  ![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-d-3.png)
- Lakukan restart dengan perintah ```service isc-dhcp```
</br>

**GRESIK**
- Edit file ```/etc/network/interfaces``` menjadi:
  ```
  auto eth0
  iface eth0 inet dhcp
  ```
  ![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-d-4.png)
- Lakukan restart network dengan peritah ```service networking restart```
</br>

**BATU**
- Lakukan install ```apt-get install isc-dhcp-relay```
- Lakukan edit pada file ```/etc/dhcp/dhcp.conf```</br>
  ![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-d-5.png)
</br>

**SIDOARJO**
- Edit file ```/etc/network/interfaces``` menjadi:
  ```
  auto eth0
  iface eth0 inet dhcp
  ```
  ![testestes](https://github.com/messyme/Jarkom_Modul5_Lapres_B12/blob/main/files/soal-d-6.png)
- Lakukan restart network dengan peritah ```service networking restart```
</br></br></br>


<a name="1"></a>
## SOAL NO 1
### Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi SURABAYA menggunakan iptables, namun Bibah tidak ingin kalian menggunakan MASQUERADE.
- Tambahkan iptables pada **SURABAYA**
  ```
  iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o eth0 -j SNAT --to source 10.151.74.54
  ```
- Pada **MALANG** edit file ```/etc/bind/named.conf.options``` agar **GRESIK** dan **SIDOARJO** dapat mengakses dari luar
  - uncomment 
    ```
    // dnssec-validation auto;
    ```
  - Ubah 0.0.0.0 menjadi 8.8.8.8
    ```
    forwarders {
      8.8.8.8;
    };
    ```
  - Kemudian tambahkan 
    ```
    allow-query{any;};
    ```  
- Lakukan testing dengan ping **google.com** pada UML **SURABAYA**
</br></br></br>


<a name="2"></a>
## SOAL NO 2
### Kalian diminta untuk mendrop semua akses SSH dari luar Topologi (UML) Kalian pada server yang memiliki ip DMZ (DHCP dan DNS SERVER) pada SURABAYA demi menjaga keamanan.
- Pada **SURABAYA** tambahkan iptables
```
iptables -N LOGGING
iptables -A FORWARD -p tcp --dport 22 -d 10.151.83.104/29 -i eth0 -j LOGGING
iptables -A LOGGING -m limit --limit 5/min -j LOG --log-prefix "iptables_FORWARD_denied: " --log-level 7
iptables -A LOGGING -j DROP
```
- Lakukan testing dengan cara:
  - Install netcat di UML **Mojokerto** dan UML **Malang** dengan perintah ```apt-get install netcat```
  - Pada UML **Mojokerto** dan **Malang** gunakan perintah ```nc -l -p <nomor_port>```

</br></br></br>


<a name="3"></a>
## SOAL NO 3
### Karena tim kalian maksimal terdiri dari 3 orang, Bibah meminta kalian untuk membatasi DHCP dan DNS server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan yang berasal dari mana saja menggunakan iptables pada masing masing server, selebihnya akan di DROP.
- Pada **MALANG** dan **MOJOKERTO** tambahkan iptables sebagai berikut:
```
iptables -N LOGGING
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j LOGGING
iptables -A LOGGING -m limit --limit 5/min -j LOG --log-prefix "iptables_FORWARD_denied: " --log-level 7
iptables -A LOGGING -j DROP
```
- Lakukan testing dengan melakukan ping pada 4 UML
</br></br></br>


<a name="4"></a>
## SOAL NO 4
### kemudian kalian diminta untuk membatasi akses ke MALANG yang berasal dari SUBNET SIDOARJO dan SUBNET GRESIK dengan peraturan sebagai berikut: (4) Akses dari subnet SIDOARJO hanya diperbolehkan pada pukul 07.00 - 17.00 pada hari Senin sampai Jumat. 
- Pada **MALANG** tambahkan iptables:
  ```
  iptables -A INPUT -s 192.168.3.0/24 -m time --timestart 07:00 --timestop 17:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
  iptables -A INPUT -s 192.168.3.0/24 -j REJECT
  ```
</br></br></br>


<a name="5"></a>
## SOAL NO 5
### Akses dari subnet GRESIK hanya diperbolehkan pada pukul 17.00 hingga pukul 07.00 setiap harinya. Selain itu paket akan di REJECT.
- Pada **MALANG** tambahkan iptables:
  ```
  iptables -A INPUT -s 192.168.2.0/24 -m time --timestart 07:00 --timestop 17:00 -j REJECT
  ```
</br></br></br>


<a name="6"></a>
## SOAL NO 6
### Karena kita memiliki 2 buah WEB Server, Bibah ingin SURABAYA disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada PROBOLINGGO port 80 dan MADIUN port 80.
- Pada **SURABAYA** tambahkan:
```
iptables -t nat -A PREROUTING -p tcp -d 10.151.83.106 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.168.0.10:80
iptables -t nat -A PREROUTING -p tcp -d 10.151.83.106 -j DNAT --to-destination 192.168.0.11:80
iptables -t nat -A POSTROUTING -p tcp -d 192.168.0.10 --dport 80 -j SNAT --to-source 10.151.83.106
iptables -t nat -A POSTROUTING -p tcp -d 192.168.0.11 --dport 80 -j SNAT --to-source 10.151.83.106
```
- Untuk melakukan testing:
  - Install netcat pada UML **Malang**, **Probolinggo**, **Madiun**, **Surabaya**, serta **Gresik** dengan menggunakan perintah ```apt-get install netcat```
  - Pada UML **Madiun** gunakan perintah ```nc -l -p 80```
  - Pada UML **Probolinggo** gunakan perintah ```nc -l -p 80```
  - Pada UML Client **Gresik** gunakan perintah ```nc ipMalang 80```
  - Ketik bebas pada UML **Gresik** maka akan muncul di UML **Madiun** atau **Probolinggo**
</br></br></br>


<a name="7"></a>
## SOAL NO 7
### Bibah ingin agar semua paket didrop oleh firewall (dalam topologi) tercatat dalam log pada setiap UML yang memiliki aturan drop.
- Pada **SURABAYA** tambahkan:
```
iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A OUTPUT -j LOGGING
iptables -A LOGGING -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP
```
- Jalankan iptables dan gunakan perintah ```nano /var/log/messages```
</br></br></br>
