---
title: Eszközkezelés Microsoft 365
description: A Microsoft 365 Nagyvállalati verzió Microsoft Intune tartalmaz. Ismerje meg, hogy az Intune hogyan nyújt mobileszköz-kezelést és mobileszköz-kezelést a szervezet számára. Olvassa el a gyakori forgatókönyveket, és az Intune használatával telepítse a Microsoft 365t a környezetében.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/14/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93d8107d235d9f13af487bba4cbf6a71fc92eeab
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314533"
---
# <a name="device-management-overview"></a>Eszközkezelés – áttekintés

A rendszergazda kulcsfontosságú feladata, hogy megvédje és biztonságossá tegye a szervezet erőforrásait és adatait. Ez a feladat *eszközkezelés*. A felhasználóknak számos eszköze van, ahol megnyitják és megoszthatják személyes fájljaikat, webhelyeket kereshetnek és alkalmazásokat és játékokat telepíthetnek. Ugyanezek a felhasználók is alkalmazottak és tanulók. Eszközeiket szeretnék használni a munkahelyi és iskolai erőforrásokhoz, például az e-mailekhez és a OneNote-eszközökhöz való hozzáféréshez.

Az eszközkezelés lehetővé teszi, hogy a szervezetek védelmet nyújtsanak erőforrásaik és adataik védelmére, valamint a különböző eszközökről.

Az Eszközkezelő szolgáltató segítségével a szervezet gondoskodhat arról, hogy csak a jogosult személyek és eszközök férhessenek hozzá a védett adatokhoz. Hasonlóképpen, az eszközök felhasználói nyugodtan férhetnek hozzá a munkahelyi adatokhoz a telefonjára, mert tudják, hogy az eszközük megfelel a szervezet biztonsági követelményeinek. Szervezetként megkérheti, **hogy mit használjon az erőforrások megóvása érdekében?**

A válasz [Microsoft Intune](what-is-intune.md). Az Intune mobileszköz-felügyeletet (MDM) és mobileszköz-kezelést (MAM) is kínál. Bármely MDM-vagy MAM-megoldás főbb feladatai a következők:

- Az iOS-, Android-, Windows-és macOS-eszközök biztonságos kezelése, valamint a különböző mobil környezetek támogatása.
- Győződjön meg arról, hogy az eszközök és alkalmazások megfelelnek a szervezet biztonsági követelményeinek.
- Olyan házirendeket hozhat létre, amelyek segítenek megőrizni a szervezet adatait a szervezet tulajdonában lévő és a személyes eszközökön.
- Egyetlen, egységes mobil megoldás használatával kényszerítheti ezeket a házirendeket, és kezelheti az eszközöket, az alkalmazásokat, a felhasználókat és a csoportokat.
- A céges adatok védelme érdekében biztosíthatja, hogy a munkahelye Hogyan férhet hozzá az adataihoz, és megosztja azokat.

Az Intune a Microsoft Azure, a Microsoft 365 és a Azure Active Directory (Azure AD) szolgáltatással integrálható. Az Azure AD segítségével szabályozhatja, hogy ki férhet hozzá, és mire van hozzáférése.

## <a name="microsoft-intune"></a>Microsoft Intune

Számos szervezet, például a Microsoft, az Intune-nal gondoskodik a felhasználók által a vállalat tulajdonában lévő és a személyes mobileszközök által használt védett adatok védelméről. Az Intune eszköz-és alkalmazás-konfigurációs házirendeket, szoftverfrissítési házirendeket és telepítési állapotokat (diagramokat, táblázatokat és jelentéseket) tartalmaz, amelyek segítenek az adathozzáférés biztonságossá tételében és figyelésében.

Gyakori, hogy az emberek több különböző platformot használó eszközzel rendelkezzenek. Előfordulhat például, hogy egy alkalmazott felhasználja a Surface Pro for Work alkalmazást, és egy androidos mobileszköz a magánéletében. Emellett az is gyakori, hogy egy személy több eszközről is hozzáférhessen a szervezeti erőforrásokhoz, például a Microsoft Outlookhoz és a SharePointhoz.

Az Intune-nal több eszközt is kezelhet személyenként, valamint az egyes eszközökön futó különböző platformokat, például az iOS, a macOS, az Android és a Windows rendszert. Az Intune elkülöníti a szabályzatokat és a beállításokat az eszköz platformja alapján. Így egyszerűen kezelheti és megtekintheti egy adott platform eszközeit.

A **[gyakori forgatókönyvek](common-scenarios.md)** egy nagyszerű erőforrás, amelyből megtudhatja, hogyan válaszol az Intune a mobileszközök használata során felmerülő gyakori kérdésekre. A következőkkel kapcsolatos forgatókönyvek találhatók:  

- E-mailek védelme helyszíni Exchange-sel
- Az Office 365 biztonságos és biztonságos elérése
- Személyes eszközök használata a szervezeti erőforrások eléréséhez

Az Intune-nal kapcsolatos további információkért lásd: [Mi az az Intune](what-is-intune.md).

## <a name="integration-with-secure-and-protect-services"></a>Integráció a biztonságos és a védelemmel ellátott szolgáltatásokkal

Az Eszközkezelő megoldás egyik kulcsfontosságú feladata a biztonság és a védelem biztosítása. Az Intune nagyszerű munkát végez a más szolgáltatásokkal való integrálásában a feladat eléréséhez. Példa:

