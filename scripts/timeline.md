#!/bin/bash
TARGET_DIR="/media/ubuntu/USB/forensic_sorted"
OUT_FILE="/media/ubuntu/USB/timeline_windows.txt"

echo "DATE | FICHIER" > "$OUT_FILE"
echo "---------------------------" >> "$OUT_FILE"

find "$TARGET_DIR" -type f -printf "%TY-%Tm-%Td %TH:%TM:%TS | %p\n" \
| sort >> "$OUT_FILE"

echo "✅ TIMELINE CRÉÉE : $OUT_FILE"
