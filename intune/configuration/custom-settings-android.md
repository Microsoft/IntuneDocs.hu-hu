---
title: Egyéni beállítások hozzáadása Android-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Egyéni profilok Android-eszközökhöz való hozzáadásával vagy létrehozásával előmegosztott kulccsal rendelkező Wi-Fi-profilt és alkalmazásonkénti VPN-profilt hozhat létre, vagy engedélyezheti és letilthatja a Samsung Knox Standard-eszközök alkalmazásait a Microsoft Intune-ban
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
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
ms.openlocfilehash: 17f0b30d0a8c706a7fdff1c7da722eeccdf097eb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495788"
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

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a profil nevét, például: `android custom profile`.
    - **Leírás:** Itt adhatja meg a profil leírását.
    - **Platform**: Válassza az **Android** lehetőséget.
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

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).

Tekintse meg, hogyan [hozhat létre profilokat Android Enterprise-eszközökön](custom-settings-android-for-work.md).
