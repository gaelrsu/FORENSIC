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




## Forensics memory approach
   1/ Process Identification and Verification: Let's begin by identifying all active processes. Malicious software often masquerades as legitimate processes, sometimes with subtle name variations to avoid detection. We need to:
   
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
















