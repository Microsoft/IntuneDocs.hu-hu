---
title: Személyes adatelemzés, exportálás vagy törlés
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan naplózhatja, exportálhatja vagy törölheti a személyes információkat.
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
ms.openlocfilehash: 74428abf8141c648b5b81bba3177cc89a3cb01d2
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306817"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Személyes adattárolás naplózása, exportálása vagy törlése az Intune-ban

Az Intune-rendszergazdák naplókat használhatnak a személyes adatkezelési tevékenységek nyomon követéséhez. A rendszergazdák is exportálhatók és törölhetik a személyes adatfájlokat.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Személyes adattárolás naplózása

A naplók a bérlői rendszergazdák számára a Microsoft Intune módosítását előidéző tevékenységek rekordjait biztosítják. A naplók számos kezelési tevékenységhez érhetők el, és általában a létrehozás, a frissítés (Szerkesztés), a törlés és a hozzárendelés művelet. A naplózási eseményeket létrehozó távoli feladatok is megtekinthetők. Ezek a naplók olyan felhasználók személyes adatait is tartalmazhatják, akiknek az eszközei regisztrálva vannak az Intune-ban.  

Biztonsági okokból az Intune egy évig megtarthatja a felhasználók és eszközök műveleteinek naplóit. Ezeket a naplókat a rendszer automatikusan törli az egy évig tartó megőrzési időszak után.

A naplók áttekintéséhez tekintse meg [az Intune-tevékenységek naplózása](../fundamentals/monitor-audit-logs.md)című témakört. 

A rendszergazdák nem törölhetik a naplókat.

Ezeket a naplózási eseményeket egy évig őrzi meg a rendszer. A bérlői rendszergazdák [a támogatási kérelem űrlapján](https://privacy.microsoft.com/en-US/privacy-questions?)keresztül kérhetik a naplókat.

## <a name="export-personal-data"></a>Személyes adatexportálás

A rendszergazdák a felhasználók személyes adataikat, köztük a fiókokat, a szolgáltatási és a kapcsolódó naplókat is exportálhatunk, hogy megfeleljenek az adattulajdonosi jogosultsági kérelmeknek. Ön és a szervezete eldönti, hogy az adattulajdonost a személyes adatai másolatával látja-e el, vagy ha jogos üzleti oka van annak visszatartására. Ha úgy dönt, hogy megadja ezt a lehetőséget, megadhatja a tényleges dokumentum másolatával, a megfelelő módon lefedett verzióval vagy a megosztásnak megfelelőnek tartott részek képernyőképével.

A felhasználók személyes adatfájljainak exportálásához a következőket használhatja: 
- az Intune MDM-eszköz panel az eszközök listájának exportálásához. Az eszközökre vonatkozó Adatmásolást közvetlenül is elvégezheti.
- a [export-IntuneData. ps1 parancsfájl](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>A végfelhasználói személyes adatértékek törlése

A személyes adatok az Intune-felügyeletből való eltávolításának három módja van:
- A felhasználó törlése Azure Active Directory
- Eszköz visszaállítása a gyári beállításokra
- Felhasználó saját eltávolítása

### <a name="delete-a-user-from-intune"></a>Felhasználó törlése az Intune-ból

A végfelhasználók Intune-ból származó személyes adatainak törléséhez a rendszergazdának [törölnie kell a felhasználót Azure Active Directoryról (HRE)](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user). Ha a felhasználó törölve lett a HRE-ből (rögzítetten törölve), az Intune fogadja a törlési jelet a HRE, majd automatikusan megkezdi a felhasználó személyes adatainak az Intune szolgáltatásból való végleges törlését. A felhasználó adatait az eltávolítási művelettől számított 30 napon belül törölni fogjuk az Intune szolgáltatásból.

### <a name="reset-device-to-factory-settings"></a>Eszköz visszaállítása a gyári beállításokra
A gyári beállítások visszaállítása visszaállítja az összes vállalati és személyes értéket és beállítást az eredeti gyári beállításokra. Az eszköz a következő alkalmazott számára való biztosításához hasznos. A felhasználói fájlok, a felhasználó által telepített alkalmazások és a nem alapértelmezett beállítások törlődnek, és ezek az adatok törlődnek az Intune szolgáltatásból az eltávolítási művelettől számított 30 napon belül.

### <a name="user-self-removal-from-intune-management"></a>Felhasználói önálló eltávolítás az Intune-felügyeletből
A felhasználók a rendszergazdai segítség nélkül eltávolíthatják [Android-, Apple-vagy Windows-alapú](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) személyes eszközét az Intune-felügyeletből.   

### <a name="retire"></a>Nyugdíjba
A kivonási művelet eltávolítja az Intune által kiépített, például a vállalati alkalmazásokat, az Intune által felügyelt alkalmazásokkal kapcsolatos információkat **, a házirend** -beállításokat és az Intune-nal üzembe helyezendő e-mail-profilokat. Ez a művelet elhagyja a felhasználó személyes adategységét az eszközön.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Bérlő törlése Microsoft Intune

Ha az Intune-bérlői ügyfél megszakítja az Intune-fiókját, az ügyfél az Intune-fiók bezárása után 180 napon belül törli az összes bérlői adatmódosítást. Ha a HRE-bérlő más Microsoft nagyvállalati előfizetésekhez (Azure, Office 365) van társítva, akkor csak az Intune-ügyfél adatait törli a rendszer. A HRE-bérlői erőforrást a többi előfizetés is használja. Ha az Intune-fiók a HRE-bérlőhöz társított egyetlen előfizetés, akkor a bérlő törlődik, és az összes erőforrás és ügyfél adatai is törlődnek.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Felhasználó törlése hibrid mobileszköz-kezelési (MDM) környezetben
Ha hibrid MDM-környezettel (Configuration Manager) integrált Intune-nal rendelkezik, a következő műveleteket kell végrehajtania (sorrendben) a felhasználó teljes törléséhez, és a helyi Active Directory, a Configuration Manager és az Intune teljes eltávolításához.

1. Törölje a felhasználót a helyi Active Directoryból (AD). Ezzel leállítja a felhasználót, hogy szinkronizálja az Azure AD-t, és a Configuration Manager felderítése is felderíti. 
2. Törölje a felhasználót a Configuration Manager-konzolról, és távolítsa el a felhasználót és a kapcsolódó adatait a Configuration Managerból. A konzolon válassza az **eszközök és megfelelőség** > **felhasználók**lehetőséget, kattintson a jobb gombbal a törölni kívánt felhasználóra, majd kattintson a **Törlés**parancsra.
3. [Törölje a felhasználót a HRE-ből](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user), amely egyszerre eltávolítja a felhasználót és a hozzá tartozó Azure Active Directory és Intune-beli adatait. Ha a felhasználó törölve lett a HRE-ből (rögzítetten törölve), az Intune fogadja a törlési jelet a HRE, majd automatikusan megkezdi a felhasználó személyes adatainak az Intune szolgáltatásból való végleges törlését. A felhasználó adatait az eltávolítási művelettől számított 30 napon belül törölni fogjuk az Intune szolgáltatásból.

> [!Important]
>Az új hibrid MDM-ügyfelek bevezetése elavult. További információ: [áttérés hibrid mobileszköz-kezelésről az Intune-ra az Azure-](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) blogbejegyzésben.

## <a name="next-steps"></a>Következő lépések

Megtudhatja [, hogyan naplózhatja, exportálhatja vagy törölheti](privacy-data-audit-export-delete.md) a személyes adatvédelmet az Intune-ban.
