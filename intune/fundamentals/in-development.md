---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514564"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>Fejlesztés a Microsoft Intune – február 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Webes klipek átcélzása a Microsoft Edge-be iOS-/iPadOS-eszközökön<!-- 5455276 -->
Az iOS-/iPadOS-eszközökön rögzített webalkalmazásként feldolgozható webklipeket frissíteni kell. Az újonnan telepített webklipek a Microsoft Edge-ben nyílnak meg a Intune Managed Browser helyett, ha egy védett böngészőben kell megnyitni. A meglévő webklipeket újra meg kell célozni, hogy a Managed Browser helyett a Microsoft Edge-ben nyíljon meg.

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>a macOS Céges portál felhasználói élményének fejlesztése<!-- 5568987 -->
Fejlesztjük a macOS-eszközök regisztrálási élményét és a Mac Céges portál alkalmazást. A következőket várhatja el:
- Jobb Microsoft automatikus **frissítési** élmény a regisztráció során, amely biztosítja, hogy a felhasználók a céges portál legújabb verziójával rendelkezzenek.
- Továbbfejlesztett megfelelőség-ellenőrzési lépés a regisztráció során.
- A másolt incidensek azonosítóinak támogatása, így a felhasználók gyorsabban küldhetnek hibákat az eszközeiről a céges támogatási csapatnak.

A regisztrációval és a Mac Céges portál alkalmazással kapcsolatos további információkért lásd: macOS-eszköz regisztrálása a Céges portál alkalmazással (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp). 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Képernyő eltávolítva Céges portál, Android munkahelyi profil regisztrációja<!--6103987 -->
A **Mi a következő lépés?** a rendszer eltávolítja az androidos munkahelyi profil beléptetési folyamatát céges portál a felhasználói élmény egyszerűsítése érdekében. Az androidos munkahelyi profil regisztrálási folyamatának megtekintéséhez nyissa meg az [androidos]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile) munkahelyi profil beléptetése című részt.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>Microsoft Defender Advanced Threat Protection (ATP) alkalmazás macOS rendszerhez<!-- 5424518 idready -->
Az Intune-nal egyszerűen üzembe helyezheti a macOS rendszerhez készült Microsoft Defender Advanced Threat Protection (ATP) alkalmazást a felügyelt Mac-eszközökön. További információ: [a Microsoft Defender komplex veszélyforrások elleni védelem Mac rendszerhez](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac). 

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Vezetékes hálózati eszközök konfigurációs profiljai macOS-eszközökhöz<!-- 3508686  -->
A rendszer elérhetővé teszi az új macOS-eszköz konfigurációs profilt, amely a vezetékes hálózatokat (az**eszköz konfigurációját** > **profilokat** > a **profil létrehozása** > **MacOS** platformon > **vezetékes hálózat** profil típusa) beállítására. Ezzel a szolgáltatással 802.1 x-profilokat hozhat létre a vezetékes hálózatok kezeléséhez, és ezeket a vezetékes hálózatokat a macOS-eszközökre is üzembe helyezheti.

A következőkre vonatkozik:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>A IKEv2 VPN-kapcsolatokkal rendelkező VPN-profilok mindig az iOS/iPadOS eszközökön használhatók <!-- 1947932 idready -->
IOS-/iPadOS-eszközökön létrehozhat egy IKEv2-kapcsolattal rendelkező VPN-profilt (az**eszköz konfigurációjának** > **profiljait** > **profil létrehozása** > **iOS/iPadOS** for platform > **VPN** a profil típusa). A jövőbeli frissítésekben a IKEv2-mel is konfigurálhatja az Always-on. Ha be van állítva, a IKEv2 VPN-profilok automatikusan csatlakoznak, és csatlakoztatva maradnak (vagy gyorsan újracsatlakozhatnak) a VPN-hez. A hálózat vagy az eszközök újraindítása esetén is csatlakoztatva marad.

IOS/iPadOS esetén a always-on VPN a IKEv2-profilokra korlátozódik.

