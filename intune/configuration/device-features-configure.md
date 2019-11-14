---
title: iOS- és macOS-eszközprofilok létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Adjon hozzá vagy hozzon létre egy iOS-vagy macOS-eszköz profilt, majd konfigurálja a AirPrint beállításait, a kezdőképernyő elrendezését, az alkalmazások értesítéseit, a megosztott eszközt, az egyszeri bejelentkezést és a webtartalom-szűrő beállításait a Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f02188e6dd6cea6048731d119f8f307224810dd9
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059953"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>iOS-es vagy macOS-es eszközfunkció-beállítások megadása az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune számos funkciót és beállítást tartalmaz, amelyek segítségével a rendszergazdák vezérelhetik az iOS-és macOS-eszközöket. A rendszergazdák például a következőket tehetik:

- A hálózatban lévő AirPrint-nyomtatók elérésének engedélyezése a felhasználók számára
- Alkalmazások és mappák hozzáadása a kezdőképernyőn, beleértve az új lapok hozzáadását
- Válassza ki, hogy megjelenjenek-e az alkalmazás értesítései
- A zárolási képernyő beállítása üzenet vagy objektum címkének megjelenítéséhez, különösen a megosztott eszközökhöz
- Biztonságos egyszeri bejelentkezési élményt biztosíthat a felhasználóknak az alkalmazások közötti hitelesítő adatok megosztásához
- Felnőtt nyelvet használó webhelyek szűrése, valamint adott webhelyek engedélyezése vagy letiltása

Az Intune a "konfigurációs profilok" használatával hozza létre és szabja testre ezeket a beállításokat a szervezet igényeinek megfelelően. Miután hozzáadta ezeket a funkciókat egy profilhoz, leküldheti vagy üzembe helyezheti a profilt az iOS-és macOS-eszközökön a szervezetben.

Ez a cikk a konfigurálható különböző szolgáltatásokat ismerteti, és bemutatja, hogyan hozhat létre egy eszköz-konfigurációs profilt. Az [iOS](ios-device-features-settings.md) -és [MacOS](macos-device-features-settings.md) -eszközökhöz elérhető összes beállítás is megjelenik.

## <a name="airprint"></a>AirPrint

A AirPrint egy Apple-szolgáltatás, amely lehetővé teszi, hogy az eszközök vezeték nélküli hálózaton keresztül nyomtassanak a fájlokra. Az Intune-ban AirPrint-információkat adhat hozzá az eszközökhöz.

