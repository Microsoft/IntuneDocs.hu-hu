---
title: Az Exchange-összekötő hibaelhárítása
titleSuffix: Microsoft Intune
description: A helyszíni Intune Exchange Connectorral kapcsolatos problémák elhárítása.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 962e66a9fdf6d8abcf6855f645775026ee4db850
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508839"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Az Intune Exchange Connector hibáinak megoldása

Ez a cikk az Intune Exchange Connectorral kapcsolatos problémák elhárítását ismerteti.

## <a name="before-you-start"></a>Előkészületek

Mielőtt elkezdené az Exchange Connector hibáinak elhárítását az Intune-ban, gyűjtsön össze néhány alapvető információt, hogy szilárd alapokon dolgozzon. Ez a megközelítés segít jobban megérteni a probléma természetét, és gyorsabban megoldani.

- Ellenőrizze, hogy a folyamat megfelel-e a telepítési követelményeknek. Lásd: a helyszíni [Intune Exchange Connector beállítása](exchange-connector-install.md).
- Győződjön meg arról, hogy a fiókja Exchange-és Intune-rendszergazdai jogosultságokkal is rendelkezik.
- Jegyezze fel a teljes és pontos hibaüzenet szövegét, részleteit, valamint az üzenet megjelenítésének helyét.
- A probléma elindításának megállapítása: 
  - Az összekötőt első alkalommal állítja be? 
  - Az összekötő megfelelően működik, és nem sikerül?
  - Ha működik, milyen változások történtek az Intune-környezetben, az Exchange-környezetben vagy az összekötő szoftvert futtató számítógépen?
- Mi a MDM-szolgáltató? Ha System Center Configuration Manager, a Configuration Manager melyik verzióját használja?
- Milyen verziójú Exchange-verziót használ?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>További információ az Exchange Connectorral kapcsolatos problémákról a PowerShell használatával

- Egy postaládához tartozó összes mobileszköz listájának lekéréséhez használja a `Get-ActiveSyncDeviceStatistics -mailbox mbx` értéket.
- A postaláda SMTP-címeinek listájának lekéréséhez használja a következőt: `Get-Mailbox -Identity user | select emailaddresses | fl`
- Az eszköz hozzáférési állapotával kapcsolatos részletes információkért használja `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>Az összekötő konfigurációjának áttekintése

Tekintse át a helyszíni [Exchange Connector követelményeit](exchange-connector-install.md#intune-exchange-connector-requirements) , és győződjön meg arról, hogy a környezet és az összekötő megfelelően van konfigurálva. 

### <a name="general-considerations-for-the-connector"></a>Az összekötő általános szempontjai

- Győződjön meg arról, hogy a tűzfal és a proxykiszolgáló engedélyezi a kommunikációt az Intune Exchange Connectort és az Intune szolgáltatást futtató kiszolgáló között.

- Az Intune Exchange Connectort és az Exchange ügyfél-hozzáférési kiszolgálót (CAS) futtató számítógépnek tartományhoz kell csatlakoznia, és ugyanazon a helyi hálózaton kell lennie. Győződjön meg arról, hogy a szükséges engedélyek hozzá lettek adva az Intune Exchange Connector által használt fiókhoz.

- Az értesítési fiók az *automatikus észlelési* beállítások beolvasására szolgál. Az Exchange Autodisover kapcsolatos további információkért lásd: [az automatikus észlelési szolgáltatás az Exchange Serveren](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016).

- Az Intune Exchange Connector egy kérést küld a EWS URL-címére az értesítési fiók hitelesítő adataival az értesítő e-mailek küldéséhez, valamint az *első lépések* hivatkozásra (az Intune-ban való regisztráláshoz). Az első *lépések* hivatkozásra kattintva regisztrálhatja az Android nem Knox rendszerű eszközökre vonatkozó követelményt. Ellenkező esetben a feltételes hozzáférés letiltja ezeket az eszközöket.

### <a name="common-issues-for-connector-configurations"></a>Összekötő-konfigurációk gyakori problémái

- **Fiók engedélyei**: a Microsoft Intune Exchange Connector párbeszédpanelen ellenőrizze, hogy van-e olyan felhasználói fiók, amely rendelkezik a megfelelő engedélyekkel a [szükséges Windows PowerShell Exchange-parancsmagok](exchange-connector-install.md#exchange-cmdlet-requirements)végrehajtásához.
- **Értesítő e-mail üzenetek**: értesítések engedélyezése és értesítési fiók megadására.
- **Ügyfél-hozzáférési kiszolgáló szinkronizálása**: az Exchange-összekötő konfigurálásakor olyan hitelesítésszolgáltatókat adhat meg, amelyek az Exchange Connectort futtató kiszolgáló számára a legkisebb hálózati késéssel rendelkeznek. A CAS és az Exchange Connector közötti kommunikációs késés késleltetheti az eszközök felderítését, különösen ha dedikált Exchange Online-t használ.
- **Szinkronizálási ütemezés**: az újonnan beléptetett eszközzel rendelkező felhasználók csak akkor férhetnek hozzá a hozzáféréshez, ha az Exchange Connector szinkronizálva lett az Exchange-hitelesítésszolgáltatókkal. Teljes szinkronizálás naponta egyszer, az eltérések (gyors) szinkronizálása pedig naponta többször történik. A késés minimalizálása érdekében [manuálisan is kikényszeríthet gyors vagy teljes szinkronizálást](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync).

## <a name="next-steps"></a>További lépések
A következő cikkek segíthetnek a gyakori problémák és a konkrét hibák megoldásában:

- [Az Intune Exchange Connector gyakori problémáinak elhárítása](troubleshoot-exchange-connector-common-problems.md).
- [Az Intune Exchange Connector gyakori hibáinak elhárítása](troubleshoot-exchange-connector-common-errors.md).

Kérjen segítséget a támogatási szolgálattól vagy az Intune-Közösségtől:

- A probléma megoldásához, illetve a Microsoft támogatási esetének megnyitásához tekintse meg a [támogatás kérése](../fundamentals/get-support.md) az Intune-konzollal való használatát ismertető témakört. 
- A probléma közzététele a [Microsoft Intune fórumokon](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
