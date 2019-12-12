---
title: A Microsoft Intune eszköz-felügyeleti képességei
description: Ebből a témakörből megtudhatja, hogyan segíthet az Intune kezelni az Ön által regisztrált mobileszközöket.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64df7ccad203109c201b0e18c3d20023690e31aa
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503229"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>A Microsoft Intune regisztrált eszközök kezelésével kapcsolatos képességei

A Microsoft Intune segítségével sokféle eszközt kezelhet úgy, hogy *regisztrálja* őket a szolgáltatásban. Egyes eszköztípusokat regisztrálhat saját maga, vagy regisztrálhatják a felhasználók a *Vállalati portál* alkalmazással. A regisztráció lehetővé teszi az alkalmazások tallózását és telepítését, gondoskodjon arról, hogy az eszközök megfeleljenek a vállalati házirendeknek, és kapcsolatba lépjenek az informatikai támogatási szolgálattal.

Ez a cikk az eszközök regisztrálását követően kapott funkciók teljes listáját tartalmazza.

A felügyeletet, a leltárt, az alkalmazások telepítését, a kiépítést és a kivonást egyaránt az Intune-ban kezeli a Azure Portal.

A felhasználók hozzáférést kapnak a vállalati portálhoz, és ennek segítségével alkalmazásokat telepíthetnek, eszközöket regisztrálhatnak vagy távolíthatnak el, és segítségért az informatikai osztályhoz vagy a segélyszolgálathoz fordulhatnak.



## <a name="device-security-and-configuration"></a>Eszközvédelem és -beállítás

|Képesség|Details|További információ|
|--------------|-----------|--------------------|
|Konfigurációs szabályzatok<br><br>Egyéni házirendek| Lehetővé teszi számos beállítás és funkció kezelését a szervezethez tartozó mobileszközökön. Például megkövetelheti jelszó használatát, korlátozhatja a sikertelen bejelentkezési kísérletek számát, megadhatja, hogy a képernyő hány perc után zárolódjon, beállíthatja a jelszó lejárati idejét, és letilthatja a korábban használt jelszavak ismételt használatát. Szabályozhatja továbbá a hardveres és szoftveres funkcióknak (például az eszköz kamerájának és a webböngészőnek) a használatát.<br><br>Egyéni szabályzatok használata, ha a konfigurációs házirendek nem tartalmazzák a szükséges beállításokat. iOS-eszközök esetén importálhatja az Apple Configurator eszközből exportált beállításokat. Más eszközök esetében az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállítások segítségével konfigurálhatja a beállításokat és a szolgáltatásokat az eszközön.|[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](../protect/device-compliance-get-started.md)|
|Távoli törlés, távoli zárolás és PIN-kód alaphelyzetbe állítása|Az eszköz elvesztése vagy eltulajdonítása esetén törli a bizalmas adatokat. Távolról zárolhatja például az eszközt, visszaállíthatja a gyári beállításokat vagy törölheti csak a vállalati adatokat.<br><br>Ha a felhasználók nem tudnak hozzáférni egy eszközhöz, alaphelyzetbe állíthatja a PIN-kódokat, zárolhatja az eltűnt vagy ellopott eszközöket, vagy törölhet róluk minden adatot.|Az eszközök védelmének biztosítása [távoli zárolás](../remote-actions/device-remote-lock.md) és [PIN-kód alaphelyzetbe állítása](../remote-actions/device-passcode-reset.md) révén|
|Teljes képernyős mód|Lehetővé teszi a mobileszközök bizonyos funkciói, például a képernyőfelvétel-készítés és a kikapcsolás zárolását. Emellett az eszközt egyetlen meghatározott alkalmazás futtatására korlátozhatja. |[iOS-eszközök konfigurációs házirendjének beállításai a Microsoft Intune-ban](../configuration/device-restrictions-ios.md)|
|Autopilot alaphelyzetbe állítása|Feladatot küld az eszköznek, hogy távolról elindítsa az alaphelyzetbe állítási folyamatot, elkerülve annak szükségességét, hogy az informatikai munkatársak vagy más rendszergazdák felkeressék az egyes gépeket a folyamat elindításához. Ha az Autopilot alaphelyzetbe állítását egy eszközön használja, az eszköz elsődleges felhasználója el lesz távolítva. A következő felhasználó, aki az Alaphelyzetbe állítás után bejelentkezik, elsődleges felhasználóként lesz beállítva.|[Távoli Windows Autopilot alaphelyzetbe állítása](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)|

## <a name="app-management"></a>Alkalmazáskezelés

