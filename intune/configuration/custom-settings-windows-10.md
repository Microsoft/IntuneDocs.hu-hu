---
title: Egyéni beállítások hozzáadása Windows 10-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Hozzáadhat vagy létrehozhat egy egyéni profilt, amelyet a Windows 10 rendszerű eszközök OMA-URI-beállításaihoz használhat a Microsoft Intune-ban. Egyéni beállítások hozzáadásához használjon egyéni profilt.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51ee389351dd0ccccf69f01e932f7374ca38b03b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730879"
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

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a profil nevét, például `windows 10 custom profile`.
    - **Description** (Leírás): Adja meg a profil leírását.
    - **Platform**: Válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: Válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adjon meg egy egyedi nevet az OMA-URI beállítás számára, amellyel az egyszerűen azonosítható a beállítások listájában.
    - **Description** (Leírás): Adjon meg egy leírást, amely áttekintést nyújt a beállításról, valamint minden egyéb fontos adatot.
    - **OMA-URI** (megkülönbözteti a kis-és nagybetűket): Adja meg a beállításként használni kívánt OMA-URI-t.
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

A következő példa a **Connectivity/AllowVPNOverCellular** beállítás engedélyezését mutatja be. Ez a beállítás lehetővé teszi, hogy a Windows 10-es eszköz VPN-kapcsolatot nyisson meg mobilhálózaton keresztül.

![VPN-beállításokat tartalmazó egyéni szabályzat – példa](./media/custom-settings-windows-10/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>A konfigurálható szabályzatok megkeresése

A Windows 10 által támogatott konfigurációszolgáltatók (CSP-k) teljes listájáért lásd a [konfigurációszolgáltatók referenciáját](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

Nem minden beállítás kompatibilis a Windows 10 összes verziójával. A [Konfigurációszolgáltatók referenciája](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) című témakörből megtudhatja, hogy az egyes CSP-k mely verziókat támogatják.

Az Intune nem támogatja a [konfigurációszolgáltatók referenciájában](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) felsorolt összes beállítást. Ha tudni szeretné, hogy az Intune támogatja-e a kívánt beállítást, nyissa meg a beállításhoz tartozó cikket. Minden beállítás oldalán szerepelnek az általa támogatott műveletek. Az Intune-nal való együttműködéshez a beállításnak támogatnia kell a **Hozzáadás**, a **Csere**és a **lekérés** műveletet. Ha a **Get** művelet által visszaadott érték nem egyezik a **Hozzáadás** vagy a **Csere** művelet által megadott értékkel, akkor az Intune megfelelőségi hibát jelez.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).
