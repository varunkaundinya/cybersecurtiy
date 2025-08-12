# 🖧 OSI Model (Open Systems Interconnection)

The **OSI Model** is a conceptual framework that describes how data is transmitted over a network in **seven layers**.  
Each layer serves a specific function and communicates with the layers directly above and below it.

---

## 📚 Layers of the OSI Model

### **1. Physical Layer**
- **Purpose:** Deals with the physical medium for data transmission.
- **Functions:**
  - Transmission and reception of raw binary data.
  - Electrical, mechanical, and procedural interfaces.
- **Examples:** Ethernet cables, fiber optics, hubs, repeaters.
- **Data Unit:** Bits.

---

### **2. Data Link Layer**
- **Purpose:** Responsible for node-to-node data transfer and error detection.
- **Functions:**
  - Framing (grouping bits into frames).
  - Error detection and correction.
  - Flow control.
- **Examples:** Switches, MAC addresses, ARP (Address Resolution Protocol).
- **Data Unit:** Frames.
- **Sublayers:**
  - **LLC (Logical Link Control)**
  - **MAC (Media Access Control)**

---

### **3. Network Layer**
- **Purpose:** Determines how data is sent from one device to another (routing).
- **Functions:**
  - Logical addressing (IP addresses).
  - Routing and path determination.
- **Examples:** Routers, IPv4, IPv6, ICMP.
- **Data Unit:** Packets.

---

### **4. Transport Layer**
- **Purpose:** Ensures complete data transfer between devices.
- **Functions:**
  - Segmentation and reassembly.
  - Error recovery.
  - Flow control.
- **Examples:** TCP (reliable), UDP (fast but unreliable).
- **Data Unit:** Segments (TCP) / Datagrams (UDP).

---

### **5. Session Layer**
- **Purpose:** Manages and controls connections between computers.
- **Functions:**
  - Establishing, maintaining, and ending sessions.
  - Synchronization.
- **Examples:** APIs, NetBIOS, PPTP.

---

### **6. Presentation Layer**
- **Purpose:** Translates data into a format that the application layer can understand.
- **Functions:**
  - Data encryption and decryption.
  - Data compression.
  - Data format translation.
- **Examples:** SSL/TLS, JPEG, GIF, ASCII, EBCDIC.

---

### **7. Application Layer**
- **Purpose:** Closest to the end user; provides network services to applications.
- **Functions:**
  - User interface for network services.
  - Resource sharing, file transfers, email.
- **Examples:** HTTP, FTP, SMTP, DNS.
- **Data Unit:** Data.

---

## 📝 Summary Table

| Layer No. | Layer Name         | Data Unit     | Examples                      | Key Function                       |
|-----------|-------------------|--------------|--------------------------------|-------------------------------------|
| 7         | Application       | Data         | HTTP, FTP, SMTP, DNS           | Network services to applications   |
| 6         | Presentation      | Data         | SSL/TLS, JPEG, ASCII           | Translation, encryption, compression |
| 5         | Session           | Data         | NetBIOS, PPTP                  | Session management                  |
| 4         | Transport         | Segments     | TCP, UDP                       | Reliable/fast delivery, error handling |
| 3         | Network           | Packets      | IP, ICMP, Routers              | Logical addressing, routing         |
| 2         | Data Link         | Frames       | Switches, MAC, ARP             | Error detection, flow control       |
| 1         | Physical          | Bits         | Cables, Hubs, Fiber optics     | Physical transmission               |

---
