---
title: Adatgyűjtés az Intune-ban
description: Tájékoztató a személyes adatok Intune-beli gyűjtéséről.
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
ms.openlocfilehash: 08066c0742ad4ad02f907e55cc84eb65068c9b99
ms.sourcegitcommit: c9725ddae6c0f82a491de27c87f240254d32716b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70986422"
---
# <a name="data-collection-in-intune"></a>Adatgyűjtés az Intune-ban

Ha a felhasználók vállalati vagy személyes eszközeiket az Intune-ban regisztrálják, az Intune személyes adatokat is gyűjt és megoszt. Az Intune az alábbi forrásokból származó személyes adatokat gyűjti:

- A rendszergazda Intune-használata az Azure Portalon.
- Végfelhasználói eszközök (amikor Intune-felügyeletre regisztrálnak, valamint használat közben).
- Ügyfélfiókok és harmadik féltől származó szolgáltatások (a rendszergazda utasítása alapján).
- Diagnosztikai, teljesítménybeli és használati információk.

Az Intune ezekből a forrásokból az alábbi három kategóriába tartozó adatokat gyűjti: [azonosított](#identified-data), [álnevesített](#pseudonymized-data) és [összesített](#aggregated-data).

> [!NOTE]
> A szolgáltatás által gyűjtött adatokat semmilyen okból nem adjuk át harmadik félnek.

## <a name="identified-data"></a>Azonosított adatok

Az Intune által gyűjtött személyes adat többsége azonosított adat. Az ilyen adatok egy felhasználóhoz, eszközhöz vagy alkalmazáshoz köthetőek, és elengedhetetlenek a felügyelethez. Az azonosított adatokat a felhasználó eszközének és alkalmazásainak felügyeletéhez, valamint az Intune szolgáltatás kiépítéséhez használjuk.

Az Intune által gyűjtött azonosított adatok többek között az alábbiak lehetnek: 

- Felhasználói adatok
  - A tulajdonos neve vagy a felhasználó (a felhasználó Azure-ban regisztrált, az AzureUserId által azonosított neve)
  - Egyszerű felhasználónév vagy e-mail-cím
  - Külső felhasználói azonosítók (például AppleId)
- A hardverleltár információi
  - Eszköz neve
  - Gyártó
  - Operációs rendszer
  - Sorozatszám
  - IMEI-szám
  - IP-cím
  - Wi-Fi Mac-címe
  - ICCID
  - Telefonszám
- Az auditnapló adatai, többek között az alábbi tevékenységekhez kapcsolódó adatok
  - A számítógépeken futó
  - Hozzon létre
  - Frissítés (szerkesztés)
  - Törlés
  - Hozzárendelés
  - Távoli feladatok
- Támogatási információk
  - Kapcsolattartási adatok (név, telefonszám, e-mail-cím)
  - E-mail-beszélgetések a Microsoft-támogatással és a termék- és/vagy az ügyfélélményt kezelő munkatársakkal
- Hozzáférés-vezérlési adatok (az Intune ezeket az adatokat arra használja, hogy a felügyeleti szerepkörökhöz és funkciókhoz való hozzáférést kezelje például a [Szerepköralapú hozzáférés-vezérlés](role-based-access-control.md) funkcióval.
  - Statikus hitelesítők (az ügyfél jelszava)
  - Adatvédelmi kulcsok tanúsítványokhoz 
- Adminisztrátori és fiókinformációk
  - A rendszergazdai felhasználó utóneve és vezetékneve
  - A rendszergazdai felhasználó neve
  - Egyszerű felhasználónév (e-mail)
  - Telefonszám
  - A fiók tulajdonosának e-mail-címe
  - Minden ügyfél-rendszergazda Active Directory-azonosítója
  - Ügyfélszámlázási fizetési adatok
  - Előfizetői kulcs
- Alkalmazásleltár, például
  - alkalmazásnév
  - verzió
  - alkalmazásazonosító
  - méret
  - telepítés helye
  - Az alkalmazás leltáradatait csak akkor gyűjti a rendszer, ha a rendszergazda az eszközt vállalati tulajdonúnak jelölte meg, vagy ha be van kapcsolva a megfelelő alkalmazás funkció.  
- Az ügyfél harmadik féltől származó bérlőazonosítója, például Apple ID. 

## <a name="pseudonymized-data"></a>Álnevesített adatok

Az álnevesített adatok egy egyedi azonosítóhoz tartoznak, amely általában a rendszer által generált szám, és amely önmagában nem alkalmas egyének azonosítására, de amelynek használatával a cég szolgáltatásokat nyújthat a felhasználóknak. 

Az Intune által gyűjtött álnevesített adatok többek között az alábbiak lehetnek: 

- Egy felhasználóhoz és/vagy egy eszközhöz kapcsolódó diagnosztikai, teljesítménybeli és használati adatok
  - A szám, mely azt jelzi, hányszor használtak egy funkciót
  - A funkcióhoz érkező parancsok
  - Egy szolgáltatás válaszideje
  - Telepítések és más folyamatok sikerességi rátája
  - Az Intune vállalati portálon előforduló alkalmazáshibák
  - Felhasználók és eszközök azonosítói
  - Hivatkozási, korrelációs és felügyeleti célokból gyűjtött azonosítók 
- Eszközhöz vagy felhasználóhoz nem köthető eszközadatok (ha az ilyen adat eszközhöz vagy felhasználóhoz köthető, akkor azt az Intune azonosított adatként kezeli)
  - Intune-eszközazonosító
  - Azure Active Directory-eszközazonosító
  - Az Intune eszközfelügyeleti azonosítója
  - Bérlőazonosító
  - Fiókazonosító
  - EAS-eszközazonosító
  - Platformspecifikus azonosítók
  - AppleID iOS-eszközök esetén
  - MAC-címek Mac-eszközök esetén
  - Windows-azonosító Windows-eszközök esetén
- Felügyelt alkalmazás adatai
  - Felügyelt alkalmazás azonosítója
  - Felügyelt alkalmazás eszközcímkéje
  - Az Intune eszközfelügyeleti azonosítója
  - Azure Active Directory-eszközazonosító
  - Titkosítási kulcsok

## <a name="aggregated-data"></a>Összesített adatok

Az összesített adatokat az Intune szolgáltatás kiépítéséhez és fejlesztéséhez használjuk fel. 

Az Intune által gyűjtött összesített adatok többek között az alábbiak lehetnek: 

- Rendszergazdai használati adatok az összes Intune-bérlőből (például a felügyeleti konzol használata közben kiválasztott felügyeleti vezérlők)
- Bérlői fiókok adatai (ez az adat az Intune-panelről érhető el)
  - A regisztrált eszközök vagy felhasználók száma
  - Azonosított eszközplatformok száma  
  - A telepített eszközök száma
  - installedDeviceCount: Azon eszközök száma, amelyeken az alkalmazás telepítve van.
  - notApplicableDeviceCount: Azon eszközök száma, amelyekhez az alkalmazás nem alkalmazható.
  - notInstalledDeviceCount: Azon eszközök száma, amelyekhez az alkalmazás alkalmazható, de nincs telepítve.
  - pendingInstallDeviceCount: Azon eszközök száma, amelyeken az alkalmazás alkalmazható, és a telepítés függőben van.

## <a name="next-steps"></a>További lépések

További információ arról, ahogyan az Intune [tárolja, feldolgozza](privacy-data-store-process.md) és [megosztja](privacy-data-secure-share.md) a személyes adatokat. 
