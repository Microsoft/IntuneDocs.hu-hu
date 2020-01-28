---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78022dc4bdfa108bcd04e180ab413cbf04d2c728
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755612"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Fejlesztés a Microsoft Intune – január 2020

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Értesítések megjelenítése a Windows Céges portál alkalmazásához<!-- 1808082  -->
A Windows-eszközökön a Céges portál alkalmazást frissítjük a bejelentési értesítések megjelenítéséhez a felhasználók számára, még akkor is, ha az alkalmazás be van zárva. A frissítés csak akkor jeleníti meg az elérhető alkalmazások értesítéseit, ha a telepítés állapota befejeződött vagy sikertelen. A Céges portál alkalmazás nem jeleníti meg az értesítéseket a szükséges alkalmazásokhoz. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>A Céges portál alkalmazás telepítési állapotüzenetek megjelenítése<!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>Webes klipek átcélzása a Microsoft Edge-hez iOS-eszközökön<!-- 5455276 -->
Az iOS-eszközökön rögzített webalkalmazásként szolgáló webes klipeket frissíteni kell. Az újonnan telepített webklipek a Microsoft Edge-ben nyílnak meg a Intune Managed Browser helyett, ha egy védett böngészőben kell megnyitni. A meglévő webklipeket újra meg kell célozni, hogy a Managed Browser helyett a Microsoft Edge-ben nyíljon meg. 


<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Vezetékes hálózati eszközök konfigurációs profiljai macOS-eszközökhöz<!-- 3508686  -->
A rendszer elérhetővé teszi az új macOS-eszköz konfigurációs profilt, amely a vezetékes hálózatokat (az**eszköz konfigurációját** > **profilokat** > a **profil létrehozása** > **MacOS** platformon > **vezetékes hálózat** profil típusa) beállítására. Ezzel a szolgáltatással 802.1 x-profilokat hozhat létre a vezetékes hálózatok kezeléséhez, és ezeket a vezetékes hálózatokat a macOS-eszközökre is üzembe helyezheti.

A következőkre vonatkozik:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>A IKEv2 VPN-kapcsolatokkal rendelkező VPN-profilok mindig az iOS-eszközökön használhatók <!-- 1947932 idready -->
IOS-eszközökön létrehozhat olyan VPN-profilt, amely IKEv2-kapcsolattal (az**eszköz konfigurációjának** > **profiljaival** > **create Profile** > **iOS/iPadOS** for platform > **VPN** a profil típusa). A jövőbeli frissítésekben a IKEv2-mel is konfigurálhatja az Always-on. Ha be van állítva, a IKEv2 VPN-profilok automatikusan csatlakoznak, és csatlakoztatva maradnak (vagy gyorsan újracsatlakozhatnak) a VPN-hez. A hálózat vagy az eszközök újraindítása esetén is csatlakoztatva marad.

Az iOS-en a always-on VPN a IKEv2-profilokra korlátozódik.

Az aktuálisan konfigurálható IKEv2-beállítások megtekintéséhez lépjen a [VPN-beállítások hozzáadása iOS-eszközökön a Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

A következőkre vonatkozik:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Továbbfejlesztett felhasználói felületi élmény a konfigurációs profilok iOS-és macOS-eszközökön való létrehozásakor<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Ha iOS-vagy macOS-eszközökhöz hoz létre profilt, a rendszer frissíti az Endpoint Management felügyeleti központban található felhasználói élményt. Ez a változás hatással van a következő eszköz-konfigurációs profilokra (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > **iOS** vagy **MacOS** for platform):

- Egyéni: iOS, macOS
- Eszköz funkciói: iOS, macOS
- Eszköz korlátozásai: iOS, macOS
- Endpoint Protection: macOS
- Bővítmények: macOS
- Preferencia fájl: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Továbbfejlesztett felhasználói felületi élmény OEMConfig-konfigurációs profilok létrehozásakor androidos vállalati eszközökön<!-- 5568645 idready  -->
Ha androidos vállalati eszközökhöz hoz létre vagy szerkeszt egy OEMConfig-profilt, a rendszer frissíti az Endpoint Management felügyeleti központ felületét. A frissített élmény áttekintést nyújt a konfigurált beállításokról. Ez a változás hatással van a OEMConfig-eszköz konfigurációs profiljára (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > **Android Enterprise** for platform > **OEMConfig** ).

Ez a funkció az alábbiakra vonatkozik:
- Vállalati Android 

<!-- ***********************************************-->
<!--## Device enrollment-->



<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés


### <a name="new-information-in-device-details---4471759-5604099----"></a>Új információ az eszköz részleteiben<!-- 4471759 5604099  -->
A következő információk lesznek hozzáadva az eszközök **áttekintő** lapjához:
- Memória kapacitása (a fizikai memória mennyisége az eszközön)
- Tárolási kapacitás (az eszközön található fizikai tárterület mennyisége) 
- CPU-processzor típusa és sebessége
- RAM-és processzor-adatmennyiség

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Az Intune-szerepkörök felhasználói felületének módosításai elérkeznek<!--5801612 idready-->
A [Microsoft Endpoint Manager felügyeleti központ](https://go.microsoft.com/fwlink/?linkid=2109431) felhasználói felületének > **bérlői adminisztrációs** > **szerepkörei** egy sokkal felhasználóbarát és intuitív kialakításban lesznek módosítva. Ez a felhasználói élmény ugyanazokat a beállításokat és adatokat tartalmazza, amelyeket most használ, de az új felület egy varázsló-szerű folyamatot alkalmaz.


<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Származtatott hitelesítő adatok támogatása androidos COBO-eszközökön<!--4839592-->
A származtatott hitelesítő adatokat az Android Enterprise teljes körűen felügyelt eszközökön is használhatja. A támogatás a Entrust Datacard, a közbenjáró és a DISA fajtatiszta hitelesítő adatok beolvasására is használható. Az alkalmazás-hitelesítés, a Wi-Fi, a VPN, az S/MIME-aláírás és/vagy az azt támogató alkalmazások esetében a rendszer származtatott hitelesítő adatokat használhat. 

<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>További információ
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.


