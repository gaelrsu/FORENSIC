# Windows Registry

HKEY_CURRENT_USER : Contains the root of the configuration information for the user who is currently logged on. \
HKEY_USERS : Contains all the actively loaded user profiles on the computer. \
HKEY_LOCAL_MACHINE :  contains informations & parameters for all users on the computer. ex : software, global parameter .... HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run \
HKEY_CLASSES_ROOT : The information that is stored here makes sure that the correct program opens when you open a file by using Windows Explorer.  \
HKEY_CURRENT_CONFIG : Contains information about the hardware profile that is used by the local computer at system startup. 


## Hives

Found here : C:\Windows\System32\Config \
DEFAULT : HKEY_USERS\DEFAULT \
SAM : HKEY_LOCAL_MACHINE\SAM \
SECURITY : HKEY_LOCAL_MACHINE\Security \
SOFTWARE : HKEY_LOCAL_MACHINE\Software \
SYSTEM : HKEY_LOCAL_MACHINE\System \\
Or in user directory :  C:\Users\<username>\ \
NTUSER.DAT : HKEY_CURRENT_USER (when a user logs in) \
USRCLASS.DAT : HKEY_CURRENT_USER\Software\CLASSES
