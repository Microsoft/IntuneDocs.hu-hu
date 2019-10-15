---
title: A Microsoft Intune eszköz-felügyeleti képességei
description: Ebből a témakörből megtudhatja, hogyan segíthet az Intune a regisztrált eszközök kezelésében.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: bf862e59e135a875f5f18af731c581f3e5ea89d5
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306615"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>A Microsoft Intune regisztrált eszközök felügyeleti képességei

A Microsoft Intune lehetővé teszi, hogy a szolgáltatásba való *regisztrálással* különböző eszközöket kezeljen. Regisztrálhat bizonyos típusú eszközöket, vagy a felhasználók regisztrálhatnak a *Vállalati portál* alkalmazással. A regisztráció lehetővé teszi az alkalmazások tallózását és telepítését, gondoskodjon arról, hogy az eszközök megfeleljenek a vállalati házirendeknek, és kapcsolatba lépjenek az informatikai támogatási szolgálattal.

Ez a cikk az eszközök regisztrálását követően kapott funkciók teljes listáját tartalmazza.

A felügyeletet, a leltárt, az alkalmazások telepítését, a kiépítést és a kivonást egyaránt az Intune-ban kezeli a Azure Portal.

A felhasználók hozzáférést kapnak a vállalati portálhoz, amely lehetővé teszi az alkalmazások telepítését, az eszközök regisztrálását és eltávolítását, valamint az informatikai részleg vagy a segélyszolgálat elérhetőségét.



## <a name="device-security-and-configuration"></a>Eszköz biztonsága és konfigurációja

|Szolgáltatás|Részletek|További információ|
|--------------|-----------|--------------------|
|Konfigurációs szabályzatok<br><br>Egyéni szabályzatok| Lehetővé teszi a szervezeten belüli mobileszközök számos beállításának és funkciójának kezelését. Megkövetelheti például a jelszót, korlátozhatja a sikertelen próbálkozások számát, korlátozhatja a képernyő zárolása előtti időt, a jelszó lejáratát, és megakadályozhatja a korábban használt jelszavakat. A hardveres és szoftveres funkciók, például az eszköz kamera vagy a webböngésző használatát is szabályozhatja.<br><br>Egyéni szabályzatok használata, ha a konfigurációs házirendek nem tartalmazzák a szükséges beállításokat. IOS-eszközök esetén importálhatja az Apple konfigurátor eszközből exportált beállításokat. Más eszközök esetében az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállítások segítségével konfigurálhatja az eszköz beállításait és funkcióit.|[Az eszközök beállításainak és funkcióinak kezelése Microsoft Intune házirenddel](../protect/device-compliance-get-started.md)|
|Távoli törlés, távoli zárolás és PIN-kód alaphelyzetbe állítása|Bizalmas adatokat töröl az eszköz elvesztésekor vagy ellopásakor. Például távolról zárolhatja az eszközt, visszaállíthatja a gyári beállításokat, vagy törölheti csak a vállalati adatokból.<br><br>Alaphelyzetbe állíthatja a PIN-kódokat, ha a felhasználók elvesztik a hozzáférést az eszközhöz, zárolják az eltűnt vagy ellopott eszközöket, vagy törölhetik az adatokból a hiányzó vagy ellopott eszközökről.|Az eszközök védelmének biztosítása [távoli zárolás](../remote-actions/device-remote-lock.md) és [PIN-kód alaphelyzetbe állítása](../remote-actions/device-passcode-reset.md) révén|
|Teljes képernyős mód|Lehetővé teszi a mobileszközök bizonyos funkcióinak, például a képernyőfelvételek és a Power switchek zárolását. Azt is lehetővé teszi, hogy az eszközök egyetlen megadott alkalmazás futtatására legyenek korlátozva. |[az iOS-es konfigurációs házirend beállításai a Microsoft Intune](../configuration/device-restrictions-ios.md)|
|Autopilot alaphelyzetbe állítása|Feladatot küld az eszköznek, hogy távolról elindítsa az alaphelyzetbe állítási folyamatot, elkerülve annak szükségességét, hogy az informatikai munkatársak vagy más rendszergazdák felkeressék az egyes gépeket a folyamat elindításához. Ha az Autopilot alaphelyzetbe állítását egy eszközön használja, az eszköz elsődleges felhasználója el lesz távolítva. A következő felhasználó, aki az Alaphelyzetbe állítás után bejelentkezik, elsődleges felhasználóként lesz beállítva.|[Távoli Windows Autopilot alaphelyzetbe állítása](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)|

## <a name="app-management"></a>Alkalmazások kezelése

