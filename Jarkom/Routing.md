Catatan routing:
- Routing berfungsi untuk menghubungkan network yang berbeda
- Routing dapat dilakukan dengan menggunakan switch pada layer 3
- Pada layer 4 atau aplikasi, yang dibutuhkan adalah server
- Tugas router adalah untuk memforward data menggunakan protokol (Algoritma Routing) -> Static dan Dynamic

Static Routing
- Pengisian tabel routing diisi manual oleh administrator

Tugas:
Routing dengan 3 router:
1. Routing Static
2. Routing IGRP
3. Routing OSPF
4. Routing BGP

Router 1 
Network1 : 192.168.10.0/24
Network2 : 192.168.11.0/24
Network3 : 192.168.12.0/22

Router 2
Network1: 192.168.20.0/24
Network2: 192.168.21.0/24

Router 3
Network1 : 192.168.30.0/24
Network2 : 192.168.31.0/24
Network3 : 192.168.32.0/23

Router 1 menuju Router 2
10.10.10..0/30

Router 2 menuju Router 3
20.20.20.0/30

Router 1
en
conf t
hostname Router-1
-- Masuk ke port gigabit
int gigabitEthernet 0/0
ip add 10.10.10.1 255.255.255.252
no sh
exit

Kasih IP ke fa
int fa 4/0
ip add 192.168.10.1 255.255.255.0
no sh
exit

int fa 5/0
ip add 192.168.11.1 255.255.255.0
no sh
exit

int fa 6/0
ip add 192.168.12.1 255.255.255.0
no sh
exit

Config DHCP
ip dhcp pool net1
default-router 192.168.10.1
network 192.168.10.0 255.255.255.0
exit

ip dhcp pool net11
default-router 192.168.11.1
network 192.168.11.0 255.255.255.0
exit

ip dhcp pool net12
default-router 192.168.12.1
network 192.168.12.0 255.255.255.0
exit
do wr mem

Router 2
hostname Router-2
int gigabitEthernet 1/0
ip add 10.10.10.2 255.255.255.252
no sh
exit

int gigabitEthernet 0/0
ip add 20.20.20.1 255.255.255.252
no sh
exit

Masukin ip ke fa
int fa 4/0
ip add 192.168.20.1 255.255.255.0
no sh
exit

int fa 5/0
ip add 192.168.21.1 255.255.255.0
no sh
exit

DHCP
ip dhcp pool net20
network 192.168.20.0 255.255.255.0
default-router 192.168.20.1
exit

ip dhcp pool net21
network 192.168.21.0 255.255.255.0
default-router 192.168.21.1
exit
do wr mem

Router 3
hostname Router-3
int gigabitEthernet1/0
ip add 20.20.20.2 255.255.255.252
no sh
exit

int fa4/0
ip add 192.168.30.1 255.255.255.0
no sh
exit

int fa5/0
ip add 192.168.31.1 255.255.255.0
no sh
exit

int fa6/0
ip add 192.168.32.1 255.255.255.0
no sh
exit

Configure DHCP
ip dhcp pool network30
default-router 192.168.30.0
network 192.168.30.0 255.255.255.0
exit

ip dhcp pool network31
default-router 192.168.31.0
network 192.168.31.0 255.255.255.0
exit

ip dhcp pool network32
default-router 192.168.32.0
network 192.168.32.0 255.255.255.0
exit
do wr mem


Routing static
Buka router 1
en 
conf t
ip route 192.168.10.0 255.255.255.0 10.10.10.2
ip route 192.168.11.0 255.255.255.0 10.10.10.2
ip route 192.168.12.0 255.255.255.0 10.10.10.2
ip route 192.168.20.0 255.255.255.0 10.10.10.2
ip route 192.168.21.0 255.255.255.0 10.10.10.2
ip route 192.168.30.0 255.255.255.0 10.10.10.2
ip route 192.168.31.0 255.255.255.0 10.10.10.2
ip route 192.168.32.0 255.255.255.0 10.10.10.2
Pakai jalur sebelahnya
ip route 20.20.20.0 255.255.255.252 10.10.10.2
do wr mem

Router 2
en
conf t
ip route 192.168.10.0 255.255.255.0 10.10.10.1
ip route 192.168.11.0 255.255.255.0 10.10.10.1
ip route 192.168.12.0 255.255.255.0 10.10.10.1
ip route 192.168.30.0 255.255.255.0 20.20.20.2
ip route 192.168.31.0 255.255.255.0 20.20.20.2
ip route 192.168.32.0 255.255.255.0 20.20.20.2
do wr mem

router 3
en
conf t
ip route 192.168.20.0 255.255.255.0 20.20.20.1
ip route 192.168.21.0 255.255.255.0 20.20.20.1
ip route 192.168.22.0 255.255.255.0 20.20.20.1
ip route 192.168.10.0 255.255.255.0 20.20.20.1
ip route 192.168.11.0 255.255.255.0 20.20.20.1
ip route 192.168.12.0 255.255.255.0 20.20.20.1
ip route 10.10.10.0 255.255.255.252 20.20.20.1
do wr mem

EIGRP
Hanya perlu tau network dirinya
Router 1
en
conf t
router eigrp 1 
network 192.168.10.0 0.0.0.255
network 10.10.10.0 0.0.0.3
no auto-summary
exit
do sh run
(ip classless)

Router 2
en
conf t
router eigrp 1
network 192.168.20.0
network 10.10.10.0
network 20.20.20.0
no auto-summary
exit
do sh run

Router 3
en conf t
router eigrp 1
network 20.20.20.0 0.0.0.3
network 192.168.30.0 0.0.0.255
no auto-summary
exit
do sh run

auto-summary -> dari class pool jadi classless

OSPF
Router 1
en
conf t
router ospf 1 
network 192.168.10.0 0.0.0.255 area 1
area di atur 
network 10.10.10.0 0.0.0.3 area 1

Router 2
en 
conf t
router ospf 1
network 192.168.20.0 0.0.0.255 area 1
network 10.10.10.0 0.0.0.3 area 1
network 20.20.20.0 0.0.0.3 area 1
exit
do wr mem

Router 3
en conf t
router ospf 1
network 20.20.20.0 0.0.0.3 area 1
network 192.168.30.0 0.0.0.255 area 1 
exit
do wr mem

BGP
diimplementasikan untuk isp
bgp hack net
Router 1
en 
conf t
router bgp 10 
(pake neighbor sama networknya)
neighbor 10.10.10.2 remote-as 20
network 192.168.10.0 mask 255.255.255.0
network 10.10.10.0 mask 255.255.255.252
exit
do wr mem

Router 2
Me remote dari router 1 ke route3
en 
conf t
router bgp 20
neighbor 10.10.10.1 remote-as 10
neighbor 20.20.20.2 remote-as 30
network 20.20.20.0 mask 255.255.255.252
network 10.10.10.0 mask 255.255.255.252
network 192.168.20.0 mask 255.255.255.0

Router 3
en 
conf t
router bgp 30
neighbor 20.20.20.1 remote-as 20
network 20.20.20.0 mask 255.255.255.252
network 192.168.30.0 mask 255.255.255.0
exit
do wr mem

harus di dhcp
laptop jadiin kabel pake cfe
