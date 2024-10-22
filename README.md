# Jarkom-Modul-3-IT45-2024

### **Paradis (DHCP Relay)**
```bash
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.239.1.0
    netmask 255.255.255.0

auto eth2
iface eth2 inet static
    address 192.239.2.0
    netmask 255.255.255.0

auto eth3
iface eth3 inet static
    address 192.239.3.0
    netmask 255.255.255.0

auto eth4
iface eth4 inet static
    address 192.239.4.0
    netmask 255.255.255.0
```

---

### **Fritz (DNS Server)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.4.2
    netmask 255.255.255.0
    gateway 192.239.4.0
```

---

### **Tybur (DHCP Server)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.4.3
    netmask 255.255.255.0
    gateway 192.239.4.0
```

---

### **Warhammer (Database Server)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.3.4
    netmask 255.255.255.0
    gateway 192.239.3.0
```

---

### **Beast (Load Balancer Laravel)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.3.2
    netmask 255.255.255.0
    gateway 192.239.3.0
```

---

### **Colossal (Load Balancer PHP)**
```bash
auto eth0
iface eth0 inet static
    address 192.239.3.3
    netmask 255.255.255.0
    gateway 192.239.3.0
```

---

### **Annie, Bertholdt, Reiner (Laravel Workers)**
```bash
# Annie
auto eth0
iface eth0 inet static
    address 192.239.1.2
    netmask 255.255.255.0
    gateway 192.239.1.0

# Bertholdt
auto eth0
iface eth0 inet static
    address 192.239.1.3
    netmask 255.255.255.0
    gateway 192.239.1.0

# Reiner
auto eth0
iface eth0 inet static
    address 192.239.1.4
    netmask 255.255.255.0
    gateway 192.239.1.0
```

---

### **Armin, Eren, Mikasa (PHP Workers)**
```bash
# Armin
auto eth0
iface eth0 inet static
    address 192.239.2.2
    netmask 255.255.255.0
    gateway 192.239.2.0

# Eren
auto eth0
iface eth0 inet static
    address 192.239.2.3
    netmask 255.255.255.0
    gateway 192.239.2.0

# Mikasa
auto eth0
iface eth0 inet static
    address 192.239.2.4
    netmask 255.255.255.0
    gateway 192.239.2.0
```

---

### **Zeke, Erwin (Clients)**
```bash
auto eth0
iface eth0 inet dhcp
```

---
