---
title: A Microsoft Intune szolgáltatás leírása
description: A Microsoft Intune egy felhőalapú szolgáltatás, amellyel Windows, iOS, Mac OS X, Android és Windows Mobile rendszerű eszközök felügyelhetők.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 05/30/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5d65882c3811b05f7f8f137f76dc919e18f0da5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505324"
---
# <a name="microsoft-intune-service-description"></a>A Microsoft Intune szolgáltatás leírása

Az Intune egy felhőalapú nagyvállalati mobileszköz-felügyeleti (EMM) szolgáltatás, amely segítséget nyújt a munkatársak hatékonyságának fenntartásához a vállalati adatok védelmének megőrzése mellett. Az Intune-nal a következőkre nyílik lehetősége:
* Felügyelheti a munkatársak által a vállalati adatok elérésére használt mobileszközöket.
* Felügyelheti a munkatársak által használt ügyfélalkalmazásokat.
* Megóvhatja vállalati adatokat, szabályozva azt, ahogyan a munkatársak elérik és megosztják őket.
* Gondoskodhat arról, hogy az eszközök és az alkalmazások megfeleljenek a vállalat biztonsági követelményeinek.

Az Intune szorosan együttműködik az identitáskezelés és a hozzáférés-vezérlés terén az Azure Active Directoryval (Azure AD), valamint az adatvédelem terén az Azure Information Protectionnel. A felügyeleti lehetőségek bővítése céljából integrálhatja a System Center Configuration Managerrel is.

Ha szeretne továbbiakat megtudni arról, hogyan kezelheti az eszközöket, alkalmazásokat és védheti a céges adatokat az Intune-nal, olvassa el az [Intune dokumentációját](../index.yml).

## <a name="30-day-free-trial"></a>30 napos ingyenes próbaverzió
Az Intune használatát egy 30 napos ingyenes próbaverzióval kezdheti meg, amely 100 felhasználói licencet tartalmaz. Az ingyenes próbaverzió elindításához [látogasson el az Intune bejelentkezési oldalára](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20). Ha munkahelye vállalati szerződéssel vagy egy egyenértékű mennyiségi licencszerződéssel rendelkezik, az ingyenes próbaverzió beállítását bízza Microsoft-képviselőjére.

> [!NOTE]
> Ha munkahelyének van munkahelyi vagy iskolai Microsoft Online Services-fiókja, és előfordulhat, hogy a próbaidőszak leteltével élesben folytatja ennek az Intune-előfizetésnek a használatát, akkor az oldalon válassza a **Bejelentkezés** lehetőséget, és a hitelesítéshez használja a munkahelye globális rendszergazdai fiókját. Ez a művelet gondoskodik arról, hogy az Intune próbaverzió a meglévő munkahelyi vagy iskolai fiókhoz kapcsolódjon.

<!--- For a list of settings that you can set up on mobile devices, see:

- [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)

- [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](/sccm/mdm/understand/hybrid-mobile-device-management)

