---
title: Egyéni beállítások hozzáadása Android Enterprise-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Egyéni profilok hozzáadása vagy létrehozása Android Enterprise-eszközökhöz a Microsoft Intune-ban
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: baa202ba5fdb554af56724279456cf43961ff82d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730915"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Egyéni beállítások használata Android Enterprise-eszközökhöz a Microsoft Intune-ban

A Microsoft Intune használatával egyéni beállításokat adhat hozzá az Android Enterprise Work Profiles eszközökhöz, vagy létrehozhat egyéni profilt. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

Az Android Enterprise rendszer egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók vezérléséhez Android Enterprise-eszközökön. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik ezeket a funkciókat.

Az Intune korlátozott számú androidos vállalati egyéni profilt támogat, többek között a következőket:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: Egy [előmegosztott kulccsal rendelkező Wi-Fi-profil létrehozása](wi-fi-profile-shared-key.md) néhány példát is tartalmaz.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [Az alkalmazáson belüli VPN-profilok létrehozása](android-pulse-secure-per-app-vpn.md) néhány példát is tartalmaz.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: Tekintse meg a [példát](#example) (ebben a cikkben).

Ha további beállításokra van szüksége, tekintse meg [az OEMConfig for Android Enterprise](android-oem-configuration-overview.md)című témakört.

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt az Android Enterprise-eszközök számára. Emellett egy olyan egyéni profilra is mutat példát, amely nem engedélyezi a másolást és a beillesztést.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a profil nevét, például `android enterprise custom profile`
    - **Description** (Leírás): Adja meg a profil leírását
    - **Platform**: Az **Android Enterprise** kiválasztása
    - **Profil típusa**: **Egyéni** elem kiválasztása

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adja meg az OMA-URI beállítás egyedi nevét, így könnyen megtalálhatja.
    - **Description** (Leírás): Adjon meg egy leírást, amely áttekintést nyújt a beállításról, valamint minden egyéb fontos adatot.
    - **OMA-URI**: Adja meg a beállításként használni kívánt OMA-URI-t.
    - **Adattípus**: Válassza ki az OMA-URI beállításhoz használni kívánt adattípust. A választható lehetőségek:

      - Sztring
      - Sztring (XML-fájl)
      - Dátum és időpont
      - Egész szám
      - Lebegőpontos szám
      - Logikai
      - Base64 (fájl)

    - **Érték**: Adja meg azt az adatértéket, amelyet hozzá szeretne rendelni a megadott OMA-URI azonosítóhoz. Az érték a választott adattípustól függ. A **Dátum és idő** típus esetén például a dátumválasztóból választhat értéket.

    Néhány beállítás megadása után válassza az **Exportálás** lehetőséget. Az **Exportálás** a hozzáadott értékek listáját hozza létre egy vesszővel tagolt (.csv) fájlban.

5. Válassza ki **OK** a módosítások mentéséhez. Szükség szerint adjon hozzá további beállításokat.
6. Ha elkészült, az Intune-profil létrehozásához kattintson az **OK** > **Létrehozás** lehetőségre. Ha a profil elkészült, megjelenik az **Eszközkonfiguráció – Profilok** listában.

## <a name="example"></a>Példa

Ebben a példában egy olyan egyéni profil jön létre, amely nem engedélyezi a másolási és a beillesztési műveleteket a munkahelyi és a személyes alkalmazások között Android Enterprise-eszközökön.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a profil nevét, például `android ent block copy paste custom profile`.
    - **Description** (Leírás): Adja meg a profil leírását.
    - **Platform**: Válassza az **Android Enterprise**lehetőséget.
    - **Profil típusa**: Válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Írjon be valamit, például `Block copy and paste`.
    - **Description** (Leírás): Írjon be valamit, például `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: Adja meg a `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste` értéket.
    - **Adattípus**: Válassza a **Boolean** értéket, hogy az OMA-URI értéke **true** vagy **false**.
    - **Érték**: Válassza az **igaz**lehetőséget.

5. Miután megadta a beállításokat, a környezetének a képhez hasonlónak kell kinéznie:

    ![Tiltsa le a másolást és a beillesztést az androidos munkahelyi profilban.](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

Amikor hozzárendeli ezt a profilt az Ön által felügyelt Android Enterprise-eszközökhöz, a másolás és a beillesztés nem lesz engedélyezett a munkahelyi és a személyes profilok alkalmazásai között.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).

Tekintse meg, hogyan [hozhat létre profilokat Android-eszközökön](../custom-settings-android.md).
