---
title: "Eszközök védelme | Microsoft Intune"
description: 
keywords: 
author: Robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c52448ab454a764be922319fb930a85a86c3996e
ms.openlocfilehash: c8f833593e6a4606b0dd56373d4dc016c7ea0924


---

# Eszközök védelme a Microsoft Intune-nal
Ha eszközeit már az Intune-ban felügyeli, akkor valószínűleg arról is gondoskodni kíván, hogy védve legyenek a jogosulatlan hozzáférés és más fenyegetések ellen. Íme az Intune néhány olyan funkciója, amelyek e célok megvalósítását segítik elő.

> [!TIP]
> Ez a témakör nem ismerteti az Intune összes, eszközei védelmét elősegítő módszerét. Használhatja az Intune-szabályzatokat számos eszközbiztonsági beállítás megadásához, például jelszavak beállításához, titkosítási beállításokhoz, illetve olyan hardverösszetevők, mint a Bluetooth és a kamera beállításaihoz. A beállításokkal kapcsolatban bővebben lásd [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) című témakört.

## PIN-kódok alaphelyzetbe állítása a felhasználók eszközökről való kizárása esetén
Mivel a mobileszközökön lévő vállalati adatok védelmének legfontosabb eleme a hitelesítő kódok használatának megkövetelése, időnként [alaphelyzetbe kell állítania a hitelesítő kódot](use-remote-lock-and-passcode-reset-in-microsoft-intune.md), vagy ehhez segítséget kell nyújtania az alkalmazottnak a hitelesítő kód eltávolításával vagy ideiglenes jelszó távolról történő beállításával. Elvesztés vagy lopás esetén [távolról is zárolhatja az eszközöket](use-remote-lock-and-passcode-reset-in-microsoft-intune.md).

## Kiegészítő védelmi réteg hozzáadása Windows rendszerű eszközökhöz
A[többtényezős hitelesítés (MFA)](protect-windows-devices-with-multi-factor-authentication.md) biztonságosabb módszer a hálózatban lévő Windows és Windows Phone rendszerű eszközök felhasználóinak hitelesítésére.  A Multi-Factor Authentication szolgáltatás használatakor a felhasználóknak nem csupán felhasználónévvel és jelszóval, egy telefonhívással vagy szöveges üzenettel kell megerősíteniük identitásukat.

## A Microsoft Passport beállításainak szabályozása Windows-eszközökön
Az Intune lehetővé teszi az integrációt a [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) nevű, a Windows 10-ben vagy későbbi verzióban használható alternatív bejelentkezési módszer alkalmazását. Ez az Active Directoryt vagy az Azure Active Directory egy fiókját használja jelszó, intelligens kártya vagy virtuális intelligens kártya helyett.

## Az aktiválási zár megkerülése iOS-eszközökön
Az aktiválási zár funkcióval senki nem törölheti vagy aktiválhatja újra az eszközt addig, amíg meg nem adta a felhasználó az Apple ID azonosítóját és jelszavát. Azonban ez problémákkal is járhat, például akkor, ha a felhasználó a zár feloldása nélkül elhagyja a céget. Az [iOS aktiválási zár megkerülésével](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) feloldhatja a felügyelt iOS-eszközök zárolását, így azokat új feladatokhoz használhatja, vagy törölheti a tartalmát.

## Intune ügyfélprogram által felügyelt Windows rendszerű számítógépek védelme
Az Intune továbbra is támogatja az olyan Windows rendszerű számítógépek védelmét, amelyek nincsenek regisztrálva, de felügyeletüket az Intune ügyfélszoftvere biztosítja. Ha szeretné tudni, hogyan segítik ezek a szabályzatok a Windows rendszerű számítógépek védelmét, a [Szabályzatok használata az Intune ügyfélszoftvert futtató Windows rendszerű számítógépek védelméhez](policies-to-protect-windows-pcs-in-microsoft-intune.md) című témakörből tájékozódhat.



<!--HONumber=Jun16_HO4-->


