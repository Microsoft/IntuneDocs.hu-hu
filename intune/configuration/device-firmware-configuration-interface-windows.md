---
title: A Windows BIOS szolgáltatásainak frissítése a MDM-szabályzatok használatával Microsoft Intune-Azure | Microsoft Docs
description: Adja hozzá az eszköz belső vezérlőprogram-konfigurációs felületének (DFCI) profilját az UEFI-beállítások, például a processzor, a beépített hardver és a rendszerindítási beállítások kezeléséhez Microsoft Intune Windows 10-es eszközökön.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6d4b076b508316cdb2d3d5f2814fc5e46a014e7
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709515"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>Eszköz belső vezérlőprogram konfigurációs felületi profiljainak használata Microsoft Intune (nyilvános előzetes verzió) esetén Windows-eszközökön

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ha az Intune-t használja az Autopilot-eszközök kezeléséhez, a regisztrációt követően az UEFI (BIOS) beállításait is kezelheti az eszköz belső vezérlőprogram konfigurációs felületének (DFCI) használatával. Az előnyök, forgatókönyvek és előfeltételek áttekintését lásd: [a DFCI áttekintése](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/).

A DFCI [lehetővé teszi](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) , hogy a Windows átadja a felügyeleti parancsokat az Intune-ból az UEFI-be (Unified Extensible Firmware Interface).

Az Intune-ban ezzel a szolgáltatással vezérelheti a BIOS beállításait. A belső vezérlőprogram általában rugalmasabb a kártékony támadásokkal szemben. Korlátozza a végfelhasználók számára a BIOS feletti irányítást, ami jó megoldás a feltört helyzetben.

Például a Windows 10-es eszközöket biztonságos környezetben kell használni, és le szeretné tiltani a kamerát. A kamerát letilthatja a belső vezérlőprogram-rétegben, így nem számít, hogy a végfelhasználó milyen módon működik. Az operációs rendszer újratelepítése vagy a számítógép törlése nem kapcsolja vissza a kamerát. Egy másik példában a rendszerindítási beállítások zárolásával megakadályozhatja, hogy a felhasználók egy másik operációs rendszert vagy a Windows egy régebbi verzióját, amely nem rendelkezik azonos biztonsági funkciókkal.

Egy régebbi Windows-verzió újratelepítésekor telepítsen egy különálló operációs rendszert, vagy formázza a merevlemezt, nem bírálhatja felül a DFCI-felügyeletet. Ez a funkció megakadályozza, hogy a kártevők az operációs rendszer folyamataival kommunikáljanak, beleértve a emelt szintű operációsrendszer-folyamatokat is. A DFCI megbízhatósági lánca nyilvános kulcsú titkosítást használ, és nem függ a helyi UEFI (BIOS) jelszavas biztonságtól. Ez a biztonsági réteg megakadályozza, hogy a helyi felhasználók hozzáférjenek a felügyelt beállításokhoz az eszköz UEFI-(BIOS-) menüiből.

Ez a funkció az alábbiakra vonatkozik:

- Windows 10 RS5 (1809) és újabb verziók a támogatott UEFI-ben

## <a name="before-you-begin"></a>Előkészületek

- Az eszköz gyártójának a gyártási folyamatban vagy a telepített belső vezérlőprogram-frissítésnél hozzá kell adnia az UEFI belső vezérlőprogram-DFCI. A [DFCI támogató gyártók](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci), illetve a DFCI használatához szükséges belső vezérlőprogram-verzió meghatározásához használja az eszközök gyártóit.

