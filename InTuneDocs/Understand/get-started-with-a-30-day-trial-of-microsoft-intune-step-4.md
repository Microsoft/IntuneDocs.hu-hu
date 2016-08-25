---
title: "Szabályzatok létrehozása és alkalmazások közzététele a próbaidőszak felhasználói számára | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9755499575118feecf33780ee29a70525f95508e
ms.openlocfilehash: 658806c07ea78a327819376c1b47af53ac51f0f9


---


# Szabályzatok létrehozása és alkalmazások közzététele a próbaidőszak felhasználói számára
Az Intune-szabályzatok lehetőséget biztosítanak a mobileszközök biztonsági beállításainak kezelésére, a Windows tűzfal és az Endpoint Protection szolgáltatás számítógépeken alkalmazott beállításainak karbantartására, illetve alkalmazások telepítésére. Ha azt tervezi, hogy az Intune szolgáltatást olyan eszközökön használja majd, amelyeket a próbaidőszakot követő üzemi használatra konfigurált, elengedhetetlen fontosságú, hogy kövesse [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies), illetve a [Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) című témakörben szereplő utasításokat.

Az Intune használatával az alkalmazásokat kétféle módon telepítheti. Az első egy **kötelező telepítés**, mely az adott alkalmazást automatikusan telepíti a felügyelt számítógépekre. A másik egy **elérhető telepítés**, mely telepíti az adott alkalmazást, vagy létrehoz egy hozzá kapcsolódó hivatkozást az Intune Vállalati portálon, így a felhasználók maguk dönthetik el, hogy a számítógépükre vagy a mobilkészülékükre telepítik az alkalmazást.

Az alkalmazások Intune használatával történő telepítése előtt győződjön meg róla, hogy az alkalmazás közzétételéhez, terjesztéséhez és használatához szükséges megfelelő licencekkel rendelkezik. A **Licencek** munkaterületen a Microsoft mennyiségi licencszerződéssel vásárolt és a Microsofttól származó, vagy a más módon megvásárolt és nem a Microsofttól származó alkalmazások és szoftverek licencszerződéseivel kapcsolatos adatokat veheti fel és kezelheti. Ezek segítségével olyan licencjelentéseket is létrehozhat, amelyek a kezelt licencek használati adatait a teljes vállalatra vonatkozóan megjelenítik, így naprakész információkkal rendelkezhet a licenchasználati tevékenységről.

E lépések során egy mobileszköz-konfigurációs házirendet és egy Windows számítógépes tűzfalházirendet állít be, valamint a Skype alkalmazást elérhető telepítésként konfigurálja az előzetesen regisztrált mobileszközökhöz. Az új házirend hozzáadását és telepítését követően a csoportot alkotó valamennyi – a házirend telepítésével érintett – felhasználó és eszköz számára e beállítások jelentik majd az alapvető házirendet. E házirendek részletes adatait később bármikor megtekintheti és módosíthatja a felügyeleti konzol **Házirend** munkaterületén.

## Mobileszköz-konfigurációs házirend létrehozása és alkalmazása

1.  Nyissa meg az [Intune felügyeleti konzolt](https://manage.microsoft.com/).

2.  A bal oldali ablaktáblában kattintson a **Házirend** ikonra.

3.  A **Házirendek – áttekintés** lap **Feladatok** listájában válassza a **Házirend hozzáadása** lehetőséget.

4.  A házirendlistában bontsa ki azt a platformot, amelyhez létre szeretné hozni a házirendet, válassza az **Általános konfiguráció**, majd az **Egyéni házirend létrehozása és telepítése az ajánlott beállításokkal** lehetőséget, és végül kattintson a **Házirend létrehozása** gombra.

5.  Amikor a program kéri, hogy **válassza ki, hogy mely csoportokra vonatkozóan szeretné bevezetni ezt a házirendet**, válassza a **Próbafelhasználók** csoportot a listából, és kattintson a **Hozzáadás** &gt; **OK** elemre.

A házirend ekkor megjelenik a konfigurációs házirendek listájában, és már alkalmazva van a **Próbafelhasználók** csoportra. A beállítások megtekintéséhez kattintson duplán a házirendre.

## A Skype alkalmazás mobileszközökre történő közzététele

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) kattintson az **Alkalmazások** ikonra, majd az **Alkalmazások** &gt; **Alkalmazás hozzáadása** elemre. Ha a rendszer kéri, adja meg az Intune szolgáltatásban használt hitelesítő adatait.

    > [!NOTE]
    > Az **Intune Software Publisher** első elindításakor egy kis ideig várakozni kell, amíg az alkalmazás települ.

