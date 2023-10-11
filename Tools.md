# Tools

__________________________________________________________________________________
# Application

## Registry Explorer

## AppCompatCacheParser.exe
https://github.com/EricZimmerman/AppCompatCacheParser
extract metadata associated with application execution

## Volatility 
On kali extract from volatility memory 
https://github.com/volatilityfoundation/volatility3
```bash
volatility -f membump.mem --profile=Win10x64_14393 shincachemem --output=csv --output-file=./shimcache.csv
```

## AmcacheParser
https://github.com/EricZimmerman/AmcacheParser

__________________________________________________________________________________
# SRUM
## SRUM-DUMP
https://github.com/MarkBaggett/srum-dump






## scdbg shellcode debugger
```
scdbg.exe binName.bin
```


checksum verification or heuristic analysis.

__________________________________________________________________________________
# Forensic Imaging
```
Forensic imaging is a fundamental process in digital forensics that involves creating an exact,
bit-by-bit copy of digital storage media, such as hard drives, solid-state drives, USB drives,
and memory cards. This process is crucial for preserving the original state of the data, ensuring
data integrity, and maintaining the admissibility of evidence in legal proceedings. Forensic
imaging plays a critical role in investigations by allowing analysts to examine evidence without
altering or compromising the original data.
```
## Tools
- [AFF4 Imager](https://github.com/Velocidex/c-aff4)
- [FTK Imager](https://www.exterro.com/ftk-imager)
- DD and DCFLDD
- Virtualization Tools
- Mount the image from a wm with [Arsenal Image Mounter](https://arsenalrecon.com/downloads)

__________________________________________________________________________________
# Extracting Host-based Evidence & Rapid Triage
## memory acquisition tools
- [WinPmem](https://github.com/Velocidex/WinPmem)
- [DumpIt](https://www.magnetforensics.com/resources/magnet-dumpit-for-windows/) generates a physical memory dump of Windows and Linux
- [MemDump](https://www.nirsoft.net/utils/nircmd.html) capture the contents of a system's RAM
- [Belkasoft RAM Capturer](https://belkasoft.com/ram-capturer) capture the RAM of a running Windows computer
- [Magnet RAM Capture](https://www.magnetforensics.com/resources/magnet-ram-capture/) capture the volatile memory of a system
- [LiME (Linux Memory Extractor)](https://github.com/504ensicsLabs/LiME) capture volatile memory evading many common anti-forensic measures

## Rapid Triage
- [KAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape)
- [Velociraptor ](https://github.com/Velocidex/velociraptor)



__________________________________________________________________________________
# links
https://www.youtube.com/playlist?list=PLlv3b9B16ZadqDQH0lTRO4kqn2P1g9Mve

eCDFP

https://www.sans.org/blog/sans-dfir-course-roadmap-and-job-role-matrix/

https://www.13cubed.com/downloads/dfir_cheat_sheet.pdf

https://codered.eccouncil.org/course/digital-forensics-essentials?logged=true








