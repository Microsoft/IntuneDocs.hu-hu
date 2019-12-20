---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35e4612c9aa482204ea61c46c5cc56051874e6de
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207400"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>Fejlesztés a Microsoft Intune – december 2019

A készültség és a tervezés elősegítése érdekében ez az oldal felsorolja az Intune felhasználói felületének frissítéseit és a fejlesztés alatt álló, de még nem kiadott funkciókat. Az oldalon található információk mellett:

- Ha várható, hogy a módosítás előtt végre kell hajtania a lépéseket, közzé kell tenni egy kiegészítő bejegyzést az Office Message Centerben.
- Ha egy szolgáltatás éles környezetbe kerül, akár előzetes, akár általánosan elérhető, a szolgáltatás leírása az oldalról az [újdonságokra](whats-new.md)kerül át.
- Ez az oldal és az [új](whats-new.md) oldal rendszeresen frissül. További hírekért látogasson vissza.
- Tekintse meg a stratégiai termékek és ütemtervek [Microsoft 365 ütemtervét](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) .

> [!NOTE]
> Ez az oldal az Intune-funkciókra vonatkozó jelenlegi elvárásait mutatja be egy későbbi kiadásban. Előfordulhat, hogy a dátumok és az egyes funkciók változhatnak. Ez a lap nem ismerteti a fejlesztés összes funkcióját.

**RSS-hírcsatorna**: az alábbi URL-cím másolásával és a hírcsatorna-olvasóba való beillesztésével megtudhatja, hogy az oldal frissítése megtörtént-e: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Alkalmazáskezelés

### <a name="user-licensed-vpp-apps-for-user-enrollment-ios-devices---5619268---"></a>Felhasználó által licencelt VPP-alkalmazások felhasználói beléptetési iOS-eszközökhöz<!-- 5619268 -->
A felhasználók beléptetésére szolgáló iOS-eszközök esetében a végfelhasználók többé nem fognak megjelenni a rendelkezésre álló, eszközre licencelt VPP-alkalmazásokkal. A végfelhasználók azonban továbbra is láthatják az összes felhasználó által licencelt VPP-alkalmazást a Céges portálon belül. További információ a VPP-alkalmazásokról: [Apple Volume Purchase program által vásárolt iOS-és MacOS-alkalmazások kezelése Microsoft Intune használatával](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Személyes helyreállítási kulcs beolvasása a MEM titkosított macOS-eszközökről<!-- 4851745 -->
A végfelhasználók a saját helyreállítási kulcsát (FileVault-kulcs) az iOS Céges portál alkalmazás használatával tudják lekérni. A személyes helyreállítási kulccsal rendelkező eszközt regisztrálni kell az Intune-ban, és az Intune-on keresztül kell titkosítani a FileVault-mel. Az iOS Céges portál alkalmazás használatával a végfelhasználó megnyithatja a Safari webes nézetét, és lekérheti a személyes helyreállítási kulcsát. Az Intune-ban válassza az **eszközök** > *a titkosított és regisztrált macOS-eszköz > a* **helyreállítási kulcs beszerzése**lehetőséget. További információ a FileVault: FileVault- [titkosítás MacOS rendszerhez](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Értesítések megjelenítése a Windows Céges portál alkalmazásához<!-- 1808082  -->
A Windows-eszközökön a Céges portál alkalmazást frissítjük a bejelentési értesítések megjelenítéséhez a felhasználók számára, még akkor is, ha az alkalmazás be van zárva. A frissítés csak akkor jeleníti meg az elérhető alkalmazások értesítéseit, ha a telepítés állapota befejeződött vagy sikertelen. A Céges portál alkalmazás nem jeleníti meg az értesítéseket a szükséges alkalmazásokhoz.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>A Céges portál alkalmazás telepítési állapotüzenetek megjelenítése<!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Automatikus proxybeállítások hozzáadása Wi-Fi profilokhoz androidos vállalati munkahelyi profilokhoz<!-- 4490822 idready -->
Az Android Enterprise munkahelyi profil eszközein Wi-Fi profilok hozhatók létre. Ha a Wi-Fi Enterprise-típust választja, megadhatja a Wi-Fi-hálózaton használt bővíthető hitelesítési protokoll (EAP) típusát is.

Egy jövőbeli frissítés esetében, ha a vállalat típusát választja, megadhatja az automatikus proxybeállításokat, beleértve a proxykiszolgáló URL-címét, például a `proxy.contoso.com`.

A konfigurálható aktuális Wi-Fi beállítások megjelenítéséhez nyissa meg a [Wi-Fi beállítások hozzáadása az Android Enterprise és az Android kioszkot futtató eszközökhöz Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

A következőkre vonatkozik:
- Androidos vállalati munkahelyi profil

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Vezetékes hálózati eszközök konfigurációs profiljai macOS-eszközökhöz<!-- 3508686  -->
A rendszer elérhetővé teszi az új macOS-eszköz konfigurációs profilt, amely a vezetékes hálózatokat (az**eszköz konfigurációját** > **profilokat** > a **profil létrehozása** > **MacOS** platformon > **vezetékes hálózat** profil típusa) beállítására. Ezzel a szolgáltatással 802.1 x-profilokat hozhat létre a vezetékes hálózatok kezeléséhez, és ezeket a vezetékes hálózatokat a macOS-eszközökre is üzembe helyezheti.

A következőkre vonatkozik:
- macOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

<!--
## Security
-->

<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>További információ
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.