For more about System Center Configuration Manager, see [Documentation  for System Center Configuration Manager](/sccm/index).--->
## <a name="intune-onboarding-benefit"></a>Kedvezményes Intune-bevezetési támogatás
A Microsoft az Intune bevezetési értékelemet a jogosult csomagokban foglalt jogosult szolgáltatások esetében kínálja. Ez lehetővé teszi, hogy távoli segítséget kérjen a Microsoft szakértőitől az Intune-környezet üzembe helyezéséhez. A bevezetési értékelemmel kapcsolatos további információkért lásd: [A Microsoft Intune bevezetési értékelemének leírása](http://go.microsoft.com/fwlink/?LinkId=619281).


## <a name="learn-how-intune-service-updates-affect-you"></a>Az Intune szolgáltatásfrissítéseinek hatása a felhasználókra

Mivel a mobileszköz-kezelési ökoszisztéma az operációs rendszer frissítéseivel és a mobilalkalmazások kiadásával gyakran változik, a Microsoft az Intune-t gyakran frissíti. Az Intune szolgáltatás változásairól háromféle módon értesülhet:

- [Újdonságok a Microsoft Intune-ban](whats-new.md). Ezt a témakört a havi szolgáltatásfrissítésekkel frissítjük, de heti frissítések is előfordulhatnak, ha új alkalmazás (például a Céges Portál alkalmazás) jelenik meg.

- A fontos szolgáltatási frissítéseket a [Microsoft 365 felügyeleti központ](https://admin.microsoft.com/) üzenetközpont is bejelentette. Az [Office 365 felügyeleti társalkalmazás](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) telepítésével mobileszközén is fogadhatja az értesítéseket. További tudnivalók az [Office 365 üzenetközpontjában](https://support.office.com/client/results?Shownav=true&ns=O365ENTADMIN&version=15&ver=15&HelpID=O365E_MCManageUpdates) való munkavégzésről.

  Néhány hasznos tanács:

  - Az Office 365 üzenetközpontjában célzott üzenetek jelennek meg. Így ha például a cég nem használja az Intune oktatási ajánlatait, akkor nem küldünk üzenetet az Intune oktatási ajánlataival kapcsolatban.

  - Az üzenetek lejárati idővel rendelkeznek. Például egy szolgáltatásfrissítésről tájékoztató értesítés, amely az Újdonságok oldalra mutató hivatkozást is tartalmaz, valószínűleg még az előtt lejár, hogy megjelenne az újabb szolgáltatásfrissítési értesítés. Ellenkező esetben előfordulhatna, hogy nagy mennyiségű nem releváns üzenetek halmozódnak fel.

  - Az Office 365 felügyeleti mobilalkalmazással kereshet is az üzenetekben, és továbbíthatja is az üzeneteket, ha például másokkal is meg szeretné osztani azokat a szervezeten belül.

  - A jövőben tervezzük bevezetni azt a lehetőséget, hogy az Üzenetközpont beállításainak szerkesztése lehetőség alatt kijelölhesse az **Intune-t**, és így csak az Intune-előfizetéshez kapcsolódó üzenetek jelenjenek meg. Az Office 365 mobileszköz-kezelése más szolgáltatás, tehát nem az Intune-ra vonatkozik.

- Két blogban is közzétesszük az EMS-üzeneteket és az Intune-támogatás bevált módszereit:

  - [Enterprise Mobility + Security blog](https://blogs.technet.microsoft.com/enterprisemobility/)

  - [Intune-támogatási blog](https://blogs.technet.microsoft.com/intunesupport/)

> [!Note]
> Az Intune szolgáltatás állapotának figyelése a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com)végezhető el. Válassza a bal oldali panel **Szolgáltatás állapota** elemét. A szolgáltatás állapotát ezen kívül az [Office 365 felügyeleti mobilalkalmazás](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) használatával is ellenőrizheti.

## <a name="types-of-notices-microsoft-provides-about-the-intune-service"></a>A Microsoft Intune szolgáltatással kapcsolatos értesítések típusai

Hogy fel tudjon készülni a szolgáltatás változásaira, a szolgáltatásváltozást megelőzően legalább 7–90 nappal értesítjük, annak függvényében, hogy milyen hatású a változtatás. Ezek a változások a következő típusúak lehetnek:

- A végfelhasználói élményt érintő változások, amelyekről tanácsos értesíteni a segélyszolgálat munkatársait vagy a végfelhasználókat. Az ilyen típusú változásokról 7-30 nappal korábban teszünk közzé értesítést, és az [Újdonságok az Intune-alkalmazás felhasználói felületén](whats-new-app-ui.md) című témakörben is dokumentáljuk őket. A helyesírási hibákhoz hasonló kisebb javításokról általában nem teszünk közzé dokumentációt. Azonban a felhasználói felület olyan változása, amely a végfelhasználó regisztrálási folyamatát érinti, elég jelentős ahhoz, hogy erről egyrészt üzenetet küldjünk az ügyfeleknek az Office 365 üzenetközpontjában, másrészt az Újdonságok az Intune-alkalmazás felhasználói felületén témakörre mutató hivatkozást is közzétegyünk. Így a változásokról időben értesülhet ahhoz, hogy felülvizsgálja és módosítsa a végfelhasználói útmutatót, mielőtt a változások éles környezetben is hatályba lépnek.

- Az olyan változtatásokat, amelyek az Ön beavatkozását is szükségessé teszik, **tervezett változtatásoknak** nevezzük. Ezekről általában 30 nappal korábban küldünk értesítést. Az Office 365 üzenetközpontban az ilyen típusú változásoknál a Kategória minden esetben Tervezett változtatás. Ha már rendelkezünk információval arról, hogy pontosan mikor jelenik meg a változtatás éles környezetben, akkor közzétesszük a **Beavatkozás határideje** információt is, amely vizuális figyelemfelhívást és ikont is tartalmaz.

- Kivonások esetén a legtöbbször 90 nappal a kivonás előtt teszünk közzé értesítést. Ha például megszüntetjük a támogatást az IE valamely verziójához, arra törekszünk, hogy erről 90 nappal korábban értesítsünk Önt. A kivonások azonban nem mindig kezelhetők ilyen egyszerűen, ha azt egy más cég jelenti be. Egy böngészőt kínáló cég például bejelentette, hogy a böngészőjük legújabb buildje nem támogatja tovább a Silverlightot, ezért értesítettük az ügyfeleket, hogy megszüntetjük az illető böngésző támogatását, az értesítés azonban a változás előtt kevesebb mint 90 nappal történt.

- Az Intune szolgáltatás kivonása esetén 12 hónappal korábban értesítjük.

Végül abban a ritka esetben, ha az Ön esemény utáni beavatkozására van szükség a szolgáltatás helyreállításához, vagy ha olyan nagy horderejű változás történik, amelyet az ügyfélvisszajelzések alapján a működést jelentősen befolyásolónak minősítünk, e-mailben értesítjük a szolgáltatás rendszergazdáit attól függően, hogy hogyan állították be az [Office 365 kommunikációs beállításait](https://support.office.com/article/Change-your-contact-preferences-for-communications-from-Microsoft-6f70de1b-a64d-4498-bfbd-be8c83a9c0fc), és amennyiben meg van adva egy érvényes (lehetőleg munkahelyi) e-mail-cím.  


<!--- ## Choose the management solution that’s right for you
You can set up Intune in several ways to manage and help protect your company's mobile devices and computers (referred to as **devices** in this article).

- **Intune stand-alone configuration.** Use the web-based admin console in Intune to manage devices in your organization. Intune can be used without any on-premises IT infrastructure. If you use Intune with Active Directory Domain Services, you can use domain user accounts that you manage with Domain Services with Intune.

- **Intune with System Center Configuration Manager.** Use the Configuration Manager management console to manage computers and mobile devices in your enterprise. This configuration can help you to manage all your organization’s devices through a single console, the Configuration Manager Admin Console. Configuration Manager supports large numbers of mobile devices, servers, and computers. For more about Configuration Manager, see [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](/sccm/mdm/understand/hybrid-mobile-device-management). For more help deciding which approach is right for you, see [Choose between Microsoft Intune standalone and hybrid mobile device management with Configuration Manager](/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).--->

## <a name="language-support"></a>Nyelvi támogatás
Az Intune az Azure Portalon fut, amely a következő nyelveket támogatja: angol, cseh, francia, holland, japán, kínai (egyszerűsített), kínai (hagyományos), koreai, lengyel, magyar, német, olasz, orosz, portugál (brazíliai), portugál (portugáliai), spanyol, svéd, török.

Az Intune felügyeleti konzol és a felhasználói mobilélmények az Azure-portál által támogatott nyelveken kívül a következő nyelveket támogatják: dán, finn, görög, norvég és román.

<!--- ## Learn more about Intune
Use these resources to learn more about Intune:

- The [Microsoft Intune Trust Center](https://www.microsoft.com/server-cloud/products/intune-trust-center/) provides information about the security, privacy, and compliance practices of Intune, and it describes some of Intune's certifications.

- [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)--->
