# Triage Examination & Analysis Tools

indispensable tools
[Eric Zimmerman](https://ericzimmerman.github.io/#!index.md)

## Timestamps in the Windows NTFS File System
  File Create: \
        Modified Timestamp (M): The Modified timestamp is updated to reflect the time of file creation. \
        Accessed Timestamp (A): The Accessed timestamp is updated to reflect that the file was accessed at the time of creation. \
        Birth (Created) Timestamp (b): The Birth timestamp is set to the time of file creation. 

  File Modify: \
        Modified Timestamp (M): The Modified timestamp is updated to reflect the time when the file's content or attributes were last modified. \
        Accessed Timestamp (A): The Accessed timestamp is not updated when the file is modified. \
        Birth (Created) Timestamp (b): The Birth timestamp is not updated when the file is modified. 

  File Copy: \
        Modified Timestamp (M): The Modified timestamp is typically not updated when a file is copied. It usually inherits the timestamp from the source file. \
        Accessed Timestamp (A): The Accessed timestamp is updated to reflect that the file was accessed at the time of copying. \
        Birth (Created) Timestamp (b): The Birth timestamp is updated to the time of copying, indicating when the copy was created. 

  File Access: \
        Modified Timestamp (M): The Modified timestamp is not updated when the file is accessed. \
        Accessed Timestamp (A): The Accessed timestamp is updated to reflect the time of access. \
        Birth (Created) Timestamp (b): The Birth timestamp is not updated when the file is accessed. 

____________________________________________________________________________________________________________      
        
## $MFT
```
The term MAC(b) times denotes a series of timestamps linked to files or objects. 
These timestamps are pivotal as they shed light on the chronology of events or actions on a file system. 
The acronym MAC(b) is an abbreviation for Modified, Accessed, Changed, and (b) Birth times. 
The inclusion of b signifies the Birth timestamp, which isn't universally present across all file systems 
or easily accessible via standard Windows API functions.```
```

### MFT Explorer tool
GUI , you just have to select the file
use 'inspect file record' to see MFT details

### MFTECmd
```bash
.\MFTECmd.exe -f 'C:\Users\johndoe\Desktop\FileName.txt
  Use the entry sequence found with MFT Explorer ex : 0x17170
```
## Zone.Identifier
When a file is fetched from the internet, Windows assigns it a Zone Identifier (ZoneId). This ZoneId, embedded in the file's metadata, signifies the source or security zone of the file's origin. 
```
dans /Downloads
Get-Item * -Stream Zone.Identifier -ErrorAction SilentlyContinue
Get-Content * -Stream Zone.Identifier -ErrorAction SilentlyContinue
```

## Analyzing Timeline with Timeline Explorer
```
Timeline Explorer (by Eric Zimmerman) used to create and analyse timeline artifacts from differents sources. 
```

## MFT File Record
### MFTECmd
```
.\MFTECmd.exe -f 'C:\Users\grsu\Desktop\forensic_data\kape_output\D\$MFT' --de 27142
```
____________________________________________________________________________________________________________  
## USN Journal
### KAPE
used to collect USN Journal in the following directory: <KAPE_output_folder>\<Drive>\$Extend
### MFTECmd
```
.\MFTECmd.exe -f 'C:\Users\grsu\Desktop\forensic_data\kape_output\D\$Extend\$J' --csv C:\Users\grsu\Desktop\forensic_data\mft_analysis\ --csvf MFT_J.csv
```
send the extract to Timeline Explorer 
____________________________________________________________________________________________________________  
## Windows Event Logs
### KAPE
```
inside : <KAPE_output_folder>\Windows\System32\winevt\logs
```

### EvtxECmd
```
find :
```
C:\Users\johndoe\Desktop\Get-ZimmermanTools\net6\EvtxeCmd

Use :
```
EvtxeCmd.exe -f "C:\Temp\Application.evtx" --csv "c:\temp\out" --csvf MyOutputFile.csv 
```

sync the map :
```
.\EvtxECmd.exe --sync 
```

convert file to a CSV file :
```
.\EvtxECmd.exe -f "C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\System32\winevt\logs\Microsoft-Windows-Sysmon%4Operational.evtx" --csv "C:\Users\grsu\Desktop\forensic_data\event_logs\csv_timeline" --csvf kape_log.csv
after that upload it in Timeline Explorer
```

### EQL
```
pip install eql
```

locate :
```
C:\Users\grsu\Desktop\eqllib-master
```

parsing Sysmon events from Windows Event Logs :
```
import-module .\scrape-events.ps1
```

activate the Get-EventProps function :
```
Get-WinEvent -Path C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\System32\winevt\logs\Microsoft-Windows-Sysmon%4Operational.evtx -Oldest | Get-EventProps | ConvertTo-Json | Out-File -Encoding ASCII -FilePath C:\Users\grsu\Desktop\forensic_data\event_logs\eql_format_json\eql-sysmon-data-kape.json
```

display user/group :
``` 
eql query -f C:\Users\grsu\Desktop\forensic_data\event_logs\eql_format_json\eql-sysmon-data-kape.json "EventId=1 and (Image='*net.exe' and (wildcard(CommandLine, '* user*', '*localgroup *', '*group *')))"
```

____________________________________________________________________________________________________________  
## Windows Registry
### KAPE store :
```
<KAPE_output_folder>\Windows\System32\config
```
### Registry Explorer
```
GUI interface used to navigate and dissect the contents of Windows Registry
C:\Users\johndoe\Desktop\Get-ZimmermanTools\net6\RegistryExplorer
```
### RegRipper
```
.\rip.exe -h
.\rip.exe -l -c > plugins.csv
choose a plugin with -p
.\rip.exe -r "C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\System32\config\SYSTEM" -p compname
```
____________________________________________________________________________________________________________  
## Investigation of Prefetch
Prefetch files are created for every program that is executed on a Windows system, prefetch files are stored in the C:\Windows\Prefetch\ directory.
### KAPE
```
<KAPE_output_folder>\Windows\prefetch
```
### PECmd
```
located : C:\Users\johndoe\Desktop\Get-ZimmermanTools\net6
.\PECmd.exe -h
.\PECmd.exe -f C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\prefetch\DISCORD.EXE-7191FAD6.pf
```
#### Convert Prefetch Files to CSV to load it in Timeline Explorer
```
.\PECmd.exe -d C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\prefetch --csv C:\Users\grsu\Desktop\forensic_data\prefetch_analysis
```
____________________________________________________________________________________________________________  
## ShimCache 
use to detect the execution of potentially malicious files.
located : HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\ControlSet001\Control\Session Manager\AppCompatCache
```
Go to C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\System32\config in the registry explorer and select AppCompatCache
```
## Amcache
used to store evidence related to program execution.
located at C:\Windows\AppCompat\Programs\AmCache.hve
parse it with [AmcacheParser](https://github.com/EricZimmerman/AmcacheParser)
```
parse and convert this file into a CSV :
.\AmcacheParser.exe -f "C:\Users\johndoe\Desktop\forensic_data\kape_output\D\Windows\AppCompat\Programs\AmCache.hve" --csv C:\Users\johndoe\Desktop\forensic_data\amcache-analysis
```
## BAM (Background Activity Moderator)
tracks and logs the execution of certain types of background or scheduled tasks.
```
On the registry explorer :
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\bam\State\UserSettings\{USER-SID}
```
____________________________________________________________________________________________________________  
## API Call Data

### API Monitor
[API Monitor](http://www.rohitab.com/apimonitor)
```
File menu, choose Open find the location of the .apmx64 file and select it.
```
### Registry Persistence via Run Keys
```
look for RegOpenKeyExA function search for RegOpenKey on the Find console
```
### Process Injection
```
search for the CreateProcess
```


## KAPE
Rapid artifact parsing and extraction solutions.
[KAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape)



















