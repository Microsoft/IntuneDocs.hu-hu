---
title: "Eszközök regisztrálása | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69cf07aa0747448e0ef3384b5b5132e0e76aed45
ms.openlocfilehash: 930cbc806d8fd1185cf33fd64d866b88ec9a6a04


---

# Eszközök regisztrálása felügyeletre a Microsoft Intune-ban
A Microsoft Intune mobileszköz-kezelési (MDM) funkciója a regisztráció segítségével vonja felügyelet alá az eszközöket, és teszi lehetővé az erőforrásokhoz való hozzáférést. Az eszközök regisztrálásának módja az eszköz típusától, a tulajdonostól, és a felügyeleti szinttől függ. A „saját eszközök használata” (BYOD) és a vállalati tulajdonban lévő eszközök (COD) használata esetén szükség van a regisztrálási folyamatra. A helyi vagy felhőalapú Exchange ActiveSync programot használó vállalatok számára egyszerűbb, regisztráció nélküli felügyelet is megvalósítható. Az Intune ügyfélszoftvere segítségével Windows-számítógépek is felügyelhetők.

###  Támogatott eszközplatformok

Az Intune a következő eszközplatformokat képes kezelni:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Az eszközök regisztrálási módszereinek áttekintése

A következő táblázat a vállalati tulajdonú eszközök regisztrálási módszereit, valamint azok előnyeit foglalja össze.

**iOS-eszközök regisztrálási módszerei**

