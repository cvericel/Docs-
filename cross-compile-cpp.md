---
title: Cross-Compile the C++ Code to 64-Bit DLL
tags:
  - C++
  - Development
  - Exploitation
---

### Cross-Compile C++ Code to 64-Bit DLL

```bash cross-c
x86_64-w64-mingw32-gcc myDLL.cpp --shared -o myDLL.dll
```