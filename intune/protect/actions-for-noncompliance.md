---
title: Meg nem felelés esetén használható üzenetek és műveletek az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Értesítési e-mailt hozhat létre, és elküldheti azt a nem megfelelő eszközökre. Miután az eszköz nem megfelelőként lett megjelölve, hozzáadhat olyan műveleteket, mint a türelmi időszak kijelölése a megfelelőség teljesítéséig, vagy egy ütemterv, amely az eszköz megfelelővé válásáig letiltja a hozzáférést. Mindezt megteheti az Azure-beli Microsoft Intune használatával.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fabc475e1ae05e6ef3fe70e8a507a15bee456cb
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732343"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>E-mailek automatizálása és műveletek hozzáadása a nem megfelelő eszközökhöz az Intune-ban

A megfelelőségi szabályzatoknak vagy szabályoknak nem megfelelő eszközökhöz hozzáadhat nem **megfelelőségi műveleteket**. Ez a funkció egy időben rendezett műveletsort konfigurál, például a végfelhasználói levelezést és egyebeket.

## <a name="overview"></a>Áttekintés

Alapértelmezés szerint az Intune a nem megfelelő eszköz észlelése után azonnal nem megfelelőként jelöli meg azt. Az Azure Active Directory (AD) [feltételes hozzáférés](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) ezt követően blokkolja az eszközt. Ha egy eszköz nem megfelelő, a meg nem **felelés** esetén is rugalmasságot biztosít, hogy eldöntse, mi a teendő. Például nem kell azonnal letiltani az eszközt, hanem türelmi időszakot is meghatározhat az eszköz megfelelőségének visszaállításáig.

Többféle művelet használható:

- **E-mail küldése a végfelhasználónak**: E-mail-értesítések testreszabása, mielőtt elküldené a felhasználónak. Testre szabhatja az e-mail címzettjeit és tárgyát, az üzenet szövegét, a céges emblémát és a kapcsolattartási adatokat.

    Az Intune a nem megfelelő eszköz adatait is szerepelteti az értesítésben.

- **A nem megfelelő eszköz távoli zárolása**: A nem megfelelő eszközökön távoli zárolást adhat ki. A felhasználótól az eszköz PIN-kódot vagy jelszót fog kérni az eszköz feloldásához. További információ a [Távoli zárolás](../remote-actions/device-remote-lock.md) funkcióról. 

- Az **eszköz nem megfelelőként való megjelölése**: Hozzon létre egy ütemtervet (a napok száma szerint), miután az eszköz nem megfelelőként van megjelölve. A műveletet konfigurálhatja azonnali kezdettel, de meghatározhat egy türelmi időszakot is a megfelelőséghez.

Ez a cikk a következőkhöz nyújt útmutatást:

- Üzenetalapú értesítés sablonjának létrehozása
- Művelet létrehozása nem megfelelőségi esetekhez, például e-mail küldése vagy eszköz távoli zárolása


## <a name="before-you-begin"></a>Előkészületek

