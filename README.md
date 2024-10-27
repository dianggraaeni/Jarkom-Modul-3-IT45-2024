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
```
apt-get update
apt-get install isc-dhcp-server -y
```


---
## Testing No 2
![image](https://github.com/user-attachments/assets/f52125ee-3fab-4f97-8e7b-ed4ccc83de25)

## Testing No 3
![image](https://github.com/user-attachments/assets/0de16a1c-f443-4de0-9cb8-dd5f1d351ada)

## Testing No 4
![image](https://github.com/user-attachments/assets/3bc6008a-768d-4965-a54e-51aa1ff95322)

![image](https://github.com/user-attachments/assets/c18ec67b-203f-4af4-a37e-1468b48ffd2f)



