---
title: "Szabályzatok létrehozása és alkalmazások közzététele | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2847c9af38ae0ddddc8d76d548ae7abddc63e4c1
ms.openlocfilehash: b3b65a1fd1e426bf566f39382321a29e913f102c


---

# Házirendek létrehozása és alkalmazások közzététele
Az Intune-szabályzatok lehetőséget biztosítanak a mobileszközök biztonsági beállításainak kezelésére, a Windows tűzfal és az Endpoint Protection szolgáltatás számítógépeken alkalmazott beállításainak karbantartására, illetve alkalmazások telepítésére. További információkért olvassa el [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies), illetve a [Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) című témaköröket.

Az Intune használatával az alkalmazásokat kétféle módon telepítheti. Az első egy **kötelező telepítés**, mely az adott alkalmazást automatikusan telepíti a felügyelt számítógépekre. A másik egy **elérhető telepítés**, mely telepíti az adott alkalmazást, vagy létrehoz egy hozzá kapcsolódó hivatkozást az Intune Vállalati portálon, így a felhasználók maguk dönthetik el, hogy a számítógépükre vagy a mobilkészülékükre telepítik az alkalmazást.

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

Az alábbi lépések segítségével egy mobileszköz-konfigurációs szabályzatot és egy Windows-alapú számítógépes tűzfalházirendet állíthat be, valamint a Skype alkalmazást elérhető telepítésként konfigurálhatja az előzetesen regisztrált mobileszközökhöz.

> [!TIP]
> Az új házirend hozzáadását és telepítését követően a csoportot alkotó valamennyi – a házirend telepítésével érintett – felhasználó és eszköz számára e beállítások jelentik majd az alapvető házirendet. A házirendek részletes adatainak megtekintése és szerkesztése később a Házirend munkaterületen bármikor elérhető.


## Mobileszköz-konfigurációs házirend létrehozása és alkalmazása

1.  Nyissa meg az [Intune felügyeleti konzolt](https://manage.microsoft.com/).

2.  A bal oldali ablaktáblában kattintson a **Házirend** ikonra.

    ![admin-console-policy-workspace](./media/policy.png)

3.  A **Házirendek – áttekintés** lap **Feladatok** listájában válassza a **Házirend hozzáadása** lehetőséget.

4.  A szabályzatok listájában bontsa ki azt a platformot, amelyre a létrehozandó szabályzat vonatkozni fog, ezt követően válassza az **Általános konfiguráció** > **Egyéni házirend létrehozása és telepítése az ajánlott beállításokkal** > **Házirend létrehozása** lehetőséget.

5.  Ha a rendszer a **Válassza ki, hogy mely csoportokra vonatkozóan szeretné bevezetni ezt a házirendet** üzenetben felszólítja erre, a rendelkezésre álló csoportok listájából válasszon ki egy csoportot, majd kattintson a **Hozzáadás** > **OK** gombra.

A szabályzat ekkor megjelenik a konfigurációs szabályzatok listájában, és már alkalmazva van az **Intune-felhasználók** csoportra. A beállítások megtekintéséhez kattintson duplán a házirendre.

## A Skype alkalmazás mobileszközökre történő közzététele

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) kattintson az **Alkalmazások** ikonra, majd az **Alkalmazások** > **Alkalmazás hozzáadása** elemre. Ha a rendszer kéri, adja meg az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] szolgáltatásban használt hitelesítő adatait.

    ![admin-console-apps-workspace](./media/apps.png)

    > [!NOTE]
    > Az **Intune Software Publisher** első elindításakor egy kis ideig várakozni kell, amíg az alkalmazás települ.

2.  Olvassa el a biztonsági figyelmeztetést, majd válassza a **Futtatás** lehetőséget.

3.  Az **Előkészületek** lapon válassza a **Tovább** elemet.

4.  A **Szoftver telepítése** lap **Válassza ki, hogyan szeretné elérhetővé tenni ezt a szoftvert az eszközök számára** beállításánál válassza a **Külső hivatkozás** lehetőséget.

5.  Az **Adja meg az URL-címet** mezőben adja meg a szoftver külső hivatkozását, majd válassza a **Tovább** elemet. Ügyeljen arra, hogy az URL-cím elé kiírja a **http://** előtagot. A Skype alkalmazás esetén az alábbi hivatkozások közül válassza az Ön által használt mobileszköz platformjának megfelelőt:

    -   **iOS:**   [https://itunes.apple.com/hu/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:**  [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 vagy Windows Phone 8.1:**  [http://www.windowsphone.com/hu-hu/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  A **Szoftver leírása** lapon adja meg a felhasználók számára a szoftverrel kapcsolatban a Vállalati portálon megjeleníteni kívánt adatokat, majd válassza a **Tovább** elemet. A következő beállítások érhetők el (ez a példa a Skype alkalmazásra vonatkozik):

    -   **Kiadó:** Adja meg a kiadó nevét: „Microsoft”

    -   **Név:** Írja be a **Skype**

    -   **Leírás:** Adja meg a szoftver leírását, például: **Skype kommunikációs alkalmazás**

    -   **Kategória:** Válassza ki a szoftverre legjobban illő kategóriát, például: **Együttműködés**

    -   **Megjelenítés kiemelt alkalmazásként és kiemelés a vállalati portálon:** Ezzel a lehetőséggel hangsúlyosan jelenítheti meg az alkalmazást a Vállalati portálon a mobileszközökön.

    -   **Ikon:** Adja meg, hogy kíván-e ikont hozzárendelni a szoftverhez. A választható ikon maximális mérete 250 x 250 képpont, az ajánlott mérete 32 x 32 képpont.

7.  Az **Összefoglalás** lapon ellenőrizze a szoftver adatait, majd válassza a **Feltöltés** lehetőséget. Kattintson a **Bezárás** gombra a varázslóból való kilépéshez.

8.  Az [Intune felügyeleti konzoljában](https://manage.microsoft.com/) válassza az **Alkalmazások** > **Alkalmazások** > **Skype** > **Központi telepítés kezelése** lehetőséget.

9. A **Csoportok kiválasztása** lapon válassza az **Intune-felhasználók** csoportot, hogy a szoftver telepítése ebben a felhasználói csoportban történjen, majd válassza a **Hozzáadás** > **Tovább** elemet.

10. A **Telepítési művelet** lapon válassza a **Telepíthető** lehetőséget a csoport **Jóváhagyás** oszlopában.

11. Válassza a **Befejezés** lehetőséget.

A továbbiakban a Vállalati portálon keresztül telepítheti a Skype alkalmazást a mobileszközökre, ehhez azonban először a számítógépekre és a mobileszközökre telepítenie kell az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] alkalmazást.


### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések útmutató* 6. lépését.

>[!div class="step-by-step"]

>[&larr; **Felhasználók és eszközök rendszerezése**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**A Vállalati portál testreszabása** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  



<!--HONumber=Jun16_HO4-->


