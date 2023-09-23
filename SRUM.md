# System Resources Utilisation Manager
Track system ressources utilization like CPU, network activity ...

## Srum-Dump
```
C:\Windows\System32\sru\
srum_dump.exe -i SCRUMDB2.dat -o outfile.xlsx -t specifyTemplate.xlsx
# Grab the file is impossible you have to use tools :
```
### FTK imager 
```
File => Add evidence item => logical drive 
  Go to : C:\Windows\System32\sru\SRUDB.dat
right clic => export file => Desktop
```
### Via CMD
```
vssadmin list shadows
# copy the shadow path then create a link  !! think about the \at the end
mklink /d SRUM //shadowpath\

cd SRUM
cd Windows\System32\sru
copy SRUMDB.dat \Desktop\SRUMDB2.dat
# to remove :
rd /s SRUM
```
### ROBOCOPY


































