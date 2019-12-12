---
title: Klasszikus Intune-csoportok az Azure Portalon
titleSuffix: Microsoft Intune
description: A Microsoft Intune Azure Portal csoportokkal kapcsolatos újdonságainak ismertetése.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/31/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0cf8e136b3ef5c3d4329e075af4c180423d74a15
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502849"
---
# <a name="microsoft-intune-classic-groups-in-the-azure-portal"></a>Klasszikus Microsoft Intune-csoportok az Azure Portalon

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A visszajelzések alapján módosításokat vezetünk be a Microsoft Intune-beli csoportok használatában.
Az Azure Portalról használt Intune esetén az Intune-csoportok migrálva lettek az Azure Active Directory biztonsági csoportjaiba.

Ez azért hasznos, mert így a csoportfelügyeleti környezet egységes a teljes Enterprise Mobility + Security csomagban, valamint az Azure AD-alkalmazásokban. Ezen kívül az új funkció kiterjesztéséhez és testre szabásához a PowerShell és a Graph API is használható.

Az Azure AD-alapú biztonsági csoportok az Intune minden telepítéstípusát támogatják mind a felhasználókat, mind az eszközöket tekintve. Használhatók továbbá az Azure AD-alapú dinamikus csoportok, amelyek az Ön által megadott attribútumok alapján automatikusan frissülnek. Például létrehozhat egy csoportot, amely az összes iOS 9 rendszerű eszközt tartalmazza. Az iOS 9-es eszközök regisztrálás után automatikusan megjelennek a dinamikus csoportban.

## <a name="what-is-not-available"></a>Mi az, ami nem érhető el?

Előfordulhat, hogy a korábbi Intune-csoportok funkcióinak némelyike nem érhető el az Azure AD-ben:

- A **Nem csoportosított felhasználók** és a **Nem csoportosított eszközök** Intune-csoportjai már nem érhetők el.
- A **Meghatározott tagok kizárása** a csoportból funkció az Azure Portalon nem érhető el, megoldható azonban az Azure AD-alapú biztonsági csoportok speciális szabályaival. Létrehozhat például egy olyan speciális szabályt, amely egyetlen biztonsági csoportba foglalja a Sales nevű részleg minden munkatársát, kivéve azokat, akiknek a beosztásában szerepel az „Assistant” szó. Ezt a következő szabállyal érheti el:

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- A klasszikus Intune-konzolon elérhető **Minden Exchange ActiveSync által kezelt eszköz** csoport nem lett migrálva az Azure AD-be, az EAS által kezelt eszközök információit azonban továbbra is elérheti az Azure Portalról.

## <a name="how-to-get-started"></a>Első lépések

- Az alábbi Azure AD-vel kapcsolatos cikkek segítenek tájékozódni az Azure AD-alapú biztonsági csoportokról és azok működéséről:
  - [Az erőforrásokhoz való hozzáférés kezelése Azure Active Directory-csoportokkal](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/).
  - [Csoportkezelés az Azure Active Directoryban](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).
  - [Attribútumok használata speciális szabályok létrehozására](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
- Fontos, hogy azok a rendszergazdák, akik csoportokat fognak létrehozni, hozzá legyenek adva az **Intune-szolgáltatásadminisztrátor** Azure AD-szerepkörhöz. Az Azure AD szolgáltatásadminisztrátori szerepkörének nincs **Csoportok kezelése** engedélye.
- Ha Intune-csoportjai használták a **Meghatározott tagok kizárása** beállítást, akkor el kell döntenie, hogy át tudja-e alakítani ezeket a csoportokat úgy, hogy ne legyen bennük kizárás, vagy speciális szabályokra van szüksége a céges igények miatt.


## <a name="what-happened-to-intune-groups"></a>Mi történt az Intune-csoportokkal?
A csoportok az Azure Portalról az Azure Portalon lévő Intune-ba való migrálásakor a következő szabályok érvényesek:

| Csoportok az Intune-ban|Csoportok az Azure AD-ben|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Statikus felhasználói csoport|Statikus Azure AD biztonsági csoport|
|Dinamikus felhasználói csoport|Statikus Azure AD biztonsági csoportok Azure AD biztonságicsoport-hierarchiával|
|Statikus eszközcsoport|Statikus Azure AD biztonsági csoport|
|Dinamikus eszközcsoport|Dinamikus Azure AD biztonsági csoport|
|Belefoglalási feltételt tartalmazó csoport|Statikus Azure AD biztonsági csoport, amely tartalmazza az Intune-beli belefoglalási feltétel által érintett statikus/dinamikus tagokat|
|Kizárási feltételt tartalmazó csoport|Nem lesz áttelepítve|
|Beépített csoportok:<br>- **Minden felhasználó**<br>- **Nem csoportosított felhasználók**<br>- **Minden eszköz**<br>- **Nem csoportosított eszközök**<br>- **Minden számítógép**<br>- **Minden mobileszköz**<br>- **Minden MDM-mel felügyelt eszköz**<br>- **Minden EAS által felügyelt eszköz**|Azure AD biztonsági csoportok|

## <a name="group-hierarchy"></a>Csoporthierarchia

Az Intune-konzolon minden csoportnak volt szülőcsoportja, és a csoportok csak a szülőcsoport tagjait tartalmazhatták. Az Azure AD-ben a gyermekcsoportok a szülőcsoportjukon kívüli tagokat is tartalmazhatnak.

## <a name="group-attributes"></a>Csoportattribútumok
Az attribútumok a csoportok definiálása során felhasználható eszköztulajdonságok. Ez a táblázat bemutatja, hogyan fog történni ezeknek a feltételeknek az Azure AD-alapú biztonsági csoportokba való migrálása.

| Attribútum az Intune-ban|Attribútum az Azure AD-ben|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Eszközcsoportok szervezeti egység (OU) attribútuma|Dinamikus csoportok OU attribútuma.|
|Eszközcsoportok Tartománynév attribútuma|Dinamikus csoportok Tartománynév attribútuma.|
|Biztonsági csoport mint a felhasználócsoportok attribútuma|A csoportok nem lehetnek attribútumok az Azure AD dinamikus lekérdezéseiben. A dinamikus csoportok csak felhasználó- vagy eszközspecifikus attribútumokat tartalmazhatnak.|
|A felhasználócsoportok Manager (Kezelő) attribútuma|A *manager* (kezelő) attribútumra vonatkozó speciális szabály dinamikus csoportokban|
|A szülő felhasználócsoport minden felhasználója|Statikus csoport, amelynek ez a csoport a tagja|
|A szülő eszközcsoport minden mobileszköze|Statikus csoport, amelynek ez a csoport a tagja|
|Az Intune által kezelt összes mobileszköz|Egy dinamikus csoport Management Type (Kezelés típusa) attribútumának „MDM” értéke|
|Statikus csoportokba ágyazott csoportok |Statikus csoportokba ágyazott csoportok|
|Dinamikus csoportokba ágyazott csoportok|Egy beágyazott szintet tartalmazó dinamikus csoport|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>Mi történik a korábban telepített szabályzatokkal és alkalmazásokkal?

A szabályzatokat és az alkalmazásokat továbbra is telepíteni lehet a csoportokba. Ezeket a csoportokat azonban az Intune-konzol helyett az Azure Portalon lehet kezelni.
