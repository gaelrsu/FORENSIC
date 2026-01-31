#!/bin/bash
BASE="/media/ubuntu/USB/forensic_sorted"
OUT="/media/ubuntu/USB/windows_artifacts_found.txt"

echo "WINDOWS ARTEFACTS FOUND" > "$OUT"
echo "=======================" >> "$OUT"

find "$BASE" -type f | grep -Ei \
"NTUSER\.DAT|USRCLASS\.DAT|Recent|History|Cookies|WebCache|\.evtx|\.pf$|\.lnk$" \
>> "$OUT"

echo "✅ ARTEFACTS WINDOWS LISTÉS : $OUT"
