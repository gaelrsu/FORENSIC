# Windows NTFS Index Attributes $I30 Files
Evidence of deleted or overwritten files may be present within the slack of the $I30 file.

## Tool to parse $I30

First you have to extract the file with FTKimager :
```
add evidence item => logical drive => C: => Path to the file => right clic on $I30 => export => desktop
```

### INDSParse
https://github.com/williballenthin/INDXParse
```
python INDXParse.py -c -d /I30
python INDXParse.py -c -d /I30 > output.csv
```
### sleuthkit
https://www.sleuthkit.org/































