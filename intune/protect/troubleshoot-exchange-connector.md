---
title: Az Exchange-összekötő hibaelhárítása
titleSuffix: Microsoft Intune
description: A helyszíni Intune Exchange Connectorral kapcsolatos problémák elhárítása.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 217241ab4cead7f1087fe5bf6128cbf3dadb6ee2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729431"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>A helyszíni Intune Exchange Connector hibaelhárítása

Ez a cikk a helyszíni Intune Exchange Connectorral kapcsolatos problémák elhárítását ismerteti.

## <a name="steps-for-checking-the-connector-configuration"></a>Lépések a Connector konfigurációjának ellenőrzéséhez 

A [Helyszíni Intune Exchange Connector beállítása](exchange-connector-install.md) című cikk alapján győződjön meg róla, hogy az összekötő helyesen van konfigurálva. Az alábbiakban néhány gyakori problémát sorolunk fel. A javítások után ellenőrizze, hogy a probléma megoldódott-e.

- Ellenőrizze, hogy a Microsoft Intune Exchange Connector párbeszédablakban megadott felhasználói fiók megfelelő engedélyekkel rendelkezik-e a [szükséges Windows PowerShell Exchange parancsmagok](exchange-connector-install.md#exchange-cmdlet-requirements) végrehajtásához.
- Engedélyezze az értesítéseket, és adjon meg egy értesítési fiókot.
- Az Exchange Connector konfigurálásakor olyan ügyfélelérési kiszolgálót (CAS-t) adjon meg, amely a lehető legközelebb van az Exchange Connectort futtató kiszolgálóhoz. A CAS és az Exchange Connector közötti kommunikációs késés késleltetheti az eszköz észlelését, különösen az Exchange Online dedikált verziójának használatakor.
- Az újonnan regisztrált eszközök felhasználói esetleg csak akkor jutnak hozzáféréshez, amikor az Exchange Connector szinkronizál az Exchange CAS-szel. Teljes szinkronizálás naponta egyszer, az eltérések (gyors) szinkronizálása pedig naponta többször történik.  A késés minimalizálása érdekében [manuálisan is kikényszeríthet gyors vagy teljes szinkronizálást](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync).
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Az Exchange ActiveSync-eszköz nem deríthető fel az Exchange-ből
[Az Exchange Connector tevékenységének figyelésével](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support) ellenőrizze, hogy az Exchange Connector szinkronizál-e az Exchange-kiszolgálóval. Ha az eszköz csatlakozása óta sikeresen lezajlott egy teljes vagy gyors szinkronizálás, akkor megvizsgálhatja a további, alább felsorolt hibalehetőségeket. Ha nem került sor a szinkronizálásra, gyűjtse össze a szinkronizálási naplókat, és csatolja őket egy támogatási kérelemhez.

- Ellenőrizze, hogy a felhasználók rendelkeznek-e Intune-licenccel, ellenkező esetben az Exchange Connector nem észleli az eszközeit.
- Ha egy felhasználó elsődleges SMTP-címe különbözik az Azure Active Directoryban (Azure AD) szereplő egyszerű felhasználónevétől, az Exchange Connector nem észleli az adott felhasználó eszközeit. A probléma megoldásához javítsa ki az elsődleges SMTP-címet.
- Ha környezetében Exchange 2010 és Exchange 2013 postaláda-kiszolgálói is vannak, akkor ajánlott az Exchange Connectort egy Exchange 2013 CAS-re irányítani. Ellenkező esetben, ha az Exchange Connector az Exchange 2010 CAS-szel való kommunikációra van beállítva, az Exchange Connector nem fogja észlelni az Exchange 2013 felhasználóinak eszközeit. 
- Az Exchange Online dedikált verzióján alapuló környezetben a kezdeti beállítás során az Exchange Connectornak egy Exchange 2013-as (és nem Exchange 2010-es) CAS felé kell mutatnia, ugyanis a Connector csak ezzel a CAS-szel kommunikál a PowerShell-parancsmagok végrehajtásakor.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>További adatok gyűjtése az Exchange Connectorral kapcsolatos problémákról a PowerShell segítségével
- Egy postaládához tartozó összes mobileszköz listájának lekéréséhez használja a `Get-ActiveSyncDeviceStatistics -mailbox mbx` értéket.
- A postaláda SMTP-címeinek listájának lekéréséhez használja a következőt: `Get-Mailbox -Identity user | select emailaddresses | fl`
- Az eszköz hozzáférési állapotával kapcsolatos részletes információkért használja `Get-CASMailbox <upn> | fl`

## <a name="next-steps"></a>További lépések
Ha ezek az információk nem segítettek, akkor [Támogatást kérhet a Microsoft Intune-hoz](../fundamentals/get-support.md).
