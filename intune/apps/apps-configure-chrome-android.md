---
title: A Google Chrome beállítása Android-eszközökhöz az Intune használatával
titleSuffix: Microsoft Intune
description: Intune-os konfigurációs szabályzatok használata Android-eszközökhöz készült Google Chrome-nal.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35f52e80f83426c076ac7925d308daacf4595f88
ms.sourcegitcommit: b1e97211db7cb949eb39be6776b3a11d434fdab0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251508"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>A Google Chrome beállítása Android-eszközökhöz az Intune használatával 

A Google Chrome Android-eszközökhöz való konfigurálásához Intune-alkalmazás-konfigurációs szabályzatot is használhat. Az alkalmazás beállításai automatikusan alkalmazhatók. Megadhatja például a könyvjelzőket és a blokkolni vagy engedélyezni kívánt URL-címeket.

## <a name="prerequisites"></a>Előfeltételek

- A felhasználó androidos vállalati eszközét regisztrálni kell az Intune-ban. További információ: [az Android Enterprise Work profiling-eszközök regisztrációjának beállítása](~/enrollment/android-work-profile-enroll.md).
- A Google Chrome felügyelt Google Play-alkalmazásként lett hozzáadva. A felügyelt Google Play szolgáltatással kapcsolatos további információkért lásd: [az Intune-fiók összekötése a felügyelt Google Play-fiókkal](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>A Google Chrome alkalmazás hozzáadása az Intune-hoz

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Az **Intune** panelen válassza az **ügyfélalkalmazások**@no__t – 2**alkalmazások**@no__t – 4**Hozzáadás** elemet, majd adja hozzá a **felügyelt Google Play** alkalmazást.
3. Lépjen a felügyelt Google Play áruházba, keresse meg a **Google Chrome** -t, és hagyja jóvá.

    ![Google Chrome keresése és jóváhagyása](~/apps/media/apps-configure-chrome-android/search.png)

4. Rendelje hozzá a Google Chrome-t egy felhasználói csoporthoz kötelező alkalmazás típusaként. A Google Chrome automatikusan települ, amikor az eszköz regisztrálva van az Intune-ban.

A felügyelt Google Play-alkalmazások Intune-hoz való hozzáadásával kapcsolatos további információkért lásd: [felügyelt Google Play áruházbeli alkalmazások](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-an-app-configuration-policy-for-managed-android-enterprise-devices"></a>Alkalmazás-konfigurációs szabályzat hozzáadása a felügyelt Android Enterprise-eszközökhöz

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) panelen válassza az **alkalmazás-konfigurációs házirendek** > **Hozzáadás**lehetőséget.
2. Adja hozzá a szabályzat nevét, válassza a **felügyelt eszközök** lehetőséget az eszköz regisztrálása alatt **, a platform alatt.**

    ![Google Chrome konfigurációs szabályzat hozzáadása](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Kattintson a **társított alkalmazás** lehetőségre, és válassza a **Google Chrome**lehetőséget.

    ![Válassza a Google Chrome lehetőséget a társított alkalmazás alatt](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Kattintson a **konfigurációs beállítások**elemre, válassza a **Configuration Designer használata**lehetőséget, majd kattintson a **Hozzáadás** gombra a konfigurációs kulcsok kiválasztásához.

    ![A use Configuration Designer hozzáadása](~/apps/media/apps-configure-chrome-android/configuration.png)

    Alább látható az általános beállítások példája:
    - **URL-címek listájához való hozzáférés letiltása**: `["*"]`
    - **URL-címek listájához való hozzáférés engedélyezése**: `["baidu.com", "yahoo.com", "chrome://*"]`
    - **Felügyelt könyvjelzők**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Incognito mód elérhetősége**: `Incognito mode disabled`

    Miután hozzáadta a konfigurációs beállításokat a Configuration Designer használatával, a rendszer egy táblázatban sorolja fel őket. 

    ![Általános beállítások](~/apps/media/apps-configure-chrome-android/common-settings.png)

    A fenti beállítások könyvjelzőket hoznak létre, és engedélyezik a hozzáférést az összes webhelyhez, kivéve `baidu.com`, `yahoo.com` és `chrome://`.

5. Kattintson **az OK gombra** , és adja hozzá a konfigurációs szabályzatot az Intune **-hoz.**
6. Rendelje hozzá ezt a konfigurációs szabályzatot egy felhasználói csoporthoz. További információ: [alkalmazások társítása csoportokhoz Microsoft Intune használatával](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Eszköz beállításainak ellenőrzése

Ha az androidos eszköz regisztrálva van az Android Enterprise-ban, a rendszer automatikusan telepíti a felügyelt Google Chrome-alkalmazást a portfólió ikonnal.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Indítsa el a Google Chrome-t, és megtalálja az alkalmazott beállításokat.

   Könyvjelzők<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   Blokkolt URL-cím:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   URL-cím engedélyezése:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Inkognitóban lap:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Hibakeresés

1. Az Intune-portálon ellenőrizheti a szabályzat központi telepítésének állapotát.

    ![A házirend központi telepítési állapotának figyelése](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Indítsa el a Google Chrome-ot, és keresse fel a **Chrome://Policy** Ellenőrizheti, hogy a beállítások alkalmazása sikeres volt-e.

    ![A beállítások jóváhagyása sikeresen megtörtént](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>További információk

- [Alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt Android Enterprise-eszközökhöz](~/app-configuration-policies-use-android.md)
- [Chrome vállalati szabályzatok listája](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Következő lépések

- Az Android Enterprise teljes körűen felügyelt eszközökkel kapcsolatos további információkért lásd: [az Android Enterprise Intune-regisztrációjának beállítása teljes mértékben](~/enrollment/android-fully-managed-enroll.md)felügyelt eszközök.
