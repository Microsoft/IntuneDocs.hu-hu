---
title: A Windows 10 kézbesítési optimalizálási beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Annak konfigurálása, hogy az Intune-nal felügyelt Windows 10-es eszközök hogyan használják a kézbesítési optimalizálást. Az Intune-ban hozzon létre egy eszköz-konfigurációs profilt a frissítések internetről történő telepítéséhez. Azt is megtudhatja, hogyan lehet lecserélni a meglévő frissítési gyűrűket egy kézbesítési optimalizálási profillal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124809"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Kézbesítési optimalizálási beállítások a Microsoft Intune

Az Intune-nal a Windows 10-es eszközök kézbesítési optimalizálási beállításainak használatával csökkentheti a sávszélesség-használatot, amikor az eszközök letöltik az alkalmazásokat és a frissítéseket. Konfigurálja a kézbesítési optimalizálást az eszköz konfigurációs profiljainak részeként.  

Ez a cikk bemutatja, hogyan konfigurálhatja a kézbesítés optimalizálási beállításait az eszköz konfigurációs profiljának részeként. Miután létrehozta a profilt, a profilt hozzárendelheti vagy üzembe helyezheti a Windows 10-es eszközökön. 

Az Intune által támogatott kézbesítési optimalizálási beállítások listájának megtekintéséhez lásd: az [Intune kézbesítési optimalizálási beállításai](../delivery-optimization-settings.md).  

Ha többet szeretne megtudni a Windows 10-es továbbítási optimalizálásáról, tekintse meg a Windows dokumentációjának [kézbesítési optimalizálási frissítései](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) című témakört.  

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

3. Adja meg a következő tulajdonságokat:

    - **Név**: Adja meg az új profil leíró nevét.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: válassza a **kézbesítési optimalizálás**lehetőséget.

4. Válassza a **beállítások** > a **Konfigurálás**lehetőséget, és adja meg, hogyan szeretné letölteni a frissítéseket és az alkalmazásokat. Az elérhető beállításokkal kapcsolatos további információkért lásd: [az Intune kézbesítési optimalizálási beállításai](../delivery-optimization-settings.md).

5. Ha elkészült, válassza **az OK** > **Létrehozás** lehetőséget a módosítások mentéséhez.

Ekkor létrejön a profil, és megjelenik a listában. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , majd [Figyelje annak állapotát](device-profile-monitor.md).

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>A Windows 10-es frissítési körökből származó kézbesítési optimalizálás eltávolítása

A kézbesítési optimalizálás korábban a szoftverfrissítési gyűrűk részeként lett konfigurálva. Az 2019-es verziótól kezdődően a kézbesítési optimalizálási beállítások a kézbesítő optimalizálási eszköz konfigurációs profiljának részeként vannak konfigurálva, amely további beállításokat tartalmaz, amelyek több, mint szoftverfrissítés-kézbesítést érintenek az eszközökre. Ha még nem tette meg, távolítsa el a kézbesítési optimalizálási beállítást a frissítési körökből úgy, hogy a beállítás *nincs konfigurálva*értékre állítva, majd egy kézbesítési optimalizálási profillal felügyeli az elérhető lehetőségek szélesebb körét.

1. Kézbesítési optimalizálási eszköz konfigurációs profiljának létrehozása:

    1. A Microsoft Endpoint Manager felügyeleti központban válassza az **eszközök** > **konfigurációs profilok** > **profil létrehozása**lehetőséget.
    2. Adja meg a következő tulajdonságokat:

        - **Név**: Adja meg az új profil leíró nevét.
        - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
        - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
        - **Profil típusa**: válassza a **kézbesítési optimalizálás**lehetőséget.
        - **Beállítások**: a **kézbesítési optimalizálás letöltési módjához**válassza ki ugyanazt a módot, amelyet a meglévő szoftverfrissítési kör használ, hacsak nem szeretné módosítani az eszközökön alkalmazott beállításokat. A választható lehetőségek:
            - **Nincs konfigurálva**
            - **Csak HTTP, nincs társ**
            - **HTTP összekeverve az azonos NAT mögötti egyenrangú hálózattal**
            - **HTTP összekeverve egy privát csoporton belüli társ-összevonással**
            - **HTTP-vel kevert internetes társak**
            - **Egyszerű letöltési mód társ nélkül**
            - **Mellőzési mód**
    3. Konfigurálja az esetlegesen felügyelni kívánt további beállításokat.

2. Rendelje hozzá az új profilt ugyanahhoz az eszközökhöz és felhasználókhoz, mint a meglévő szoftverfrissítési gyűrű. [A profil hozzárendelésével](device-profile-assign.md) felsorolja a lépéseket.

3. A meglévő szoftveres gyűrű konfigurálásának visszaadása:
    1. A Microsoft Endpoint Manager felügyeleti központban lépjen a **szoftverfrissítések** > Windows 10 frissítési körök elemre.
    2. A listában válassza ki a frissítési gyűrűt.
    3. A beállítások területen állítsa be a **kézbesítési optimalizálás letöltési módját** a **nincs konfigurálva**értékre.
    4. **Az OK gombra** > **menteni** a módosításokat.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak](device-profile-monitor.md) állapotát.  
Tekintse meg az Intune [kézbesítési optimalizálási beállításait](../delivery-optimization-settings.md) .
