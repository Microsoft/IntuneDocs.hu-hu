---
title: Sablonok használata Windows 10-es eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
description: A Windows 10-es eszközökhöz tartozó beállítási csoportok létrehozásához használja a Microsoft Intune felügyeleti sablonjait. Ezekkel a beállításokkal vezérelheti az Office-programokat, a Microsoft Edge-t, az Internet Explorer biztonságos funkcióit, vezérelheti a OneDrive, a távoli asztal funkcióit, az Automatikus lejátszást, az energiagazdálkodási beállításokat, valamint a HTTP-nyomtatást. használjon különböző felhasználói bejelentkezési beállításokat, és szabályozza az Eseménynapló méretét.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7f5a85896a2e6e7be845b2314c4f837dcaeb7b0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507018"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Csoportházirend-beállítások konfigurálása a Windows 10-es sablonokkal Microsoft Intune

A szervezetben lévő eszközök kezelésekor olyan beállításokat kíván létrehozni, amelyek különböző eszközcsoport-csoportokra vonatkoznak. Például több eszközosztály is van. A Groupa esetében a beállítások egy adott készletét szeretné hozzárendelni. A GroupB esetében más beállításokat szeretne hozzárendelni. Azt is szeretné, hogy a konfigurálható beállítások egyszerű áttekintése legyen.

Ezt a feladatot Microsoft Intune **Felügyeleti sablonok** használatával végezheti el. A felügyeleti sablonok több száz olyan beállítást foglalnak magukban, amelyek a Microsoft Edge 77-es és újabb verzióiban, az Internet Explorerben, Microsoft Office programokban, a távoli asztalokon, a OneDrive, a jelszavakban és a PIN-kódokban Ezek a beállítások lehetővé teszik a csoport rendszergazdái számára a csoportházirendek kezelését a felhő használatával.

