# Jarkom-Modul-2-B09-2023

## Anggota Kelompok
| Nama | NRP |
|---------------------------|------------|
|Wan Sabrina Mayzura | 5025211023 |
|Syarifah Talitha Erfany | 5025211175 |

## Daftar Isi
- [Daftar Isi](#daftar-isi)
  - [Topologi](#topologi)
  - [Config](#config)
- [Soal 1](#Soal-1)
  - [Script](#script)
  - [Result](#result)
- [Soal 2](#Soal-2)
  - [Script](#script-1)
  - [Result](#result-1)
- [Soal 3](#Soal-3)
  - [Script](#script-2)
  - [Result](#result-2)
- [Soal 4](#Soal-4)
  - [Script](#script-3)
  - [Result](#result-3)
- [Soal 5](#Soal-5)
  - [Script](#script-4)
  - [Result](#result-4)
- [Soal 6](#Soal-6)
  - [Script](#script-5)
  - [Result](#result-5)
- [Soal 7](#Soal-7)
  - [Script](#script-6)
  - [Result](#result-6)
- [Soal 8](#Soal-8)
  - [Script](#script-7)
  - [Result](#result-7)
- [Soal 9](#Soal-9)
  - [Script](#script-8)
  - [Result](#result-8)
- [Soal 10](#Soal-10)
  - [Script](#script-9)
  - [Result](#result-9)
- [Soal 11](#Soal-11)
  - [Script](#script-10)
  - [Result](#result-10)
- [Soal 12](#Soal-12)
  - [Script](#script-11)
  - [Result](#result-11)
- [Soal 13](#Soal-13)
  - [Script](#script-12)
  - [Result](#result-12)
- [Soal 14](#Soal-14)
  - [Script](#script-13)
  - [Result](#result-13)
- [Soal 15](#Soal-15)
  - [Script](#script-14)
  - [Result](#result-14)
- [Soal 16](#Soal-16)
  - [Script](#script-15)
  - [Result](#result-15)
- [Soal 17](#Soal-17)
  - [Script](#script-16)
  - [Result](#result-16)
- [Soal 18](#Soal-18)
  - [Script](#script-17)
  - [Result](#result-17)
- [Soal 19](#Soal-19)
  - [Script](#script-18)
  - [Result](#result-18)
- [Soal 20](#Soal-20)
  - [Script](#script-19)
  - [Result](#result-19)

## Topologi
![image](topologi.png)

## Config 
- **Router**
  ```
    auto eth0
    iface eth0 inet dhcp

    auto eth1
    iface eth1 inet static
        address 10.10.1.1
        netmask 255.255.255.0

    auto eth2
    iface eth2 inet static
        address 10.10.2.1
        netmask 255.255.255.0
  ```
- **Nakula**
  ```
    auto eth0
    iface eth0 inet static
	    address 10.10.1.2
	    netmask 255.255.255.0
	    gateway 10.10.1.1
  ```
- **Sadewa**
  ```
    auto eth0
    iface eth0 inet static
        address 10.10.1.3
        netmask 255.255.255.0
        gateway 10.10.1.1
  ```
- **Abimanyu**
  ```
    auto eth0
    iface eth0 inet static
        address 10.10.1.4
        netmask 255.255.255.0
        gateway 10.10.1.1
  ```
- **Prabukusuma**
  ```
    auto eth0
    iface eth0 inet static
        address 10.10.1.5
        netmask 255.255.255.0
        gateway 10.10.1.1
  ```
- **Wisanggeni**
  ```
    auto eth0
    iface eth0 inet static
        address 10.10.1.6
        netmask 255.255.255.0
        gateway 10.10.1.1
  ```
- **Arjuna**
  ```
    auto eth0
    iface eth0 inet static
        address 10.10.2.2
        netmask 255.255.255.0
        gateway 10.10.2.1
  ```
- **Werkudara**
  ```
    auto eth0
    iface eth0 inet static
        address 10.10.2.3
        netmask 255.255.255.0
        gateway 10.10.2.1
  ```
- **Yudhistira**
  ```
    auto eth0
    iface eth0 inet static
        address 10.10.2.4
        netmask 255.255.255.0
        gateway 10.10.2.1
  ```
- **Notes of Config**
  ```
  Router	: 10.10.1.1 (Switch 1)
  Yudhistira	: 192.173.1.2
  Nakula	        : 192.173.1.3
  Router	: 10.10.2.1 (Switch 2)
  Werkudara	: 192.173.2.2
  Sadewa	        : 192.173.2.3
  Arjuna	        : 192.173.3.5
  ```

## Soal 1 
> Yudhistira akan digunakan sebagai DNS Master, Werkudara sebagai DNS Slave, Arjuna merupakan Load Balancer yang terdiri dari beberapa Web Server yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Buatlah topologi dengan pembagian sebagai berikut. Folder topologi dapat diakses pada drive berikut

### Script
**Yudhistira**
pada nano `/etc/resolv.conf`
```
nameserver 192.168.122.1
```

**Nakula**
pada nano `/etc/resolv.conf`
```
nameserver 192.168.122.1
nameserver 10.10.2.4 #IP Yudhistira
nameserver 10.10.2.3 #IP Werkudara
```

```
ping google.com
```

### Result

![image](no1/google.png)

## Soal 2 
> Buatlah website utama dengan akses ke arjuna.yyy.com dengan alias www.arjuna.yyy.com dengan yyy merupakan kode kelompok.
Config

### Script

**Yudhistira**
1. Dalam `arjuna.B03.com`
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     arjuna.B03.com. root.arjuna.B03.com. (
                        2023100901      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      arjuna.B03.com.
@       IN      A       10.10.2.2        ; IP arjuna karena point ke arjuna
www     IN      CNAME   arjuna.B03.com.
@       IN	    AAAA    ::1
```

2. nano `named.conf.local` yang berada di root agar tidak hilang
```
zone “arjuna.B03.com" {
    type master;
    file "/etc/bind/arjuna/arjuna.B03.com";
};
```

3. No2.sh
```
#!bin/bash

echo '
zone "arjuna.B03.com" {
    type master;
    file "/etc/bind/arjuna/arjuna.B03.com";
};' >> /etc/bind/named.conf.local

mkdir /etc/bind/arjuna
cp arjuna.B03.com /etc/bind/arjuna/arjuna.B03.com

service bind9 restart
```

**Nakula**
```
ping arjuna.B03
ping www.arjuna.B03.com
```

### Result

![image]()


## Soal 3
> Dengan cara yang sama seperti soal nomor 2, buatlah website utama dengan akses ke abimanyu.yyy.com dan alias www.abimanyu.yyy.com.

### Script

**Yudhistira**
```
```

**Abimanyu**
```
```

### Result

![image]()

## Soal 4
> Kemudian, karena terdapat beberapa web yang harus di-deploy, buatlah subdomain parikesit.abimanyu.yyy.com yang diatur DNS-nya di Yudhistira dan mengarah ke Abimanyu.

### Script

**Yudhistira**

```
```

**Abimanyu**
```
```

### Result

![image]()

## Soal 5
> Buat juga reverse domain untuk domain utama.

### Script

**Yudhistira**
```
```

**Abimanyu / Client yang lain**
```
```

### Result

![image]()

## Soal 6
> Agar dapat tetap dihubungi ketika DNS Server Yudhistira bermasalah, buat juga Werkudara sebagai DNS Slave untuk domain utama.

### Script
**Yudhistira**
```
```

**Werkudara (DNS Slave)**
```
```

**Abimanyu**
```
```

### Result

![image]()

![image]()

## Soal 7
> Seperti yang kita tahu karena banyak sekali informasi yang harus diterima, buatlah subdomain khusus untuk perang yaitu baratayuda.abimanyu.yyy.com dengan alias www.baratayuda.abimanyu.yyy.com yang didelegasikan dari Yudhistira ke Werkudara dengan IP menuju ke Abimanyu dalam folder Baratayuda

### Script
**Yudhistira**

```
```

**Werkudara**
```
```

### Result

![image]()

## Soal 8
> Untuk informasi yang lebih spesifik mengenai Ranjapan Baratayuda, buatlah subdomain melalui Werkudara dengan akses rjp.baratayuda.abimanyu.yyy.com dengan alias www.rjp.baratayuda.abimanyu.yyy.com yang mengarah ke Abimanyu.
```
```

### Script
**Werkudara**
```
```
### Result

![image]()


## Soal 9
> Arjuna merupakan suatu Load Balancer Nginx dengan tiga worker yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Lakukan deployment pada masing-masing worker

### Script
**Arjuna (Load Balancing)**
```
```

**PrabuKusuma, Abimanyu,, Wisanggeni**
```
```

**Client (Sadewa / Nakula)**
```
```

### Result

![image]()

**Load Balancing**

![image]()

![image]()

![image]()

## Soal 10
> Kemudian gunakan algoritma Round Robin untuk Load Balancer pada Arjuna. Gunakan server_name pada soal nomor 1. Untuk melakukan pengecekan akses alamat web tersebut kemudian pastikan worker yang digunakan untuk menangani permintaan akan berganti ganti secara acak. Untuk webserver di masing-masing worker wajib berjalan di port 8001-8003. Contoh (Prabakusuma:8001, Abimanyu:8002, Wisanggeni:8003)

### Script

**Arjuna (Load Balancing)**
```
```

**PrabuKusuma, Abimanyu, Wisanggeni**
```
```
### Result

![image]()

**Load Balancing**

![image]()

![image]()

![image]()

## Soal 11
> Selain menggunakan Nginx, lakukan konfigurasi Apache Web Server pada worker Abimanyu dengan web server www.abimanyu.yyy.com. Pertama dibutuhkan web server dengan DocumentRoot pada /var/www/abimanyu.yyy

### Script
**Yudhistira**
```
```

**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result

![image]()

## Soal 12
> Setelah itu ubahlah agar url www.abimanyu.yyy.com/index.php/home menjadi www.abimanyu.yyy.com/home.

```
```

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result

![image]()

## Soal 13
> Selain itu, pada subdomain www.parikesit.abimanyu.yyy.com, DocumentRoot disimpan pada /var/www/parikesit.abimanyu.yyy

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result

![image]()

## Soal 14
> Pada subdomain tersebut folder /public hanya dapat melakukan directory listing sedangkan pada folder /secret tidak dapat diakses (403 Forbidden)

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result

![image]()

![image]()

## Soal 15
> Buatlah kustomisasi halaman error pada folder /error untuk mengganti error kode pada Apache. Error kode yang perlu diganti adalah 404 Not Found dan 403 Forbidden.

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result
**Error**
![image]()

![image]()

**Forbidden**
![image]()

![image]()

## Soal 16
> Buatlah suatu konfigurasi virtual host agar file asset www.parikesit.abimanyu.yyy.com/public/js menjadi www.parikesit.abimanyu.yyy.com/js 

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result

## Soal 17
> Agar aman, buatlah konfigurasi agar www.rjp.baratayuda.abimanyu.yyy.com hanya dapat diakses melalui port 14000 dan 14400.

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result
**Port 14000 atau 14400**
![image]()

**Port yang tidak sesuai**
![image]()

## Soal 18
> Untuk mengaksesnya buatlah autentikasi username berupa “Wayang” dan password “baratayudayyy” dengan yyy merupakan kode kelompok. Letakkan DocumentRoot pada /var/www/rjp.baratayuda.abimanyu.yyy.

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```
```

### Result
![image]()

![image]()

![image]()

![image]()

## Soal 19
> Buatlah agar setiap kali mengakses IP dari Abimanyu akan secara otomatis dialihkan ke www.abimanyu.yyy.com (alias)

### Script
**Abimanyu**
```
```

Config test
```
```

**Client (Sadewa)**
```
```

### Result
![image]()

![image]()

## Soal 20
> Karena website www.parikesit.abimanyu.yyy.com semakin banyak pengunjung dan banyak gambar gambar random, maka ubahlah request gambar yang memiliki substring “abimanyu” akan diarahkan menuju abimanyu.png.

### Script
**Abimanyu**
```
```

**Client (Sadewa)**
```

```
### Result
![image]()

![image]()

![image]()