- A meg nem felelés esetén végrehajtandó műveletek beállításához legalább egy eszközmegfelelőségi szabályzatra van szükség. Eszközmegfelelőségi szabályzat létrehozásához tekintse meg a következő platformokat:

  - [Android](compliance-policy-create-android.md)
  - [Androidos munkahelyi profilok](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Ha eszköz-megfelelőségi szabályzatok segítségével tiltja le az eszközöket a vállalati erőforrásokból, be kell állítania az Azure AD feltételes hozzáférését. Útmutatásért tekintse meg [a feltételes hozzáférés Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) vagy a [feltételes hozzáférés az Intune](conditional-access-intune-common-ways-use.md) -nal való használatát ismertető témakört.

## <a name="create-a-notification-message-template"></a>Értesítési üzenetsablon létrehozása

Ha e-mailt szeretne küldeni a felhasználóknak, hozzon létre egy értesítési üzenetsablont. Ha egy eszköz nem megfelelő, a sablonban megadott adatok a felhasználóknak küldött e-mail tetején jelennek meg.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközmegfelelőség** > **Értesítések** lehetőséget.
3. Válassza az **Értesítés létrehozása** lehetőséget. Adja meg a következő információkat:

   - **Name**
   - **Subject**
   - **Üzenet**
   - **E-mail fejléce – a cég emblémájának megjelenítése**
   - **E-mail lábléce – a cég emblémájának megjelenítése**
   - **E-mail lábléce – a kapcsolatfelvételi adatok megjelenítése**

   ![Megfelelőségről szóló értesítési üzenetminta az Intune-ban](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

4. Ha megadta a szükséges információkat, válassza a **Létrehozás** elemet. Az értesítési üzenet sablonja mostantól használható. Az e-mail-sablonokhoz a Céges portál branding részeként feltöltött emblémát használjuk. A Céges portál arculatának kialakításáról a [Vállalati identitási arculat testreszabása](../apps/company-portal-app.md#company-identity-branding-customization) című cikk nyújt bővebb tájékoztatást.

> [!NOTE]
> Megváltoztathatja vagy frissítheti a korábban létrehozott meglévő értesítési sablonokat is.

## <a name="add-actions-for-noncompliance"></a>Meg nem felelés esetén végrehajtandó műveletek hozzáadása

Eszközmegfelelőségi szabályzat létrehozásakor az Intune automatikusan létrehoz egy meg nem felelés esetén végrehajtandó műveletet. Ha egy eszköz nem felel meg a megfelelőségi szabályzatnak, ez a művelet nem megfelelőként jelöli meg az eszközt. Testre szabhatja, hogy az eszköz meddig maradjon nem megfelelőként megjelölve. Ezt a műveletet nem lehet eltávolítani.

További műveletet akkor vehet fel, ha megfelelőségi szabályzatot hoz létre, vagy frissít egy meglévő szabályzatot. 

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza az **eszköz megfelelősége**lehetőséget.
2. Kattintson a **Szabályzatok** elemre, válassza ki az egyik szabályzatot, majd kattintson a **Tulajdonságok** elemre. 

    Még nincs szabályzata? Létrehozhat egy új szabályzatot [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md), vagy más platformokon.
  
    > [!NOTE]
    > A JAMF-eszközök és az eszközcsoportok segítségével megcélzott eszközök jelenleg nem képesek megfelelőségi műveleteket fogadni.

3. Válassza a **Meg nem felelés esetén végrehajtandó műveletek** > **Hozzáadás** lehetőséget.
4. Válassza ki a **műveletet**: 

    - **E-mail küldése a végfelhasználóknak**: Ha az eszköz nem megfelelő, válassza a felhasználó e-mail-címét. Ezenkívül: 
    
         - Válassza ki a korábban létrehozott **üzenetsablont**
         - Csoportok kiválasztásával adjon meg esetleges **további címzetteket**
    
    - **A nem megfelelő eszköz távoli zárolása**: Ha az eszköz nem megfelelő, zárolja az eszközt. Ez a művelet kényszeríti a felhasználót, hogy PIN-kódot vagy jelszót adjon meg az eszköz zárolásának feloldásához. 
    
5. **Ütemterv**konfigurálása: Adja meg a nem megfelelő napok számát (0 – 365) a felhasználói eszközökön a művelet elindításához. A türelmi időszak után kikényszerítheti a [feltételes hozzáférési](conditional-access-intune-common-ways-use.md) szabályzatot. Ha **0** (nulla) értéket ad meg, akkor a feltételes hozzáférés **azonnal**érvénybe lép. Ha például egy eszköz nem megfelelő, a feltételes hozzáférés használatával azonnal letilthatja az e-mailek, a SharePoint és az egyéb szervezeti erőforrások elérését.

    Megfelelőségi szabályzat létrehozásakor a rendszer automatikusan létrehozza a **megjelölő eszköz nem megfelelő** műveletét, és automatikusan **0** napra (azonnal) állítja be. Ezzel a művelettel, amikor az eszköz bejelentkezik, az eszköz azonnal nem megfelelőként lesz kiértékelve. Ha a feltételes hozzáférést is használja, a feltételes hozzáférés azonnal beindul. Ha engedélyezni szeretné a türelmi időszakot, **módosítsa az** **eszköz megjelölése nem megfelelő** műveletét.
    
    A megfelelőségi szabályzatban például a felhasználót is értesíteni kívánja. Az **E-mail küldése a végfelhasználónak** művelethez adható. Ezen **E-mail küldése** műveletnél az **ütemtervet** 2 napra állítja be. Ha az eszköz vagy a végfelhasználó továbbra is a 2. napon nem megfelelőként van kiértékelve, akkor az e-mailt a 2. napon küldi el a rendszer. Ha a nem megfelelőségi 5. napon szeretné elküldeni a felhasználót, adjon hozzá egy újabb műveletet, és állítsa be az **ütemtervet** 5 napra.

    A megfelelőséggel és a beépített műveletekkel kapcsolatos további információkért tekintse meg a [megfelelőség áttekintését](device-compliance-get-started.md).

6. Ha elkészült, kattintson a **Hozzáadás** > **OK** elemre a módosítások mentéséhez.

## <a name="next-steps"></a>További lépések

[A szabályzatok figyelése](compliance-policy-monitor.md).
