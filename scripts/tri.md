#!/bin/bash
RECUP_DIR="/media/ubuntu/USB/forensic_recovery"
OUT_DIR="/media/ubuntu/USB/forensic_sorted"

mkdir -p "$OUT_DIR"/{docs,images,videos,archives,others}

find "$RECUP_DIR" -type f | while read file; do
    case "${file,,}" in
        *.pdf|*.doc|*.docx|*.xls|*.xlsx|*.txt)
            mv "$file" "$OUT_DIR/docs/" ;;
        *.jpg|*.jpeg|*.png|*.gif)
            mv "$file" "$OUT_DIR/images/" ;;
        *.mp4|*.avi|*.mkv)
            mv "$file" "$OUT_DIR/videos/" ;;
        *.zip|*.rar|*.7z)
            mv "$file" "$OUT_DIR/archives/" ;;
        *)
            mv "$file" "$OUT_DIR/others/" ;;
    esac
done

echo "✅ TRI TERMINÉ : $OUT_DIR"
