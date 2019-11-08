---
title: Milyen adatokhoz férhet hozzá a munkahelye, ha regisztrálja eszközét?
description: Ismerteti, hogy a rendszergazda mit láthat a felügyelt eszközön, és mit nem.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc50f48afbd527f3c6d82cc0c71a166b0356ab9e
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801482"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>Milyen adatok láthatók a szervezet számára, ha regisztrálom az eszközömet?

A szervezete számára nem láthatók az Ön személyes adatai, amikor eszközt regisztrál a Microsoft Intune-ban. Amikor regisztrálja eszközét, Ön engedélyezi a szervezetének bizonyos eszközadatoknak, például az eszköz típusának és sorozatszámának megtekintését. A szervezet ezt az információt az eszközön lévő vállalati adatok védelmére használja fel.

**A szervezet számára soha nem látható adatok:**

- Hívási és böngészési előzmények
- E-mailek és SMS-ek
- Névjegyek
- Naptár
- Jelszavak
- Képek, beleértve a Fényképezőgép alkalmazás vagy a Filmtekercs mappa tartalmát
- fájlokat

**A szervezet számára mindig látható adatok:**

- Eszközmodell, például Google Pixel
- Eszköz gyártója, például a Microsoft
- Operációs rendszer és annak verziója, például iOS 12.0.1
- Alkalmazás-leltár és-alkalmazások nevei, például a Microsoft Word. A személyes eszközökön a szervezet csak a felügyelt alkalmazások leltárát látja. A vállalati tulajdonú eszközökön a szervezet a teljes alkalmazásleltárat láthatja.
- Az eszköz tulajdonosa
- Eszköz neve
- Eszköz sorozatszáma
- IMEI

**A szervezet számára esetlegesen látható adatok:**

- Telefonszám: a vállalat által birtokolt eszközök esetében teljes telefonszáma látható. A személyes tulajdonú eszközök esetében csak a telefonszám utolsó négy számjegye látható a szervezet számára. Az egyes eszközök tulajdonosi típusát az **eszköz részletes** lapján tekintheti meg.
- Eszköz tárhelye: Ha nem tud telepíteni egy szükséges alkalmazást, a szervezet ellenőrizheti az eszköz tárhelyét, valamint hogy az elegendő-e.  
- Hely: a szervezet soha nem láthatja az eszköz helyét, hacsak nem kell helyreállítani egy elveszett, felügyelt iOS-eszközt. A felügyelt eszközökről további információért látogasson el az [Apple iOS dokumentációjában](https://go.microsoft.com/fwlink/?linkid=853816) .  
- Az alkalmazás leltárának részletei: Ha a szervezet a Mobile Threat Defense szolgáltatást használja, megtekintheti az iOS-eszközön lévő alkalmazások adatait. További információk: [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md). Ha rendelkezik személyes eszközzel, a szervezet csak a felügyelt alkalmazások leltárát látja. Ha rendelkezik vállalati tulajdonú eszközzel, a szervezet láthatja az összes alkalmazás leltárát.
- Hálózati adatok: az androidos eszközök hálózati kapcsolatairól bizonyos adatok elérhetőek lehetnek a szervezet informatikai részlege számára. Például ha a szervezet egyes eszközeinek egy bizonyos épületen belül kell maradniuk, az eszköz azonosítja a hálózatot, amelyhez csatlakozik. 
