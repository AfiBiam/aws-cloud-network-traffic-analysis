# aws-cloud-network-traffic-analysis
AWS EC2–based network simulation and traffic analysis using Mininet and Wireshark, demonstrating IPv4/IPv6 communication and protocol inspection.

**Wireshark • Mininet • DNS • HTTP • TCP/IP • ICMPv6 • TLS**

This repository showcases a **cloud computing and network analysis project executed entirely on AWS**.  
The project combines **packet-level traffic analysis** and **network simulation** to demonstrate hands-on experience with real-world networking and security concepts.

All work was performed inside an **AWS EC2 instance**, using **Wireshark** for packet inspection and **Mininet** for network simulation.

This project is relevant to **Cloud Engineer, Cybersecurity Analyst, SOC Analyst, Network Analyst, and IT Infrastructure roles**.

---

## ☁️ Cloud Environment

- **Cloud Provider:** Amazon Web Services (AWS)
- **Compute:** AWS EC2 instance using a preconfigured Ubuntu AMI
- **Access Method:** Remote Desktop / Windows App (RDP)
- **Network Simulation:** Mininet
- **Packet Analysis:** Wireshark

All packet captures and analysis were performed **within the AWS cloud environment**, not on a local machine.

---

## 🧠 Skills Demonstrated

- Cloud-based networking (AWS EC2)
- Secure remote access configuration (RDP)
- Packet capture and analysis using Wireshark
- Network simulation using Mininet
- DNS request and response analysis
- HTTP request/response inspection
- TCP and IP header analysis
- IPv6 and ICMPv6 traffic analysis
- TLS and certificate validation traffic (OCSP)
- Traffic flow visualization and statistics interpretation

---

## 🧪 Part 1: Network Traffic Analysis Using Wireshark

