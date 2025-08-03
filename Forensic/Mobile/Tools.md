# TOOLS

I/ Andriller
```
sudo apt-get install android-tools-adb python3-tk
git clone https://github.com/den4uk/andriller.git
cd andriller
pip3 install -r requirements.txt
python3 -m andriller
```
Extract 
Click the 'Output' button in the 'Global Output Location' section and select a directory.
After connecting your device to the computer, click the 'Check' button in the 'Extraction (USB)' section. If Andriller successfully connects to the device, the serial number of the connected device will appear next to the button as "Serial ID", indicating that everything is proceeding correctly: 
now start the data extraction process by clicking the 'Extract' button. Andriller will attempt to retrieve files using the 'Device Backup' method and will ask you to allow the device to perform a backup. At this stage, you will need to go to the device and authorize.
| File Name     | Path                                                                                     | Content                                                             |
|---------------|------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| contacts.db   | /data/data/com.android.providers.contacts/databases/contacts.db                         | Contacts list, phone numbers, email addresses, and other contact information |
| sms.db        | /data/data/com.android.providers.sms/databases/sms.db                                   | Sent and received text messages                                    |
| calls.db      | /data/data/com.android.providers.call_log/databases/calls.db                            | Call logs, call durations, call numbers, and other details         |
| calendar.db   | /data/data/com.android.calendar/databases/calendar.db                                    | Calendar events, notes, and appointments                           |
| mmssms.db     | /data/data/com.android.providers.mms/databases/mmssms.db                                 | Multimedia messages (photos, videos, voice messages)               |


II/ Androidqf
Used to quickly provide the essential data needed for a digital forensics operation.
```
git clone https://github.com/botherder/androidqf.git
cd androidqf/build
./androidqf_linux_amd64
```
When you run the application, it automatically connects to the device connected to the computer and starts collecting information about it. The information collected is written to a directory with the same name as the "acquisition id" specified in the "Starting a new acquisition" section.
Then we will found : 

    The file "dumpsys.txt" contains the output of the "adb shell dumpsys" command. This file contains information about active and past activities, current windows and their states, battery status and history, and memory usage (meminfo).
    The 'getprop.txt' file contains the output of the 'adb shell getprop' command, which provides detailed information ranging from the device's serial number and model to its current hardware configuration.
    The 'logcat.txt' file contains the output of the 'adb shell logcat' command, which provides system log records.
    The “packages.json” file lists the APKs installed on the system and their details.
    The “processes.txt” file lists the running processes on the system and their details
    The “Settings_” files contain database dumps related to system settings.

    
