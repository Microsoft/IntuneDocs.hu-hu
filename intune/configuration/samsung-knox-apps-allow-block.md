---
title: Microsoft Intune-szabályzat alkalmazások engedélyezésére és letiltására Samsung Knox-eszközökön
titleSuffix: ''
description: Egyéni profil létrehozása alkalmazások engedélyezéséhez és letiltásához Samsung Knox Standard-eszközökön.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207077"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Alkalmazások engedélyezése és letiltása egyéni szabályzattal Samsung Knox Standard-eszközökön a Microsoft Intune-ban 

Ennek a cikknek az eljárásaival elkészíthet egy egyéni Microsoft Intune-szabályzatot, amellyel az alábbiak egyikét hozhatja létre:

- Az eszközön nem futtatható alkalmazások listája. A listában szereplő alkalmazások le lesznek tiltva, és nem futtathatóak még akkor sem, ha a szabályzat létrehozása előtt lettek telepítve.
- Azon alkalmazások listája, amelyek telepítése engedélyezett az eszköz felhasználói számára a Google Play áruházból. Csak a listán szereplő alkalmazások telepíthetők. Az áruházból más alkalmazások nem telepíthetők.

Ezek a beállítások kizárólag a Samsung Knox Standard rendszerű eszközökön használhatók.

## <a name="create-an-allowed-or-blocked-app-list"></a>Az engedélyezett vagy tiltott alkalmazások listájának létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. A jó profilnév például a **Windows Phone egyéni profilja**.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **Platform**: válassza az **Android**lehetőséget.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    Az eszközön nem futtatható alkalmazások listájához:

    - **Név**: adja meg a **következőt: preventstartpackages**.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést nyújt az adott beállításról, valamint más olyan releváns információkat tartalmaz, amelyek segítenek a profil megkeresésében. Adja meg például a **futtatásra blokkolt alkalmazások listáját**.
    - **OMA-URI** (megkülönbözteti a kis-és nagybetűket): írja be a **./vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**.
    - **Adattípus**: válassza a **karakterlánc**lehetőséget.
    - **Érték**: adja meg az engedélyezni kívánt alkalmazáscsomag-nevek listáját. A `;`, a `:`vagy a `|` elválasztóként használható. Például írja be a következőt: `package1;package2;`.

   Azon alkalmazások listájához, amelyek telepítése engedélyezett a felhasználók számára a Google Play áruházból, miközben minden más alkalmazás le van tiltva:

    - **Név**: adja meg a **következőt: allowinstallpackages**.
    - **Leírás**: adjon meg egy leírást, amely áttekintést nyújt a beállításról, valamint a profil megkeresését segítő egyéb releváns információkat. Adja meg például a **felhasználók által a Google Play áruházból telepíthető alkalmazások listáját**.
    - **OMA-URI** (megkülönbözteti a kis-és nagybetűket): írja be a **./vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**.
    - **Adattípus**: válassza a **karakterlánc**lehetőséget.
    - **Érték**: adja meg az engedélyezni kívánt alkalmazáscsomag-nevek listáját. A `;`, a `:`vagy a `|` elválasztóként használható. Például írja be a következőt: `package1;package2;`.

5. A módosítások mentéséhez válassza az **OK** gombot.
6. Ha elkészült, válassza az **OK** > **Létrehozás** lehetőséget az Intune-profil létrehozásához. Ha elkészült, a profil megjelenik az **eszközök – konfigurációs profilok** listában.

>[!TIP]
> Az alkalmazás csomagazonosítóját úgy tudja megtalálni, hogy a Google Play áruházban megkeresi az alkalmazás oldalát. A csomagazonosítót az alkalmazáscsomag URL-címe tartalmazza. Például a Microsoft Word alkalmazás azonosítója **com.microsoft.office.word**.

Amikor a rendszer a következő alkalommal ellenőrzi, hogy minden megcélozt eszköz bejelentkezik-e, alkalmazza az alkalmazás beállításait.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).
