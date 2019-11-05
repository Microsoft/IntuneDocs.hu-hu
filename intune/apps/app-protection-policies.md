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
ms.openlocfilehash: 98976403d58c33f22f7ceeabec1d38f076f9bbe7
ms.sourcegitcommit: ae6f2e7812e7fd36f2393b8f4b6cd8de63777b2c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73592071"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Megtudhatja, hogyan hozhat létre és rendelhet hozzá Microsoft Intune app Protection-házirendeket (alkalmazást) a szervezet felhasználói számára. A témakör a meglévő szabályzatok módosítását is ismerteti.

## <a name="before-you-begin"></a>Előkészületek

Az alkalmazásvédelmi szabályzatok vonatkozhatnak az Intune által felügyelt és nem felügyelt eszközökön futó alkalmazásokra is. Részletesebb információ az alkalmazásvédelmi szabályzatok működéséről és az Intune alkalmazásvédelmi szabályzatai által támogatott forgatókönyvekről: [A Microsoft Intune alkalmazásvédelmi szabályzatai](app-protection-policy.md)

Amennyiben az MAM által támogatott alkalmazások listáját keresi, lásd az [MAM alkalmazáslistáját](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

További információk a cég üzletági (LOB) alkalmazásainak a Microsoft Intune-hoz való hozzáadásáról az alkalmazásvédelmi szabályzatok előkészítése céljából: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md).

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
    | Az alkalmazások célzása minden eszköz típusán | Ezzel a beállítással a szabályzatot a felügyeleti állapotú eszközökön futó alkalmazásokra is megcélozhatja. Válassza a **nem** lehetőséget az alkalmazások célzásához adott eszközökön. További információ: [a TARGET app Protection-szabályzatok az eszközkezelés alapján](#target-app-protection-policies-based-on-device-management-state) |
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

9. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.<br>
   A **hozzárendelések** lapon engedélyezheti az alkalmazás-védelmi házirendet a felhasználók csoportjaihoz.
   
    >[!IMPORTANT]
    > Ha az Intune-ban és a Configuration Managerben kezeli az eszközöket, a szabályzat csak a kijelölt csoport közvetlen felhasználói esetében lép érvénybe. A csoportba ágyazott alárendelt csoportok tagjaira a szabályzat nem vonatkozik.

10. Kattintson a **Tovább gombra: felülvizsgálat + létrehozás** elemre, és tekintse át az alkalmazás védelmi házirendjéhez megadott értékeket és beállításokat.

11. Ha elkészült, kattintson a **Létrehozás** gombra az alkalmazás-védelmi szabályzat létrehozásához az Intune-ban. 

    > [!TIP]
    > A szabályzat beállításai csak akkor lépnek érvénybe, ha munkahelyi környezetben használják az alkalmazásokat. Ha a végfelhasználók az alkalmazást személyes célra használják, nem vonatkoznak rájuk a ezek szabályzatok. Figyelje meg, hogy a létrehozott új fájlokat személyes fájlként kezeli a rendszer. 

A végfelhasználók az App Store-ból vagy a Google Play áruházból tölthetik le az alkalmazásokat. További információkért lásd:
* [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-android.md)
* [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>A meglévő szabályzatok módosítása
A meglévő szabályzatokat szerkesztheti, és alkalmazhatja azokat a megcélzott felhasználókra. Ha azonban a meglévő szabályzatok módosításakor a felhasználók már be voltak jelentkezve az alkalmazásokba, csak egy 8 órás időszak elteltével láthatják a változtatásokat.

A változtatások hatásának érzékeléséhez a felhasználónak ki kell jelentkeznie az alkalmazásból, majd újból be kell jelentkeznie.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>A szabályzathoz társított alkalmazások listájának módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. A *Intune app Protection* ablaktáblán válassza a **Tulajdonságok**lehetőséget.

3. Az *alkalmazások*című szakasz mellett válassza a **Szerkesztés**lehetőséget.

4. Az **alkalmazások** oldalon kiválaszthatja, hogyan szeretné alkalmazni a szabályzatot különböző eszközökön futó alkalmazásokra. Legalább egy alkalmazást fel kell vennie.<p>
    
    | Érték/beállítás | Description |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Az alkalmazások célzása minden eszköz típusán | Ezzel a beállítással a szabályzatot a felügyeleti állapotú eszközökön futó alkalmazásokra is megcélozhatja. Válassza a **nem** lehetőséget az alkalmazások célzásához adott eszközökön. További információ: [a TARGET app Protection-szabályzatok az eszközkezelés alapján](#target-app-protection-policies-based-on-device-management-state) |
    |     Eszközök típusai | Ezzel a beállítással adhatja meg, hogy a szabályzat a MDM által felügyelt vagy nem felügyelt eszközökre vonatkozzon-e. IOS-ALKALMAZÁSokra vonatkozó szabályzatok esetén válasszon a nem **felügyelt** és **felügyelt** eszközök közül. Android-ALKALMAZÁSokra vonatkozó szabályzatok esetén válassza a nem **felügyelt**, **androidos eszközök rendszergazdája**és az **Android Enterprise**lehetőséget.  |
    | Nyilvános alkalmazások | Kattintson a **nyilvános alkalmazások kiválasztása** lehetőségre a célként használandó alkalmazások kiválasztásához. |
    | Egyéni alkalmazások | Az **egyéni alkalmazások kiválasztása** lehetőségre kattintva kiválaszthat egy köteg-azonosító alapján megcélzott egyéni alkalmazásokat. |

    A kiválasztott alkalmazás (ok) megjelenik a nyilvános és az egyéni alkalmazások listájában. 

5. A Szabályzathoz kiválasztott alkalmazások áttekintéséhez kattintson a **felülvizsgálat + létrehozás** elemre.

6. Ha elkészült, kattintson a **Mentés** gombra az alkalmazás védelmi házirendjének frissítéséhez.
 
#### <a name="to-change-the-list-of-user-groups"></a>A felhasználói csoportok listájának módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. A *Intune app Protection* ablaktáblán válassza a **Tulajdonságok**lehetőséget.

3. A *hozzárendelések*című szakasz mellett válassza a **Szerkesztés**lehetőséget.

4. Új felhasználói csoportot úgy adhat hozzá a szabályzathoz, hogy a *Belefoglalás* lapon a **befoglalandó csoportok kijelölése** lehetőséget választja, majd kiválasztja a felhasználói csoportot. A csoport hozzáadásához válassza a **kiválasztás** lehetőséget. 

5. Felhasználói csoport kizárásához a *kizárás* lapon válassza a **kizárni kívánt csoportok kiválasztása**lehetőséget, majd válassza ki a felhasználói csoportot. A felhasználói csoport eltávolításához válassza a **Kiválasztás** lehetőséget.  

6. A korábban hozzáadott csoportok törléséhez a *Belefoglalás* vagy *kizárás* lapon válassza a három pontot (...), és válassza a **Törlés**lehetőséget.

7. A házirendhez kiválasztott felhasználói csoportok áttekintéséhez kattintson a **felülvizsgálat + létrehozás** elemre.

8. A hozzárendelések módosítása után a **Mentés** gombra kattintva mentse a konfigurációt, és telepítse a szabályzatot az új felhasználók csoportba. Ha a **Mégse gombra** kattint a konfiguráció mentése előtt, elveti a *belefoglalási* és *kizárási* lapokon végrehajtott összes módosítást.

### <a name="to-change-policy-settings"></a>A szabályzatbeállítások módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. A *Intune app Protection* ablaktáblán válassza a **Tulajdonságok**lehetőséget.

3. A módosítani kívánt beállításokhoz tartozó szakasz mellett válassza a **Szerkesztés**lehetőséget. Módosítsa a beállításokat az új értékre.

7. A szabályzat frissített beállításainak áttekintéséhez kattintson a **felülvizsgálat + létrehozás** elemre.

4. Kattintson a **Save (Mentés** ) gombra a módosítások mentéséhez. Ismételje a beállítási terület kiválasztásából, a módosításból és végül annak mentéséből álló folyamatot addig, amíg el nem készül minden módosítással. Ekkor bezárhatja az *Intune App Protection – Tulajdonságok* panelt. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Eszközkezelési állapottól függő alkalmazásvédelmi szabályzatok
Vállalatoknál gyakori, hogy a felhasználóknak engedélyezett mind az Intune által felügyelt (MDM) eszközök használata, mind pedig a nem felügyelt, csak az Intune alkalmazásvédelmi szabályzatok által védett eszközök használata. A nem felügyelt eszközöket gyakran saját (BYOD-) eszközöknek nevezik.

Mivel az Intune alkalmazásvédelmi szabályzatok a felhasználói identitásra irányulnak, a felhasználók védelmi beállításait a rendszer alkalmazhatja mind a regisztrált (MDM által felügyelt), mind pedig a regisztrálatlan (MDM nélküli) eszközökre. Emiatt lehetősége van megadni, hogy az Intune alkalmazásvédelmi szabályzatot az Intune-ban regisztrált vagy regisztrálatlan iOS- és Android-eszközökre kívánja-e alkalmazni. A nem felügyelt eszközökre vonatkozóan egyetlen védelmi szabályzattal rendelkezhet, amelyben szigorú adatvesztés-megelőzési (DLP) vezérlők találhatók, valamint egy külön védelmi szabályzat a MDM által felügyelt eszközökhöz, ahol a DLP-vezérlők valamivel nyugodtabbak lehetnek. További információ arról, hogy ez hogyan működik a személyes Android Enterprise-eszközökön: [alkalmazás-védelmi szabályzatok és munkahelyi profilok](android-deployment-scenarios-app-protection-work-profiles.md).

Ezen szabályzatok létrehozásához tallózással keresse meg az **ügyfélalkalmazások** > **alkalmazás-védelmi szabályzatokat** az Intune-konzolon, majd válassza a **házirend létrehozása**lehetőséget. Másik lehetőségként egy meglévő alkalmazásvédelmi szabályzatot is szerkeszthet. Ahhoz, hogy az alkalmazás védelmi szabályzata a felügyelt és a nem felügyelt eszközökre is vonatkozzon, navigáljon az **alkalmazások** lapra, és győződjön meg róla, hogy az **összes eszközön a cél az alkalmazásokhoz** beállítás értéke **Igen**, az alapértelmezett érték. Ha azt szeretné, hogy a rendszer részletesen hozzárendelje a hozzárendelést a felügyeleti állapot alapján, a **nem**értékre állítsa a **cél alkalmazást az összes eszközön** . 

### <a name="device-types"></a>Eszközök típusai

- Nem **felügyelt**: a nem felügyelt eszközök olyan eszközök, amelyeken nem észlelhető az Intune Mdm-kezelője. Ide tartoznak a külső gyártótól származó MDM-szállítók által kezelt eszközök.
- **Intune által felügyelt eszközök**: a felügyelt eszközöket az Intune Mdm kezeli.
- **Android-eszköz rendszergazdája**: az Intune által felügyelt eszközök az Android-eszközök felügyeleti API-ját használják.
- **Android Enterprise**: Intune által felügyelt eszközök az Android Enterprise munkahelyi profilokkal vagy az Android Enterprise teljes körű eszközkezelés használatával.

> [!NOTE]
> Az Android-eszközök arra kérik, hogy telepítse a Intune Céges portál alkalmazást, függetlenül attól, hogy melyik típusú eszköz van kiválasztva. Ha például az "Android Enterprise" lehetőséget választja, akkor a nem felügyelt Android-eszközökkel rendelkező felhasználókat is kéri a rendszer.

IOS esetén további alkalmazás-konfigurációs beállításokra van szükség az alkalmazás-beállítások az Intune-ban regisztrált eszközökön futó alkalmazások számára történő megcélzásához:

- Az **IntuneMAMUPN** beállítást az MDM által felügyelt összes alkalmazáshoz be kell állítani. További információért lásd: [iOS-alkalmazások közti adatátvitel felügyelete a Microsoft Intune-ban](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- A **IntuneMAMDeviceID** minden harmadik féltől származó és üzletági Mdm felügyelt alkalmazáshoz konfigurálni kell. Az **IntuneMAMDeviceID** beállítást az eszközazonosító jogkivonatra kell konfigurálni. Például `key=IntuneMAMDeviceID, value={{deviceID}}`. További információt az [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz](app-configuration-policies-use-ios.md) című témakörben talál.
- Amennyiben csak az **IntuneMAMDeviceID** van konfigurálva, az Intune APP nem felügyeltnek tekinti az eszközt.

> [!NOTE]
> Ha kifejezetten iOS-eszközökre vonatkozó támogatási információkat keres az alkalmazásvédelmi szabályzatok eszközkezelési állapottól függő alkalmazásáról, lásd: [MAM-alapú védelmi szabályzatok alkalmazása eszközkezelési állapot alapján](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state).

## <a name="policy-settings"></a>Szabályzatbeállítások
Az iOS és az Android szabályzatbeállításait tartalmazó lista megtekintéséhez válasszon a következő hivatkozások közül:

- [iOS-szabályzatok](app-protection-policy-settings-ios.md)
- [Android-szabályzatok](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>További lépések
[A megfelelőség és a felhasználói állapot figyelése](app-protection-policies-monitor.md)

## <a name="see-also"></a>További információ
* [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-android.md)
* [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-ios.md)
