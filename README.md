# python-2
# 1. Kitoblar bazasi (Ro'yxat ichida lug'atlar - List of Dictionaries)
kutubxona = [
    {"id": 1, "nom": "O'tkan kunlar", "muallif": "Abdulla Qodiriy", "mavjud": True},
    {"id": 2, "nom": "Dunyoning ishlari", "muallif": "O'tkir Hoshimov", "mavjud": True},
    {"id": 3, "nom": "Yulduzli tunlar", "muallif": "Pirimqul Qodirov", "mavjud": False}
]

# 2. Yangi kitob qo'shish funksiyasi (append metodi)
def kitob_qoshish(yangi_nom, yangi_muallif):
    yangi_kitob = {
        "id": len(kutubxona) + 1,
        "nom": yangi_nom,
        "muallif": yangi_muallif,
        "mavjud": True
    }
    kutubxona.append(yangi_kitob)
    print(f"✅ '{yangi_nom}' kitobi kutubxonaga qo'shildi.")

# 3. Barcha kitoblarni konsolga chiroyli chiqarish (for tsikli)
def kitoblarni_ko_rsat():
    print("\n--- Kutubxonadagi barcha kitoblar ---")
    for kitob in kutubxona:
        holat = "Mavjud" if kitob["mavjud"] else "Ijaraga berilgan"
        print(f"{kitob['id']}. \"{kitob['nom']}\" - {kitob['muallif']} ({holat})")

# 4. Kitobni ijaraga olish funksiyasi
def kitob_olish(kitob_nomi):
    topilgan_kitob = None
    
    # Kitobni nom bo'yicha qidirish
    for kitob in kutubxona:
        if kitob["nom"].lower() == kitob_nomi.lower():
            topilgan_kitob = kitob
            break

    if topilgan_kitob:
        if topilgan_kitob["mavjud"]:
            topilgan_kitob["mavjud"] = False
            print(f"\n📖 Marhamat, siz '{topilgan_kitob['nom']}' kitobini oldingiz.")
        else:
            print(f"\n❌ Kechirasiz, '{topilgan_kitob['nom']}' kitobi hozir ijarada.")
    else:
        print(f"\n🔍 Afsuski, bizda '{kitob_nomi}' nomli kitob topilmadi.")


# ---- TIZIMNI ISHLATIB KO'RISH ----

kitoblarni_ko_rsat()  # Dastlabki holatni ko'rish

kitob_qoshish("Sariq devni minib", "Xudoyberdi To'xtaboyev")  # Yangi kitob qo'shish

kitob_olish("O'tkan kunlar")  # Kitobni ijaraga olish

kitoblarni_ko_rsat()  # O'zgargan holatni qayta tekshirish
