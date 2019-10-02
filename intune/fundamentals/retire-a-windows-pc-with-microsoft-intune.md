---
title: Windows rendszerű számítógépek kivonása
titleSuffix: Microsoft Intune
description: Az Intune által felügyelt Windows rendszerű számítógépek kivonása.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: f41194f7a0f8de9fd1a0d6803ad63a2f253b89bf
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729491"
---
# <a name="retire-a-windows-pc"></a>Windows rendszerű számítógépek kivonása

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

A következő lépésekkel kivonhatja az Intune-szoftverügyféllel számítógépként felügyelt számítógépeket. Ha kivonja a számítógépet, a rendszer eltávolítja azt az Intune-alapú felügyeletből. Az Intune-ból nem tudja törölni egy számítógép összes adatát az eredeti gyári beállítások visszaállításához.

1. A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza a kivonni kívánt a számítógépet).

2. Jelölje ki a kivonni kívánt eszközöket, majd válassza a **Kivonás/Összes adat törlése** elemet.

Ha a számítógépet újból regisztrálni szeretné az Intune-ban, telepítse újra az szoftverügyfelet a számítógépen [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](../install-the-windows-pc-client-with-microsoft-intune.md) című témakörben található információk segítségével.

Ha a számítógép nem tud csatlakozni az Intune-hoz, egy üzenet jelenik meg az **Irányítópult** munkaterületen.

A számítógép kivonásakor:

- A rendszer eltávolítja az Intune-felügyeletből és -leltárból, és a számítógéphez társított licenc ismét felhasználhatóvá válik. Ha a Kivonás/Összes adat törlése elemre kattint, a rendszer eltávolítja az Intune-szoftverügyfelet, de az alkalmazások és az adatok megmaradnak a számítógépen. A kivonás nem hajt végre teljes törlést a számítógépen.

- Az állapota már nem jelenik meg az Intune-konzolon.

- Az Intune eltávolítja az szoftverügyfelet a számítógépről. Ha a számítógép nincs csatlakoztatva az Intune szolgáltatáshoz, a rendszer a számítógép következő csatlakozásakor távolítja el a szoftverügyfelet.

- Megtörténik a Microsoft Intune Endpoint Protection eltávolítása a számítógépről. Ha a számítógépen telepítve van egy másik végponti alkalmazás, és le van tiltva, akkor az alkalmazás a Microsoft Intune Endpoint Protection eltávolítása után újból engedélyezhető a számítógép védelmének biztosításához.

- A rendszer eltávolít minden szabályzatot a számítógépről, és módosulnak a szabályzatok által beállított értékek.

- A számítógép többé nem kap szoftver- vagy a kártevődefiníció-frissítéseket az Intune szolgáltatástól.

- Konfigurációjuktól függően az kivont számítógépek a Windows Server Update Services, a Windows Update vagy a Microsoft Update használatával továbbra is kaphatnak frissítéseket.

    > [!IMPORTANT]
    > Ha az ügyfélszoftver egy csoportházirend-objektummal (GPO) lett telepítve, akkor az ügyfélszoftver eltávolítása előtt el kell távolítania a csoportházirend-objektumot (GPO), hogy megakadályozza a szoftver újratelepítését.

    Ha az Endpoint Protection-ügyfél eltávolítása nem sikerült, további segítséget itt találhat: [Az Endpoint Protection hibáinak elhárítása](/intune/troubleshoot-endpoint-protection-in-microsoft-intune).

## <a name="see-also"></a>Lásd még:

[A Windows rendszerű számítógépek Intune-szoftverügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
