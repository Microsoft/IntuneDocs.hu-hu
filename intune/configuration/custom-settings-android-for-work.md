---
title: Egyéni beállítások hozzáadása Android Enterprise-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Egyéni profilok hozzáadása vagy létrehozása Android Enterprise-eszközökhöz a Microsoft Intune-ban
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
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
ms.openlocfilehash: 1bd6e2d5ceebd23e87f464d15376594d1764c5b8
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206805"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Egyéni beállítások használata Android Enterprise-eszközökhöz a Microsoft Intune-ban

A Microsoft Intune használatával egyéni beállításokat adhat hozzá az Android Enterprise Work Profiles eszközökhöz, vagy létrehozhat egyéni profilt. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

Az Android Enterprise rendszer egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók vezérléséhez Android Enterprise-eszközökön. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik ezeket a funkciókat.

Az Intune a következő korlátozott számú androidos vállalati egyéni profilt támogatja:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [egy előmegosztott kulccsal rendelkező Wi-Fi-profil létrehozása](wi-fi-profile-shared-key.md) néhány példát is tartalmaz.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [hozzon létre egy alkalmazáson belüli VPN-profilt](android-pulse-secure-per-app-vpn.md) néhány példát.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: Tekintse meg a jelen cikkben szereplő [példát](#example) . Ez a beállítás a felhasználói felületen is elérhető. További információ: [androidos vállalati eszközbeállítások a funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md).

Ha további beállításokra van szüksége, tekintse meg [az OEMConfig for Android Enterprise](android-oem-configuration-overview.md)című témakört.

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt az Android Enterprise-eszközök számára. Emellett egy olyan egyéni profilra is mutat példát, amely nem engedélyezi a másolást és a beillesztést.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profilnév például az **Android Enterprise egyéni profil**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza az **Android Enterprise**lehetőséget.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adjon meg egyedi nevet az OMA-URI-beállítás számára, hogy könnyen megtalálja.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **OMA-URI**: Adja meg azt az OMA-URI azonosítót, amelyet beállításként kíván használni.
    - **Adattípus**: válassza ki az OMA-URI beállításhoz használni kívánt adattípust. A választható lehetőségek:

      - Sztring
      - Sztring (XML-fájl)
      - Dátum és időpont
      - Egész szám
      - Lebegőpontos szám
      - Logikai
      - Base64 (fájl)

    - **Érték** – Adja meg a megadott OMA-URI azonosítóhoz társítandó értéket. Az érték a választott adattípustól függ. Ha például a **dátum és idő**lehetőséget választja, válassza ki a kívánt értéket a dátumválasztó listából.

    Néhány beállítás megadása után válassza az **Exportálás** lehetőséget. Az **Exportálás** a hozzáadott értékek listáját hozza létre egy vesszővel tagolt (.csv) fájlban.

5. A módosítások mentéséhez válassza az **OK** gombot. Szükség szerint adjon hozzá további beállításokat.
6. Ha elkészült, válassza az **OK** > **Létrehozás** lehetőséget az Intune-profil létrehozásához. Ha elkészült, a profil megjelenik az **eszközök – konfigurációs profilok** listában.

## <a name="example"></a>Példa

Ebben a példában egy olyan egyéni profil jön létre, amely nem engedélyezi a másolási és a beillesztési műveleteket a munkahelyi és a személyes alkalmazások között Android Enterprise-eszközökön.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Adja meg például az **Android ENT blokk másolás egyéni profil beillesztése**funkciót.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza az **Android Enterprise**lehetőséget.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adjon meg a következőhöz hasonló nevet: `Block copy and paste`.
    - **Leírás**: Adjon meg a következőhöz hasonló leírást: `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: Írja be a következőt: `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Adattípus**: válassza a **Boolean** értéket, hogy az OMA-URI értéke **true** vagy **false**.
    - **Érték**: válassza az **igaz**értéket.

5. Miután megadta a beállításokat, a környezetének a képhez hasonlónak kell kinéznie:

    ![Tiltsa le a másolást és a beillesztést az androidos munkahelyi profilban.](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

Amikor hozzárendeli ezt a profilt az Ön által felügyelt Android Enterprise-eszközökhöz, a másolás és a beillesztés nem lesz engedélyezett a munkahelyi és a személyes profilok alkalmazásai között.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Hozzon létre egy [egyéni profilt az Android-eszközökön](../custom-settings-android.md).
