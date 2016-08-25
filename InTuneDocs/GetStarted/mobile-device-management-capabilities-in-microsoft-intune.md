---
title: "Mobileszköz-kezelési képességek | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: 0f460165f251acf95f4af36afa39409d3eb21162


---
# A Microsoft Intune mobileszköz-kezelési képességei

A Microsoft Intune segítségével sokféle eszközt kezelhet úgy, hogy *regisztrálja* őket a szolgáltatásban. A felhasználók ezt követően sokféle műveletet végezhetnek el a *vállalati portál* segítségével: regisztrálhatják az alkalmazásokat, válogathatnak az alkalmazások közül, telepíthetik őket, ellenőrizhetik, hogy megfelel-e az eszközük a vállalat szabályzatainak, és az informatikai támogatási munkatársakhoz fordulhatnak.
Ez a témakör minden olyan előnyt felsorol, amely az eszközök regisztrálásából ered.

A felügyeletet, a leltárt, az alkalmazások telepítését, a létesítést és a használatból való kivonást egyaránt az Intune felügyeleti konzoljával lehet kezelni. A felhasználók hozzáférést kapnak a vállalati portálhoz, és ennek segítségével telepíthetik az alkalmazásokat, regisztrálhatják és távolíthatják el eszközeiket, és ugyancsak a portál segítségével fordulhatnak informatikai osztályukhoz vagy segélyszolgálatukhoz.



## Eszközvédelem és -beállítás

