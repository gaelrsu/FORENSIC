##pour importation dans Excel Autopsy Timesketch ###

#!/bin/bash
BASE="/media/ubuntu/USB/forensic_sorted"
OUT="/media/ubuntu/USB/timeline_windows.csv"

echo "date,time,file_path" > "$OUT"

find "$BASE" -type f -printf "%TY-%Tm-%Td,%TH:%TM:%TS,%p\n" \
| sort >> "$OUT"

echo "✅ TIMELINE CSV CRÉÉE : $OUT"
