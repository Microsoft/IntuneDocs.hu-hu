---
title: Egyéni beállítások hozzáadása Windows Phone 8.1 rendszerű eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Hozzáadhat vagy létrehozhat egy egyéni profilt, amelyet a Windows Phone 8.1 rendszerű eszközök OMA-URI-beállításaihoz használhat a Microsoft Intune-ban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6807caad60eb492324f37e0c406b44a4052589e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730851"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Egyéni beállítások használata Windows Phone 8.1 rendszerű eszközökhöz az Intune-ban

A Microsoft Intune-nal egyéni beállításokat adhat hozzá vagy hozhat létre a Windows Phone 8.1 rendszerű eszközökhöz „egyéni profilok” használatával. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

A Windows Phone 8.1 egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók konfigurálásához. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik az eszközök funkcióit. [Windows Phone-telefon 8,1 Mdm protokoll dokumentációja](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) felsorolja a beállításokat.

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt Windows Phone 8.1 rendszerű eszközökhöz. 

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a profil nevét, például `windows phone custom profile`.
    - **Description** (Leírás): Adja meg a profil leírását.
    - **Platform**: Válassza a **Windows Phone-telefon 8,1**lehetőséget.
    - **Profil típusa**: Válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adjon meg egy egyedi nevet az OMA-URI beállítás számára, amellyel az egyszerűen azonosítható a beállítások listájában.
    - **Description** (Leírás): Adjon meg egy leírást, amely áttekintést nyújt a beállításról, valamint a profil megkeresését segítő egyéb releváns információkat.
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

A következő példában a Windows 8,1 Phone rendszerű eszközök nem módosíthatják a mobil hálózatokat, ha a szolgáltató lefedettségi területén kívül utaznak.

- **Név**: Mobil adatroaming engedélyezése
- **Description** (Leírás): A mobil adatroaming engedélyezése vagy letiltása
- **OMA-URI** (megkülönbözteti a kis-és nagybetűket):./vendor/MSFT/PolicyManager/My/connectivity/AllowCellularDataRoaming
- **Adattípus**: Integer
- **Érték**: 0

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).

Tekintse meg, hogyan hozhat létre egyéni profilt [Windows 10 rendszerű eszközökön](../custom-settings-windows-10.md).
