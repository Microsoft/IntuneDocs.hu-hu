---
title: "A Microsoft Intune App SDK áttekintése | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 8a9dfe8224b4e0e441691043eaffea73c456b3ec


---

# A Microsoft Intune App SDK áttekintése
Az iOS és az Android platformhoz is elérhető Intune App SDK lehetővé teszi a Microsoft Intune mobilalkalmazás-felügyeleti funkcióinak használatát. Emellett igyekeztünk csökkenteni a fejlesztők részéről szükséges kódmódosításokat. Az SDK legtöbb funkcióját alkalmazása viselkedésének módosítása nélkül is engedélyezheti. Ha hatékonyabbá szeretné tenni a végfelhasználók és a rendszergazdák munkáját, az API-jainkkal személyre szabhatja alkalmazása működését olyan funkciók tekintetében, amelyek használatához az alkalmazás közreműködése szükséges. 

Az alkalmazás engedélyezése után a rendszergazdák szabályzatokat telepíthetnek az Intune által felügyelt alkalmazásokhoz, és a vállalati adatok hatékonyabb védelmére használhatják ezeket a funkciókat.

# Jellemzők
## Vállalati dokumentumok felhasználók általi áthelyezésének szabályozása
A rendszergazdák az Intune által felügyelt alkalmazásokban szabályozhatják a vállalati dokumentumok áthelyezését. Telepíthet például olyan szabályzatot, amely megakadályozza, hogy az adott fájlról biztonsági másolatot készítő alkalmazások biztonsági másolatot készítsenek a vállalati adatokról a felhőbe.  

## Vágólappal kapcsolatos korlátozások beállítása
A rendszergazdák konfigurálhatják a vágólap működését az Intune által felügyelt alkalmazásokban. Telepíthetnek például olyan szabályzatot, amely megakadályozza, hogy a végfelhasználók a vágólap segítségével adatokat másoljanak vagy vágjanak ki az Intune által felügyelt alkalmazásokból, és nem felügyelt alkalmazásokba illesszék be azokat.

## Képernyőfelvételek készítésére vonatkozó korlátozások konfigurálása
A rendszergazdák megakadályozhatják, hogy a felhasználók képernyőfelvételeket készítsenek az Intune által felügyelt alkalmazásokról. Ezzel a korlátozással elkerülhető a bizalmas vállalati információk rögzítése és nyilvánosságra hozatala. Ez a funkció csak Android-eszközök esetén használható. 

## Mentett adatok titkosításának kényszerítése
A rendszergazdák olyan szabályzatot alkalmazhatnak, amely biztosítja, hogy az alkalmazás által az adott eszközre mentett adatok titkosítva legyenek.

## Vállalati adatok távoli törlése
A rendszergazdák távolról törölhetik az Intune által felügyelt alkalmazásokból a vállalati adatokat, amikor megszüntetik az eszköz Microsoft Intune-beli regisztrációját. Ez a funkció identitásalapú, és csak azokat a fájlokat törli, amelyek az adott végfelhasználó vállalati identitásához kapcsolódnak. A szolgáltatásnak ehhez az alkalmazás közreműködésére van szüksége. Az alkalmazás a felhasználói beállítások alapján határozza meg azt az identitást, amelyhez a törlést végre kell hajtani. Ilyen felhasználói beállítások hiányában alapértelmezés szerint az alkalmazás könyvtára lesz törölve, és a végfelhasználó értesítést kap arról, hogy a vállalati erőforrásokhoz való hozzáférését visszavonták. 

## Felügyelt böngésző használatának kényszerítése
A rendszergazdák felügyelt böngésző használatát kényszeríthetik az Intune által felügyelt alkalmazásokban található hivatkozások megnyitásakor. A Microsoft Intune által felügyelt böngésző használatával biztosítható, hogy az (Intune által felügyelt levelezőprogramban megtekintett) e-mailekben megjelenő hivatkozások csak az Intune által felügyelt alkalmazások tartományán belüli helyekre mutassanak.

## PIN-kód használatára vonatkozó szabályzat alkalmazása
A rendszergazdák PIN-kód használatára vonatkozó szabályzat alkalmazását kényszeríthetik az Intune által felügyelt alkalmazások indításakor. Ezzel a szabályzattal meggyőződhetnek arról, hogy az alkalmazásokat indító felhasználók ugyanazok a végfelhasználók, akik a Microsoft Intune-ban regisztrálták eszközeiket. Amikor a végfelhasználók a PIN-kódjukat konfigurálják, az Intune App SDK az Azure Active Directory segítségével összehasonlítja a végfelhasználók hitelesítő adatait az eszközregisztrációs hitelesítő adatokkal. 

## Hitelesítő adatok kérése a felhasználóktól az alkalmazások indításához
A rendszergazdák megkövetelhetik, hogy a felhasználók az Intune által felügyelt alkalmazások indítása előtt adják meg hitelesítő adataikat. Az Intune App SDK az Azure Active Directory segítségével teszi lehetővé az egyszeri bejelentkezést, ami azt jelenti, hogy a hitelesítő adatokat elég egyszer megadni, és a későbbi bejelentkezések során a rendszer ismét azokat használja. A rendszer az [Azure Active Directoryval összevont](https://msdn.microsoft.com/en-us/library/azure/jj679342.aspx) identitáskezelési megoldások hitelesítését is támogatja. 

## Eszközök állapotának és megfelelőségének ellenőrzése
A rendszergazdák ellenőrizhetik az eszközök állapotát és vállalati szabályzatoknak való megfelelőségét, mielőtt a végfelhasználók hozzáférhetnének az Intune által felügyelt alkalmazásokhoz. Az iOS platformon a szabályzat ellenőrzi, hogy az eszköz jailbreakelve lett-e. Az Android platformon a szabályzat ellenőrzi, hogy az eszköz rootolt-e.  





<!--HONumber=Jun16_HO4-->