2.  Olvassa el a biztonsági figyelmeztetést, majd válassza a **Futtatás** lehetőséget.

3.  Az **Előkészületek** lapon válassza a **Tovább** elemet.

4.  A **Szoftvertelepítés** lap **Válassza ki, hogyan legyen elérhető a szoftver az eszközök számára**beállításánál válassza a **Külső hivatkozás**lehetőséget.

5.  Az **Adja meg az URL-címet** mezőben adja meg a szoftver külső hivatkozását, majd válassza a **Tovább** elemet. Ügyeljen arra, hogy az URL-cím elé kiírja a **https://** előtagot. A Skype alkalmazás esetén az alábbi hivatkozások közül válassza az Ön által használt mobileszköz platformjának megfelelőt:

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 vagy Windows Phone 8.1:** [http://www.windowsphone.com/hu-hu/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  A **Szoftver leírása** lapon adja meg a felhasználók számára a szoftverrel kapcsolatban a Vállalati portálon megjeleníteni kívánt adatokat, majd válassza a **Tovább** elemet. A következő beállítások érhetők el (ez a példa a Skype alkalmazásra vonatkozik):

    -   **Kiadó:** Adja meg a kiadó nevét: **Microsoft**

    -   **Név:** Írja be a **Skype**

    -   **Leírás:** Adja meg a szoftver leírását, például: **Skype kommunikációs alkalmazás**

    -   **Kategória:** Válassza ki a szoftverre legjobban illő kategóriát, például: **Együttműködés**

    -   **Megjelenítés kiemelt alkalmazásként és kiemelés a vállalati portálon:** Ezzel a lehetőséggel hangsúlyosan jelenítheti meg az alkalmazást a Vállalati portálon a mobileszközökön.

    -   **Ikon:**  (Nem kötelező) Adja meg, hogy kíván-e ikont hozzárendelni a szoftverhez. Az ikon mérete legfeljebb 250 x 250 képpont lehet, a javasolt ikonméret azonban 32 x 32 képpont.

7.  Az **Összefoglalás** lapon ellenőrizze a szoftver adatait, majd válassza a **Feltöltés** lehetőséget. Kattintson a **Bezárás** gombra a varázslóból való kilépéshez.

8.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) kattintson az **Alkalmazások** &gt; **Alkalmazások** &gt; **Skype** &gt; **Üzembe helyezés kezelése** elemre.

9. A **Csoportok kiválasztása** lapon válassza a **Próbafelhasználók** csoportot, hogy a szoftver telepítése ebben a felhasználói csoportban történjen, majd kattintson a **Hozzáadás** &gt; **Tovább** elemre.

10. A **Telepítési művelet** lapon válassza a **Telepíthető** lehetőséget a csoport **Jóváhagyás** oszlopában.

11. Válassza a **Befejezés** lehetőséget.

Most már a Vállalati portálon keresztül telepítheti a Skype alkalmazást a mobileszközökre, ehhez azonban először a számítógépekre és a mobileszközökre kell telepítenie az Intune alkalmazást.

### További lépések
Gratulálunk! Befejezte a *Microsoft Intune próbaverzió* útmutatójának 4. lépését.

>[!div class="step-by-step"]

>[&larr; **Eszközcsoportok létrehozása**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)     [**Eszközök regisztrálása** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md)  



<!--HONumber=Jun16_HO4-->


