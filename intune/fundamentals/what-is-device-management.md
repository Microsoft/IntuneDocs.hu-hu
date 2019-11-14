---
title: Eszközkezelés a Microsoft 365-ben
description: A Microsoft 365 Nagyvállalati verzió tartalmazza a Microsoft Intune-t. Ismerje meg, hogy az Intune hogyan nyújt mobileszköz-kezelést és mobileszköz-kezelést a szervezet számára. Olvassa el a gyakori forgatókönyveket, és az Intune használatával telepítse a Microsoft 365t a környezetében.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ab41026cd9b2ceeaaa478fc27c984d0d89db4c5
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74058528"
---
# <a name="device-management-overview"></a>Eszközkezelés áttekintése

Minden rendszergazda egyik fő feladata a vállalati erőforrások és adatok biztonságba helyezése és védelme. Ez a feladat *eszközkezelés*. A felhasználóknak számos eszköze van, ahol megnyitják és megoszthatják személyes fájljaikat, webhelyeket kereshetnek és alkalmazásokat és játékokat telepíthetnek. Ugyanezek a felhasználók is alkalmazottak és tanulók. Eszközeiket szeretnék használni a munkahelyi és iskolai erőforrásokhoz, például az e-mailekhez és a OneNote-eszközökhöz való hozzáféréshez.

Az eszközkezelés lehetővé teszi, hogy a szervezetek védelmet nyújtsanak erőforrásaik és adataik védelmére, valamint a különböző eszközökről.

Az Eszközkezelő szolgáltató segítségével a szervezet gondoskodhat arról, hogy csak a jogosult személyek és eszközök férhessenek hozzá a védett adatokhoz. Hasonlóképpen, az eszközök felhasználói nyugodtan férhetnek hozzá a munkahelyi adatokhoz a telefonjára, mert tudják, hogy az eszközük megfelel a szervezet biztonsági követelményeinek. Minden vállalatnál felmerülhet a kérdés: **Mit használhatnánk erőforrásaink védelme érdekében?**

A válasz [Microsoft Intune](what-is-intune.md). Az Intune mobileszköz-kezelést (MDM) és mobilalkalmazás-kezelést (MAM) is kínál. Minden MDM- és MAM-megoldás fő feladatai közé tartoznak a következők:

- Az iOS-, Android-, Windows-és macOS-eszközök biztonságos kezelése, valamint a különböző mobil környezetek támogatása.
- Győződjön meg arról, hogy az eszközök és alkalmazások megfelelnek a szervezet biztonsági követelményeinek.
- Olyan házirendeket hozhat létre, amelyek segítenek megőrizni a szervezet adatait a szervezet tulajdonában lévő és a személyes eszközökön.
- Az ezeket a szabályzatokat érvényesítő egyetlen, egységes mobilmegoldás használata, valamint az eszközök, alkalmazások, felhasználók és csoportok kezelésének támogatása.
- A céges adatok védelme érdekében biztosíthatja, hogy a munkahelye Hogyan férhet hozzá az adataihoz, és megosztja azokat.

Az Intune a Microsoft Azure, a Microsoft 365 és a Azure Active Directory (Azure AD) szolgáltatással integrálható. Az Azure AD segít szabályozni, hogy ki, mihez fér hozzá.

## <a name="microsoft-intune"></a>Microsoft Intune

Számos vállalat, köztük a Microsoft is az Intune használatával védi a felhasználók által vállalati vagy saját tulajdonban lévő mobileszközökön hozzáférhető, szellemi tulajdont képező adatok védelmére. Az Intune eszköz-és alkalmazás-konfigurációs házirendeket, szoftverfrissítési házirendeket és telepítési állapotokat (diagramokat, táblázatokat és jelentéseket) tartalmaz, amelyek segítenek az adathozzáférés biztonságossá tételében és figyelésében.

Sokan rendelkeznek több, különböző platformokat használó eszközzel. Egy alkalmazott használhat például Surface Pro-t a munkájához, és egy Androidos mobileszközt magáncélokra. Az is gyakori, hogy az illető ezekről az eszközökről egyaránt használja az olyan vállalati erőforrásokat, amilyen az Outlook és a SharePoint.

Az Intune-nal személyenként több eszköz, és az egyes eszközökön futó több platform, például iOS, macOS, Android és Windows is kezelhető. Az Intune elkülöníti a szabályzatokat és a beállításokat az eszköz platformja alapján. Így egyszerűen kezelheti és megtekintheti egy adott platform eszközeit.

A **[Gyakori helyzetek](common-scenarios.md)** kitűnő forrás, amelyből megtudhatja, hogyan válaszolja meg az Intune a mobileszközökkel végzett munka során gyakran felmerülő kérdéseket. Megtalálhatja a következő helyzetek ismertetését:  

- Levelezés védelme helyszíni Exchange használatával
- Az Office 365 biztonságos elérése
- Vállalati erőforrások elérése személyes eszközökkel

Az Intune-nal kapcsolatos további információkért lásd: [Mi az az Intune](what-is-intune.md).

## <a name="integration-with-secure-and-protect-services"></a>Integráció biztonsági és védelmi szolgáltatásokkal

Minden eszközkezelési megoldás fő feladata a biztonság és a védelem. Az Intune erőssége a más szolgáltatásokkal való integráció, ennek a feladatnak a szolgálatában. Példa:

