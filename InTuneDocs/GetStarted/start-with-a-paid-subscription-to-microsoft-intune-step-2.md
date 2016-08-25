---
title: "Egyéni tartománynév beállítása | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: a202f06fef0bc8b7eec730728ec10e5fbf234902


---


# Állítson be egy egyéni tartománynevet

Az Intune alapértelmezés szerint azt az **<domain>.onmicrosoft.com** tartománynevet használja, amely akkor jött létre, amikor Ön először előfizetett a szolgáltatásra. Ha a szervezete egyéni tartománnyal rendelkezik, saját Intune-példányát beállíthatja arra, hogy ezt a tartományt használja az előfizetéskor megadott tartománynév helyett.

Mielőtt új felhasználói fiókokat hozna létre, vagy szinkronizálná a helyi Active Directory-beli fiókokat, célszerű eldöntenie, hogy az .onmicrosoft.com tartományt fogja-e használni, vagy egyéni tartományneve(ke)t kíván-e hozzáadni. Az egyéni tartománynév beállítása a felhasználók hozzáadása előtt megkönnyítheti az előfizetéshez tartozó felhasználói azonosítók kezelését, mivel így a felhasználók azokkal a hitelesítő adatokkal jelentkezhetnek be, amelyeket a tartomány egyéb erőforrásainak elérésére is használnak.

Amikor előfizet egy felhőalapú Microsoft-szolgáltatásra, az adott szolgáltatáspéldány az identitás- és címtárszolgáltatásokat biztosító [Microsoft AD-bérlőjévé](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) válik. És mivel az Intune-t ugyanúgy lehet beállítani arra, hogy az Ön szervezetének egyéni tartománynevét használja, mint bármely más Azure AD-bérlőt, az [Add your domain](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/) (Egyéni tartomány felvétele) című témakör útmutatását követheti.

> [!TIP]
> További információt az egyéni tartománynak egy felhőalapú Microsoft-szolgáltatással való használatáról az [Conceptual overview of custom domain names in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/) (Az Azure Active Directoryban használt egyéni tartománynevek elméleti áttekintése) című témakör tartalmaz.

### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések* útmutató 2. lépését.

>[!div class="step-by-step"]

>[&larr; **Bejelentkezés az Intune-ba**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Felhasználók hozzáadása az Intune-hoz** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Jun16_HO4-->


