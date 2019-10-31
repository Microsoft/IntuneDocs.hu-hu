---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182920"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>Fejlesztés a Microsoft Intune – november 2019

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>S/MIME-támogatás a Microsoft Outlook Mobile-hoz <!-- 2669398  -->
Az Intune támogatja az olyan S/MIME-aláírási és titkosítási tanúsítványok továbbítását, amelyek az Outlook Mobile-ban iOS és Android rendszereken is használhatók. Kapcsolódó információk: [iOS-eszközök e-mail-beállításai](~/configuration/email-settings-ios.md) és [e-mail-beállítások Android-eszközökhöz](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>Egyéni beállítások macOS-alkalmazások támogatása <!-- 4736278  -->
Az Intune támogatni fogja az egyéni beállításokat, így adott kulcsokat és értékeket adhat hozzá egy meglévő Preferences (. plist) fájlhoz a macOS-alkalmazások és az eszköz konfigurálásához. Nem minden alkalmazás támogatja a felügyelt beállításokat, és bizonyos esetekben csak bizonyos beállítások kezelhetők. A beállítások csak az eszköz csatornán keresztül lesznek telepítve. Csak az eszköz csatornájának beállításait tároló. xml kiterjesztésű fájlokat vagy. xml fájlokat kell feltöltenie.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Hozzárendelés típusa érték a Windows Céges portálban <!-- 5459950  -->
A Windows Céges portál alkalmazás **telepített alkalmazások** lapja frissülni fog. A **telepített alkalmazások** lap **hozzárendelés típusa** oszlopa úgy lett frissítve, hogy "a szervezet által igényelt" néven kell meghívni. A lehetséges értékek az **Igen** vagy a **nem** értékkel jelölhetők meg a szükséges és az elérhető alkalmazások. Ez a változás a végfelhasználók megtévesztésére reagál. További információ a Windows vállalati portálról: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Win32-alkalmazások futtatása Windows 10-es S üzemmódú eszközökön <!-- 3747604  --> 
A Windows 10 S módban felügyelt eszközökön Win32-alkalmazásokat telepíthet és futtathat. Hozzon létre egy vagy több kiegészítő szabályzatot az S üzemmódhoz a Windows Defender Application Control (WDAC) PowerShell-eszközök használatával. A kiegészítő szabályzatok aláírásához használja az eszköz Guard-aláírási portálját. Ezután töltse fel és terjessze a szabályzatokat az Intune-on keresztül. 

Az Intune-ban ezt a képességet az **ügyfélalkalmazások** > **Windows 10 S kiegészítő szabályzatok**kiválasztásával találja meg. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Alkalmazás rendelkezésre állásának beállítása dátum és idő alapján <!-- 3510685  -->
Rendszergazdaként konfigurálhatja a szükséges alkalmazás kezdési idejét és határidejét. A kezdési időpontban az Intune felügyeleti bővítmény letölti az alkalmazás tartalmát, és gyorsítótárazza. Az alkalmazás a határidő lejártakor lesz telepítve. Az elérhető alkalmazások esetében a kezdési időpont akkor fog megjelenni, amikor az alkalmazás megjelenik a Céges portálban. 

Az alkalmazások rendelkezésre állásának beállítása dátum és idő alapján:

1. Az Intune-ban válassza a **Client apps** > **alkalmazások**elemet. 
1. Válasszon ki egy alkalmazást a listából, vagy adjon hozzá egy újat a **Hozzáadás gombra**kattintva. 
1. Az alkalmazás panelen válassza a **hozzárendelések** > **Csoport hozzáadása**elemet. 
1. Állítsa a **hozzárendelés típusát** **kötelező** értékre, majd válassza a **befoglalt csoportok**lehetőséget. 
1. Állítsa be **ezt az alkalmazást az összes felhasználó** számára az **Igen**értékre. 
1. Válassza a **Szerkesztés** lehetőséget a **végfelhasználói élmény** beállításainak módosításához. 
1. A **végfelhasználói élmény** panelen szükség szerint állítsa be a **szoftver rendelkezésre állási idejét** . 

További információt az [Alkalmazások hozzáadása a Microsoft Intune-hoz](../apps/apps-add.md) című cikkben talál.

### <a name="require-win32-apps-to-restart----3136567----"></a>Win32-alkalmazások újraindításának megkövetelése <!-- 3136567  -->
A sikeres telepítés után a Win32-alkalmazás újraindítását is megkövetelheti. Kiválaszthatja, hogy mennyi idő (türelmi időszak) legyen az újraindítás előtt.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Értesítések megjelenítése a Windows Céges portál alkalmazásához <!-- 1808082  -->
A Windows-eszközökön a Céges portál alkalmazást frissítjük a bejelentési értesítések megjelenítéséhez a felhasználók számára, még akkor is, ha az alkalmazás be van zárva. A frissítés csak akkor jeleníti meg az elérhető alkalmazások értesítéseit, ha a telepítés állapota befejeződött vagy sikertelen. A Céges portál alkalmazás nem jeleníti meg az értesítéseket a szükséges alkalmazásokhoz.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>A Céges portál alkalmazás telepítési állapotüzenetek megjelenítése <!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.
- Az alkalmazás telepítése sikeresen megtörtént, de újraindítást igényel.
- Az alkalmazás telepítése folyamatban van, de a folytatáshoz újraindítás szükséges.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune alkalmazás Android-és iOS-eszközökön lehetővé teszi az alkalmazások értesítési tartalmának vezérlését a szervezeti fiókok számára. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy az összes APP-kompatibilis alkalmazáshoz nem érhető el. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>PKCS-tanúsítványok használata Wi-Fi profilokkal Windows 10 és újabb rendszerű eszközökön <!-- 3246388  -->
Jelenleg a SCEP-tanúsítványokkal rendelkező Windows Wi-Fi-profilokat hitelesítheti (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **Windows 10 és újabb verziók** a platformhoz > **Wi-Fi** Profil típusa > **Enterprise** > **EAP-típus**). A PKCS-tanúsítványokat használhatja a Windows Wi-Fi profiljaival. Ez a funkció lehetővé teszi a felhasználók számára a Wi-Fi profilok hitelesítését a bérlő új vagy meglévő PKCS-tanúsítványainak használatával. 

A Wi-Fi profilokkal kapcsolatos további információkért lásd: [Wi-Fi beállítások hozzáadása a Windows 10-es és újabb rendszerű eszközökhöz az Intune-ban](../configuration/wi-fi-settings-windows.md).

A következőkre vonatkozik:
- Windows 10 és újabb

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>Új ExchangeActiveSync-beállítások az e-mail-eszköz konfigurációs profiljának létrehozásakor iOS-eszközökön <!-- 4892824  --> 
IOS/iPadOS-eszközökön konfigurálhatja az e-mailek kapcsolatát egy eszköz konfigurációs profiljában (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/iPadOS** platform > **e-mailben** a profil típusa). 

Új ExchangeActiveSync-beállítások lesznek elérhetők, beleértve a következőket:
- Válassza ki a szinkronizálni kívánt szolgáltatásokat (vagy tiltsa le a szinkronizálást), például az e-maileket, a naptárat és a névjegyeket.
- Engedélyezi (vagy letiltja) a felhasználók számára ezen szolgáltatások szinkronizálási beállításainak módosítását az eszközön. 

Az aktuális beállítások megjelenítéséhez nyissa meg az [iOS-eszközök e-mail profiljának beállításait az Intune-ban](../configuration/email-settings-ios.md).

A következőkre vonatkozik:
- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>Személyes Google-fiókok hozzáadásának megakadályozása az Android Enterprise-eszközök tulajdonosa és dedikált eszközei számára <!-- 5353228  -->
Megakadályozhatja, hogy a felhasználók személyes Google-fiókokat hozzanak létre az Android Enterprise-eszköz tulajdonosán és dedikált eszközein (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **Android Enterprise** a platform > **eszköz tulajdonosa csak > eszköz korlátozásait** > **felhasználók és fiókok beállításait**) adja meg.

Az aktuálisan konfigurálható beállítások megjelenítéséhez nyissa meg az [androidos vállalati eszköz beállításait, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-android-for-work.md).

A következőkre vonatkozik:
- Androidos vállalati eszköz tulajdonosa
- Androidos vállalati dedikált eszközök

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>A Siri-parancsok beállításának kiszolgálóoldali naplózása el lesz távolítva az iOS-eszköz korlátozási profiljában <!-- 5468501  -->
Az iOS-eszközökön létrehozhat egy eszköz-korlátozási profilt, amely konfigurál egy kiszolgálóoldali naplózást a Siri-parancsokhoz (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/iPadOS** for platform > **Eszközök korlátozásai** a profil típusa > **beépített alkalmazások**). A **Siri-parancsok beállításának kiszolgálóoldali naplózása** el lesz távolítva.

Ez a beállítás el lesz távolítva az Intune felügyeleti konzolról. Ez a beállítás nincs hatással az eszközre annak ellenére, hogy a konfigurált beállításokkal rendelkező meglévő házirendek továbbra is megjelenítik a beállítást. Ha el szeretné távolítani a beállítást a meglévő szabályzatok közül, lépjen a szabályzatra, végezze el a másodlagos szerkesztést, mentse, és a szabályzat frissülni fog.

A konfigurálható beállítások megtekintéséhez tekintse meg az [iOS-és iPadOS-eszközök beállításait, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

A következőkre vonatkozik:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Az Autopilot-eszközökhöz tartozó eszköznév értékének szerkesztése<!-- 2640074  -->
Szerkesztheti az Azure AD-hez csatlakoztatott Autopilot-eszközökhöz tartozó eszköznév értékét. Ehhez nyissa meg az **Intune** > **eszközök beléptetése** > **Windows-regisztráció** > **Windows Autopilot** > **eszközöket** > Válassza ki az eszközt, > a jobb oldali ablaktáblában módosítsa az **eszköznév** értékét. > **Mentés**.


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>A csoport címke értékének szerkesztése az Autopilot-eszközökhöz<!-- 4816775 -->
Az Autopilot-eszközökhöz a **Group címke** értékét is szerkesztheti:

1. Válassza **az Intune** > **eszközök beléptetése** > **Windows-beléptetés** > **Windows Autopilot** > **eszközök**elemet.
1. Válassza ki az eszközt.
1. A jobb oldali ablaktáblán módosítsa a **csoport címke** értékét.
1. Válassza a **Mentés** lehetőséget.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>JAMF-felügyeletet igénylő macOS-felhasználói csoportok célzása <!-- 4061739 -->
A felhasználók meghatározott csoportjait megcélozhatja, hogy a macOS-eszközöket a JAMF kezelje. Ez a célzás lehetővé teszi, hogy a JAMF-megfelelőségi integrációt a macOS-eszközök egy részhalmazára alkalmazza, míg más eszközöket továbbra is az Intune kezel. A célzás azt is lehetővé teszi, hogy fokozatosan áttelepítse a felhasználók eszközeit egy mobileszköz-felügyeleti (MDM) rendszerről a másikra.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune-alkalmazások

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Továbbfejlesztett macOS-regisztrációs élmény Céges portál <!-- 5074349  -->
A macOS-regisztrálási élmény Céges portál egyszerűbb regisztrációs folyamattal fog rendelkezni, amely szorosabban igazodik a Céges portál iOS-es regisztrálási élményhez. Az eszköz felhasználói a következőket fogják látni:  

* Egy fényesebb felhasználói felület.  
* Továbbfejlesztett regisztrációs ellenőrzőlista.  
* Az eszközök regisztrálásával kapcsolatos tudnivalók.  
* Továbbfejlesztett hibaelhárítási beállítások.  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Továbbfejlesztett ellenőrzőlista-kialakítás az androidos Céges portál alkalmazásban<!-- 5550857  -->
Az Android rendszerhez készült Céges portál alkalmazásban a telepítési ellenőrzőlista egy könnyű kialakítással és új ikonokkal frissül. A módosítások összhangban lesznek az iOS rendszerhez készült Céges portál alkalmazás legújabb frissítéseivel.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Figyelés és hibaelhárítás

### <a name="updated-support-experience-------5012398------"></a>Frissített támogatási élmény   <!--  5012398    -->
A folyamatos fejlődés részeként frissíteni fogjuk a konzolon belüli támogatási élményt az Intune-ban.  Javítani fogjuk a konzolon belüli kereséseket és visszajelzéseket a gyakori problémák esetén, és a munkafolyamatot egyszerűsítjük, hogy kapcsolatba lépjenek a támogatási szolgálattal.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>Ismétlődő egyéni vagy beépített szerepkörök <!-- 1081938 -->
Lehetőség van a beépített és az egyéni szerepkörök másolására. Ehhez nyissa meg az **Intune** > **szerepkörök** > az **összes szerepkört** > válasszon egy szerepkört a listáról > **duplikálása**. Ügyeljen arra, hogy új nevet adjon meg, amely egyedi.

<!-- ***********************************************-->

## <a name="security"></a>Biztonság

### <a name="bitlocker-key-rotation--------2564951--------"></a>BitLocker-kulcs elforgatása     <!-- 2564951      -->
Az Intune-nal a Windows 1909-es vagy újabb verzióját futtató felügyelt eszközökön elforgathatja a BitLocker helyreállítási kulcsait. 

<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>További információ
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.