- A **Microsoft 365** kulcsszerepet játszik a gyakori informatikai feladatok egyszerűsítésében. A Microsoft 365 felügyeleti központban felhasználókat hoz létre, és kezelheti a csoportokat. Emellett más szolgáltatásokhoz is hozzáférhet, például az Intune-hoz, az Azure AD-hoz és egyebekhez.

  Hozzon létre például egy iOS-eszközök csoportot Microsoft 365. Az Intune ez után olyan iOS-funkciókkal kapcsolatos szabályzatokat küld le az iOS-eszközök csoportjának, mint az App Store-hozzáférés, az AirDrop használata, biztonsági másolatot készítése az iCloudban, az Apple webes szűrőjének használata és sok egyéb.

- A **Windows Defender** a Windows 10-es eszközök védelmében közreműködő számos biztonsági funkciót tartalmaz. Az Intune és a Windows Defender együttes használatával megteheti például a következőket:

  - Engedélyezheti a [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md) megoldást, amely gyanús tevékenységeket keres mobileszközökön, fájlokban és alkalmazásokban.
  - A [Microsoft Defender komplex veszélyforrások elleni védelem (ATP)](../protect/advanced-threat-protection.md) használatával megakadályozhatja a mobileszközök biztonsági megsértését. A és a segítségével korlátozhatja a biztonsági rések hatását azáltal, hogy blokkolja a felhasználót a vállalati erőforrásokból.

- A **feltételes hozzáférés** a Azure Active Directory egyik funkciója, és szépen együttműködik az Intune-nal. A [feltételes hozzáférés](../protect/conditional-access.md)használata esetén győződjön meg arról, hogy csak a megfelelő eszközök férhetnek hozzá az e-mailekhez, a sharepointhoz és más alkalmazásokhoz.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Az Önnek megfelelő eszközkezelési megoldás kiválasztása

Az eszközkezelés több módon is megközelíthető. Először is kezelheti az eszközök különböző aspektusait az Intune-ban beépített funkciókkal. Ezt a módszert a **mobileszköz-felügyelet (Mdm)** nevezzük. A felhasználók "regisztrálják" az eszközeiket, és tanúsítványokat használnak az Intune-nal való kommunikációhoz. Rendszergazdaként leküldheti az alkalmazásokat az eszközökön, korlátozhatja az eszközöket egy adott operációs rendszerre, letilthatja a személyes eszközöket, és így tovább. Ha egy eszköz elveszett vagy ellopták, akkor eltávolíthatják az eszközről az összes adatot.

A második megközelítés szerint az eszközökön lévő alkalmazások lesznek kezelve. Ezt a módszert **Mobile Application Management (MAM)** néven nevezzük. A felhasználók a személyes eszközeiket használhatják a szervezeti erőforrások elérésére. Egy alkalmazás, például e-mail vagy a SharePoint megnyitásakor a rendszer további hitelesítést kér a felhasználótól. Ha egy eszköz elveszett vagy ellopták, akkor az eszközről az összes vállalati adat eltávolítható.

Az [MDM és az MAM](byod-technology-decisions.md) együtt is használható.

Az Intune beállításakor azt is kiválaszthatja, hogy csak az Azure Portalon, vagy az Intune és a Microsoft 365 együttes használatával kívánja kezelni az eszközöket. [A mobileszköz-kezelés áttelepítése az Intune-ba a Azure Portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) egy Microsoft IT-esettanulmány. Ebben az esetben tekintse meg, hogyan választotta a Microsoft IT a modern eszközkezelés megközelítését, és olvassa el a tanulságokat.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Az informatikai feladatok egyszerűsítése az Eszközkezelő felügyeleti központban

A [Microsoft Endpoint Manager felügyeleti központja](https://go.microsoft.com/fwlink/?linkid=2109431) a mobileszközök felügyeletére és végrehajtására szolgáló egyablakos megoldás. Ez a munkaterület magában foglalja az eszközök felügyeletéhez használt szolgáltatásokat, beleértve az Intune-t és a Azure Active Directoryt, valamint az ügyfélalkalmazások felügyeletét is.

Az Eszközkezelő felügyeleti központban a következőket teheti:

- [Eszközök regisztrálása](../enrollment/device-enrollment.md)
- [Eszközmegfelelőség beállítása](../protect/device-compliance-get-started.md)
- [Eszközök kezelése](../remote-actions/device-management.md)
- [Alkalmazások kezelése](../apps/app-management.md)  
- [iOS-es e-könyvek](../apps/vpp-ebooks-ios.md)  
- [A helyszíni Exchange-összekötő telepítése](../protect/exchange-connector-install.md)  
- [Szerepkörök kezelése](role-based-access-control.md)  
- Szoftverfrissítések kezelése
  - [Windows 10-frissítések kezelése](../protect/windows-update-for-business-configure.md)  
  - [iOS-frissítések kezelése](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Felhasználók kezelése](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Csoportok és tagok kezelése](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Hibaelhárítás](help-desk-operators.md)

## <a name="next-steps"></a>További lépések

Ha készen áll egy MDM-vagy MAM-megoldás megkezdésére, tekintse át az Intune beállításához, az eszközök regisztrálásához és a házirendek létrehozásához szükséges lépéseket. A [mobileszköz-kezelés a Microsoft 365 számára](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) is nagyszerű erőforrás.
