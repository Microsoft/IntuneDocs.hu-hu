---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 796439581ca0ae91e788a91ab0bc2ef8f6019626
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199343"
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

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>iOS-felhasználó által licencelt VPP-alkalmazások<!-- 5619268 idready -->
A felhasználók beléptetésére szolgáló iOS-eszközök esetében a végfelhasználók többé nem fognak megjelenni a rendelkezésre álló, eszközre licencelt VPP-alkalmazásokkal. A végfelhasználók azonban továbbra is láthatják az összes felhasználó által licencelt VPP-alkalmazást a Céges portálon belül. További információ a VPP-alkalmazásokról: [Apple Volume Purchase program által vásárolt iOS-és MacOS-alkalmazások kezelése Microsoft Intune használatával](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>Személyes helyreállítási kulcs beolvasása a MEM titkosított macOS-eszközökről<!-- 4851745 idready -->
A végfelhasználók a saját helyreállítási kulcsát (FileVault-kulcs) az iOS Céges portál alkalmazás használatával tudják lekérni. A személyes helyreállítási kulccsal rendelkező eszközt regisztrálni kell az Intune-ban, és az Intune-on keresztül kell titkosítani a FileVault-mel. Az iOS Céges portál alkalmazás használatával a végfelhasználó megnyithatja a Safari webes nézetét, és lekérheti a személyes helyreállítási kulcsát. Az Intune-ban válassza az **eszközök** > *a titkosított és regisztrált macOS-eszköz > a* **helyreállítási kulcs beszerzése**lehetőséget. További információ a FileVault: FileVault- [titkosítás MacOS rendszerhez](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="microsoft-app-icons-update--4677605--"></a>Microsoft-alkalmazás ikonjainak frissítése<!--4677605-->
Az alkalmazás-védelmi házirendek és az alkalmazás-konfigurációs házirendek alkalmazás-célcsoportok ablaktábláján a Microsoft-alkalmazásokhoz használt ikonok frissülnek.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>S/MIME-támogatás a Microsoft Outlook Mobile-hoz<!-- 2669398  -->
Az Intune támogatja az olyan S/MIME-aláírási és titkosítási tanúsítványok továbbítását, amelyek az Outlook Mobile-ban iOS és Android rendszereken is használhatók. Kapcsolódó információk: [iOS-eszközök e-mail-beállításai](~/configuration/email-settings-ios.md) és [e-mail-beállítások Android-eszközökhöz](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>Egyéni beállítások macOS-alkalmazások támogatása<!-- 4736278  -->
Az Intune támogatni fogja az egyéni beállításokat, így adott kulcsokat és értékeket adhat hozzá egy meglévő Preferences (. plist) fájlhoz a macOS-alkalmazások és az eszköz konfigurálásához. Nem minden alkalmazás támogatja a felügyelt beállításokat, és bizonyos esetekben csak bizonyos beállítások kezelhetők. A beállítások csak az eszköz csatornán keresztül lesznek telepítve. Csak az eszköz csatornájának beállításait tároló. xml kiterjesztésű fájlokat vagy. xml fájlokat kell feltöltenie.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Értesítések megjelenítése a Windows Céges portál alkalmazásához<!-- 1808082  -->
A Windows-eszközökön a Céges portál alkalmazást frissítjük a bejelentési értesítések megjelenítéséhez a felhasználók számára, még akkor is, ha az alkalmazás be van zárva. A frissítés csak akkor jeleníti meg az elérhető alkalmazások értesítéseit, ha a telepítés állapota befejeződött vagy sikertelen. A Céges portál alkalmazás nem jeleníti meg az értesítéseket a szükséges alkalmazásokhoz.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>A Céges portál alkalmazás telepítési állapotüzenetek megjelenítése<!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz<!-- 2576686 -->
Az Intune alkalmazás Android-és iOS-eszközökön lehetővé teszi az alkalmazások értesítési tartalmának vezérlését a szervezeti fiókok számára. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy az összes APP-kompatibilis alkalmazáshoz nem érhető el. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>A tanúsítvány hitelesítő adatainak a felügyelt tárolóban való konfigurálásának tiltása a felhasználók számára az Android Enterprise-eszközök tulajdonosi eszközein<!-- 3311998 idready -->
Az androidos vállalati eszközök tulajdonosi eszközein új beállítás jelenik meg, amely letiltja a felhasználók számára a tanúsítvány hitelesítő adatainak konfigurálását a felügyelt tárolóban (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **Android enterprise** for platform > **eszköz tulajdonosa csak >-eszközök korlátozásai** a profil típusa > **felhasználók + fiókok**).

Az aktuális beállítások megtekintéséhez lépjen az [Android Enterprise Device Settings elemre az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-android-for-work.md).

Érintett kiadások:
- Androidos vállalati eszköz tulajdonosa, beleértve a dedikált és teljes mértékben felügyelt eszközöket

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>Vezetékes hálózati eszközök konfigurációs profiljai macOS-eszközökhöz<!-- 3508686 idready -->
MacOS-eszközökön a jövőbeli frissítés tartalmazni fog egy új konfigurációs profilt, amely a vezetékes hálózatokat (az**eszköz konfigurációját** > **profilokat** > a **profil létrehozása** > **MacOS** platformon > **vezetékes hálózat** profil típusa) beállítására. Ezzel a szolgáltatással 802.1 x-profilokat hozhat létre a vezetékes hálózatok kezeléséhez, és ezeket a vezetékes hálózatokat a macOS-eszközökre is üzembe helyezheti.

Érintett kiadások:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Automatikus proxybeállítások hozzáadása Wi-Fi profilokhoz androidos vállalati munkahelyi profilokhoz<!-- 4490822 idready -->
Az Android Enterprise munkahelyi profil eszközein Wi-Fi profilok hozhatók létre. Ha a Wi-Fi Enterprise-típust választja, megadhatja a Wi-Fi-hálózaton használt bővíthető hitelesítési protokoll (EAP) típusát is.

Egy jövőbeli frissítés esetében, ha a vállalat típusát választja, megadhatja az automatikus proxybeállításokat, beleértve a proxykiszolgáló URL-címét, például a `proxy.contoso.com`.

A konfigurálható aktuális Wi-Fi beállítások megjelenítéséhez nyissa meg a [Wi-Fi beállítások hozzáadása az Android Enterprise és az Android kioszkot futtató eszközökhöz Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Érintett kiadások:
- Androidos vállalati munkahelyi profil

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>A hálózati hozzáférés-vezérlés (NAC) engedélyezése a Cisco AnyConnect VPN-sel iOS-eszközökön<!-- 4860111 idready -->
IOS-eszközökön létrehozhat egy VPN-profilt, és különböző kapcsolattípust használhat, beleértve a Cisco AnyConnect-t (az**eszköz konfigurációjának** > **profiljait** , > **profil létrehozása** > **iOS** for platform > **VPN** a profil típusa > **Cisco AnyConnect** for kapcsolattípus). 

A jövőbeli frissítésekben engedélyezheti a hálózati hozzáférés-vezérlést (NAC) a Cisco AnyConnect. A szolgáltatás használata:

1. A [Cisco Identity Services Engine rendszergazdai útmutatójában](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)a Cisco Identity Services Engine (ISE) az Azure-ban való konfigurálásához kövesse az **Microsoft Intune konfigurálása Mdm-kiszolgálóként** című témakör lépéseit.
2. Az Intune-eszköz konfigurációs profiljában válassza a **hálózati Access Control engedélyezése (NAC)** beállítást.

Az összes rendelkezésre álló VPN-beállítás megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS-eszközökön](../configuration/vpn-settings-ios.md)című témakört.

Érintett kiadások:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>Az iOS-, iPadOS-és macOS-eszközökön futó alkalmazásokhoz és webhelyekhez készült egyszeri bejelentkezések frissítése<!-- 4999578 idready -->
Az Intune további egyszeri bejelentkezési beállításokat ad hozzá az iOS-, iPadOS-és macOS-eszközökhöz. Jelenleg az Intune-ban konfigurálhatja a hitelesítő adatok egyszeri bejelentkezéses alkalmazásának bővítményeit és az Apple beépített Kerberos-bővítményét. Egy későbbi frissítés során konfigurálhatja a szervezete vagy az identitás-szolgáltatója által írt átirányítási SSO-alkalmazások bővítményeit. 

Ezekkel a beállításokkal zökkenőmentes egyszeri bejelentkezést állíthat be a modern hitelesítési módszereket (például OAuth és egy SAML2) használó alkalmazásokhoz és webhelyekhez. 

Az egyszeri bejelentkezéses alkalmazás kiterjesztésére vonatkozó beállítások megjelenítéséhez nyissa meg az SSO-t [iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) -en és [SSO-on MacOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)rendszeren.

Érintett kiadások:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Jóváhagyott billentyűzetek használatának megkövetelése Androidon<!--4761794 IDready -->
Megadhatja a felügyelt Android-alkalmazásokban használható jóváhagyott billentyűzetek listáját. A felügyelt alkalmazásból a rendszer kérni fogja a felhasználótól, hogy váltson az eszközön már telepített jóváhagyott billentyűzetekre, vagy ha szükséges, a rendszer a jóváhagyott billentyűzetek egyikének letöltéséhez és beállításához irányítja a Google Play Áruház. A felhasználó csak akkor szerkesztheti a szövegmezőket egy felügyelt alkalmazásban, ha az aktív billentyűzet a jóváhagyott billentyűzetek egyike.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>PKCS-tanúsítványok használata Wi-Fi profilokkal Windows 10 és újabb rendszerű eszközökön<!-- 3246388  -->
Jelenleg a SCEP-tanúsítványokkal rendelkező Windows Wi-Fi-profilokat hitelesítheti (az**eszköz konfigurációjának** > **profiljai** > a **profil létrehozása** > **Windows 10 és újabb verziók** a platform > **Wi-Fi** profil típusa > **Enterprise** > **EAP-típus**). A PKCS-tanúsítványokat használhatja a Windows Wi-Fi profiljaival. Ez a funkció lehetővé teszi a felhasználók számára a Wi-Fi profilok hitelesítését a bérlő új vagy meglévő PKCS-tanúsítványainak használatával. 

A Wi-Fi profilokkal kapcsolatos további információkért lásd: [Wi-Fi beállítások hozzáadása a Windows 10-es és újabb rendszerű eszközökhöz az Intune-ban](../configuration/wi-fi-settings-windows.md).

Érintett kiadások:
- Windows 10 és újabb

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>Új ExchangeActiveSync-beállítások az e-mail-eszköz konfigurációs profiljának létrehozásakor iOS-eszközökön<!-- 4892824  --> 
IOS-/iPadOS-eszközökön konfigurálhatja az e-mailek kapcsolatát egy eszköz konfigurációs profiljában (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/IPadOS** a platform > **e-mail-** profil típusa). 

Új ExchangeActiveSync-beállítások lesznek elérhetők, beleértve a következőket:
- Válassza ki a szinkronizálni kívánt szolgáltatásokat (vagy tiltsa le a szinkronizálást), például az e-maileket, a naptárat és a névjegyeket.
- Engedélyezi (vagy letiltja) a felhasználók számára ezen szolgáltatások szinkronizálási beállításainak módosítását az eszközön. 

Az aktuális beállítások megjelenítéséhez nyissa meg az [iOS-eszközök e-mail profiljának beállításait az Intune-ban](../configuration/email-settings-ios.md).

Érintett kiadások:
- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Személyes Google-fiókok hozzáadásának megakadályozása az Android Enterprise-eszközök tulajdonosa és dedikált eszközei számára<!-- 5353228  -->
Megakadályozhatja, hogy a felhasználók személyes Google-fiókokat hozzanak létre az androidos vállalati eszköz tulajdonosának és dedikált eszközeinek (az**eszköz konfigurációjának** > **profiljai** > **profil létrehozása** > **Android enterprise** for platform > **eszköz tulajdonosa csak > eszközök korlátozásai** a profil típusa > **felhasználók és fiókok beállításai**).

Az aktuálisan konfigurálható beállítások megjelenítéséhez nyissa meg az [androidos vállalati eszköz beállításait, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-android-for-work.md).

Érintett kiadások:
- Androidos vállalati eszköz tulajdonosa
- Androidos vállalati dedikált eszközök

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>A Siri-parancsok beállításának kiszolgálóoldali naplózása el lesz távolítva az iOS-eszköz korlátozási profiljában<!-- 5468501  -->
IOS-eszközökön létrehozhat egy eszköz-korlátozási profilt, amely a Siri-parancsok kiszolgálóoldali naplózását konfigurálja (**eszköz-konfiguráció** > **profilok** > **profil létrehozása** > **iOS/iPadOS** for platform > **eszközre vonatkozó korlátozások** a profil típusa > **beépített alkalmazások**). A **Siri-parancsok beállításának kiszolgálóoldali naplózása** el lesz távolítva.

Ez a beállítás el lesz távolítva az Intune felügyeleti konzolról. Ez a beállítás nincs hatással az eszközre annak ellenére, hogy a konfigurált beállításokkal rendelkező meglévő házirendek továbbra is megjelenítik a beállítást. Ha el szeretné távolítani a beállítást a meglévő szabályzatok közül, lépjen a szabályzatra, végezze el a másodlagos szerkesztést, mentse, és a szabályzat frissülni fog.

A konfigurálható beállítások megtekintéséhez tekintse meg az [iOS-és iPadOS-eszközök beállításait, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

Érintett kiadások:
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés



### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Az Autopilot-eszközökhöz tartozó eszköznév értékének szerkesztése<!-- 2640074  -->
Szerkesztheti az Azure AD-hez csatlakoztatott Autopilot-eszközökhöz tartozó eszköznév értékét. Ehhez nyissa meg az **Intune** > **eszközök beléptetése** > **Windows-regisztráció** > **Windows Autopilot** > **eszközöket** > Válassza ki az eszközt, > a jobb oldali ablaktáblában módosítsa az **eszköznév** értékét > **Mentés**gombra.

### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>A csoport címke értékének szerkesztése az Autopilot-eszközökhöz<!-- 4816775 -->
Az Autopilot-eszközökhöz a **Group címke** értékét is szerkesztheti:

1. Válassza az **Intune** > eszközök **beléptetése** > **Windows-regisztráció** > **Windows Autopilot** > **eszközöket**.
1. Válassza ki az eszközt.
1. A jobb oldali ablaktáblán módosítsa a **csoport címke** értékét.
1. Válassza a **Mentés** lehetőséget.

### <a name="target-macos-user-groups-to-require-jamf-management---4061739---"></a>JAMF-felügyeletet igénylő macOS-felhasználói csoportok célzása<!-- 4061739 -->
A felhasználók meghatározott csoportjait megcélozhatja, hogy a macOS-eszközöket a JAMF kezelje. Ez a célzás lehetővé teszi, hogy a JAMF-megfelelőségi integrációt a macOS-eszközök egy részhalmazára alkalmazza, míg más eszközöket továbbra is az Intune kezel. A célzás azt is lehetővé teszi, hogy fokozatosan áttelepítse a felhasználók eszközeit egy mobileszköz-felügyeleti (MDM) rendszerről a másikra.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune-alkalmazások

### <a name="improved-macos-enrollment-experience-in-company-portal---5074349----"></a>Továbbfejlesztett macOS-regisztrációs élmény Céges portál<!-- 5074349  -->
A macOS-regisztrálási élmény Céges portál egyszerűbb regisztrációs folyamattal fog rendelkezni, amely szorosabban igazodik a Céges portál iOS-es regisztrálási élményhez. Az eszköz felhasználói a következőket fogják látni:  

* Egy fényesebb felhasználói felület.  
* Továbbfejlesztett regisztrációs ellenőrzőlista.  
* Az eszközök regisztrálásával kapcsolatos tudnivalók.  
* Továbbfejlesztett hibaelhárítási beállítások.  

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Figyelés és hibaelhárítás

### <a name="centralized-audit-logs--5603185-5697164--"></a>Központi naplók<!--5603185, 5697164-->
Az új központosított naplózási felület az összes kategória naplóit egyetlen lapra gyűjti. A you'l képesnek kell lennie szűrni a naplókat, hogy megkapják a keresett adatgyűjtést. A naplók megtekintéséhez lépjen a **bérlői adminisztráció** > **naplók**elemre. További információ: a [naplók jövőbeli változása az Intune-ban](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858).

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

### <a name="duplicate-custom-or-built-in-roles---1081938---"></a>Ismétlődő egyéni vagy beépített szerepkörök<!-- 1081938 -->
Lehetőség van a beépített és az egyéni szerepkörök másolására. Ehhez nyissa meg az **Intune** > **szerepkörök** > az **összes szerepkört** > válasszon egy szerepkört a listáról > **duplikálása**. Ügyeljen arra, hogy új nevet adjon meg, amely egyedi.

<!-- ***********************************************-->

## <a name="security"></a>Biztonság

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>Tanúsítványokat tartalmazó eszközök kiépítése PKCS-tanúsítványok használatával<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
A PKCS-tanúsítvány profil használatával tanúsítványokat állíthat ki az eszközök számára, így kiterjesztheti a felhasználó-alapú tanúsítványok aktuális támogatását. Az eszköz alapú tanúsítványok támogatottak lesznek az Android, iOS és Windows platformokon, és Wi-Fi-és VPN-profilokhoz is használhatók.

<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.


