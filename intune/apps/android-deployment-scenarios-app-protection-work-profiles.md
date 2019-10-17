---
title: Alkalmazás-védelmi szabályzatok és munkahelyi profilok a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg a különbségeket és az előnyeit és hátrányait, amikor az alkalmazás védelmi szabályzatait vagy munkahelyi profilokat használ a személyes vagy BYOD androidos vállalati eszközökhöz Microsoft Intuneban. Hasonlítsa össze az alkalmazás-védelmi szabályzatok beléptetése nélkül kapott különbségeket és funkciókat (APP-WE) és az Android Enterprise munkahelyi profilokat.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a2c71e04cf842fda7b16fb8ad4a05668ccbfaa84
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507601"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Alkalmazás-védelmi szabályzatok és munkahelyi profilok az Android Enterprise-eszközökön az Intune-ban

Számos szervezetnél a rendszergazdáknak a különböző eszközökön lévő erőforrások és az információk védelme érdekében kell megfellebbezni. Az egyik kihívás a személyes Android Enterprise-eszközökhöz, más néven a saját eszközökhöz (BYOD) használt felhasználók erőforrásainak védelme. A Microsoft Intune két androidos üzembe helyezési forgatókönyvet támogat a saját eszközökhöz (BYOD):

- Alkalmazás-védelmi szabályzatok regisztráció nélkül (APP-WE)
- Androidos vállalati munkahelyi profilok

Az APP-WE és az Android munkahelyi profil üzembe helyezési forgatókönyvei a következő fontos funkciókat tartalmazzák a BYOD-környezetekben:

1. **A szervezet által felügyelt adatmennyiség védelme és elkülönítése**: mindkét megoldás a szervezet adatainak védelmét a szervezet által felügyelt adatveszteség-megelőzési (DLP) vezérlők betartatásával védi. Ezek a védelem megakadályozza a védett adatszivárgások véletlen szivárgását, például a végfelhasználók véletlenül személyes alkalmazásba vagy fiókba való megosztását. Azt is biztosítják, hogy az adatokhoz hozzáférő eszköz kifogástalan állapotú legyen, és ne veszélyeztesse azokat.

2. **Végfelhasználói adatvédelem**: az App-We és az Android Enterprise munkahelyi profilok külön végfelhasználói tartalmat biztosítanak az eszközön, valamint a mobileszköz-felügyeleti (Mdm) rendszergazda által felügyelt adatokat. Mindkét esetben a rendszergazdák kikényszerítik a szabályzatokat, például a csak PIN-kód alapú hitelesítést a szervezet által felügyelt alkalmazásokon vagy identitásokon. A rendszergazdák nem tudják beolvasni, elérni vagy törölni a végfelhasználók tulajdonában lévő vagy azok által vezérelt felhasználókat.

Az APP-WE vagy az Android Enterprise munkahelyi profilok kiválasztása a BYOD való üzembe helyezéséhez a követelményektől és az üzleti igényektől függ. A cikk célja, hogy segítséget nyújtson a döntéshez.

## <a name="about-intune-app-protection-policies"></a>Tudnivalók az Intune app Protection-szabályzatokról

Az Intune app Protection-szabályzatok (alkalmazás) a felhasználókra irányuló adatvédelmi szabályzatok. A szabályzatok adatvesztés elleni védelmet alkalmaznak az alkalmazás szintjén. Az Intune ALKALMAZÁShoz az alkalmazás-fejlesztőknek engedélyeznie kell az alkalmazás funkcióit az általuk létrehozott alkalmazásokban.

Az egyes Android-alkalmazások több módon is engedélyezve vannak az ALKALMAZÁShoz:

