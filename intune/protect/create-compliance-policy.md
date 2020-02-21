---
title: Eszköz megfelelőségi szabályzatok létrehozása a Microsoft Intuneban – Azure | Microsoft Docs
description: Eszköz megfelelőségi szabályzatok létrehozása, az állapot és a súlyossági szintek áttekintése, a türelmi időszakban állapota, a feltételes hozzáférés használata, a hozzárendelt házirend nélküli eszközök kezelése, valamint a Azure Portal és a klasszikus portál megfelelőségének eltérései Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68fcdb66591ec0e566aa702b3ca4d6c5c5448859
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514013"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Megfelelőségi szabályzat létrehozása Microsoft Intune

Az eszközmegfelelőségi szabályzatok használata kiemelten fontos, ha az Intune-t a vállalat erőforrásainak védelmére kívánja használni. Az Intune-ban létrehozhat olyan szabályokat és beállításokat, amelyeknek az eszközöknek meg kell felelniük a megfelelőnek, például a minimális operációsrendszer-verziónak. Ha az eszköz nem megfelelő, a [feltételes hozzáférés](conditional-access.md)használatával letilthatja az adatelérést és az erőforrásokat.

A nem megfelelőséggel kapcsolatos műveleteket is végrehajthat, például értesítő e-mailt küldhet a felhasználónak. A megfelelőségi szabályzatok végrehajtásának és használatuk módjának áttekintését lásd: [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md).

Ez a cikk:

- Felsorolja a kompatibilitás szabályzat létrehozásához szükséges előfeltételeket és lépéseket.
- Bemutatja, hogyan rendelheti hozzá a szabályzatot a felhasználókhoz és az eszközök csoportjaihoz.
- A további szolgáltatásokat, például a hatóköri címkéket a szabályzatok szűrésére, valamint a nem megfelelő eszközökre vonatkozó lépéseket ismerteti.
- Felsorolja a beléptetési frissítési ciklus időpontját, amikor az eszközök házirend-frissítéseket fogadnak.

## <a name="before-you-begin"></a>Előkészületek

Az eszközök megfelelőségi házirendjeinek használatához győződjön meg róla, hogy:

