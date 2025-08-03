I/ 

sources of data: 
  SIM (Subscriber Identity Module) / UICC(Universal Integrated Circuit Card)
  Media storage Cards
  Call Data Records (CDRs)
  Backups from computer or cloud storage
  Associated Internet of Things (IoT) device such as a paired smart watch
  Warrant Returns
  Self-Archives

Hierarchy of Directories

    Boot Partition (/boot): When your phone starts, the bootloader first loads the kernel and recovery loader from the boot partition. The kernel is responsible for the core functions of the operating system, and the recovery loader allows you to reset your phone to factory settings or access other advanced options.
    System Partition (/system): The system partition contains the files necessary for the Android operating system to function properly. These files include applications, frameworks, fonts, and settings.
    Data Partition (/data): The data partition contains all user-installed applications and data. This includes downloaded applications, photos, music, videos, and other files.
    Storage Partition (/storage): The storage partition contains external storage devices such as SD cards or USB drives. These devices can be used to provide additional storage space when the internal storage of your phone is full.
    Recovery Partition (/recovery): The recovery partition is a special partition that allows you to boot your phone into recovery mode or bootloader. Recovery mode lets you reset your phone to factory settings or access other advanced options.



II/ ABD
check if "Device Auth" needed
```
adb devices
```
enter shell 
```
adb shell
```
checl if MTP is mounted (and if unlock screen is needed)
```
mount | grep gvfs
```
if no auth need
``` 
ls -h /path/....
ls -al /path/..../mtp\:host\=DOOdge...../
```
Pull files 
```
Adb pull
Adb pull /source_path destination_path/

```

III/ Unlock
If we need to unlock the screen, use : Tenorshare 4uKey
delete : gesture.key to unlock 
```
rm /data/system/gesture.key
```
Brute force with Andriller

The following information is essential to get started:

    Device Model
    Serial Number
    IMEI Number
    Operating System Version
    Security Patch Level
    Whether the Device is Rooted
    User Profile
    Device Lock Status
























