---
title: Személyes adatok naplózása, exportálása vagy törlése
description: Ismertető személyes adatok naplózásáról, exportálásáról vagy törléséről.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fb30e8e07d71b72e337a8c2b27b3ed751c9d03e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729543"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Személyes adatok naplózása, exportálása vagy törlése az Intune-ban

Az Intune-rendszergazdák auditnaplók használatával követhetik nyomon a személyes adatokkal kapcsolatos tevékenységeket. A rendszergazdák exportálhatják és törölhetik is a személyes adatokat.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Személyes adatok naplózása

Az auditnaplókban a Microsoft Intune-ban változást előidéző tevékenységek jegyzékét érhetik el a bérlői rendszergazdák. Auditnaplók sokféle kezelési művelethez elérhetők, jellemzően a létrehozási, frissítési (szerkesztési), törlési és hozzárendelési műveletekhez. A naplózási eseményeket generáló távoli feladatok is áttekinthetők. Az ilyen auditnaplók személyes adatokat is tartalmazhatnak az Intune-ban regisztrált eszközzel rendelkező felhasználókról.  

Az Intune biztonsági okokból egy éven át megőrizheti a felhasználói és eszköztevékenységek auditnaplóit. Az egyéves megőrzési időtartam végén ezek a naplók automatikusan törölve lesznek.

Az auditnaplókkal kapcsolatban lásd: [Auditnaplók Intune-tevékenységekhez](../fundamentals/monitor-audit-logs.md). 

A rendszergazdák nem törölhetik az auditnaplókat.

Ezek a naplózási események egy évig lesznek megőrizve. A bérlői rendszergazdák [ezzel a támogatáskérő űrlappal](https://privacy.microsoft.com/en-US/privacy-questions?) kérhetik ki az auditnaplókat.

## <a name="export-personal-data"></a>Személyes adatok exportálása

A rendszergazdák az Adattulajdonosi jogokra vonatkozó (DSR-) kérelmek teljesítéséhez exportálni tudják a végfelhasználók személyes adatait, köztük a fiók és a szolgáltatások adatait, valamint az azokhoz tartozó naplókat. Önnek és vállalatának kell meghatároznia, hogy kiadja-e az adattulajdonosnak a személyes adatok másolatát, vagy jogszerű üzleti indoka van azok visszatartására. Ha az adatok kiadása mellett dönt, akkor azokat átadhatja a tényleges dokumentum másolataként, egy megfelelően kivonatolt változatban vagy az Ön által megoszthatónak ítélt részleteket ábrázoló képernyőkép formájában.

A felhasználók személyes adatai a következők használatával exportálható: 
- az Intune Mobileszköz-kezelés paneljén, ahol eszközlista exportálható. Az eszközök adatai közvetlenül is másolhatók.
- az [Export-IntuneData.ps1 szkript](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>Végfelhasználók személyes adatainak törlése

Az Intune felügyelete alól három módon távolíthatók el személyes adatok:
- A felhasználó törlése az Azure Active Directoryból
- Az eszköz gyári beállításainak visszaállítása
- A felhasználó eltávolítja önmagát

### <a name="delete-a-user-from-intune"></a>Felhasználó törlése az Intune-ból

A rendszergazdák úgy törölhetik egy végfelhasználó személyes adatait az Intune-ból, hogy [törlik a felhasználót az Azure Active Directoryból (AAD)](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user). Amikor egy felhasználót törölnek az AAD-ból (végleges törléssel), az Intune jelzést kap a törlésről az AAD-tól és automatikusan elkezdi törölni az adott felhasználó összes személyes adatát az Intune szolgáltatásból. A felhasználó adatai az eltávolítási műveletet követő 30 napon belül törölve lesznek az Intune szolgáltatásból.

### <a name="reset-device-to-factory-settings"></a>Eszköz gyári beállításainak visszaállítása
A gyári beállítások visszaállítása minden vállalati és személyes adatot és beállítást visszaállít az eredeti gyári beállításokra. Így adható át az eszköz egy másik alkalmazottnak. A felhasználó fájljai, az általa telepített alkalmazások és az összes nem alapértelmezett beállítás el lesz távolítva, és ezek az adatok az eltávolítási műveletet követő 30 napon belül törölve lesznek az Intune szolgáltatásból.

### <a name="user-self-removal-from-intune-management"></a>A felhasználó eltávolítja önmagát az Intune-felügyelet alól
A felhasználók rendszergazdai közreműködés nélkül is eltávolíthatják saját [Android, Apple vagy Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) rendszerű eszközeiket az Intune-felügyelet alól.   

### <a name="retire"></a>Kivonás
A **Kivonás** művelet eltávolítja az olyan, Intune által szolgáltatott adatokat, mint a vállalati alkalmazások, az Intune által felügyelt alkalmazásokkal kapcsolatos adatok, a szabályzatok beállításai és az Intune-on keresztül kapott e-mail-profilok. Ez a művelet meghagyja az eszközön a felhasználó személyes adatait.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Bérlő törlése a Microsoft Intune-ból

Ha egy Intune-bérlőbeli ügyfél lemondja Intune-fiókját, akkor minden bérlői adat törölve lesz az Intune-fiók ügyfél általi lezárását követő 180 napon belül. Ha az AAD-bérlő más Microsoft nagyvállalati előfizetésekhez is társítva van (Azure, Office 365), akkor csak az Intune-ügyfél adatai lesznek törölve. Az AAD-bérlői erőforrás megmarad, hogy a többi előfizetés használhassa. Ha az Intune-fiók az AAD-bérlőhöz rendelt egyetlen előfizetés, akkor a bérlő törölve lesz, valamint törölve lesz minden erőforrás és az ügyfél összes adata is.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Felhasználó törlése hibrid mobileszköz-felügyeleti (MDM) környezetben
Amennyiben hibrid MDM-környezettel rendelkezik (a Configuration Managerrel integrált Intune), a következő műveleteket kell végrehajtania (a megadott sorrendben), hogy egy felhasználót teljesen töröljön a helyszíni Active Directoryból, a Configuration Managerből, és az Intune-ból is.

1. Törölje a felhasználót a helyszíni Active Directoryból (AD). A felhasználó ez után nem lesz szinkronizálva az Azure AD-val, és a Configuration Manager sem fogja észlelni. 
2. A felhasználó és a hozzá tartozó adatok úgy törölhetők a Configuration Managerből, hogy törli a felhasználót a Configuration Manager konzolon. A konzolon nyissa meg az **Eszközök és megfelelőség** > **Felhasználók** elemet, kattintson a jobb gombbal a törölni kívánt felhasználóra, majd kattintson a **Törlés** lehetőségre.
3. [Törölje a felhasználót az AAD-ból](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user). Ezáltal a felhasználó és a hozzá tartozó adatok egyidejűleg törölve lesznek az Azure Active Directoryból és az Intune-ból is. Amikor egy felhasználót törölnek az AAD-ból (végleges törléssel), az Intune jelzést kap a törlésről az AAD-tól és automatikusan elkezdi törölni az adott felhasználó összes személyes adatát az Intune szolgáltatásból. A felhasználó adatai az eltávolítási műveletet követő 30 napon belül törölve lesznek az Intune szolgáltatásból.

> [!Important]
>Az új hibrid MDM-ügyfelek bevezetése elavult. További információ: [áttérés hibrid mobileszköz-kezelésről az Intune-ra az Azure-](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) blogbejegyzésben.

## <a name="next-steps"></a>További lépések

Ismertető személyes adatok Intune-beli [naplózásáról, exportálásáról vagy törléséről](privacy-data-audit-export-delete.md).
