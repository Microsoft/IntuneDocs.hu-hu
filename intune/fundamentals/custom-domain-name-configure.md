---
title: Állítson be egy egyéni tartománynevet
titleSuffix: Microsoft Intune
description: Egyéni tartománynév hozzáadása a Microsoft Intune-előfizetéshez
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1087082400b321c07ea5993ca0280bf0ce455b1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731563"
---
# <a name="configure-a-custom-domain-name"></a>Állítson be egy egyéni tartománynevet

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Ez a témakör arról tájékoztatja a rendszergazdákat, hogy miképpen szabhatják testre a bejelentkezést egy DNS CNAME rekord létrehozásával a Microsoft Intune-ban.

Amikor egy szervezet előfizet a Microsoft egy felhőszolgáltatására, például az Intune-ra, a következőhöz hasonló, az Azure Active Directoryban (AD) tárolt kezdeti tartománynevet kap: **tartomanynev.onmicrosoft.com**. Ebben a példában a **tartomanynev** a regisztrációkor választott tartománynév, az **onmicrosoft.com** pedig az előfizetéshez hozzáadott fiókokhoz rendelt utótag. Saját szervezete egyéni tartományát konfigurálhatja az Intune elérésére az előfizetéskor megadott tartománynév helyett.

Mielőtt felhasználói fiókokat hozna létre, vagy szinkronizálná a helyi Active Directoryt, célszerű eldöntenie, hogy az .onmicrosoft.com tartományt fogja-e használni, vagy egyéni tartományneve(ke)t kíván-e hozzáadni. Az egyéni tartomány beállítása a felhasználók hozzáadása előtt egyszerűbbé teheti a felhasználók kezelését. Az ügyfél tartományának beállítása lehetővé teszi, hogy a felhasználók a más tartományi erőforrásokhoz való hozzáféréshez használt hitelesítő adatokkal jelentkezzenek be.

Amikor előfizet egy felhőalapú Microsoft-szolgáltatásra, az adott szolgáltatáspéldány az identitás- és címtárszolgáltatásokat biztosító [Microsoft AD-bérlőjévé](https://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) válik. És mivel az Intune-t ugyanúgy lehet beállítani arra, hogy az Ön szervezetének egyéni tartománynevét használja, mint bármely más Azure AD-bérlőt, az [Add your domain](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/) (Egyéni tartomány felvétele) című témakör útmutatását követheti.

> [!TIP]
> Az egyéni tartományok kapcsolatos további információkért lásd: [Conceptual overview of custom domain names in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/) (Az Azure Active Directoryban használt egyéni tartománynevek elméleti áttekintése) .

A kezdeti onmicrosoft.com tartománynév nem nevezhető át és nem távolítható el. Az Intune-nal használt egyéni tartománynevek hozzáadásával, ellenőrzésével vagy eltávolításával megtarthatja az üzleti identitását.

## <a name="to-add-and-verify-your-custom-domain"></a>Egyéni tartomány hozzáadása és hitelesítése

1. Lépjen a [Microsoft 365 felügyeleti központba](https://admin.microsoft.com/) , és jelentkezzen be a rendszergazdai fiókjával.

2. A navigációs ablakban kattintson a **Beállítás** &gt; **Tartományok** elemre.

3. Kattintson a **Tartomány felvétele** gombra, és írja be az egyéni tartománynevet. Kattintson a **Tovább** gombra.
   ![Képernyőkép a Microsoft 365 felügyeleti központ beállításairól > a kiválasztott tartományok és új tartománynév hozzáadása](./media/custom-domain-name-configure/domain-custom-add.png)
4. A megnyíló **Tartomány hitelesítése** párbeszédpanelen megtalálhatja a DNS-szolgáltatón létrehozandó TXT-rekord értékeit.
    - **GoDaddy-felhasználók**: Microsoft 365 felügyeleti központ átirányítja Önt a GoDaddy bejelentkezési oldalára. A hitelesítő adatok megadása és a tartományváltást engedélyező megállapodás elfogadása után a TXT-rekord automatikusan létrejön. Alternatív módszerként [a TXT-rekord manuálisan is létrehozható](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Register.com-felhasználók**: A TXT-rekord létrehozásához kövesse a [részletes útmutatót](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) .
5. [Előfordulhat, hogy további DNS-rekordokat kell létrehoznia az Intune-regisztrációhoz](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium).

Az egyéni tartományok hozzáadásának és hitelesítésének lépései [az Azure Active Directoryban is végrehajthatók](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Tudjon meg többet [a kezdeti onmicrosoft.com tartománnyal kapcsolatban (Office 365)](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A).

Ha szeretne többet megtudni arról, hogyan [egyszerűsítheti a Windows-regisztrációt prémium szintű Azure ad nélkül](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium) , hozzon létre egy DNS-CNAME-t, amely átirányítja a regisztrációt az Intune-kiszolgálókra.
