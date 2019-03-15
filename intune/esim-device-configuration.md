---
title: eSIM-adatkapcsolatok engedélyezése az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az eSIM-kártya felvétele vagy használata révén különböző díjcsomagokkal férhet hozzá az internethez és az adatokhoz. Az Intune-ban aktiváló kódokat vehet fel vagy importálhat, és egy konfigurációs profil használatával hozzárendelheti azokat az eszközökhöz. Monitorozhatja az eSIM-profilokat és ellenőrizheti az eSIM-kompatibilis eszközök állapotát is.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bdaf5768c1b78fbd07a732ee6690e59638fcff1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57390412"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>eSIM mobilhálózati profilok konfigurálása az Intune-ban – Nyilvános előzetes verzió

> [!NOTE]
> A Microsoftot érdekli az Ön véleménye. Ha kérdezne vagy vitát indítana, küldjön e-mailt a következő címre: `eSIMonIntune@microsoft.com`.

## <a name="introduction"></a>Bevezetés

Az eSIM egy beágyazott SIM-kártya, amely mobilhálózati adatkapcsolaton keresztül teszi lehetővé az eSIM-kompatibilis eszközök, például a [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro), kapcsolódását az internethez. eSIM-kártya birtokában nincs szüksége mobilszolgáltató által kibocsátott SIM-kártyára. A világot járva váltogathatja is a mobilszolgáltatókat és díjcsomagokat, és mindig kapcsolatban maradhat.

Megteheti például, hogy két külön mobil díjcsomagot használ munkához és személyes célra. Utazás közben a díjcsomagokat kínáló helyi mobilszolgáltatók keresésével kapcsolódhat az internethez.

A mobilszolgáltató által megadott egyszeri aktiváló kódokat importálhatja az Intune-ba. A mobilhálózati díjcsomagok eSIM-modulban történő konfigurálásához telepítenie kell az aktiváló kódokat az eSIM-kompatibilis eszközön. Amikor az Intune telepíti az aktiváló kódot, az eSIM-kártya hardver-modulja az aktiváló kódban található adatok révén kapcsolódik a mobilszolgáltatóhoz. A kész eSIM-profil letöltődik az eszközre, és konfigurálva lesz a mobilhálózaton történő aktiváláshoz.

Ahhoz, hogy az eSIM-kártyát az Intune használatával telepítse az eszközön, a következőkre lesz szüksége:

- **esim-kártya használatára képes eszközök**, például a Surface LTE: Lásd: [Ha az eszköz támogatja az esim-kártya](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). Vagy tekintse meg [néhány ismert eSIM-kompatibilis eszköz](#esim-capable-devices) listáját (a jelen cikkben).
- **Windows 10 őszi alkotói frissítéssel rendelkező számítógép** (1709-es vagy újabb), amely regisztrálva van az Intune-on, és MDM-felügyelet alatt áll
- **Aktiváló kódok** a mobilszolgáltatótól Ezeket az egyszer használható aktiváló kódokat fel kell venni az Intune-ban, majd telepíteni kell az eSIM-kompatibilis eszközön. Az eSIM-kártya aktiváló kódjait a mobilszolgáltatójánál szerezheti be.

## <a name="deploy-esim-to-devices---overview"></a>eSIM-kártya telepítése az eszközökön – áttekintés

Az eSIM-kártya telepítése során a rendszergazda a következőket hajtja végre:

1. A mobilszolgáltató által megadott aktiváló kódok importálása
2. Azure Active Directory- (Azure AD-) eszközcsoport létrehozása, amely az Ön eSIM-kompatibilis eszközeit tartalmazza
3. Azure AD-csoport hozzárendelése az Ön importált előfizetés-készletéhez
4. A központi telepítés figyelése

A cikk ezeket a lépéseket veszi sorra.

## <a name="esim-capable-devices"></a>eSIM-kompatibilis eszközök

A következő eszközök eSIM-kompatibilitását már bejelentették, vagy megtalálhatók a piacon. Ellenőrizze, hogy [az eszköze támogatja-e az eSIM-kártyát](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre Folio 13
- Lenovo Yoga C630
- Samsung Galaxy Book 2

## <a name="step-1-add-cellular-activation-codes"></a>1. lépés: Mobilhálózati aktiváló kód hozzáadása

A mobilhálózati aktiváló kódokat a mobilszolgáltató adja meg egy vesszővel tagolt (csv) fájlban. Miután megkapta a fájlt, vegye fel az Intune-ban a következő lépésekben:

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com/).
2. Kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
3. Kattintson az **Eszközkonfiguráció** > **eSIM mobilhálózati profilok** > **Hozzáadás** elemre.
4. Válassza ki az aktiváló kódot tartalmazó CSV-fájlt.
5. Válassza ki **OK** a módosítások mentéséhez.

#### <a name="csv-file-requirements"></a>A CSV-fájlokhoz kapcsolódó követelmények

Az aktiváló kódokat tartalmazó CSV-fájl kezelése során Önnek vagy a rendszergazdának a következőkre kell ügyelnie:

- A fájl csak csv formátumú lehet (fájlnév.csv).
- A fájlstruktúrának meg kell felelnie a szigorú formátumnak. Ha ez nem teljesül, meghiúsul az importálás. Az importálás során az Intune ellenőrzi a fájlt, és hiba esetén a folyamat leáll.
- Az aktiváló kódok csak egyszer használhatók fel. Korábban importált aktiváló kódok importálása nem ajánlott, mert ha ugyanazon vagy egy másik eszközön telepíti azokat, problémák léphetnek fel.
- Minden egyes fájl csak egy adott mobilszolgáltatóhoz, és minden aktiváló kód egy adott számlázási csomaghoz tartozhat. Az Intune véletlenszerűen osztja ki az aktiváló kódokat a megcélzott eszközök között. Nem garantálható, hogy egy adott aktiváló kódot egy adott eszköz kap meg.
- Egy csv-fájlban legfeljebb 1000 aktiválási kód importálható.

#### <a name="csv-file-example"></a>Példa a CSV-fájlra

1. A csv fájl első sora és első cellája a mobilszolgáltató eSIM aktiváló szolgálatának URL-címe, amelynek a neve: SM-DP+ (Subscription Manager Data Preparation server, előfizetés-kezelő adat-előkészítési kiszolgáló). Az URL-cím csak teljesen minősített, vessző nélküli tartománynév (FDQN) lehet.
2. A második és az azt követő összes további sor az egyedi, egyszer használható aktiváló kódokat tartalmazza, kétféle értékkel:

    1. Az első oszlop az egyedi ICCID (a SIM-chip azonosítója)
    2. A második oszlop az egyező eszközazonosítókat tartalmazza, csak vesszővel elválasztva (a végén nincs vessző). Lásd a következő példát:

        ![Mobilszolgáltatói aktiváló kód csv-fájljának mintája](./media/esim-device-configuration/url-activation-code-examples.png)

3. A csv-fájl neve lesz a mobilhálózati előfizetés-készlet neve az Azure Portalon. Az előző képen a fájl neve `UnlimitedDataSkynet.csv`. Tehát az Intune ezt a nevet adja az `UnlimitedDataSkynet.csv` előfizetés-készletnek:

    ![A mobilhálózati előfizetés-készlet neve azonos az aktiváló kód csv-mintafájljának nevével](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>2. lépés: Eszköz Azure AD-csoport létrehozása

Hozzon létre egy eszközcsoportot, amely az eSIM-kompatibilis eszközöket tartalmazza. A [Csoportok hozzáadása](groups-add.md) című cikk felsorolja ezeket a lépéseket.

> [!NOTE]
> - Csak eszközöket célozhat meg, személyeket nem.
> - Javasolt egy eSIM-kompatibilis eszközöket tartalmazó statikus Azure AD eszközcsoport létrehozása. A csoport használata biztosítja, hogy csak eSIM-eszközöket céloz meg.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>3. lépés: Esim-kártya az aktiváló kód hozzárendelése az eszközökhöz

Rendelje hozzá a profilt az eSIM-eszközöket tartalmazó Azure AD-csoporthoz.

1. Az [Azure Portalon](https://portal.azure.com/) kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza a **Microsoft Intune** elemet.
2. Kattintson az **Eszközkonfiguráció** > **eSIM mobilhálózat** > **Profilok** elemre.
3. A profilok listájából válassza ki a hozzárendelendő eSIM mobilhálózati előfizetés-készletet, majd válassza a **Hozzárendelés** lehetőséget.
4. Adja meg, hogy **belefoglalni** vagy **kizárni** szeretne egyes csoportokat, majd jelölje ki őket.

    ![Eszközcsoport belefoglalása a profil hozzáadásához](./media/esim-device-configuration/include-exclude-groups.png)

5. A csoportok kiválasztásakor egy Azure AD-csoportot is választ. Több csoport kiválasztásához használja a **Ctrl** billentyűt, majd jelölje ki a csoportokat.
6. Ha kész, **mentse** a módosításokat.

Az aktiváló kódok csak egyszer használhatók fel. Miután az Intune telepített egy aktiváló kódot az eszközön, az eSIM-modul kapcsolatba lép a mobilszolgáltatóval a mobilhálózati profil letöltéséhez. A kapcsolódással véglegessé válik az eszköz regisztrálása a mobilszolgáltató hálózatába.

## <a name="step-4-monitor-deployment"></a>4. lépés: A figyelő üzembe helyezés

#### <a name="review-the-deployment-status"></a>A központi telepítés állapotának áttekintése

A profil hozzárendelése után figyelheti az előfizetési készlet központi telepítésének állapotát.

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com/).
2. Kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
3. Kattintson az **Eszközkonfiguráció** > **eSIM mobilhálózati profilok** elemre. A megjelenő lista tartalmaz minden meglévő eSIM mobilhálózati előfizetési készletet.
4. Válasszon ki egy előfizetést, és tekintse át a **központi telepítés állapotát**.

#### <a name="check-the-profile-status"></a>Profil állapotának ellenőrzése
Az eszközprofil létrehozása után az Intune grafikus diagramokat nyújt. Ezek a diagramok a profilok állapotát jelenik meg, például, hogy hozzá vannak-e rendelve eszközökhöz, vagy tartalmaznak-e ütközéseket.

1. Válassza ki az **Eszközkonfiguráció** > **eSIM mobilhálózati profilok** > Meglévő előfizetés kiválasztása lehetőséget.
2. Az **Áttekintés** lapon a felső grafikon mutatja az adott eSIM mobilhálózati előfizetés-készlet központi telepítéséhez rendelt eszközök számát.

    Emellett más platformok eszközeinek számát is megjeleníti, ha ezek ugyanahhoz az eszközprofilhoz vannak rendelve.

    Az Intune megjeleníti az eszközökhöz rendelt aktiváló kód kiküldésének és telepítésének állapotát.

    - **Az eszköz nincs szinkronizálva**: Az eszköz nem lépett Intune kapcsolatba, a központi telepítésre vonatkozó házirendet esim-kártya létrehozása óta
    - **Függőben lévő aktiválási**: Egy átmeneti állapot, ha az Intune aktívan telepíti az aktiváló kódot az eszközön
    - **Aktív**: Aktiváló kódot a telepítés sikerült
    - **Az aktiválás sikertelen**: Aktiválási kód telepítése nem sikerült – hibaelhárítási útmutató megtekintéséhez.

#### <a name="view-the-detailed-device-status"></a>A részletes eszközállapot megtekintése

Figyelheti és megtekintheti az Eszközállapotban megtekinthető eszközök részletes listáját.**

1. Válassza ki az **Eszközkonfiguráció** > **eSIM mobilhálózati profilok** > Meglévő előfizetés kiválasztása lehetőséget.
2. Kattintson az **Eszközállapot** elemre. Az Intune megjeleníti az eszköz további adatait:

  - **Eszköz neve**: Az eszközre irányuló
  - **Felhasználói**: A regisztrált eszköz felhasználója
  - **ICCID**: A mobile által nyújtott egyedi kódot az aktiváló kód telepítve az eszközön belüli működésre
  - **Aktiválási állapot**: Az aktiváló kód az eszköz Intune-ban letöltésére és telepítésére állapota
  - **Mobilhálózati állapot**: A mobileszköz operátor által biztosított állapota. A hibaelhárításhoz vegye fel a kapcsolatot a mobilszolgáltatóval.
  - **Utolsó bejelentkezés**: Az eszköz utolsó Intune-nal közölt dátuma

#### <a name="monitor-esim-profile-details-on-the-actual-device"></a>Az eSIM-profil adatainak figyelése az adott eszközön

1. A saját eszközön nyissa meg a **Beállítások** részt, majd > keresse meg a **Hálózat és internet** lehetőséget.
2. Válassza ki a **Mobilhálózat** > **eSIM-profilok kezelése** lehetőséget.
3. Megjelenik az eSIM-profilok listája:

    ![eSIM-profilok megtekintése a saját eszközbeállításokban](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>eSIM-profil eltávolítása az eszközről

Ha az Azure AD-csoportból eltávolítja az eszközt, az eSIM-profil is el lesz távolítva. Hajtsa végre a következőket:

1. Ellenőrizze, hogy az eSIM-eszközöket tartalmazó Azure AD-csoportot használja.
2. Nyissa meg az Azure AD-csoportot, és távolítsa el belőle az eszközt.
3. Amikor az eltávolított eszköz kapcsolatba lép az Intune-nal, a frissített szabályzat értékelése után az eSIM-profil el lesz távolítva.

Az eSIM-profil akkor is el lesz távolítva, ha az eszközt [kivonják](devices-wipe.md#retire), ha a felhasználó törölte az eszköz regisztrációját, vagy ha az eszközön a [távoli eszközműveletek alaphelyzetbe állítása](devices-wipe.md#wipe) parancs fut.

> [!NOTE]
> Előfordulhat, hogy a profil eltávolítása nem állítja le a számlázást. Lépjen kapcsolatba a mobilszolgáltatóval, és ellenőrizze az eszköz számlázási állapotát.

## <a name="best-practices--troubleshooting"></a>Ajánlott eljárások és hibaelhárítás

- Figyeljen a csv-fájl megfelelő formázására. Ellenőrizze, hogy a fájl nem tartalmaz duplikált kódokat, több mobilszolgáltatót, vagy többféle díjcsomagot. Ne feledje, hogy minden egyes fájl csak egy mobilszolgáltatóhoz és egy mobilhálózati díjcsomaghoz tartozhat.
- Hozzon létre egy statikus Azure AD-eszközcsoportot, amely csak a megcélzott eSIM-eszközöket tartalmazza.
- Ha a központi telepítés állapotában problémát tapasztal, ellenőrizze a következőket:
  - **Fájl formátuma nem megfelelő**: Lásd: **1. lépés: Adja hozzá a mobilhálózati aktiválókódot** (a jelen cikkben) való megfelelően formázza a fájlt.
  - **Mobilhálózati az aktiválás sikertelen, lépjen kapcsolatba mobilszolgáltató**: Az aktiváló kód nem lehet aktiválni a hálózaton belül. Vagy sikertelen volt a profil letöltése és a mobilhálózati aktiválás.

## <a name="next-steps"></a>További lépések
[Eszközprofilok konfigurálása](device-profiles.md)