A Windows beállításai hasonlóak a csoportházirend (GPO) beállításaihoz Active Directory (AD). Ezek a beállítások a Windowsba vannak építve, és az [ADMX által támogatott](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) , XML-t használó beállítások. Az Office-és a Microsoft Edge-beállítások az ADMX-betöltés alatt állnak, és az [Office felügyeleti sablon fájljai](https://www.microsoft.com/download/details.aspx?id=49030) és a [Microsoft Edge felügyeleti sablonfájlok](https://www.microsoftedgeinsider.com/enterprise)ADMX-beállításaival használhatók. Az Intune-sablonok azonban 100%-os felhő-alapúak. Egyszerű és közvetlen továbbítási módot kínálnak a beállítások konfigurálásához, és megkeresik a kívánt beállításokat.

**Felügyeleti sablonok** beépítettek az Intune-ba, és nincs szükség testreszabásra, beleértve az OMA-URI használatát is. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a sablonokat a Windows 10-es eszközök felügyeletéhez használja egyablakos szolgáltatásként.

Ez a cikk a Windows 10-es eszközökhöz készült sablonok létrehozásának lépéseit ismerteti, és bemutatja, hogyan szűrheti az összes elérhető beállítást az Intune-ban. A sablon létrehozásakor létrehoz egy eszköz-konfigurációs profilt. Ezt a profilt ezután hozzárendelheti vagy üzembe helyezheti a szervezet Windows 10-es eszközein.

## <a name="before-you-begin"></a>Előkészületek

- Ezen beállítások némelyike a Windows 10 1703-es (RS2) verziótól kezdődően érhető el. Bizonyos beállítások nem szerepelnek az összes Windows-kiadásban. A legjobb megoldás az, ha a Windows 10 Enterprise 1903 (19H1) és újabb verzióját használja.

- A Windows-beállítások a [Windows házirend-kriptográfiai](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies)szolgáltatásait használják. A kriptográfiai szolgáltatók a Windows különböző kiadásaiban működnek, például a Home, a Professional, a Enterprise stb. Ha szeretné megtekinteni, hogy egy CSP egy adott kiadáson működik-e, lépjen a [Windows házirend-kriptográfiai](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies)szolgáltatásra.

## <a name="create-a-template"></a>Sablon létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: adja meg a profil nevét.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: válassza a **Felügyeleti sablonok**lehetőséget.

4. Válassza a **Létrehozás** lehetőséget. Az új ablakban válassza a **Beállítások**lehetőséget. Minden beállítás fel van sorolva, és az előző és a következő nyilak használatával további beállításokat tekinthet meg:

    ![Tekintse meg a beállítások listáját, és használja az előző és a tovább gombokat](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Az Intune Windows-beállításai összekapcsolják a helyszíni csoportházirend elérési útját Helyicsoportházirend-szerkesztő (`gpedit`).

5. Alapértelmezés szerint a legördülő lista az **összes terméket**megjeleníti. A listából úgy is szűrheti a beállításokat, hogy csak a **Windows** -beállításokat jelenítse meg, csak az **Office** -beállításokat, vagy csak az **Edge 77-es vagy újabb verzióját** jeleníti meg:

    ![A lista szűrése az összes Windows vagy az összes Office-beállítás megjelenítéséhez a felügyeleti sablonokban az Intune-ban](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > A Microsoft Edge-beállítások a következőkre vonatkoznak:
    >
    > - A Microsoft Edge 77-es és újabb verziója. A Microsoft Edge 45-es és korábbi verziójának konfigurálásához tekintse meg a [Microsoft Edge böngésző eszközének korlátozási beállításait](device-restrictions-windows-10.md#microsoft-edge-browser).
    > - Windows 10 RS4 és újabb, [KB 4512509](https://support.microsoft.com/kb/4512509) -es verzióval
    > - Windows 10 RS5 és újabb, [KB 4512534](https://support.microsoft.com/kb/4512534) -es verzióval
    > - Windows 10 19H1 és újabb, [KB 4512941](https://support.microsoft.com/kb/4512941) -es verzióval

6. Válassza ki a kívánt beállításokat. Például az **Office**-on, és válassza a **korlátozott böngészés aktiválása**lehetőséget. Megjelenik a beállítás részletes leírása. Válassza az **engedélyezve**, **Letiltva**lehetőséget, vagy hagyja meg a beállítást **nincs konfigurálva** (alapértelmezett). A részletes leírás azt is ismerteti, hogy mi történik, ha az **engedélyezve**, a **Letiltva**vagy a **nincs konfigurálva**beállítást választja.
7. A módosítások mentéséhez válassza az **OK** gombot.

Folytassa a beállítások listájának átadását, és konfigurálja a kívánt beállításokat a környezetében. Néhány példa:

- A **VBA-makró értesítési beállításainak** beállításával különböző Microsoft Office programokban, például a Wordben és az Excelben kezelheti a VBA-makrókat.
- A fájlok letöltésének **engedélyezése** beállítással engedélyezheti vagy tilthatja le a letöltéseket az Internet Explorerben.
- **Jelszó kérése, ha egy számítógép felébred (csatlakoztatva)** , hogy a felhasználók jelszót kérjenek, amikor az eszközök alvó üzemmódból ébrednek.
- Az aláíratlan **ActiveX-vezérlők letöltése** beállítással megakadályozhatja, hogy a felhasználók aláíratlan ActiveX-vezérlőket töltsenek le az Internet Explorerben.
- A **rendszer-visszaállítás kikapcsolása** beállítás használatával engedélyezheti vagy megakadályozhatja, hogy a felhasználók futtassák a rendszer-visszaállítást az eszközön.
- A **Kedvencek importálásának engedélyezése** beállítás megadásával engedélyezheti vagy letilthatja a felhasználók számára a Kedvencek importálását egy másik böngészőből a Microsoft Edge-be.
- És még sok más...

## <a name="find-some-settings"></a>Néhány beállítás megkeresése

Ezekben a sablonokban több száz beállítás érhető el. A beépített funkciókkal könnyebben megtalálhatja a konkrét beállításokat:

- A sablonban válassza a **Beállítások**, az **állapot**, a **beállítás típusa**vagy az **elérési út** oszlopok elemet a lista rendezéséhez. Válassza ki például az **elérési út** oszlopot az `Microsoft Excel` elérési út összes beállításának megtekintéséhez:

  ![Kattintson a Path (elérési út) elemre a csoportházirend vagy az ADMX elérési útja szerint csoportosított összes beállítás megjelenítéséhez az Intune-ban.](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- A sablonban a **keresőmező** segítségével megtalálhatja a kívánt beállításokat. A kereséshez állítsa be a címet vagy az elérési utat. Keressen például a `copy` kifejezésre. A `copy` összes beállítása látható:

  ![Az Intune-beli felügyeleti sablonokban található összes Windows-és Office-beállítás megjelenítésének keresése a másolásban](./media/administrative-templates-windows/search-copy-settings.png) 

  Egy másik példában keressen rá a `microsoft word` kifejezésre. Megjelenik a Microsoft Word programhoz beállítható összes beállítás. Keressen rá a `explorer` kifejezésre, és tekintse meg a sablonhoz felvehető Internet Explorer-beállításokat.

## <a name="next-steps"></a>További lépések

A sablon létre lett hozva, de még nem csinál semmit. Ezután [rendelje hozzá a sablont, más néven profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).
