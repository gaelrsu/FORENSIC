#!/bin/bash
BASE="/media/ubuntu/USB/forensic_sorted"
REPORT="/media/ubuntu/USB/forensic_report_FINAL.txt"

echo "FORENSIC INVESTIGATION REPORT" > "$REPORT"
echo "=============================" >> "$REPORT"
echo "" >> "$REPORT"
echo "Investigation type : Post-OS Removal Analysis" >> "$REPORT"
echo "Source OS          : Windows (removed)" >> "$REPORT"
echo "Analysis OS        : Ubuntu Linux" >> "$REPORT"
echo "Date               : $(date)" >> "$REPORT"
echo "" >> "$REPORT"

echo "[1] FILE STATISTICS" >> "$REPORT"
echo "-------------------" >> "$REPORT"
find "$BASE" -type f | wc -l >> "$REPORT"

echo "" >> "$REPORT"
echo "[2] FILE TYPES" >> "$REPORT"
for d in docs images videos archives others; do
  echo "$d : $(find "$BASE/$d" -type f 2>/dev/null | wc -l)" >> "$REPORT"
done

echo "" >> "$REPORT"
echo "[3] OLDEST FILES (INDICATE PRIOR WINDOWS ACTIVITY)" >> "$REPORT"
find "$BASE" -type f -printf "%TY-%Tm-%Td %TH:%TM | %p\n" | sort | head -15 >> "$REPORT"

echo "" >> "$REPORT"
echo "[4] WINDOWS ARTIFACTS FOUND" >> "$REPORT"
grep -Ei "NTUSER|\.lnk|\.pf|\.evtx" /media/ubuntu/USB/windows_artifacts_found.txt \
2>/dev/null >> "$REPORT"

echo "" >> "$REPORT"
echo "[5] CONCLUSION" >> "$REPORT"
echo "Recovered files indicate prior Windows user activity." >> "$REPORT"
echo "File carving methodology used (PhotoRec)." >> "$REPORT"
echo "File structure integrity not preserved." >> "$REPORT"

echo "" >> "$REPORT"
echo "END OF REPORT" >> "$REPORT"

echo "✅ RAPPORT FINAL GÉNÉRÉ : $REPORT"
