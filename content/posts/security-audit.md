---
title: "Security Audit in IT"
date: 2024-03-23T02:01:58+05:30
description: "Security Audit merupakan salah satu subjek topik untuk keamanan informasi yang penting untuk identifikasi kerentanan, pada artikel ini akan membahas audit security baik dari sisi jaringan ataupun desktop"
tags: [audit, practical, tools, security]
---

Keamanan informasi membutuhkan pendekatan komprehensif untuk melindungi aset digital yang sudah ditulis pada artikel [Introduction to Information Security](http://localhost:1313/posts/intro-it-security/). Dengan memahami prinsip-prinsip keamanan informasi, memanfaatkan teknik kriptografi, melakukan audit rutin, dan menerapkan langkah-langkah keamanan jaringan yang kuat, organisasi dapat secara signifikan mengurangi risiko mereka terhadap ancaman siber.

Audit Rutin ini dilakukan untuk identifikasi sebuah komputer dengan kerentanan yang berujung rekomendasi untuk mengatasi kerentanan yang ada pada komputer atau layanan yang akan diaudit. Tools yang akan dibahas pada artikel ini adalah `lynis` yang dapat diinstall pada Distribusi Sistem Operasi Linux favorit anda.  


## Lynis

Tools `lynis` menjadi salah satu cara untuk audit komputer karena hasilnya yang komperhensif dan memberikan hasil rekomendasi untuk hardening komputer ataupun *service*. Cara kerja `lynis` adalah melakukan sebuah health scan sehingga dapat memberikan informasi mengenai *compliance* yang terdapat pada komputer diaudit. Identifikasi kerentanan tersebut sangat penting karena untuk melihat kondisi sistem sehingga mendapatkan tim ataupun individu bisa mengambil keputusan untuk melakukan sistem hardening tersebut. Program ini juga memiliki fitur untuk dicoba pada Dockerfile untuk identifikasi kerentanan yang terdapat pada file yang mendefinisikan container image.    

### Instalasi Lynis

Periksa apakah sistem yang akan diinstal `lynis` memiliki `sudo` privileges. Program `lynis` dapat diinstall pada beberapa distribusi Linux seperti Arch, Fedora, RHEL/CentOS, Debian, Ubuntu.

* Arch

```bash
sudo pacman -S lynis
```
* Fedora

```bash
sudo dnf install lynis
```
* RHEL/CentOS

```bash
sudo yum install lynis
```

* Debian/Ubuntu

```bash
sudo apt-get install lynis -y --fix-missing
```

### Menjalankan Audit

Program ini nantinya harus dilakukan dengan menggunakan `root` dengan perintah seperti dibawah ini 

```bash
sudo lynis
```

## Proses Audit desktop dengan Lynis

Proses Audit dengan menggunakan `lynis` akan memberikan informasi sesuai dengan jenis layanan yang diaudit. Audit dengan menggunakan desktop computer maka akan audit kernel, service, module, software pada OS. Audit dengan menggunakan server computer akan memberikan hasil audit service. Setelah hasil audit keluar maka amatilah celah keamanan dari masing-masing hasil audit.     

Berikut merupakan contoh dari proses audit desktop dengan perintah 

```bash
sudo lynis audit system
``` 

{{< figure src="../../static/images/lynis-audit.png" title="Result of Lynis Audit" >}}

`lynis` juga memberikan recomendation terkait hardening dari celah-celah keamanan yang dimiliki oleh desktop

{{< figure src="../../static/images/lynis-recommendation.png" title="Result of Lynis Recommendation" >}}

Hasil audit tersebut juga tersimpan pada directory `/var/log/lynis-report.dat`

## Audit Jaringan

Keamanan Jaringan juga merupakan hal yang penting dalam dunia IT dan Bisnis karena kasus penyerangan siber juga terjadi pada sebuah jaringan. Keamanan ini meliputi pemantauan trafik jaringan, informasi server, domain target, dan layanan yang akan dijadikan target. Information Gathering menjadi langkah awal untuk melakukan baik penyerangan maupun pertahanan jaringan komputer.

Contoh dari Information Gathering yaitu:

- Mengetahui Target Server dengan IP Publicnya 
- Mengetahui layanan yang terbuka dan berjalanan
- Mengetahui kepemilikan domain
- Mengetahui packet dan lalu lintas yang terjadi pada jaringan

## Tools Untuk Keamanan Jaringan 

Terdapat beberapa tools yang digunakan untuk melakukan pengujian keamanan jaringan baik untuk melakukan audit keamanan jaringan. Tools-tools ini memiliki beragam tujuan seperti mengetahui target, layanan yang terbuka, dll. 

- `nslookup` = mengetahui target server
- `nmap` = mengetaui target server, service yang terbuka dan berjalan 
- `nikto` = mengetahui target server, service yang terbuka dan berjalan  
- `whois` = menegathui kepemilikan domain
- `wireshark` = paket dalam jaringan dan lalu lintasnya
- `iptraf` = trafik dalam jaringan

# Kesimpulan

Pemanfaataan Audit pada keamanan informasi menjadi salah satu langkah yang penting agar sebagai Tenaga IT dapat mengamankan sebuah layanan komputer agar dapat melihat apa saja potensi serangan siber yang dapat terjadi pada sistem. Tools yang dapat membantu untuk melakukan audit ini adalah salah satunya `lynis` dan audit untuk jaringan dapat menggunakan `nslookup`, `nmap`, `nikto`, `whois`, `wireshark`, `iptraf`. 

# Reference

* Rhodes-Ousley, Mark,“Information Security: The Complete Reference“, McGraw Hill, New York, 2013
* Kurniawan, Yusuf, “Kriptografi Keamanan Internet dan Jaringan Komunikasi”, Informatika Bandung, Bandung, 2004
* Menezes, Alfred J., “Handbook of Applied Cryptography”, CRC Press, New York, 1997
* Stalling, Williams,“Network Security Essentials 4th Edition”, Prentice Hall, New Jersey, 2000
* Agus Eka Pratama, I Putu, “Keamanan Informasi”, Teknologi Informasi, Universitas Udayana, 2024 

