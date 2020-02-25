---
title: A Microsoft Defender ATP hozzáadása macOS-eszközökhöz Microsoft Intune használatával
titleSuffix: ''
description: Ismerje meg, hogyan adhat hozzá Microsoft Defender ATP-t macOS-eszközökhöz Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569904"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>A Microsoft Defender ATP hozzáadása macOS-eszközökhöz Microsoft Intune használatával

Az alkalmazások üzembe helyezése, konfigurálása, monitorozása vagy védelemmel való ellátása előtt hozzá kell adnia őket az Intune-hoz. Az elérhető [alkalmazások](~/apps/apps-add.md#app-types-in-microsoft-intune) egyike a Microsoft Defender komplex veszélyforrások elleni védelem (ATP). Ha ezt az alkalmazást az Intune-ban kiválasztja, a Microsoft Defender ATP-t hozzárendelheti és telepítheti a macOS-t futtató felügyelt eszközökre. Az alkalmazás típusa megkönnyíti a Microsoft Defender ATP a macOS-eszközökhöz való hozzárendelését anélkül, hogy a macOS-alkalmazás burkoló eszközét kellene használnia. Az alkalmazások biztonságosabbá és naprakészen tartása érdekében az alkalmazás a Microsoft AutoUpdate (MAU) szolgáltatáshoz tartozik.

## <a name="prerequisites"></a>Előfeltételek
- A macOS-eszköznek macOS 10,13 vagy újabb rendszert kell futtatnia.
- A macOS-eszköznek legalább 650 MB szabad lemezterülettel kell rendelkeznie.
- Kernel-bővítmény üzembe helyezése az Intune-ban. További információ: [MacOS kernel-bővítmények hozzáadása az Intune-ban](~/configuration/kernel-extensions-overview-macos.md).

> [!IMPORTANT]
> A kernel-bővítményt csak akkor lehet automatikusan jóváhagyni, ha az eszközön megtalálható a Microsoft Defender ATP-alkalmazás telepítése előtt. Másik lehetőségként a felhasználók a "rendszerkiterjesztés letiltott" üzenetet fogják látni a Mac számítógépen, és a **biztonsági beállítások** vagy a **Rendszerbeállítások** > a **biztonsági & adatvédelmet** , majd az **Engedélyezés**lehetőséget választva jóvá kell hagynia a bővítményt. További információ: a [kernel-bővítmény hibáinak elhárítása a Microsoft DEFENDER ATP for Mac szolgáltatásban](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext).

## <a name="add-microsoft-defender-atp-to-intune"></a>A Microsoft Defender ATP hozzáadása az Intune-hoz
A Microsoft Defender ATP-t az alábbi lépésekkel adhatja hozzá az Intune-hoz:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusa** listán a **Microsoft Defender ATP**alatt válassza a **MacOS**lehetőséget.

## <a name="configure-app-information"></a>Az alkalmazásadatok konfigurálása
Ebben a lépésben az alkalmazás telepítésével kapcsolatos információkat nyújt. Ez az információ segít azonosítani az alkalmazást az Intune-ban, és segít a felhasználóknak megkeresni az alkalmazást a vállalati portálon.

1. Az **alkalmazásadatok ablaktábla** megjelenítéséhez kattintson az **alkalmazás adatai** elemre.
2. Az **alkalmazás adatai** panelen megadhatja az alkalmazás telepítésével kapcsolatos információkat. Ez az információ segít azonosítani az alkalmazást az Intune-ban, és segít a felhasználóknak megkeresni az alkalmazást a vállalati portálon.
    - **Név**: Itt adhatja meg az alkalmazásnak a vállalati portálon megjelenő nevét. Ügyeljen arra, hogy minden név egyedi legyen. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. Megadhatja például, hogy a leírásban megjelenő felhasználók is fel legyenek listázva.
    - **Közzétevő:** Közzétevőként a Microsoft jelenik meg.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ez a beállítás megkönnyíti a felhasználók számára az alkalmazás megkeresését a vállalati portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: válassza ezt a lehetőséget, ha a felhasználók tallózásával szeretné megjeleníteni az alkalmazást a vállalati portál főoldalán.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő:** Fejlesztőként a Microsoft jelenik meg.
    - **Tulajdonos:** Tulajdonosként a Microsoft jelenik meg.
    - **Megjegyzések:**: Ide írhatja be igény szerint az alkalmazáshoz társítani kívánt megjegyzéseket.
3. Válassza az **OK** gombot.

## <a name="select-scope-tags-optional"></a>Hatóköri címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez.
1.  Válassza a **hatókör (címkék)** > **Hozzáadás**elemet.
2.  A **Select (kijelölés** ) mező használatával keresheti meg a hatókör címkéit.
3.  Jelölje be a jelölőnégyzetet az alkalmazáshoz hozzárendelni kívánt hatókör-címkék mellett.
4.  Kattintson a **kijelölés** > **OK gombra**.

## <a name="add-the-app"></a>Az alkalmazás felvétele
Ha végzett a konfigurálással, válassza a **Hozzáadás** lehetőséget az **alkalmazás-alkalmazás** ablaktáblán. 

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

> [!NOTE]
> Az Apple jelenleg nem biztosítja a Microsoft Defender ATP macOS-eszközökön való eltávolításának módját az Intune számára.

## <a name="next-steps"></a>További lépések
- A Microsoft Defender ATP macOS-eszközökön való konfigurálásával kapcsolatos további információkért lásd: [a Microsoft DEFENDER ATP konfigurálása MacOS-eszközökön](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences).
- Felhasználói csoportok esetében az alkalmazás-hozzárendelések belefoglalásáról és kizárásáról az [Alkalmazás-hozzárendelések belefoglalása vagy kizárása](~/apps/apps-inc-exl-assignments.md) című témakörben talál további információkat.
- [Alkalmazások hozzárendelése csoportokhoz](~/apps/apps-deploy.md)

