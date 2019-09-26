---
title: Eszközmegfelelőségi szabályzatok az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az eszközök megfelelőségi házirendjeinek használatának első lépései, az állapot és a súlyossági szintek áttekintése, a türelmi időszakban állapot, a feltételes hozzáférés használata, a hozzárendelt házirend nélküli eszközök kezelése, valamint a Azure Portal megfelelőségének eltérései klasszikus portál Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b7519b07b3ac2d40734c32b79466c6d7f4f5d4e8
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/24/2019
ms.locfileid: "71303965"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Megfelelőségi szabályzat létrehozása Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

  - Android
  - Vállalati Android
  - iOS
  - macOS (előzetes verzió)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Eszközök regisztrálása az Intune-ban (a megfelelőségi állapot megtekintéséhez szükséges)

- Eszközök regisztrálása egy felhasználónak, vagy elsődleges felhasználó nélkül regisztrálhat. A több felhasználóhoz regisztrált eszközök nem támogatottak.

## <a name="create-the-policy"></a>A szabályzat létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközmegfelelőség** elemet. A következő lehetőségek közül választhat:

    - **Áttekintés**: A megfelelő, nem kiértékelt és így megjelenő eszközök összegzését és számát jeleníti meg. Emellett felsorolja a szabályzatokat és az egyes beállításokat is. Az [Intune-eszközök megfelelőségi házirendjeinek figyelése](compliance-policy-monitor.md) jó információkat biztosít.
    - **Kezelés**: Eszközöket hozhat létre, [értesítéseket](quickstart-send-notification.md) küldhet a nem megfelelő eszközökre, és engedélyezheti a [hálózati kerítést](use-network-locations.md).
    - **Figyelő**: Győződjön meg az eszközök megfelelőségi állapotáról, valamint a beállítás és a házirend szintjén. Az [Intune-eszközök megfelelőségi házirendjeinek figyelése](compliance-policy-monitor.md) jó erőforrás. A naplókat is megtekintheti, és megtekintheti az eszközök veszélyforrások ügynökének állapotát.
    - **Telepítés**: Használja a [beépített megfelelőségi szabályzatokat](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), engedélyezze a [Microsoft Defender komplex veszélyforrások elleni védelem (ATP)](advanced-threat-protection.md)szolgáltatást, vegyen fel egy [Mobile Threat Defense-összekötőt](mobile-threat-defense.md), és használja a [JAMF](conditional-access-integrate-jamf.md)-t.

3. Válassza a **Szabályzatok** > **Szabályzat létrehozása** lehetőséget. Adja meg a következő tulajdonságokat:

    - **Név**: Adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. A megfelelő szabályzat neve például **nem megfelelőként jelöli**meg az iOS-es feltört eszközöket.
    - **Description** (Leírás): Adja meg a szabályzat leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza ki az eszközök platformját. A választható lehetőségek:  

       - **Android**
       - **Vállalati Android**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 és újabb**
       - **Windows 10 és újabb**

    - **Beállítások**: A következő cikkek felsorolják és leírják az egyes platformok beállításait:

        - [Android](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone-telefon 8,1, Windows 8,1 és újabb verziók](compliance-policy-create-windows-8-1.md)
        - [Windows 10 és újabb](compliance-policy-create-windows.md)

4. Ha elkészült, kattintson **az OK** > **Létrehozás** gombra a módosítások mentéséhez. Ekkor létrejön a szabályzat, és megjelenik a listában. Ezután rendelje hozzá a szabályzatot a csoportokhoz.

## <a name="assign-user-groups"></a>Felhasználói csoportok hozzárendelése

A szabályzat létrehozása után a következő lépés a szabályzat társítása a csoportokhoz:

1. Válassza ki a létrehozott szabályzatot. A meglévő szabályzatok az **Eszközmegfelelőség** > **Szabályzatok** alatt találhatók.
2. Válassza ki a szabályzatot > **hozzárendeléseket**. Belefoglalhat vagy kizárhat Azure Active Directory (AD) biztonsági csoportokat.
3. Azure AD-biztonsági csoportjait a **Kijelölt csoportok** lehetőséget választva tekintheti meg. Válassza ki azokat a felhasználói csoportokat, amelyekre alkalmazni szeretné a szabályzatot > válassza a **Mentés** lehetőséget a szabályzat felhasználók számára történő telepítéséhez.

A szabályzatot alkalmazta a felhasználókra. A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználók által használt eszközök megfelelőségét.

### <a name="evaluate-how-many-users-are-targeted"></a>Annak kiértékelése, hogy hány felhasználó van megcélozva

