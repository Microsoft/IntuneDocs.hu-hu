---
title: Alkalmazásvédelmi szabályzatok létrehozása és telepítése
titleSuffix: Microsoft Intune
description: Ez a témakör bemutatja, hogyan hozhat létre és rendelhet hozzá Microsoft Intune app Protection-házirendeket (alkalmazást).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 615509c8a1e7063644d9fa3e0250096b9153c3e3
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71304422"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az alábbiakban azt ismertetjük, hogyan hozhat létre és rendelhet hozzá a Microsoft Intune-ban alkalmazásvédelmi szabályzatokat a felhasználók számára. A témakör a meglévő szabályzatok módosítását is ismerteti.

## <a name="before-you-begin"></a>Előkészületek

Az alkalmazásvédelmi szabályzatok vonatkozhatnak az Intune által felügyelt és nem felügyelt eszközökön futó alkalmazásokra is. Részletesebb információ az alkalmazásvédelmi szabályzatok működéséről és az Intune alkalmazásvédelmi szabályzatai által támogatott forgatókönyvekről: [A Microsoft Intune alkalmazásvédelmi szabályzatai](app-protection-policy.md)

Amennyiben az MAM által támogatott alkalmazások listáját keresi, lásd az [MAM alkalmazáslistáját](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

További információk a cég üzletági (LOB) alkalmazásainak a Microsoft Intune-hoz való hozzáadásáról az alkalmazásvédelmi szabályzatok előkészítése céljából: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md).

## <a name="create-an-app-protection-policy"></a>Alkalmazásvédelmi szabályzat létrehozása
1. Az Intune portálon válassza az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** lehetőséget. Ekkor megnyílik az **Alkalmazásvédelmi szabályzatok** panel, amelyen új szabályzatokat hozhat létre, és szerkesztheti a meglévőket.
2. Válassza a **Szabályzat létrehozása** lehetőséget.

   ![Képernyőfelvétel a Szabályzat hozzáadása panelről](./media/app-protection-add-policy.png)

3. Adja meg a szabályzat nevét, egy rövid leírást, és válassza ki a szabályzat platformtípusát. Az egyes platformokon egynél több szabályzatot is beállíthat.

4. Válassza az **Alkalmazások** elemet az **Alkalmazások** panel megnyitásához, ahol megjelenik a rendelkezésre álló alkalmazások listája. Egy vagy több alkalmazást is kijelölhet a listában a létrehozott szabályzattal való társításra. Jelöljön ki legalább egy alkalmazást a szabályzat létrehozásához.  

5. Az alkalmazások kijelölése után a mentéshez válassza a **Kiválasztás** lehetőséget.

6. A **Szabályzat hozzáadása** panelen válassza a **Kötelező beállítások konfigurálása** lehetőséget a **Beállítások** megnyitásához.

   Három szabályzatbeállítási kategória létezik:
   - **Adatvédelem** – ez a csoport tartalmazza az adatveszteség-megelőzési (DLP) vezérlőket, például a kivágási, másolási, beillesztési és mentési korlátozásokat. Ezek a beállítások szabják meg, hogy hogyan kezelhetik a felhasználók az adatokat az alkalmazásokban.
   - **Hozzáférési követelmények** – Ez a csoport tartalmazza a PIN-kód alkalmazásonkénti beállítási lehetőségeit, amelyek meghatározzák, hogyan férnek hozzá a végfelhasználók az alkalmazásokhoz egy munkahelyi környezetben.  
   - **Feltételes indítás** – Ez a csoport olyan beállításokat tartalmaz, mint a minimális operációsrendszer-követelmények, a függetlenített és feltört eszközök észlelése, és az offline türelmi időszakok.

   Használatuk megkönnyítése érdekében a szabályzatbeállításoknak alapértelmezett értékük van. Ha az alapértelmezett értékek megfelelnek az elvárásainak, nem szükséges változtatnia.

   > [!TIP]
   > A szabályzat beállításai csak akkor lépnek érvénybe, ha munkahelyi környezetben használják az alkalmazásokat. Ha a végfelhasználók az alkalmazást személyes célra használják, nem vonatkoznak rájuk a ezek szabályzatok. Figyelje meg, hogy a létrehozott új fájlokat személyes fájlként kezeli a rendszer. 

