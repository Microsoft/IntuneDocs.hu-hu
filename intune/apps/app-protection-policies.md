---
title: Alkalmazásvédelmi szabályzatok létrehozása és telepítése
titleSuffix: Microsoft Intune
description: Ez a témakör bemutatja, hogyan hozhat létre és rendelhet hozzá Microsoft Intune app Protection-házirendeket (alkalmazást).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8e105dae43c4e7139c8e44a8c6535baebe31cc4
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585480"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Megtudhatja, hogyan hozhat létre és rendelhet hozzá Microsoft Intune app Protection-házirendeket (alkalmazást) a szervezet felhasználói számára. A témakör a meglévő szabályzatok módosítását is ismerteti.

## <a name="before-you-begin"></a>Előkészületek

Az alkalmazásvédelmi szabályzatok vonatkozhatnak az Intune által felügyelt és nem felügyelt eszközökön futó alkalmazásokra is. Részletesebb információ az alkalmazásvédelmi szabályzatok működéséről és az Intune alkalmazásvédelmi szabályzatai által támogatott forgatókönyvekről: [A Microsoft Intune alkalmazásvédelmi szabályzatai](app-protection-policy.md)

Amennyiben az MAM által támogatott alkalmazások listáját keresi, lásd az [MAM alkalmazáslistáját](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

További információk a cég üzletági (LOB) alkalmazásainak a Microsoft Intune-hoz való hozzáadásáról az alkalmazásvédelmi szabályzatok előkészítése céljából: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md).

Az alkalmazás-védelmi szabályzat létrehozásának folyamata jelenleg a platformtól függően eltérő:
- Alkalmazás-védelmi szabályzatok iOS/iPadOS és Android-alkalmazásokhoz
- Alkalmazás-védelmi szabályzatok Windows 10-es alkalmazásokhoz

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>Alkalmazás-védelmi szabályzatok iOS/iPadOS és Android-alkalmazásokhoz

