---
title: iOS-alkalmazások alkalmazásvédelmi szabályzatokkal
description: Ez a témakör azt ismerteti, hogy milyen hatással vannak az iOS-alkalmazásokra az alkalmazásvédelmi szabályzatok.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606621"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Milyen hatással vannak az iOS-alkalmazásokra az alkalmazásvédelmi szabályzatok?

Az Intune app Protection-szabályzatok a munkahelyi vagy iskolai használatra használt alkalmazásokra vonatkoznak. Ez azt jelenti, hogy ha az alkalmazottak és a tanulók személyes környezetben használják az alkalmazásaikat, akkor a saját tapasztalataikban nem tapasztalnak különbséget. A munkahelyi vagy iskolai kontextusban azonban kéréseket kaphatnak a fiókok döntéseinek meghozatalához, a beállítások frissítéséhez vagy a segítségért való kapcsolatfelvételhez. Ebből a cikkből megtudhatja, hogy a felhasználók milyen élményt nyújtanak, amikor megpróbálnak hozzáférni és használni az Intune által védett alkalmazásokat.  

## <a name="access-apps"></a>Alkalmazások elérése

Ha az eszköz **nincs regisztrálva az Intune-ban**, a rendszer az alkalmazás első használatakor felkéri a felhasználót, hogy indítsa újra az alkalmazást. Újraindításra van szükség, hogy az alkalmazásra vonatkozó adatvédelmi szabályzatok alkalmazhatók legyenek az alkalmazásra.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Az **Intune-felügyeletre regisztrált** eszközöknél üzenet jelenik meg, amely tájékoztatja a felhasználót, hogy az alkalmazás mostantól felügyelet alatt áll.

## <a name="use-apps-with-multi-identity-support"></a>A többszörös identitást támogató alkalmazások használata

A többszörös identitást támogató alkalmazások lehetővé teszik, hogy különböző munkahelyi és személyes fiókokat használjanak ugyanazon alkalmazások eléréséhez. Az alkalmazás-védelmi szabályzatok, például az eszköz PIN-kódjának beírása akkor aktiválódik, ha a felhasználók munkahelyi vagy iskolai környezetben férnek hozzá ezekhez az alkalmazásokhoz.   

A felhasználók az összes alkalmazásban különbözőképpen használhatják a PIN-kódot, attól függően, hogyan konfigurálja a szabályzatokat.  Például beállíthatja a szabályzatokat úgy, hogy:       
* A Microsoft Outlook PIN-kódot kér a felhasználótól az alkalmazás indításakor. 
* A OneDrive megkéri a felhasználót a PIN-kód megadására, amikor bejelentkeznek a munkahelyi fiókjába.  
* A Microsoft Word, a PowerPoint és az Excel megkéri a felhasználót a PIN-kód megadására, amikor a vállalati OneDrive a vállalati helyen tárolt dokumentumokhoz férnek hozzá.  

- További információ azon alkalmazásokról, amelyek támogatják az [alkalmazásvédelmet és a többszörös identitást](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) az Intune-nal.  

## <a name="manage-user-accounts-on-the-device"></a>Felhasználói fiókok kezelése az eszközön  

Az Intune app Protection-szabályzatok felhasználónként egy felügyelt munkahelyi vagy iskolai fiókra korlátozzák a felhasználókat. Az alkalmazás-védelmi házirendek nem korlátozzák a felhasználók által hozzáadható nem felügyelt fiókok számát.   

- Ha a felhasználó egy második felügyelt fiókot próbál hozzáadni, akkor meg kell adnia, hogy mely felügyelt fiókot szeretné használni. Ha a felhasználó hozzáadja a második fiókot, a rendszer eltávolítja az első fiókot.
- Ha védelmi szabályzatokat ad hozzá egy másik felhasználói fiókhoz, a rendszer megkéri a felhasználót, hogy válassza ki, melyik felügyelt fiókot szeretné használni. A másik fiók el lesz távolítva. 

Egyes felhasználók nem kapják meg a felügyelt fiókok közötti váltást vagy választást. A beállítás nem érhető el a következő eszközökön:
* Intune által felügyelt  
* A külső gyártótól származó nagyvállalati mobilitási megoldások felügyelik, és a IntuneMAMUPN beállítással vannak konfigurálva 

A következő példa azt ismerteti, hogyan történik több felhasználói fiók kezelése:  

Az A felhasználó két vállalatnak dolgozik: az**X vállalatnak** és az **Y**vállalatnak. Az A felhasználó rendelkezik egy munkahelyi fiókkal az egyes vállalatokhoz, és mindkettő az Intune használatával telepíti az alkalmazás-védelmi szabályzatokat. Az **X vállalat** az **Y vállalat** **előtt** üzembe helyezi az alkalmazás-védelmi szabályzatokat. Az **X vállalathoz** tartozó fiók először az alkalmazás-védelmi szabályzatot kapja meg. Ha azt szeretné, hogy az alkalmazásvédelmi szabályzatok az Y vállalathoz tartozó fiókot kezeljék, akkor el kell távolítania az X vállalathoz tartozó fiókot, és hozzá kell adnia az Y vállalathoz tartozó felhasználói fiókot.  

## <a name="next-steps"></a>További lépések

[Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](end-user-mam-apps-android.md)