7. A konfiguráció mentéséhez válassza az **OK** gombot. Ekkor visszakerül a **Szabályzat hozzáadása** panelre.
8. Válassza a **Létrehozás** lehetőséget a szabályzat létrehozásához és a beállítások mentéséhez.

A létrehozott új szabályzatok egy felhasználóhoz sem lesznek hozzárendelve, amíg ezt Ön explicit módon meg nem teszi. A szabályzatok életbe léptetéséről a [Szabályzat telepítése a felhasználók számára](app-protection-policies.md#deploy-a-policy-to-users) című szakasz nyújt tájékoztatást.

## <a name="deploy-a-policy-to-users"></a>Szabályzat telepítése a felhasználók számára

1. Jelöljön ki egy szabályzatot az **Alkalmazásvédelmi szabályzatok** panelen.

2. Az ***Intune App Protection** panelen a **Hozzárendelések** lehetőség választásával nyissa meg az **Intune App Protection – Hozzárendelések** panelt. A *Befoglalás* lapon válassza a **Belefoglalandó csoportok kijelölése** lehetőséget. 

   ![Képernyőkép a hozzárendelések panelről, és válassza ki a kívánt csoportokat menüt](./media/app-protection-policy-add-users.png)

3. Megjelenik egy lista, amelyen az **Azure Active Directory** összes biztonsági csoportja szerepel. Válassza ki azokat a felhasználói csoportokat, amelyekhez hozzá szeretné rendelni a szabályzatot, és válassza a **Kiválasztás** elemet. 

    ![Képernyőkép a felhasználói csoport hozzáadása panelről az Azure AD-felhasználók listájával](./media/azure-ad-user-group-list.png)

4. A csoportok belefoglalása és kizárása után a **Mentés** gombra kattintva mentse a konfigurációt, és telepítse a szabályzatot a felhasználók számára. Ha a konfiguráció mentése előtt kiválasztja az **Elvetés** lehetőséget, a rendszer elveti a *belefoglalási* és *kizárási* lapokon végrehajtott összes módosítást.   
 
     ![A mentési és elvetési beállításokat ábrázoló képernyőkép](./media/save-assignment.png)
  
A szabályzat ezzel létrejött, és telepítve lett a felhasználók számára.

A szabályzat csak a Microsoft Intune-licenccel rendelkező felhasználókra érvényes. A kijelölt biztonsági csoporthoz tartozó, Intune-licenccel nem rendelkező felhasználókra a szabályzat nem vonatkozik.

>[!IMPORTANT]
> Ha az Intune-ban és a Configuration Managerben kezeli az eszközöket, a szabályzat csak a kijelölt csoport közvetlen felhasználói esetében lép érvénybe. A csoportba ágyazott alárendelt csoportok tagjaira a szabályzat nem vonatkozik.

A végfelhasználók az App Store-ból vagy a Google Play áruházból tölthetik le az alkalmazásokat. További információkért lásd:
* [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](app-protection-enabled-apps-android.md)
* [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](app-protection-enabled-apps-ios.md)

## <a name="change-existing-policies"></a>A meglévő szabályzatok módosítása
A meglévő szabályzatokat szerkesztheti, és alkalmazhatja azokat a megcélzott felhasználókra. Ha azonban a meglévő szabályzatok módosításakor a felhasználók már be voltak jelentkezve az alkalmazásokba, csak egy 8 órás időszak elteltével láthatják a változtatásokat.

A változtatások hatásának érzékeléséhez a felhasználónak ki kell jelentkeznie az alkalmazásból, majd újból be kell jelentkeznie.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>A szabályzathoz társított alkalmazások listájának módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. Az alkalmazások listájának megnyitásához az *Intune App Protection* panelen válassza a **Célzott alkalmazások** lehetőséget.

3. A listában eltávolíthat vagy hozzáadhat alkalmazásokat, majd a **Mentés** ikont választva mentheti a módosításokat.

### <a name="to-change-the-list-of-user-groups"></a>A felhasználói csoportok listájának módosítása


1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. Az *Intune App Protection* panelen a **Hozzárendelések** választásával nyissa meg az **Intune App Protection - Hozzárendelések** panelt, amelyen megjelenik azoknak a felhasználói csoportoknak a listája, amelyekre a szabályzat jelenleg érvényes.

3. Új felhasználói csoportot úgy adhat hozzá a szabályzathoz, hogy a *Belefoglalás* lapon a **befoglalandó csoportok kijelölése** lehetőséget választja, majd kiválasztja a felhasználói csoportot. A csoport hozzáadásához válassza a **kiválasztás** lehetőséget. 

4. Felhasználói csoport kizárásához a *kizárás* lapon válassza a **kizárni kívánt csoportok kiválasztása**lehetőséget, majd válassza ki a felhasználói csoportot. A felhasználói csoport eltávolításához válassza a **Kiválasztás** lehetőséget.  

5. A korábban hozzáadott csoportok törléséhez a *Belefoglalás* vagy *kizárás* lapon válassza a három pontot (...), és válassza a **Törlés**lehetőséget. 

5. A hozzárendelések módosítása után a **Mentés** gombra kattintva mentse a konfigurációt, és telepítse a szabályzatot az új felhasználók csoportba. Ha a konfiguráció mentése előtt kiválasztja az **Elvetés** lehetőséget, a rendszer elveti a *belefoglalási* és *kizárási* lapokon végrehajtott összes módosítást.

### <a name="to-change-policy-settings"></a>A szabályzatbeállítások módosítása

1. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot.

2. Az Ön által szerkeszthető beállítási területek listájának megnyitásához az *Intune App Protection* panelen válassza a **Tulajdonságok** lehetőséget. 

3. Válassza ki a módosítani kívánt beállítást tartalmazó területet, például az **Adatáthelyezést** vagy a **Hozzáférési követelményeket**. Módosítsa a beállításokat az új értékre.

4. A módosítások mentéséhez válassza a **Mentés** ikont. Ismételje a beállítási terület kiválasztásából, a módosításból és végül annak mentéséből álló folyamatot addig, amíg el nem készül minden módosítással. Ekkor bezárhatja az *Intune App Protection – Tulajdonságok* panelt. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Eszközkezelési állapottól függő alkalmazásvédelmi szabályzatok
Vállalatoknál gyakori, hogy a felhasználóknak engedélyezett mind az Intune által felügyelt (MDM) eszközök használata, mind pedig a nem felügyelt, csak az Intune alkalmazásvédelmi szabályzatok által védett eszközök használata. A nem felügyelt eszközöket gyakran saját (BYOD-) eszközöknek nevezik.

Mivel az Intune alkalmazásvédelmi szabályzatok a felhasználói identitásra irányulnak, a felhasználók védelmi beállításait a rendszer alkalmazhatja mind a regisztrált (MDM által felügyelt), mind pedig a regisztrálatlan (MDM nélküli) eszközökre. Emiatt lehetősége van megadni, hogy az Intune alkalmazásvédelmi szabályzatot az Intune-ban regisztrált vagy regisztrálatlan iOS- és Android-eszközökre kívánja-e alkalmazni. A nem felügyelt eszközökre vonatkozóan egyetlen védelmi szabályzattal rendelkezhet, amelyben szigorú adatvesztés-megelőzési (DLP) vezérlők találhatók, valamint egy külön védelmi szabályzat a MDM által felügyelt eszközökhöz, ahol a DLP-vezérlők valamivel nyugodtabbak lehetnek. Ha többet szeretne megtudni arról, hogy ez hogyan működik a személyes Android enteprise-eszközökön, tekintse meg az [alkalmazás-védelmi szabályzatok és a munkahelyi profilok](android-deployment-scenarios-app-protection-work-profiles.md)

A szabályzatok létrehozásához navigáljon az Intune-konzolon az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** lapra, majd kattintson a **Szabályzat létrehozása** elemre. Másik lehetőségként egy meglévő alkalmazásvédelmi szabályzatot is szerkeszthet. Ahhoz, hogy az alkalmazásvédelmi szabályzat a felügyelt és a nem felügyelt eszközökre egyaránt alkalmazva legyen, győződjön meg róla, hogy az **Alkalmazás minden alkalmazástípusra** beállításnál az alapértelmezett **Igen** érték van beállítva. Ha a szabályzatot az eszközkezelési állapottól függően szeretné alkalmazni, állítsa az **Alkalmazás minden alkalmazástípusra** beállítást a **Nem** értékre. 

![Képernyőfelvétel a szabályzat hozzáadása panel és a cél között az összes alkalmazás típusához](./media/app-protection-policies-target-all.png)

### <a name="app-types"></a>Alkalmazástípusok

- Nem **felügyelt eszközökön futó alkalmazások**: A nem felügyelt eszközök olyan eszközök, amelyeken nem észlelhető az Intune MDM-kezelője. Ez magában foglalja a harmadik féltől származó MDM-szállítókat is.
- **Intune által felügyelt eszközökön futó alkalmazások**: A felügyelt eszközöket az Intune MDM kezeli.
- **Alkalmazások az Android munkahelyi profilban**: Az Android Enterprise Work Profile-eszközökként regisztrált felügyelt eszközök.

> Megjegyzés androidos eszközök esetén a rendszer felszólítja, hogy telepítse a Intune Céges portál alkalmazást, függetlenül attól, hogy melyik alkalmazás típusa van kiválasztva. Ha például az "alkalmazások az Intune által felügyelt eszközökön" lehetőséget választja, akkor a nem felügyelt Android-eszközökkel rendelkező felhasználók továbbra is megtalálhatók.

IOS esetén további alkalmazás-konfigurációs beállításokra van szükség az alkalmazás-beállítások az Intune-ban regisztrált eszközökön futó alkalmazások számára történő megcélzásához:

- Az **IntuneMAMUPN** beállítást az MDM által felügyelt összes alkalmazáshoz be kell állítani. További információért lásd: [iOS-alkalmazások közti adatátvitel felügyelete a Microsoft Intune-ban](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- Az **IntuneMAMDeviceID** beállítást az összes külső féltől származó és az MDM által felügyelt üzletági alkalmazáshoz be kell állítani. Az **IntuneMAMDeviceID** beállítást az eszközazonosító jogkivonatra kell konfigurálni. Például: `key=IntuneMAMDeviceID, value={{deviceID}}`. További információt az [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz](app-configuration-policies-use-ios.md) című témakörben talál.
- Amennyiben csak az **IntuneMAMDeviceID** van konfigurálva, az Intune APP nem felügyeltnek tekinti az eszközt.

> [!NOTE]
> Ha kifejezetten iOS-eszközökre vonatkozó támogatási információkat keres az alkalmazásvédelmi szabályzatok eszközkezelési állapottól függő alkalmazásáról, lásd: [MAM-alapú védelmi szabályzatok alkalmazása eszközkezelési állapot alapján](whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Szabályzatbeállítások
Az iOS és az Android szabályzatbeállításait tartalmazó lista megtekintéséhez válasszon a következő hivatkozások közül:

- [iOS-szabályzatok](app-protection-policy-settings-ios.md)
- [Android-szabályzatok](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>További lépések
[A megfelelőség és a felhasználói állapot figyelése](app-protection-policies-monitor.md)

## <a name="see-also"></a>Lásd még:
* [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](app-protection-enabled-apps-android.md)
* [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](app-protection-enabled-apps-ios.md)
