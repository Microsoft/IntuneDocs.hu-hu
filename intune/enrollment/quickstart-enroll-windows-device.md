---
title: 'Rövid útmutató: Windows 10 rendszerű asztali eszköz regisztrálása a Microsoft Intune-ban'
description: 'Rövid útmutató: A Céges portál használata Windows 10 rendszerű asztali eszköz regisztrálása a Microsoft Intune-ban.'
services: microsoft-intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/30/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91f20411f668428c8bf3af8b0bd4ae6f4b0b545f
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713514"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>Rövid útmutató: Windows 10 rendszerű eszköz regisztrálása

Ebben a rövid útmutatóban először Intune-felhasználói szerepkörben fog tevékenykedni, és regisztrálja a Windows 10 rendszerű eszközét a Microsoft Intune-ban. Ezután térjen vissza az Intune-hoz, és erősítse meg az eszköz regisztrálását.

A vállalati eszközök Microsoft Intune-beli regisztrálása lehetővé teszi, hogy a Windows 10 rendszerű eszközök hozzáférjenek a szervezet védett adataihoz, beleértve az e-maileket, a fájlokat és az egyéb erőforrásokat. Ez a Windows 10 rendszerű asztali számítógépekre és a Windows 10 Mobile rendszerű eszközökre egyaránt vonatkozik. Az eszközök regisztrálásával biztonságossá tehető ez a hozzáférés Ön és a szervezet számára, és elkülöníthetők a munkahelyi adatok a személyes adatoktól.

> [!TIP]
> Tekintse át, hogy mi történik, amikor [regisztrálja az eszközét az Intune-ban](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows), és mit jelent ez az [eszközön található adatok szempontjából](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune).

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Microsoft Intune-előfizetés – [regisztráljon egy ingyenes próbafiókkal](../fundamentals/free-trial-sign-up.md)
- A rövid útmutató követéséhez, végezze el a lépéseket az [automatikus regisztráció beállításához az Intune-ban](quickstart-setup-auto-enrollment.md).

## <a name="confirm-your-windows-10-desktop-version"></a>A Windows 10 asztali verzió megerősítése

A Windows 10 asztali verzió regisztrációja előtt erősítse meg a Windows telepített verzióját.

1. Kattintson a jobb gombbal a Windows **Start** ikonjára, majd válassza a **Gépház** lehetőséget a Windows Gépház megjelenítéséhez.

   ![A Windows Gépház képernyőképe – rendszer](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. Válassza a **Rendszer** > **Névjegy** lehetőséget. 

   ![Képernyőkép a rendszer beállításairól](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > Be is írhatja „a gép névjegye” kifejezést a **keresősávba**, majd válassza **A gép névjegye** lehetőséget.

3. A **Gépház** ablakban megjelenik egy, a **Windows-specifikációkat** tartalmazó lista a számítógéphez. A listában keresse meg a **Verzió** bejegyzést.

4. Ellenőrizze, hogy a Windows 10-es **verzió** **1607-es vagy újabb-e**.

    > [!IMPORTANT]
    > Az ebben a rövid útmutatóban bemutatott lépések a **1607-es vagy újabb** Windows 10-verzióra vonatkoznak, ha a verzió **1511-es vagy régebbi**, folytassa [ezekkel a lépésekkel](/intune-user-help/enroll-windows-10-device).  

## <a name="enroll-windows-10-desktop"></a>A Windows 10 asztali verzió regisztrálása

1. Térjen vissza a Windows Gépházba, és válassza a **Fiókok** lehetőséget.

   ![Képernyőkép a rendszer beállításairól – Fiókok](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. Válassza a **Hozzáférés munkahelyi vagy iskolai rendszerhez** > **Csatlakozás** elemet.

    ![Válassza a Hozzáférés munkahelyi vagy iskolai fiókhoz lehetőséget](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. Jelentkezzen be az Intune-ba munkahelyi vagy iskolai fiókjával, majd válassza a **Tovább** lehetőséget. Ha követte a [felhasználó létrehozása és a licencek kiosztása](../fundamentals/quickstart-create-user.md) című útmutatót, akkor bejelentkezhet a létrehozott felhasználói fiókkal.

    > [!NOTE]
    > Ha az „.onmicrosoft.com” címet álltja be, a felhasználói fiókban az **.onmicrosoft.com** a fiók címének része lesz. 

   ![Adja meg a munkahelyi vagy iskolai fiókját](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    Ekkor megjelenik egy üzenet arról, hogy a munkahely vagy iskola regisztrálja az eszközt.

4. Amikor megjelenik a **Készen vagyunk!** képernyő, válassza a **Kész** elemet. Ezzel készen is van.

5. Ekkor megjelenik az új fiók a **Hozzáférés munkahelyi vagy iskolai rendszerhez** beállítások részeként a Windows asztali verzióban.

   ![Képernyőkép az újonnan hozzáadott fiókról](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    Ha követte a fenti lépéseket, de továbbra sem tud hozzáférni munkahelyi vagy iskolai e-mail fiókjához és fájljaihoz, kövesse a [Hibaelhárítási teendők, ha ezt látja: Hozzáférés munkahelyi vagy iskolai rendszerhez](/intune-user-help/troubleshoot-your-windows-10-device-windows#troubleshooting-steps-to-follow-if-you-see-access-work-or-school) című részben leírt lépéseket.

## <a name="confirm-your-device-enrollment-in-intune"></a>Eszközök regisztrációjának megerősítése az Intune-ban

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként.
2. Válassza az **eszközök** > **minden eszköz** lehetőséget a regisztrált eszközök Intune-ban való megtekintéséhez.
3. Ellenőrizze, hogy rendelkezik-e további regisztrált eszközökkel az Intune-ban.

   ![Képernyőkép az Intune-ban regisztrált eszközökről](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

A Windows-eszköz regisztrációjának törléséhez tekintse meg a [Windows-eszköz eltávolítása a felügyelet alól](/intune-user-help/unenroll-your-device-from-intune-windows) szakaszt.

## <a name="next-steps"></a>További lépések

Ebből a rövid útmutatóból elsajátíthatta, hogyan regisztrálhat Windows 10-es eszközt az Intune-ban. Megismerkedhet az eszközregisztráció más módjaival is, bármely platformon. Az eszközök Intune-nal való használatáról további információért olvassa el a [Felügyelt eszközök használata a munkavégzéshez](/intune-user-help/use-managed-devices-to-get-work-done) szakaszt.

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Kötelező jelszóhossz beállítása Android-eszközökhöz](../quickstart-set-password-length-android.md)
