---
# required metadata

title: A Microsoft Intune szolgáltatásban használt tartománynevek | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# A Microsoft Intune szolgáltatásban használt tartománynevek

A Microsoft Intune beállítása előtt olvassa el ezt a témakört, valamint a [Tudnivalók a Microsoft Intune elindítása előtt](what-to-know-before-you-start-microsoft-intune.md) című témakörben felsorolt követelmények listáját..

Amikor egy szervezet előfizet a Microsoft egy felhőszolgáltatására, például az Intune-ra, egy, a következőhöz hasonló kezdeti tartománynevet kap: **contoso.onmicrosoft.com**. Ebben a példában a **contoso** a regisztrációkor választott tartománynév, az **onmicrosoft.com** pedig az előfizetéshez hozzáadott fiókokhoz rendelt utótag. A tartománynevet a regisztrációs folyamat befejezése után nem lehet módosítani. Globális rendszergazdaként azonban hozzáadhatók a szervezet által a szolgáltatáshoz használható egyéni tartománynevek, vagy eltávolíthatók a korábban hozzáadott tartományok.

Az onmicrosoft tartomány használatakor alapértelmezés szerint minden importált felhasználó az **onmicrosoft.com** utótagot kapja meg az egyszerű felhasználónevéhez (UPN).

Ha a regisztrációkor megkapott tartománynév helyett egy saját tulajdonú tartománynevet szeretne használni, azt felveheti az Azure Active Directory szolgáltatásba. Miután hozzáadta a tartományt, és megerősítette, hogy az a tulajdonában áll, a DNS-szolgáltató DNS-erőforrásrekordjainak módosításával létrehozhat a tartománynevet tartalmazó fiókokat és csoportokat. Ha egyéni tartományt tervez használni, egyszerűbbé teheti a felhasználói fiókok kezelését azzal, hogy egyéni tartománynevet állít be az előfizetéshez, mielőtt megkezdi a felhasználók szinkronizálását a helyi Active Directoryból.

Az Intune számára ugyanúgy kell konfigurálni a tartományneveket és a DNS-erőforrásrekordokat, mint az Azure Active Directory bármilyen más bérlője számára. Útmutatásért lásd: [Add your custom domain name to simplify sign-in using Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/) (Egyéni tartománynév felvétele az Azure Active Directoryba a bejelentkezés leegyszerűsítésére).

### További információ
[Tudnivalók a Microsoft Intune elindítása előtt](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO1-->


