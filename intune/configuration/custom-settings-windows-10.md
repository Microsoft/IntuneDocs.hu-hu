---
title: Egyéni beállítások hozzáadása Windows 10-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Hozzáadhat vagy létrehozhat egy egyéni profilt, amelyet a Windows 10 rendszerű eszközök OMA-URI-beállításaihoz használhat a Microsoft Intune-ban. Egyéni beállítások hozzáadásához használjon egyéni profilt.
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
ms.openlocfilehash: 9e3d2784e0242498fbae43ab61034a5be31b0952
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206771"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Egyéni beállítások használata Windows 10 rendszerű eszközökhöz az Intune-ban

A Microsoft Intune-nal egyéni beállításokat adhat hozzá vagy hozhat létre a Windows 10-eszközökhöz „egyéni profilok” használatával. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

A Windows 10 egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók konfigurálásához. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik az eszközök funkcióit. 

A Windows 10 számos konfigurációszolgáltatói beállítást tesz elérhetővé, ilyen például a [Szabályzat-konfigurációszolgáltató (Policy Configuration Service Provider, Policy CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Ha egy adott beállítást keres, ne feledje, hogy a [Windows 10 eszközkorlátozási profil](device-restrictions-windows-10.md) számos beépített beállítást tartalmaz. Így nem feltétlenül kell egyéni értékeket megadnia.

Ez a cikk:

- bemutatja, hogyan hozhat létre egyéni profilokat Windows 10-eszközökhöz;
- tartalmazza a javasolt OMA-URI-beállítások listáját;
- példaként bemutat egy egyéni profilt, amely megnyit egy VPN-kapcsolatot.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profilnév például a **Windows 10 egyéni profilja**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név** – Adjon meg egy egyedi nevet az OMA-URI-beállítás számára, amellyel az egyszerűen azonosítható a beállítások listájában.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **OMA-URI** (megkülönbözteti a kis- és nagybetűket) – Adja meg azt az OMA-URI azonosítót, amelyet beállításként kíván használni.
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

A következő példa a **Connectivity/AllowVPNOverCellular** beállítás engedélyezését mutatja be. Ez a beállítás lehetővé teszi, hogy a Windows 10-es eszköz VPN-kapcsolatot nyisson meg mobilhálózaton keresztül.

![VPN-beállításokat tartalmazó egyéni szabályzat – példa](./media/custom-settings-windows-10/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>A konfigurálható szabályzatok megkeresése

A Windows 10 által támogatott konfigurációszolgáltatók (CSP-k) teljes listájáért lásd a [konfigurációszolgáltatók referenciáját](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

Nem minden beállítás kompatibilis a Windows 10 összes verziójával. A [Konfigurációszolgáltatók referenciája](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) című témakörből megtudhatja, hogy az egyes CSP-k mely verziókat támogatják.

Az Intune nem támogatja a [konfigurációszolgáltatók referenciájában](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) felsorolt összes beállítást. Ha tudni szeretné, hogy az Intune támogatja-e a kívánt beállítást, nyissa meg a beállításhoz tartozó cikket. Minden beállítás oldalán szerepelnek az általa támogatott műveletek. Az Intune-nal való együttműködéshez a beállításnak támogatnia kell a **Hozzáadás**, a **Csere**és a **lekérés** műveletet. Ha a **Get** művelet által visszaadott érték nem egyezik a **Hozzáadás** vagy a **Csere** művelet által megadott értékkel, akkor az Intune megfelelőségi hibát jelez.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).
