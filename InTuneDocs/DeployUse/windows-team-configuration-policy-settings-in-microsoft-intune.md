---
title: "A Windows Team konfigurációs házirendjének beállításai | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: b08d52289b94429b1328a7470469a7efdf4d46a7


---

# A Windows Team konfigurációs házirendjének beállításai a Microsoft Intune-ban
Regisztrált Windows 10 Team eszközök, például a Microsoft Surface Hub beállításainak konfigurálására használhatja a **Windows 10 Team eszközökhöz készült általános konfigurációs házirendjét**.

|Beállítás neve|Részletek|
|----------------|-----------|
|**Képernyő felébresztésének engedélyezése, ha valaki van a helyiségben**|Lehetővé teszi az eszköz automatikus felébresztését, ha az érzékelők valakit észlelnek a helyiségben.|
|**PIN-kód kérése vezeték nélküli vetítéshez**|Meghatározza, hogy meg kell-e adni a PIN-kódot az eszköz vezeték nélküli vetítési funkcióinak használata előtt.|
|**Karbantartási időszak megadása az eszközfrissítésekhez**|Meghatározza, hogy mely időszakban kerül sor az eszköz frissítéseire. Beállíthatja a kezdési időt és az időtartamot (1-5 óra) is.|
|**Az Azure-os Operational Insights engedélyezése**|A Microsoft Operations Manager csomag részét képező Azure-os Operational Insights naplófájladatokat gyűjt, tárol és elemez a from Windows 10 Team-eszközökről.<br /><br />Az Azure-os Operational Insights szolgáltatáshoz végzett csatlakozáshoz meg kell adnia egy **munkaterület-azonosítót** és egy **munkaterületkulcsot**.|
|**Miracast vezeték nélküli vetítés engedélyezése**|Engedélyezze ezt a lehetőséget, hogy a Windows 10 Team-eszköz Miracast technológiát használó eszközökkel vetíthessen.<br /><br />Ha engedélyezi ezt a lehetőséget, a **Válasszon Miracast-csatornát** területen válassza ki a tartalom vetítéséhez használni kívánt Miracast-csatornát.|
|**Az üdvözlőképernyőn megjelenő értekezletadatok kiválasztása**|Ha engedélyezi ezt a lehetőséget, kiválaszthatja az **Üdvözöljük** képernyő **Értekezletek** csempéjén megjelenő adatokat. A következőket teheti:<br /><br />-   **Csak szervező és időpont megjelenítése**<br />-   **Szervező, időpont és tárgy megjelenítése (zártkörű értekezletek esetén a tárgy rejtett)**|
|**Zárolási képernyő háttérképének URL-címe**|Engedélyezze ezt a beállítást, ha az Ön által megadott URL-címről egy egyéni hátteret szeretne megjeleníteni a Windows 10 Team-eszközök **Üdvözöljük** képernyőjén.<br /><br />A képnek PNG formátumban kell lennie, és az URL-címnek a **https://** karakterlánccal kell kezdődnie.|


### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


