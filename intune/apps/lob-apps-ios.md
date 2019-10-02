---
title: IOS-es üzletági alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Útmutató az iOS-es üzletági (LOB) alkalmazások Microsoft Intunehoz való hozzáadásához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59cde9d38523c3683d56c54b66b563b7a95c49f9
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731115"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>IOS-es üzletági alkalmazások hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikkben található információ segítségével iOS rendszerű üzletági alkalmazást adhat hozzá a Microsoft Intune-hoz. Az üzletági (LOB) alkalmazások olyan alkalmazások, amelyeket az Intune-ban egy IPA-alkalmazás telepítési fájljában adhat hozzá. Az ilyen alkalmazásokat általában házon belül írják. Először csatlakoznia kell az iOS Developer Enterprise programhoz. Ennek módjáról további információt az [Apple webhelyén](https://developer.apple.com/programs/ios/enterprise/)talál.

>[!NOTE]
>Az iOS-eszközök felhasználói eltávolíthatnak néhányat a beépített iOS-alkalmazások közül, például a Részvények vagy a Térképek alkalmazást. Az Intune nem használható ezek újratelepítésére. Amennyiben a felhasználó törölte ezeket az alkalmazásokat, manuálisan telepítheti újra őket az App Store áruházból.
>
>az iOS LOB-alkalmazások esetében az alkalmazás legfeljebb 4 GB méretű lehet.

## <a name="step-1-specify-the-software-setup-file"></a>1\. lépés: A szoftvertelepítési fájl beállítása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** területen válassza a **Kezelés** > **Alkalmazások** elemet.
5. Az alkalmazások listája fölött válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazás hozzáadása** panelen válassza az **Üzletági alkalmazás** lehetőséget.

## <a name="step-2-configure-the-app-package-file"></a>2\. lépés: Az alkalmazáscsomag-fájl konfigurálása

1. Az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazáscsomag-fájl** lehetőséget.
2. Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ez után válasszon ki egy **.ipa** kiterjesztésű iOS-telepítőfájlt.
3. Amikor végzett, válassza az **OK** gombot.


## <a name="step-3-configure-app-information"></a>3\. lépés: Az alkalmazásadatok konfigurálása

1. Az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazásadatok** lehetőséget.
2. Az **Alkalmazás adatai** panelen adja meg az alkalmazásadatokat. A választott alkalmazástól függően előfordulhat, hogy egyes értékek automatikusan ki vannak töltve a panelen.
    - **Név**: Adja meg az alkalmazásnak a vállalati portálon megjelenő nevét. Ügyeljen arra, hogy a megadott alkalmazásnevek egyediek legyenek. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a Céges portálon.
    - **Description** (Leírás): Adja meg az alkalmazás leírását. A leírás megjelenik a Céges portálon.
    - **Közzétevő**: Itt adhatja meg az alkalmazás kiadójának nevét.
    - **Minimális operációs rendszer**: A listából válassza ki az operációs rendszer minimálisan szükséges verzióját, amelyre az alkalmazást telepíteni lehet. Ha az alkalmazást régebbi operációs rendszerrel rendelkező eszközhöz rendelik hozzá, akkor nem lesz telepítve.
    - **Kategória**: Válasszon ki egy vagy több beépített alkalmazás-kategóriát, vagy válasszon ki egy Ön által létrehozott kategóriát. A kategóriákkal megkönnyítheti a felhasználók számára az alkalmazás megkeresését a Céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: Az alkalmazás jól észrevehető módon való megjelenítése a vállalati portál fő lapján, amikor a felhasználók tallózással alkalmazásokat keresnek.
    - **Információs URL-cím**: Nem kötelező: megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Adatvédelmi URL-cím**: Nem kötelező: megadhatja az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Fejlesztő**: Igény szerint megadhatja az alkalmazás-fejlesztő nevét.
    - **Tulajdonos**: Igény szerint megadhatja az alkalmazás tulajdonosának nevét. Például **HR részleg**.
    - **Megjegyzések**: Adja meg az alkalmazáshoz hozzárendelni kívánt megjegyzéseket.
    - **Embléma**: Töltse fel az alkalmazáshoz társított ikont. Ez az ikon jelenik meg az alkalmazásnál a Céges portálon böngésző felhasználók számára.
3. Amikor végzett, válassza az **OK** gombot.

## <a name="step-4-finish-up"></a>4\. lépés: Befejezés

1. Az **Alkalmazás hozzáadása** panelen ellenőrizze, hogy helyesek-e az alkalmazáshoz megadott információk.
2. Az alkalmazást a **Hozzáadás** elem kiválasztásával töltheti fel az Intune-ba.

A létrehozott alkalmazás ekkor megjelenik az alkalmazások listájában. A listából hozzárendelheti az alkalmazást a választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

> [!NOTE]
> Az iOS üzletági (LOB) alkalmazások üzembehelyezési profiljai 30 nappal a lejáratuk előtt értesítést küldenek.

## <a name="step-5-update-a-line-of-business-app"></a>5\. lépés: Üzletági alkalmazás frissítése

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

A rendszer automatikusan telepíti az üzletági alkalmazás frissítését.

> [!NOTE]
> Ahhoz, hogy az Intune szolgáltatás sikeresen üzembe tudja helyezni az új IPA-fájlt az eszközön, az IPA-csomagban található Info.plist fájlban meg kell növelni a `CFBundleVersion` sztring értékét.

## <a name="next-steps"></a>További lépések

- A létrehozott alkalmazás megjelenik az alkalmazások listájában. Mostantól hozzárendelheti az Ön által választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

- További tájékoztató az alkalmazás jellemzőinek és hozzárendelési állapotának figyeléséről. Lásd: [Alkalmazásadatok és -hozzárendelések figyelése](apps-monitor.md).

- További tudnivalók az Intune-beli alkalmazás környezetéről. Lásd: [Az eszközök és alkalmazások életciklusának áttekintése](../fundamentals/device-lifecycle.md).
