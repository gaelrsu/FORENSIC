#!/bin/bash
# ============================================
# Windows Data Recovery - Forensic Safe Script
# ============================================

# >>>>>> À ADAPTER <<<<<<
SOURCE_DISK="/dev/sda"                     # disque Ubuntu (SOURCE)
DEST_MOUNT="/media/ubuntu/USB"             # point de montage du disque USB
DEST_DIR="$DEST_MOUNT/forensic_recovery"   # dossier de sortie
# >>>>>>>>>>>>>>>>>>>>>>>

clear
echo "============================================"
echo "  FORENSIC RECOVERY SCRIPT (PhotoRec)"
echo "============================================"
echo
echo "DISQUE SOURCE     : $SOURCE_DISK"
echo "DISQUE DESTINATION: $DEST_DIR"
echo
echo "⚠️  AUCUNE écriture sur le disque source"
echo "⚠️  La récupération ira UNIQUEMENT sur l'USB"
echo
read -p "CONFIRMER (oui/non) : " CONFIRM

if [[ "$CONFIRM" != "oui" ]]; then
    echo "❌ Annulé"
    exit 1
fi

# Vérifications
if [ ! -b "$SOURCE_DISK" ]; then
    echo "❌ Disque source introuvable"
    exit 1
fi

if [ ! -d "$DEST_MOUNT" ]; then
    echo "❌ Disque USB non monté"
    exit 1
fi

# Préparation
sudo mkdir -p "$DEST_DIR"
sudo chmod 777 "$DEST_DIR"

echo
echo "✅ Destination prête"
echo "📁 $DEST_DIR"
echo
echo "🚀 Lancement de PhotoRec"
echo "--------------------------------------------"
echo "Choix à faire dans PhotoRec :"
echo "  - Disque       : $SOURCE_DISK"
echo "  - Partition    : Whole disk"
echo "  - File system  : Other"
echo "  - Destination  : $DEST_DIR"
echo "--------------------------------------------"
echo

sudo photorec "$SOURCE_DISK"

echo
echo "============================================"
echo "  RÉCUPÉRATION TERMINÉE"
echo "============================================"
echo "Résultats dans : $DEST_DIR"
