---
title: "Az Intune App SDK által nyújtott előnyök | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: 3abf566831348de11f718370d6267e3ff4355bfb


---

# Az Intune App SDK áttekintése
Az iOS és az Android platformhoz is elérhető Intune App SDK lehetővé teszi a Microsoft Intune mobilalkalmazás-felügyeleti funkcióinak használatát. Emellett igyekeztünk csökkenteni a fejlesztők részéről szükséges kódmódosításokat. Az SDK legtöbb funkcióját alkalmazása viselkedésének módosítása nélkül is engedélyezheti. Ha hatékonyabbá szeretné tenni a végfelhasználók és a rendszergazdák munkáját, az API-jainkkal személyre szabhatja alkalmazása működését olyan funkciók tekintetében, amelyek használatához az alkalmazás közreműködése szükséges. Az alkalmazás engedélyezése után a rendszergazdák szabályzatokat telepíthetnek az Intune által felügyelt alkalmazásokhoz, és a vállalati adatok hatékonyabb védelmére használhatják ezeket a funkciókat.

## Normál funkciók

### Vállalati dokumentumok felhasználók általi áthelyezésének szabályozása
A rendszergazdák az Intune által felügyelt alkalmazásokban szabályozhatják a vállalati dokumentumok áthelyezését. Telepíthet például olyan szabályzatot, amely megakadályozza, hogy az adott fájlról biztonsági másolatot készítő alkalmazások biztonsági másolatot készítsenek a vállalati adatokról a felhőbe.

### Vágólappal kapcsolatos korlátozások beállítása
A rendszergazdák konfigurálhatják a vágólap működését az Intune által felügyelt alkalmazásokban. Telepíthetnek például olyan szabályzatot, amely megakadályozza, hogy a végfelhasználók a vágólap segítségével adatokat másoljanak vagy vágjanak ki az Intune által felügyelt alkalmazásokból, és nem felügyelt alkalmazásokba illesszék be azokat.

### Képernyőfelvételek készítésére vonatkozó korlátozások konfigurálása
A rendszergazdák megakadályozhatják, hogy a felhasználók képernyőfelvételeket készítsenek az Intune által felügyelt alkalmazásokról. Ezzel a korlátozással elkerülhető a bizalmas vállalati információk rögzítése és nyilvánosságra hozatala. Ez a funkció csak Android-eszközök esetén használható.

### Mentett adatok titkosításának kényszerítése
A rendszergazdák olyan szabályzatot alkalmazhatnak, amely biztosítja, hogy az alkalmazás által az adott eszközre mentett adatok titkosítva legyenek.

### Vállalati adatok távoli törlése
A rendszergazdák távolról törölhetik az Intune által felügyelt alkalmazásokból a vállalati adatokat, amikor megszüntetik az eszköz Microsoft Intune-beli regisztrációját. Ez a funkció identitásalapú, és csak azokat a fájlokat törli, amelyek az adott végfelhasználó vállalati identitásához kapcsolódnak. A szolgáltatásnak ehhez az alkalmazás közreműködésére van szüksége. Az alkalmazás a felhasználói beállítások alapján határozza meg azt az identitást, amelyhez a törlést végre kell hajtani. Ilyen felhasználói beállítások hiányában alapértelmezés szerint az alkalmazás könyvtára lesz törölve, és a végfelhasználó értesítést kap arról, hogy a vállalati erőforrásokhoz való hozzáférését visszavonták.

### Felügyelt böngésző használatának kényszerítése
A rendszergazdák felügyelt böngésző használatát kényszeríthetik az Intune által felügyelt alkalmazásokban található hivatkozások megnyitásakor. A Microsoft Intune által felügyelt böngésző használatával biztosítható, hogy az (Intune által felügyelt levelezőprogramban megtekintett) e-mailekben megjelenő hivatkozások csak az Intune által felügyelt alkalmazások tartományán belüli helyekre mutassanak.

### PIN-kód használatára vonatkozó szabályzat alkalmazása
A rendszergazdák PIN-kód használatára vonatkozó szabályzat alkalmazását kényszeríthetik az Intune által felügyelt alkalmazások indításakor. Ezzel a szabályzattal meggyőződhetnek arról, hogy az alkalmazásokat indító felhasználók ugyanazok a végfelhasználók, akik a Microsoft Intune-ban regisztrálták eszközeiket. Amikor a végfelhasználók beállítják PIN-kódjukat, az Intune App SDK az Azure Active Directory segítségével összehasonlítja a végfelhasználók hitelesítő adatait az eszközregisztrációs hitelesítő adatokkal.