- Az eszközt regisztrálni kell a Windows Autopilot számára egy [Microsoft Cloud megoldás-szolgáltató (CSP) partner](https://partner.microsoft.com/cloud-solution-provider)által, vagy közvetlenül az OEM-nek kell regisztrálnia. 

  Az Autopilot szolgáltatáshoz manuálisan regisztrált eszközök, például [a csv-fájlból importált adatok](../enrollment/enrollment-autopilot.md#add-devices)nem ENGEDÉLYEZETTEK a DFCI használatakor. A DFCI-kezelés kialakításával az eszköz kereskedelmi beszerzésének külső igazolására van szükség egy SZÁMÍTÓGÉPGYÁRTÓ vagy egy Microsoft CSP-partner regisztrálása révén a Windows Autopilot szolgáltatásban.

  Az eszköz regisztrálása után a sorozatszám megjelenik a Windows Autopilot-eszközök listájában.

  Az Autopilot szolgáltatással kapcsolatos további információkért, beleértve a követelményeket is, lásd: [Windows-eszközök regisztrálása az Intune-ban a Windows Autopilot használatával](../enrollment/enrollment-autopilot.md).

## <a name="create-your-azure-ad-security-groups"></a>Azure AD-beli biztonsági csoportok létrehozása

Az Autopilot Deployment-profilok az Azure AD biztonsági csoportokhoz vannak rendelve. Ügyeljen arra, hogy olyan csoportokat hozzon létre, amelyek tartalmazzák a DFCI által támogatott eszközöket. A DFCI-eszközök esetében a legtöbb szervezet felhasználói csoportok helyett létrehozhat eszközcsoport-csoportokat. Vegye figyelembe a következő forgatókönyveket:

- Az emberi erőforrások (HR) különböző Windows-eszközökkel rendelkeznek. Biztonsági okokból nem szeretné, hogy a csoport minden felhasználója használhassa a kamerát az eszközökön. Ebben a forgatókönyvben létrehozhat egy HR biztonsági felhasználói csoportot, így a szabályzat a HR-csoportban lévő felhasználókra is vonatkozik, függetlenül az eszköz típusától.
- A gyártási emeleten 10 eszköz van. Az összes eszközön meg szeretné akadályozni, hogy az eszközök USB-eszközről induljon el. Ebben az esetben létrehozhat egy biztonsági eszközök csoportot, és hozzáadhatja a 10 eszközt a csoporthoz.

A csoportok Intune-beli létrehozásával kapcsolatos további információkért lásd: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](../fundamentals/groups-add.md).

## <a name="create-the-profiles"></a>Profilok létrehozása

A DFCI használatához hozza létre a következő profilokat, és rendelje hozzá őket a csoportjához.

### <a name="create-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil létrehozása

Ez a profil beállítja és előre konfigurálja az új eszközöket. Az [Autopilot Deployment-profil](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) a profil létrehozásának lépéseit sorolja fel.

### <a name="create-an-enrollment-state-page-profile"></a>Regisztrációs állapot lap profiljának létrehozása

Ez a profil gondoskodik arról, hogy az eszközök ellenőrzése és engedélyezése a DFCI a Windows telepítése során. Erősen ajánlott ezt a profilt használni az eszközök használatának letiltásához, amíg az összes alkalmazás és profil nincs telepítve. A [regisztrációs állapot lap profilja](../enrollment/windows-enrollment-status.md) felsorolja a profil létrehozásának lépéseit.

### <a name="create-the-dfci-profile"></a>A DFCI-profil létrehozása

Ez a profil tartalmazza a konfigurált DFCI-beállításokat.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. Egy jó profilnév például a **Windows: DFCI-beállítások konfigurálása Windows-eszközökön**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza a **Windows 10-es vagy újabb verzió** lehetőséget.
    - **Profil típusa**: válassza az **eszköz belső vezérlőprogram konfigurációs felületét**.

4. A beállítások konfigurálása:

    - Az **UEFI-(BIOS-) beállítások módosításának engedélyezése a helyi felhasználó számára**: az Ön beállításai:
      - **Csak a nem konfigurált beállítások**: a helyi felhasználó megváltoztathatja a beállításokat, *kivéve* azokat, amelyek explicit módon **engedélyezik** vagy **letiltják** az Intune-t.
      - **Nincs**: a helyi felhasználó nem változtathatja meg az UEFI-(BIOS-) beállításokat, beleértve a DFCI-profilban nem szereplő beállításokat is.

    - **CPU-és IO-virtualizálás**: a lehetőségek:
        - **Nincs konfigurálva**: az Intune nem érinti ezt a funkciót, és az összes beállítást elhagyja.
        - **Engedélyezve**: a BIOS lehetővé teszi a platform CPU-és IO-virtualizációs funkcióinak használatát az operációs rendszer számára. Bekapcsolja a Windows virtualizációs alapú biztonsági és eszköz-Guard technológiákat.
        - **Letiltás**: a BIOS letiltja a platform CPU-& i/o-virtualizációs képességeit, és megakadályozza azok használatát.
    - **Fényképezőgépek**: a lehetőségek:
        - **Nincs konfigurálva**: az Intune nem érinti ezt a funkciót, és az összes beállítást elhagyja.
        - **Engedélyezve**: az UEFI (BIOS) által közvetlenül kezelt összes beépített kamera engedélyezve van. A perifériák, például az USB-kamerák, nem érintettek.
        - **Letiltva**: az UEFI (BIOS) által közvetlenül kezelt összes beépített kamera le van tiltva. A perifériák, például az USB-kamerák, nem érintettek.
    - **Mikrofonok és hangszórók**: a lehetőségek:
        - **Nincs konfigurálva**: az Intune nem érinti ezt a funkciót, és az összes beállítást elhagyja.
        - **Engedélyezve**: az UEFI (BIOS) által közvetlenül kezelt beépített mikrofonok és hangszórók engedélyezve vannak. A perifériákat, például az USB-eszközöket, nem érinti.
        - **Letiltva**: az UEFI (BIOS) által közvetlenül kezelt beépített mikrofonok és hangszórók le vannak tiltva. A perifériákat, például az USB-eszközöket, nem érinti.
    - **Rádiók (Bluetooth, Wi-Fi, NFC stb.)** : a lehetőségek:
        - **Nincs konfigurálva**: az Intune nem érinti ezt a funkciót, és az összes beállítást elhagyja.
        - **Engedélyezve**: az UEFI (BIOS) által közvetlenül kezelt összes beépített rádió engedélyezve van. A perifériákat, például az USB-eszközöket, nem érinti.
        - **Letiltva**: az UEFI (BIOS) által közvetlenül kezelt összes beépített rádió le van tiltva. A perifériákat, például az USB-eszközöket, nem érinti.

        > [!WARNING]
        > Ha letiltja a **választógombok** beállítását, az eszköznek vezetékes hálózati kapcsolatra van szüksége. Ellenkező esetben előfordulhat, hogy az eszköz nem felügyelhető.

    - **Rendszerindítás külső adathordozóról (USB, SD)** : az Ön beállításai:
        - **Nincs konfigurálva**: az Intune nem érinti ezt a funkciót, és az összes beállítást elhagyja.
        - **Engedélyezve**: az UEFI (BIOS) lehetővé teszi a nem merevlemezes tárterületről történő rendszerindítás elindítását.
        - **Letiltva**: az UEFI (BIOS) nem teszi lehetővé a nem merevlemezes tárolóról történő rendszerindítás használatát.
    - **Rendszerindítás hálózati adapterekről**: az Ön beállításai:
        - **Nincs konfigurálva**: az Intune nem érinti ezt a funkciót, és az összes beállítást elhagyja.
        - **Engedélyezve**: az UEFI (BIOS) lehetővé teszi a beépített hálózati adapterekről történő rendszerindítást.
        - **Letiltva**: az UEFI (BIOS) nem engedélyezi a beépített hálózati adapterek indítását.

5. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a listában.

## <a name="assign-the-profiles-and-reboot"></a>A profilok kiosztása és újraindítása

A profilok létrehozása után készen állnak a [hozzárendelésre](../configuration/device-profile-assign.md). Ügyeljen arra, hogy a profilokat a DFCI-eszközöket tartalmazó Azure AD-beli biztonsági csoportokhoz rendelje.

Amikor az eszköz futtatja a Windows Autopilot-t, a regisztráció állapota lapon a DFCI újraindítást igényelhet. Ez az első újraindítás az UEFI-t regisztrálja az Intune-ban. 

Ha ellenőrizni szeretné, hogy az eszköz regisztrálva van-e, újra lehet indítani az eszközt, de ez nem kötelező. Az eszköz gyártójának utasításait követve nyissa meg az UEFI menüt, és ellenőrizze, hogy az UEFI most már felügyelve van-e.

Amikor az eszköz legközelebb szinkronizál az Intune-nal, a Windows megkapja a DFCI beállításait. Indítsa újra az eszközt. Ez a harmadik újraindítás szükséges ahhoz, hogy az UEFI megkapja a DFCI beállításait a Windows rendszerből.

## <a name="update-existing-dfci-settings"></a>Meglévő DFCI-beállítások frissítése

Ha módosítani kívánja a meglévő DFCI-beállításokat a használatban lévő eszközökön, akkor a. A meglévő DFCI-profilban módosítsa a beállításokat, és mentse a módosításokat. Mivel a profil már hozzá van rendelve, az új DFCI-beállítások az alábbiak szerint lépnek érvénybe:

1. Az eszköz az Intune szolgáltatással ellenőrzi a profil frissítéseinek áttekintését. A bejelentkezések különböző időpontokban történnek. További információ: amikor az [eszközök házirend-, profil-vagy alkalmazás-frissítéseket kapnak](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

2. Az új beállítások érvénybe léptetéséhez indítsa újra az eszközt [távolról](../remote-actions/device-restart.md) vagy helyileg.

Megadhatja a [bejelentkező eszközöket](../remote-actions/device-sync.md)is. Sikeres szinkronizálás után a rendszer [újraindítja a jelet](../remote-actions/device-restart.md).

>[!NOTE]
> A DFCI-profil törlése vagy az eszköz a profilhoz rendelt csoportból való eltávolítása nem távolítja el a DFCI-beállításokat, vagy újból engedélyezi az UEFI (BIOS) menüket. Ha le szeretné állítani a DFCI használatát, frissítse a meglévő DFCI-profilt. További információ a lépésekről: [az eszköz](#retire) kivonása ebben a cikkben.

## <a name="reuse-retire-or-recover-the-device"></a>Az eszköz újbóli felhasználása, kivonása vagy helyreállítása

### <a name="reuse"></a>Újbóli használatának

Ha azt tervezi, hogy alaphelyzetbe állítja a Windowst az eszköz újrafelhasználásához, [törölje az eszközt](../remote-actions/devices-wipe.md). Ne **távolítsa** el az Autopilot-eszköz rekordját.

Az eszköz törlését követően helyezze át az eszközt az új DFCI és Autopilot-profilokhoz rendelt csoportba. Győződjön meg arról, hogy újraindítja az eszközt a Windows telepítő újbóli futtatásához.

### <a name="retire"></a>Kivonás

Ha készen áll az eszköz kivonására és a felügyelet alól való kivonására, frissítse a DFCI-profilt a kilépési állapotban lévő UEFI (BIOS) beállításokra. Az összes beállítást általában engedélyezni szeretné. Példa:

1. Nyissa meg a DFCI-profilt (az**eszköz konfigurációs** > **profiljai**).
2. Módosítsa a **helyi felhasználó engedélyezése az UEFI-(BIOS-) beállítások módosítását** **csak a nem konfigurált beállításokra**.
3. Állítsa be az összes többi beállítást, hogy **ne legyen konfigurálva**.
4. Mentse a beállításokat.

Ezekkel a lépésekkel feloldható az eszköz UEFI-(BIOS-) menüinek feloldása. Az értékek változatlanok maradnak, mint a profil (**engedélyezve** vagy **Letiltva**), és nem állíthatók vissza az alapértelmezett operációsrendszer-értékekre.

Most már készen áll az eszköz törlésére. Az eszköz törlését követően törölje az Autopilot-rekordot. A rekord törlése megakadályozza, hogy az eszköz automatikusan újra regisztrálja az újraindítást.

### <a name="recover"></a>Visszaszerez

Ha töröl egy eszközt, és törli az Autopilot-rekordot az UEFI (BIOS) menük zárolásának feloldása előtt, akkor a menük zárolva maradnak. Az Intune nem tudja elküldeni a profilok frissítését a zárolás feloldásához.

Az eszköz zárolásának feloldásához nyissa meg az UEFI (BIOS) menüt, és frissítse a felügyeletet a hálózatról. A helyreállítás feloldja a menüket, de az összes UEFI (BIOS) beállítást az előző Intune DFCI-profil értékeire állítja be.

## <a name="end-user-impact"></a>Végfelhasználói hatás

A DFCI házirend alkalmazása esetén a helyi felhasználók nem változtathatják meg a DFCI által konfigurált beállításokat, még akkor sem, ha az UEFI (BIOS) menü jelszavas védelemmel van ellátva. A megadott beállításoktól függően előfordulhat, hogy a végfelhasználók hibákat észlelnek, és nem lehet diagnosztizálni a hardveres összetevőket. Ügyeljen arra, hogy a végfelhasználók számára a letiltott beállítások magyarázatát biztosító dokumentációt adjon meg.  

## <a name="next-steps"></a>További lépések

A profil hozzárendelése után [Figyelje annak állapotát](../device-profile-monitor.md).