Az aktuálisan konfigurálható IKEv2-beállítások megtekintéséhez lépjen a [VPN-beállítások hozzáadása iOS/iPadOS eszközökhöz a Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

A következőkre vonatkozik:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Továbbfejlesztett felhasználói felületi élmény a konfigurációs profilok iOS/iPadOS és macOS rendszerű eszközökön való létrehozásakor<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Ha iOS/iPadOS vagy macOS rendszerű eszközökhöz hoz létre profilt, a rendszer frissíti az Endpoint Management felügyeleti központban található felhasználói élményt. Ez a változás hatással van a következő eszköz-konfigurációs profilokra (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > **iOS** vagy **MacOS** for platform):

- Egyéni: iOS/iPadOS, macOS
- Eszköz szolgáltatásai: iOS/iPadOS, macOS
- Eszköz korlátozásai: iOS/iPadOS, macOS
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

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Windows-eszközök elsődleges felhasználójának módosítása <!-- 3794742 -->
Megváltoztathatja az elsődleges felhasználót a Windows Hybrid és az Azure AD-hez csatlakoztatott eszközökhöz. Ehhez nyissa meg az **Intune** > **eszközök** > **minden eszköz** > válasszon egy eszközt > **Tulajdonságok** > **elsődleges felhasználó**. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Sorozatszám az Apple MDM push-tanúsítvány oldalán<!--5947765 -->
Az Apple MDM push-tanúsítvány lapján megjelenik a sorozatszám. A sorozatszám szükséges ahhoz, hogy újra hozzáférhessen az Apple MDM push-tanúsítványhoz, ha a tanúsítvány létrehozásához használt Apple ID azonosítóhoz való hozzáférés elvész. A sorozatszám megjelenítéséhez nyissa meg az **eszközök** > **iOS** > **iOS-regisztráció** > az **Apple Mdm push-tanúsítvány**lehetőséget.

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>Válassza ki, hogy mely iOS-/iPadOS-frissítéseket szeretné leküldeni a regisztrált eszközökre<!--5879689 -->
Kiválaszthat egy adott iOS/iPadOS-frissítést, amely az Apple Business Manager vagy az Apple School Manager használatával regisztrált eszközökre küldi le azokat. Az ilyen eszközöknek rendelkeznie kell egy olyan eszköz-konfigurációs házirenddel, amely bizonyos számú nap elteltével késlelteti a szoftverfrissítés láthatóságát. Ennek a funkciónak a megtekintéséhez nyissa meg a MEM >- **eszközök** ** > ios** -es > **frissítési szabályzatok iOS/iPadOS > a** **profil létrehozása**lehetőséget.

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>Új frissítési ütemterv beállítások az operációs rendszer frissítéseinek beléptetéséhez a beléptetett iOS/iPadOS-eszközökön<!--5879689-->
Az iOS/iPadOS operációs rendszer frissítéseinek ütemezésekor a következő lehetőségek közül választhat. Ez az Apple Business Manager vagy az Apple School Manager regisztrációs típusait használó eszközökre vonatkozik.
- Frissítés a következő bejelentkezéskor
- Frissítés az ütemezett idő alatt
- Frissítés az ütemezett időkereten kívül

Az utóbbi két lehetőség esetében több időablakot is létrehozhat.

Az új beállítások megjelenítéséhez nyissa meg a MEM >- **eszközök** > **iOS** **- > frissítési szabályzatok iOS/iPadOS > a** **profil létrehozása**lehetőséget.


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Figyelés és hibaelhárítás

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Továbbfejlesztett Intune jelentéskészítési élmény<!-- 3791418 idready -->
Az Intune mostantól továbbfejlesztett jelentéskészítési lehetőségeket kínál, beleértve az új jelentési típusokat, a jobb jelentési szervezetet, a célzottabb nézeteket, a jobb jelentési funkciókat, valamint a több konzisztens és kellő időben megjelenő adatát. A jelentéskészítési élmény a nyilvános előzetes verzióról a GA-ra (általánosan elérhető) vált. Emellett a GA-kiadás a honosítási támogatást, a hibajavításokat, a tervezési javításokat és az eszközök megfelelőségi adatainak a [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)lévő csempén való összegzését is biztosítja.

Az új Jelentéstípusok a következőkre összpontosítanak:
- **Működés** – a negatív állapotú friss rekordokat biztosít. 
- **Szervezet** – a teljes állapot szélesebb körű összegzését biztosítja.
- **Előzmények** – mintákat és trendeket biztosít egy adott időszakra vonatkozóan.
- **Specialist** – lehetővé teszi, hogy a nyers adatait használja saját egyéni jelentéseinek létrehozásához.

Az új jelentések első halmaza az eszköz megfelelőségére koncentrál. További információ: [Blog Microsoft Intune jelentési keretrendszer](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) és [Intune-jelentések](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Az Intune-szerepkörök felhasználói felületének módosításai elérkeznek<!--5801612 idready-->
A [Microsoft Endpoint Manager felügyeleti központ](https://go.microsoft.com/fwlink/?linkid=2109431) felhasználói felületének > **bérlői adminisztrációs** > **szerepkörei** egy sokkal felhasználóbarát és intuitív kialakításban lesznek módosítva. Ez a felhasználói élmény ugyanazokat a beállításokat és adatokat tartalmazza, amelyeket most használ, de az új felület egy varázsló-szerű folyamatot alkalmaz.


<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Származtatott hitelesítő adatok támogatása androidos COBO-eszközökön<!--4839592-->
A származtatott hitelesítő adatokat az Android Enterprise teljes körűen felügyelt eszközökön is használhatja. A támogatás a Entrust Datacard, a közbenjáró és a DISA fajtatiszta hitelesítő adatok beolvasására is használható. Az alkalmazás-hitelesítés, a Wi-Fi, a VPN, az S/MIME-aláírás és/vagy az azt támogató alkalmazások esetében a rendszer származtatott hitelesítő adatokat használhat.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>A Microsoft Defender víruskereső és a Windows biztonsági élmény beállításainak kezelése a vírusvédelmi szabályzat használatával<!--6131401 -->
A *végpontok biztonsági* csomópontján megadhatja a **víruskereső**beállításait. Ha a szabályzatot a víruskeresőhöz konfigurálja, a Windows 10-es eszközökhöz tartozó beállításokat a következő két profillal adhatja meg:

- Microsoft Defender víruskereső: a felhőalapú védelem, a víruskeresők kizárása, a szervizelés, a vizsgálati beállítások és egyéb beállítások kezelése.
- Windows biztonsági élmény: felügyelheti, hogy a felhasználók hogyan használják a Windows biztonsági beállításokat az eszközökön. Beállíthatja, hogy a végfelhasználók hogyan tekinthetik meg a Microsoft Defender Security centert és a kapott értesítéseket. 

<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>További információ
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.


