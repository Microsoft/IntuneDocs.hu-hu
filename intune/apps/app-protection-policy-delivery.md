---
title: Az App Protection-szabályzatok kézbesítésének és időzítésének ismertetése
titleSuffix: Microsoft Intune
description: Ismerkedjen meg a különböző központi telepítési Windows alkalmazás-védelmi házirendekkel, hogy megtudja, mikor kell megjelenniük a végfelhasználói eszközökön.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9f9b6734dc5a5af320519a5f65442f01d21d66f
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940232"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Az App Protection-szabályzat kézbesítési időzítésének ismertetése

Ismerkedjen meg a különböző központi telepítési Windows alkalmazás-védelmi házirendekkel, hogy megtudja, mikor jelenjenek meg a módosítások a végfelhasználói eszközökön.

## <a name="delivery-timing-summary"></a>Kézbesítés időzítésének összegzése

Az alkalmazás-védelmi szabályzat kézbesítése a licencelési állapottól és az Intune szolgáltatás regisztrálásával függ a felhasználók számára.  

|    Felhasználói állapot    |    Az App Protection működése     |    Újrapróbálkozási időköz (lásd a megjegyzést)    |    Miért jelentkezik?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    A bérlő nincs előkészítve    |    Várjon a következő újrapróbálkozási időközre.  Az alkalmazás védelme nem aktív a felhasználó számára.    |    24 óra    |    Akkor következik be, amikor nem állította be a bérlőt az Intune-hoz.    |
|    A felhasználó nem rendelkezik licenccel     |    Várjon a következő újrapróbálkozási időközre.  Az alkalmazás védelme nem aktív a felhasználó számára.     |    12 óra – az androidos eszközökön az intervallumhoz az Intune APP SDK 5.6.0 vagy újabb verziójára van szükség. Ellenkező esetben az Android-eszközök esetében az intervallum 24 óra.   |    Akkor következik be, amikor nem licencelte a felhasználót az Intune-hoz.    |
|    A felhasználóhoz nincs hozzárendelve alkalmazás-védelmi szabályzat    |    Várjon a következő újrapróbálkozási időközre.  Az alkalmazás védelme nem aktív a felhasználó számára.    |    12 óra        |    Akkor következik be, amikor nincs hozzárendelve az Alkalmazásbeállítások a felhasználóhoz.    |
|    A felhasználó sikeresen regisztrált az Intune MAM-ban    |    Az App Protection házirend-beállításokkal lesz alkalmazva.    A frissítések az újrapróbálkozási időköz alapján történnek    |    Felhasználói terhelés alapján meghatározott Intune-szolgáltatás.    Általában 30 perc.     |    Akkor következik be, amikor a felhasználó sikeresen regisztrálta az Intune szolgáltatásban a MAM-konfigurációt.    |

> [!NOTE]
> Az újrapróbálkozási időközök előírhatják az aktív alkalmazások használatát, ami azt jelenti, hogy az alkalmazás elindul és használatban van.  Ha az újrapróbálkozási időköz 24 óra, és a felhasználó 48 órát vár az alkalmazás elindításához, akkor az alkalmazás védelmi ügyfele 48 órával később újrapróbálkozik.

## <a name="handling-network-connectivity-issues"></a>Hálózati kapcsolattal kapcsolatos problémák kezelése

Ha a felhasználói regisztráció hálózati kapcsolat miatt meghiúsul, a rendszer gyorsított újrapróbálkozási időközt használ.  Az Application Protection-ügyfél egyre több intervallumban próbálkozik addig, amíg az intervallum eléri a 60 percet vagy a sikeres kapcsolódást.  Az ügyfél ezután 60 perces időközönként újra próbálkozik, amíg a rendszer sikeres kapcsolódást nem végez. Ezt követően az ügyfél a felhasználói állapot alapján visszaadja a normál újrapróbálkozási időközt.

## <a name="next-steps"></a>További lépések

[Licencek kiosztása a felhasználók számára, hogy regisztrálni tudják az eszközöket az Intune-ban](../fundamentals/licenses-assign.md)

