

# 🔍 Nmap Practice Guide for Cybersecurity Analysts (Kali Linux)

> **⚠️ WARNING!!!**
> This guide is intended **ONLY for educational and ethical testing purposes**. Never scan networks or devices without **explicit permission**. Unauthorized scanning is illegal and unethical. Always use a controlled lab or your own test environment.

---

## 🛠️ Prerequisites

- ✅ Kali Linux (installed or in a VM)
- ✅ Basic Linux CLI knowledge
- ✅ Internet connection (for package updates)
- ✅ A test lab or scan-safe targets (e.g., your own local network or `scanme.nmap.org`)

---

## 🧪 Step-by-Step Nmap Practice Guide

### 🔹 Step 1: Update Kali Linux
```bash
sudo apt update && sudo apt upgrade -y
````

---

### 🔹 Step 2: Verify Nmap Installation

```bash
nmap --version
```

If not installed:

```bash
sudo apt install nmap -y
```

---

### 🔹 Step 3: Understand the Basics

Try scanning a public target (allowed by the owner):

```bash
nmap scanme.nmap.org
```

> `scanme.nmap.org` is a test site by the Nmap team. Use responsibly.

---

### 🔹 Step 4: Ping Scan (Discover Live Hosts)

```bash
nmap -sn 192.168.1.0/24
```

* Detects which hosts are **up** without port scanning.

---

### 🔹 Step 5: TCP Connect Scan (Full Scan)

```bash
nmap -sT 192.168.1.10
```

* Performs a full **TCP connection scan**.

---

### 🔹 Step 6: SYN Scan (Stealth Scan)

```bash
sudo nmap -sS 192.168.1.10
```

* Faster and stealthier than `-sT`.

---

### 🔹 Step 7: Service Version Detection

```bash
nmap -sV 192.168.1.10
```

* Identifies running **services and versions**.

---

### 🔹 Step 8: OS Detection

```bash
sudo nmap -O 192.168.1.10
```

* Attempts to detect the **Operating System**.

---

### 🔹 Step 9: Aggressive Scan (All-in-One)

```bash
sudo nmap -A 192.168.1.10
```

* Combines OS detection, version detection, script scanning, and traceroute.

---

### 🔹 Step 10: Scan Multiple IPs or Ranges

```bash
nmap 192.168.1.10 192.168.1.20 192.168.1.30
nmap 192.168.1.0/24
```

---

### 🔹 Step 11: Scan Specific Ports

```bash
nmap -p 21,22,80,443 192.168.1.10
```

---

### 🔹 Step 12: Use Nmap Scripts (NSE)

```bash
nmap --script vuln 192.168.1.10
```

* Run built-in **vulnerability scripts**.

List all available scripts:

```bash
ls /usr/share/nmap/scripts/
```

---

### 🔹 Step 13: Save Scan Results

```bash
nmap -oN scan.txt 192.168.1.10         # Normal format
nmap -oX scan.xml 192.168.1.10         # XML
nmap -oG scan.gnmap 192.168.1.10       # Grepable
```

---

### 🔹 Step 14: Practice in a Safe Lab Environment

✅ Options:

* **Metasploitable2 VM**
* **TryHackMe**
* **Hack The Box**
* **VulnHub**

---

## 📁 Resources

* [Nmap Book (official)](https://nmap.org/book/)
* [Nmap Cheat Sheet (SANS)](https://www.sans.org/media/score/checklists/NmapCheatSheet.pdf)
* [TryHackMe Nmap Room](https://tryhackme.com/room/introtonmap)

---

## ✅ Final Tips

* Document your scans and findings in a **practice report**.
* Practice regularly using lab environments.
* Always stay ethical and legal.

---

> ✍️ Maintained by: \groua7
> 💼 Role: Cybersecurity Analyst | Ethical Hacker in Training