|Képesség|Details|További információ|
|--------------|-----------|--------------------|
|Alkalmazások telepítése és kezelése|Számos eszközt kínál, amelyek segítségével kezelheti a mobilalkalmazásokat teljes életciklusukon keresztül, beleértve a telepítési fájlokból és alkalmazás-áruházakból történő telepítést, az alkalmazás állapotának részletes megfigyelését, valamint az alkalmazás eltávolítását.|[Alkalmazások telepítése a Microsoft Intune-ban](../apps/apps-deploy.md)|
|Megfelelő és nem megfelelő alkalmazások|Lehetővé teszi a szabályzatnak megfelelő (így a felhasználók által telepíthető) és nem megfelelő (így a felhasználók által nem telepíthető) alkalmazások listájának megadását.|[iOS-szabályzatbeállítások a Microsoft Intune-ban](../configuration/device-restrictions-ios.md)|
|Mobilalkalmazás-kezelés|A mobilalkalmazás-felügyelet révén korlátozásokat konfigurálhat az alkalmazásokra vonatkozóan az Intune-nal kezelt eszközökre és a nem az Intune-nal kezelt eszközökre egyaránt. A vállalati adatok biztonságát a műveletek, például a másolás és beillesztés, az adatok külső biztonsági mentése és az alkalmazások közötti adatátvitel korlátozásával növelheti.|[Mobilalkalmazás-kezelési házirendek konfigurálása és telepítése a Microsoft Intune-konzolon](../developer/app-wrapper-prepare-android.md)|
|iOS-mobilalkalmazás konfigurálása|A mobilalkalmazás-konfigurációs szabályzatokkal automatikusan megadhatja azokat a beállításokat, amelyekre szükség lehet, amikor egy felhasználó egy iOS-alkalmazást futtat. Előfordulhat például, hogy az alkalmazás portszám vagy bejelentkezési beállítások megadását kéri a felhasználótól. Egyszerűsítheti az alkalmazások konfigurációját, és csökkentheti a támogatási hívások számát.|[iOS-alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek segítségével a Microsoft Intune-ban](../apps/app-configuration-policies-use-ios.md)|
|iOS-mobilalkalmazás létesítési profiljai|Segít létesítési profilokat telepíteni a lejárathoz közelítő iOS-alkalmazásokhoz. |[Az iOS-mobileszközös létesítésiprofil-szabályzatok segítségével megakadályozhatja, hogy az alkalmazásai lejárjanak](../apps/app-provisioning-profile-ios.md)|
|Felügyelt böngésző|Konfigurálja a felügyeltböngésző-szabályzatokat, amelyekkel szabályozható, hogy az eszköz felhasználói mely webhelyeket látogathatják meg. Emellett mobilalkalmazás-kezelési házirendeket is alkalmazhat a felügyelt böngészőre.|[Az internet-hozzáférés felügyelt böngészőszabályzatokkal való kezelése a Microsoft Intune-ban](../apps/app-configuration-managed-browser.md)|
|Vállalati Windows Hello|Lehetővé teszi az integrációt a Vállalati Windows Hello nevű, a Windows 10-ben használható alternatív bejelentkezési módszerrel. Ez a helyi Active Directoryt vagy az Azure Active Directoryt használja jelszavak, intelligens kártyák vagy virtuális intelligens kártyák helyett.|[A Vállalati Windows Hello beállításainak szabályozása az eszközökön a Microsoft Intune-nal](../protect/windows-hello.md)|
|Mennyiségi licencszerződés keretében vásárolt alkalmazások|Segít a mennyiségi licencszerződés keretében vásárolt alkalmazások felügyeletében. Ehhez importálja a licencadatokat az App Store áruházból, figyelemmel kíséri, hogy hány licencet használt fel, és meggátolja, hogy több alkalmazáspéldányt telepítsen, mint amennyit vásárolt.|[Mennyiségi programban vásárolt alkalmazások felügyelete a Microsoft Intune-nal](../apps/vpp-apps.md)|

## <a name="company-resource-access"></a>Vállalati erőforrások elérése

|Képesség|Details|További információ|
|--------------|-----------|--------------------|
|Tanúsítványprofilok|Létrehozhat és telepíthet megbízhatótanúsítvány-profilokat és egyszerű tanúsítványigénylési protokollon (SCEP) alapuló tanúsítványokat, amelyek segítségével biztonságossá teheti és hitelesítheti a Wi-Fi-, VPN- és e-mail-profilokat.|[Az erőforrások biztonságos elérése a Microsoft Intune tanúsítványprofiljai segítségével](../protect/certificates-configure.md)|
|Wi-Fi profilok|Vezeték nélküli hálózati beállításokat léptethet érvénybe a felhasználók számára. E beállítások érvénybe léptetésével csökkentheti a vállalati hálózat eléréséhez szükséges felhasználói beavatkozást.|[Wi-Fi-kapcsolatok a Microsoft Intune-ban](../configuration/wi-fi-settings-configure.md)|
|E-mail profilok|E-mail-beállításokat hoz létre és helyez üzembe az eszközökön, így a felhasználók a saját eszközein anélkül érhetik el a vállalati e-maileket, hogy azok megadják a szükséges beállításokat|[Vállalati levelezéshez való hozzáférés konfigurálása e-mail profilokkal a Microsoft Intune-ban](../configuration/email-settings-configure.md)|
|VPN-profilok|VPN-beállításokat léptethet érvénybe a szervezethez tartozó felhasználók és eszközök számára. A beállítások központi telepítésével csökkentheti a vállalati hálózatban lévő erőforrások eléréséhez szükséges felhasználói beavatkozást.|[VPN-kapcsolatok a Microsoft Intune-ban](../configuration/device-profiles.md#vpn)|
|Feltételes hozzáférési szabályzatok|A Microsoft Exchange-levelezéshez és a SharePoint Online-hoz való hozzáférés felügyelete a nem az Intune által felügyelt eszközökön.|[Az e-mailek és a SharePoint elérésének korlátozása a Microsoft Intune használatával](../protect/app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>További lépések

[Tekintse meg a felügyelhető eszközök listáját](../remote-actions/device-management.md).
