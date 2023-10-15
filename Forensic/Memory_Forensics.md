# Memory Forensics

types of data found in RAM that are valuable for incident investigation:

- Network connections
- File handles and open Files
- Open registry keys
- Running processes on the system
- Loaded modules
- Loaded device drivers
- Command history and console sessions
- Kernel data structures
- User and credential information
- Malware artifacts
- System configuration
- Process memory regions


________________________________________________________________________________________

## Forensics memory approach
   1/ Process Identification and Verification: Malicious software often masquerades as legitimate processes, sometimes with subtle name variations to avoid detection. We need to:
   
- Enumerate all running processes.
- Determine their origin within the operating system.
- Cross-reference with known legitimate processes.
- Highlight any discrepancies or suspicious naming conventions.

   2/ Deep Dive into Process Components: Once we've flagged potentially rogue processes, our next step is to scrutinize the associated Dynamic Link Libraries (DLLs) and handles. Malware often exploits DLLs to conceal its activities. We should:
   
- Examine DLLs linked to the suspicious process.
- Check for unauthorized or malicious DLLs.
- Investigate any signs of DLL injection or hijacking.

  3/  Network Activity Analysis: Many malware strains, especially those that operate in stages, necessitate internet connectivity. They might beacon to Command and Control (C2) servers or exfiltrate data. To uncover these:
  
- Review active and passive network connections in the system's memory.
- Identify and document external IP addresses and associated domains.
- Determine the nature and purpose of the communication.
  - Validate the process' legitimacy.
  - Assess if the process typically requires network communication.
  - Trace back to the parent process.
  - Evaluate its behavior and necessity.

   4/ Code Injection Detection: Advanced adversaries often employ techniques like process hollowing or utilize unmapped memory sections. To counter this, we should:
   
- Use memory analysis tools to detect anomalies or signs of these techniques.
- Identify any processes that seem to occupy unusual memory spaces or exhibit unexpected behaviors.

   5/ Rootkit Discovery: Achieving stealth and persistence is a common goal for adversaries. Rootkits, which embed deep within the OS, grant threat actors continuous, often elevated, system access while evading detection. To tackle this:
   
- Scan for signs of rootkit activity or deep OS alterations.
- Identify any processes or drivers operating at unusually high privileges or exhibiting stealth behaviors.

  6/  Extraction of Suspicious Elements: After pinpointing suspicious processes, drivers, or executables, we need to isolate them for in-depth analysis. This involves:
  
- Dumping the suspicious components from memory.
- Storing them securely for subsequent examination using specialized forensic tools.


________________________________________________________________________________________

# Volatility Framework

- Volatility v2: https://github.com/volatilityfoundation/volatility/wiki/Command-Reference
-Volatility v3: https://volatility3.readthedocs.io/en/latest/index.html
[CheatSheet](https://blog.onfvp.com/post/volatility-cheatsheet/)

## Identifying Profile
```
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem imageinfo 
```
### Identifying Running Processes
```
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem --profile=Win7SP1x64 pslist
```
### Identifying Network Artifcats
```
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem --profile=Win7SP1x64 netscan
```
#### Identifying Injected Code
```
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem --profile=Win7SP1x64 malfind --pid=608
```
#### Identifying Handles
```
# Handles are files and object references held by a specific process within a memory dump.
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem --profile=Win7SP1x64 handles -p 1512 --object-type=Key
vol.py -f /home/UserName/Dumps/MemoryDumps/Win7-2515534d.vmem --profile=Win7SP1x64 handles -p 1512 --object-type=File
vol.py -f /home/UserName/Dumps/MemoryDumps/Win7-2515534d.vmem --profile=Win7SP1x64 handles -p 1512 --object-type=Process
```

### Identifying Windows Services
```
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem --profile=Win7SP1x64 svcscan | more
```

### Identifying Loaded DLLs
```
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem --profile=Win7SP1x64 dlllist -p 1512
```

### Identifying Hives (registry files)
```
vol.py -f /home/UserName/Dumps/Win7-2515534d.vmem --profile=Win7SP1x64 hivelist
```

## Rootkit Analysis
[EPROCESS](https://www.nirsoft.net/kernel_struct/vista/EPROCESS.html) is a data structure in the Windows kernel that represents a process

















