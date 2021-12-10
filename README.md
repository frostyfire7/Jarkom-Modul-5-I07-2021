# Jarkom-Modul-5-I07-2021

Ascarya Arkaandhiyaa Allaam (05111942000027)\
Farah Dhiah Qorirah (05111942000018)\
Julius Adetya Eka Bhaswara (05111942000026)

## (A) Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Luffy dibawah ini

![image](https://user-images.githubusercontent.com/77782259/145575814-f089ae9d-b104-4f81-b3c6-706245711bb1.png)

Keterangan :\
    Doriki adalah DNS Server\
		Jipangu adalah DHCP Server\
		Maingate dan Jorge adalah Web Server\
		Jumlah Host pada Blueno adalah 100 host\
		Jumlah Host pada Cipher adalah 700 host\
		Jumlah Host pada Elena adalah 300 host\
		Jumlah Host pada Fukurou adalah 200 host
    
## (B) Karena kalian telah belajar subnetting dan routing, Luffy ingin meminta kalian untuk membuat topologi tersebut menggunakan teknik CIDR atau VLSM. setelah melakukan subnetting

### Subnet

![image](https://user-images.githubusercontent.com/77782259/145575912-62376fd7-1953-469b-a1f9-b9a5f63febf2.png)

### Tabel Subnet
**Subnet**|**Node**|**IP**|**Subnet Mask**|**Length**|
:-------:| :-------:|:-------:|:-------:|:-------:|
| A | Water7  	|  10.41.7.1	|  255.255.255.128	|	/25  	|
| A | Blueno	|  10.41.7.2  	|  255.255.255.128	|	    	|
| B | Water7	|  10.41.7.129  |  255.255.255.248	|	/29    	|
| B | Doriki	|  10.41.7.130  |  255.255.255.248	|	    	|
| B | Jipangu	|  10.41.7.131  |  255.255.255.248	|	    	|
| C | Water7	|  10.41.0.1  	|  255.255.252.0	|	/22    	|
| C | Ciper	|  10.41.0.2  	|  255.255.252.0	|	   	|
| D | Foosha	|  10.41.7.145	|  255.255.255.252	|	/30    	|
| D | Water7	|  10.41.7.146	|  255.255.255.252	|	    	|
| E | Foosha	|  10.41.7.149	|  255.255.255.252	|	/30    	|
| E | Guanhao	|  10.41.7.150	|  255.255.255.252	|	    	|
| F | Guanhao	|  10.41.6.1  	|  255.255.255.0	|	/24    	|
| F | Elena	|  10.41.6.2  	|  255.255.255.0	|	    	|
| G | Guanhao	|  10.41.7.137	|  255.255.255.248	|	/29  	|
| G | Jorge	|  10.41.7.138	|  255.255.255.248	|	    	|
| G | Maingate	|  10.41.7.139	|  255.255.255.248	|	    	|
| H | Guanhao	|  10.41.4.2  	|  255.255.254.0	|	/23   	|
| H | Fukurou	|  10.41.4.2  	|  255.255.254.0	|	    	|


### Subnet Tree

![image](https://user-images.githubusercontent.com/77782259/145576019-e57c86fd-c4e6-4421-9913-8c29e258a3c5.png)
## CONFIG NODE
### FOOSHA
```shell
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddress ether 5e:0d:2e:c6:9b:9a

auto eth1
iface eth1 inet static
	address 10.41.7.145
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.41.7.149
	netmask 255.255.255.252
```
### WATER7
```shell
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.41.7.146
	netmask 255.255.255.252
  	gateway 10.41.7.145
  
auto eth1
iface eth1 inet static
	address 10.41.7.1
	netmask 255.255.255.128
  
auto eth2
iface eth2 inet static
  address 10.41.7.129
  netmask 255.255.255.248


auto eth3
iface eth3 inet static
  address 10.41.0.1
  netmask 255.255.252.0
```
### GUANHAO
```shell
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.41.7.150
	netmask 255.255.255.252
  	gateway 10.41.7.149
  
auto eth1
iface eth1 inet static
	address 10.41.6.1
	netmask 255.255.255.0
  
auto eth2
iface eth2 inet static
  address 10.41.7.137
  netmask 255.255.255.248


auto eth3
iface eth3 inet static
  address 10.41.4.1
  netmask 255.255.254.0
```
### Blueno
```shell
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.41.7.2
	netmask 255.255.255.128
	gateway 10.41.7.1
```
### Doriki
```shell
auto eth0
iface eth0 inet static
	address 10.41.7.130
	netmask 255.255.255.248
	gateway 10.41.7.129	
```
### Jipangu
```shell
auto eth0
iface eth0 inet static
	address 10.41.7.131
	netmask 255.255.255.248
	gateway 10.41.7.129
```
### Cipher
```shell
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.41.0.2
	netmask 255.255.252.0
	gateway 10.41.0.1
```
### Fukurou
```shell
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.41.4.2
	netmask 255.255.254.0
	gateway 10.41.4.1
```
### Maingate
```shell
auto eth0
iface eth0 inet static
	address 10.41.7.139
	netmask 255.255.255.248
	gateway 10.41.7.137
```
### Jorge
```shell
auto eth0
iface eth0 inet static
	address 10.41.7.138
	netmask 255.255.255.248
	gateway 10.41.7.137
```
### Elena
```shell
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.41.6.2
	netmask 255.255.255.0
	gateway 10.41.6.2
```
## (C) Setelah melakukan subnetting, Kalian juga diharuskan melakukan Routing agar setiap perangkat pada jaringan tersebut dapat terhubung.
## Routing
### FOOSHA
```shell
# !/bin/sh

route add -net 10.41.7.0 netmask 255.255.255.128 gw 10.41.7.146
route add -net 10.41.7.128 netmask 255.255.255.248 gw 10.41.7.146
route add -net 10.41.0.0 netmask 255.255.252.0 gw 10.41.7.146

route add -net 10.41.6.0 netmask 255.255.255.0 gw 10.41.7.150
route add -net 10.41.7.136 netmask 255.255.255.248 gw 10.41.7.150
route add -net 10.41.4.0 netmask 255.255.254.0 gw 10.41.7.150
```
### WATER7
```shell
# !/bin/sh

route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.41.7.145
```
## GUANHAO
```shell
# !/bin/sh

route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.38.7.149
```
nano ./.bashrc
```shell
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.38.0.0/16
```
## D. Tugas berikutnya adalah memberikan ip pada subnet Blueno, Cipher, Fukurou, dan Elena secara dinamis menggunakan bantuan DHCP server. Kemudian kalian ingat bahwa kalian harus setting DHCP Relay pada router yang menghubungkannya.
### Doriki (DNS Server)
nano config.sh
```shell
# !/bin/sh

apt-get update
apt-get install bind9 -y
```
### Jipangu (DHCP Server)
nano config.sh
```shell
# !/bin/sh

apt-get update
apt-get install isc-dhcp-server -y
```
nano isc-dhcp-server
```shell
INTERFACES="eth0"
```
nano dhcpd.conf
```shell
# Blueno
subnet 10.41.7.0 netmask 255.255.255.128 {
    range 10.41.7.2 10.41.7.126;
    option routers 10.41.7.1;
    option broadcast-address 10.41.7.127;
    option domain-name-servers 10.41.7.130;
    default-lease-time 360;
    max-lease-time 7200;
}

# Cipher
subnet 10.41.0.0 netmask 255.255.252.0	 {
    range 10.41.0.2 10.41.3.254;
    option routers 10.41.0.1;
    option broadcast-address 10.41.3.255;
    option domain-name-servers 10.41.7.130;
    default-lease-time 720;
    max-lease-time 7200;
}

# Fukurou
subnet 10.41.4.0 netmask 255.255.254.0 {
    range 10.41.4.2 10.41.5.254;
    option routers 10.41.4.1;
    option broadcast-address 10.41.5.255;
    option domain-name-servers 10.41.7.130;
    default-lease-time 720;
    max-lease-time 7200;
}

# Elena
subnet 10.41.6.0 netmask 255.255.255.0 {
    range 10.41.6.2 10.41.6.254;
    option routers 10.41.6.1;
    option broadcast-address 10.41.6.255;
    option domain-name-servers 10.41.7.130;
    default-lease-time 720;
    max-lease-time 7200;
}

# Routing dari Jipangu ke router Water7
subnet 10.41.7.128 netmask 255.255.255.248 {
        option routers 10.41.7.129;
}

# Routing dari Jipangu ke router Guanhao
subnet 10.41.7.136 netmask 255.255.255.248 {
        option routers 10.41.7.137;
}

# Routing dari Jipangu ke router Foosha
subnet 10.41.7.144 netmask 255.255.255.252 {
        option routers 10.41.7.145;
}

# Routing dari Foosha ke Guanhao
subnet 10.41.7.148 netmask 255.255.255.252 {
        option routers 10.41.7.149;
}

# Water7
#subnet 10.41.7.144 netmask 255.255.255.252 {
#        option routers 10.41.7.145;
#}

# Guanhao
#subnet 10.41.7.148 netmask 255.255.255.252 {
#        option routers 10.41.7.149;
#}

host FOOSHA {
    hardware ethernet 5e:0d:2e:c6:9b:9a;
    fixed-address 192.168.122.98;
}
```
[Redacted] Foosha (DHCP Relay)
nano config.sh
```shell
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start
```
nano /etc/default/isc-dhcp-relay
```shell
# What servers should the DHCP relay forward requests to?
SERVERS="10.41.7.131"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```
Water7 (DHCP Relay)
nano config.sh
```shell
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start
```
nano /etc/default/isc-dhcp-relay
```shell
# What servers should the DHCP relay forward requests to?
SERVERS="10.41.7.131"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2 eth3"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```
Guanhao (DHCP Relay)
nano config.sh
```shell
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start
```
nano /etc/default/isc-dhcp-relay
```shell
# What servers should the DHCP relay forward requests to?
SERVERS="10.41.7.131"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2 eth3"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```
### Maingate (Web Server)

nano config.sh
```shell
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start
```
### Jorge (Web Server)

nano config.sh
```shell
# !/bin/sh

apt-get update
```
### Blueno (Client)

All

Config ditambah:
```shell
auto eth0
iface eth0 inet dhcp
```
nano config.sh
```shell
# !/bin/sh
```
Cipher
```shell
# !/bin/sh
```
Fukurou
```shell
# !/bin/sh
```
Elena
```shell
# !/bin/sh
```
## 1) Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.
nano config.sh on Foosha
```shell
iptables -t nat -A POSTROUTING -s 10.41.0.0/21 -o eth0 -j SNAT --to-source 192.168.122.98
```
Yang Butuh Update (Water7, Doriki, Jipangu, dan Guanhao)
```shell
echo nameserver 192.168.122.1 > /etc/resolv.conf
```
Testing

Screenshot

## 2) Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang memiliki ip DHCP dan DNS Server demi menjaga keamanan.
nano config.sh on Foosha
```shell
iptables -A FORWARD -p tcp --dport 80 -d 10.41.7.128/29 -i eth0 -j DROP
```
```shell
# doriki DNS
iptables -A INPUT -s 10.41.7.130 -j DROP
# subnet a2, a3, a6, a7
iptables -A INPUT -s 10.41.7.0/25 -j DROP
iptables -A INPUT -s 10.41.0.0/22 -j DROP
iptables -A INPUT -s 10.41.4.0/23 -j DROP
iptables -A INPUT -s 10.41.6.0/24 -j DROP
```
```shell
iptables -A INPUT -p tcp --dport 80 -j DROP
```
Test
```shell
nmap 10.41.7.128
nmap 10.41.7.131
```
Screenshot

## 3) Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.
nano config.sh on Jipangu and Doriki
```shell
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```
Screenshot

Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut:

## 4) Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis
### Doriki
```shell
iptables -A INPUT -s 10.41.7.0/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 10.41.7.0/25 -m time --timestart 15:01 --timestop 23:59 -j REJECT
iptables -A INPUT -s 10.41.7.0/25 -m time --timestart 00:00 --timestop 06:59 -j REJECT
iptables -A INPUT -s 10.41.7.0/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Fri,Sat,Sun -j REJECT

iptables -A INPUT -s 10.41.0.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 10.41.0.0/22 -m time --timestart 15:01 --timestop 06:59 -j REJECT
iptables -A INPUT -s 10.41.0.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Fri,Sat,Sun -j REJECT
```
```shell
date
```
```shell
Senin
date -s "6 DEC 2021 08:00:00" -> bisa
date -s "6 DEC 2021 18:00:00" -> gabisa


Sabtu
date -s "13 NOV 2021 09:00:00" -> gabisa
date -s "13 NOV 2021 01:00:00" -> gabisa
```
Screenshot

## 5) Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.
```shell
iptables -A INPUT -s 10.41.6.0/24 -m time --timestart 15:01 --timestop 06:59 -j REJECT

iptables -A INPUT -s 10.41.4.0/23 -m time --timestart 15:01 --timestop 06:59 -j REJECT
```
Screenshot

Selain itu di reject

## 6) Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate
```shell
iptables -t nat -A PREROUTING -p tcp -d 10.41.7.130 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.41.7.138:80
iptables -t nat -A PREROUTING -p tcp -d 10.41.7.130 -j DNAT --to-destination 10.41.7.139:80
iptables -t nat -A POSTROUTING -p tcp -d 10.41.7.138 --dport 80 -j SNAT --to-source 10.41.7.130
iptables -t nat -A POSTROUTING -p tcp -d 10.41.7.139 --dport 80 -j SNAT --to-source 10.41.7.130
```
Luffy berterima kasih pada kalian karena telah membantunya. Luffy juga mengingatkan agar semua aturan iptables harus disimpan pada sistem atau paling tidak kalian menyediakan script sebagai backup

