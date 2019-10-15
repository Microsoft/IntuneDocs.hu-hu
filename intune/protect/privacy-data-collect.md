---
title: Adatgyűjtés az Intune-ban
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan gyűjti össze a személyes adatokat az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd1d0de4b1ae930ebeff07539f9cfa8848f0b7ce
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306907"
---
# <a name="data-collection-in-intune"></a>Adatgyűjtés az Intune-ban

Ha a felhasználók az Intune-nal regisztrálják vállalati vagy személyes eszközeiket, akkor az Intune néhány személyes adatot gyűjt és oszt meg. Az Intune a következő forrásokból gyűjt személyes adatokat:

- A rendszergazda használja az Intune-t a Azure Portal.
- Végfelhasználói eszközök (amikor regisztrálnak az Intune felügyeletére és a használat során).
- A harmadik féltől származó szolgáltatásokhoz tartozó felhasználói fiókok (a rendszergazda utasításai szerint).
- Diagnosztikai, teljesítmény-és használati információk.

Ezekből a forrásokból az Intune a következő három kategóriába tartozó adatokat gyűjti össze: [azonosított](#identified-data), [álneves](#pseudonymized-data)és [aggregált](#aggregated-data).

> [!NOTE]
> A szolgáltatás által gyűjtött adatokat semmilyen okból nem adjuk át harmadik félnek.

## <a name="identified-data"></a>Azonosított adatértékek

Az Intune által gyűjtött legtöbb személyes adatok azonosított adatok. Ezek az adategységek egy felhasználóhoz, eszközhöz vagy alkalmazáshoz vannak kötve, és elengedhetetlenek a felügyelet természetéhez. Az azonosított adatként a felhasználó eszközének és alkalmazásainak kezeléséhez, valamint az Intune szolgáltatás üzembe helyezéséhez van szükség.

Az Intune által gyűjtött azonosított adatok tartalmazhatnak, de nem korlátozódnak a következőkre: 

- Felhasználói adatok
  - Tulajdonos neve/felhasználó megjelenítése (a theAzureUserID által azonosított felhasználó Azure-ban regisztrált neve)
  - Egyszerű felhasználónév vagy e-mail-cím
  - A harmadik féltől származó felhasználó azonosítja (például AppleID)
- A hardver leltárával kapcsolatos információk
  - Eszköz neve
  - Gyártó
  - Operációs rendszer
  - Sorozatszám
  - IMEI-szám
  - IP-cím
  - Wi-Fi MacAddress
  - ICCID
  - Telefonszám
- Naplózási adatok, beleértve a következő tevékenységekkel kapcsolatos adatokat
  - Kezelés
  - Létrehozás
  - Frissítés (Szerkesztés)
  - Törlés
  - Hozzárendelés
  - Távoli feladatok
- Támogatási információk
  - Kapcsolattartási adatok (név, telefonszám, e-mail-cím)
  - E-mailes beszélgetések a Microsoft terméktámogatási, termék-és/vagy felhasználói élményért felelős csapatának tagjaival
- Hozzáférés-vezérlési adatok (az Intune ezeket az adatokat használja a rendszergazdai szerepkörökhöz és függvényekhez való hozzáférés kezeléséhez olyan funkciókkal, mint a [szerepköralapú Access Control](../fundamentals/role-based-access-control.md).
  - Statikus hitelesítő (ügyfél jelszava)
  - Tanúsítványok adatvédelmi kulcsa 
- Rendszergazdai és fiókadatok
  - Rendszergazdai felhasználó vezetékneve és utóneve
  - Rendszergazdai Felhasználónév
  - Egyszerű felhasználónév (e-mail)
  - Telefonszám
  - Fiók tulajdonosának e-mail-címe
  - Az ügyfél rendszergazdájának Active Directory azonosítója
  - Fizetési információk ügyfél-számlázáshoz
  - Előfizetői azonosító
- Alkalmazás leltározása, például:
  - Alkalmazás neve
  - version
  - alkalmazás azonosítója
  - Méret
  - telepítési hely
  - Az alkalmazás leltározási adatok csak akkor lesznek összegyűjtve, ha a rendszergazda megjelöli a vállalati tulajdonú eszközként, vagy ha be van kapcsolva a megfelelő alkalmazás funkció.  
- Az ügyfél harmadik féltől származó bérlői azonosítói, például az Apple ID. 

## <a name="pseudonymized-data"></a>Álneves adathalmaz

Az álneves adat egy egyedi azonosítóval van társítva, amely általában a rendszer által a saját azonosítására nem alkalmas, de a vállalati szolgáltatások felhasználók számára történő továbbítására használt szám. 

Az Intune által gyűjtött álneves adatok tartalmazhatnak, de nem korlátozódnak a következőkre: 

- Felhasználóhoz és/vagy eszközhöz kötött diagnosztikai, teljesítmény-és használati adatok
  - A szolgáltatás használatának időpontjának száma
  - A szolgáltatáshoz megadott parancsok
  - A szolgáltatás válaszideje
  - A telepítések és egyéb folyamatok sikerességi aránya
  - Az Intune vállalati portál alkalmazás hibái
  - Felhasználó-és eszköz-azonosítók
  - Azonosítók referencia-, korrelációs, kezelési célokra 
- Eszközhöz vagy felhasználóhoz nem kötött eszközbeállítások (ha ezek az eszközök egy eszközhöz vagy felhasználóhoz vannak kötve, az Intune azonosított adatként kezeli azt)
  - Intune-eszköz azonosítója
  - Azure Active Directory eszköz azonosítója
  - Intune-eszközkezelés azonosítója
  - Bérlőazonosító
  - Fiókazonosító
  - EAS-eszköz azonosítója
  - Platform-specifikus azonosítók
  - AppleID iOS-eszközökhöz
  - MAC-címek Mac-eszközökhöz
  - Windows-azonosító Windows-eszközökhöz
- Felügyelt alkalmazás adatai
  - Felügyelt alkalmazás azonosítója
  - Felügyelt alkalmazás-eszköz címkéje
  - Intune-eszközkezelés azonosítója
  - Azure Active Directory eszköz azonosítója
  - Titkosítási kulcsok

## <a name="aggregated-data"></a>Összesített adatértékek

Az összesített adatokat az Intune szolgáltatás kiépítésére és fejlesztésére használjuk. 

Az Intune által gyűjtött összesített adatok tartalmazhatnak, de nem korlátozódnak a következőkre: 

- Rendszergazdai használati adatok az összes Intune-bérlőről (például a Felügyeleti konzollal való interakciókor kiválasztott rendszergazdai vezérlők)
- Bérlői fiók adatai (ezek az adatok az Intune panelen érhetők el)
  - A regisztrált eszközök vagy felhasználók száma
  - Azonosított eszköz platformok száma  
  - Telepített eszközök száma
  - installedDeviceCount: azon eszközök száma, amelyeken az alkalmazás telepítve van.
  - notApplicableDeviceCount: azon eszközök száma, amelyekhez az alkalmazás nem alkalmazható.
  - notInstalledDeviceCount: azon eszközök száma, amelyekhez az alkalmazás alkalmazható, de nincs telepítve.
  - pendingInstallDeviceCount: azon eszközök száma, amelyeken az alkalmazás alkalmazható, és a telepítés függőben van.

## <a name="next-steps"></a>Következő lépések

Tudjon meg többet [arról, hogy](privacy-data-secure-share.md) az Intune hogyan [tárolja és dolgozza](privacy-data-store-process.md) fel a személyes adatait. 
