---
title: Egyéni beállítások hozzáadása Android Enterprise-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Egyéni profilok hozzáadása vagy létrehozása Android Enterprise-eszközökhöz a Microsoft Intune-ban
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd2ab7ad8eb155719695bede1f539d5c264d455b
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319830"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Egyéni beállítások használata Android Enterprise-eszközökhöz a Microsoft Intune-ban

Using Microsoft Intune, you can add or create custom settings for your Android Enterprise Work Profile devices using a "custom profile". Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

Az Android Enterprise rendszer egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók vezérléséhez Android Enterprise-eszközökön. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik ezeket a funkciókat.

Intune supports the following limited number of Android Enterprise custom profiles:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [Create a Wi-Fi profile with a pre-shared key](wi-fi-profile-shared-key.md) has some examples.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [Create a per-app VPN profile](android-pulse-secure-per-app-vpn.md) has some examples.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: See the [example](#example) in this article. This setting is also available in the user interface. For more information, see [Android Enterprise device settings to allow or restrict features](device-restrictions-android-for-work.md).

If you need additional settings, see [OEMConfig for Android Enterprise](android-oem-configuration-overview.md).

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt az Android Enterprise-eszközök számára. Emellett egy olyan egyéni profilra is mutat példát, amely nem engedélyezi a másolást és a beillesztést.

## <a name="create-the-profile"></a>A profil létrehozása

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a profil nevét, például: `android enterprise custom profile`.
    - **Leírás**: Itt adhatja meg a profil leírását.
    - **Platform**: Válassza az **Android Enterprise** lehetőséget.
    - **Profil típusa**: Válassza az **Egyéni** lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adjon meg egyedi nevet az OMA-URI-beállítás számára, hogy könnyen megtalálja.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **OMA-URI**: Adja meg azt az OMA-URI azonosítót, amelyet beállításként kíván használni.
    - **Adattípus**: Adja meg azt az adattípust, amelyet az OMA-URI beállításhoz szeretne használni. A választható lehetőségek:

      - Sztring
      - Sztring (XML-fájl)
      - Dátum és időpont
      - Egész szám
      - Lebegőpontos szám
      - Logikai
      - Base64 (fájl)

    - **Érték** – Adja meg a megadott OMA-URI azonosítóhoz társítandó értéket. Az érték a választott adattípustól függ. A **Dátum és idő** típus esetén például a dátumválasztóból választhat értéket.

    Néhány beállítás megadása után válassza az **Exportálás** lehetőséget. Az **Exportálás** a hozzáadott értékek listáját hozza létre egy vesszővel tagolt (.csv) fájlban.

5. A módosítások mentéséhez válassza az **OK** gombot. Szükség szerint adjon hozzá további beállításokat.
6. Ha elkészült, az Intune-profil létrehozásához kattintson az **OK** > **Létrehozás** lehetőségre. Ha a profil elkészült, megjelenik az **Eszközkonfiguráció – Profilok** listában.

## <a name="example"></a>Példa

Ebben a példában egy olyan egyéni profil jön létre, amely nem engedélyezi a másolási és a beillesztési műveleteket a munkahelyi és a személyes alkalmazások között Android Enterprise-eszközökön.

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a profil nevét, például: `android ent block copy paste custom profile`.
    - **Leírás:** Itt adhatja meg a profil leírását.
    - **Platform**: Válassza az **Android Enterprise** lehetőséget.
    - **Profil típusa**: Válassza az **Egyéni** lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adjon meg a következőhöz hasonló nevet: `Block copy and paste`.
    - **Leírás**: Adjon meg a következőhöz hasonló leírást: `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: Írja be a következőt: `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Adattípus**: Válassza a **Logikai** lehetőséget, hogy az OMA-URI azonosító értéke **Igaz** vagy **Hamis** lehessen.
    - **Érték**: Válassza az **Igaz** lehetőséget.

5. Miután megadta a beállításokat, a környezetének a képhez hasonlónak kell kinéznie:

    ![Tiltsa le a másolást és a beillesztést az androidos munkahelyi profilban.](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

Amikor hozzárendeli ezt a profilt az Ön által felügyelt Android Enterprise-eszközökhöz, a másolás és a beillesztés nem lesz engedélyezett a munkahelyi és a személyes profilok alkalmazásai között.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).

Tekintse meg, hogyan [hozhat létre profilokat Android-eszközökön](../custom-settings-android.md).
