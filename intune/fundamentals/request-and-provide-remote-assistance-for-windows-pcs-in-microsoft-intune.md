---
title: Távsegítség kérése és nyújtása Windows rendszerű számítógépekhez
titleSuffix: Microsoft Intune
description: Végfelhasználói és rendszergazdai lépések a PC-ként felügyelt Windows rendszerű számítógépek távsegítségéhez és a számítógépek távolról indításához.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26df7250aefa519c20708879b68af7c35113814f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509855"
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Távsegítség kérése és nyújtása Windows rendszerű számítógépekhez

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Az ebben a témakörben ismertetett információk csak az Intune-szoftverügyféllel PC-ként felügyelt Windows-számítógépekre vonatkoznak.

Az Intune a külön megvásárolható [TeamViewer](https://www.teamviewer.com) szoftver segítségével képes lehetővé tenni, hogy távsegítséget nyújtson az Intune-szoftverügyfelet futtató felhasználóinak. Önt riasztás értesíti róla, ha egy felhasználó segítséget kér a Microsoft Intune Centeren keresztül. Ekkor elfogadhatja a kérést, és biztosíthatja a szükséges támogatást. Ez a funkció az Intune jelenlegi Windows Távsegítség szolgáltatását cseréli le.


## <a name="before-you-start"></a>Előkészületek

Ahhoz, hogy a távsegítség funkcióval támogatást biztosíthasson az azt kérő felhasználóknak, teljesítenie kell a következő előfeltételeket:

- [Regisztrálnia kell egy TeamViewer-fiókot](https://login.teamviewer.com/LogOn#register), hogy be tudjon jelentkezni a TeamViewer weboldalára.
- A kezelni kívánt Windows-számítógépeket [a Windows rendszerű szoftverügyfélnek kell felügyelnie](../manage-windows-pcs-with-microsoft-intune.md)
- Az Intune által támogatott bármely számítógépes Windows operációs rendszer támogatható.

## <a name="configure-the-teamviewer-connector"></a>A TeamViewer-összekötő konfigurálása

1. A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com) válassza a **Felügyelet** elemet.
2. A **Felügyelet** munkaterületen válassza a **TeamViewer** lehetőséget.
3. A **TeamViewer** oldal **TeamViewer-összekötő** részénél válassza az **Engedélyezés** lehetőséget.
4. **A TeamViewer engedélyezése** párbeszédpanelen olvassa el, majd az **Elfogadás** gombra kattintva fogadja el a licencfeltételeket. Ha még nem rendelkezik TeamViewer-licenccel, kattintson a **TeamViewer-licenc vásárlása** elemre.
5. Megnyílik a TeamViewer böngészőablaka. Jelentkezzen be az oldalra a TeamViewerhez kapott hitelesítő adataival.
6. A TeamViewer oldalán olvassa el, majd fogadja el a beállításokat, amelyek lehetővé teszik az Intune és a TeamViewer összekapcsolását.
7. Az Intune-konzolban ellenőrizze, hogy a **TeamViewer-összekötő** beállítás értéke a következő-e: **Engedélyezve**.


## <a name="open-a-remote-assistance-request-end-user"></a>Végfelhasználói távsegítségkérés benyújtása

1. A Windows rendszerű ügyfélszámítógépen nyissa meg a **Microsoft Intune Centert**.
2. A **Távsegítség** menüben válassza a **Távsegítség kérése** lehetőséget.
3. A kérés jóváhagyását követően (lásd alább) az ügyfél megnyitja a TeamViewert. A felhasználónak jóvá kell hagynia az esetleg megjelenő üzeneteket, amelyek arról tájékoztatják, hogy a böngésző meg szeretné nyitni a TeamViewer alkalmazást.
4. A felhasználónál megjelenik egy üzenet, amely megkérdezi, hogy szeretné-e engedélyezni, hogy Ön átvegye az irányítást a számítógép felett. A folytatáshoz meg kell adni az engedélyt.
5. A távsegítség-munkamenet során a felhasználót egy ablak tájékoztatja arról, hogy Ön csatlakozik hozzá. Az ablak bezárása esetén a távoli munkamenet is lezárul.

## <a name="respond-to-a-remote-assistance-request"></a>Válasz távsegítségre vonatkozó kérésre

1. A felhasználók által benyújtott távsegítségkéréseket a **Riasztások** munkaterület **Figyelés** > **Távsegítség** menüjében tekintheti meg. Példa:
   > ![Távsegítségkérést bemutató képernyőkép](./media/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune/team-viewer.png)

<br>Azokat a kéréseket, amelyekre 4 órán át nem érkezik válasz, a rendszer eltávolítja.
2. A kérés elfogadásához kattintson **A kérelem jóváhagyása és a Távsegítség alkalmazás elindítása** elemre.
3. A **Függőben van egy új távsegítség-kérés** párbeszédpanelen válassza **A távsegítségkérés elfogadása** lehetőséget. Ha még nincs telepítve a számítógépre a TeamViewer a további szükséges alkalmazásokkal együtt, megtörténik a telepítés.
4. A TeamViewer ezt követően tájékoztatja a végfelhasználót, hogy Ön szeretné átvenni az irányítást a számítógép felett. Ha a felhasználó megadja az engedélyt, megnyílik a TeamViewer ablaka, és Ön megkezdheti a felhasználó számítógépének kezelését.

A távsegítség-munkamenet ideje alatt a TeamViewer összes rendelkezésre álló parancsa használható a távoli számítógép vezérlésére. A parancsokkal kapcsolatban a TeamViewer webhelyén található [Manual for remote control](http://www.teamviewer.com/en/support/documents/) (Távvezérlési kézikönyv) dokumentumban talál további információkat.

## <a name="close-the-remote-assistance-session"></a>A távsegítség-munkamenet lezárása

A **TeamViewer** ablakának **Műveletek** menüjében válassza a **Munkamenet vége** lehetőséget.

## <a name="remotely-restart-a-windows-pc"></a>Windows rendszerű számítógépek távoli újraindítása
Amikor hibák megoldásán dolgozik, elképzelhető, hogy időről időre távolról kell újraindítania ügyfelei számítógépét. Kövesse az alábbi lépéseket a Windows rendszerű számítógépek távoli újraindításához.

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza azt a számítógépet, amelyet újra szeretne indítani).

2. Jelöljön ki egy vagy több számítógépet, majd válassza a **Távoli feladatok** &gt; **Számítógép újraindítása** elemet.

3. A feladat állapotának megtekintéséhez válassza a lap jobb alsó sarkában található **Távoli feladatok** elemet.

4. A **Feladat állapota** párbeszédpanelen áttekintheti az aktuális távoli feladatokat, a feladatok állapotát, az eszköz nevét és minden jelentett hibát.

## <a name="see-also"></a>További információ

[A Windows rendszerű számítógépek Intune-szoftverügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