### Hitelesítő adatok kérése a felhasználóktól az alkalmazások indításához
A rendszergazdák megkövetelhetik, hogy a felhasználók az Intune által felügyelt alkalmazások indítása előtt adják meg hitelesítő adataikat. Az Intune App SDK az Azure Active Directory segítségével teszi lehetővé az egyszeri bejelentkezést, ami azt jelenti, hogy a hitelesítő adatokat elég egyszer megadni, és a későbbi bejelentkezések során a rendszer ismét azokat használja. A rendszer az [Azure Active Directoryval összevont](https://msdn.microsoft.com/library/azure/jj679342.aspx) identitáskezelési megoldások hitelesítését is támogatja.

### Eszközök állapotának és megfelelőségének ellenőrzése
A rendszergazdák ellenőrizhetik az eszközök állapotát és vállalati szabályzatoknak való megfelelőségét, mielőtt a végfelhasználók hozzáférhetnének az Intune által felügyelt alkalmazásokhoz. Az iOS platformon a szabályzat ellenőrzi, hogy az eszköz jailbreakelve lett-e. Az Android platformon a szabályzat ellenőrzi, hogy az eszköz rootolt-e.

## Előzetes verziójú funkciók
A Microsoft Intune App SDK több „előzetes verziójú” funkciót is tartalmaz. Megkezdheti az előzetes verziójú API-kkal való integrációt, de csak tesztelési célokra. Megjegyzendő, hogy ezek az előzetes verziójú funkciók kiegészítik, nem pedig leváltják a meglévő forgatókönyveket.

### Többszörös identitás támogatása a Microsoft Intune App SDK-ban
A többszörös identitás támogatása lehetővé teszi a szabályzatok által felügyelt (vállalati) és a felügyelet nélküli (személyes) fiókok ugyanazon alkalmazásban való egyidejű használatát.

### Példa a többszörös identitás használatára
Számos felhasználó konfigurál vállalati és személyes e-mail fiókot is az iOS, illetve az Android rendszerhez készült Outlook alkalmazásban. Amikor a felhasználó a vállalati fiók adataihoz fér hozzá, a rendszergazdának biztosnak kell lennie abban, hogy arra alkalmazva lesz az MAM-szabályzatokon alapuló felügyelet. Ugyanakkor ha a felhasználó a személyes e-mail fiókjához fér hozzá, az adatoknak a rendszergazda felügyeletén kívül kell esniük. A Microsoft Intune ezt úgy éri el, hogy a felügyeleti szabályzatot az alkalmazásban csak a vállalati fiókra alkalmazza. A többszörös identitás támogatása megoldást kínál arra az adatvédelmi problémára, amellyel a szervezetek a személyes és munkahelyi fiókokat egyaránt támogató alkalmazások és eszközök használata során szembesülnek.

### A többszörös identitás támogatásának módja
Az előzetes verziójú API-k lehetővé teszik egy egyszerű felhasználónév (UPN) megadását meghatározott – például vágólapalapú – adatműveletekhez, valamit fájlműveletekhez. A Microsoft Intune App SDK ellenőrzi, hogy a híváshoz használt UPN egyezik-e az eszköz Microsoft Intune szolgáltatásban való regisztrációjához használt UPN-nel. Ha az UPN-ek egyeznek, a hívást vállalati adatokra vonatkozó hívásként kezeli a rendszer, és gondoskodik az adatok védelméről. Ha az UPN-ek nem egyeznek, a rendszer a hívást személyes adatokra vonatkozó hívásként kezeli, és nem alkalmaz adatvédelmet.

### Alkalmazásfelügyelet eszközregisztráció nélkül
A saját eszközt használó felhasználók sok esetben anélkül szeretnének vállalati adatokat megtekinteni és használni, hogy eszközüket mobileszköz-felügyeleti (MDM) termékben kellene regisztrálniuk. Az MDM-alapú regisztrációhoz globális irányítás szükséges az eszköz felett, a felhasználók pedig sok esetben nem szívesen biztosítanak saját eszközük felett ilyen mértékű irányítást a vállalatnak.

A regisztráció nélküli eszközfelügyelettel a Microsoft Intune szolgáltatás közvetlenül az alkalmazásokra alkalmazhat MAM-szabályzatokat, mindehhez nincs szüksége MDM-csatornára. Mivel nincs szükség MDM-csatornára, MDM-regisztráció sem szükséges.




<!--HONumber=Jun16_HO4-->


