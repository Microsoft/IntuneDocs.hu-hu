---
title: iOS-alkalmazások alkalmazásvédelmi szabályzatokkal
description: Ez a témakör azt ismerteti, hogy milyen hatással vannak az iOS-alkalmazásokra az alkalmazásvédelmi szabályzatok.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 807b33867d827415165eb65d81b91683830735f5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502858"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Milyen hatással vannak az iOS-alkalmazásokra az alkalmazásvédelmi szabályzatok?

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

 Ez a témakör ismerteti a felhasználói élményt, amikor alkalmazás-védelmi házirendekkel rendelkező alkalmazásokat használ. Az alkalmazásvédelmi szabályzatokat csak akkor alkalmazza a rendszer, amikor az alkalmazásokat munkahelyi környezetben használják; például ha a felhasználó munkahelyi fiókkal fér hozzá az alkalmazásokhoz, vagy a cég OneDrive Vállalati verzióbeli helyén tárolt fájlokhoz fér hozzá.

## <a name="access-apps"></a>Alkalmazások elérése

Ha az eszköz **nincs regisztrálva az Intune-ban**, a rendszer az alkalmazás első használatakor felkéri a felhasználót, hogy indítsa újra az alkalmazást. Az újraindítás azért szükséges, hogy a rendszer alkalmazni tudja az alkalmazásvédelmi szabályzatokat az alkalmazásra.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Az **Intune-felügyeletre regisztrált** eszközöknél üzenet jelenik meg, amely tájékoztatja a felhasználót, hogy az alkalmazás mostantól felügyelet alatt áll.

## <a name="use-apps-with-multi-identity-support"></a>A többszörös identitást támogató alkalmazások használata

A több identitást támogató alkalmazások esetében az alkalmazás különböző (munkahelyi és személyes) fiókokkal is elérhető, ilyenkor az alkalmazásvédelmi szabályzatokat csak az alkalmazások munkahelyi környezetben való használata esetén alkalmazza a rendszer.  

Például a munkahelyi adatok elérésekor a felhasználónak PIN-kódot kell megadnia. Az **Outlook alkalmazás** esetében a felhasználónak az alkalmazás indításakor kell megadnia a PIN-kódot. A **OneDrive alkalmazás** esetében a felhasználónak a munkahelyi fiók beírásakor kell megadnia a PIN-kódot.  A Microsoft **Word**, a **PowerPoint** és az **Excel** esetében a felhasználónak akkor kell megadnia a PIN-kódot, ha a vállalat OneDrive vállalati helyén tárolt dokumentumhoz szeretne hozzáférni.

- További információ azon alkalmazásokról, amelyek támogatják az [alkalmazásvédelmet és a többszörös identitást](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) az Intune-nal.

Az alkalmazásvédelmi szabályzatokat a rendszer csak a munkahelyi használat esetén alkalmazza. Ez azt jelenti, hogy az alkalmazás eltérő módon működhet, attól függően, hogy munkahelyi vagy személyes célokra használják.

## <a name="manage-user-accounts-on-the-device"></a>Felhasználói fiókok kezelése az eszközön

A többszörös identitású alkalmazások lehetővé teszik, hogy a felhasználók több fiókot is hozzáadjanak.  Az Intune APP csak egy felügyelt fiókot támogat.  Az Intune APP a felügyelt fiókok számát azonban nem korlátozza.

Ha felügyelt fiók van jelen az alkalmazásban:
* Ha a felhasználó egy második felügyelt fiókot próbál hozzáadni, akkor meg kell adnia, hogy mely felügyelt fiókot szeretné használni.  A másik fiók el lesz távolítva.
* Ha a rendszergazda egy második meglévő fiókhoz ad hozzá szabályzatot, a felhasználónak ki kell választania, hogy mely felügyelt fiókot szeretné használni.  A másik fiók el lesz távolítva.

A következő példák részletesen bemutatják, hogy a rendszer hogyan kezeli a további felhasználói fiókokat.

Az A felhasználó két vállalatnak dolgozik: az**X vállalatnak** és az **Y**vállalatnak. Az A felhasználó rendelkezik egy munkahelyi fiókkal az egyes vállalatokhoz, és mindkettő az Intune használatával telepíti az alkalmazás-védelmi szabályzatokat. Az **X vállalat** az **Y vállalat** **előtt** üzembe helyezi az alkalmazás-védelmi szabályzatokat. Az **X vállalathoz** tartozó fiók először az alkalmazás-védelmi szabályzatot kapja meg. Ha azt szeretné, hogy az alkalmazásvédelmi szabályzatok az Y vállalathoz tartozó fiókot kezeljék, akkor el kell távolítania az X vállalathoz tartozó fiókot, és hozzá kell adnia az Y vállalathoz tartozó felhasználói fiókot.

### <a name="add-a-second-account"></a>Második fiók hozzáadása

Ha iOS-eszközt használ, és egy második munkahelyi fiókot szeretne felvenni ezen az eszközön, a blokkolásról tájékoztató üzenet jelenhet meg. Megjelennek a fiókok, és Ön kiválaszthatja, hogy melyiket kívánja eltávolítani.

## <a name="next-steps"></a>További lépések
[Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](end-user-mam-apps-android.md)
