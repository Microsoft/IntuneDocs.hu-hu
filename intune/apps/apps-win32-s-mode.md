---
title: Win32-alkalmazások engedélyezése S módú eszközökön
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan engedélyezheti a Win32-alkalmazásokat az S módú eszközökön a Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e17972a3a87bd9c42db54753d4da3bb81703377
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563625"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>Win32-alkalmazások engedélyezése S módú eszközökön

A [Windows 10 S Mode](https://docs.microsoft.com/windows/deployment/s-mode) egy zárolt operációs rendszer, amely csak az áruházbeli alkalmazásokat futtatja. Alapértelmezés szerint a Windows S Mode-eszközök nem engedélyezik a Win32-alkalmazások telepítését és végrehajtását. Ezek az eszközök egyetlen *Win 10-es alapházirenddel*rendelkeznek, amely az S Mode-eszközt zárolja az összes Win32-alkalmazás futtatásával. Ha azonban az Intune-ban létrehoz és használ egy S-alapú **kiegészítő szabályzatot** , akkor a Win32-alkalmazásokat telepítheti és futtathatja a Windows 10 S üzemmódú felügyelt eszközökön. A [Microsoft Defender Application Control (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) PowerShell-eszközök használatával egy vagy több kiegészítő szabályzatot hozhat létre a Windows S üzemmódhoz. A kiegészítő szabályzatokat az [Eszközkezelő-aláírási szolgáltatással (betétbiztosítási rendszerek)](https://go.microsoft.com/fwlink/?linkid=2095629) vagy a [SignTool. exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) fájllal kell aláírnia, majd fel kell töltenie és terjesztenie kell a szabályzatokat az Intune-on keresztül. Alternatív megoldásként aláírhatja a kiegészítő szabályzatokat a szervezete egy kiépítési tanúsítvánnyal, azonban az előnyben részesített módszer a betétbiztosítási rendszerek használata. Abban a példányban, amelyet a szervezete által használt összekapcsolási tanúsítvány használatával használ, az eszközön jelen kell lennie az olyan főtanúsítványnak, amelyet az összekapcsolási tanúsítványnak, amely a szervezeti egységnek van kialakítva.

Az S módú kiegészítő szabályzat az Intune-ban való hozzárendelésével engedélyezheti, hogy az eszköz kivételt hozzon az eszköz meglévő üzemmód-házirendjéhez, amely lehetővé teszi a feltöltött kapcsolódó aláírt alkalmazás-katalógus használatát. A szabályzat az S Mode-eszközön használható alkalmazások engedélyezési listáját (az alkalmazás katalógusát) állítja be.

> [!NOTE]
> A Win32-alkalmazások az S módú eszközökön csak a Windows 10 2019 Update (Build 18363) vagy újabb verziójában támogatottak.

<!-- Add WDAC tooling diagram  -->

A Win32-alkalmazások Windows 10-es eszközökön való futtatásának engedélyezése a következő lépésekkel végezhető el:

1. Az S Mode-eszközök Intune-on keresztüli engedélyezése a Windows 10 S beléptetési folyamatának részeként.
2. Hozzon létre egy kiegészítő szabályzatot a Win32-alkalmazások engedélyezéséhez:
   - Kiegészítő szabályzat létrehozásához használhatja a [Microsoft Defender Application Control (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) eszközöket. A házirendben lévő alapházirend-azonosítónak meg kell egyeznie az S módú alapházirend-azonosítóval (amely a-ügyfélen rögzített kód). Győződjön meg arról is, hogy a házirend verziója magasabb, mint az előző verzió.
   - A betétbiztosítási rendszerek használatával aláírhatja a kiegészítő szabályzatot. További információ: [kód integritási szabályzatának aláírása az Eszközkezelő aláírásával](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing).
   - Az aláírt kiegészítő szabályzatot az Intune-ba feltöltve egy Windows 10 S módú kiegészítő szabályzat létrehozásával (lásd alább).
3. A Win32-alkalmazások katalógusait az Intune-on keresztül engedélyezheti:
   - A katalógus fájljait (1 minden alkalmazáshoz) létrehozhatja, és a betétbiztosítási rendszerek vagy más tanúsítvány-infrastruktúrával aláírhatja őket.
   - Az aláírt katalógust a [Microsoft Win32 Content PREP Tool](https://go.microsoft.com/fwlink/?linkid=2065730)használatával csomagolja ki a *. intunewin fájlba.* További információ: [win32 app Management – a Win32 alkalmazás tartalmának előkészítése feltöltésre](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload).
   - Az Intune az aláírt alkalmazás-katalógus használatával telepíti a Win32 alkalmazást az S Mode eszközön az [Intune felügyeleti bővítménnyel](~/apps/intune-management-extension.md).

> [!NOTE]
> Az üzletági (LOB) `.appx` és `.appx` Windows 10-es üzemmódú csomagokat a rendszer a Microsoft Store for Business (MSFB) aláírásával fogja támogatni.
>
> Az alkalmazásokra vonatkozó **kiegészítő szabályzatot** az Intune felügyeleti bővítménnyel kell továbbítani.
>
> Az S módú házirendeket az eszköz szintjén kell kikényszeríteni. Az eszközön több megcélzó házirend lesz egyesítve. Az egyesített szabályzat érvénybe lép az eszközön.

Windows 10 S módú kiegészítő szabályzat létrehozásához kövesse az alábbi lépéseket:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **alkalmazások** > **S módú kiegészítő házirendek** elemet > a **házirend létrehozása**lehetőséget.
3. A házirendfájl hozzáadása előtt létre kell hoznia és alá kell írnia a **fájlt**. További információkért lásd:
    - [WDAC-szabályzat létrehozása PowerShell-eszközök használatával és bináris formátumba konvertálása](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Bejelentkezés az Eszközkezelő-aláírási szolgáltatás használatával](https://go.microsoft.com/fwlink/?linkid=2095629) **(ajánlott)**

4. Az **alapvető beállítások** lapon adja hozzá a következő értékeket:

    | Érték | Description |
    |--------------|------------------------------------------------|
    | Házirend fájl | A WDAC házirendet tartalmazó fájl. |
    | Név | A szabályzat neve. |
    | Description | Választható A szabályzat leírása. |

5. Kattintson a **Tovább gombra: hatókör címkék**.<br>
   A **hatókör címkék** lapon megadhatja, hogy ki láthatja az alkalmazás-szabályzatot az Intune-ban. A hatókör-címkékkel kapcsolatos további információkért lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](~/fundamentals/scope-tags.md).

6. Kattintson a **Tovább: hozzárendelések**elemre.<br>
   A **hozzárendelések** lapon hozzárendelheti a szabályzatot a felhasználókhoz és az eszközökhöz. Fontos megjegyezni, hogy a szabályzatot hozzárendelhet egy eszközhöz, függetlenül attól, hogy az eszközt az Intune felügyeli-e.
7. Kattintson a **Tovább gombra: felülvizsgálat + létrehozás** elemre, és tekintse át a profilhoz megadott értékeket.
8. Ha elkészült, kattintson a **Létrehozás** gombra az S módú kiegészítő szabályzat létrehozásához az Intune-ban. 

A szabályzat létrehozása után a rendszer hozzáadja az Intune-ban található S módú kiegészítő szabályzatok listájához. A szabályzat hozzárendelése után a házirend üzembe lesz helyezve az eszközökön. Vegye figyelembe, hogy az alkalmazást ugyanarra a biztonsági csoportra kell telepíteni, mint a kiegészítő szabályzatot. Megkezdheti az alkalmazások célzását és hozzárendelését az eszközökhöz. Ez lehetővé teszi a végfelhasználók számára az alkalmazások telepítését és végrehajtását az S módú eszközökön.

## <a name="removal-of-s-mode-policy"></a>S módú házirend eltávolítása

Jelenleg az S módú kiegészítő szabályzat az eszközről való eltávolításához hozzá kell rendelnie és telepítenie kell egy üres szabályzatot, hogy felülírja a meglévő S mód kiegészítő szabályzatát.

## <a name="policy-reporting"></a>Házirend-jelentéskészítés

Az eszköz szintjén kikényszerített S mód kiegészítő szabályzat csak az eszközök szintjén jelent jelentést. A sucesss és a hibákra vonatkozó feltételekhez rendelkezésre áll az eszközök szintjének jelentése. 

Jelentéskészítési értékek, amelyek az Intune-konzolon az S Mode jelentési házirendek esetében láthatók:
- **Sikeres**: az S módú kiegészítő házirend érvényben van.
- **Ismeretlen**: az S módú kiegészítő szabályzat állapota nem ismert.
- **TokenError**: az S mód kiegészítő szabályzata szerkezetileg rendben van, de hiba történt a jogkivonat engedélyezésekor.
- **NotAuthorizedByToken**: a jogkivonat nem engedélyezi ezt az S módú kiegészítő szabályzatot.
- **PolicyNotFound**: az S mód kiegészítő szabályzata nem található.

## <a name="next-steps"></a>További lépések

- További információ: Win32- [alkalmazások az s módban](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s).
- További információk az alkalmazások Intune-hoz való hozzáadásáról: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md).
- A Win32-alkalmazásokkal kapcsolatos további információkért lásd: [Intune win32 app Management](~/apps/apps-win32-app-management.md).
