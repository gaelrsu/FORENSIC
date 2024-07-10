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

## Analyzing Timeline with Timeline Explorer
```
Timeline Explorer (by Eric Zimmerman) used to create and analyse timeline artifacts from differents sources. 
```

## MFT File Record
### MFTECmd
```
.\MFTECmd.exe -f 'C:\Users\grsu\Desktop\forensic_data\kape_output\D\$MFT' --de 27142 MFTECmd version 1.2.3
```

## USN Journal
### KAPE
used to collect USN Journal in the following directory: <KAPE_output_folder>\<Drive>\$Extend
### MFTECmd
```
.\MFTECmd.exe -f 'C:\Users\grsu\Desktop\forensic_data\kape_output\D\$Extend\$J' --csv C:\Users\grsu\Desktop\forensic_data\mft_analysis\ --csvf MFT_J.csv MFTECmd version 1.2.3
```
send the extract to Timeline Explorer 

## Windows Event Logs
### KAPE
```
inside : <KAPE_output_folder>\Windows\System32\winevt\logs
```
### EvtxECmd
```
find :
C:\Users\johndoe\Desktop\Get-ZimmermanTools\net6\EvtxeCmd

Use :
EvtxeCmd.exe -f "C:\Temp\Application.evtx" --csv "c:\temp\out" --csvf MyOutputFile.csv
sync the map : 
.\EvtxECmd.exe --sync
convert file to a CSV file :
.\EvtxECmd.exe -f "C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\System32\winevt\logs\Microsoft-Windows-Sysmon%4Operational.evtx" --csv "C:\Users\grsu\Desktop\forensic_data\event_logs\csv_timeline" --csvf kape_log.csv EvtxECmd version 1.5.4.0
after that upload it in Timeline Explorer
```
### EQL
```
pip install eql
locate :
C:\Users\grsu\Desktop\eqllib-master

parsing Sysmon events from Windows Event Logs :
import-module .\scrape-events.ps1

activate the Get-EventProps function :
Get-WinEvent -Path C:\Users\grsu\Desktop\forensic_data\kape_output\D\Windows\System32\winevt\logs\Microsoft-Windows-Sysmon%4Operational.evtx -Oldest | Get-EventProps | ConvertTo-Json | Out-File -Encoding ASCII -FilePath C:\Users\grsu\Desktop\forensic_data\event_logs\eql_format_json\eql-sysmon-data-kape.json
```

## KAPE
Rapid artifact parsing and extraction solutions.
[KAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape)



