|Szolgáltatás|Részletek|További információ|
|--------------|-----------|--------------------|
|Alkalmazások központi telepítése és kezelése|Számos eszközt biztosít a mobileszközök életcikluson keresztüli kezeléséhez, beleértve a telepítési fájlokból és az alkalmazás-áruházakból származó alkalmazások telepítését, az alkalmazások állapotának részletes figyelését és az alkalmazások eltávolítását.|[Alkalmazások telepítése Microsoft Intune](../apps/apps-deploy.md)|
|Megfelelő és nem megfelelő alkalmazások|Lehetővé teszi, hogy megadhatja a megfelelő alkalmazások (a felhasználók által telepíthető) és a nem megfelelő alkalmazások (a felhasználók által nem telepíthető) listáját.|[iOS-szabályzat beállításai a Microsoft Intune](../configuration/device-restrictions-ios.md)|
|Mobile Application Management|Az alkalmazásokra vonatkozó korlátozásokat az Intune-nal felügyelt és az Intune-nal nem felügyelt összes eszközön a mobileszköz-felügyelet használatával konfigurálja. A vállalati adatok biztonságát a műveletek, például a másolás és beillesztés, az adatok külső biztonsági mentése és az alkalmazások közötti adatátvitel korlátozásával növelheti.|[A mobileszköz-kezelési házirendek konfigurálása és telepítése a Microsoft Intune-konzolon](../developer/app-wrapper-prepare-android.md)|
|iOS-alapú Mobile App-konfiguráció|A a Mobile App konfigurációs házirendjeivel adja meg az iOS-alkalmazások beállításait, amelyekre szükség lehet, amikor a felhasználó futtatja az alkalmazást. Előfordulhat például, hogy egy alkalmazás portszám vagy bejelentkezési adatok megadását kéri a felhasználótól. Egyszerűsítheti az alkalmazások konfigurációját, és csökkentheti a támogatási hívások számát.|[IOS-alkalmazások konfigurálása a Mobile App konfigurációs házirendjeivel Microsoft Intune](../apps/app-configuration-policies-use-ios.md)|
|iOS Mobile App kiépítési profilok|Segítséget nyújt a kiépítési profilok üzembe helyezéséhez a közeljövőben lejáró iOS-alkalmazásokhoz. |[IOS Mobile-alapú kiépítési profilok használata az alkalmazások lejáratának megakadályozása érdekében](../apps/app-provisioning-profile-ios.md)|
|Felügyelt böngésző|A Managed Browser-szabályzatok konfigurálásával szabályozhatja azokat a webhelyeket, amelyeket az eszköz felhasználói megkereshetnek. Emellett a felügyelt böngészőre is alkalmazhat Mobile Application Management-házirendeket.|[Internet-hozzáférés kezelése Managed Browser-szabályzatokkal a Microsoft Intune használatával](../apps/app-configuration-managed-browser.md)|
|Vállalati Windows Hello|Lehetővé teszi az integrációt a Windows Hello for Business szolgáltatással, amely egy alternatív bejelentkezési módszer a Windows 10 rendszerhez, amely helyszíni Active Directory vagy Azure Active Directory használ a jelszavak, intelligens kártyák vagy virtuális intelligens kártyák helyett.|[A vállalati Windows Hello beállításainak szabályozása az eszközökön Microsoft Intune](../protect/windows-hello.md)|
|Mennyiségi licencszerződés keretében vásárolt alkalmazások|Segít a mennyiségi vásárlási program keretében vásárolt alkalmazások kezelésében. Ehhez importálja a licenceket az App Store áruházból, nyomon követi, hogy hány licencet használt fel, és meggátolja, hogy több példányt telepítsen az alkalmazásból, mint amennyit a tulajdonosa.|[Mennyiségi programban vásárolt alkalmazások felügyelete Microsoft Intune használatával](../apps/vpp-apps.md)|

## <a name="company-resource-access"></a>Vállalati erőforrás-hozzáférés

|Szolgáltatás|Részletek|További információ|
|--------------|-----------|--------------------|
|Tanúsítvány-profilok|Megbízható tanúsítvány-és Egyszerű tanúsítványigénylési protokoll-(SCEP-) tanúsítványokat hoz létre és telepít, amelyek segítségével biztonságossá teheti és hitelesítheti a Wi-Fi-, VPN-és e-mail-profilokat.|[Az erőforrások biztonságos elérése a Microsoft Intune tanúsítványprofiljai segítségével](../protect/certificates-configure.md)|
|Wi-Fi profilok|A vezeték nélküli hálózati beállításokat telepíti a felhasználók számára. Ezeknek a beállításoknak a központi telepítésével minimálisra csökkenthető a vállalati hálózathoz való kapcsolódáshoz szükséges felhasználói erőfeszítés.|[Wi-Fi-kapcsolatok a Microsoft Intune-ban](../configuration/wi-fi-settings-configure.md)|
|E-mail profilok|E-mail-beállításokat hoz létre és helyez üzembe az eszközökön, így a felhasználók a saját eszközein anélkül érhetik el a vállalati e-maileket, hogy azok megadják a szükséges beállításokat|[Vállalati levelezéshez való hozzáférés konfigurálása e-mail-profilokkal a Microsoft Intune-ban](../configuration/email-settings-configure.md)|
|VPN-profilok|VPN-beállításokat helyez üzembe a szervezet felhasználói és eszközei számára. Ezeknek a beállításoknak a központi telepítésével minimálisra csökkenthető a vállalati hálózaton lévő erőforrásokhoz való kapcsolódáshoz szükséges felhasználói erőfeszítés.|[VPN-kapcsolatok a Microsoft Intune-ban](../configuration/device-profiles.md#vpn)|
|Feltételes hozzáférési szabályzatok|A a Microsoft Exchange e-mailekhez és a SharePoint Online-hoz való hozzáférést a nem az Intune által felügyelt eszközökön kezeli.|[Az e-mailek és a SharePoint elérésének korlátozása Microsoft Intune](../protect/app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Következő lépések

[Tekintse meg a felügyelhető eszközök listáját](../remote-actions/device-management.md).
