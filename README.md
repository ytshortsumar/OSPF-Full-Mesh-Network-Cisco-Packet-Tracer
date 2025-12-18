# OSPF Full Mesh Network Implementation Using Cisco Packet Tracer

## 📘 Project Overview
This project demonstrates the design and configuration of a **4-router Full Mesh network topology** using **OSPF (Open Shortest Path First)** in Cisco Packet Tracer.

The network is built completely from scratch, starting with hardware preparation, IP addressing, and finally dynamic routing configuration using **OSPF Area 0**. Each router is directly connected to every other router, ensuring high availability and multiple redundant paths.

---

## 🎯 Project Objectives
- Build a full mesh WAN topology
- Configure serial and LAN interfaces
- Implement **OSPF dynamic routing**
- Understand OSPF Area 0 operation
- Verify full connectivity and redundancy

---

## 🧱 Network Topology

### Devices Used
- **4 × Cisco 2811 Routers**
- **4 × PCs**
- **Serial WAN links (Full Mesh)**

Each router connects to:
- **1 LAN**
- **3 Serial WAN links** (to the other routers)

---

## ⚙️ Hardware Preparation

### Router Module Configuration
- Cisco 2811 routers do not have enough serial ports by default
- **Two WIC-2T modules** are added to each router
- This provides **4 serial interfaces per router**, sufficient for full mesh connectivity

---

## 🌐 IP Addressing Scheme

### LAN Networks
| Router | LAN Network | Gateway |
|-------|------------|---------|
| R0 | 192.168.10.0/24 | 192.168.10.1 |
| R1 | 192.168.20.0/24 | 192.168.20.1 |
| R2 | 192.168.30.0/24 | 192.168.30.1 |
| R3 | 192.168.40.0/24 | 192.168.40.1 |

---

### WAN Networks (Serial Links)
| Network | Connected Routers |
|-------|------------------|
| 192.168.50.0 | R0 ↔ R1 |
| 192.168.60.0 | R2 ↔ R3 |
| 192.168.70.0 | R0 ↔ R2 |
| 192.168.80.0 | R1 ↔ R3 |
| 192.168.90.0 | R1 ↔ R2 |
| 192.168.100.0 | R0 ↔ R3 |

---

## 🔁 Routing Protocol

### OSPF Configuration
- **Routing Protocol**: OSPF
- **Process ID**: 1
- **Area**: 0 (Backbone Area)
- **Wildcard Mask**: 0.0.0.255

Example:


router ospf 1
network 192.168.X.0 0.0.0.255 area 0

All routers participate in **Area 0**, allowing full route exchange and fast convergence.

---

## 🖥️ PC Configuration

| PC | IP Address | Subnet Mask | Default Gateway |
|----|-----------|-------------|-----------------|
| PC0 | 192.168.10.2 | 255.255.255.0 | 192.168.10.1 |
| PC1 | 192.168.30.2 | 255.255.255.0 | 192.168.30.1 |
| PC2 | 192.168.20.2 | 255.255.255.0 | 192.168.20.1 |
| PC3 | 192.168.40.2 | 255.255.255.0 | 192.168.40.1 |

## ✅ Verification & Testing

### OSPF Neighbor Verification
show ip ospf neighbor

Expected Result:
- All routers form OSPF adjacencies

---

### Routing Table Verification
show ip route


Expected Result:
- Routes marked with **O** (OSPF-learned routes)

---

### Connectivity Tests
- Ping between **any PC to any other PC** ✔
- Full connectivity confirmed across all LANs
- Multiple alternative paths available if a link fails

---

## 📂 Files Included
- `OSPF Mesh Network from Scratch.pkt`
- `README.md`

---

## 🧠 Key Learning Outcomes
- OSPF configuration and operation
- Full mesh WAN design
- Serial interface configuration
- OSPF Area 0 concepts
- Redundancy and fast convergence

---

## 🛠 Tools Used
- Cisco Packet Tracer
- Cisco 2811 Routers
- OSPF Dynamic Routing Protocol

---

## 👤 Author
**Umar Farooq**  
Networking Lab Assignment

