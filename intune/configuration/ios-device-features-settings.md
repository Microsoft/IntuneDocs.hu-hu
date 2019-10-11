---
title: iOS-eszközök funkciójának beállításai a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg az iOS-eszközök AirPrint, a kezdőképernyő elrendezését, az alkalmazás értesítései, a megosztott eszköz, az egyszeri bejelentkezés és a webtartalom-szűrő beállításait a Microsoft Intuneban. Ezekkel a beállításokkal konfigurálhatja az iOS-eszközöket a szervezete ezen Apple-szolgáltatásainak használatához.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 341609afeec02c67b4ea0d85a541fca61345ced4
ms.sourcegitcommit: fca2670142c083d7562c0a36547a6a451863e315
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/08/2019
ms.locfileid: "72036477"
---
# <a name="ios-and-ipados-device-settings-to-use-common-ios-features-in-intune"></a>iOS-és iPadOS-eszközök beállításai az Intune közös iOS-funkcióinak használatához

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune tartalmaz néhány beépített beállítást, amely lehetővé teszi, hogy az iOS-felhasználók különböző Apple-funkciókat használjanak az eszközön. A rendszergazdák például szabályozhatják, hogy az iOS-felhasználók hogyan használják a AirPrint-nyomtatókat, hogyan adhatnak hozzá alkalmazásokat és mappákat a kezdőképernyőn lévő dockhoz és lapokhoz, hogyan jeleníthetők meg az alkalmazás értesítései, megjelenjenek az eszköz címkéi adatai a zárolási képernyőn, egyszeri bejelentkezéses hitelesítés használata és felhasználók hitelesítése tanúsítványokkal.

Ezekkel a szolgáltatásokkal vezérelheti az iOS-eszközöket a mobileszköz-kezelési (MDM) megoldás részeként.

Ez a cikk felsorolja ezeket a beállításokat, és leírja az egyes beállításokat. További információ ezekről a funkciókról: [iOS-vagy MacOS-eszköz funkció beállításainak](../device-features-configure.md)megadása.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy IOS-eszköz konfigurációs profilját](../device-features-configure.md).

