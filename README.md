# Jarkom-Modul-4-D04-2023
# Anggota Kelompok
|                Nama                |    NRP     |
| :--------------------------------: | :--------: |
|       Muhammad Rafi Sutrisno       | 5025211167 |
|      Nadira Milha Nailul Fath      | 5025211253 |
## Soal
1. Soal shift dikerjakan pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda.
Keterangan: Bila di CPT menggunakan VLSM, maka di GNS3 menggunakan CIDR atau sebaliknya
2. Jika tidak ada pemberitahuan revisi soal dari asisten, berarti semua soal BERSIFAT BENAR dan DAPAT DIKERJAKAN.
3. Untuk di GNS3 CLOUD merupakan NAT1 jangan sampai salah agar bisa terkoneksi internet.
4. Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan
5. Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.
## Topologi
### Cisco Packet Tracer
![Screenshot 2023-12-06 173130](https://github.com/nadiramlha/Jarkom-Modul-4-D04-2023/assets/88009253/04fe3987-15be-4a71-9150-d474be54804c)
### GNS3
## VLSM
Berikut Merupakan tree VLSM
![Jarkom4 (4) - Nadiramilhanf](https://github.com/nadiramlha/Jarkom-Modul-4-D04-2023/assets/88009253/d622db16-9e82-4cf0-a0f1-37cab6361d32)


## CIDR

Untuk perhitungan cidr kami menggunakan gns. Berikut adalah foto topologi :
![Alt text](./source/image0.png)

Berikutnya dilakukan penggabungan subnet. Penggabungan saya menggabungkan semua kemungkinan subnet yang bisa digabungkan pada setiap iterasi.
Berikut adalah tabel penggabungan nya :

![Alt text](./source/image.png)
![Alt text](./source/image-1.png)
![Alt text](./source/image-2.png)
![Alt text](./source/image-3.png)

Selanjutnya membuat tree, berikut adalah tree nya :
![Alt text](./source/tree.png)

Ip didapatkan dari calculator berikut :
![Alt text](./source/cal.png)

Selanjutnya didapatkan network id, netmask, dan broadcast dari masing masing subnet seperti berikut :
![Alt text](./source/image-4.png)

Lalu lakukan konfigurasi pada masing masing node sesuai dengan ip yang telah didapatkan.
Berikut adalah konfigurasi masing masing node :

AURA
```
auto eth0
iface eth0 inet dhcp
up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.193.0.0/14

auto eth1
iface eth1 inet static
	address 192.193.0.1
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.194.0.1
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 192.195.0.1
	netmask 255.255.255.252
```

FRIEREN
```
auto eth0
iface eth0 inet static
	address 192.193.0.2
	netmask 255.255.255.252
	gateway 192.193.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.193.128.1
	netmask 255.255.255.224

auto eth2
iface eth2 inet static
	address 192.193.192.1
	netmask 255.255.255.252
```
FLAMME
```
auto eth0
iface eth0 inet static
	address 192.193.192.2
	netmask 255.255.255.252
	gateway 192.193.192.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.193.224.1
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.193.240.1
	netmask 255.255.252.0

auto eth3
iface eth3 inet static
	address 192.193.248.1
	netmask 255.255.255.252
```
FERN
```
auto eth0
iface eth0 inet static
	address 192.193.224.2
	netmask 255.255.255.252
	gateway 192.193.224.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.193.232.1
	netmask 255.255.248.0
```
HIMMEL
```
auto eth0
iface eth0 inet static
	address 192.193.248.2
	netmask 255.255.255.252
	gateway 192.193.248.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.193.252.1
	netmask 255.255.255.248
```
EISEN
```
auto eth0
iface eth0 inet static
	address 192.195.0.2
	netmask 255.255.255.252
	gateway 192.195.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.196.32.1
	netmask 255.255.255.248

auto eth2
iface eth2 inet static
	address 192.196.0.1
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 192.196.64.1
	netmask 255.255.255.252

auto eth4
iface eth4 inet static
	address 192.196.128.1
	netmask 255.255.255.252
```
LINIE
```
auto eth0
iface eth0 inet static
	address 192.196.128.2
	netmask 255.255.255.252
	gateway 192.196.128.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.196.192.1
	netmask 255.255.254.0

auto eth2
iface eth2 inet static
	address 192.196.224.1
	netmask 255.255.255.252
```
LAWINE
```
auto eth0
iface eth0 inet static
	address 192.196.224.2
	netmask 255.255.255.252
	gateway 192.196.224.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.196.240.1
	netmask 255.255.255.192
```
HEITER
```
auto eth0
iface eth0 inet static
	address 192.196.240.2
	netmask 255.255.255.192
	gateway 192.196.240.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.196.248.1
	netmask 255.255.252.0
```
LUGNER
```
auto eth0
iface eth0 inet static
	address 192.196.64.2
	netmask 255.255.255.252
	gateway 192.196.64.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.196.112.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 192.196.96.1
	netmask 255.255.255.0
```

DANKEN
```
auto eth0
iface eth0 inet static
	address 192.194.0.2
	netmask 255.255.255.252
	gateway 192.194.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 192.194.128.1
	netmask 255.255.255.128
```

LAKEKORIDOR
```
auto eth0
iface eth0 inet static
	address 192.193.128.2
	netmask 255.255.255.224
	gateway 192.193.128.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
LAUBHILLS
```
auto eth0
iface eth0 inet static
	address 192.193.232.2
	netmask 255.255.255.224
	gateway 192.193.232.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
APETITREGION
```
auto eth0
iface eth0 inet static
	address 192.193.232.3
	netmask 255.255.255.224
	gateway 192.193.232.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
ROHRROAD
```
auto eth0
iface eth0 inet static
	address 192.193.240.2
	netmask 255.255.252.0
	gateway 192.193.240.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
SCHWERMOUNTAINS
```
auto eth0
iface eth0 inet static
	address 192.193.252.2
	netmask 255.255.255.248
	gateway 192.193.252.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
RICHTER
```
auto eth0
iface eth0 inet static
	address 192.196.32.2
	netmask 255.255.255.248
	gateway 192.196.32.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
REVOLTE
```
auto eth0
iface eth0 inet static
	address 192.196.32.3
	netmask 255.255.255.248
	gateway 192.196.32.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
BREDREGION
```
auto eth0
iface eth0 inet static
	address 192.196.240.2
	netmask 255.255.255.192
	gateway 192.196.240.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
SEIN
```
auto eth0
iface eth0 inet static
	address 192.196.248.2
	netmask 255.255.252.0
	gateway 192.196.248.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
REIGELCANYON
```
auto eth0
iface eth0 inet static
	address 192.196.248.3
	netmask 255.255.252.0
	gateway 192.196.248.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
GRANZCHANNEL
```
auto eth0
iface eth0 inet static
	address 192.196.192.2
	netmask 255.255.254.0
	gateway 192.196.192.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
GROBEFOREST
```
auto eth0
iface eth0 inet static
	address 192.196.96.2
	netmask 255.255.255.0
	gateway 192.196.96.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
TURKREGION
```
auto eth0
iface eth0 inet static
	address 192.196.112.2
	netmask 255.255.252.0
	gateway 192.196.112.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
STARK
```
auto eth0
iface eth0 inet static
	address 192.196.0.2
	netmask 255.255.252.0
	gateway 192.196.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
WILEREGION
```
auto eth0
iface eth0 inet static
	address 192.194.128.2
	netmask 255.255.255.128
	gateway 192.194.128.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
ROYALCAPITAL
```
auto eth0
iface eth0 inet static
	address 192.194.128.3
	netmask 255.255.255.128
	gateway 192.194.128.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

Selanjutnya setelah melakukan konfigurasi pada masing masing node, lakukan routing agar semua node terhubung. 
Berikut adalah scicpt untuk routing :

AURA
```
#Kiri
route add -net 192.193.128.0 netmask 255.255.255.224 gw 192.193.0.2
route add -net 192.193.192.0 netmask 255.255.255.252 gw 192.193.0.2
route add -net 192.193.224.0 netmask 255.255.255.252 gw 192.193.0.2 
route add -net 192.193.232.0 netmask 255.255.248.0 gw 192.193.0.2 
route add -net 192.193.240.0 netmask 255.255.252.0 gw 192.193.0.2 
route add -net 192.193.248.0 netmask 255.255.255.252 gw 192.193.0.2 
route add -net 192.193.252.0 netmask 255.255.255.248 gw 192.193.0.2 


#Kanan
route add -net 192.194.128.0 netmask 255.255.255.0 gw 192.194.0.2

#Bawah
route add -net 192.196.0.0 netmask 255.255.255.252 gw 192.195.0.2
route add -net 192.196.32.0 netmask 255.255.255.248 gw 192.195.0.2
route add -net 192.196.64.0 netmask 255.255.255.252 gw 192.195.0.2
route add -net 192.196.128.0 netmask 255.255.255.252 gw 192.195.0.2
route add -net 192.196.224.0 netmask 255.255.255.252 gw 192.195.0.2
route add -net 192.196.240.0 netmask 255.255.255.192 gw 192.195.0.2
route add -net 192.196.248.0 netmask 255.255.252.0 gw 192.195.0.2
route add -net 192.196.96.0 netmask 255.255.255.0 gw 192.195.0.2
route add -net 192.196.112.0 netmask 255.255.252.0 gw 192.195.0.2
route add -net 192.196.192.0 netmask 255.255.254.0 gw 192.195.0.2
```

FRIEREN
```
route add -net 192.193.224.0 netmask 255.255.255.252 gw 192.193.192.2
route add -net 192.193.232.0 netmask 255.255.248.0 gw 192.193.192.2
route add -net 192.193.240.0 netmask 255.255.252.0 gw 192.193.192.2
route add -net 192.193.248.0 netmask 255.255.255.252 gw 192.193.192.2
route add -net 192.193.252.0 netmask 255.255.255.248 gw 192.193.192.2 
```
FLEMME
```
route add -net 192.193.232.0 netmask 255.255.248.0 gw 192.193.224.2
route add -net 192.193.252.0 netmask 255.255.255.248 gw 192.193.248.2
```
FERN
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.193.224.1
```
HIMMEL
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.193.248.1
```
EISEN
```
route add -net 192.196.96.0 netmask 255.255.255.0 gw 192.196.64.2
route add -net 192.196.112.0 netmask 255.255.252.0 gw 192.196.64.2

route add -net 192.196.224.0 netmask 255.255.255.252 gw 192.196.128.2
route add -net 192.196.240.0 netmask 255.255.255.192 gw 192.196.128.2
route add -net 192.196.248.0 netmask 255.255.252.0 gw 192.196.128.2
route add -net 192.196.192.0 netmask 255.255.254.0 gw 192.196.128.2
```
LUGNER
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.196.64.1
```
LINIE ##
```
route add -net 192.196.240.0 netmask 255.255.255.192 gw 192.196.224.2
route add -net 192.196.248.0 netmask 255.255.252.0 gw 192.196.224.2
```
LAWINE
```
route add -net 192.196.248.0 netmask 255.255.252.0 gw 192.196.240.2
```
HEITER
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.196.240.1
```
DENKEN
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.193.0.1
```

Berikut adalah video DEMO 
- Testing berupa melakukan ping pada :
- Sein - Richter
- GranzChannel - Turk Region
- RiegelCanyon - Aura
- Fern - Linie
- RoyalCapital - LaubHills
- Heiter - Denken
- SchwerMountains - Lugner
<br/>
Link drive video : https://drive.google.com/file/d/10WvhPthwa2SKIA2pUfAyuI6AIV3fk3mG/view

