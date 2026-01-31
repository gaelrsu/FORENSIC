#!/bin/bash
BASE="/media/ubuntu/USB/forensic_sorted"
OUT="/media/ubuntu/USB/hashes_sha256.txt"

echo "SHA256 HASH LIST" > "$OUT"
echo "================" >> "$OUT"
echo "Date: $(date)" >> "$OUT"
echo "" >> "$OUT"

find "$BASE" -type f -exec sha256sum {} \; >> "$OUT"

echo "✅ HASHES GÉNÉRÉS : $OUT"
