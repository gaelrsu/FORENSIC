#!/bin/bash
REPORT="/media/ubuntu/USB/forensic_report.txt"
BASE="/media/ubuntu/USB/forensic_sorted"

echo "FORENSIC REPORT - WINDOWS RECOVERY" > "$REPORT"
echo "==================================" >> "$REPORT"
echo "" >> "$REPORT"
echo "Date : $(date)" >> "$REPORT"
echo "" >> "$REPORT"

echo "[+] FICHIERS RÉCUPÉRÉS :" >> "$REPORT"
find "$BASE" -type f | wc -l >> "$REPORT"

echo "" >> "$REPORT"
echo "[+] DÉTAIL PAR TYPE :" >> "$REPORT"
for d in docs images videos archives others; do
    echo "- $d : $(find "$BASE/$d" -type f 2>/dev/null | wc -l)" >> "$REPORT"
done

echo "" >> "$REPORT"
echo "[+] TOP 20 FICHIERS LES PLUS ANCIENS :" >> "$REPORT"
find "$BASE" -type f -printf "%T@ %p\n" | sort -n | head -20 >> "$REPORT"

echo "" >> "$REPORT"
echo "[+] FIN DU RAPPORT" >> "$REPORT"

echo "✅ RAPPORT GÉNÉRÉ : $REPORT"