1. **Natív módon integrálva a Microsoft első féltől származó alkalmazásaiba**: Microsoft Office androidos alkalmazások és más Microsoft-alkalmazások kiválasztása, az INTUNE-alkalmazás beépített része. Ezek az Office-alkalmazások, például a Word, a OneDrive, az Outlook stb., nincs szükség további testreszabásra a házirendek alkalmazásához. Ezeket az alkalmazásokat a végfelhasználók közvetlenül Google Play Áruház telepíthetik.

2. **A fejlesztők az INTUNE SDK-val integrálhatók az alkalmazásba**. az alkalmazások fejlesztői az Intune SDK-t integrálják a forráskódba, és újrafordítják alkalmazásaikat az Intune app Policy funkcióinak támogatásához.

3. **Becsomagolta az Intune alkalmazás-burkoló eszköz használatával**: egyes ügyfelek Android-alkalmazásokat fordítanak le (. APK-fájl) a forráskódhoz való hozzáférés nélkül. A forráskód nélkül a fejlesztő nem tud integrálni az Intune SDK-val. Az SDK nélkül nem tudják engedélyezni az alkalmazás alkalmazását az alkalmazás-szabályzatokhoz. Az alkalmazás-szabályzatok támogatásához a fejlesztőnek módosítania kell az alkalmazást, vagy újra kell visszaadnia.

    Az Intune segít az alkalmazás- **burkoló eszközön** a meglévő Android-alkalmazásokhoz (apk), és létrehoz egy alkalmazást, amely felismeri az alkalmazás-szabályzatokat.

    További információ erről az eszközről: [üzletági alkalmazások előkészítése az App Protection-házirendekhez](../developer/apps-prepare-mobile-application-management.md).