- **Microsoft 365** egy kulcsfontosságú összetevő a gyakori informatikai feladatok egyszerűsítéséhez. A Microsoft 365 felügyeleti központban felhasználókat hoz létre, és kezelheti a csoportokat. Emellett más szolgáltatásokhoz is hozzáférhet, például az Intune-hoz, az Azure AD-hoz és egyebekhez.

  Hozzon létre például egy iOS-eszközök csoportot Microsoft 365. Ezt követően az Intune használatával leküldheti a házirendeket az iOS-eszközök csoportba, amely az iOS-funkciókra koncentrál, például az alkalmazás-áruház eléréséhez, a AirDrop használatával, az Apple webes szűrő használatával történő biztonsági mentéssel, valamint egyebek mellett.

- A **Windows Defender** számos biztonsági funkciót tartalmaz, amelyek segítenek a Windows 10-es eszközök védelmében. Az Intune és a Windows Defender együttes használatával például a következőket teheti:

  - A [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md) lehetővé teszi a gyanús tevékenységek keresését a mobileszközökön található fájlokban és alkalmazásokban.
  - A [Microsoft Defender komplex veszélyforrások elleni védelem (ATP)](../protect/advanced-threat-protection.md) használatával megakadályozhatja a mobileszközök biztonsági megsértését. A és a segítségével korlátozhatja a biztonsági rések hatását azáltal, hogy blokkolja a felhasználót a vállalati erőforrásokból.

- A **feltételes hozzáférés** a Azure Active Directory egyik funkciója, és szépen együttműködik az Intune-nal. A [feltételes hozzáférés](../protect/conditional-access.md)használata esetén győződjön meg arról, hogy csak a megfelelő eszközök férhetnek hozzá az e-mailekhez, a sharepointhoz és más alkalmazásokhoz.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Válassza ki az Ön számára legmegfelelőbb eszköz-kezelési megoldást

Több módon is megközelítheti az eszközök felügyeletét. Először is kezelheti az eszközök különböző aspektusait az Intune-ban beépített funkciókkal. Ezt a módszert a **mobileszköz-felügyelet (Mdm)** nevezzük. A felhasználók "regisztrálják" az eszközeiket, és tanúsítványokat használnak az Intune-nal való kommunikációhoz. Rendszergazdaként leküldheti az alkalmazásokat az eszközökön, korlátozhatja az eszközöket egy adott operációs rendszerre, letilthatja a személyes eszközöket, és így tovább. Ha egy eszköz elvesztése vagy ellopása megszakadt, akkor az eszközről is eltávolíthatja az összes adatforrást.

A második megközelítésben az alkalmazások kezelése az eszközökön. Ezt a módszert **Mobile Application Management (MAM)** néven nevezzük. A felhasználók a személyes eszközeiket használhatják a szervezeti erőforrások elérésére. Az alkalmazások, például az e-mailek vagy a SharePoint megnyitásakor a rendszer a felhasználókat további hitelesítésre kéri. Ha egy eszköz elvesztése vagy ellopása megszakadt, akkor az eszközről eltávolíthatja az összes szervezeti adatforrást.

A [Mdm és a MAM](byod-technology-decisions.md) együttes használatát is használhatja.

Az Intune beállításakor azt is megteheti, hogy az eszközöket csak a Azure Portalban használja, vagy az Intune-t és az Microsoft 365 együtt szeretné kezelni az eszközöket. [A mobileszköz-kezelés áttelepítése az Intune-ba a Azure Portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) egy Microsoft IT-esettanulmány. Ebben az esetben tekintse meg, hogyan választotta a Microsoft IT a modern eszközkezelés megközelítését, és olvassa el a tanulságokat.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Az informatikai feladatok egyszerűsítése az Eszközkezelő felügyeleti központban

Az [Eszközkezelő felügyeleti központ](https://devicemanagement.microsoft.com/) egy egyablakos áruház a mobileszközök feladatainak kezeléséhez és végrehajtásához. Ez a munkaterület magában foglalja az eszközök felügyeletéhez használt szolgáltatásokat, beleértve az Intune-t és a Azure Active Directoryt, valamint az ügyfélalkalmazások felügyeletét is.

Az Eszközkezelő felügyeleti központban a következőket teheti:

- [Eszközök regisztrálása](../enrollment/device-enrollment.md)
- [Eszköz megfelelőségének beállítása](../protect/device-compliance-get-started.md)
- [Eszközök kezelése](../remote-actions/device-management.md)
- [Alkalmazások kezelése](../apps/app-management.md)  
- [iOS-es e-könyvek](../apps/vpp-ebooks-ios.md)  
- [A helyszíni Exchange-összekötő telepítése](../protect/exchange-connector-install.md)  
- [Szerepkörök kezelése](role-based-access-control.md)  
- Szoftverfrissítések kezelése
  - [A Windows 10 frissítéseinek kezelése](../protect/windows-update-for-business-configure.md)  
  - [IOS-frissítések kezelése](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Felhasználók kezelése](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Csoportok és tagok kezelése](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Hibaelhárítás](help-desk-operators.md)

## <a name="next-steps"></a>Következő lépések

Ha készen áll egy MDM-vagy MAM-megoldás megkezdésére, tekintse át az Intune beállításához, az eszközök regisztrálásához és a házirendek létrehozásához szükséges lépéseket. A [mobileszköz-kezelés a Microsoft 365 számára](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) is nagyszerű erőforrás.
