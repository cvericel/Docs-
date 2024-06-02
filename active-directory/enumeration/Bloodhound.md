---
title: Bloodhound
description: Tips & tricks for bloodhound
tags:
  - Active Directory
  - Enumeration
---

[!badge variant="info" text="Active Directory" margin="0 8 0 0"]
[!badge variant="info" text="Enumeration" margin="0 8 0 0"]

## Setup Bloodhound

```bash Start NoSQL Database
# Default creds => neo4j:neo4j
sudo neo4j start
```

```bash Start BloodHound
bloodhound
```

---

## Collecting data with Sharphound

+++ Script

```powershell 
Import-Module .\Sharphound.ps1
Invoke-BloodHound -CollectionMethod All -OutputDirectory C:\Temp\
```

[!file sharphound.ps1](https://raw.githubusercontent.com/BloodHoundAD/BloodHound/master/Collectors/SharpHound.ps1)

+++ Executable

```powershell 
.\SharpHound.exe -c All -OutputDirectory C:\Temp\
```

[!file sharphound.exe](https://github.com/BloodHoundAD/BloodHound/raw/master/Collectors/SharpHound.exe)

+++ Python (User needed)

```bash From Kali Linux
bloodhound-python -d $domain -u $user -p $password -c all -ns $ip
```

+++

---

## BloodHound Tips

Right click on node allow you to get information about the node and also how to compromise the user / machine.
Always tag owned node, this can be useful during an internal pentest to note where you are.
It's then possible to ask the shortest path to a node from the owned ones.

```bash Some useful commands
# Show all computers found.
MATCH (m:Computer) RETURN m

# Display all users found.
MATCH (m:User) RETURN m

# Display all active sessions.
MATCH p = (c:Computer)-[:HasSession]->(m:User) RETURN p 
```
