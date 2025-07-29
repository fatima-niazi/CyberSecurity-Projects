#  Day 2: Network Packet Analysis using Wireshark

This folder contains the Day 2 cybersecurity project focused on capturing and analyzing live network traffic using **Wireshark**.

---

##  Tools Used
- Wireshark
- Kali Linux / Parrot OS
- Terminal: `ping`, `nslookup`
- Browser (to simulate HTTP & DNS traffic)

---

##  Objective
Understand how data flows through a network by:
- Capturing live traffic
- Applying protocol-based filters
- Inspecting packet layers (Ethernet, IP, TCP, DNS, HTTP)
- Following TCP streams to reconstruct web conversations

---

##  Steps Performed

###  1. Packet Capture
- Started Wireshark
- Selected interface (`wlan0` or `eth0`)
- Captured traffic while:
  - Visiting websites
  - Running `ping google.com`
  - Using `nslookup github.com`

###  2. Filters Applied
| Filter | Purpose |
|--------|---------|
| `http` | Showed HTTP requests and headers |
| `dns` | Showed domain lookups and IP responses |
| `icmp` | Captured ping traffic |
| `ip.addr == YOUR_IP` | Isolated host-specific traffic |
| `tcp.flags.syn == 1 && tcp.flags.ack == 0` | Detected TCP handshake SYN packets |

###  3. Followed TCP Stream
- Followed an HTTP connection using **“Follow TCP Stream”**
- Captured full conversation between client and server (GET request + response)
- Screenshots included

---

##  Files Included

| File | Description |
|------|-------------|
| `Day2_Network_Packet_Analysis_Report_UPDATED.docx` | Full documentation with screenshots and analysis |
| `capture.pcapng` | Saved packet capture file 

---

>  All activity was conducted in a safe, ethical environment for learning purposes only.
