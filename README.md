#!/bin/bash

# include utils
source utils/functions.sh

clear
echo "=============================================="
echo "         TURKCHAIN NODE INSTALLER"
echo "=============================================="
echo ""
echo "Select Language / Dil Seçiniz:"
echo ""
echo "  1) English"
echo "  2) Türkçe"
echo ""
read -p "Choice / Seçim (1-2): " LANG

if [ "$LANG" == "1" ]; then
    LANGUAGE="EN"
elif [ "$LANG" == "2" ]; then
    LANGUAGE="TR"
else
    echo "Invalid choice! / Geçersiz seçim!"
    exit 1
fi

clear
echo "=============================================="
echo "         TURKCHAIN NODE INSTALLER"
echo "=============================================="

if [ "$LANGUAGE" == "EN" ]; then
    echo ""
    echo "Which type of node do you want to install?"
    echo ""
    echo "  1) Validator Node"
    echo "  2) Full Node"
    echo "  3) RPC Node"
    echo "  4) Seed Node"
    echo ""
    read -p "Enter your choice (1-4): " SECIM

else
    echo ""
    echo "Hangi tür node kurmak istiyorsun?"
    echo ""
    echo "  1) Validator Node"
    echo "  2) Full Node"
    echo "  3) RPC Node"
    echo "  4) Seed Node"
    echo ""
    read -p "Seçimini gir (1-4): " SECIM
fi

case $SECIM in
    1)
        [ "$LANGUAGE" == "EN" ] && echo "[+] Validator Node selected" || echo "[+] Validator Node seçildi"
        create_validator_node
        ;;
    2)
        [ "$LANGUAGE" == "EN" ] && echo "[+] Full Node selected" || echo "[+] Full Node seçildi"
        run_fullnode
        ;;
    3)
        [ "$LANGUAGE" == "EN" ] && echo "[+] RPC Node selected" || echo "[+] RPC Node seçildi"
        run_rpc
        ;;
    4)
        [ "$LANGUAGE" == "EN" ] && echo "[+] Seed Node selected" || echo "[+] Seed Node seçildi"
        run_seed
        ;;
    *)
        [ "$LANGUAGE" == "EN" ] && echo "Invalid choice!" || echo "Hata: Geçersiz seçim!"
        exit 1
        ;;
esac
