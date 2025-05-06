

# 🛡️ Web Server Scanning with Nikto (Kali Linux)

> **⚠️ WARNING!!!**  
> This guide is for **educational and authorized testing purposes only**. Nikto is a **powerful web server scanner** that can trigger alerts or cause disruptions. **Do NOT scan** websites or web apps **you do not own or have explicit permission to test**. Use it only in a **lab** or **legal test environment**.

---

## 🛠️ Prerequisites

- ✅ Kali Linux (VM or native)
- ✅ Nikto (pre-installed on Kali)
- ✅ Basic terminal knowledge
- ✅ A test web server (e.g., DVWA, Metasploitable2, OWASP BWA)

---

## 🧪 Step-by-Step Nikto Practice Guide

---

### 🔹 Step 1: Update Kali Linux

```bash
sudo apt update && sudo apt upgrade -y
````

---

### 🔹 Step 2: Verify Nikto Installation

```bash
nikto -Version
```

If missing:

```bash
sudo apt install nikto -y
```

---

### 🔹 Step 3: Perform a Basic Scan

```bash
nikto -h http://192.168.1.100
```

* `-h` specifies the **host**
* Use **HTTP** or **HTTPS** as appropriate

---

### 🔹 Step 4: Scan with SSL (HTTPS)

```bash
nikto -h https://192.168.1.101
```

---

### 🔹 Step 5: Scan a Specific Port

```bash
nikto -h 192.168.1.100 -p 8080
```

---

### 🔹 Step 6: Use a Specific User-Agent

```bash
nikto -h http://192.168.1.100 -useragent "Mozilla/5.0"
```

---

### 🔹 Step 7: Output Results to a File

```bash
nikto -h http://192.168.1.100 -o scan_report.txt
```

Use other formats:

```bash
nikto -h http://192.168.1.100 -Format html -o report.html
```

Available formats: `txt`, `html`, `csv`, `xml`, `nbe`

---

### 🔹 Step 8: Tuning Scan Options

Exclude specific checks:

```bash
nikto -h http://192.168.1.100 -Tuning 123
```

Tuning options:

* `1`: Interesting files
* `2`: Misconfigurations
* `3`: Default files
* `4`: Information disclosure
* `5`: Injection vulnerabilities

---

### 🔹 Step 9: Scan Multiple Hosts

```bash
nikto -h hosts.txt
```

Where `hosts.txt` contains one target per line.

---

### 🔹 Step 10: Use Proxy (Optional)

```bash
nikto -h http://192.168.1.100 -useproxy http://127.0.0.1:8080
```

> Useful for intercepting with **Burp Suite** or routing traffic through a proxy.

---

### 🔹 Step 11: Scan Web Apps in Practice Labs

✅ Test environments:

* **Metasploitable2 (port 80)**
* **DVWA**
* **bWAPP**
* **OWASP Broken Web Apps**
* **TryHackMe Web Hacking rooms**
* **Hack The Box retired boxes**

---

## 📁 Resources

* [Nikto Official Site](https://cirt.net/Nikto2)
* [Nikto GitHub Repo](https://github.com/sullo/nikto)
* [TryHackMe Web Fundamentals](https://tryhackme.com/room/owasptop10)
* [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)

---

## ✅ Final Tips

* Nikto is **noisy** and will trigger IDS/IPS alerts.
* Pair it with **Burp Suite**, **Nmap**, or **Metasploit** for deeper testing.
* Always document findings and output for reporting practice.

---

> ✍️ Maintained by: \groua7
> 💼 Role: Cybersecurity Analyst | Web App Tester in Training


