---
title: Egyéni beállítások hozzáadása Windows Phone 8.1 rendszerű eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Hozzáadhat vagy létrehozhat egy egyéni profilt, amelyet a Windows Phone 8.1 rendszerű eszközök OMA-URI-beállításaihoz használhat a Microsoft Intune-ban.
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
ms.openlocfilehash: 6ed1f43e7c7e6f0580cb22513a489fb32c30e5f6
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206754"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Egyéni beállítások használata Windows Phone 8.1 rendszerű eszközökhöz az Intune-ban

A Microsoft Intune-nal egyéni beállításokat adhat hozzá vagy hozhat létre a Windows Phone 8.1 rendszerű eszközökhöz „egyéni profilok” használatával. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

A Windows Phone 8.1 egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók konfigurálásához. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik az eszközök funkcióit. [Windows Phone-telefon 8,1 Mdm protokoll dokumentációja](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) felsorolja a beállításokat.

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt Windows Phone 8.1 rendszerű eszközökhöz. 

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. A jó profilnév például a **Windows Phone egyéni profilja**.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **Platform**: válassza a **Windows Phone-telefon 8,1**lehetőséget.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név** – Adjon meg egy egyedi nevet az OMA-URI-beállítás számára, amellyel az egyszerűen azonosítható a beállítások listájában.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést nyújt az adott beállításról, valamint más olyan releváns információkat tartalmaz, amelyek segítenek a profil megkeresésében.
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

A következő példában a Windows 8,1 Phone rendszerű eszközök nem módosíthatják a mobil hálózatokat a szolgáltatói lefedettségi területen kívülre való utazáskor.

- **Név**: mobil adatroaming engedélyezése
- **Leírás**: a mobil adatroaming engedélyezése vagy letiltása
- **OMA-URI** (megkülönbözteti a kis-és nagybetűket):./vendor/MSFT/PolicyManager/My/connectivity/AllowCellularDataRoaming
- **Adattípus**: egész szám
- **Érték**: 0

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Hozzon létre egy [egyéni profilt a Windows 10-es eszközökön](../custom-settings-windows-10.md).