- Használja az alábbi előfizetéseket:

  - Intune
  - Ha feltételes hozzáférést használ, akkor Azure Active Directory (AD) Premium kiadásra van szüksége. A [Azure Active Directory díjszabása](https://azure.microsoft.com/pricing/details/active-directory/) felsorolja, hogy mit kap a különböző kiadásokban. Az Intune-megfelelőség nem igényli az Azure AD-t.

- Használjon támogatott platformot:

  - Android-eszköz rendszergazdája
  - Vállalati Android
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - WVPN-profilokdows Phone 8.1

- Eszközök regisztrálása az Intune-ban (a megfelelőségi állapot megtekintéséhez szükséges)

- Eszközök regisztrálása egy felhasználónak, vagy elsődleges felhasználó nélkül regisztrálhat. A több felhasználóhoz regisztrált eszközök nem támogatottak.

## <a name="create-the-policy"></a>A szabályzat létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **megfelelőségi szabályzatok** > **házirend létrehozása**lehetőséget.

3. A következő tulajdonságokat kell megadnia:

   - **Név**: adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. A megfelelő szabályzat neve például az **iOS/iPadOS feltört eszközök nem megfelelőként való megjelölése**.

   - **Leírás**: adja meg a szabályzat leírását. A beállítás használata nem kötelező, de ajánlott.

   - **Platform**: válassza ki az eszközök platformját. A választható lehetőségek:
     - **Android-eszköz rendszergazdája**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 és újabb verziók**
     - **Windows 10 és újabb**

     Az *Android Enterprise*esetében ki kell választania egy **profil típusát**:
     - **Eszköz tulajdonosa**
     - **Munkahelyi profil**

   - **Beállítások**: az alábbi cikkek felsorolják és leírják az egyes platformok beállításait:
     - [Android-eszköz rendszergazdája](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone-telefon 8,1, Windows 8,1 és újabb verziók](compliance-policy-create-windows-8-1.md)
     - [Windows 10 és újabb](compliance-policy-create-windows.md)  

   - **Helyek** *(Android-eszköz rendszergazdája)* : a szabályzatban az eszköz helye alapján kényszerítheti a megfelelőséget. Válasszon a meglévő helyekről. Még nem rendelkezik hellyel? Az Intune-ban a [webhelyek (hálózati kerítés) használatával](use-network-locations.md) biztosítunk útmutatást.  

   - Nem **megfelelőségi műveletek**: olyan eszközök esetében, amelyek nem felelnek meg a megfelelőségi szabályzatoknak, hozzáadhat egy műveletsort az automatikus alkalmazáshoz. Módosíthatja az eszköz nem megfelelőként való megjelölésének ütemezését, megadhatja például, hogy egy nap elteltével jelölje a rendszer nem megfelelőnek az eszközt. Hozzáadhat egy második műveletet is, amely e-mailt küld a felhasználónak, ha az eszköz nem megfelelő.

     A [Műveletek hozzáadása nem megfelelő eszközökhöz](actions-for-noncompliance.md) további információval szolgál, többek között arról, hogyan hozhat létre értesítési e-mailt a felhasználók számára.

     Például, a Helyek funkciót használja, és hozzáad egy helyet egy megfelelőségi szabályzatban. Az alapértelmezett meg nem felelési művelet alkalmazandó, ha kiválaszt legalább egy helyet. Ha az eszköz nem csatlakozik a megadott helyekhez, akkor azonnal nem megfelelőnek számít. Biztosíthat a felhasználóknak egy türelmi időszakot, például egy napot.

   - **Hatókör (címkék)** : a hatókör-címkék nagyszerű módot kapnak a házirendek adott csoportokra, például `US-NC IT Team` vagy `JohnGlenn_ITDepartment`történő szűrésére. A beállítások hozzáadása után hozzá lehet adni egy hatókör-címkét a megfelelőségi szabályzatokhoz. [Hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md) jó erőforrás.

4. Ha elkészült, válassza **az OK** > **Létrehozás** lehetőséget a módosítások mentéséhez. Ekkor létrejön a szabályzat, és megjelenik a listában. Ezután rendelje hozzá a szabályzatot a csoportokhoz.

## <a name="assign-the-policy"></a>A szabályzat hozzárendelése

A szabályzat létrehozása után a következő lépés a szabályzat társítása a csoportokhoz:

1. Válassza ki a létrehozott szabályzatot. A meglévő szabályzatok az **eszközök** > **megfelelőségi szabályzatok** > **szabályzatok**.

2. Válassza ki a *szabályzatot* > **hozzárendeléseket**. Belefoglalhat vagy kizárhat Azure Active Directory (AD) biztonsági csoportokat.

3. Azure AD-biztonsági csoportjait a **Kijelölt csoportok** lehetőséget választva tekintheti meg. Válassza ki azokat a csoportokat, amelyekre alkalmazni szeretné a szabályzatot > válassza a **Mentés** lehetőséget a szabályzat telepítéséhez.

A szabályzat által megadott felhasználók vagy eszközök megfelelőségét a rendszer az Intune-ba való bejelentkezéskor értékeli.

### <a name="evaluate-how-many-users-are-targeted"></a>Annak kiértékelése, hogy hány felhasználó van megcélozva

A szabályzat hozzárendelésével azt is **kiértékelheti** , hogy hány felhasználót érint a rendszer. Ez a szolgáltatás kiszámítja a felhasználókat; nem számítja ki az eszközöket.

1. Az Intune-ban válassza az **eszközök** > **megfelelőségi szabályzatok** > **szabályzatok**lehetőséget.

2. Válasszon ki egy *házirendet* > **hozzárendelések** > **kiértékelése**. Egy üzenet mutatja, hogy a szabályzat hány felhasználót céloz meg.

Ha a **kiértékelés** gomb szürkén jelenik meg, győződjön meg arról, hogy a szabályzat hozzá van rendelve egy vagy több csoporthoz.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>A ciklus idejének frissítése

Az Intune különböző frissítési ciklusokat használ a megfelelőségi szabályzatok frissítéseinek kereséséhez. Ha az eszköz nemrég lett regisztrálva, a bejelentkezés gyakrabban fut. A [házirend-és profil-frissítési ciklusok](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) a becsült frissítési időpontokat listázza.

A felhasználók bármikor megnyithatják a Céges portál alkalmazást, és az eszköz szinkronizálásával azonnal ellenőrizhetők a házirendek frissítései.

### <a name="assign-an-ingraceperiod-status"></a>Türelmi időszakban állapot hozzárendelése

A megfelelőségi szabályzatok Türelmi időszakban állapota egy érték. Ezt az értéket a rendszer az adott eszköz türelmi időszaka és az eszközre érvényes megfelelőségi szabályzat tényleges állapota alapján határozza meg.

Konkrétan, ha egy eszköz Nem megfelelő állapotú egy hozzárendelt megfelelőségi szabályzatra vonatkozóan, illetve:

- Az eszközhöz nincs hozzárendelve türelmi időszak, a megfelelőségi szabályzathoz hozzárendelt érték nem megfelelő.
- Az eszköz lejárt türelmi időszakot tartalmaz, a megfelelőségi szabályzathoz hozzárendelt érték nem megfelelő.
- Az eszköz a jövőben türelmi időszakot tartalmaz, a megfelelőségi szabályzathoz hozzárendelt érték pedig türelmi időszakban

Az alábbi táblázat összefoglalja ezt részletesen:

|Aktuális megfelelőségi állapot|A hozzárendelt türelmi időszak értéke|Tényleges megfelelőségi állapot|
|---------|---------|---------|
|Nem megfelelő |Nincs hozzárendelve türelmi időszak |Nem megfelelő |
|Nem megfelelő |Tegnapi dátum|Nem megfelelő|
|Nem megfelelő |Holnapi dátum|InGracePeriod|

Az eszközmegfelelőségi szabályzatok figyelésével kapcsolatos további információkért lásd: [Intune-eszközmegfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Megfelelőségi szabályzat eredményül kapott állapotának hozzárendelése

Ha egy eszközhöz több megfelelőségi szabályzat tartozik, és az eszköz megfelelőségi állapota két vagy több hozzárendelt megfelelőségi szabályzat esetében eltérő, akkor egyetlen eredményül kapott megfelelőségi állapot lesz hozzárendelve. A hozzárendelés az egyes megfelelőségi állapotokhoz hozzárendelt fogalmi szintű súlyossági szinten alapul. Az egyes megfelelőségi állapotok a következő súlyossági szinttel rendelkeznek:

|Állapot  |Severity  |
|---------|---------|
|Ismeretlen     |1|
|Nem alkalmazható     |2|
|Compliant (Megfelelő)|3|
|InGracePeriod|4|
|Nem megfelelő|5|
|Hiba|6|

Ha egy eszköz több megfelelőségi szabályzattal rendelkezik, akkor az eszközhöz hozzárendelt összes szabályzaté közül a legmagasabb súlyossági szintet rendeli hozzá a rendszer az eszközhöz.

Egy eszközhöz például három megfelelőségi szabályzat van rendelve: egy ismeretlen állapot (súlyosság = 1), egy megfelelő állapot (súlyosság = 3) és egy türelmi időszakban állapot (súlyosság = 4). A türelmi időszakban állapota a legmagasabb súlyossági szinttel rendelkezik. Tehát mindhárom házirend rendelkezik a türelmi időszakban megfelelőségi állapotával.

## <a name="next-steps"></a>További lépések

[A szabályzatok figyelése](compliance-policy-monitor.md).
