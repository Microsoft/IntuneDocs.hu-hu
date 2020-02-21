---
title: Eszközök védelme a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Megismerhet néhány módot, amelyek segítségével az Intune segít megvédeni az eszközét a jogosulatlan hozzáféréstől és más fenyegetésektől.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: conceptual
ms.subservice: protect
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49c629039c08c892c7d6b19422d79c9eb1a8d760
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510469"
---
# <a name="protect-devices-with-microsoft-intune"></a>Eszközök védelme a Microsoft Intune-nal

A Microsoft Intune segít megvédeni a kezelt eszközöket és az azokon tárolt adatokat.

## <a name="device-configuration"></a>Eszközök konfigurálása
Az Intune [konfigurációs szabályzatai](../configuration/device-profiles.md) egy sor beállítás és funkció ellenőrzésével járulnak hozzá az eszközök védelméhez. Például:

- Korlátozhatja az eszköz hardveres funkcióit, például a kamera vagy a Bluetooth használatát.
- Megfelelő és nem megfelelő alkalmazásokat konfigurálhat. Nem megfelelő alkalmazás telepítése esetén riasztást kap (és egyes platformok képesek ténylegesen megakadályozni a telepítést).

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>PIN-kódok alaphelyzetbe állítása a felhasználók eszközökről való kizárása esetén
Mivel a mobileszközökön lévő vállalati adatok védelmének legfontosabb eleme a hitelesítő kódok használatának megkövetelése, időnként [alaphelyzetbe kell állítania a hitelesítő kódot](../remote-actions/device-passcode-reset.md), vagy ehhez segítséget kell nyújtania az alkalmazottnak a hitelesítő kód eltávolításával vagy ideiglenes jelszó távolról történő beállításával. Elvesztés vagy lopás esetén [távolról is zárolhatja az eszközöket](../remote-actions/device-remote-lock.md).

## <a name="retire-devices-and-remove-data"></a>Eszközök kivonása és adatok eltávolítása
Ha egy eszközt [ki kell vonni az Intune-felügyelet alól](../remote-actions/devices-wipe.md) (például azért, mert a felhasználó távozik a vállalattól, vagy mert az eszköz elvész vagy ellopják), valószínű, hogy szükség van az adatok eltávolítására az eszközről. Az Intune egy sor módszert kínál a vállalati adatok biztonságának megőrzésére.

## <a name="require-devices-to-be-compliant"></a>Megfelelőség előírása az eszközök számára
Az Intune olyan [eszközmegfelelőségi szabályzatokat](device-compliance-get-started.md) biztosít, amelyek segítségével értékelheti (és bizonyos esetekben kijavíthatja) azokat az eszközöket, amelyek nem felelnek meg a meghatározott szabályoknak. Jelentéseket kaphat például a következőkről:
- iOS/iPadOS eszközök
- titkosított vagy nem titkosított eszközök
- Windows 10-es eszközök állapota (az állapotigazolási szolgáltatás adatai alapján).

## <a name="protect-apps-and-the-data-they-use"></a>Az alkalmazások és az általuk használt adatok védelme
Az Intune egy sor funkciót biztosít az alkalmazások és adataik védelmére. A mobilalkalmazás-kezelési (MAM-) szabályzatok például a következőket biztosítják:
- meggátolják, hogy védett alkalmazások biztonsági másolatot készítsenek az adatokról
- korlátozzák a más alkalmazásokba történő másolást és beillesztést
- PIN-kódot kérhetnek egy alkalmazás eléréséhez További információ: [Az alkalmazások és az adatok védelme a Microsoft Intune-nal](../apps/app-protection-policy.md)

## <a name="add-an-additional-layer-of-protection-to-devices"></a>Kiegészítő védelmi réteg hozzáadása az eszközökhöz
A [többtényezős hitelesítés (MFA)](../enrollment/multi-factor-authentication.md) segítségével a hálózatban lévő eszközök felhasználóinak hitelesítését még biztonságosabb módon végezheti.  A többtényezős hitelesítés (MFA) szolgáltatás használatakor a felhasználóknak a felhasználónév-jelszó pároson túlmenően egy telefonhívással vagy szöveges üzenettel is igazolniuk kell személyazonosságukat.

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>A Vállalati Windows Hello beállításainak szabályozása Windows-eszközökön
Az Intune lehetővé teszi az integrációt a [Vállalati Windows Hello](windows-hello.md) nevű, a Windows 10-ben és későbbi verziókban használható alternatív bejelentkezési módszerrel, amely az Active Directoryt vagy az Azure Active Directory egy fiókját használja jelszó, intelligens kártya vagy virtuális intelligens kártya helyett.

## <a name="disable-activation-lock-on-ios-devices"></a>Aktiválási zár letiltása iOS-eszközökön
Az aktiválási zár funkció segít megvédeni a felhasználói eszközöket. A funkció engedélyezése esetén senki nem törölheti vagy aktiválhatja újra az eszközt addig, amíg meg nem adta a felhasználó Apple ID azonosítóját és jelszavát. Azonban ez problémákkal is járhat, például akkor, ha a felhasználó a zár feloldása nélkül elhagyja a céget. Az [iOS/iPadOS aktiválási zár letiltása](../remote-actions/device-activation-lock-disable.md) segíthet a felügyelt iOS-/iPadOS-eszközök zárolásának eltávolításában, amely lehetővé teszi az újbóli kiosztását vagy törlését.

## <a name="next-steps"></a>További lépések

További információ a [Mobile Threat Defense-ről](mobile-threat-defense.md)
