---
title: Meg nem felelés esetén használható üzenetek és műveletek az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Értesítési e-mailt hozhat létre, és elküldheti azt a nem megfelelő eszközökre. Miután az eszköz nem megfelelőként lett megjelölve, hozzáadhat olyan műveleteket, mint a türelmi időszak kijelölése a megfelelőség teljesítéséig, vagy egy ütemterv, amely az eszköz megfelelővé válásáig letiltja a hozzáférést. Mindezt megteheti az Azure-beli Microsoft Intune használatával.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e3867bfc2de29c059766e134bd0d2c8801e1c70
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712885"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>E-mailek automatizálása és műveletek hozzáadása a nem megfelelő eszközökhöz az Intune-ban

A megfelelőségi szabályzatoknak vagy szabályoknak nem megfelelő eszközökhöz hozzáadhat nem **megfelelőségi műveleteket**. Ez a funkció egy időben rendezett műveletsort konfigurál, például a végfelhasználói levelezést és egyebeket.

## <a name="overview"></a>Házirend

Alapértelmezés szerint az Intune a nem megfelelő eszköz észlelése után azonnal nem megfelelőként jelöli meg azt. Az Azure Active Directory (AD) [feltételes hozzáférés](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) ezt követően blokkolja az eszközt. Ha egy eszköz nem megfelelő, a meg nem **felelés** esetén is rugalmasságot biztosít, hogy eldöntse, mi a teendő. Például nem kell azonnal letiltani az eszközt, hanem türelmi időszakot is meghatározhat az eszköz megfelelőségének visszaállításáig.

Többféle művelet használható:

- **E-mail küldése a felhasználónak**: Testreszabhatja az értesítő e-mailt, mielőtt elküldené a végfelhasználónak. Testre szabhatja az e-mail címzettjeit és tárgyát, az üzenet szövegét, a céges emblémát és a kapcsolattartási adatokat.

    Az Intune a nem megfelelő eszköz adatait is szerepelteti az értesítésben.

- **A nem megfelelő eszköz távoli zárolása**: A nem megfelelő eszközök esetén távoli zárolást rendelhet el. A felhasználótól az eszköz PIN-kódot vagy jelszót fog kérni az eszköz feloldásához. További információ a [Távoli zárolás](../remote-actions/device-remote-lock.md) funkcióról.

- **Eszköz megjelölése nem megfelelőként**: Megadhatja, hogy hány napon belül legyen nem megfelelőként megjelölve az eszköz. A műveletet konfigurálhatja azonnali kezdettel, de meghatározhat egy türelmi időszakot is a megfelelőséghez.

Ez a cikk a következőkhöz nyújt útmutatást:

- Üzenetalapú értesítés sablonjának létrehozása
- Művelet létrehozása nem megfelelőségi esetekhez, például e-mail küldése vagy eszköz távoli zárolása


## <a name="before-you-begin"></a>Előkészületek

