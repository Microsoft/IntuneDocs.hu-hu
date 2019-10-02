---
title: A Windows 10 kézbesítési optimalizálási beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Annak konfigurálása, hogy az Intune-nal felügyelt Windows 10-es eszközök hogyan használják a kézbesítési optimalizálást. Az Intune-ban hozzon létre egy eszköz-konfigurációs profilt a frissítések internetről történő telepítéséhez. Azt is megtudhatja, hogyan lehet lecserélni a meglévő frissítési gyűrűket egy kézbesítési optimalizálási profillal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 4357a3235386d9fd17c1df23004e9bc8ddeb28ca
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730847"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Kézbesítési optimalizálási beállítások a Microsoft Intune

Az Intune-nal a Windows 10-es eszközök kézbesítési optimalizálási beállításaival csökkentheti a sávszélesség-használatot, amikor az eszközök letöltik az alkalmazásokat és a frissítéseket. A kézbesítés optimalizálása az eszköz konfigurációs profiljainak részeként van konfigurálva.  

Ez a cikk bemutatja, hogyan konfigurálhatja a kézbesítés optimalizálási beállításait az eszköz konfigurációs profiljának részeként. Miután létrehozta a profilt, a profilt hozzárendelheti vagy üzembe helyezheti a Windows 10-es eszközökön. 

Az Intune által támogatott kézbesítési optimalizálási beállítások listáját itt tekintheti meg: az [Intune kézbesítési optimalizálási beállításai](../delivery-optimization-settings.md).  

Ha többet szeretne megtudni a Windows 10-es továbbítási optimalizálásáról, tekintse meg a Windows dokumentációjának [kézbesítési optimalizálási frissítései](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) című témakört.  


> [!NOTE]
> **Szoftverfrissítések – a Windows 10 frissítési gyűrűit** a **kézbesítési optimalizálási** beállítások váltották fel. A meglévő frissítési körök módosíthatók a **kézbesítési optimalizálási** beállítások használatára. [Meglévő frissítési körök áthelyezése a kézbesítési optimalizálásba](#move-existing-update-rings-to-delivery-optimization) (ebben a cikkben) 
## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.

3. Adja meg a következő tulajdonságokat:

    - **Név**: Adjon meg egy leíró nevet az új profilhoz.
    - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza ki a platformot:  

        - **Windows 10 és újabb**

    - **Profil típusa**: Válassza a **kézbesítési optimalizálás**lehetőséget.
    - **Beállítások**: Konfigurálja azokat a beállításokat, amelyek meghatározzák, hogyan szeretné letölteni a frissítéseket és az alkalmazásokat. Az elérhető beállításokkal kapcsolatos további információkért lásd: [az Intune kézbesítési optimalizálási beállításai](../delivery-optimization-settings.md).

4. Ha elkészült, kattintson **az OK** > **Létrehozás** gombra a módosítások mentéséhez.

Ekkor létrejön a profil, és megjelenik a listában. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , majd [Figyelje annak állapotát](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Meglévő frissítési körök áthelyezése a kézbesítési optimalizálásba

A **kézbesítési optimalizálási** beállítások lecserélik a **szoftverfrissítéseket – a Windows 10 frissítési gyűrűit**. A meglévő frissítési körök egyszerűen módosíthatók a **kézbesítési optimalizálási** beállítások használatára. Ha a továbbítási optimalizálási profil létrehozásakor ugyanazokat a beállításokat szeretné karbantartani, használja ugyanazt a *továbbítási optimalizálási letöltési módot* , majd állítsa be a már használatban lévő beállításokat. Azonban a továbbítási optimalizálási beállítások újrakonfigurálásával kihasználhatja a kézbesítési optimalizálási profil által kezelhető további beállítások teljes körét.

1. Kézbesítési optimalizálás konfigurációs profiljának létrehozása:

    1. Az Intune-ban válassza az **eszköz konfigurációja** > **profilok** > **profil létrehozása**lehetőséget.
    2. Adja meg a következő tulajdonságokat:

        - **Név**: Adjon meg egy leíró nevet az új profilhoz.
        - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
        - **Platform**: Válassza **a Windows 10 és újabb**lehetőséget.
        - **Profil típusa**: Válassza a **kézbesítési optimalizálás**lehetőséget.
        - **Beállítások**: A **kézbesítési optimalizálás letöltési módjához**válassza ki ugyanazt a módot, amelyet a meglévő szoftverfrissítési kör használ, kivéve, ha módosítani szeretné az eszközökön alkalmazott beállításokat. A választható lehetőségek:
            - **Nincs konfigurálva**
            - **Csak HTTP, nincs társ**
            - **HTTP összekeverve az azonos NAT mögötti egyenrangú hálózattal**
            - **HTTP összekeverve egy privát csoporton belüli társ-összevonással**
            - **HTTP-vel kevert internetes társak**
            - **Egyszerű letöltési mód társ nélkül**
            - **Mellőzési mód**
    3. Konfigurálja az esetlegesen felügyelni kívánt további beállításokat.
1. Rendelje hozzá az új profilt ugyanahhoz az eszközökhöz és felhasználókhoz, mint a meglévő szoftverfrissítési gyűrű. [A profil hozzárendelésével](device-profile-assign.md) felsorolja a lépéseket.

3. A meglévő szoftveres gyűrű konfigurálásának visszaadása:
    1. Az Intune-ban lépjen a **szoftverfrissítések** > Windows 10 frissítési körök elemre.
    2. A listában válassza ki a frissítési gyűrűt.
    3. A beállítások területen állítsa be a **kézbesítési optimalizálás letöltési módját** a **nincs konfigurálva**értékre.
    4. **OK**@no__t – 1**mentse** a módosításokat.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak](device-profile-monitor.md) állapotát.  
Tekintse meg az Intune [kézbesítési optimalizálási beállításait](../delivery-optimization-settings.md) .