> [!NOTE]
> Ezek a beállítások a különböző regisztrációs típusokra vonatkoznak, és egyes beállítások az összes regisztrációs lehetőségre érvényesek. A különböző regisztrációs típusokkal kapcsolatos további információkért lásd: [iOS-regisztráció](../ios-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

> [!NOTE]
> Ügyeljen arra, hogy az összes nyomtatót ugyanahhoz a profilhoz adja. Az Apple megakadályozza, hogy több AirPrint-profil is megcélozza ugyanazt az eszközt.

- **IP-cím**: Adja meg a nyomtató IPv4-vagy IPv6-címeit. Ha az állomásnevek használatával azonosítja a nyomtatókat, az IP-címet a nyomtató a terminálon való pingelésével érheti el. Az IP-cím és az elérési út (ebben a cikkben) beszerzése további részleteket tartalmaz.
- **Elérési út**: Az elérési út általában `ipp/print` a hálózatban lévő nyomtatókhoz. Az IP-cím és az elérési út (ebben a cikkben) beszerzése további részleteket tartalmaz.
- **Port**: Adja meg a AirPrint célhelyének figyelési portját. Ha üresen hagyja ezt a tulajdonságot, a AirPrint az alapértelmezett portot használja. Elérhető az iOS 11,0-es és újabb verzióiban.
- **TLS**: Válassza az **Engedélyezés** lehetőséget a AirPrint-kapcsolatok TRANSPORT Layer Security (TLS) használatával történő biztonságossá tételéhez. Elérhető az iOS 11,0-es és újabb verzióiban.

AirPrint-kiszolgálók hozzáadásához a következőket teheti:

- A **Hozzáadás** hozzáadja a AirPrint-kiszolgálót a listához. Számos AirPrint-kiszolgáló adható hozzá.
- **Importáljon** egy vesszővel tagolt (. csv) fájlt ezekkel az adatokkal. Vagy az **Exportálás** gombra kattintva hozzon létre egy listát a hozzáadott AirPrint-kiszolgálókról.

### <a name="get-server-ip-address-resource-path-and-port"></a>Kiszolgáló IP-címének, erőforrás-elérési útjának és portjának beolvasása

AirPrinter-kiszolgálók hozzáadásához szüksége lesz a nyomtató IP-címére, az erőforrás elérési útjára és a portra. Az alábbi lépések bemutatják, hogyan kérheti le ezeket az információkat.

1. Olyan Mac gépen, amely ugyanahhoz a helyi hálózathoz (alhálózat) csatlakozik, mint a AirPrint-nyomtatók, nyissa meg a **terminált** (a **/Applications/Utilities alatt**).
2. A terminálban írja be a `ippfind` értéket, majd kattintson az ENTER gombra.

    Jegyezze fel a nyomtató adatait. Előfordulhat például, hogy a `ipp://myprinter.local.:631/ipp/port1` értékhez hasonló értéket ad vissza. Az első rész a nyomtató neve. Az utolsó rész (`ipp/port1`) az erőforrás elérési útja.

3. A terminálban írja be a `ping myprinter.local` értéket, majd kattintson az ENTER gombra.

   Jegyezze fel az IP-címet. Előfordulhat például, hogy a `PING myprinter.local (10.50.25.21)` értékhez hasonló értéket ad vissza.

4. Használja az IP-cím és az erőforrás elérési útjának értékét. Ebben a példában az IP-cím `10.50.25.21`, az erőforrás elérési útja pedig `/ipp/port1`.

## <a name="home-screen-layout"></a>A kezdőképernyő elrendezése

Ez a funkció az alábbiakra vonatkozik:

- iOS 9,3 vagy újabb

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

### <a name="dock"></a>Dock

A **Dock** beállításait használva legfeljebb hat elemet vagy mappát adhat hozzá az iOS-képernyő dockhoz. Számos eszköz kevesebb elemet támogat. Az iPhone-eszközök például legfeljebb négy elemet támogatnak. Ebben az esetben csak az első négy hozzáadott elem jelenik meg az eszközön.

Az eszköz dockhoz legfeljebb **hat** elemet (az alkalmazások és a mappák együttesét) adhat hozzá.

- **Hozzáadás**: Alkalmazásokat vagy mappákat adhat hozzá a dockhoz az eszközön.
- **Írja be a következőt**: **Alkalmazás** vagy **mappa**hozzáadása:

  - **Alkalmazás**: Válassza ezt a lehetőséget, ha alkalmazásokat szeretne hozzáadni a képernyőn lévő dockhoz. Be

    - **Alkalmazás neve**: Adja meg az alkalmazás nevét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az iOS-eszközön.
    - Alkalmazáscsomag **azonosítója**: Adja meg az alkalmazás köteg-AZONOSÍTÓját. További Példákért lásd a [beépített iOS-alkalmazások köteg-azonosítóit](bundle-ids-built-in-ios-apps.md) .

  - **Mappa**: Válassza ezt a lehetőséget, ha mappát szeretne hozzáadni a képernyőn a dockhoz.

    A mappában lévő lapokhoz hozzáadott alkalmazások balról jobbra, a listával megegyező sorrendben lesznek elrendezve. Ha több alkalmazást ad hozzá, mint amennyi elfér egy oldalon, az alkalmazások átkerülnek egy másik lapra.

    - **Mappa neve**: Adja meg a mappa nevét. Ez a név jelenik meg a felhasználók számára az eszközön.
    - **Lapok listája**: **Adjon hozzá** egy lapot, és adja meg a következő tulajdonságokat:

      - **Oldal neve**: Adja meg az oldal nevét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az iOS-eszközön.
      - **Alkalmazás neve**: Adja meg az alkalmazás nevét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az iOS-eszközön.
      - Alkalmazáscsomag **azonosítója**: Adja meg az alkalmazás köteg-AZONOSÍTÓját. További Példákért lásd a [beépített iOS-alkalmazások köteg-azonosítóit](bundle-ids-built-in-ios-apps.md) .

      Akár **20** oldalt is hozzáadhat az eszköz dockhoz.

> [!NOTE]
> Amikor ikonokat ad hozzá a Dock-beállításokkal, a kezdőképernyő és az oldalak ikonjai zárolva vannak, és nem helyezhetők át. Ez az iOS-és az Apple MDM-házirendjeivel is megtervezhető.

#### <a name="example"></a>Példa

A következő példában a Dock képernyő csak a Safari, a posta és a Stocks alkalmazásokat jeleníti meg. A levelezési alkalmazás a tulajdonságok megjelenítéséhez van kiválasztva:

![Példa iOS Dock beállításokra](./media/ios-device-features-settings/FfFiUcP.png)

Ha a szabályzatot egy iPhone-hoz rendeli hozzá, a Dock a következő képhez hasonlóan néz ki:

![Példa iOS Dock elrendezésére iPhone-eszközön](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>Pages

Adja hozzá a kezdőképernyőn megjeleníteni kívánt lapokat és az egyes lapokon megjeleníteni kívánt alkalmazásokat. Az oldalhoz hozzáadott alkalmazások balról jobbra, a listával megegyező sorrendben vannak rendezve. Ha több alkalmazást ad hozzá, mint amennyi elfér egy oldalon, az alkalmazások átkerülnek egy másik lapra.

> [!TIP]
> A kezdőképernyő és a lapok listájában lévő elemek átrendezéséhez húzza őket a kívánt helyre.

Egy eszközön legfeljebb **40** lapot adhat hozzá.

- **Lapok listája**: **Adjon hozzá** egy lapot, és adja meg a következő tulajdonságokat:

  - **Oldal neve**: Adja meg az oldal nevét. A rendszer ezt a nevet használja a Azure Portalban lévő hivatkozáshoz, és *nem* jelenik meg az iOS-eszközön.

  Egy eszközön legfeljebb **60** elemet (alkalmazásokat és mappákat) adhat hozzá.

  - **Hozzáadás**: Alkalmazásokat vagy mappákat adhat hozzá az eszköz egyik lapjához.

    - **Írja be a következőt**: **Alkalmazás** vagy **mappa**hozzáadása:

      - **Alkalmazás**: Válassza ezt a lehetőséget, ha alkalmazásokat szeretne hozzáadni a képernyőn lévő laphoz. Ezt is adja meg:

        - **Alkalmazás neve**: Adja meg az alkalmazás nevét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az iOS-eszközön.
        - Alkalmazáscsomag **azonosítója**: Adja meg az alkalmazás köteg-AZONOSÍTÓját. További Példákért lásd a [beépített iOS-alkalmazások köteg-azonosítóit](bundle-ids-built-in-ios-apps.md) .

      - **Mappa**: Válassza ezt a lehetőséget, ha mappát szeretne hozzáadni a képernyőn a dockhoz.

        A mappában lévő lapokhoz hozzáadott alkalmazások balról jobbra, a listával megegyező sorrendben lesznek elrendezve. Ha több alkalmazást ad hozzá, mint amennyi elfér egy oldalon, az alkalmazások átkerülnek egy másik lapra.

        - **Mappa neve**: Adja meg a mappa nevét. Ez a név jelenik meg a felhasználók számára az eszközön.
        - **Hozzáadás**: Lapokat helyez el a mappába. Adja meg a következő tulajdonságokat is:

          - **Oldal neve**: Adja meg az oldal nevét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az iOS-eszközön.
          - **Alkalmazás neve**: Adja meg az alkalmazás nevét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az iOS-eszközön.
          - Alkalmazáscsomag **azonosítója**: Adja meg az alkalmazás köteg-AZONOSÍTÓját. További Példákért lásd a [beépített iOS-alkalmazások köteg-azonosítóit](bundle-ids-built-in-ios-apps.md) .

#### <a name="example"></a>Példa

A következő példában egy **contoso** nevű új oldal van hozzáadva. Az oldalon a barátok és beállítások keresése alkalmazások láthatók. A beállítások alkalmazás a tulajdonságok megjelenítéséhez van kiválasztva:

![Példa iOS-kezdőképernyő beállítására](./media/ios-device-features-settings/Jc2OxyX.png)

Ha a szabályzatot egy iPhone-hoz rendeli hozzá, az oldal az alábbi képhez hasonlóan néz ki:

![iOS-eszköz módosított kezdőképernyővel](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>Alkalmazás-értesítések

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Hozzáadás**: Értesítések hozzáadása az alkalmazásokhoz:

    ![Alkalmazás-értesítés hozzáadása az iOS-profilban az Intune-ban](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - Alkalmazáscsomag **azonosítója**: Adja meg a hozzáadni kívánt alkalmazás alkalmazáscsomag- **azonosítóját** . További Példákért lásd a [beépített iOS-alkalmazások köteg-azonosítóit](bundle-ids-built-in-ios-apps.md) .
  - **Alkalmazás neve**: Adja meg a hozzáadni kívánt alkalmazás nevét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az eszközön.
  - **Közzétevő**: Adja meg a hozzáadni kívánt alkalmazás közzétevőjét. A rendszer ezt a nevet használja a Azure Portalban való hivatkozáshoz. *Nem* jelenik meg az eszközön.
  - **Értesítések**: **Engedélyezheti** vagy **letilthatja** , hogy az alkalmazás értesítéseket küldjön az eszközre.
    - **Megjelenítés az értesítési központban**: Az **Engedélyezés** beállítás megadásával az alkalmazás értesítéseket jeleníthet meg az eszköz értesítési központban. A **Letiltás** beállítás megadásával megakadályozható, hogy az alkalmazás értesítéseket jelenít meg az értesítési központban.
    - **Megjelenítés a zárolási képernyőn**: Az **Engedélyezés** gombra kattintva megtekintheti az alkalmazásból származó értesítéseket az eszköz zárolási képernyőjén. A **Letiltás** beállítás megadásával megakadályozható, hogy az alkalmazás megjelenítse az értesítéseket a zárolási képernyőn.
    - **Riasztás típusa**: Amikor az eszköz zárolva van, válassza ki, hogyan jelenjen meg az értesítés. A választható lehetőségek:
      - **Nincs**: Nem jelenik meg értesítés.
      - **Szalagcím**: A rendszer röviden megjeleníti egy szalagcímet az értesítéssel.
      - **Modális**: Az értesítés megjelenik, és a felhasználónak manuálisan el kell indítania azt az eszköz használatának folytatása előtt.
    - **Jelvény az alkalmazás ikonján**: Az **Engedélyezés** elemre kattintva hozzáadhat egy jelvényt az alkalmazás ikonjához. A jelvény azt jelenti, hogy az alkalmazás elküldött egy értesítést.
    - **Hangok**: Az **Engedélyezés** gombra kattintva hangjelzést adhat az értesítés kézbesítéséről.

## <a name="lock-screen-message"></a>A zárolási képernyő üzenete

Ez a funkció az alábbiakra vonatkozik:

- iOS 9.3 és újabb verziók

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Eszköz címkéjének adatai**: Adja meg az eszköz eszköz címkéjével kapcsolatos adatokat. Például írja be a következőt: `Owned by Contoso Corp` vagy `Serial Number: {{serialnumber}}`.

  A beírt szöveg megjelenik a bejelentkezési ablak és az eszköz zárolási képernyőjén.

- A **zárolási képernyő lábjegyzete**: Ha az eszköz elveszett vagy ellopták, adjon meg egy megjegyzést, amely segíthet a visszaadott eszköz beszerzésében. Megadhatja a kívánt szöveget. Például: `If found, call Contoso at ...`.

  Az eszköz-jogkivonatok az eszközre vonatkozó információk hozzáadására is használhatók ezekhez a mezőkhöz. A sorozatszám megjelenítéséhez például írja be a következőt: `Serial Number: {{serialnumber}}`. A zárolási képernyőn a szöveg a következőhöz hasonlóan jelenik meg: `Serial Number 123456789ABC`. Változók beírásakor ügyeljen arra, hogy kapcsos zárójeleket használjon `{{ }}`. Az [alkalmazás-konfigurációs tokenek](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) tartalmazzák a használható változók listáját. A `deviceName` vagy bármely más, eszközre jellemző értéket is használhatja.

  > [!NOTE]
  > A rendszer nem érvényesíti a változókat a felhasználói felületen, és megkülönbözteti a kis-és nagybetűket. Ennek eredményeképpen előfordulhat, hogy a profilok helytelen bevitelsel lettek mentve. Ha például `{{deviceid}}` helyett a `{{DeviceID}}` értéket adja meg, akkor az eszköz egyedi azonosítója helyett a literál sztring jelenik meg. Ügyeljen arra, hogy a helyes adatokat adja meg.

## <a name="single-sign-on"></a>Egyszeri bejelentkezés

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Username attribútum a HRE**: Az Intune az Azure AD-ben minden felhasználó számára keresi ezt az attribútumot. Az Intune ezután feltölti a megfelelő mezőt (például UPN) az eszközre telepített XML-kód létrehozása előtt. A választható lehetőségek:

  - **Egyszerű felhasználónév**: Az egyszerű felhasználónév az alábbi módon van elemezve:

    ![Felhasználónév attribútum](./media/ios-device-features-settings/User-name-attribute.png)

    Szükség esetén felülírhatja a tartományt is, ha beírja a kívánt tartománynevet a **Tartomány** szövegmezőbe.

    A contoso például több régióval rendelkezik, például Európa, Ázsia és Észak-Amerika. A contoso szeretné, hogy az ázsiai felhasználók az egyszeri bejelentkezést használják, és az alkalmazásnak az UPN-t kell `username@asia.contoso.com` formátumban megadnia. Amikor kiválasztja az **egyszerű felhasználónév**lehetőséget, az egyes felhasználók tartománya az Azure ad-ből kerül, amely `contoso.com`. Így az ázsiai felhasználók esetében válassza az **egyszerű felhasználónév**lehetőséget, és írja be a `asia.contoso.com` értéket. A végfelhasználó UPN-je `username@asia.contoso.com` lesz, `username@contoso.com` helyett.

  - **Intune-eszköz azonosítója**: Az Intune automatikusan kiválasztja az Intune-eszköz AZONOSÍTÓját.

    Az alkalmazásoknak alapértelmezés szerint csak az eszközazonosítóra van szükségük. Ha azonban az alkalmazás a tartományt és az eszköz AZONOSÍTÓját használja, beírhatja a tartományt a tartomány szövegmezőbe.

    > [!NOTE]
    > Alapértelmezett esetben hagyja a tartományt üresen, ha eszközazonosítót használ.

  - **Azure AD-eszköz azonosítója**

- **Tartomány**: Adja meg az URL-cím tartomány részét. Például írja be a következőt: `contoso.com`.
- **Az egyszeri bejelentkezést használó URL-előtagok**: **Adjon hozzá** olyan URL-címeket a szervezetben, amelyek felhasználói egyszeri bejelentkezéses hitelesítést igényelnek.

  Ha egy felhasználó csatlakozik ezen webhelyekhez, az iOS-eszköz az egyszeri bejelentkezés hitelesítő adatait használja, és a felhasználónak nem kell hitelesítő adatokat megadnia. Ha a többtényezős hitelesítés engedélyezve van, akkor a felhasználóknak a második hitelesítést kell megadniuk.

  > [!NOTE]
  > Ezeknek az URL-címeknek érvényes formátumú teljes tartományneveknek kell lenniük. Az Apple használatához a `http://<yourURL.domain>` formátumúnak kell lennie.

  Az URL-egyeztetési mintáknak `http://` vagy `https://` előtaggal kell kezdődniük. Egy egyszerű karakterlánc-egyezés fut, így a `http://www.contoso.com/` URL-előtag nem egyezik meg `http://www.contoso.com:80/` értékkel. Az iOS 10,0-es vagy újabb verzióiban az összes egyező érték megadásához egyetlen helyettesítő karaktert \* lehet használni. Például `http://*.contoso.com/` a `http://store.contoso.com/` és a `http://www.contoso.com` értéknek felel meg.

  A `http://.com` és a `https://.com` minták az összes HTTP-és HTTPS-URL-címet megegyeznek.

- Az **egyszeri bejelentkezést használó alkalmazások**: Az egyszeri bejelentkezést használó végfelhasználói eszközökön is **hozzáadhat** alkalmazásokat.

  A `AppIdentifierMatches` tömbnek tartalmaznia kell az alkalmazáscsomag-azonosítóknak megfelelő karakterláncokat. Ezek a karakterláncok lehetnek pontos egyezések, például `com.contoso.myapp`, vagy a \* helyettesítő karakter használatával megadhatják a köteg AZONOSÍTÓjának előtag-egyezését. A helyettesítő karakternek egy pont karakter (.) után kell megjelennie, és csak egyszer szerepelhet a karakterlánc végén, például `com.contoso.*`. A helyettesítő karakter használatakor az összes olyan alkalmazás hozzáférést kap a fiókhoz, amelynek a kötegazonosítója a megadott előtaggal kezdődik.

  Az **Alkalmazásnév** elemnél megadhat egy felhasználóbarát nevet, amely alapján könnyebben felismeri a kötegazonosítót.

- **Hitelesítőadat-megújítási tanúsítvány**: Ha tanúsítványokat használ a hitelesítéshez (nem a jelszavakhoz), válassza ki a meglévő SCEP-vagy PFX-tanúsítványt a hitelesítési tanúsítványként. Ez a tanúsítvány általában ugyanaz a tanúsítvány, amelyet más profilokhoz, például VPN-hez, Wi-Fi-hez vagy e-mailhez telepítenek a felhasználó számára.

## <a name="web-content-filter"></a>Webes tartalom szűrője

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Szűrő típusa**: Válassza az adott webhelyek engedélyezése lehetőséget. A választható lehetőségek:

  - **URL-címek konfigurálása**: Az Apple beépített webes szűrője, amely felnőtt kifejezéseket keres, beleértve a káromkodást és a szexuálisan explicit nyelvet. Ez a szolgáltatás kiértékeli az egyes weblapokat a betöltéskor, valamint azonosítja és blokkolja a nem megfelelő tartalmat. Olyan URL-címeket is hozzáadhat, amelyeket a szűrő nem szeretne ellenőrizni. Vagy letilthatja a megadott URL-címeket, az Apple-szűrők beállításaitól függetlenül.

    - **Engedélyezett URL-címek**: **Adja hozzá** az engedélyezni kívánt URL-címeket. Ezek az URL-címek megkerülik az Apple webes szűrőjét.

        > [!NOTE]
        > A beírt URL-címek azok az URL-címek, amelyeket nem szeretne evauluated az Apple Web Filter használatával. Ezek az URL-címek nem az engedélyezett webhelyek listája. Az engedélyezett webhelyek listájának létrehozásához állítsa be a **szűrő típusát** **adott webhelyekre**.

    - **Letiltott URL-címek**: **Adja hozzá** azokat az URL-címeket, amelyekről le szeretné állítani a megnyitását, függetlenül az Apple Web Filter beállításaitól.

  - **Csak meghatározott webhelyek** (csak a Safari böngésző esetében): Ezek az URL-címek hozzáadódnak a Safari böngésző könyvjelzői közé. A felhasználó számára **csak** a helyek meglátogatása engedélyezett; más helyek nem nyithatók meg. Akkor célszerű ezt a lehetőséget választani, ha a felhasználók által elérhető URL-ek listája pontosan ismert.

    - **URL-CÍM**: Adja meg az engedélyezni kívánt webhely URL-címét. Például írja be a következőt: `https://www.contoso.com`.
    - **Könyvjelző elérési útja**: Adja meg a könyvjelző tárolásának elérési útját. Például írja be a következőt: `/Contoso/Business Apps`. Ha nem adja meg az elérési utat, a könyvjelző az eszköz alapértelmezett könyvjelzőmappájába kerül.
    - **Cím**: Adjon meg egy leíró címet a könyvjelző számára.

    Ha nem ad meg URL-címet, a végfelhasználók nem férhetnek hozzá a webhelyekhez, kivéve `microsoft.com`, `microsoft.net` és `apple.com`. Az Intune automatikusan engedélyezi ezeket az URL-címeket.

## <a name="single-sign-on-app-extension"></a>Egyszeri bejelentkezési alkalmazás bővítménye

Ez a funkció az alábbiakra vonatkozik:

- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Egyszeri bejelentkezéses alkalmazás bővítményének típusa**: Válassza ki a hitelesítő adatok SSO-alkalmazásának típusát. Az SSO app Extension-profil mentésekor nem módosítható az egyszeri bejelentkezéses alkalmazás bővítményének típusa. A választható lehetőségek:

  - **Nincs konfigurálva**: Nem használják az alkalmazás-bővítményeket. Az alkalmazás-bővítmény letiltásához átválthatja az SSO-alkalmazás kiterjesztésének típusát a **Kerberos** vagy a **hitelesítő adatok** között, hogy **ne legyen konfigurálva**.
  - **Hitelesítő adat**: Használjon egy általános, testreszabható hitelesítőadat-alkalmazás-bővítményt az SSO végrehajtásához. Győződjön meg arról, hogy ismeri a szervezet SSO-alkalmazásának bővítmény-AZONOSÍTÓját.
  - **Kerberos**: Használja az Apple beépített Kerberos-bővítményét, amely az iOS 13,0 (és újabb) és a iPadOS 13,0 (és újabb verziók) része. Ez a beállítás a **hitelesítőadat** -alkalmazás kiterjesztésének Kerberos-specifikus verziója.

  > [!TIP]
  > A **hitelesítő adatok** típusával adja hozzá a saját konfigurációs értékeit, hogy áthaladjon a bővítményen. Ehelyett érdemes lehet az Apple által biztosított beépített konfigurációs beállításokat használni a **Kerberos** -típusban.

- **BŐVÍTMÉNY azonosítója** (csak hitelesítő adatok): Adja meg az SSO-alkalmazás kiterjesztését azonosító köteg-azonosítót, például `com.apple.extensiblesso`.
- **Csoport azonosítója** (csak hitelesítő adatok): Adja meg az egyszeri bejelentkezéses alkalmazás bővítményének csapat-azonosítóját. A csapat azonosítója az Apple által generált 10 karakteres alfanumerikus (számok és betűk) karakterlánc, például `ABCDE12345`. A csoport AZONOSÍTÓjának megadása nem kötelező.

  [Keresse meg a csoport azonosítóját (az](https://help.apple.com/developer-account/#/dev55c3c710c) Apple webhelyének megnyitása), amely további információkat tartalmaz.

- **Tartomány**: Adja meg a Kerberos-tartomány nevét. A tartománynevet tőkésíteni kell, például `CONTOSO.COM`. A tartománynév általában megegyezik a DNS-tartománynévvel, de minden nagybetűvel.

- **Tartományok**: Adja meg az egyszeri bejelentkezéssel hitelesíthető helyek tartomány-vagy állomásnevek nevét. Ha például a webhely `mysite.contoso.com`, akkor `mysite` az állomásnév, és a `contoso.com` a tartománynév. Ha a felhasználók bármelyik webhelyhez csatlakoznak, az alkalmazás-bővítmény kezeli a hitelesítési kihívást. Ez a hitelesítés lehetővé teszi a felhasználók számára a bejelentkezéshez a Face ID, a Touch ID vagy az Apple pincode/PIN-kód használatát.

  - Az egyszeri bejelentkezési alkalmazás bővítményének Intune-profiljainak minden tartományának egyedinek kell lennie. A tartományokat nem lehet megismételni a Bejelentkezési alkalmazás bővítményeinek egyik profiljában sem, még akkor is, ha különböző típusú egyszeri bejelentkezéses alkalmazás-bővítményeket használ.
  - Ezek a tartományok nem megkülönböztetik a kis-és nagybetűket

- **További konfiguráció** (csak hitelesítő adatok): Adja meg az egyszeri bejelentkezéses alkalmazás kiterjesztésére vonatkozó további, bővítményekre vonatkozó adatbevitelt:
  - **Konfigurációs kulcs**: Adja meg a hozzáadni kívánt elem nevét, például `user name`.
  - **Érték típusa**: Adja meg az adattípust. A választható lehetőségek:

    - Sztring
    - Logikai A **konfigurációs érték**mezőbe írja be a `True` vagy a `False` értéket.
    - Egész A **konfigurációs érték**mezőbe írjon be egy számot.
    
  - **Konfigurációs érték**: Adja meg az adatbevitelt.

  - **Hozzáadás**: A konfigurációs kulcsok hozzáadásához válassza a lehetőséget.

- **Kulcstartó használata** (csak Kerberos): A **blokkolás** gombra kattintva megakadályozhatja a jelszavak mentését és tárolását a kulcstartóban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszavak mentését és tárolását a kulcstartóban.
- **Face ID, Touch ID vagy PIN kód** (csak Kerberos): **Megkövetelheti** a felhasználóktól, hogy a hozzáadott tartományba való bejelentkezéshez megadják a Face ID, a Touch ID vagy az Apple PIN-kódot. **Nincs konfigurálva** (alapértelmezés) nem igényli, hogy a felhasználók biometrikus vagy PIN-kódot használjanak a bejelentkezéshez.
- **Alapértelmezett tartomány** (csak Kerberos): Válassza az **Engedélyezés** lehetőséget az alapértelmezett tartományként megadott **tartomány** értékének beállításához. **Nincs konfigurálva** (alapértelmezés) nem állítja be az alapértelmezett tartományt.

  > [!TIP]
  > - Akkor **engedélyezze** ezt a beállítást, ha több Kerberos SSO-alkalmazás-bővítményt konfigurál a szervezetében.
  > - Ha több birodalmat használ, **engedélyezze** ezt a beállítást. Az alapértelmezett tartományként megadott **tartományi** értéket állítja be.
  > - Ha csak egy tartománya van, hagyja meg, hogy **nincs konfigurálva** (alapértelmezett).

- **Egyszerű név** (csak Kerberos): Adja meg a Kerberos-tag felhasználónevét. Nem kell belefoglalni a tartománynevet. Például `user@contoso.com`, `user` az egyszerű név, és a `contoso.com` a tartománynév.
- **Active Directory Helykód** (csak Kerberos): Adja meg annak a Active Directory helynek a nevét, amelyet a Kerberos-bővítménynek használnia kell. Előfordulhat, hogy nem kell módosítania ezt az értéket, mivel a Kerberos-bővítmény automatikusan megkeresi a Active Directory hely kódját.
- **Gyorsítótár neve** (csak Kerberos): Adja meg a Kerberos-gyorsítótár általános biztonsági szolgáltatásainak (GSS) nevét. Valószínűleg nem kell beállítania ezt az értéket.
- Alkalmazáscsomag- **azonosítók** (csak Kerberos): **Adja hozzá** azokat az alkalmazáscsomag-azonosítókat, amelyeken egyszeri bejelentkezést kell használnia az eszközökön. Ezek az alkalmazások hozzáférést kapnak a Kerberos-jegy biztosításához, a hitelesítési jegyet, és hitelesítik a felhasználókat a hozzáférésre jogosult szolgáltatásokhoz.
- **Tartományi tartomány leképezése** (csak Kerberos): **Adja hozzá** a tartományhoz hozzárendelni kívánt tartományi DNS-utótagokat. Akkor használja ezt a beállítást, ha a gazdagépek DNS-nevei nem egyeznek a tartománynév nevével. Valószínűleg nem kell létrehoznia ezt az egyéni tartomány – tartomány társítást.

## <a name="wallpaper"></a>Háttérkép

Váratlan viselkedést tapasztalhat, ha egy rendszerkép nélküli profilt egy meglévő rendszerképpel rendelkező eszközhöz rendel hozzá. Létrehozhat például egy rendszerkép nélküli profilt. Ez a profil olyan eszközökhöz van rendelve, amelyeken már van rendszerkép. Ebben az esetben előfordulhat, hogy a rendszerkép módosul az eszköz alapértelmezett értékére, vagy az eredeti rendszerkép is marad az eszközön. Ezt a viselkedést az Apple MDM platformja szabályozza és korlátozza.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Háttérkép megjelenítési helye**: Válasszon egy helyet az eszközön a rendszerkép megjelenítéséhez. A választható lehetőségek:
  - **Nincs konfigurálva**: Nincs hozzáadva egyéni rendszerkép az eszközhöz. Az eszköz az operációs rendszer alapértelmezett értékeit használja.
  - **Zárolási képernyő**: Hozzáadja a rendszerképet a zárolási képernyőhöz.
  - **Kezdőképernyő**: Hozzáadja a rendszerképet a kezdőképernyő képernyőhöz.
  - **A zárolási képernyő és a kezdőképernyő**: Ugyanazt a rendszerképet használja a zárolási képernyőn és a kezdőképernyőn.
- **Háttérkép**: Töltsön fel egy meglévő. png,. jpg vagy. jpeg rendszerképet, amelyet használni szeretne. Győződjön meg arról, hogy a fájl mérete kisebb, mint 750 KB. **Eltávolíthatja** a hozzáadott rendszerképet is.

> [!TIP]
> Ha különböző képeket szeretne megjeleníteni a zárolási képernyőn és a kezdőképernyőn, hozzon létre egy profilt a zárolási képernyő képével. Hozzon létre egy másik profilt a kezdőképernyő képével. Mindkét profilt hozzárendelheti az iOS-felhasználókhoz vagy-eszközökhöz.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](../device-profile-monitor.md).

A [MacOS](macos-device-features-settings.md) -eszközökhöz is létrehozhat eszköz-szolgáltatási profilokat.
