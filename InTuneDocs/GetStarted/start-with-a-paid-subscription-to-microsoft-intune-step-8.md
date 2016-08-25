---
title: "Mobileszközök regisztrálása és alkalmazások telepítése| Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6cb729533107d511fa0cc863ec6ab842e7624982
ms.openlocfilehash: 78cf5472a6069e09b5072253635066d95094a89e


---

# Mobileszközök regisztrálása és alkalmazások telepítése
Az Intune szolgáltatással történő mobileszköz-kezelés beállításához először meg kell adnia a mobileszközt kezelő szolgáltatót, engedélyeznie kell a mobileszköz-kezelést az eszközplatformhoz, majd regisztrálnia kell az eszközöket a Vállalati portál alkalmazásban. Ezután telepítheti a 6. lépésben közzétett Microsoft Skype alkalmazást.

## Eszközkezelés engedélyezése és eszközök regisztrálása

1.  **Az Intune beállítása mobileszköz-kezelő szolgáltatóként** Az [Intune felügyeleti konzoljában](https://manage.microsoft.com/) válassza a **Felügyelet** > **Mobileszköz-kezelés** elemet, majd kattintson a **Feladatok** csoport **Mobileszköz-kezelő szolgáltató megadása** elemére.  Kattintson a Mobileszköz-kezelő szolgáltató párbeszédpanel **Igen** gombjára.
    ![Felügyeleti konzol. Mobileszköz-kezelés beállítása az Intune-hoz](./media/mdmAuthority.png)

2.  **Mobileszköz-kezelés engedélyezése az eszközplatformhoz** A mobileszköz-kezelés engedélyezése a kezelni kívánt eszközplatform esetében. A követelmények a platformtól függően eltérőek:

    -   **iOS és Mac OS X**: lásd az [iOS- és Mac-eszközök kezelésének beállítása a Microsoft Intune-ban](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) című témakört.

    -   **Windows Phone**: lásd a [Windows Phone-telefonok Microsoft Intune-beli kezelésének beállítása](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) című témakört.

    -   **Android**: A felhasználók a [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider) Áruházból letölthető Vállalati portál alkalmazással regisztrálhatják androidos mobileszközeiket. Így nincs szükség további Intune konfigurációra.

3.  **Eszközök regisztrálása**:

    -   **Android** – Telepítse a Microsoft Corporation által kiadott **Intune Vállalati portál** alkalmazást, melyet a [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) áruházban érhet el, és jelentkezzen be az Intune szolgáltatás fent megadott hitelesítő adataival.

    -   **iOS és Mac OS X** – Telepítse a Microsoft Corporation által kiadott **Microsoft Intune Vállalati portál** alkalmazást, melyet az App Store áruházban érhet el, és jelentkezzen be az Intune fent megadott hitelesítő adataival. Az eszköz felvételéhez tekintse át a **Regisztrált eszközök** listát.

    -   **Windows Phone 8.1** – Telepítse a Microsoft Corporation által kiadott **Vállalati portál** alkalmazást, melyet a Windows Phone Áruházban érhet el, és jelentkezzen be az Intune szolgáltatás fent megadott hitelesítő adataival.  Az eszköz felvételéhez tekintse át a **Regisztrált eszközök** listát.

    -   **Windows Phone 8.0** – A felhasználóknak a **Rendszerbeállítások** &gt; **Vállalati alkalmazások** lehetőségre kell kattintaniuk, és be kell jelentkezniük az Intune-hoz fent megadott felhasználói hitelesítő adatokkal. A Vállalati portál alkalmazás telepítve van a telefonjára.

    Ha a program a **kiszolgáló címét**kéri, írja be a manage.microsoft.com címet.

## Alkalmazás telepítése egy regisztrált eszközre
Az első lépéseket ismertető jelen útmutató [6. lépésében](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) közzétette a Skype alkalmazást a saját Intune-felhasználók csoportja számára. Most ezt az alkalmazást egy újonnan regisztrált eszközre fogja telepíteni.

Nyissa meg a Vállalati portált a regisztrált mobileszközön, majd válassza az **Alkalmazások** lehetőséget, és telepítse a **Microsoft Skype** alkalmazást.

A mobileszközök [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-nal történő kezelésével kapcsolatban további információk a [Felkészülés az eszközök regisztrálására a Microsoft Intune-ban](/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) című témakörben olvashatók.


### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések útmutatójának* utolsó lépését. Most, hogy a kezdeti konfigurálást befejezte, további MDM-funkciók engedélyezését is fontolóra veheti.

>[!div class="step-by-step"]

>[&larr; **Eszközök regisztrálása**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Konfigurációt követő feladatok** &rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Jun16_HO4-->


