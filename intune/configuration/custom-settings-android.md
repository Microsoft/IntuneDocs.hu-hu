---
title: Egyéni beállítások hozzáadása Android-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Egyéni profilok Android-eszközökhöz való hozzáadásával vagy létrehozásával előmegosztott kulccsal rendelkező Wi-Fi-profilt és alkalmazásonkénti VPN-profilt hozhat létre, vagy engedélyezheti és letilthatja a Samsung Knox Standard-eszközök alkalmazásait a Microsoft Intune-ban
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
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8137a806598facd540781702b1c2c359e89d6bda
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206788"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>Egyéni beállítások használata Android-eszközökhöz a Microsoft Intune-ban

A Microsoft Intune-nal egyéni beállításokat adhat hozzá vagy hozhat létre az Android-eszközökhöz „egyéni profilok” használatával. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

Az Android rendszer egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók konfigurálásához Android-eszközökön. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik ezeket a funkciókat.

Egyéni profillal a következő Android-beállításokat konfigurálhatja és rendelheti hozzá. A következő beállítások nem érhetők el beépítetten az Intune-ban:

- [Wi-Fi-profil létrehozása előmegosztott kulccsal](/intune/wi-fi-profile-shared-key)
- [Alkalmazásonkénti VPN-profil létrehozása](/intune/android-pulse-secure-per-app-vpn)
- [Alkalmazások engedélyezése és letiltása Samsung Knox Standard-eszközökön](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Az egyéni profilokban csak a felsorolt beállítások konfigurálhatók. Az Android-eszközök nem teszik elérhetővé a konfigurálható OMA-URI-beállítások teljes listáját. Ha több beállítást szeretne látni, szavazzon rájuk az [Intune Uservoice webhelyén](https://microsoftintune.uservoice.com/forums/291681-ideas).

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt az Android-eszközök számára.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profil neve például az **Android egyéni profil**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza az **Android**lehetőséget.
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

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Hozzon létre egy [egyéni profilt az Android Enterprise rendszerű eszközökön](custom-settings-android-for-work.md).
