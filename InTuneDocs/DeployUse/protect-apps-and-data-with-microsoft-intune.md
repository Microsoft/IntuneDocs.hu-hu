---
title: "Alkalmazások és adatok védelme | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ded7bd6c971a9448ad6e6492ebc5e42dfcb5d76e
ms.openlocfilehash: 9445b4b171eb2102d73cf0e866e85b535274eee2


---

# Alkalmazások és adatok védelme a Microsoft Intune-nal


Az Intune a vállalati adatokat több technológiai réteg segítségével védi.  Az identitáskezelő rétegben a feltételes hozzáférés gondoskodik a védelemről: a szolgáltatásokhoz csak felügyelt, illetve a szabályoknak megfelelő eszközökkel lehet hozzáférni.  Az ügyfél-alkalmazási rétegben a mobilalkalmazás-kezelés (MAM) gondoskodik az adatvesztés elleni védelemről. Ennek részeként megakadályozza az adatok nem védett alkalmazásokba vagy tárhelyekre történő áthelyezését, illetve az eszköz elvesztése vagy ellopása esetén törli az adatokat.  Az adatvédelem megvalósítása mellett a mobil munkaerő termelékenységének megőrzése érdekében e két védelmi réteget együttesen kell használni.

A vállalati adatok védelmének fontos kezdőlépése a feltételes hozzáférés alkalmazása. Ez azt garantálja, hogy a védendő adatok eléréséhez használt eszközök biztonsági védelmet, például erős jelszót, titkosítást használjanak, és ne legyenek függetlenítve. A Microsoft Intune lehetőséget biztosít olyan feltételek megadására, amelyeknek az eszközöknek meg kell felelniük ahhoz, hogy hozzáférést kapjanak a vállalati e-mailekhez és adatokhoz.

A [feltételes hozzáférést](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) két, az Intune-ban megadható szabályzattípus határozza meg:
- A [Megfelelőségi szabályzatok](introduction-to-device-compliance-policies-in-microsoft-intune.md) határozzák meg az eszközök megfelelőségét. A következőkhöz hasonló beállításokat és feltételeket értékelik ki:
  - PIN-kód és jelszavak: Létrehozhatók olyan szabályok, amelyek jelszót kérnek egy adott eszköz feloldásához, vagy a jelszó összetettségi követelményeit és egyéb jelszó-beállításokat adnak meg.
  - Titkosítás: A hozzáférés a titkosított eszközökre korlátozható.
  - Az eszköz nincs függetlenítve vagy feltörve: Az Intune észleli, ha egy regisztrált eszköz függetlenítve van, így beállítható egy szabályzat az ilyen típusú eszközök hozzáférésének letiltására.
- [Feltételes hozzáférési szabályzatok](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) egy adott szolgáltatáshoz állíthatók be, például az Exchange Online vagy a SharePoint Online számára. Minden egyes szolgáltatás esetében meghatározhatja, hogy a házirendek melyik felhasználói csoportokra vonatkozzon. Biztosíthatja például, hogy a pénzügyi részleg dolgozói csak a regisztrált és a házirendeknek megfelelő eszközökről férhessenek hozzá a vállalati e-mailekhez.

A vállalati erőforrásokhoz való hozzáférés biztosítása csak első lépése a vállalati adatok védelmének. Arra is szükség van, hogy az eszközön már elért adatokat is meg lehessen védeni. Az adatok ezután már másolhatók, áthelyezhetők, másik helyre menthetők vagy megoszthatók. Az Intune ezt a problémát azáltal oldja meg, hogy lehetővé teszi az adatmozgás korlátozását szabályzatok létrehozásával, például:
- A másolás és a beillesztés letiltása, vagy a munkahelyi környezeten kívülre történő adatátvitel megakadályozása
- A személyes felhőalapú tárhelyre készített biztonsági mentés letiltása, a Mentés másként parancs letiltása
- Az alkalmazások elérésének védelme PIN-kód/jelszó vagy vállalati hitelesítő adatok kérésével
- Webes hivatkozások megnyitása kizárólag az Intune Managed Browser böngészőben

A szabályzatoknak ezt a csoportját [mobilalkalmazás-felügyeleti (MAM) szabályzatoknak](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) nevezzük.  A MAM-szabályzatok alkalmazhatók a felügyelt és a nem felügyelt eszközökön futó alkalmazásokra is.  A vállalati adatok védelme érdekében a MAM-szabályzatok alkalmazhatók az Intune-ban regisztrált eszközökön, a más külső féltől származó MDM által regisztrált és felügyelt eszközökön, illetve olyan eszközökön, amelyeket esetleg nem Ön felügyel, például az alkalmazotti tulajdonú eszközökön.

Ahhoz, hogy egy alkalmazáshoz MAM-szabályzat legyen társítható, az alkalmazásnak tartalmaznia kell a Microsoft Intune szoftverfejlesztői készletet (SDK), vagy használnia kell az alkalmazásburkoló eszközt.

Egyes alkalmazások, mint például a Microsoft Office beépítve tartalmazzák az alkalmazásfejlesztő készletet (SDK-t). A támogatott alkalmazások teljes listája a Microsoft Intune alkalmazáspartnerek oldalán, a [Microsoft Intune mobilalkalmazás-galériában](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) található. Ha szeretné megtekinteni a támogatott forgatókönyveket, platformokat, illetve, hogy az alkalmazás támogatja-e a többszörös identitást, válassza ki az adott alkalmazást.

[Egyéni kialakítású üzleti alkalmazásait](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) is alkalmassá teheti a MAM-szabályzatokkal való használatra.

Ha egy eszközt elveszítenek vagy ellopnak, vagy ha a felhasználó már nem dolgozik a vállalatnál, akkor az adatmozgás korlátozása mellett alkalmazható [a vállalati adatok szelektív törlése](wipe-managed-company-app-data-with-microsoft-intune.md), ami csak a személyes adatokat hagyja meg.



<!--HONumber=Jun16_HO4-->


