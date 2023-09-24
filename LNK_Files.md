# LNK Files and Jump Lists
Link File or Jump Lists it's a metadata used by the windows shell.
A link file is automaticly created when you open a document.
You'll found :
```
The original path
TImestamps (modification, last open / creation / access)
Size
Attributes (read-only / hidden / system etc)
System name, volume name, volume serial number (sometimes MAC address)
Information idicate is the resource is local or on remote 
```
This files are stored with the extension : 
```
.automaticdestination-ms 
Object Linking and Embeddeing (OLE) + Compound Files (CF) = OLECF
Multiple data "Streams" within a single file
Also referred to as a "Compound Binary File"
Each stream contains an embedded LNK
"DestList" acts as a Most Recently Used (MRU) list
```
```
.customdestination-ms
Are usually created a user pins an item to the taskbar or Start menu
Are not an OLECF and not contain streams
LNK file data can often be carved from this files
Possible to be parsing via hex editor
```
## Paths
```
C:\Users\UserName\AppData\Roaming\Microsoft\Windows\Recent
C:\Users\UserName\AppData\Roaming\Microsoft\Office\Recent
# With CMD
C:\Users\UserName\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations
C:\Users\UserName\AppData\Roaming\Microsoft\Office\Recent\CustomDestinations
```
## Exiftool
```
exiftool capture.png.lnk
```

## LNK explorer
https://github.com/EricZimmerman/LECmd
```
LECmd.exe

LECmd.exe -d C:\Users\UserName\AppData\Roaming\Microsoft\Windows\Recent -q --csv \PathForTheOutput
```

## Jump List Explorer
https://github.com/EricZimmerman/JLECmd
https://github.com/EricZimmerman/JumpList/blob/master/JumpList/Resources/AppIDs.txt
```
JLECmd.exe
JLECmd.exe -f C:\Users\UserName\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations\<IDsnumber>.AutomaticDestinations-ms -q --csv \Path-to-save
```





