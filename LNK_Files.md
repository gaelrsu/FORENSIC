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


















