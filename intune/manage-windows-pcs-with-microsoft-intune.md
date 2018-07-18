---
title: Számítógépek felügyelete az ügyfélszoftverrel
titlesuffix: Microsoft Intune
description: Windows rendszerű számítógépek felügyelete az Intune ügyfélszoftverrel.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: a22aafdca8c049367d4c88d27a07a7c1825a01e3
ms.sourcegitcommit: e6e93419f46e8647d4661eeca09eb1e2e460ad2b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966918"
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Windows rendszerű számítógépek kezelése az Intune-szoftverügyfélen keresztül számítógépként

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> A Microsoft Intune-ban kezelheti a Windows-számítógépeket [mobileszközként a mobileszköz-kezelés (MDM),](windows-enroll.md) vagy számítógépként az Intune szoftverügyfél használatával, a lent ismertetett módon. A Microsoft azonban azt javasolja, hogy az ügyfelek [lehetőség szerint az MDM-megoldást válasszák](windows-enroll.md) a felügyelethez.

Az Intune átfogó megoldást nyújt a mobileszközök kezelésére a szervezetek számára. Az Intune a Windows 10 operációs rendszer beépített modern eszközfelügyeleti lehetőségeinek használatával képes mobileszközként kezelni a Windows rendszerű számítógépeket. A szervezet felügyeleti igényeinek teljesítése érdekében az Intune számítógépként is képes kezelni a Windows rendszerű számítógépeket az Intune-szoftverügyfélen keresztül. Ez a felügyeleti módszer a korábbi Windows operációs rendszer hagyományos számítógép-felügyeleti képességeit használja.

Az Intune-szoftverügyfél a korábbi operációs rendszerrel működő, például a Windows 7 rendszerű számítógépekhez a legalkalmasabb, amelyeket nem lehet mobileszközként kezelni. Az Intune-szoftverügyfél a Csoportházirend és hasonló felügyeleti képességek segítségével kezeli a számítógépeket a felhőből.

Az Intune támogatja a Windows rendszerű számítógépek számítógépként való kezelését a szoftverügyfél használatával – maximum 7000 számítógépig. Ennél is nagyobb méretű környezet esetén mobileszközként kezelheti Windows 10 rendszerű számítógépeit. Az Intune egyes kiadásai és a Windows 10 frissítései a mobileszköz-kezelési architektúrán alapuló felügyeleti funkciókat tartalmaznak. Erősen ajánlott a szervezet áthelyezése a Windows 10 mobileszközként történő kezelésére.


> [!NOTE]
> A Windows 8.1-es vagy újabb rendszerű eszközöket kezelheti számítógépként az Intune-ügyfélszoftverrel, vagy mobileszközként. Mindkét módszert azonban nem használhatja ugyanazon az eszközön. Alaposan mérlegeljen, mielőtt a számítógépeknek az Intune-ügyfélszoftverrel való kezelése mellett döntene. Ez a témakör kizárólag az Intune-szoftverügyféllel PC-ként kezelt eszközökre vonatkozik.

## <a name="requirements-for-intune-pc-client-management"></a>Az Intune-számítógépügyfél általi felügyelet követelményei

**Hardver**: Az Intune-ügyfélszoftver a következő minimális hardverkövetelményekkel telepíthető:

|Követelmény|További információ|
|---------------|--------------------|
|Hálózat|Az ügyfél használatához a számítógépnek internetkapcsolattal kell rendelkeznie.|
|Processzor és memória|A processzorra és a RAM-ra vonatkozó követelményeket a számítógép operációs rendszere határozza meg.|
|Lemezterület|200 MB szabad lemezterület az ügyfélszoftver telepítése előtt.|

**Szoftver**: Az ügyfélszoftver az alábbi szoftverkövetelményekkel telepíthető:

