---
title: Windows 10 rendszerű virtuális gépek használata Microsoft Intune
titleSuffix: ''
description: Irányelvek a Windows 10 rendszerű virtuális gépek használatáról Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afaf2c8a63bfaed1fdb593baf42c8fa258d7893
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74266335"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>Windows 10 rendszerű virtuális gépek használata az Intune-nal

Az Intune bizonyos korlátozásokkal támogatja a Windows 10 Enterprise rendszert futtató virtuális gépek felügyeletét. Az Intune-felügyelet nem függ attól, hogy az azonos virtuális gép Windows rendszerű virtuális asztali felügyeletét nem befolyásolja-e.

Windows 10 rendszerű virtuális gépek Intune-nal való kezelésekor tartsa szem előtt a következő szempontokat:

## <a name="enrollment"></a>Beléptetés
- Az Intune-nal nem ajánlott az igény szerinti, a munkamenet-állomást futtató virtuális gépek kezelése. Minden virtuális gépet regisztrálni kell a létrehozásakor. Emellett a virtuális gépek rendszeres törlésével a rendszer törli az árva eszközöket az Intune-ban mindaddig, amíg meg nem [tisztítják](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules)őket. 
- A Windows Autopilot önálló üzembe helyezési módja nem támogatott, mert platformmegbízhatósági modult (TPM) igényel. 
- A kezdőélmény (OOBE) beléptetése nem támogatott olyan virtuális gépeken, amelyek csak RDP használatával érhetők el (például az Azure-ban üzemeltetett virtuális gépeken). Ez a korlátozás a következőket jelenti:
    - A Windows Autopilot és a kereskedelmi OOBE nem támogatott.
    - A regisztrációs állapot lapja nem támogatott az eszköz-környezeti házirendek esetében.

## <a name="configuration"></a>Konfiguráció
Az Intune nem támogat olyan konfigurációt, amely platformmegbízhatósági modul vagy hardveres kezelést használ, beleértve a következőket:
- [BitLocker-beállítások](../configuration/device-profiles.md#endpoint-protection)
- [Eszköz belső vezérlőprogram konfigurációs felületének beállításai](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>Jelentéskészítés
Az Intune automatikusan észleli a virtuális gépeket, és azokat "virtuális gép"ként jelenti az **eszközökön** > **minden eszközön** > válasszon egy eszközt > **Áttekintés** > **Model** mező. 

A felszabadított virtuális gépek hozzájárulhatnak a nem megfelelő eszközök jelentéseihez, mert nem tudnak [bejelentkezni az Intune szolgáltatásba](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retirement"></a>Kivonás
Ha csak RDP-hozzáféréssel rendelkezik, ne használja a [Törlés műveletet](../remote-actions/devices-wipe.md#wipe). A törlés művelettel törölheti a virtuális gép RDP-beállításait, és megakadályozhatja, hogy a rendszer soha ne csatlakozzon újra.


