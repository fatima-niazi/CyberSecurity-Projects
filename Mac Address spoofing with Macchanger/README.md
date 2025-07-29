
#  MAC Address Spoofing using macchanger

This folder contains my cybersecurity project focused on MAC address spoofing using the `macchanger` utility in Linux. 
The objective was to understand how MAC addresses function in local networking and how changing them can impact device identity and access.

---

##  Tools Used

- Kali Linux 
- Terminal
- macchanger
- ip / ifconfig

---

##  Objective

- Understand the purpose and structure of MAC addresses
- Perform MAC spoofing (both random and manual)
- Analyze the spoofed MAC address in system and optional traffic captures
- Revert safely to the original MAC address

---

##  Steps Performed

###  1. Identified Available Network Interfaces

```bash
ip link show
```

The active interface was identified as `eth0`.

---

###  2. Brought Interface Down

```bash
sudo ip link set eth0 down
```

*Reason:* MAC addresses can only be changed when the interface is disabled.

---

###  3. Spoofed the MAC Address

**Random MAC:**
```bash
sudo macchanger -r eth0
```

**Manual MAC:**
```bash
sudo macchanger --mac=00:11:22:33:44:55 eth0
```

macchanger showed:
- Permanent MAC
- Current MAC
- New (spoofed) MAC

---

###  4. Brought Interface Back Up

```bash
sudo ip link set eth0 up
```

---

###  5. Verified the Change

```bash
macchanger -s eth0
```
or
```bash
ifconfig eth0
```

---

##  Restore to Original MAC Address

```bash
sudo ip link set eth0 down
sudo macchanger -p eth0
sudo ip link set eth0 up
```

 Rebooting also resets the MAC to its permanent hardware value.

---

##  Files Included

| File                                    | Description                                  |
|-----------------------------------------|----------------------------------------------|
| `MAC_Address_Spoofing_Report.docx` | Full documentation of the spoofing process   |


---

> ⚠This project was conducted in a safe, isolated lab environment and is for **educational purposes only**.
