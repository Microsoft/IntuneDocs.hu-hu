---
title: Office 365 frissítése felügyeleti sablonokkal Microsoft Intune-Azure-ban | Microsoft Docs
description: Az Office 365-alkalmazások legújabb verzióra való frissítéséhez használja a Microsoft Intune felügyeleti sablonjait, és válassza ki, hogy az Office milyen gyakran keressen frissítéseket. Tekintse meg azokat az eszköz-beállításkulcsokat, amelyek akkor frissülnek, amikor az Intune-szabályzatot Office Update-re alkalmazza.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dcd1948899ec4023a65c62f7106298b065b46883
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206924"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>A frissítési csatorna és a célként megadott verzió beállításainak használatával frissítse az Office 365-et Microsoft Intune Felügyeleti sablonok

Az Intune-ban a [Windows 10 sablonjait használhatja a csoportházirend-beállítások konfigurálásához](administrative-templates-windows.md). Ez a cikk bemutatja, hogyan frissítheti az Office 365-et felügyeleti sablonnal az Intune-ban. Emellett útmutatást nyújt a szabályzatok sikeres ellenőrzésének megerősítéséhez. Ez az információ a hibaelhárítás során is segít.

Ebben a forgatókönyvben egy felügyeleti sablont hoz létre az Intune-ban, amely frissíti az Office 365-et az eszközökön.

A felügyeleti sablonokkal kapcsolatos további információkért lásd: [Windows 10 sablonok a csoportházirend-beállítások konfigurálásához](administrative-templates-windows.md).

A következőkre vonatkozik:

- Windows 10 és újabb
- Office 365

## <a name="prerequisites"></a>Előfeltételek

Ügyeljen arra, hogy az Office-alkalmazások [Office 365 ProPlus az automatikus frissítéseket](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) . Ezt a csoportházirend vagy az Intune Office 2016 ADMX-sablon használatával végezheti el:

