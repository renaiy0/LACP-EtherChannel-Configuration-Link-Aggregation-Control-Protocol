# 🛡️ Enterprise Network Security Infrastructure
## Multi-Zone Cisco ASA Firewall with OSPF Dynamic Routing

<div align="center">

![Cisco](https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![ASA](https://img.shields.io/badge/ASA_5506X-FF0000?style=for-the-badge)
![OSPF](https://img.shields.io/badge/OSPF-00BCB4?style=for-the-badge)
![Security](https://img.shields.io/badge/Network_Security-4A154B?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Production_Ready-success?style=for-the-badge)

**Advanced enterprise network architecture with zone-based firewall, dynamic routing, and DMZ implementation**

*Complete simulation of real-world corporate network infrastructure with multi-layered security*

[View Topology](#-network-topology) • [Configuration](#-complete-configuration) • [Testing](#-testing--verification) • [Troubleshooting](#-troubleshooting-guide)

---

[![Cisco ASA](https://img.shields.io/badge/Firewall-ASA_5506X-red)](https://www.cisco.com/c/en/us/products/security/asa-5506-x-firewall/index.html)
[![OSPF](https://img.shields.io/badge/Routing-OSPFv2-blue)](https://www.cisco.com/c/en/us/support/docs/ip/open-shortest-path-first-ospf/7039-1.html)
[![Packet Tracer](https://img.shields.io/badge/Simulation-Packet_Tracer_8.2-orange)](https://www.netacad.com/courses/packet-tracer)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## 📋 Table of Contents

- [🎯 Project Overview](#-project-overview)
- [🏗️ Network Architecture](#️-network-architecture)
- [🖼️ Network Topology](#️-network-topology)
- [📊 IP Addressing Scheme](#-ip-addressing-scheme)
- [⚙️ Device Configuration](#️-device-configuration)
  - [ASA Firewall Setup](#-cisco-asa-5506-x-firewall-configuration)
  - [OSPF Router Configuration](#-ospf-router-configuration)
  - [Static Routing](#-static-routing-configuration)
- [🔐 Security Implementation](#-security-implementation)
- [🛰️ Routing Protocol Details](#️-routing-protocol-details)
- [📸 Configuration Screenshots](#-configuration-screenshots)
- [🧪 Testing & Verification](#-testing--verification)
- [🐛 Troubleshooting Guide](#-troubleshooting-guide)
- [🔒 Security Best Practices](#-security-best-practices)
- [📁 Project Structure](#-project-structure)
- [🎓 Learning Objectives](#-learning-objectives)
- [🚀 Getting Started](#-getting-started)
- [📚 Additional Resources](#-additional-resources)

---

## 🎯 Project Overview

This project demonstrates a **production-grade enterprise network infrastructure** featuring:

### Core Components

🔥 **Multi-Zone Firewall Architecture**
- Cisco ASA 5506-X with three security zones (IN/DMZ/OUT)
- Zone-based security policies with hierarchical trust levels
- Stateful packet inspection and connection tracking
- NAT/PAT for internal-to-external communication

🛰️ **Dynamic Routing Protocol**
- OSPFv2 implementation across multiple routers
- Area 0 (backbone) configuration
- Automatic route discovery and convergence
- Load balancing and redundancy

🌐 **Network Segmentation**
- Internal LAN for corporate users
- DMZ zone for public-facing servers
- External/Internet connectivity zone
- User network with OSPF integration

🔐 **Enterprise Security Features**
- Password-protected management access
- User authentication and authorization
- Security level enforcement (0-100 scale)
- Access control lists and traffic filtering

### Key Implementation Highlights

✨ **Three-Layer Network Architecture** - Segregation of internal, DMZ, and external networks  
🔄 **Hybrid Routing** - Combination of static and dynamic routing protocols  
🛡️ **Defense in Depth** - Multiple security layers for comprehensive protection  
📡 **Scalable Design** - Easily expandable to accommodate growth  
🎯 **Best Practice Implementation** - Industry-standard network design patterns  

### Real-World Applications

This topology simulates:
- **Corporate Headquarters** with internal users and public servers
- **Branch Office Connectivity** via OSPF routing
- **Internet Gateway** with firewall protection
- **DMZ Services** hosting web/email/DNS servers
- **Secure Remote Access** for administrators

---

## 🏗️ Network Architecture

### 🔹 Zone-Based Security Design
```
┌─────────────────────────────────────────────────────────────┐
│                    CISCO ASA 5506-X                         │
│                   Security Appliance                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   ┌───────────────┐  ┌───────────────┐  ┌──────────────┐  │
│   │   IN ZONE     │  │   DMZ ZONE    │  │  OUT ZONE    │  │
│   │  Security 10  │  │  Security 50  │  │ Security 0   │  │
│   └───────┬───────┘  └───────┬───────┘  └──────┬───────┘  │
│           │                  │                  │          │
└───────────┼──────────────────┼──────────────────┼──────────┘
            │                  │                  │
            ▼                  ▼                  ▼
    ┌───────────────┐  ┌──────────────┐  ┌──────────────┐
    │  Internal LAN │  │ Public Servers│  │   Internet   │
    │ 192.168.100.x │  │  172.16.10.x  │  │  50.50.50.x  │
    │               │  │               │  │              │
    │  • PC Clients │  │  • Web Server │  │  • Gateway   │
    │  • Workstations│  │  • DB Server  │  │  • ISP Link  │
    └───────────────┘  └──────────────┘  └──────────────┘
```

### 🔹 Network Segments Overview

#### 🟢 **Internal Zone (IN)** - Security Level 10

**Purpose:** Corporate internal network for trusted users and devices

**Network Details:**
- **Subnet:** `192.168.100.0/25`
- **Gateway:** `192.168.100.1` (ASA Gi1/1)
- **Available Hosts:** 126 addresses
- **Security Level:** 10 (Highest Trust)

**Connected Devices:**
- 💻 PC0 - Internal Workstation
- 💻 PC1 - Internal Workstation
- 🔌 Cisco 2960-24TT Switch
- 📡 Multiple client endpoints

**Characteristics:**
- Full internet access via NAT
- Access to DMZ servers (controlled)
- Restricted inbound access from external networks
- Protected by stateful firewall inspection

#### 🟡 **User Network** - OSPF Integrated

**Purpose:** Secondary user segment with dynamic routing

**Network Details:**
- **Subnet:** `10.10.10.0/24`
- **Gateway:** Router Fa0/1 (`10.10.10.1`)
- **Routing:** OSPF Area 0
- **Available Hosts:** 254 addresses

**Connected Devices:**
- 🖥️ PC4 - User workstation
- 🔀 Cisco 2911 Router
- 📊 OSPF-enabled infrastructure

**Characteristics:**
- Dynamic route learning via OSPF
- Redundant path availability
- Automatic failover capability
- Inter-site connectivity

#### 🔵 **DMZ Zone (Demilitarized Zone)** - Security Level 50

**Purpose:** Public-facing services accessible from internet

**Network Details:**
- **Subnet:** `172.16.10.0/24`
- **Gateway:** `172.16.10.1` (ASA Gi1/2)
- **Available Hosts:** 254 addresses
- **Security Level:** 50 (Medium Trust)

**Hosted Services:**
- 🌐 Server1 - Web Server (HTTP/HTTPS)
- 💾 Server2 - Database Server
- 📧 Server3 - Email/DNS Server

**Characteristics:**
- Limited access to internal network
- Controlled internet access
- Publically accessible (with port forwarding)
- Isolated from internal resources

#### 🔴 **External Zone (OUT)** - Security Level 0

**Purpose:** Internet connectivity and external communications

**Network Details:**
- **Subnet:** `50.50.50.0/24`
- **Gateway:** ASA Gi1/3 (`50.50.50.2`)
- **Upstream Router:** `50.50.50.1`
- **Security Level:** 0 (Untrusted)

**Characteristics:**
- Direct internet connectivity
- Source for all inbound traffic
- NAT translation endpoint
- Highest scrutiny for incoming packets

#### 🟣 **OSPF Backbone Area**

**Purpose:** Dynamic routing infrastructure

**Network Details:**
- **Primary Subnet:** `20.20.20.0/24`
- **Protocol:** OSPFv2 (Area 0)
- **Process ID:** 10

**OSPF Participants:**
- Router @ `20.20.20.2` (Fa0/1)
- Router @ `10.10.10.1` (Fa0/0)
- Advertised networks: `10.10.10.0/24`, `20.20.20.0/24`

**Characteristics:**
- Automatic route discovery
- Sub-second convergence
- Load balancing across equal-cost paths
- Scalable for future growth

---

## 🖼️ Network Topology

<div align="center">
  <img src="assets/topology.png" alt="Complete Network Architecture" width="1000"/>
  <p><em>Complete enterprise network topology with multi-zone security architecture</em></p>
</div>

### Topology Components

| Component | Model | Quantity | Purpose |
|-----------|-------|----------|---------|
| **Firewall** | Cisco ASA 5506-X | 1 | Multi-zone security appliance |
| **Router** | Cisco 2911 | 3 | Layer 3 routing and OSPF |
| **Switch** | Cisco 2960-24TT | 3 | Layer 2 switching |
| **Server** | Generic PT Server | 3 | DMZ services (Web/DB/Email) |
| **Workstation** | Generic PT PC | 4 | End-user devices |

### Connection Matrix
```
ASA (PERIMETER)
├─── Gi1/1 (IN) ────────► Switch1 ────► PC0, PC1 (Internal Network)
│
├─── Gi1/2 (DMZ) ───────► Switch2 ────► Server1, Server2, Server3
│
└─── Gi1/3 (OUT) ───────► Router4 ────► Internet Gateway
                              │
                              ├────────► OSPF Router (20.20.20.x)
                              │
                              └────────► User Network (10.10.10.x)
```

---

## 📊 IP Addressing Scheme

### Complete Address Allocation Table

| Device/Interface | IP Address | Subnet Mask | Default Gateway | Network | VLAN/Zone |
|------------------|------------|-------------|-----------------|---------|-----------|
| **ASA - Gi1/1 (IN)** | 192.168.100.1 | 255.255.255.128 | - | 192.168.100.0/25 | IN |
| **ASA - Gi1/2 (DMZ)** | 172.16.10.1 | 255.255.255.0 | - | 172.16.10.0/24 | DMZ |
| **ASA - Gi1/3 (OUT)** | 50.50.50.2 | 255.255.255.0 | 50.50.50.1 | 50.50.50.0/24 | OUT |
| **Switch1** | 192.168.100.254 | 255.255.255.128 | 192.168.100.1 | Internal | IN |
| **PC0** | 192.168.100.2 | 255.255.255.128 | 192.168.100.1 | Internal | IN |
| **PC1** | 192.168.100.3 | 255.255.255.128 | 192.168.100.1 | Internal | IN |
| **Server1 (Web)** | 172.16.10.2 | 255.255.255.0 | 172.16.10.1 | DMZ | DMZ |
| **Server2 (DB)** | 172.16.10.3 | 255.255.255.0 | 172.16.10.1 | DMZ | DMZ |
| **Server3 (Email)** | 172.16.10.4 | 255.255.255.0 | 172.16.10.1 | DMZ | DMZ |
| **Router4 - Fa0/1** | 50.50.50.1 | 255.255.255.0 | - | External | OUT |
| **Router4 - Fa0/0** | 20.20.20.1 | 255.255.255.0 | - | OSPF Backbone | - |
| **OSPF Router - Fa0/1** | 20.20.20.2 | 255.255.255.0 | - | OSPF Backbone | - |
| **OSPF Router - Fa0/0** | 10.10.10.1 | 255.255.255.0 | - | User Network | - |
| **PC4** | 10.10.10.2 | 255.255.255.0 | 10.10.10.1 | User Network | - |

### Subnet Summary
```
┌─────────────────────────────────────────────────────────────────┐
│ Network Segment Summary                                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  📍 Internal LAN (IN Zone)                                      │
│     Network:     192.168.100.0/25                              │
│     Usable IPs:  192.168.100.1 - 192.168.100.126              │
│     Broadcast:   192.168.100.127                              │
│     Hosts:       126                                           │
│                                                                 │
│  📍 DMZ Segment                                                 │
│     Network:     172.16.10.0/24                               │
│     Usable IPs:  172.16.10.1 - 172.16.10.254                 │
│     Broadcast:   172.16.10.255                                │
│     Hosts:       254                                           │
│                                                                 │
│  📍 External Network (OUT Zone)                                 │
│     Network:     50.50.50.0/24                                │
│     Usable IPs:  50.50.50.1 - 50.50.50.254                   │
│     Broadcast:   50.50.50.255                                 │
│     Hosts:       254                                           │
│                                                                 │
│  📍 User Network (OSPF)                                         │
│     Network:     10.10.10.0/24                                │
│     Usable IPs:  10.10.10.1 - 10.10.10.254                   │
│     Broadcast:   10.10.10.255                                 │
│     Hosts:       254                                           │
│                                                                 │
│  📍 OSPF Backbone                                               │
│     Network:     20.20.20.0/24                                │
│     Usable IPs:  20.20.20.1 - 20.20.20.254                   │
│     Broadcast:   20.20.20.255                                 │
│     Hosts:       254                                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## ⚙️ Device Configuration

### 🔥 Cisco ASA 5506-X Firewall Configuration

#### Step 1: Basic Configuration
```cisco
ciscoasa> enable
ciscoasa# configure terminal

! Set hostname
ciscoasa(config)# hostname PERIMETER
PERIMETER(config)#

! Configure enable password
PERIMETER(config)# enable password maliq

! Create user accounts
PERIMETER(config)# username PERIMETER password HALIQ privilege 15
PERIMETER(config)# username mal password HALIQ privilege 15

! Set domain name (required for SSH)
PERIMETER(config)# domain-name enterprise.local
```

#### Step 2: Interface Configuration

##### Configure INSIDE Interface (Gi1/1)
```cisco
PERIMETER(config)# interface GigabitEthernet1/1
PERIMETER(config-if)# nameif IN
INFO: Security level for "IN" set to 0 by default.

PERIMETER(config-if)# security-level 10
PERIMETER(config-if)# ip address 192.168.100.1 255.255.255.128
PERIMETER(config-if)# no shutdown
PERIMETER(config-if)# description Internal Corporate Network
PERIMETER(config-if)# exit

! Verify configuration
PERIMETER# show interface GigabitEthernet1/1
```

##### Configure DMZ Interface (Gi1/2)
```cisco
PERIMETER(config)# interface GigabitEthernet1/2
PERIMETER(config-if)# nameif DMZ
INFO: Security level for "DMZ" set to 0 by default.

PERIMETER(config-if)# security-level 50
PERIMETER(config-if)# ip address 172.16.10.1 255.255.255.0
PERIMETER(config-if)# no shutdown
PERIMETER(config-if)# description Public DMZ Services
PERIMETER(config-if)# exit
```

##### Configure OUTSIDE Interface (Gi1/3)
```cisco
PERIMETER(config)# interface GigabitEthernet1/3
PERIMETER(config-if)# nameif OUT
INFO: Security level for "OUT" set to 0 by default.

PERIMETER(config-if)# security-level 0
PERIMETER(config-if)# ip address 50.50.50.2 255.255.255.0
PERIMETER(config-if)# no shutdown
PERIMETER(config-if)# description External Internet Connection
PERIMETER(config-if)# exit
```

#### Step 3: Static Routing Configuration
```cisco
! Default route to Internet
PERIMETER(config)# route OUT 0.0.0.0 0.0.0.0 50.50.50.1 1

! Route to User Network via OSPF router
PERIMETER(config)# route OUT 10.10.10.0 255.255.255.0 20.20.20.1 1

! Route to OSPF backbone area
PERIMETER(config)# route OUT 20.20.20.0 255.255.255.0 50.50.50.1 1

! Route to internal segments (directly connected - automatic)
! 192.168.100.0/25 via Gi1/1 (automatic)
! 172.16.10.0/24 via Gi1/2 (automatic)

! Verify routing table
PERIMETER# show route

Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, V - VPN
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, + - replicated route

Gateway of last resort is 50.50.50.1 to network 0.0.0.0

S*   0.0.0.0 0.0.0.0 [1/0] via 50.50.50.1, OUT
S    10.10.10.0 255.255.255.0 [1/0] via 20.20.20.1, OUT
S    20.20.20.0 255.255.255.0 [1/0] via 50.50.50.1, OUT
C    50.50.50.0 255.255.255.0 is directly connected, OUT
L    50.50.50.2 255.255.255.255 is directly connected, OUT
C    172.16.10.0 255.255.255.0 is directly connected, DMZ
L    172.16.10.1 255.255.255.255 is directly connected, DMZ
C    192.168.100.0 255.255.255.128 is directly connected, IN
L    192.168.100.1 255.255.255.255 is directly connected, IN
```

#### Step 4: NAT Configuration
```cisco
! Configure NAT for internal network to access internet
PERIMETER(config)# object network IN-NETWORK
PERIMETER(config-network-object)# subnet 192.168.100.0 255.255.255.128
PERIMETER(config-network-object)# nat (IN,OUT) dynamic interface
PERIMETER(config-network-object)# exit

! Configure NAT for DMZ servers (if needed for outbound)
PERIMETER(config)# object network DMZ-NETWORK
PERIMETER(config-network-object)# subnet 172.16.10.0 255.255.255.0
PERIMETER(config-network-object)# nat (DMZ,OUT) dynamic interface
PERIMETER(config-network-object)# exit

! Verify NAT configuration
PERIMETER# show nat
```

#### Step 5: Access Control Configuration
```cisco
! Allow ICMP (ping) from IN to any
PERIMETER(config)# access-list IN-TO-ANY extended permit icmp any any

! Apply ACL to IN interface
PERIMETER(config)# access-group IN-TO-ANY in interface IN

! Allow DMZ servers to be accessed from outside (example: web server)
PERIMETER(config)# access-list OUT-TO-DMZ extended permit tcp any host 172.16.10.2 eq 80
PERIMETER(config)# access-list OUT-TO-DMZ extended permit tcp any host 172.16.10.2 eq 443
PERIMETER(config)# access-group OUT-TO-DMZ in interface OUT
```

#### Verification Commands
```cisco
! Show all interfaces
PERIMETER# show interface ip brief

Interface                  IP-Address      OK? Method Status                Protocol
GigabitEthernet1/1         192.168.100.1   YES manual up                    up
GigabitEthernet1/2         172.16.10.1     YES manual up                    up
GigabitEthernet1/3         50.50.50.2      YES manual up                    up

! Show nameif and security levels
PERIMETER# show nameif

Interface                Name                     Security
GigabitEthernet1/1       IN                       10
GigabitEthernet1/2       DMZ                      50
GigabitEthernet1/3       OUT                      0

! Show running configuration
PERIMETER# show running-config

! Show version
PERIMETER# show version

! Show connections
PERIMETER# show conn

! Show NAT translations
PERIMETER# show xlate
```

---

### 🔄 OSPF Router Configuration

#### Primary OSPF Router Setup
```cisco
Router> enable
Router# configure terminal
Router(config)# hostname OSPF-ROUTER
OSPF-ROUTER(config)#

! Configure Fa0/0 (User Network)
OSPF-ROUTER(config)# interface FastEthernet0/0
OSPF-ROUTER(config-if)# ip address 10.10.10.1 255.255.255.0
OSPF-ROUTER(config-if)# description User Network Segment
OSPF-ROUTER(config-if)# no shutdown
OSPF-ROUTER(config-if)# exit

! Configure Fa0/1 (OSPF Backbone)
OSPF-ROUTER(config)# interface FastEthernet0/1
OSPF-ROUTER(config-if)# ip address 20.20.20.2 255.255.255.0
OSPF-ROUTER(config-if)# description OSPF Backbone Area 0
OSPF-ROUTER(config-if)# no shutdown
OSPF-ROUTER(config-if)# exit

! Enable OSPF routing
OSPF-ROUTER(config)# router ospf 10
OSPF-ROUTER(config-router)# router-id 1.1.1.2
OSPF-ROUTER(config-router)# network 10.10.10.0 0.0.0.255 area 0
OSPF-ROUTER(config-router)# network 20.20.20.0 0.0.0.255 area 0
OSPF-ROUTER(config-router)# passive-interface FastEthernet0/0
OSPF-ROUTER(config-router)# exit

! Configure default route pointing to ASA
OSPF-ROUTER(config)# ip route 0.0.0.0 0.0.0.0 20.20.20.1

! Redistribute static routes into OSPF (optional)
OSPF-ROUTER(config)# router ospf 10
OSPF-ROUTER(config-router)# default-information originate
OSPF-ROUTER(config-router)# exit
```

#### Gateway Router Configuration (Router4)
```cisco
Router> enable
Router# configure terminal
Router(config)# hostname GATEWAY-ROUTER
GATEWAY-ROUTER(config)#

! Configure Fa0/0 (OSPF Backbone)
GATEWAY-ROUTER(config)# interface FastEthernet0/0
GATEWAY-ROUTER(config-if)# ip address 20.20.20.1 255.255.255.0
GATEWAY-ROUTER(config-if)# description OSPF Backbone Connection
GATEWAY-ROUTER(config-if)# no shutdown
GATEWAY-ROUTER(config-if)# exit

! Configure Fa0/1 (External/Internet)
GATEWAY-ROUTER(config)# interface FastEthernet0/1
GATEWAY-ROUTER(config-if)# ip address 50.50.50.1 255.255.255.0
GATEWAY-ROUTER(config-if)# description Connection to ASA OUT Interface
GATEWAY-ROUTER(config-if)# no shutdown
GATEWAY-ROUTER(config-if)# exit

! Enable OSPF
GATEWAY-ROUTER(config)# router ospf 10
GATEWAY-ROUTER(config-router)# router-id 1.1.1.1
GATEWAY-ROUTER(config-router)# network 20.20.20.0 0.0.0.255 area 0
GATEWAY-ROUTER(config-router)# exit

! Static route to ASA networks
GATEWAY-ROUTER(config)# ip route 192.168.100.0 255.255.255.128 50.50.50.2
GATEWAY-ROUTER(config)# ip route 172.16.10.0 255.255.255.0 50.50.50.2
```

#### OSPF Verification
```cisco
! Show OSPF neighbors
OSPF-ROUTER# show ip ospf neighbor

Neighbor ID     Pri   State           Dead Time   Address         Interface
1.1.1.1           1   FULL/DR         00:00:35    20.20.20.1      FastEthernet0/1

! Show OSPF database
OSPF-ROUTER# show ip ospf database

! Show OSPF interfaces
OSPF-ROUTER# show ip ospf interface

! Show OSPF routing table
OSPF-ROUTER# show ip route ospf

O    192.168.100.0/25 [110/2] via 20.20.20.1, 00:10:25, FastEthernet0/1

! Show IP protocols
OSPF-ROUTER# show ip protocols

Routing Protocol is "ospf 10"
  Outgoing update filter list for all interfaces is not set
  Incoming update filter list for all interfaces is not set
  Router ID 1.1.1.2
  Number of areas in this router is 1. 1 normal 0 stub 0 nssa
  Maximum path: 4
  Routing for Networks:
    10.10.10.0 0.0.0.255 area 0
    20.20.20.0 0.0.0.255 area 0

! Show OSPF process details
OSPF-ROUTER# show ip ospf

 Routing Process "ospf 10" with ID 1.1.1.2
 Start time: 00:00:05.123, Time elapsed: 00:15:32.456
 Supports only single TOS(TOS0) routes
 Supports opaque LSA
 Supports Link-local Signaling (LLS)
 Supports area transit capability
 Router is not originating router-LSAs with maximum metric
 Initial SPF schedule delay 5000 msecs
 Minimum hold time between two consecutive SPFs 10000 msecs
 Maximum wait time between two consecutive SPFs 10000 msecs
```

---

### 🔀 Static Routing Configuration

#### ASA Static Routes (Already Configured Above)
```cisco
! Summary of ASA static routes
PERIMETER# show route

S*   0.0.0.0 0.0.0.0 [1/0] via 50.50.50.1, OUT          # Default route
S    10.10.10.0 255.255.255.0 [1/0] via 20.20.20.1, OUT # User network
S    20.20.20.0 255.255.255.0 [1/0] via 50.50.50.1, OUT # OSPF backbone
C    50.50.50.0 255.255.255.0 is directly connected, OUT
C    172.16.10.0 255.255.255.0 is directly connected, DMZ
C    192.168.100.0 255.255.255.128 is directly connected, IN
```

#### Complete Routing Table Analysis
