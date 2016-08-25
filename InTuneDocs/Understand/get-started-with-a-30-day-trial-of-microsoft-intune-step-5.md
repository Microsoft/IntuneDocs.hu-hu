---
title: "A próbaidőszak alatt használt mobileszközök regisztrálása | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9755499575118feecf33780ee29a70525f95508e
ms.openlocfilehash: f26b64015f483eb5b6a6efbaa6fe6730dde7dac9


---

# A próbaidőszak alatt használt mobileszközök regisztrálása és alkalmazások telepítése
Az Intune szolgáltatással történő mobileszköz-kezelés beállításához először mobileszköz-kezelő szolgáltatót kell beállítani, engedélyezni kell a mobileszköz-kezelést az eszközplatformhoz, majd regisztrálni kell az eszközöket a Vállalati portál alkalmazással. Ezután telepítheti a közzétett Microsoft Skype alkalmazást.

## A szolgáltatás előkészítése az eszközkezeléshez

1.  **Az Intune beállítása mobileszköz-kezelő szolgáltatóként**

    Az [Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Felügyelet** &gt; **Mobileszköz-kezelés** elemre. Válassza a **Feladatok** > **MDM-szolgáltató megadása** lehetőséget, majd az **MDM-szolgáltató** párbeszédpanelen kattintson az **Igen** gombra.

2.  **Mobileszköz-kezelés engedélyezése az eszközplatformhoz**

    A mobileszköz-kezelés engedélyezése a kezelni kívánt eszközplatform esetén. A követelmények a platformtól függően eltérőek:

    -   **iOS és Mac OS X**: lásd az [iOS- és Mac-eszközök kezelésének beállítása a Microsoft Intune-ban](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune) című témakört.

    -   **Android**: Az Android rendszerű mobileszközök lehetővé teszik, hogy a felhasználók a Google Play áruházban elérhető Vállalati portál alkalmazással regisztráljanak. Így nincs szükség további Intune konfigurációra.

    -   **Windows Phone**: lásd a [Windows Phone-telefonok Microsoft Intune-beli kezelésének beállítása](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune) című témakört.

## Teszteszközök regisztrálása

### iOS és Mac OS X
Telepítse a Microsoft Corporation által kiadott **Microsoft Intune Vállalati portál** alkalmazást, amelyet az App Store áruházban érhet el, és jelentkezzen be az Intune korábban ismertetett módon hozzáadott hitelesítő adataival. Az eszköz felvételéhez tekintse át a **Regisztrált eszközök** listát.

### Android
Telepítse a Microsoft Corporation által kiadott **Intune Vállalati portál** alkalmazást, melyet a [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) Áruházban érhet el, és jelentkezzen be az Intune szolgáltatás fent megadott hitelesítő adataival.

### Windows Phone 8.1
Telepítse a Microsoft Corporation által kiadott **Vállalati portál** alkalmazást, melyet a Windows Phone Áruházban érhet el, és jelentkezzen be az Intune szolgáltatás fent megadott hitelesítő adataival.  Az eszköz felvételéhez tekintse át a **Regisztrált eszközök** listát.

 ### Windows Phone 8.0
 A felhasználóknak a **Rendszerbeállítások** &gt; **Vállalati alkalmazások** lehetőségre kell kattintaniuk, és be kell jelentkezniük az Intune-hoz a fent megadott felhasználói hitelesítő adatokkal. A Vállalati portál alkalmazás telepítve van a telefonjára.

Ha a program a **kiszolgáló címét**kéri, írja be a manage.microsoft.com címet.


## A korábban telepített alkalmazások telepítése
Nyissa meg a Vállalati portált a mobileszközön, majd válassza az **Alkalmazások** lehetőséget, és telepítse a **Microsoft Skype** alkalmazást.

A mobileszközök Intune használatával történő kezelésével kapcsolatosan bővebb információk a [Felkészülés az eszközök regisztrálására a Microsoft Intune-ban](/Intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) című témakörben olvashatók.

### További lépések
Gratulálunk! Befejezte a *Microsoft Intune próbaverzió* útmutatójának 5. lépését.

>[!div class="step-by-step"]

>[&larr; **Házirendek létrehozása**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)     [**Beállítások és kiegészítő funkciók** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)  



<!--HONumber=Jun16_HO4-->


