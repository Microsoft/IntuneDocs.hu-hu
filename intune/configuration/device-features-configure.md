---
title: iOS- és macOS-eszközprofilok létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Adjon hozzá vagy hozzon létre egy iOS-vagy macOS-eszköz profilt, majd konfigurálja a AirPrint beállításait, a kezdőképernyő elrendezését, az alkalmazások értesítéseit, a megosztott eszközt, az egyszeri bejelentkezést és a webtartalom-szűrő beállításait a Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
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
ms.openlocfilehash: d887c7bc3c7e9ea8b6719993b5ba4909e9c18ea8
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992929"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>iOS-es vagy macOS-es eszközfunkció-beállítások megadása az Intune-ban

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

A következőre érvényes

- iOS 7,0 és újabb verziók
- iPadOS 13,0 és újabb verziók
- macOS 10,10 és újabb verziók

## <a name="app-notifications"></a>Alkalmazásértesítések

Válassza ki, hogy az iOS-és iPad-eszközökön milyen alkalmazások kapják meg az értesítéseket. Az Intune-ból például elküldheti az alkalmazás értesítéseit, hogy azok megjelenjenek az értesítési központban, megjelenjenek a zárolási képernyőn, vagy hanglejátszást végeznek.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [alkalmazások értesítései iOS rendszeren](ios-device-features-settings.md#app-notifications).

A szolgáltatással kapcsolatos további információkért lásd: [értesítések](https://developer.apple.com/notifications/) az Apple webhelyén.

A következőre érvényes

- iOS 9,3 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="associated-domains"></a>Társított tartományok

A társított tartományok lehetővé teszik a tartományok, például a `contoso.com`és az alkalmazások közötti kapcsolat létrehozását. Ez a funkció lehetővé teszi a következőket:

- Megoszthatja az adatokat és bejelentkezési hitelesítő adatokat a szervezet alkalmazásai és webhelyei között.
- Használja a webhelyén alapuló alkalmazás-szolgáltatásokat, például az egyszeri bejelentkezési alkalmazás bővítményét, az univerzális hivatkozásokat és a jelszó automatikus kitöltését.

  Hozzon létre például egy társított tartományt, amely lehetővé teszi a jelszó automatikus kitöltését, hogy az alkalmazáshoz társított webhelyek hitelesítő adatait (például a jelszót) javasolja.

Az Intune-ban konfigurálható beállítások listáját lásd: [társított tartományok MacOS rendszeren](macos-device-features-settings.md#associated-domains).

A szolgáltatással kapcsolatos további információkért lásd: [az alkalmazás társított tartományának beállítása](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains) az Apple webhelyén.

A következőre érvényes

- macOS 10,15 és újabb verziók

## <a name="home-screen-layout"></a>A kezdőképernyő elrendezése

Ezekkel a beállításokkal konfigurálhatja az alkalmazások elrendezését és mappáit a Dock és a Home képernyőkön az iOS-és iPadOS-eszközökön. A következőket teheti:

- Alkalmazások és mappák a képernyőhöz való hozzáadásához használja a **Dock** beállításait. Például jelenítse meg a Safarit és a posta alkalmazást az eszköz dockján.
- Adja hozzá a kezdőképernyőn megjeleníteni kívánt **lapokat** és az egyes oldalakon megjeleníteni kívánt alkalmazásokat. Például vegyen fel egy **contoso** -lapot, és adja hozzá a beállítások alkalmazást ezen a lapon.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [kezdőképernyő elrendezése iOS](ios-device-features-settings.md#home-screen-layout)-en.

A következőre érvényes

- iOS 9,3 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="lock-screen-message"></a>A zárolási képernyő üzenete

Ezekkel a beállításokkal egyéni üzenetet vagy szöveget jeleníthet meg a bejelentkezési ablak és a zárolási képernyő megjelenítéséhez. Megadhat például egy "ha elveszett, vissza..." értéket. üzenet, és az eszköz címkével kapcsolatos információk megjelenítése.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: a [képernyő-üzenet beállításainak zárolása iOS rendszeren](ios-device-features-settings.md#lock-screen-message).

A zárolási képernyőn megjelenő üzenetekkel kapcsolatos további információkért lásd: [LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) az Apple webhelyén.

A következőre érvényes

- iOS 9,3 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="login-items"></a>Bejelentkezési elemek

Ezzel a szolgáltatással kiválaszthatja azokat az alkalmazásokat, egyéni alkalmazásokat, fájlokat és mappákat, amelyeket a felhasználók az eszközökre való bejelentkezéskor nyitnak meg.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: a macOS-beli [bejelentkezési elemek](macos-device-features-settings.md#login-items).

A következőre érvényes

- macOS 10,13 és újabb verziók

## <a name="login-window"></a>Bejelentkezési ablak

A bejelentkezési képernyő és a felhasználók számára elérhető függvények megjelenésének szabályozása a bejelentkezés előtt. Hozzáadhat például egy egyéni üzenettel rendelkező szalagcímet, ha az alvó gomb látható, és így tovább.

Az Intune-ban konfigurálható beállítások listáját lásd: [bejelentkezési ablak MacOS rendszeren](macos-device-features-settings.md#login-window).

A következőre érvényes

- macOS 10,7 és újabb verziók

## <a name="single-sign-on"></a>Egyszeri bejelentkezés

A legtöbb üzletviteli alkalmazás biztonsági célokból megkövetel bizonyos szintű felhasználóhitelesítést. Sok esetben a hitelesítéshez a felhasználónak többször kell megadnia ugyanazokat a hitelesítő adatokat. A felhasználói élmény javítása érdekében a fejlesztők egyszeri bejelentkezést (SSO) használó alkalmazásokat hozhatnak létre. Az egyszeri bejelentkezés használata csökkenti azt a számot, ahányszor a felhasználónak meg kell adnia a hitelesítő adatokat.

Az egyszeri bejelentkezés használatához ellenőrizze, hogy rendelkezik-e az alábbiakkal:

- Egy alkalmazás, amely úgy van kódolva, hogy az eszközön egyszeri bejelentkezéssel megkeresse a felhasználói hitelesítőadat-tárolót.
- Az iOS-eszközön való egyszeri bejelentkezéshez konfigurált Intune.

![Egyszeri bejelentkezés panel](./media/device-features-configure/sso-blade.png)

Az Intune-ban konfigurálható beállítások listáját lásd: [egyszeri bejelentkezés iOS rendszeren](ios-device-features-settings.md#single-sign-on).

A következőre érvényes

- iOS 7,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

## <a name="single-sign-on-app-extension"></a>Egyszeri bejelentkezési alkalmazás bővítménye

Ezek a beállítások olyan alkalmazás-bővítményt konfigurálnak, amely lehetővé teszi az egyszeri bejelentkezést (SSO) az iOS-, iPadOS-és macOS-eszközökhöz. A legtöbb üzletági (LOB) alkalmazás és a szervezet webhelyei bizonyos fokú biztonságos felhasználói hitelesítést igényelnek. Sok esetben a hitelesítéshez a felhasználóknak többször is meg kell adniuk ugyanazokat a hitelesítő adatokat. Az SSO a hitelesítő adatok egyszer való megadása után hozzáférést biztosít a felhasználóknak az alkalmazásokhoz és a webhelyekhez. A bejelentkezést követően a felhasználók automatikusan hozzáférhetnek az alkalmazásokhoz és a webhelyekhez, vagy használhatnak hozzáférést a Face ID, a Touch ID vagy az Apple PIN-kóddal.

Az Intune-ban ezekkel a beállításokkal konfigurálhatja a szervezet, az identitás-szolgáltató vagy az Apple által létrehozott SSO AP-bővítményt. Az SSO-alkalmazás bővítmény kezeli a felhasználók hitelesítését. Ezek a beállítások az átirányítás típusa és a hitelesítő adatok típusú egyszeri bejelentkezéses alkalmazás-bővítmények konfigurálását végzik.

- Az átirányítási típus a modern hitelesítési protokollok, például a OAuth és a egy SAML2 számára készült.
- A hitelesítőadat-típus a kérdés-válasz hitelesítési folyamatokhoz lett tervezve. Választhat az Apple által biztosított Kerberos-specifikus hitelesítő adatok és az általános hitelesítőadat-bővítmény közül.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [iOS SSO-alkalmazás kiterjesztése](ios-device-features-settings.md#single-sign-on-app-extension) és [MacOS SSO-alkalmazás kiterjesztése](macos-device-features-settings.md#single-sign-on-app-extension).

Az egyszeri bejelentkezéses alkalmazások kiterjesztésének fejlesztésével kapcsolatos további információkért tekintse meg a [bővíthető vállalati egyszeri bejelentkezést](https://developer.apple.com/videos/play/tech-talks/301) az Apple webhelyén. A szolgáltatás Apple-leírásának olvasásához tekintse meg az [egyszeri bejelentkezési bővítmények adattartalom-beállításait](https://support.apple.com/guide/mdm/single-sign-on-extensions-mdmfd9cdf845/web). 

> [!NOTE]
> Az **egyszeri bejelentkezési alkalmazás bővítményének** funkciója eltér az **egyszeri bejelentkezési** szolgáltatástól:
>
> - Az **egyszeri bejelentkezés alkalmazás-bővítmény** beállításai a iPadOS 13,0 (és újabb), az iOS 13,0 (és újabb), valamint a MacOS 10,15 (és újabb verziók) esetében érvényesek. Az **egyszeri bejelentkezés** beállításai a iPadOS 13,0 (és újabb) és az iOS 7,0 és újabb rendszerekre vonatkoznak.
>
> - Az **egyszeri bejelentkezés alkalmazás-bővítmény** beállításai olyan bővítményeket határoznak meg, amelyeket az identitás-szolgáltatók vagy a szervezetek használhatnak a zökkenőmentes vállalati bejelentkezési élmény biztosításához. Az **egyszeri bejelentkezési** beállítások a Kerberos-fiók adatait határozzák meg, amikor a felhasználók hozzáférnek a kiszolgálókhoz vagy alkalmazásokhoz.
>
> - Az **egyszeri bejelentkezési alkalmazás bővítménye** az Apple operációs rendszert használja a hitelesítéshez. Így előfordulhat, hogy az **egyszeri bejelentkezésnél**jobb a végfelhasználói élmény.
>
> - Egy fejlesztési perspektívából az **egyszeri bejelentkezési alkalmazás bővítménnyel**bármilyen típusú átirányítási SSO-vagy hitelesítő adatokat tartalmazó egyszeri bejelentkezéses hitelesítést használhat. **Egyszeri bejelentkezés**esetén csak Kerberos SSO-hitelesítést használhat.
>
> - A Kerberos **egyszeri bejelentkezési alkalmazás bővítményét** az Apple fejlesztette ki, és az iOS 13.0 + és a MacOS 10.15 + platformokra épül. A beépített Kerberos-bővítmény használatával a felhasználók bejelentkezhetnek a Kerberos-hitelesítést támogató natív alkalmazásokba és webhelyekre. Az **egyszeri bejelentkezés** nem a Kerberos Apple-implementációja.
>
> - A beépített Kerberos **egyszeri bejelentkezési alkalmazás-bővítmény** a weblapok és alkalmazások Kerberos-problémáit kezeli ugyanúgy, mint az **egyszeri bejelentkezés**. A beépített Kerberos-bővítmény azonban támogatja a jelszavak módosítását, és a vállalati hálózatokban jobban viselkedik. A Kerberos **egyszeri bejelentkezés alkalmazás-bővítmény** és az **egyszeri bejelentkezés**között a jobb teljesítmény és képességek miatt ajánlott a bővítmény használata.

A következőre érvényes

- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók
- macOS 10,15 és újabb verziók

## <a name="wallpaper"></a>Háttérkép

Adjon hozzá egy egyéni. png,. jpg vagy. jpeg formátumú rendszerképet a felügyelt iOS-eszközökhöz. Például az Intune használatával vegyen fel egy vállalati emblémát az eszközök zárolási képernyőjére.

Az Intune-ban konfigurálható beállítások listáját lásd: [háttérkép az iOS](ios-device-features-settings.md#wallpaper)-ben.

A következőre érvényes

- iOS
- iPadOS 13,0 és újabb verziók

## <a name="web-content-filter"></a>Webes tartalom szűrője

Ezek a beállítások a weblapok kiértékeléséhez, valamint a felnőtt tartalmak és a felnőtt nyelv letiltásához használhatják az Apple beépített AutoSzűrő algoritmusát. Létrehozhatja az engedélyezett webhivatkozások és a korlátozott webes hivatkozások listáját is. Engedélyezheti például, hogy csak `contoso` webhelyeket nyisson meg.

Az Intune-ban konfigurálható beállítások listáját itt tekintheti meg: [webes tartalom szűrője iOS rendszeren](ios-device-features-settings.md#web-content-filter).

A következőre érvényes

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