A szabályzat hozzárendelésével azt is **kiértékelheti** , hogy hány felhasználót érint a rendszer. Ez a szolgáltatás kiszámítja a felhasználókat; nem számítja ki az eszközöket.

1. Az Intune-ban válassza az **eszköz megfelelőségi** > **szabályzatok**lehetőséget.
2. Válasszon ki egy házirendet > **hozzárendelések** > **kiértékelése**. Egy üzenet mutatja, hogy a szabályzat hány felhasználót céloz meg.

Ha a **kiértékelés** gomb szürkén jelenik meg, győződjön meg arról, hogy a szabályzat hozzá van rendelve egy vagy több csoporthoz.

## <a name="actions-for-noncompliance"></a>Meg nem felelés esetén végrehajtandó műveletek

Azon eszközök esetében, amelyek nem felelnek meg a megfelelőségi szabályzatoknak, hozzáadhat egy műveletsort az automatikus alkalmazáshoz. Módosíthatja az eszköz nem megfelelőként való megjelölésének ütemezését, megadhatja például, hogy egy nap elteltével jelölje a rendszer nem megfelelőnek az eszközt. Hozzáadhat egy második műveletet is, amely e-mailt küld a felhasználónak, ha az eszköz nem megfelelő.

A [Műveletek hozzáadása nem megfelelő eszközökhöz](actions-for-noncompliance.md) további információval szolgál, többek között értesítési e-mailt hozhat létre a felhasználók számára.

Például, a Helyek funkciót használja, és hozzáad egy helyet egy megfelelőségi szabályzatban. Az alapértelmezett meg nem felelési művelet alkalmazandó, ha kiválaszt legalább egy helyet. Ha az eszköz nem csatlakozik a megadott helyekhez, akkor azonnal nem megfelelőnek számít. Biztosíthat a felhasználóknak egy türelmi időszakot, például egy napot.

## <a name="scope-tags"></a>Hatókörcímkék

A hatókör címkéi lehetővé teszik a házirendek hozzárendelését és szűrését adott csoportokra, például értékesítésre, HR-re, az összes US-NC-alkalmazottakra stb. A beállítások hozzáadása után hozzá lehet adni egy hatókör-címkét a megfelelőségi szabályzatokhoz. [Hatókör-címkék használata a házirendek szűréséhez](scope-tags.md) jó erőforrás.

## <a name="refresh-cycle-times"></a>A ciklus idejének frissítése

Az Intune különböző frissítési ciklusokat használ a megfelelőségi szabályzatok frissítéseinek kereséséhez. Ha az eszköz nemrég lett regisztrálva, a bejelentkezés gyakrabban fut. A [házirend-és profil-frissítési ciklusok](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) a becsült frissítési időpontokat listázza.

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
|Nem megfelelő |Holnapi dátum|Türelmi időszakban|

Az eszközmegfelelőségi szabályzatok figyelésével kapcsolatos további információkért lásd: [Intune-eszközmegfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Megfelelőségi szabályzat eredményül kapott állapotának hozzárendelése

Ha egy eszközhöz több megfelelőségi szabályzat tartozik, és az eszköz megfelelőségi állapota két vagy több hozzárendelt megfelelőségi szabályzat esetében eltérő, akkor egyetlen eredményül kapott megfelelőségi állapot lesz hozzárendelve. A hozzárendelés az egyes megfelelőségi állapotokhoz hozzárendelt fogalmi szintű súlyossági szinten alapul. Az egyes megfelelőségi állapotok a következő súlyossági szinttel rendelkeznek:

|State  |severity  |
|---------|---------|
|Ismeretlen     |1|
|Nem alkalmazható     |2|
|Compliant (Megfelelő)|3|
|Türelmi időszakban|4|
|Nem megfelelő|5|
|Hiba|6|

Ha egy eszköz több megfelelőségi szabályzattal rendelkezik, akkor az eszközhöz hozzárendelt összes szabályzaté közül a legmagasabb súlyossági szintet rendeli hozzá a rendszer az eszközhöz.

Egy eszközhöz például három megfelelőségi szabályzat van rendelve: egy ismeretlen állapot (súlyosság = 1), egy megfelelő állapot (súlyosság = 3) és egy türelmi időszakban állapot (súlyosság = 4). A türelmi időszakban állapota a legmagasabb súlyossági szinttel rendelkezik. Tehát mindhárom házirend rendelkezik a türelmi időszakban megfelelőségi állapotával.

## <a name="next-steps"></a>További lépések

[A szabályzatok figyelése](compliance-policy-monitor.md).