|Képesség|Részletek|További információ|
|--------------|-----------|--------------------|
|Beállítási házirendek<br><br>Egyéni házirendek|A mobileszközök konfigurációs házirendjei segítségével számos beállítást és funkciót kezelhet a szervezethez tartozó mobileszközökön. Például megkövetelheti a jelszó használatát, korlátozhatja a sikertelen bejelentkezési kísérletek számát, azt, hogy a képernyő hány perc után zárolódjon, beállíthatja a jelszó lejárati idejét, és letilthatja az előzőleg használt jelszavakat. Továbbá szabályozhatja a hardveres és szoftveres funkcióknak (például az eszköz kamerájának és a webböngészőnek) a használatát.<br><br>Az egyéni házirendeket akkor használja, ha a konfigurációs házirendek nem tartalmazzák a kívánt beállítást. iOS-eszközök esetén importálhatja az Apple Configurator Tool eszközből exportált beállításokat. Más eszközök esetében az OMA-URI beállítások segítségével konfigurálhatja a beállításokat és a szolgáltatásokat az eszközön.|[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|Távoli törlés, távoli zárolás és PIN-kód alaphelyzetbe állítása|Törölheti a bizalmas adatokat, ha az eszközt elveszíti vagy ellopják. Távolról zárolhatja például az eszközt, visszaállíthatja a gyári beállításokat vagy törölheti csak a vállalati adatokat.<br>Ha a felhasználók nem tudnak hozzáférni egy eszközhöz, alaphelyzetbe állíthatja a PIN-kódokat, zárolhatja az eltűnt vagy ellopott eszközöket, vagy törölhet róluk minden adatot.|[Távoli zárolással és a PIN-kód alaphelyzetbe állításával védheti az eszközöket](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune), illetve [kivonhatja az eszközöket az Intune felügyelete alól](/intune/deploy-use/retire-devices-from-microsoft-intune-management).|
|Teljes képernyős mód|Lehetővé teszi a mobileszközök bizonyos funkcióinak, például a képernyőfelvétel-készítés és a kikapcsolás zárolását. Emellett az eszközt egyetlen meghatározott alkalmazás futtatására korlátozhatja.|[iOS-eszközök konfigurációs házirendjének beállításai a Microsoft Intune-ban](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## Alkalmazáskezelés

|Képesség|Részletek|További információ|
|--------------|-----------|--------------------|
|Alkalmazások telepítése és kezelése|Számos eszközt kínál, amelyek segítségével kezelheti a mobilalkalmazásokat teljes életciklusukon keresztül, beleértve a telepítési fájlokból és alkalmazás-áruházakból történő telepítést, az alkalmazás állapotának részletes megfigyelését, valamint az alkalmazás eltávolítását.|[Alkalmazások telepítése a Microsoft Intune-ban](/intune/deploy-use/deploy-apps)|
|Megfelelő és nem megfelelő alkalmazások|Lehetővé teszi az engedélyezett alkalmazások (amelyeket a felhasználók telepíthetnek) és a nem engedélyezett alkalmazások (amelyeket a felhasználók nem telepíthetnek) listájának meghatározását.|[iOS-szabályzatbeállítások a Microsoft Intune-ban](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Mobilalkalmazás-kezelés|A mobilalkalmazások kezelésre révén korlátozásokat konfigurálhat az alkalmazásokra vonatkozóan az Intune-nal kezelt eszközökre és a nem az Intune-nal kezelt eszközökre egyaránt. Ennek segítségével növelheti a vállalati adatok biztonságát bizonyos műveletek, például a másolás és beillesztés, az adatok külső biztonsági mentése, valamint az adatok alkalmazások közötti átvitelének korlátozásával.|[Configure and deploy mobile application management policies in the Microsoft Intune console](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[iOS-alkalmazások mobilalkalmazás-kezeléshez való előkészítése a Microsoft Intune alkalmazásburkoló eszközével](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Android-alkalmazások előkészítése mobilalkalmazás-felügyelethez a Microsoft Intune alkalmazásburkoló eszközével](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|Mobilalkalmazás-konfiguráció|A mobilalkalmazás-konfigurációs szabályzatokkal automatikusan megadhatja azokat a beállításokat, amelyekre szükség lehet, amikor egy felhasználó egy iOS-alkalmazást futtat. Előfordulhat például, hogy az alkalmazás portszám vagy bejelentkezési beállítások megadását kéri a felhasználótól. Ezzel leegyszerűsíthető az alkalmazások konfigurálása, és csökkenthető a segélyszolgálatra beérkező hívások száma.|[iOS-alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek segítségével a Microsoft Intune-ban](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Felügyelt böngésző|A felügyelt böngésző felhasználók számára történő telepítése után beállíthat egy házirendet a felügyelt böngészőhöz, amellyel szabályozhatja a látogatható webhelyeket. Emellett mobilalkalmazás-kezelési házirendeket is alkalmazhat a felügyelt böngészőre.|[Az internet-hozzáférés felügyelt böngészőszabályzatokkal való kezelése a Microsoft Intune-ban](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Microsoft Passport|Az Intune lehetővé teszi az integrációt a Microsoft Passport for Work nevű, a Windows 10-ben használható alternatív bejelentkezési módszert. Ez az Active Directoryt vagy az Azure Active Directory egy fiókját használja jelszó, intelligens kártya vagy virtuális intelligens kártya helyett.|[A Microsoft Passport beállításainak szabályozása az eszközökön a Microsoft Intune-nal](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|

## Vállalati erőforrások elérése

|Képesség|Részletek|További információ|
|--------------|-----------|--------------------|
|Tanúsítványprofilok|Létrehozhat és telepíthet megbízhatótanúsítvány-profilokat és SCEP-tanúsítványokat, amelyek segítségével biztonságossá teheti és hitelesítheti a Wi-Fi, VPN- és e-mail profilokat.|[Az erőforrások biztonságos elérése a Microsoft Intune tanúsítványprofiljai segítségével](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Wi-Fi profilok|Vezeték nélküli hálózati beállításokat telepíthet a felhasználók számára. Ezen beállítások telepítésével lecsökkentheti a vállalati hálózat hozzáféréséhez szükséges végfelhasználói beavatkozást.|[Wi-Fi-kapcsolatok a Microsoft Intune-ban](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|E-mail profilok|E-mail beállításokat hozhat létre és telepíthet az eszközökön. A felhasználók így külön beállítások elvégzése nélkül férhetnek hozzá vállalati levelezésükhöz saját eszközeiken.|[Vállalati levelezéshez való hozzáférés konfigurálása e-mail profilokkal a Microsoft Intune-ban](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN-profilok|VPN-beállításokat telepíthet a szervezethez tartozó felhasználók és eszközök számára. Ezen beállítások telepítésével lecsökkentheti a vállalati hálózaton lévő erőforrások eléréséhez szükséges végfelhasználói beavatkozást.|[VPN-kapcsolatok a Microsoft Intune-ban](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|Feltételes hozzáférési házirendek|A Microsoft Exchange e-mailekhez és SharePoint Online-hoz való hozzáférés felügyelete a nem az Intune által kezelt eszközökön|[Az e-mailek és a SharePoint elérésének korlátozása a Microsoft Intune használatával](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## Leltár és jelentéskészítés

|Képesség|Részletek|További információ|
|--------------|-----------|--------------------|
|Leltár és jelentéskészítés|Információkat kereshet a kezelt eszközökről és az azok által használt szoftverekről.|[A regisztrált eszközök áttekintése a Microsoft Intune leltárfunkciójával](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|


### További információ
[A Microsoft Intune Windows-számítógépek felügyeletére szolgáló képességei](windows-pc-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