### Wireshark Interface & Capture Review
- Explored Wireshark menus, capture options, and statistics
- Analyzed an **offline packet capture**
- Verified no capture filters were applied (full traffic visibility)
- ![Wirsharkinterface1](https://github.com/user-attachments/assets/e57366e6-fc95-4b0a-84dd-5a2b27e864b0)


---

### DNS Analysis
- Applied DNS display filter (`dns`)
- Identified:
  - Client IP: `10.0.2.15`
  - DNS Server: `209.18.47.62`
  - Queried domain: `www.umuc.edu`
- DNS responses returned **four IP addresses**, demonstrating load distribution
- <img width="625" height="471" alt="DNS responses" src="https://github.com/user-attachments/assets/f74e9b45-ff98-4fcd-9bb2-1059e1ad78b7" />


**DNS Protocol Details**
- Protocol: UDP
- Destination Port: 53
- Display filter used: `udp.port == 53`
- <img width="586" height="360" alt="UDP port 53" src="https://github.com/user-attachments/assets/37588b1e-8b2f-4f57-8c42-c04701e155b7" />


---

### HTTP & Certificate Validation Traffic
- Identified **OCSP (Online Certificate Status Protocol)** traffic operating over HTTP
- OCSP used for real-time SSL/TLS certificate validation
- <img width="635" height="458" alt="OCSP" src="https://github.com/user-attachments/assets/f0a1c7ae-d373-48df-9306-73a3da5879bf" />

**Security relevance:** OCSP traffic is commonly observed during secure web sessions and incident investigations.

---

### HTTP Request & Response Analysis
- First HTTP request identified in packet **#3453**
- Method: `GET`
- Destination IP: `23.49.176.128`
- Observed HTTP redirection (`302`) and successful responses (`200 OK`)
- <img width="644" height="294" alt="FIRSTHTTP" src="https://github.com/user-attachments/assets/d4cb3732-fd17-48c5-8cd5-edab36d74bb3" />


---

### File Retrieval & Packet Content Inspection
- HTTP GET request in packet **#3512**
- Response packet **#3535**
  - Status Code: `200 OK`
  - File Size: `1283 bytes`
  - File Type: **PNG (Portable Network Graphics)**
  - Extra Header: `Last-Modified`
  - <img width="667" height="306" alt="Packet #3512 " src="https://github.com/user-attachments/assets/c5656dd2-c604-4347-8f99-e46b2ef2ae11" />


---

### IP & TCP Header Analysis
**IP Header**
- Total Length: `409 bytes`
- Time To Live (TTL): `64`
- <img width="609" height="385" alt="IPHeader" src="https://github.com/user-attachments/assets/5e548962-2d64-45cc-9fa5-a3e61b7ad779" />


**TCP Header**
- Source Port: `35722`
- Destination Port: `80`
- Sequence Number: `1`
- Window Size: `64240`
- <img width="647" height="390" alt="TCPHeader" src="https://github.com/user-attachments/assets/47b16a93-ef7e-45fb-9b1d-70d677492269" />

---

### Traffic Visualization & Statistics
- **I/O Graph:** Displayed packet and byte volume over time
- <img width="643" height="398" alt="IO:Graph" src="https://github.com/user-attachments/assets/1d79116b-2ee0-4d90-a3a5-fd6feb2fee51" />

- **Flow Graph:** Visualized end-to-end communication between hosts
- <img width="633" height="541" alt="FLOWGRAPH" src="https://github.com/user-attachments/assets/d1390b30-af6c-455c-bbed-8ce8b535bc51" />

- No `akamai.net` domains were resolved in this capture
- <img width="566" height="473" alt="Noresolved1" src="https://github.com/user-attachments/assets/123fed4a-a049-48c2-8c72-238d9f0609dd" />

<img width="617" height="388" alt="akamaidomain" src="https://github.com/user-attachments/assets/9cf68f88-e60f-4909-93fa-b94a0cdb3754" />

---

## 🧪 Part 2: Cloud Network Simulation Using Mininet on AWS

### Environment Setup
- Launched an **AWS EC2 instance using a preconfigured Ubuntu AMI**
- <img width="681" height="226" alt="AMI" src="https://github.com/user-attachments/assets/bd4a988d-e489-49f6-92b5-1df5892aef81" />

- Confirmed **Mininet was installed and running**
- <img width="649" height="222" alt="Mininetrunning" src="https://github.com/user-attachments/assets/da032e7e-3a90-4d95-9df9-ad24e9f2d7d5" />

- Configured the instance for **Remote Desktop access**
- <img width="752" height="336" alt="Remoteconnect" src="https://github.com/user-attachments/assets/eb28a4d0-2da8-452a-aaf1-b13dceecb08c" />

- Set a secure password for the **Ubuntu user**
- <img width="671" height="258" alt="userpassword" src="https://github.com/user-attachments/assets/a1116dca-3bcd-454e-b380-d8a1354228d6" />

- Connected to the EC2 instance using the **Windows App (Remote Desktop)**
- <img width="685" height="454" alt="AddPC" src="https://github.com/user-attachments/assets/6f67acb7-9c7e-4201-93c4-9b028138fb0f" />


This configuration enabled full graphical access to run **Mininet and Wireshark directly within the AWS environment**.

---

### Network Simulation with Mininet
- Executed Mininet to simulate a virtual network topology
- Generated live traffic by pinging one simulated host from another
- Verified successful host-to-host connectivity
- <img width="651" height="429" alt="hi h2 stimulation " src="https://github.com/user-attachments/assets/54cb7667-800a-4596-b6cc-a652d863e4e1" />


**Simulated host IPv6 addresses:**
- **Host h1:** `fe80::b409:dfff:fe1c:a42d`
- **Host h2:** `fe80::f03f:82ff:fedb:4004`
  

---

### Packet Capture & ICMPv6 Analysis
- Captured Mininet-generated traffic using **Wireshark**
- Observed **ICMPv6 (Internet Control Message Protocol for IPv6)** packets during host communication

**ICMPv6 findings:**
- ICMPv6 allows devices on the same network to locate each other
- Used by hosts to discover routers and obtain network configuration details
- Captured **Router Solicitation** messages, confirming IPv6 router and neighbor discovery behavior

---

### Why This Matters
This part of the project demonstrates:
- Practical cloud networking skills using AWS EC2
- Ability to simulate and validate network behavior using Mininet
- Hands-on IPv6 traffic analysis
- Packet-level verification of control-plane protocols (ICMPv6)

These skills directly support **Cloud Engineering, Network Engineering, SOC, and Cybersecurity roles**.

---

## 📁 Repository Structure

