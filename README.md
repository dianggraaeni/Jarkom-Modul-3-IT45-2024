# Jarkom-Modul-3-IT45-2024

|           Nama               |     NRP    |
|            --                |     --     |
| Dian Anggraeni Putri         | 5027231016 |
| ⁠Abhirama Triadyatma Hermawan | 5027231061 |

### **Paradis (DHCP Relay)**
```bash
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.239.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.239.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.239.3.1
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 192.239.4.1
	netmask 255.255.255.0
```

---

### **Fritz (DNS Server)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.4.2
    netmask 255.255.255.0
    gateway 192.239.4.1
```

---

### **Tybur (DHCP Server)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.4.3
    netmask 255.255.255.0
    gateway 192.239.4.1
```

---

### **Warhammer (Database Server)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.3.4
    netmask 255.255.255.0
    gateway 192.239.3.1
```

---

### **Beast (Load Balancer Laravel)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.3.2
    netmask 255.255.255.0
    gateway 192.239.3.1
```

---

### **Colossal (Load Balancer PHP)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.3.3
    netmask 255.255.255.0
    gateway 192.239.3.1
```

---

### **Annie, Bertholdt, Reiner (Laravel Workers)**
## Annie
```bash
auto eth0
iface eth0 inet static
	address 192.239.1.2
	netmask 255.255.255.0
	gateway 192.239.1.1
```

## Bertholdt
```bash
auto eth0
iface eth0 inet static
    address 192.239.1.3
    netmask 255.255.255.0
    gateway 192.239.1.1
```

## Reiner
```bash
auto eth0
iface eth0 inet static
    address 192.239.1.4
    netmask 255.255.255.0
    gateway 192.239.1.1
```

---

### **Armin, Eren, Mikasa (PHP Workers)**
## Armin
```bash
auto eth0
iface eth0 inet static
    address 192.239.2.2
    netmask 255.255.255.0
    gateway 192.239.2.1
```

## Eren
```bash
auto eth0
iface eth0 inet static
    address 192.239.2.3
    netmask 255.255.255.0
    gateway 192.239.2.1
```

## Mikasa
```bash
auto eth0
iface eth0 inet static
    address 192.239.2.4
    netmask 255.255.255.0
    gateway 192.239.2.1
```

---

### **Zeke, Erwin (Clients)**
```bash
auto eth0
iface eth0 inet dhcp
```
---

### **Code**
```
apt-get update
apt-get install isc-dhcp-server -y
```

```
nano /etc/dhcp/dhcpd.conf
```

```
subnet 192.239.1.0 netmask 255.255.255.0 {
    range 192.239.1.5 192.239.1.25;
    range 192.239.1.50 192.239.1.100;
    option routers 192.239.1.1;
    option broadcast-address 192.239.1.255;
    option domain-name-servers 192.239.4.2;  # Fritz sebagai DNS Server
    default-lease-time 1800;  # Lease time 30 menit untuk Marley
    max-lease-time 5220;      # Lease time maksimal 87 menit
}

subnet 192.239.2.0 netmask 255.255.255.0 {
    range 192.239.2.9 192.239.2.27;
    range 192.239.2.81 192.239.2.243;
    option routers 192.239.2.1;
    option broadcast-address 192.239.2.255;
    option domain-name-servers 192.239.4.2;  # Fritz sebagai DNS Server
    default-lease-time 360;   # Lease time 6 menit untuk Eldia
    max-lease-time 5220;      # Lease time maksimal 87 menit
}

subnet 192.239.3.0 netmask 255.255.255.0 {
    option routers 192.239.3.1;
}

subnet 192.239.4.0 netmask 255.255.255.0 {
    option routers 192.239.4.1;
}
```

```
service isc-dhcp-server restart
```

```
apt-get update
apt-get install isc-dhcp-relay -y
```

```
nano /etc/default/isc-dhcp-relay
```

```
SERVERS="192.239.4.3"  # IP dari DHCP server (Tybur)
INTERFACES="eth1 eth2 eth3 eth4"  
OPTIONS=""
```

```
service isc-dhcp-relay restart
```

```
apt-get update
apt-get install bind9 -y
```

```
nano /etc/bind/named.conf.options
```

```
options {
    directory "/var/cache/bind";
    forwarders {
         192.168.122.1;  
    };
    allow-query { any; };
    listen-on-v6 { any; };
};
```

```
nano /etc/bind/named.conf.local
```

```
zone "marley.it45.com" {
    type master;
    file "/etc/bind/jarkom/marley.it45.com";
};

zone "eldia.it45.com" {
    type master;
    file "/etc/bind/jarkom/eldia.it45.com";
};
```

```
mkdir /etc/bind/jarkom
```

```
nano /etc/bind/jarkom/marley.it45.com
```

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    marley.it45.com. root.marley.it45.com. (
             2024102701        ; Serial
             604800        ; Refresh
             86400        ; Retry
             2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    marley.it45.com.
@       IN    A    192.239.1.2
```

```
nano /etc/bind/jarkom/eldia.it45.com
```

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    eldia.it45.com. root.eldia.it45.com. (
             2024102701        ; Serial
             604800        ; Refresh
             86400        ; Retry
             2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    eldia.it45.com.
@       IN    A    192.239.2.2
```

```
service bind9 restart
```

```
ifconfig
```

```
ping marley.it45.com
ping eldia.it45.com
```

---
## Testing No 2
![image](https://github.com/user-attachments/assets/f52125ee-3fab-4f97-8e7b-ed4ccc83de25)

## Testing No 3
![image](https://github.com/user-attachments/assets/0de16a1c-f443-4de0-9cb8-dd5f1d351ada)

## Testing No 4
![image](https://github.com/user-attachments/assets/3bc6008a-768d-4965-a54e-51aa1ff95322)

![image](https://github.com/user-attachments/assets/c18ec67b-203f-4af4-a37e-1468b48ffd2f)



