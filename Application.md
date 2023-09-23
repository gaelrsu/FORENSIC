# Application

## RecentFileCache.bef
Registry Explorer
Contains metadata associated with application execution in Windows 7
```
C:\Windows\AppCompat\Program\
```
## AppCompatCache
Registry Explorer
Contains metadata associated with application execution in Windows 10
```
key: HKEY_LOCAL_MACHINE\SYSTEM\CurentControlSet\Control\Session Manager\AppCompatCache
```

## Check app hash
```
shasum app.exe
```

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