Ha iOS-/iPadOS-és Android-alkalmazásokhoz hoz létre alkalmazás-védelmi szabályzatot, egy új alkalmazás-védelmi házirendet eredményező modern Intune-folyamatot követ.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>IOS-/iPadOS-vagy Android-alkalmazás-védelmi szabályzat létrehozása
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Az Intune-portálon válassza az **ügyfélalkalmazások**  > **app Protection-házirendek**elemet. Ekkor megnyílik az **Alkalmazásvédelmi szabályzatok** panel, amelyen új szabályzatokat hozhat létre, és szerkesztheti a meglévőket.
3. Válassza a **házirend létrehozása** lehetőséget, és válassza az **iOS/IPadOS** vagy az **Android**lehetőséget. Megjelenik a **szabályzat létrehozása** panel.
4. Az **alapvető beállítások** lapon adja hozzá a következő értékeket:

    | Érték | Description |
    |--------------|------------------------------------------------|
    | Név | Az alkalmazás védelmi szabályzatának neve. |
    | Description | Választható Az alkalmazás védelmi szabályzatának leírása. |


    A **platform** értéke a fenti választás alapján van beállítva.

    ![Képernyőkép a szabályzat létrehozása panel alapismeretek lapján](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Az **alkalmazások** lap megjelenítéséhez kattintson a **tovább** gombra.<br>
    Az **alkalmazások** oldalon kiválaszthatja, hogyan szeretné alkalmazni a szabályzatot különböző eszközökön futó alkalmazásokra. Legalább egy alkalmazást fel kell vennie.<p>
    
    | Érték/beállítás | Description |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Az alkalmazások célzása minden eszköz típusán | Ezzel a beállítással a szabályzatot a felügyeleti állapotú eszközökön futó alkalmazásokra is megcélozhatja. Válassza a **nem** lehetőséget az alkalmazások célzásához adott eszközökön. |
    |     Eszközök típusai | Ezzel a beállítással adhatja meg, hogy a szabályzat a MDM által felügyelt vagy nem felügyelt eszközökre vonatkozzon-e. IOS-ALKALMAZÁSokra vonatkozó szabályzatok esetén válasszon a nem **felügyelt** és **felügyelt** eszközök közül. Android-ALKALMAZÁSokra vonatkozó szabályzatok esetén válassza a nem **felügyelt**, **androidos eszközök rendszergazdája**és az **Android Enterprise**lehetőséget.  |
    | Nyilvános alkalmazások | Kattintson a **nyilvános alkalmazások kiválasztása** lehetőségre a célként használandó alkalmazások kiválasztásához. |
    | Egyéni alkalmazások | Az **egyéni alkalmazások kiválasztása** lehetőségre kattintva kiválaszthat egy köteg-azonosító alapján megcélzott egyéni alkalmazásokat. |
    
    A kiválasztott alkalmazás (ok) megjelenik a nyilvános és az egyéni alkalmazások listájában. 
6. Az **Adatvédelem** lap megjelenítéséhez kattintson a **tovább** gombra.<br>
    Ezen a lapon megtekintheti az adatveszteség-megelőzési (DLP) vezérlők beállításait, beleértve a kivágási, másolási, beillesztési és mentési korlátozásokat is. Ezek a beállítások határozzák meg, hogy a felhasználók hogyan használják az adatvédelmi szabályzat hatálya alá eső alkalmazásokban lévő adatszolgáltatásokat.

    **Adatvédelmi beállítások**:<br>
    - **iOS/iPadOS adatvédelem** – további információ: [iOS-alkalmazás védelmi szabályzatának beállításai – adatvédelem](~/apps/app-protection-policy-settings-ios.md#data-protection).
    - **Android-adatvédelem** – további információért lásd: az [Android-alkalmazások védelmi házirendjének beállításai – adatvédelem](~/apps/app-protection-policy-settings-android.md#data-protection).

7. A **hozzáférési követelmények** lap megjelenítéséhez kattintson a **tovább** gombra.<br>
    Ezen a lapon megadhatja a PIN-kód és a hitelesítő adatok azon követelményeit, amelyeket a felhasználóknak meg kell felelniük az alkalmazások munkahelyi környezetben való eléréséhez. 
 
    **Hozzáférési követelmények beállításai**:<br>
    - **iOS/iPadOS hozzáférési követelmények** – további információért lásd: az [iOS-alkalmazások védelmi házirendjének beállításai – hozzáférési követelmények](~/apps/app-protection-policy-settings-ios.md#access-requirements).
    - **Android-hozzáférési követelmények** – további információért lásd: az [Android-alkalmazások védelmi házirendjének beállításai – hozzáférési követelmények](~/apps/app-protection-policy-settings-android.md#access-requirements).

8. Kattintson a **tovább** gombra a **feltételes indítási** oldal megjelenítéséhez.<br>
    Ezen a lapon adhatók meg az alkalmazás-védelmi szabályzat bejelentkezési biztonsági követelményei. Válasszon egy **Beállítást**, és adjon meg egy **Értéket**, amelynek a felhasználónak meg kell felelnie ahhoz, hogy bejelentkezhessen a vállalati alkalmazásába. Ezután válassza ki azt a **műveletet** , amelyet el szeretne végezni, ha a felhasználók nem felelnek meg a követelményeknek. Bizonyos esetekben egy beállításhoz több művelet is megadható.

    **Feltételes indítási beállítások**:<br>
    - **iOS/iPadOS feltételes indítás** – további információért lásd: az [iOS-alkalmazások védelmi házirendjének beállításai – feltételes indítás](~/apps/app-protection-policy-settings-ios.md#conditional-launch).
    - **Android feltételes indítás** – további információért lásd: [Android-alkalmazás védelmi házirendjének beállításai – feltételes indítás](~/apps/app-protection-policy-settings-android.md#conditional-launch).

7. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.<br>
   A **hozzárendelések** lapon engedélyezheti az alkalmazás-védelmi házirendet a felhasználók csoportjaihoz. 
8. Kattintson a **Tovább gombra: felülvizsgálat + létrehozás** elemre, és tekintse át az alkalmazás védelmi házirendjéhez megadott értékeket és beállításokat.
9. Ha elkészült, kattintson a **Létrehozás** gombra az alkalmazás-védelmi szabályzat létrehozásához az Intune-ban. 

## <a name="app-protection-policies-for-windows-10-apps"></a>Alkalmazás-védelmi szabályzatok Windows 10-es alkalmazásokhoz

Ha Windows 10-es alkalmazásokhoz hoz létre alkalmazás-védelmi szabályzatot, az Intune egy klasszikus folyamatát fogja követni.

### <a name="create-a-windows-10-app-protection-policy"></a>Windows 10 app Protection-szabályzat létrehozása
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Az Intune-portálon válassza az **ügyfélalkalmazások**  > **app Protection-házirendek**elemet. Ekkor megnyílik az **Alkalmazásvédelmi szabályzatok** panel, amelyen új szabályzatokat hozhat létre, és szerkesztheti a meglévőket.
3. Válassza a **házirend létrehozása**lehetőséget.

    <img alt="Screenshot of the 'Create policy' blade for Windows 10" src="~/apps/media/app-protection-policies/app-protection-add-policy.png" width="350">

4. Adja meg a szabályzat nevét, egy rövid leírást, és válassza ki a szabályzat platformtípusát. Az egyes platformokon egynél több szabályzatot is beállíthat.

4. Dönthet úgy, hogy az **összes típusú alkalmazást Megcélozja**. Ez a beállítás lehetővé teszi, hogy a szabályzatot bármilyen felügyeleti állapotú eszközön lévő alkalmazásokba célozza. A házirend ütközésének feloldása során a rendszer felülírja ezt a beállítást, ha egy felhasználó egy adott felügyeleti állapotra vonatkozó házirendet tartalmaz. További információ: [Eszközkezelési állapottól függő alkalmazásvédelmi szabályzatok](~/apps/app-protection-policies.md#target-app-protection-policies-based-on-device-management-state).

5. Válassza az **Alkalmazások** elemet az **Alkalmazások** panel megnyitásához, ahol megjelenik a rendelkezésre álló alkalmazások listája. Egy vagy több alkalmazást is kijelölhet a listában a létrehozott szabályzattal való társításra. Jelöljön ki legalább egy alkalmazást a szabályzat létrehozásához.  

6. Az alkalmazások kijelölése után a mentéshez válassza a **Kiválasztás** lehetőséget.

7. A **Szabályzat hozzáadása** panelen válassza a **Kötelező beállítások konfigurálása** lehetőséget a **Beállítások** megnyitásához.

   A szabályzatra vonatkozó beállítások három kategóriába tartoznak:
   - **Adatvédelem** – ez a csoport tartalmazza az adatveszteség-megelőzési (DLP) vezérlőket, például a kivágási, másolási, beillesztési és mentési korlátozásokat. Ezek a beállítások szabják meg, hogy hogyan kezelhetik a felhasználók az adatokat az alkalmazásokban.
   - **Hozzáférési követelmények** – Ez a csoport tartalmazza a PIN-kód alkalmazásonkénti beállítási lehetőségeit, amelyek meghatározzák, hogyan férnek hozzá a végfelhasználók az alkalmazásokhoz egy munkahelyi környezetben.  
   - **Feltételes bevezetés** – Ebbe a csoportba olyan beállítások tartoznak, mint az operációs rendszerre vonatkozó minimális beállítások, a függetlenítésészlelés és a rootolt eszközök felderítése, valamint az offline türelmi időszakok.

   Használatuk megkönnyítése érdekében a szabályzatbeállításoknak alapértelmezett értékük van. Ha az alapértelmezett értékek megfelelnek az elvárásainak, nem szükséges változtatnia.

   > [!TIP]
   > A szabályzat beállításai csak akkor lépnek érvénybe, ha munkahelyi környezetben használják az alkalmazásokat. Ha a végfelhasználók az alkalmazást személyes célra használják, nem vonatkoznak rájuk a ezek szabályzatok. Figyelje meg, hogy a létrehozott új fájlokat személyes fájlként kezeli a rendszer. 

8. A konfiguráció mentéséhez válassza az **OK** gombot. Ekkor visszakerül a **Szabályzat hozzáadása** panelre.
9. Válassza a **Létrehozás** lehetőséget a szabályzat létrehozásához és a beállítások mentéséhez.

Az Ön által létrehozott új Windows 10-es házirendek nincsenek hozzárendelve a felhasználókhoz, amíg erre kifejezetten nem kerül sor. Windows 10 házirend hozzárendeléséhez tekintse [meg a Windows 10-es szabályzatok felhasználók számára való hozzárendelését](~/apps/app-protection-policies.md#assign-a-windows-10-policy-to-users) ismertető témakört.

### <a name="assign-a-windows-10-policy-to-users"></a>Windows 10-es házirend társítása a felhasználókhoz 

1. Jelöljön ki egy szabályzatot az **Alkalmazásvédelmi szabályzatok** panelen.

2. Az ***Intune App Protection** panelen a **Hozzárendelések** lehetőség választásával nyissa meg az **Intune App Protection – Hozzárendelések** panelt. A *Befoglalás* lapon válassza a **Belefoglalandó csoportok kijelölése** lehetőséget. 

   ![Képernyőkép a hozzárendelések panelről, és válassza ki a kívánt csoportokat menüt](./media/app-protection-policies/app-protection-policy-add-users.png)

3. Megjelenik egy lista, amelyen az **Azure Active Directory** összes biztonsági csoportja szerepel. Válassza ki azokat a felhasználói csoportokat, amelyekhez hozzá szeretné rendelni a szabályzatot, és válassza a **Kiválasztás** elemet. 

    ![Képernyőkép a felhasználói csoport hozzáadása panelről az Azure AD-felhasználók listájával](./media/app-protection-policies/azure-ad-user-group-list.png)

4. A csoportok belefoglalása és kizárása után a **Mentés** gombra kattintva mentse a konfigurációt, és telepítse a szabályzatot a felhasználók számára. Ha a konfiguráció mentése előtt kiválasztja az **Elvetés** lehetőséget, a rendszer elveti a *belefoglalási* és *kizárási* lapokon végrehajtott összes módosítást.   
 
     ![A mentési és elvetési beállításokat ábrázoló képernyőkép](./media/app-protection-policies/save-assignment.png)
  
A szabályzat ezzel létrejött, és telepítve lett a felhasználók számára.

A szabályzat csak a Microsoft Intune-licenccel rendelkező felhasználókra érvényes. A kijelölt biztonsági csoporthoz tartozó, Intune-licenccel nem rendelkező felhasználókra a szabályzat nem vonatkozik.

>[!IMPORTANT]
> Ha az Intune-ban és a Configuration Managerben kezeli az eszközöket, a szabályzat csak a kijelölt csoport közvetlen felhasználói esetében lép érvénybe. A csoportba ágyazott alárendelt csoportok tagjaira a szabályzat nem vonatkozik.

A végfelhasználók az App Store-ból vagy a Google Play áruházból tölthetik le az alkalmazásokat. További információkért lásd:
* [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-android.md)
* [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-ios.md)

### <a name="change-existing-windows-10-policies"></a>Meglévő Windows 10-es házirendek módosítása
A meglévő szabályzatokat szerkesztheti, és alkalmazhatja azokat a megcélzott felhasználókra. Ha azonban a meglévő szabályzatok módosításakor a felhasználók már be voltak jelentkezve az alkalmazásokba, csak egy 8 órás időszak elteltével láthatják a változtatásokat.

A változtatások hatásának érzékeléséhez a felhasználónak ki kell jelentkeznie az alkalmazásból, majd újból be kell jelentkeznie.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>A szabályzathoz társított alkalmazások listájának módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. Az alkalmazások listájának megnyitásához az *Intune App Protection* panelen válassza a **Célzott alkalmazások** lehetőséget.

3. A listában eltávolíthat vagy hozzáadhat alkalmazásokat, majd a **Mentés** ikont választva mentheti a módosításokat.

#### <a name="to-change-the-list-of-user-groups"></a>A felhasználói csoportok listájának módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. Az *Intune App Protection* panelen a **Hozzárendelések** választásával nyissa meg az **Intune App Protection - Hozzárendelések** panelt, amelyen megjelenik azoknak a felhasználói csoportoknak a listája, amelyekre a szabályzat jelenleg érvényes.

3. Új felhasználói csoportot úgy adhat hozzá a szabályzathoz, hogy a *Belefoglalás* lapon a **befoglalandó csoportok kijelölése** lehetőséget választja, majd kiválasztja a felhasználói csoportot. A csoport hozzáadásához válassza a **kiválasztás** lehetőséget. 

4. Felhasználói csoport kizárásához a *kizárás* lapon válassza a **kizárni kívánt csoportok kiválasztása**lehetőséget, majd válassza ki a felhasználói csoportot. A felhasználói csoport eltávolításához válassza a **Kiválasztás** lehetőséget.  

5. A korábban hozzáadott csoportok törléséhez a *Belefoglalás* vagy *kizárás* lapon válassza a három pontot (...), és válassza a **Törlés**lehetőséget. 

5. A hozzárendelések módosítása után a **Mentés** gombra kattintva mentse a konfigurációt, és telepítse a szabályzatot az új felhasználók csoportba. Ha a konfiguráció mentése előtt kiválasztja az **Elvetés** lehetőséget, a rendszer elveti a *belefoglalási* és *kizárási* lapokon végrehajtott összes módosítást.

### <a name="to-change-windows-10-policy-settings"></a>A Windows 10-es házirend beállításainak módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. Az Ön által szerkeszthető beállítási területek listájának megnyitásához az *Intune App Protection* panelen válassza a **Tulajdonságok** lehetőséget. 

3. Válassza ki a módosítani kívánt beállítást tartalmazó területet, például az **Adatáthelyezést** vagy a **Hozzáférési követelményeket**. Módosítsa a beállításokat az új értékre.

4. A módosítások mentéséhez válassza a **Mentés** ikont. Ismételje a beállítási terület kiválasztásából, a módosításból és végül annak mentéséből álló folyamatot addig, amíg el nem készül minden módosítással. Ekkor bezárhatja az *Intune App Protection – Tulajdonságok* panelt. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Eszközkezelési állapottól függő alkalmazásvédelmi szabályzatok
Vállalatoknál gyakori, hogy a felhasználóknak engedélyezett mind az Intune által felügyelt (MDM) eszközök használata, mind pedig a nem felügyelt, csak az Intune alkalmazásvédelmi szabályzatok által védett eszközök használata. A nem felügyelt eszközöket gyakran saját (BYOD-) eszközöknek nevezik.

Mivel az Intune alkalmazásvédelmi szabályzatok a felhasználói identitásra irányulnak, a felhasználók védelmi beállításait a rendszer alkalmazhatja mind a regisztrált (MDM által felügyelt), mind pedig a regisztrálatlan (MDM nélküli) eszközökre. Emiatt lehetősége van megadni, hogy az Intune alkalmazásvédelmi szabályzatot az Intune-ban regisztrált vagy regisztrálatlan iOS- és Android-eszközökre kívánja-e alkalmazni. A nem felügyelt eszközökre vonatkozóan egyetlen védelmi szabályzattal rendelkezhet, amelyben szigorú adatvesztés-megelőzési (DLP) vezérlők találhatók, valamint egy külön védelmi szabályzat a MDM által felügyelt eszközökhöz, ahol a DLP-vezérlők valamivel nyugodtabbak lehetnek. További információ arról, hogy ez hogyan működik a személyes Android Enterprise-eszközökön: [alkalmazás-védelmi szabályzatok és munkahelyi profilok](android-deployment-scenarios-app-protection-work-profiles.md).

A szabályzatok létrehozásához navigáljon az Intune-konzolon az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** lapra, majd kattintson a **Szabályzat létrehozása** elemre. Másik lehetőségként egy meglévő alkalmazásvédelmi szabályzatot is szerkeszthet. Ahhoz, hogy az alkalmazás védelmi szabályzata a felügyelt és a nem felügyelt eszközökre is vonatkozzon, navigáljon az **alkalmazások** lapra, és győződjön meg róla, hogy az **összes eszközön a cél az alkalmazásokhoz** beállítás értéke **Igen**, az alapértelmezett érték. Ha azt szeretné, hogy a rendszer részletesen hozzárendelje a hozzárendelést a felügyeleti állapot alapján, a **nem**értékre állítsa a **cél alkalmazást az összes eszközön** . 

![Képernyőfelvétel a szabályzat hozzáadása panel és a cél között az összes alkalmazás típusához](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>Alkalmazástípusok

- Nem **felügyelt eszközökön futó alkalmazások**: a nem felügyelt eszközök olyan eszközök, amelyeken az Intune Mdm-felügyelet nem észlelhető. Ez magában foglalja a harmadik féltől származó MDM-szállítókat is.
- **Intune által felügyelt eszközökön futó alkalmazások**: a felügyelt eszközöket az Intune Mdm kezeli.
- **Androidos munkahelyi profilban szereplő alkalmazások**: az Android Enterprise Work Profile-eszközökként regisztrált felügyelt eszközök.

> Megjegyzés androidos eszközök esetén a rendszer felszólítja, hogy telepítse a Intune Céges portál alkalmazást, függetlenül attól, hogy melyik alkalmazás típusa van kiválasztva. Ha például az "alkalmazások az Intune által felügyelt eszközökön" lehetőséget választja, akkor a nem felügyelt Android-eszközökkel rendelkező felhasználók továbbra is megtalálhatók.

IOS esetén további alkalmazás-konfigurációs beállításokra van szükség az alkalmazás-beállítások az Intune-ban regisztrált eszközökön futó alkalmazások számára történő megcélzásához:

- Az **IntuneMAMUPN** beállítást az MDM által felügyelt összes alkalmazáshoz be kell állítani. További információért lásd: [iOS-alkalmazások közti adatátvitel felügyelete a Microsoft Intune-ban](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- Az **IntuneMAMDeviceID** beállítást az összes külső féltől származó és az MDM által felügyelt üzletági alkalmazáshoz be kell állítani. Az **IntuneMAMDeviceID** beállítást az eszközazonosító jogkivonatra kell konfigurálni. Például `key=IntuneMAMDeviceID, value={{deviceID}}`. További információt az [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz](app-configuration-policies-use-ios.md) című témakörben talál.
- Amennyiben csak az **IntuneMAMDeviceID** van konfigurálva, az Intune APP nem felügyeltnek tekinti az eszközt.

> [!NOTE]
> Ha kifejezetten iOS-eszközökre vonatkozó támogatási információkat keres az alkalmazásvédelmi szabályzatok eszközkezelési állapottól függő alkalmazásáról, lásd: [MAM-alapú védelmi szabályzatok alkalmazása eszközkezelési állapot alapján](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Szabályzatbeállítások
Az iOS és az Android szabályzatbeállításait tartalmazó lista megtekintéséhez válasszon a következő hivatkozások közül:

- [iOS-szabályzatok](app-protection-policy-settings-ios.md)
- [Android-szabályzatok](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>További lépések
[A megfelelőség és a felhasználói állapot figyelése](app-protection-policies-monitor.md)

## <a name="see-also"></a>További információ
* [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-android.md)
* [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-ios.md)
