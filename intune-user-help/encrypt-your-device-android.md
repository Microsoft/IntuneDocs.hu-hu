---
title: Android-eszköz titkosítása az Intune-ban | Microsoft Docs
description: Az androidos eszközök titkosításának bekapcsolásához szükséges lépések az Intune-ban
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2965d6a017d92bd4535a29a2257c0cac5e6deaf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506363"
---
# <a name="encrypting-your-android-device"></a>Android-eszköz titkosítása

Az eszköz titkosítása megvédi a fájlokat és mappákat a jogosulatlan hozzáféréstől, ha az eszköz elveszett vagy ellopták. Az eszközök titkosításának bekapcsolását követően csak a megfelelő jelszóval vagy PIN-kóddal rendelkező személyek jelentkezhetnek be az eszközre. 

Az iskolai vagy munkahelyi erőforrásokhoz való hozzáféréshez a szervezetnek szüksége lehet az Android-eszköz titkosítására. Néhány újabb Android-eszköz alapértelmezés szerint titkosítva van.  

## <a name="turn-on-encryption"></a>Titkosítás bekapcsolása

Ha Céges portál vagy a Microsoft Intune alkalmazás az eszköz titkosítására kéri, hajtsa végre a következő lépéseket. 

> [!Note]
> A Huawei, vivo és ellenfél bizonyos androidos eszközei nem titkosíthatók. További információért [kattintson ide](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Állítsa be az eszköz képernyő-zárolását.  
    a. Válassza a **beállítások** > a **zárolási képernyő és a biztonság** > **képernyő zárolási típusa**lehetőséget.  
    b. Válassza a **PIN-kód**, a **jelszó**vagy a **minta**lehetőséget.  
    c. A képernyő zárolásának konfigurálásához kövesse a képernyőn megjelenő utasításokat.  

2. Lépjen vissza a **zárolási képernyő és a biztonság** elemre, és válassza a **biztonságos indítás**lehetőséget.
3. Válassza **a PIN-kód megkövetelése, ha az eszköz bekapcsolja** > **OK gombot**
4. Az eszköz megerősítéséhez és titkosításához adja meg a PIN-kódját.
5. Nyissa meg Céges portál vagy Microsoft Intune alkalmazást.
    * Céges portál felhasználók: válassza ki az eszközt, és koppintson az **eszközbeállítások ellenõrzése**lehetőségre. 
    * Microsoft Intune felhasználók: várnia kell, amíg az oldal frissül, de ha igen, a titkosítási állapotnak megfelelőre kell váltania.  

Az Android 4,4 és korábbi rendszerű eszközökön nem lehet **biztonságos indítási** lehetőség. Ebben az esetben végezze el az alábbi lépéseket az eszköz titkosításához.

1. Lépjen a **beállítások** > **biztonsági** > az **eszköz titkosítása**gombra. A képernyőn megjelenő címkék az Android-eszközök között változnak. Ha nem jelenik meg az **eszköz titkosítása** beállítás, akkor jelentkezzen be:
    * **Storage** > **Storage-titkosítás**
    * A **Storage** > **a zárolási képernyő és a biztonság** > **egyéb biztonsági beállítások** 

2. Kövesse a képernyőn megjelenő utasításokat. A titkosítás során az eszköz többször is újraindulhat.
3. Nyissa meg Céges portál vagy Microsoft Intune alkalmazást.
    * Céges portál felhasználók: válassza ki az eszközt, és koppintson az **eszközbeállítások ellenõrzése**lehetőségre.  
    * Microsoft Intune felhasználók: várnia kell, amíg az oldal frissül, de ha igen, a titkosítási állapotnak megfelelőre kell váltania.

## <a name="troubleshoot"></a>Hibaelhárítás  
**Probléma**: már titkosította az eszközt, és

- A titkosítási gomb le van tiltva.
- Egy üzenet azt jelzi, hogy titkosítania kell az eszközt.
- A Céges portál vagy Microsoft Intune alkalmazás használatakor hibaüzeneteket kap.

**Az alábbiakkal próbálkozhat**

- Ellenőrizze, hogy az eszköz fel van-e töltve és csatlakoztatva van-e.  
- Ellenőrizze, hogy beállított-e PIN-kódot vagy jelszót az eszközön.  

További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához (a kapcsolattartási adatokat a [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja), vagy írjon a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-csapatának</a>.  