| **Módszer** |  **[Törlés](#Wipe)** | **[Affinitás](#Affinity)**   |   **[Zárolás](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nem|    Igen |   Nem |
|**[DEM](#DEM)**|   Nem |Nem |Nem  |
|**[DEP](#DEP)**|   Igen |   Választható |   Választható|
|**[USB-SA](#USB-SA)**| Igen |   Választható |   Nem|
|**[USB-Direct](#USB-Direct)**| Nem |    Nem  | Nem|

**Windows- és Android-eszközök regisztrálási módszerei**

| **Módszer** |  **[Törlés](#Wipe)** | **[Affinitás](#Affinity)**   |   **[Zárolás](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nem|    Igen |   Nem |
|**[DEM](#DEM)**|   Nem |Nem |Nem  |

**A vállalati tulajdonú eszközök regisztrálási módszerei**

### BYOD
„Saját eszközök használata” (Bring Your Own Device). A felhasználók telepítik a Vállalati portál alkalmazást, és ők regisztrálják az eszközt. Az eszközök Vállalati portálon keresztüli regisztrálása az eszközt munkahelyi csatlakoztatással csatlakoztatja. iOS-eszközök Vállalati portálon keresztüli beléptetéséhez Apple ID azonosító szükséges. A BYOD módszer esetén nincs szükség a vállalati tulajdonú eszközök további konfigurálására. Lásd az [eszközkezelés beállításának](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management) lépéseit. ([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

### DEM
Eszközregisztráció-kezelő. A rendszergazda létrehozza a DEM-fiókokat a vállalati tulajdonú eszközök kezeléséhez. A kezelők ezután telepíteni tudják a Vállalati portált, és több, felhasználó nélküli eszközt regisztrálhatnak. További információ a [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) módszerről. ([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

### DEP
Apple Device Enrollment Program (Apple Készülékregisztrációs program). A rendszergazda a DEP-en keresztül vásárolt és kezelt, vállalati tulajdonú iOS-eszközökön „vezeték nélküli” szabályzatokat hoz létre és telepít. Az eszköz regisztrálása akkor történik meg, amikor a felhasználó az iOS-alapú Beállítási asszisztenst futtatja. Ez a módszer támogatja az **iOS-eszközök Felügyelt** módját, amely a következő funkciókat engedélyezi:
  - Zárolt regisztráció
  - Feltételes hozzáférés
  - Függetlenítés észlelése
  - Mobilalkalmazás-kezelés

További információk a [DEP](ios-device-enrollment-program-in-microsoft-intune.md) programról. ([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

### USB-SA
USB-kapcsolaton keresztüli, a Beállítási asszisztens használatával történő regisztrálás. A rendszergazda létrehoz egy Intune-szabályzatot, és exportálja azt az Apple Configuratorba. Az USB-csatlakozóval csatlakoztatott, vállalati tulajdonú eszközök előkészítése Intune-házirendekkel történik. A rendszergazdának minden eszközt manuálisan kell regisztrálnia. A felhasználók megkapják eszközüket, majd a Beállítási asszisztens futtatásával regisztrálják azt. Ez a módszer támogatja az **iOS-eszközök Felügyelt** módját, amely a következő funkciókat engedélyezi:
  - Feltételes hozzáférés
  - Függetlenítés észlelése
  - Mobilalkalmazás-kezelés

További információ [az eszközöknek az Apple Configurator és Beállítási asszisztens segítségével történő regisztrálásáról](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

### USB-Direct
Közvetlen regisztráció. A rendszergazda létrehoz egy Intune-szabályzatot, és exportálja azt az Apple Configuratorba. Az USB-csatlakozóval csatlakoztatott, vállalati tulajdonú eszközök regisztrálása közvetlenül történik, a gyári beállítások visszaállítása nem szükséges. A rendszergazdának minden eszközt manuálisan kell regisztrálnia. Az eszközök kezelése felhasználó nélküli eszközökként történik. Nincsenek zárolva, sem felügyelve, és nem támogathatják a feltételes hozzáférést, a függetlenítés észlelését és a mobilalkalmazás-kezelést. További információk [az Apple Configurator segítségével történő közvetlen regisztrálásáról](ios-direct-enrollment-in-microsoft-intune.md). ([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

**A vállalati tulajdonú mobileszközök működése**

### Törlés
Meghatározza, hogy az eszköz beléptetéséhez szükség van-e az eszköz gyári beállításainak visszaállítására. Ez eltávolít minden adatot az eszközről, és az eredeti állapotba állítja azt vissza.
([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

### Affinitás
Meghatározza, hogy a regisztrálási módszer támogatja-e a „Felhasználói affinitást”, amely az eszközt egy adott felhasználóval kapcsolja össze. A „Választható” jelölésű eszközök felhasználói affinitással és anélkül egyaránt regisztrálhatók. Felhasználói affinitás szükséges az alábbiak támogatásához:
  - Mobilalkalmazás-felügyeleti (MAM) alkalmazások
  - Feltételes hozzáférés az e-mailekhez és a vállalati adatokhoz
  - Vállalati portál alkalmazás

([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

### Zárolás
Meghatározza, hogy lehet-e az eszközt zárolni annak megakadályozására, hogy a felhasználó el tudja távolítani az Intune-szabályzatot. Ez a művelet gyakorlatilag kivonja az eszközt a felügyelet alól. Az iOS-eszközök csak akkor zárolhatók, ha Felügyelt módban vannak.
([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods)) ([Vissza a táblázathoz](#overview-of-corporate-owned-device-enrollment-methods))

## Eszközök regisztrálásának lehetővé tétele  
 A regisztráció segítségével a felhasználók saját eszközükön is hozzáférhetnek a vállalati erőforrásokhoz, a rendszergazdák pedig ellenőrizhetik, hogy ezek az eszközök megfelelnek-e a vállalati erőforrások védelmét szolgáló szabályzatok előírásainak. Ez a legjobb módszer arra, hogy az Intune segítségével lehetővé váljon a „saját eszközök használata”. A rendszergazdának engedélyeznie kell a regisztrációt az Intune konzolban. Ehhez esetenként megbízhatósági kapcsolatot kell létrehozni az eszközzel, és licencet kell rendelni a felhasználókhoz. Ezt követően megtörténik az eszköz regisztrálása, általában azzal, hogy a felhasználó megadja munkahelyi vagy iskolai hitelesítő adatait. Az eszköz lekéri a szabályzatot az Intune-ból, és ezzel hozzáféréshez jut az erőforrásokhoz.

[Felkészülés az eszközök Intune-beli regisztrálására](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Vállalati tulajdonú eszközök regisztrálása
A vállalati tulajdonú eszközök (COD) az Intune konzol segítségével kezelhetők. Az iOS-eszközök az Apple által biztosított megoldások segítségével közvetlenül is regisztrálhatók. A rendszergazdák vagy menedzserek bármilyen típusú eszközt regisztrálhatnak az eszközregisztráció-kezelő segítségével. Az IMEI-számmal rendelkező eszközöket azonosítani lehet, és meg lehet jelölni vállalati tulajdonúként, ami lehetőséget nyújt a vállalati tulajdonú eszközök kezelésére.

[Vállalati tulajdonú eszközök regisztrálása](manage-corporate-owned-devices.md)

## Mobileszköz-kezelés az Exchange ActiveSync és az Intune használatával
Azok a mobileszközök, amelyek nincsenek regisztrálva, de kapcsolódnak az Exchange ActiveSync (EAS) rendszerhez, EAS MDM-szabályzat segítségével kezelhetők az Intune-ban. Az Intune egy helyi vagy felhőalapú Exchange Connector összekötő segítségével kommunikál az EAS-szel.



[Mobileszköz-kezelés az Exchange ActiveSync és az Intune használatával](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Windows rendszerű számítógépek felügyelete az Intune-nal  
Az Intune Windowsra készült számítógépes ügyfélszoftvere segítségével Windows-számítógépeket is kezelhet a Microsoft Intune-ban. Az Intune ügyfél által felügyelt Windows-számítógépek:

 - Képesek szoftver- és hardverleltár jelentésére
 - Képesek asztali alkalmazások telepítésére (például .exe és .msi kiterjesztésű fájlok segítségével)
 - Tűzfalbeállítások

Az Intune ügyfélszoftverével felügyelt számítógépeken nem lehet szelektív törlést végezni, az ilyen gépek nem vonhatók ki, és az Intune számos felügyeleti funkciója (például a feltételes hozzáférés, a VPN- és Wi-Fi-beállítások meghatározása vagy a tanúsítványok és e-mail-konfigurációk telepítése) sem használható.

[Windows rendszerű számítógépek felügyelete az Intune-nal](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Jun16_HO5-->