- A meg nem felelés esetén végrehajtandó műveletek beállításához legalább egy eszközmegfelelőségi szabályzatra van szükség. Eszközmegfelelőségi szabályzat létrehozásához tekintse meg a következő platformokat:

  - [Android--](compliance-policy-create-android.md)
  - [Androidos munkahelyi profilok](compliance-policy-create-android-for-work.md)
  - [iOS--](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Ha eszköz-megfelelőségi szabályzatok segítségével tiltja le az eszközöket a vállalati erőforrásokból, be kell állítania az Azure AD feltételes hozzáférését. Útmutatásért tekintse meg [a feltételes hozzáférés Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) vagy a [feltételes hozzáférés az Intune](conditional-access-intune-common-ways-use.md) -nal való használatát ismertető témakört.

## <a name="create-a-notification-message-template"></a>Értesítési üzenetsablon létrehozása

Ha e-mailt szeretne küldeni a felhasználóknak, hozzon létre egy értesítési üzenetsablont. Ha egy eszköz nem megfelelő, a sablonban megadott adatok a felhasználóknak küldött e-mail tetején jelennek meg.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **megfelelőségi szabályzatok** > **értesítések** **Értesítés létrehozása** > .
3. Az *alapok*területen válassza a következő információkat:

   - **Név**
   - **Tárgy**
   - **Üzenet**

4. Az *alapismeretek*területen adja meg az alábbi beállításokat az értesítéshez, amely az összes alapértelmezett beállítást *engedélyezi*:

   - **E-mail fejléce – a cég emblémájának megjelenítése**
   - **E-mail lábléce – a cég emblémájának megjelenítése**
   - **E-mail lábléce – a kapcsolatfelvételi adatok megjelenítése**

   Az e-mail-sablonokhoz a Céges portál branding részeként feltöltött emblémát használjuk. A Céges portál arculatának kialakításáról a [Vállalati identitási arculat testreszabása](../apps/company-portal-app.md#company-identity-branding-customization) című cikk nyújt bővebb tájékoztatást.

   ![Megfelelőségről szóló értesítési üzenetminta az Intune-ban](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

   A folytatáshoz kattintson a **Tovább** gombra.

5. A **felülvizsgálat + létrehozás**alatt tekintse át a konfigurációkat, és győződjön meg arról, hogy az értesítési üzenet sablonja készen áll a használatra. Válassza a **Létrehozás** lehetőséget az értesítés létrehozásának befejezéséhez.

> [!NOTE]
> Kiválaszthat egy korábban létrehozott meglévő értesítési sablont is, és **szerkesztheti** az adatait a sablon frissítéséhez.

## <a name="add-actions-for-noncompliance"></a>Meg nem felelés esetén végrehajtandó műveletek hozzáadása

Eszközmegfelelőségi szabályzat létrehozásakor az Intune automatikusan létrehoz egy meg nem felelés esetén végrehajtandó műveletet. Ha egy eszköz nem felel meg a megfelelőségi szabályzatnak, ez a művelet nem megfelelőként jelöli meg az eszközt. Testre szabhatja, hogy az eszköz meddig maradjon nem megfelelőként megjelölve. Ezt a műveletet nem lehet eltávolítani.

További műveletet akkor vehet fel, ha megfelelőségi szabályzatot hoz létre, vagy frissít egy meglévő szabályzatot.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **megfelelőségi szabályzatok** > **szabályzatok**lehetőséget, válassza ki az egyik szabályzatot, majd válassza a **Tulajdonságok**lehetőséget.

   Még nincs szabályzata? Létrehozhat egy új szabályzatot [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md), vagy más platformokon.

   > [!NOTE]
   > A JAMF-eszközök és az eszközcsoportok segítségével megcélzott eszközök jelenleg nem képesek megfelelőségi műveleteket fogadni.

3. Válassza a **Meg nem felelés esetén végrehajtandó műveletek** > **Hozzáadás** lehetőséget.

4. Válassza ki a **műveletet**:

   - **E-mail küldése a felhasználóknak**: Az eszköz meg nem felelése esetén e-mailt küldhet a felhasználónak. Ezenkívül:
     - Válassza ki a korábban létrehozott **üzenetsablont**
     - Csoportok kiválasztásával adjon meg esetleges **további címzetteket**

   - **A nem megfelelő eszköz távoli zárolása**: Az eszköz meg nem felelése esetén zárolhatja az eszközt. Ez a művelet kényszeríti a felhasználót, hogy PIN-kódot vagy jelszót adjon meg az eszköz zárolásának feloldásához.

5. **Ütemterv**konfigurálása: Itt adhatja meg, hogy a nem megfelelőség után hány nap (0 – 365) után aktiválja a művelet a felhasználói eszközökön. A türelmi időszak után kikényszerítheti a [feltételes hozzáférési](conditional-access-intune-common-ways-use.md) szabályzatot. Ha **0** (nulla) értéket ad meg, akkor a feltételes hozzáférés **azonnal**érvénybe lép. Ha például egy eszköz nem megfelelő, a feltételes hozzáférés használatával azonnal letilthatja az e-mailek, a SharePoint és az egyéb szervezeti erőforrások elérését.

   Megfelelőségi szabályzat létrehozásakor a rendszer automatikusan létrehozza a **megjelölő eszköz nem megfelelő** műveletét, és automatikusan **0** napra (azonnal) állítja be. Ezzel a művelettel, amikor az eszköz bejelentkezik, az eszköz azonnal nem megfelelőként lesz kiértékelve. Ha a feltételes hozzáférést is használja, a feltételes hozzáférés azonnal beindul. Ha engedélyezni szeretné a türelmi időszakot, **módosítsa az** **eszköz megjelölése nem megfelelő** műveletét.

   A megfelelőségi szabályzatban például a felhasználót is értesíteni kívánja. Az **E-mail küldése a végfelhasználónak** művelethez adható. Ezen **E-mail küldése** műveletnél az **ütemtervet** 2 napra állítja be. Ha az eszköz vagy a végfelhasználó továbbra is a 2. napon nem megfelelőként van kiértékelve, akkor az e-mailt a 2. napon küldi el a rendszer. Ha a nem megfelelőségi 5. napon szeretné elküldeni a felhasználót, adjon hozzá egy újabb műveletet, és állítsa be az **ütemtervet** 5 napra.

   A megfelelőséggel és a beépített műveletekkel kapcsolatos további információkért tekintse meg a [megfelelőség áttekintését](device-compliance-get-started.md).

6. Ha elkészült, kattintson a **Hozzáadás** > **OK** elemre a módosítások mentéséhez.

## <a name="next-steps"></a>További lépések

[A szabályzatok figyelése](compliance-policy-monitor.md).