Az Intune-ban konfigurálható beállítások listáját lásd: [AirPrint iOS](ios-device-features-settings.md#airprint) -en és [AirPrint MacOS rendszeren](macos-device-features-settings.md#airprint).

További információ a AirPrint-ről: a [AirPrint névjegye](https://support.apple.com/HT201311) az Apple webhelyén.

A következőkre vonatkozik:

- iOS 7,0 és újabb verziók
- iPadOS 13,0 és újabb verziók
- macOS 10,10 és újabb verziók

## <a name="app-notifications"></a>Alkalmazás-értesítések

Válassza ki, hogy az iOS-és iPad-eszközökön milyen alkalmazások kapják meg az értesítéseket. Az Intune-ból például elküldheti az alkalmazás értesítéseit, hogy azok megjelenjenek az értesítési központban, megjelenjenek a zárolási képernyőn, vagy hanglejátszást végeznek.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [alkalmazások értesítései iOS rendszeren](ios-device-features-settings.md#app-notifications).

A szolgáltatással kapcsolatos további információkért lásd: [értesítések](https://developer.apple.com/notifications/) az Apple webhelyén.

A következőkre vonatkozik:

- iOS 9,3 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="associated-domains"></a>Társított tartományok

A társított tartományok lehetővé teszik a tartományok, például a `contoso.com` és az alkalmazások közötti kapcsolat létrehozását. Ez a funkció lehetővé teszi a következőket:

- Megoszthatja az adatokat és bejelentkezési hitelesítő adatokat a szervezet alkalmazásai és webhelyei között.
- Használja a webhelyén alapuló alkalmazás-szolgáltatásokat, például az egyszeri bejelentkezési alkalmazás bővítményét, az univerzális hivatkozásokat és a jelszó automatikus kitöltését.

  Hozzon létre például egy társított tartományt, amely lehetővé teszi a jelszó automatikus kitöltését, hogy az alkalmazáshoz társított webhelyek hitelesítő adatait (például a jelszót) javasolja.

Az Intune-ban konfigurálható beállítások listáját lásd: [társított tartományok MacOS rendszeren](macos-device-features-settings.md#associated-domains).

A szolgáltatással kapcsolatos további információkért lásd: [az alkalmazás társított tartományának beállítása](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains) az Apple webhelyén.

A következőkre vonatkozik:

- macOS 10,15 és újabb verziók

## <a name="home-screen-layout"></a>A kezdőképernyő elrendezése

Ezekkel a beállításokkal konfigurálhatja az alkalmazások elrendezését és mappáit a Dock és a Home képernyőkön az iOS-és iPadOS-eszközökön. A következőket teheti:

- Alkalmazások és mappák a képernyőhöz való hozzáadásához használja a **Dock** beállításait. Például jelenítse meg a Safarit és a posta alkalmazást az eszköz dockján.
- Adja hozzá a kezdőképernyőn megjeleníteni kívánt **lapokat** és az egyes oldalakon megjeleníteni kívánt alkalmazásokat. Például vegyen fel egy **contoso** -lapot, és adja hozzá a beállítások alkalmazást ezen a lapon.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [kezdőképernyő elrendezése iOS](ios-device-features-settings.md#home-screen-layout)-en.

A következőkre vonatkozik:

- iOS 9,3 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="lock-screen-message"></a>A zárolási képernyő üzenete

Ezekkel a beállításokkal egyéni üzenetet vagy szöveget jeleníthet meg a bejelentkezési ablak és a zárolási képernyő megjelenítéséhez. Megadhat például egy "ha elveszett, vissza..." értéket. üzenet, és az eszköz címkével kapcsolatos információk megjelenítése.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: a [képernyő-üzenet beállításainak zárolása iOS rendszeren](ios-device-features-settings.md#lock-screen-message).

A zárolási képernyőn megjelenő üzenetekkel kapcsolatos további információkért lásd: [LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) az Apple webhelyén.

A következőkre vonatkozik:

- iOS 9,3 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="login-items"></a>Bejelentkezési elemek

Ezzel a szolgáltatással kiválaszthatja azokat az alkalmazásokat, egyéni alkalmazásokat, fájlokat és mappákat, amelyeket a felhasználók az eszközökre való bejelentkezéskor nyitnak meg. 

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: a macOS-beli [bejelentkezési elemek](macos-device-features-settings.md#login-items).

A következőkre vonatkozik:

- macOS 10,13 és újabb verziók

## <a name="login-window"></a>Bejelentkezési ablak

A bejelentkezési képernyő és a felhasználók számára elérhető függvények megjelenésének szabályozása a bejelentkezés előtt. Hozzáadhat például egy egyéni üzenettel rendelkező szalagcímet, ha az alvó gomb látható, és így tovább.

Az Intune-ban konfigurálható beállítások listáját lásd: [bejelentkezési ablak MacOS rendszeren](macos-device-features-settings.md#login-window).

A következőkre vonatkozik:

- macOS 10,7 és újabb verziók

## <a name="single-sign-on"></a>Egyszeri bejelentkezés

A legtöbb üzletviteli alkalmazás biztonsági célokból megkövetel bizonyos szintű felhasználóhitelesítést. Sok esetben a hitelesítéshez a felhasználónak többször kell megadnia ugyanazokat a hitelesítő adatokat. A felhasználói élmény javítása érdekében a fejlesztők egyszeri bejelentkezést (SSO) használó alkalmazásokat hozhatnak létre. Az egyszeri bejelentkezés használata csökkenti azt a számot, ahányszor a felhasználónak meg kell adnia a hitelesítő adatokat.

Az egyszeri bejelentkezés használatához ellenőrizze, hogy rendelkezik-e az alábbiakkal:

- Egy alkalmazás, amely úgy van kódolva, hogy az eszközön egyszeri bejelentkezéssel megkeresse a felhasználói hitelesítőadat-tárolót.
- Az iOS-eszközön való egyszeri bejelentkezéshez konfigurált Intune.

![Egyszeri bejelentkezés panel](./media/device-features-configure/sso-blade.png)

Az Intune-ban konfigurálható beállítások listáját lásd: [egyszeri bejelentkezés iOS rendszeren](ios-device-features-settings.md#single-sign-on).

A következőkre vonatkozik:

- iOS 7,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="single-sign-on-app-extension"></a>Egyszeri bejelentkezési alkalmazás bővítménye

Ezek a beállítások olyan alkalmazás-bővítményt konfigurálnak, amely lehetővé teszi az egyszeri bejelentkezést (SSO) az iOS-, iPadOS-és macOS-eszközökhöz. A legtöbb üzletági (LOB) alkalmazás és a szervezet webhelyei bizonyos fokú biztonságos felhasználói hitelesítést igényelnek. Sok esetben a hitelesítéshez a felhasználóknak többször is meg kell adniuk ugyanazokat a hitelesítő adatokat. Az SSO a hitelesítő adatok egyszer való megadása után hozzáférést biztosít a felhasználóknak az alkalmazásokhoz és a webhelyekhez. A bejelentkezést követően a felhasználók automatikusan hozzáférhetnek az alkalmazásokhoz és a webhelyekhez, vagy használhatnak hozzáférést a Face ID, a Touch ID vagy az Apple PIN-kóddal.

Az Intune-ban ezekkel a beállításokkal konfigurálhatja az Apple beépített Kerberos-bővítményét, vagy beállíthatja a szervezete által létrehozott egyszeri bejelentkezéses alkalmazás-bővítményt. Az SSO-alkalmazás bővítmény kezeli a felhasználók hitelesítését. Ezek a beállítások konfigurálják a hitelesítő adatok típusú egyszeri bejelentkezéses alkalmazás-bővítményeket, amelyek a kérdés-válasz hitelesítési folyamatok számára lettek kialakítva. Választhat az Apple által biztosított Kerberos-specifikus hitelesítő adatok és az általános hitelesítőadat-bővítmény közül.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [iOS SSO-alkalmazás kiterjesztése](ios-device-features-settings.md#single-sign-on-app-extension) és [MacOS SSO-alkalmazás kiterjesztése](macos-device-features-settings.md#single-sign-on-app-extension).

Az egyszeri bejelentkezéses alkalmazások kiterjesztésének fejlesztésével kapcsolatos további információkért tekintse meg a [bővíthető vállalati egyszeri bejelentkezést](https://developer.apple.com/videos/play/tech-talks/301) az Apple webhelyén.

> [!NOTE]
> Az **egyszeri bejelentkezési alkalmazás bővítményének** funkciója eltér az **egyszeri bejelentkezési** szolgáltatástól:
>
> - Az **egyszeri bejelentkezés alkalmazás-bővítmény** beállításai a iPadOS 13,0 (és újabb) és az iOS 13,0 (és újabb) verzióra vonatkoznak. Az **egyszeri bejelentkezés** beállításai a iPadOS 13,0 (és újabb) és az iOS 7,0 és újabb rendszerekre vonatkoznak.
> - Az **egyszeri bejelentkezési alkalmazás-bővítmény** kezeli a hitelesítést az operációs rendszerrel. Az **egyszeri bejelentkezés**során egy adott alkalmazás kezeli a hitelesítést.
> - Az **egyszeri bejelentkezési alkalmazás bővítmény**használatakor a felhasználók csendesen jelentkeznek be az alkalmazásokba vagy a webhelyekre, vagy a Face ID, a Touch ID vagy az Apple pincode vagy PIN-kóddal. **Egyszeri bejelentkezés**használata esetén a felhasználók egy másik alkalmazás használatával jelentkeznek be az alkalmazásokba és a webhelyekre.
>
>    Az **egyszeri bejelentkezési alkalmazás bővítménye** az Apple operációs rendszert használja a hitelesítéshez. Így jobb végfelhasználói élményt biztosíthat.
>
> - Fejlesztési szempontból az **egyszeri bejelentkezési alkalmazás bővítménye** bármilyen hitelesítő adatok egyszeri bejelentkezéses hitelesítését képes használni. **Egyszeri bejelentkezés**esetén csak Kerberos SSO-hitelesítést használhat.  

A következőkre vonatkozik:

- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók
- macOS 10,15 és újabb verziók

## <a name="wallpaper"></a>Háttérkép

Adjon hozzá egy egyéni. png,. jpg vagy. jpeg formátumú rendszerképet a felügyelt iOS-eszközökhöz. Például az Intune használatával vegyen fel egy vállalati emblémát az eszközök zárolási képernyőjére.

Az Intune-ban konfigurálható beállítások listáját lásd: [háttérkép az iOS](ios-device-features-settings.md#wallpaper)-ben.

A következőkre vonatkozik:

- iOS
- iPadOS 13,0 és újabb verziók

## <a name="web-content-filter"></a>Webes tartalom szűrője

Ezek a beállítások a weblapok kiértékeléséhez, valamint a felnőtt tartalmak és a felnőtt nyelv letiltásához használhatják az Apple beépített AutoSzűrő algoritmusát. Létrehozhatja az engedélyezett webhivatkozások és a korlátozott webes hivatkozások listáját is. Engedélyezheti például, hogy csak `contoso` webhely legyen megnyitva.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [webes tartalom szűrője iOS rendszeren](ios-device-features-settings.md#web-content-filter).

A következőkre vonatkozik:

- iOS 7,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="create-a-device-profile"></a>Eszközprofil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. Például a megfelelő szabályzat neve **MacOS: konfigurálja a bejelentkezési képernyőt**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza ki az eszközök platformját. A választható lehetőségek:  
        - **iOS/iPadOS**
        - **macOS**
    - **Profil típusa**: Válassza az **Eszközfunkciók** lehetőséget.

4. A kiválasztott platformtól függően a konfigurálható beállítások eltérőek. Válassza ki a platformot a részletes beállításokhoz:

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [macOS](macos-device-features-settings.md)

5. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a profilok listájában. Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

## <a name="next-steps"></a>További lépések

A profil létrehozása után készen áll a hozzárendelésre. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Megtekintheti az [iOS](ios-device-features-settings.md) -és [MacOS](macos-device-features-settings.md) -eszközök összes eszköz-funkciójának beállításait.
