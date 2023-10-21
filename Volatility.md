# Volatility

## Obtaining OS & kernel details
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.info
```
## Identifying Injected Code
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.malfind
```
## Identifying Running Processes
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.pslist
# Or with the argument 'windows.pstree'
```
## Identifying Process Command Lines
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.cmdline
```
## Dumping Process Memory & Leveraging YARA
To extract all memory resident pages in a process into an individual file
Yara rules : https://github.com/Neo23x0/signature-base/tree/master
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.memmap --pid 4025 --dump
```
```powershell
$rules = Get-ChildItem C:\Users\UserName\Desktop\yara-4.3.2-2150-win64\rules | Select-Object -Property Name
foreach ($rule in $rules) {C:\Users\UserName\Desktop\yara-4.3.2-2150-win64\yara64.exe C:\Users\UserName\Desktop\yara-4.3.2-2150-win64\rules\$($rule.Name) C:\Users\UserName\Desktop\pid.4025.dmp}
```
## Identifying the DLL (exemple payload.DLL
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.dlllist --pid 4025
```
## Identifying Handles
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.handles --pid 4025
```
## Identifying Network Artifacts
Analyze connection details 
```bash
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.netstat
# OR
python vol.py -q -f ..\memdump\PhysicalMemory.raw windows.netscan
```