Az ALKALMAZÁSsal kompatibilis alkalmazások listájának megtekintéséhez tekintse [meg a felügyelt alkalmazások a Mobile Application Protection-szabályzatok gazdag készletét](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Üzembe helyezési forgatókönyvek

Ez a szakasz az APP-WE és az Android Enterprise Work Profile telepítési forgatókönyvek fontos jellemzőit ismerteti.

### <a name="app-we"></a>ALKALMAZÁS – WE

ALKALMAZÁS – a (z) rendszerbe állítást nem igénylő alkalmazások esetében a telepítés szabályzatokat határoz meg az alkalmazásokon, nem pedig az eszközökön. Ebben az esetben az eszközöket általában nem MDM-szolgáltató (például Intune) regisztrálja vagy kezeli. Az alkalmazások védelméhez és a szervezeti információhoz való hozzáféréshez a rendszergazdák az alkalmazás által felügyelhető alkalmazásokat használják, és adatvédelmi szabályzatokat alkalmazhatnak ezekre az alkalmazásokra.

Ez a funkció az alábbiakra vonatkozik:

- Android 4,4 és újabb verziók

> [!TIP]
> További információ: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

ALKALMAZÁS – olyan végfelhasználók számára, akik kis szervezeti lábnyomot szeretnének használni az eszközökön, és nem szeretnének regisztrálni a MDM. Rendszergazdaként továbbra is gondoskodnia kell az adatai biztonságáról. Ezek az eszközök nem kezelhetők. A gyakori MDM-feladatok és-funkciók (például a WiFi, az eszköz VPN és a Tanúsítványkezelő) nem tartoznak ennek a telepítési forgatókönyvnek a részébe.

### <a name="android-enterprise-work-profiles"></a>Androidos vállalati munkahelyi profilok

A munkahelyi profilok az androidos nagyvállalati telepítési forgatókönyvek, és az egyetlen olyan forgatókönyv, amely a BYOD használati eseteire irányul. A munkahelyi profil az Android operációs rendszer szintjén létrehozott különálló partíció, amelyet az Intune kezelhet.

Ez a funkció az alábbiakra vonatkozik:

- Android 5,0 és újabb rendszerű eszközök a Google Mobile Services

A munkahelyi profil a következő funkciókat tartalmazza:

- **Hagyományos Mdm funkciók**: a kulcsfontosságú Mdm képességek, például az alkalmazások életciklus-kezelése felügyelt Google Play használatával, bármilyen androidos vállalati környezetben elérhető. A felügyelt Google Play robusztus élményt nyújt az alkalmazások felhasználói beavatkozás nélküli telepítéséhez és frissítéséhez. Emellett az alkalmazások konfigurációs beállításait is leküldheti a szervezeti alkalmazásokba. Emellett nem szükséges, hogy a végfelhasználók az ismeretlen forrásból származó telepítéseket is engedélyezzék. Egyéb gyakori MDM tevékenységek, például tanúsítványok központi telepítése, WiFi/VPN-EK beállítása és az eszköz PIN-kód beállítása a munkahelyi profilokkal érhetők el.

- **DLP a munkahelyi profil határán**: például az App-We is kényszerítheti az adatvédelmi szabályzatok betartatását. Munkahelyi profillal a DLP-szabályzatok a munkahelyi profil szintjén érvényesek, nem az alkalmazás szintjére. A másolási/beillesztési védelmet például egy alkalmazásra alkalmazott Alkalmazásbeállítások, vagy a munkahelyi profil kényszeríti. Ha az alkalmazás munkahelyi profilba van telepítve, a rendszergazdák a szabályzat az alkalmazás szintjén való kikapcsolásával szüneteltetik a védelem másolását és beillesztését a munkahelyi profilba.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Tippek a munkahelyi profil élményének optimalizálásához

### <a name="when-to-use-app-within-work-profiles"></a>Mikor kell használni az alkalmazást a munkahelyi profilokon belül

Az Intune-alkalmazások és a munkahelyi profilok olyan kiegészítő technológiák, amelyek együtt vagy külön is használhatók. Építészeti szempontból mindkét megoldás kikényszeríti a szabályzatokat a különböző rétegeken – az alkalmazást az egyes alkalmazási rétegeken, a munkahelyi profilt pedig a profil rétegben. Egy alkalmazás-szabályzattal felügyelt alkalmazások telepítése egy munkahelyi profilban lévő alkalmazásra érvényes és támogatott forgatókönyv. Az alkalmazás, a munkahelyi profilok vagy a kombináció használata a DLP-követelményektől függ.

A munkahelyi profilok és alkalmazások kiegészítik egymás beállításait azáltal, hogy további lefedettséget biztosítanak, ha az egyik profil nem felel meg a szervezete adatvédelmi követelményeinek. Például a munkahelyi profilok nem natív módon biztosítanak olyan vezérlőket, amelyekkel korlátozható, hogy egy alkalmazás nem megbízható Felhőbeli tárolási helyre mentse. Az alkalmazás tartalmazza ezt a funkciót. Dönthet úgy, hogy a kizárólag a munkahelyi profil által biztosított DLP elegendő, és nem használja az alkalmazás használatát. Vagy megkövetelheti a kettő kombinációjának védelmét is.

### <a name="suppress-app-policy-for-work-profiles"></a>ALKALMAZÁS-házirend mellőzése munkahelyi profilokhoz

Előfordulhat, hogy támogatnia kell a több eszközt használó egyes felhasználókat – nem felügyelt eszközöket egy ALKALMAZÁSban, és a felügyelt eszközök munkahelyi profillal rendelkeznek.

Megkövetelheti például, hogy a végfelhasználók PIN-kódot adjanak meg a munkahelyi alkalmazások megnyitásakor. Az eszköztől függően a PIN-funkciókat az alkalmazás vagy a munkahelyi profil kezeli. Az APP-WE eszközök esetében a PIN-kód indítására szolgáló viselkedést az alkalmazás kényszeríti ki. Munkahelyi Profilos eszközök esetén az operációs rendszer által kényszerített eszköz-vagy munkahelyi profil-PIN-kódot használhat. A forgatókönyv végrehajtásához konfigurálja az Alkalmazásbeállítások beállításait, hogy azok ne legyenek érvényesek, *Amikor* egy alkalmazás munkahelyi profilba lett telepítve. Ha nem konfigurálja ezt a módszert, a végfelhasználónak meg kell adnia egy PIN-kódot az eszközön, majd ismét az alkalmazás rétegében.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Többszörös identitás viselkedésének vezérlése a munkahelyi profilokban

Az Office-alkalmazások, például az Outlook és a OneDrive "többszörös identitás" viselkedéssel rendelkeznek. Az alkalmazás egy példányán belül a végfelhasználó több különböző fiókhoz vagy felhőalapú tárolási helyhez is hozzáadhat kapcsolatokat. Az alkalmazásban az ezekről a helyekről beolvasott adatok elkülöníthetők vagy egyesíthetők. És a felhasználó a személyes identitások (user@outlook.com) és a szervezeti identitások (user@contoso.com) közötti helyi váltást is végezhet.

Munkahelyi profilok használata esetén érdemes lehet letiltani a többszörös identitás működését. Ha letiltja, a munkahelyi profilban az alkalmazás jelvényes példányai csak a szervezet identitásával konfigurálhatók. Az Office Android-alkalmazások támogatásához használja az engedélyezett fiókok alkalmazás konfigurációs beállítását.

További információ: [az Outlook telepítése iOS-és Android-alkalmazásokhoz konfigurációs beállítások](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>Mikor kell használni az Intune-alkalmazást?

Több nagyvállalati mobilitási forgatókönyv van, ahol az Intune-alkalmazás használata ajánlott.

### <a name="older-devices-running-android-44-51-are-being-used"></a>Az Android 4.4-5.1-et futtató régebbi eszközök használata folyamatban van

Hivatalosan a Google Mobile Services-mel vagy újabb verzióval ellátott Android-5,0 eszköz támogatja a munkahelyi profilokat, és így jogosult a felügyeletre. Néhány OEM-es Android 5,0-es és 5,1-es eszköz azonban nem támogatja a munkahelyi profilokat.

Ha olyan verziókat használ, amelyek nem támogatják a munkahelyi profilokat, és az eszközökön lévő, a szervezet adataihoz tartozó DLP biztosítására van szükség, akkor az Intune-alkalmazások funkcióit

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Nincs MDM, nincs beléptetés, a Google szolgáltatásai nem érhetők el

Egyes ügyfelek nem szeretnének az eszközök felügyeletének bármilyen formáját, beleértve a munkahelyi profil kezelését, különböző okokból:

- Jogi és felelősségi okok
- A felhasználói élmény konzisztenciája érdekében
- Az Android-eszköz környezete rendkívül heterogén
- Nincs olyan kapcsolat a Google Services szolgáltatással, amely szükséges a munkahelyi profil kezeléséhez.

A (z) vagy a Kínában lévő felhasználók például nem használhatják az Android-eszközök felügyeletét, mivel a Google szolgáltatások le vannak tiltva. Ebben az esetben használja a DLP-hez készült Intune-alkalmazást.

## <a name="summary"></a>Összefoglalás

Az Intune-nal az androidos BYOD programhoz az APP-WE és az Android Enterprise munkahelyi profilok is elérhetők. Az APP-WE vagy a Work profilok kiválasztása az üzleti és használati követelményektől függ. Az összefoglalás területen használjon munkahelyi profilokat, ha a felügyelt eszközökön, például a MDM, az alkalmazás leküldésekor és így tovább van szüksége a tevékenységekre. ALKALMAZÁS használata – Ha nem szeretné, vagy nem tudja kezelni az eszközöket, és csak az Intune APP-kompatibilis alkalmazásokat használja.

## <a name="next-steps"></a>További lépések
Az [alkalmazás-védelmi szabályzatok használatának megkezdése](app-protection-policy.md)vagy [az eszközök regisztrálása](../enrollment/android-enroll.md).