|Követelmény|További információ|
|---------------|--------------------|
|Operációs rendszer | Windows 7 SP1 vagy újabb rendszert futtató eszköz. </br></br>**A Home Edition verziók nem támogatottak.**|
|Rendszergazdai engedélyek|Az ügyfélszoftvert telepítő fióknak helyi rendszergazdai engedélyekkel kell rendelkeznie az eszközön.|
|Windows Installer 3.1|A számítógépnek legalább a Windows Installer 3.1-es verziójával kell rendelkeznie.<br /><br />A Windows Installer verziójának megtekintése egy számítógépen:<br /><br />  A számítógépen kattintson a jobb gombbal a **%windir%\System32\msiexec.exe** fájlra, majd a **Tulajdonságok** menüpontra.<br /><br />A Windows Installer legújabb verzióját letöltheti a Microsoft Developer Network webhelyen található [Windows Installer újraterjeszthető csomagok](http://go.microsoft.com/fwlink/?LinkID=234258) oldalról.|
|Nem kompatibilis ügyfélszoftver eltávolítása|Az Intune-ügyfélszoftver telepítése előtt el kell távolítania a számítógépen esetleg megtalálható Configuration Manager-, Operations Manager-, Operations Management Suite- és Service Manager-ügyfélszoftvert.|

## <a name="deploying-the-intune-software-client"></a>Az Intune-szoftverügyfél üzembe helyezése
Intune-rendszergazdaként több módon is elérhetővé teheti az Intune-szoftverügyfelet a felhasználók számára. Útmutatásért lásd: [Az Intune-szoftverügyfél telepítése Windows rendszerű számítógépekre](install-the-windows-pc-client-with-microsoft-intune.md).

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Számítógép-felügyeleti képességek az Intune-os ügyfélszoftverrel
A legtöbb esetben célszerű regisztrálni az eszközöket az Intune-ban, mivel ez több funkciót biztosít. Ugyanakkor az Intune-szoftverügyféllel is felügyelheti a számítógépeket. Ekkor a következő funkciókat érheti el:

-   **[Szoftverfrissítések kezelése](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)** - Naprakészen tarthatja a számítógépeit, és beállíthatja, hogy a rendszer mikor telepítse a frissítéseket.

-   **[Windows tűzfalházirend](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)** - Ezzel biztosíthatja, hogy a vállalatnál használt számítógépeken ne legyen inaktív vagy nem megfelelően beállított Windows tűzfal.

-   **[Kártevők elleni védelem](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)** - Az Intune Endpoint Protection védelmet használja, amely segít a számítógépes kártevők elleni védelmében.

-   **[Távsegítség](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)** - Az Intune lehetővé teszi a felhasználóknak, hogy az Intune beépített távoli asztali funkciója segítségével kapcsolatba lépjenek az informatikai támogatási csapattal (ehhez a TeamViewer szoftver szükséges).

-   **[Szoftverlicenc-gazdálkodás](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)** - Nyomon követheti az elérhető és a használatban lévő szoftverlicencek számát.
-   **[Alkalmazások központi telepítése](add-apps-for-windows-pcs-in-microsoft-intune.md)** - Szoftvereket telepíthet a felügyelt számítógépekre. Ha a szoftverügyféllel felügyeli a számítógépeket, akkor bizonyos alkalmazásfelügyeleti funkciók nem érhetők el.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Szabályzatok és alkalmazástelepítések működése az Intune-ügyfélszoftverrel

Jóllehet az Intune-ügyfélszoftver a szoftverfrissítések, a Windows tűzfal és az Endpoint Protection kezelésével támogatja a [PC-k védelmét szolgáló felügyeleti funkciókat](policies-to-protect-windows-pcs-in-microsoft-intune.md), az Intune-szoftverügyfél által felügyelt PC-ket nem lehet egyéb Intune-szabályzatokkal, így a mobileszköz-felügyeletet szolgáló **Windows**-szabályzatokkal célozni.

Ha az Intune-ügyfélszoftverrel felügyel windowsos PC-ket, csak a **Számítógép-kezelés** szakaszban látható szabályzatokat használhatja.

Az Intune a Windows rendszerű számítógépek felügyeletéhez a Windows Server Active Directory tartományi szolgáltatások (AD DS) és csoportházirend-objektumok (GPO-k) által alkalmazottakhoz hasonló szabályzatokat használ. Ha Active Directory-tartományhoz csatlakoztatott számítógépeket felügyel az Intune segítségével, akkor [győződjön meg róla, hogy az Intune-szabályzatok nem ütköznek a szervezetben használt más csoportházirend-objektumokkal](resolve-gpo-and-microsoft-intune-policy-conflicts.md). További információt a [Group Policy for beginners](https://technet.microsoft.com/library/hh147307.aspx) (Csoportházirend kezdőknek) című angol nyelvű anyagban talál.

  ![Új windowsos PC-szabályzat sablonjának kiválasztása](media/select-template-for-pc-policy.png)

Az alkalmazások telepítésekor csak a Windows Installert (.exe, .msi) használhatja.

  ![Platform és hely kiválasztása a PC-s ügyfélszoftver fájljaihoz](media/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Gyakori feladatok Windows rendszerű számítógépeken

Az Intune felügyeleti konzolján más általános számítógép-felügyeleti feladatokat is elvégezhet azokon a windowsos PC-ken, amelyeken az ügyfél telepítve van:
- [A számítógépek felügyelete szabályzatok használatával egyszerűsíthető](use-policies-to-simplify-windows-pc-management.md) – Meghatározza az Intune **Számítógép felügyeleti** szabályzatait, és megadja a Microsoft Intune Center beállításait.

- [Windows rendszerű számítógépek hardver- és szoftverleltára](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) – Leírja, miként kell létrehozni egy jelentést, amely tartalmazza a számítógépek hardverképességeit, valamint a telepített szoftvereket. Azt is leírja, miként kell frissíteni a leltárt, hogy az naprakész legyen.
- [Windows rendszerű számítógép kivonása](retire-a-windows-pc-with-microsoft-intune.md) – Felsorolja a Windows rendszerű számítógép kivonásához szükséges lépéseket és leírja, mi történik ilyenkor.
- [Felhasználók és eszközök összekapcsolásának felügyelete Windows rendszerű PC-khez](manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) – Leírja, hogy a szoftver felhasználó részére történő telepítése előtt mikor és hogyan kell összekapcsolni a felhasználót a PC-vel.
- [Távsegítség kérése és nyújtása Windows rendszerű számítógépekhez](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) – Leírja, hogy miként biztosíthat távfelügyeletet az Intune-számítógépfelhasználóknak, valamint megadja a TeamViewer telepítésének előfeltételeit.

A fenti feladatokról az [általános számítógép-felügyeleti feladatokat](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) ismertető témakörben olvashat részletesebben.

## <a name="management-limitations-of-the-intune-client-software"></a>Az Intune-ügyfélszoftver felügyeleti korlátozásai

Az Intune-ügyfélszoftverrel felügyelt PC-knél nem használhat bizonyos olyan felügyeleti lehetőségeket, amelyek segítségével PC-ként kezelheti a mobileszközöket:

-   Teljes törlés (a szelektív törlés elérhető)
-   Feltételes hozzáférés

Azt is vegye figyelembe, hogy az Intune felügyeleti konzoljának bizonyos részei, mint például az **Updates** (Frissítések), a **Protection** (Védelem) és a **Licenses** (Licencek) csak akkor jelennek meg, ha vannak az Intune-ügyfélszoftverrel regisztrált eszközök.

  ![A felügyeleti konzol csak a számítógépügyfél esetén megjelenített elemei](media/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>Segítség a hibaelhárításhoz

Az Intune-ügyfélszoftver általában a háttérben fut, és csak ritkán igényel felhasználói beavatkozást vagy hibaelhárítást. Ha számítógép-felügyelettel kapcsolatos problémák megoldására van szükség, tekintse meg a naplókat. Az Intune-ügyfélszoftver és a hozzá tartozó naplók a %Program Files%\Microsoft\OnlineManagement könyvtárba vannak telepítve.

Az eszközök Microsoft Intune-ban történő beléptetéséről további információért az [eszközregisztráció](device-enrollment.md) szakaszt is áttekintheti.
