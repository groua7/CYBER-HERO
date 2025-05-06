

# 🔓 Password Cracking with John the Ripper (Kali Linux)

> **⚠️ WARNING!!!**
> This guide is for **educational and ethical hacking purposes ONLY**. Never attempt to crack passwords or hashes without **explicit written permission**. Unauthorized use is **illegal and unethical**. Use a safe lab environment with test data or legally allowed challenges.

---

## 🛠️ Prerequisites

- ✅ Kali Linux (VM or installed)
- ✅ John the Ripper (pre-installed in Kali)
- ✅ Basic Linux CLI knowledge
- ✅ Test password files or hash samples (e.g., from CTFs or training labs)

---

## 🧪 Step-by-Step Guide to Using John the Ripper

---

### 🔹 Step 1: Update Kali Linux
```bash
sudo apt update && sudo apt upgrade -y
````

---

### 🔹 Step 2: Verify John the Ripper Installation

```bash
john --version
```

If not installed:

```bash
sudo apt install john -y
```

---

### 🔹 Step 3: Create a Test Password File

```bash
sudo useradd testuser
echo 'testpassword' | sudo passwd testuser --stdin  # For older distros
```

Export the hash from `/etc/shadow` (needs root access):

```bash
sudo unshadow /etc/passwd /etc/shadow > myhashes.txt
```

OR use a simple sample hash file like:

```bash
echo '$6$randomsalt$Zzq0EMbFn0GL9OwAhdKyF9bzAa5ko...' > testhash.txt
```

---

### 🔹 Step 4: Run a Basic Crack with Default Wordlist

```bash
john testhash.txt
```

John will use the default wordlist (`/usr/share/wordlists/rockyou.txt`) if available.

---

### 🔹 Step 5: Use a Specific Wordlist

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt testhash.txt
```

Unzip rockyou if needed:

```bash
gunzip /usr/share/wordlists/rockyou.txt.gz
```

---

### 🔹 Step 6: Show Cracked Passwords

```bash
john --show testhash.txt
```

---

### 🔹 Step 7: Perform Incremental (Brute Force) Attack

```bash
john --incremental testhash.txt
```

Note: Brute-force can take **a long time**. Use only for **short or weak hashes** in test labs.

---

### 🔹 Step 8: Cracking ZIP Files

Create a test zip:

```bash
zip --password secret123 test.zip myfile.txt
```

Convert to John format:

```bash
zip2john test.zip > ziphash.txt
john ziphash.txt --wordlist=/usr/share/wordlists/rockyou.txt
```

---

### 🔹 Step 9: Cracking /etc/shadow Format (Again)

```bash
sudo unshadow /etc/passwd /etc/shadow > shadowhash.txt
john shadowhash.txt
```

---

### 🔹 Step 10: Restore a Cracking Session

Start with:

```bash
john --session=mySession testhash.txt
```

Restore if interrupted:

```bash
john --restore=mySession
```

---

### 🔹 Step 11: Analyze and Document Results

```bash
john --show testhash.txt > results.txt
```

---

## 📚 Bonus: Hash Format References

Use `--format` for specific hash types:

| Format        | Description       |
| ------------- | ----------------- |
| `raw-md5`     | Raw MD5 hashes    |
| `sha512crypt` | Linux /etc/shadow |
| `zip`         | ZIP archive       |
| `bcrypt`      | bcrypt hashes     |

List all supported formats:

```bash
john --list=formats
```

---

## 📁 Resources

* [Official John Wiki](https://openwall.info/wiki/john)
* [CrackStation Wordlist](https://crackstation.net/)
* [TryHackMe John The Ripper Room](https://tryhackme.com/room/johntheripper)

---

## ✅ Final Tips

* Always test in **legal and controlled** environments.
* Combine John with tools like `hashcat` and `Hydra` for full password auditing practice.
* Create writeups to document cracked passwords, wordlists used, and lessons learned.

---

> ✍️ Maintained by: \groua7
> 💼 Role: Cybersecurity Analyst | Ethical Hacker in Training

