---
title: Az eszköz kivonása a felügyelet alól, ha nem fogadta el a használati feltételeket | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: bf94574bd86b0e0ce7455988781250b97d87a2c2
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529058"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>Az eszköz kivonása a felügyelet alól, ha nem fogadta el a használati feltételeket

Ha nem fogadja el a Használati feltételeket, amikor megpróbál bejelentkezni a Munkahelyi portál alkalmazásba, akkor a jövőbeni bejelentkezési próbálkozásai sikertelenek lesznek. Ebben az esetben a következő „áthidaló” megoldásokat kell alkalmaznia az eszköz Intune-ból való törléséhez.

Amikor eltávolítja a Vállalati portál alkalmazást, azzal az eszközt is törli az Intune-ból. Az eszköz többé nem tud hozzáférni a vállalati erőforrásokhoz. Az eszköz felügyelet alóli kivonásának további következményeiről további információkért lásd: [Mi történik, ha törli az eszköz regisztrációját az Intune-ból?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

A Vállalati portál alkalmazás eltávolítása előtt az **Eszközadminisztrátorok** beállításba kell lépnie, és ki kell kapcsolnia a **Vállalati portál** elemet. A lépések kissé eltérőek lehetnek attól függően, hogy milyen androidos eszközzel rendelkezik.

## <a name="removing-the-device-from-the-company-portal-app"></a>Az eszköz eltávolítása a Céges portál alkalmazásból

Az eszköz eltávolítása az Intune-ból és a Vállalati portál alkalmazás eltávolítása:

1.  Lépjen a **Settings** (Beállítások)&gt;**Security (Biztonság) &amp; Screen Lock (Képernyőzár)** &gt;**Device administrators** (Eszközadminisztrátorok) elemhez.

    A lépés elvégzésével azonnal törli az eszköz regisztrációját.

2.  Törölje a **Vállalati portál** melletti jelölőnégyzet jelölését a kikapcsoláshoz.

    Most már eltávolíthatja a Vállalati portál alkalmazást.

## <a name="removing-data-collected-by-the-company-portal-app"></a>A Céges portál alkalmazás által gyűjtött adatok eltávolítása

Az Android-eszközhöz készült Céges portál alkalmazás által az eszközön tárolt adatok törlésének módja a következő:

  - Törölje az alkalmazás adatait az Alkalmazások -> kattintás az alkalmazáson -> "Adatok törlése" gomb lépésekkel.
  - Törölje a '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' mappát.


További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához (a kapcsolattartási adatokat a [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja), vagy írjon a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-csapatának</a>.
