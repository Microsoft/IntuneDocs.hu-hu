---
title: Az S mód frissítése vagy használata Windows 10-es eszközökön – Microsoft Intune – Azure | Microsoft Docs
description: A Microsoft Intune használatával frissítse a Windows 10-es eszközöket egy másik kiadásra, vagy váltson az S üzemmódra. A rendszergazdák az eszköz konfigurációs profiljának használatával frissíthetik a Windows 10 Professional rendszert a Windows 10 Enterprise rendszerre, és kikapcsolhatják az S üzemmódot. Tekintse meg a Windows 10 Pro, N Edition, Education, Cloud, Enterprise, Core, holografikus és Mobile támogatott frissítési útvonalait.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3595e75a73868378c9c366de6c751c21a9151ae3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059519"
---
# <a name="upgrade-windows-10-editions-or-switch-out-of-s-mode-on-devices-using-microsoft-intune"></a>A Windows 10 kiadások frissítése vagy az eszközökön való kikapcsolás Microsoft Intune használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A mobileszköz-kezelési (MDM) megoldás részeként érdemes lehet frissíteni a Windows 10-es eszközöket. Például a Windows 10 Professional rendszerű eszközöket szeretné frissíteni Windows 10 Enterprise-ra. Vagy ha azt szeretné, hogy az eszköz kikapcsolja az S üzemmódot.

A [Windows 10 S üzemmód](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) (egy másik Microsoft-webhely megnyitása) a biztonság és a teljesítmény érdekében készült. Az Intune használatával kikapcsolhatja az S üzemmódot. Az S módból való váltás nem vonható vissza. Ha vált az S módból, nem válthat vissza később.

Tekintse meg az S móddal kapcsolatos [gyakran ismételt kérdéseket](https://support.microsoft.com/help/4020089/windows-10-in-s-mode-faq) .

Ez a funkció az alábbiakra vonatkozik:

- Windows 10 és újabb
- Windows 10 1809 vagy újabb az S mód esetében
- Windows Holographic for Business

Ezek a funkciók az Intune-ban érhetők el, és a rendszergazda konfigurálható. Az Intune a "konfigurációs profilok" használatával hozza létre és szabja testre ezeket a beállításokat a szervezet igényeinek megfelelően. Miután hozzáadta ezeket a szolgáltatásokat egy profilhoz, leküldheti vagy üzembe helyezheti a profilt a szervezet Windows 10-es eszközein. A profil központi telepítésekor az Intune automatikusan frissíti az eszközöket, vagy kikapcsolja az S üzemmódot.

Ez a cikk a támogatott frissítési útvonalakat sorolja fel, és bemutatja, hogyan hozhatja létre az eszköz konfigurációs profilját. Megtekintheti a [Windows 10](edition-upgrade-windows-settings.md)összes elérhető frissítési és S módú beállítását is.

> [!NOTE]
> Ha később eltávolítja a szabályzat-hozzárendelést, az eszközön lévő Windows-verzió nem áll vissza. Az eszköz továbbra is szabályosan fut.

## <a name="prerequisites"></a>Előfeltételek

Az eszközök frissítése előtt győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:

- Érvényes termékkulcs a frissített Windows-verzió telepítéséhez a szabályzat céljaként meghatározott eszközökön (Windows 10 asztali verziók esetén). Többször használható aktiválási kulcsokat (MAK) vagy kulcskezelő kiszolgálói (KMS) kulcsokat használhat.
- A Windows 10 Mobile és a Windows 10 holografikus kiadásaihoz Microsoft-licencfájl is használható. A licencfájl tartalmazza azokat a licencelési adatokat, amelyek a frissített kiadás telepítéséhez szükségesek a szabályzattal megcélzott összes eszközön.
- Már regisztrálva vannak a Microsoft Intune-ban azok a Windows 10 rendszerű eszközök, amelyekhez hozzárendeli a szabályzatot. A kiadásfrissítési szabályzat nem használható az Intune PC-ügyfélszoftvert futtató számítógépekkel.

## <a name="supported-upgrade-paths"></a>Támogatott frissítési útvonalak

A Windows 10-kiadás frissítési profiljának támogatott frissítési útvonalai az alábbi táblázatban tekinthetők meg.

| Frissítés erről a kiadásról | Frissítés erre a kiadásra |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Windows 10 Pro N kiadás | Windows 10 Education N kiadás <br/>Windows 10 Enterprise N kiadás <br/>Windows 10 Pro Education N kiadás | 
| Windows 10 Pro Education | Windows 10 Education | 
| Windows 10 Pro Education N kiadás | Windows 10 Education N kiadás |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Windows 10 Cloud N kiadás | Windows 10 Education N kiadás <br/>Windows 10 Enterprise N kiadás <br/>Windows 10 Pro N kiadás <br/>Windows 10 Pro Education N kiadás | 
| Windows 10 Enterprise | Windows 10 Education | 
| Windows 10 Enterprise N kiadás | Windows 10 Education N kiadás | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Windows 10 Core N kiadás | Windows 10 Education N kiadás <br/>Windows 10 Enterprise N kiadás <br/>Windows 10 Pro Education N kiadás | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 mobil verzió | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)  (X) = not supported    
![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Mobile|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Holographic|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png) -->

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adja meg az új profil leíró nevét. Írja be például a következőt: `Windows 10 edition upgrade profile` vagy `Windows 10 switch off S mode`.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: válassza a **kiadás frissítése**lehetőséget.
    - **Beállítások**: adja meg a konfigurálni kívánt beállításokat. Az összes beállítás listáját és a teendőket lásd:

        - [Windows 10 frissítési és S üzemmód](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a listában. Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

## <a name="next-steps"></a>További lépések

A profil létrehozása után készen áll a hozzárendelésre. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Megtekintheti a [Windows 10](edition-upgrade-windows-settings.md) és a [Windows holografikus for Business](holographic-upgrade.md) rendszerű eszközök frissítési és S üzemmódjának beállításait.