![Az Intune felügyeleti sablonban állítsa be az automatikus frissítések engedélyezése beállítást az Office-hoz.](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>A frissítési csatorna beállítása az Intune felügyeleti sablonban

1. Az [Intune felügyeleti sablonjában](administrative-templates-windows.md#create-a-template)lépjen a **csatorna frissítése** beállításra, és adja meg a kívánt csatornát. Válassza például a `Semi-Annual Channel`:

    ![Az Intune felügyeleti sablonban állítsa be az Office frissítési csatornájának beállítása beállítást.](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > Azt javasoljuk, hogy gyakrabban frissítsen. A féléves használat csak példaként szolgál.

2. Ügyeljen arra, hogy [a szabályzatot](device-profile-assign.md) a Windows 10-es eszközökhöz rendelje. Ha hamarabb szeretné tesztelni a szabályzatot, szinkronizálhatja is a szabályzatot:

    - [A szabályzat szinkronizálása az Intune-ban](../remote-actions/device-sync.md)
    - [A szabályzat manuális szinkronizálása az eszközön](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Az Intune-beállításkulcsok keresése

Miután hozzárendelte a szabályzatot és az eszköz szinkronizálásait, megerősítheti a szabályzatot:

1. Az eszközön nyissa meg a **Rendszerleíróadatbázis-szerkesztő** alkalmazást.
2. Nyissa meg az Intune-szabályzat elérési útját: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

    > [!TIP]
    > A beállításkulcs `<Provider ID>` megváltozik. Az eszköz szolgáltatói AZONOSÍTÓjának megkereséséhez nyissa meg a **Rendszerleíróadatbázis-szerkesztő** alkalmazást, és lépjen a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`elemre. Megjelenik a szolgáltató azonosítója.

    A házirend alkalmazása esetén a következő beállításkulcsok láthatók:

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    Az alábbi példát követve láthatja, hogy a `L_UpdateBranch` `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`hoz hasonló értékkel rendelkezik. Ez az érték azt jelenti, hogy az a féléves csatornára van beállítva:

    ![Felügyeleti sablon L_Updatebranch beállításkulcs – példa](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > Az [Office 365 ProPlus kezelése Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) listázza az értékeket, és azt, hogy mit jelentenek. A beállításjegyzék értékei a kiválasztott terjesztési csatornán alapulnak:
    >
    >- Havi Channel-Value = "aktuális"
    >- Havi csatorna (megcélozva) – érték = "aktuális"
    >- Féléves csatorna-érték = "aktuális"
    >- Féléves csatorna (megcélozva) – Value = "FirstReleaseDeferred"
    >- Bennfentes Fast-Value = "InsiderFast"

Ezen a ponton a rendszer sikeresen alkalmazta az Intune-szabályzatot az eszközön.

## <a name="check-the-office-registry-keys"></a>Keresse meg az Office-beállításkulcsokat

1. Az eszközön nyissa meg a **Rendszerleíróadatbázis-szerkesztő** alkalmazást.
2. Nyissa meg az Office-házirend elérési útját: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    A következő beállításkulcsokat látja:

    - `UpdateChannel`: a megadott beállításoktól függően változó dinamikus kulcs.
    - `CDNBaseUrl`: állítsa be, hogy az Office 365 Mikor telepítse az eszközt az eszközön.

3. Tekintse meg a `UpdateChannel` értéket. Az érték azt jelzi, hogy az Office milyen gyakran frissül. Az [Office 365 ProPlus kezelése Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) listázza az értékeket, és azt, hogy mire vannak beállítva.

    Az alábbi példát követve láthatja, hogy `UpdateChannel` `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`re van beállítva, amely **havonta**:

    ![Példa a felügyeleti sablon Office-UpdateChannel beállításkulcs](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    Ez a példa azt jelenti, hogy a házirend még nincs alkalmazva, mivel még mindig **havi**értékre van állítva, a **félév**helyett.

Ez a beállításkulcs akkor frissül, amikor a **feladatütemező** > az **Office automatikus frissítései 2,0** , vagy amikor egy felhasználó bejelentkezik az eszközre. A megerősítéshez nyissa meg az **Office automatikus frissítések 2,0** feladat > **eseményindítókat**. Az eseményindítók függően a `UpdateChannel` beállításkulcs frissítése előtt legalább egy nappal és még több időt is igénybe vehet.

## <a name="force-office-automatic-updates-to-run"></a>Az Office automatikus frissítéseinek futtatásának kényszerítése

A szabályzat teszteléséhez kényszerítheti a házirend-beállításokat az eszközön. A következő lépésekkel frissítheti a beállításjegyzéket. Mindig legyen körültekintő, amikor frissíti a beállításjegyzéket.

1. Törölje a beállításkulcsot:

    1. Lépjen a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates` lapra.
    2. Kattintson duplán a `UpdateDetectionLastRunTime` kulcsra, törölje az adatértéket > **OK gombra**.

2. Az Office automatikus frissítések feladat futtatása:

    1. Nyissa **meg a Feladatütemező alkalmazást az** eszközön.
    2. Bontsa ki a Feladatütemező **függvénytárat** > **Microsoft** > **Office**elemet.
    3. Válassza az **Office automatikus frissítések 2,0** > **Futtatás**:

        ![Feladatütemezés megnyitása és az Office automatikus frissítéseinek futtatása](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        Várjon, amíg a feladat befejeződik, ami több percet is igénybe vehet.

3. A **Rendszerleíróadatbázis-szerkesztő** alkalmazásban lépjen a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`elemre. A `UpdateChannel` értékének bejelölése.

    A szabályzatban beállított értékkel kell frissíteni. A példánkban az értéket `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`értékre kell állítani.

Ezen a ponton az Office Update Channel sikeresen módosult az eszközön. Nyisson meg egy Office 365-alkalmazást egy olyan felhasználó számára, aki ezt a frissítést fogadja az állapot megtekintéséhez.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Az Office-szinkronizálás kényszerítése a fiókadatok frissítésére  

Ha többre van szüksége, kényszerítheti az Office-t, hogy letöltse a legújabb verziót. A következő lépéseket csak megerősítésként kell végrehajtani, vagy ha az eszközön gyorsan kell beszerezni a legújabb verziót. Ellenkező esetben az Office elvégzi a feladatot, és automatikusan frissíti.

### <a name="step-1-force-the-office-version-to-update"></a>1. lépés: az Office-verzió frissítésének kényszerítése

1. Erősítse meg, hogy az Office-verzió támogatja a kiválasztott frissítési csatornát. Az [Office 365 ProPlus frissítési előzményei](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date) a különböző frissítési csatornákat támogató összeállítási számokat listázza.

2. Az [Intune felügyeleti sablonjában](administrative-templates-windows.md#create-a-template)lépjen a **cél verziója** beállításra, és adja meg a kívánt verziót.

    A **célként megadott verzió** beállítása a következő beállításhoz hasonlóan néz ki:

    ![Az Intune felügyeleti sablonjában adja meg az Office-cél verziójának beállítását](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - Ügyeljen arra, hogy hozzárendelje a szabályzatot.
> - Ha módosít egy meglévő szabályzatot, a módosítások az összes hozzárendelt felhasználót érintik.
> - Ha teszteli ezt a funkciót, javasolt létrehozni egy tesztelési házirendet, és hozzárendelni a szabályzatot a felhasználók egy tesztelési csoportjához.

### <a name="step-2-check-the-office-version"></a>2. lépés: az Office verziójának keresése

Az alábbi lépéseket követve tesztelheti a szabályzatot, mielőtt az összes felhasználó számára telepítené a szabályzatot.

1. A **Rendszerleíróadatbázis-szerkesztő** alkalmazásban nyissa meg a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`

2. Tekintse meg a `L_UpdateTargetVersion` értéket. A házirend alkalmazása után az érték a megadott verzióra van beállítva, például `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`.

    Ezen a ponton a rendszer sikeresen alkalmazta az Intune-szabályzatot az eszközön.

3. Ezután kényszerítheti az Office frissítését. Nyisson meg egy Office-alkalmazást, például az Excelt. Válassza a frissítés most lehetőséget (valószínűleg a **fiók** menüben).

    A frissítés több percet is igénybe vehet. Megerősítheti, hogy az Office megpróbálja beolvasni a beírt verziót:

      1. Az eszközön nyissa meg a `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`.
      2. Nyissa meg a `VersionDescriptor.xml` fájlt, és lépjen a `<Version>` szakaszra. Az elérhető verziónak meg kell egyeznie az Intune-szabályzatban megadott verzióval, például:

          ![A verziószámot tartalmazó Office XML-fájl verzió szakaszának bejelölése](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. A frissítés telepítése után az Office-alkalmazásnak meg kell jelenítenie az új verziót (például a **fiók** menüben)

## <a name="next-steps"></a>További lépések

[Az Office 365-ügyfelek csatorna-értékeinek frissítése](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)

[Az Office 365 ProPlus készült Office Cloud Policy szolgáltatás áttekintése](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[A Windows 10-es sablonokkal konfigurálja a csoportházirend-beállításokat (ADMX-sablonok) Microsoft Intune](administrative-templates-windows.md)
