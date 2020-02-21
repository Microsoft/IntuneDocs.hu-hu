---
title: iOS/iPadOS app kiépítési profilok Microsoft Intune
titleSuffix: ''
description: Az Intune biztosítja az eszközöket, amelyek segítségével proaktív módon rendelhet hozzá új kiépítési profilt azokhoz az eszközökhöz, amelyeken hamarosan lejárnak az alkalmazások.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f40b6f458a95a466874a2d1ce44fcafa37249d46
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513623"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Az iOS-alkalmazáskiépítési profilok segítségével megakadályozhatja, hogy az alkalmazásai lejárjanak

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Bevezetés

Az iPhone-hoz és Ipadekhez rendelt Apple iOS/iPadOS üzletági alkalmazások beépített kiépítési profillal és a tanúsítvánnyal aláírt kóddal vannak ellátva. Az alkalmazás futtatásakor az iOS/iPadOS megerősíti az iOS/iPadOS alkalmazás integritását, és kikényszeríti a létesítési profil által meghatározott szabályzatokat. A következő érvényesítések zajlanak le:

- **Telepítési fájl integritása** – az iOS/iPadOS összehasonlítja az alkalmazás részleteit a vállalati aláíró tanúsítvány nyilvános kulcsával. Ha ezek eltérnek, akkor előfordulhat, hogy az alkalmazás tartalma módosult. Ebben az esetben a rendszer nem engedélyezi az alkalmazás futását.
- **Képességek kényszerítése** – az iOS/iPadOS megkísérli kikényszeríteni az alkalmazás képességeit a vállalati létesítési profilból (nem az egyéni fejlesztői létesítési profilokból), amelyek az alkalmazás telepítési (. IPA) fájljában találhatók.


Az alkalmazások aláírásához használt vállalati aláíró tanúsítvány általában három évig érvényes. A kiépítési profil viszont egy év után lejár. Amíg a tanúsítvány még érvényes, az Intune biztosítja az eszközöket egy új kiépítési profil proaktív hozzárendelésére olyan eszközökhöz, amelyeken már majdnem lejáró alkalmazások vannak.
A tanúsítvány lejárata után újra regisztrálnia kell az alkalmazást egy új tanúsítvánnyal, és be kell ágyaznia egy új kiépítési profilt az új tanúsítvány kulcsával.

Rendszergazdaként a biztonsági csoportokat belefoglalhatja és kizárhatja az iOS/iPadOS alkalmazás kiépítési konfigurációjának hozzárendeléséhez. Például hozzárendelhet egy iOS/iPadOS-alkalmazás üzembe helyezési konfigurációját az összes felhasználóhoz, de kizárhat egy Executive csoportot is.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>iOS-beli mobilalkalmazás-kiépítési profilok létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > iOS-alkalmazások **létesítési profiljait** > a **profil létrehozása**lehetőséget.
3. Az **alapvető beállítások** lapon adja hozzá a következő értékeket:
    - **Név** – Adjon egy nevet a mobil kiépítési profilnak.
    - **Leírás** – Lehetősége van a házirend ismertetésének megadására.
    - **Profil feltöltése** – válassza a **Megnyitás** ikon lehetőséget, majd válassza ki az Apple [Developer webhelyéről](https://developer.apple.com/)letöltött, `.mobileprovision`t tartalmazó Apple Mobile konfigurációs profilt.

   A **lejárati dátum** a fent hozzáadott Apple Mobile konfigurációs profilban szereplő értékből lesz kitöltve.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Kattintson a **Tovább gombra: hatókör címkék**.<br>
   A **hatókör címkék** lapon megadhatja a hatókör címkéit, és meghatározhatja, hogy ki láthatja az iOS/iPadOS alkalmazás-létesítési profilt az Intune-ban. A hatókör-címkékkel kapcsolatos további információkért lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).
5. Kattintson a **Tovább: hozzárendelések**elemre.<br>
   A **hozzárendelések** lapon a profilt hozzárendelheti a felhasználókhoz és az eszközökhöz. Fontos megjegyezni, hogy a profilokat hozzárendelheti egy eszközhöz, függetlenül attól, hogy az eszközt az Intune felügyeli-e.
6. Kattintson a **Tovább gombra: felülvizsgálat + létrehozás** elemre, és tekintse át a profilhoz megadott értékeket.
7. Ha elkészült, kattintson a **Létrehozás** gombra az iOS/iPadOS app kiépítési profil létrehozásához az Intune-ban. 

## <a name="next-steps"></a>További lépések

Rendelje hozzá a profilt a szükséges iOS/iPadOS-eszközökhöz. További információt az [Eszközprofilok hozzárendelése](../device-profile-assign.md) című útmutató lépéseit használva talál.
