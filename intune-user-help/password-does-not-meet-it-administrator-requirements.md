---
title: A Intune Céges portál eszközök jelszavára vonatkozó követelmények | Microsoft Docs
description: Ez a cikk a szervezete által érvényesített általános jelszó-követelményeket ismerteti.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: efb3c261-1f6c-4d39-bfa4-18661f8c59c7
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9181510dad2640fcc8ea84ce2db2856bd02cbaf5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502177"
---
# <a name="device-password-requirements-for-enrolled-devices"></a>A regisztrált eszközökhöz tartozó eszköz jelszavára vonatkozó követelmények

A munkahelyi vagy iskolai erőforrásokhoz való hozzáférés engedélyezése előtt a szervezete megkövetelheti, hogy biztonságosabb jelszót hozzon létre. Ez a cikk a Windows 10, iOS, macOS és Android rendszerű eszközök gyakori jelszavas követelményeit ismerteti. Előfordulhat, hogy a szervezete nem kényszeríti ki az összes követelményt.  


Ha egy jelszó vagy PIN-kód már nem felel meg a követelménynek, a Céges portál üzenet jelenik meg. Ez a művelet leírja a szükséges módosításokat. Ha nem találhatók részletek az üzenetben, használja ezt a cikket hivatkozásként az aktuális jelszó összehasonlításához.  

> [!IMPORTANT]
> Ha módosította a jelszavát a követelmények teljesítése érdekében, de még mindig fogad értesítéseket, indítsa újra az eszközt.  

További segítségért vagy a szervezet konkrét követelményeinek megkereséséhez forduljon az informatikai támogatási szolgálathoz. Keresse meg a kapcsolattartási adatokat a [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) .  

## <a name="windows-10-password-requirements"></a>A Windows 10 jelszavára vonatkozó követelmények

| Üzenet | A hiba kijavítása |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Kötelező jelszót megadni. | Állítson be egy jelszót. A szervezetnek meg kell adnia egy jelszót az eszköz zárolásának feloldásához. |
| A jelszó túl egyszerű. |  Győződjön meg arról, hogy a jelszó nem tartalmaz szekvenciális vagy ismétlődő számokat, például 1234 vagy 1111. |
| A jelszó túl rövid.| Frissítsen vagy állítson be egy több karakterből álló jelszót. A szervezete megköveteli, hogy a jelszó bizonyos hosszúságú legyen. A ténylegesen kiválasztott elemek változhatnak, de a szükséges minimális hossz 4 karakter, a maximális érték pedig 16. |
| A jelszónak csak számokat kell tartalmaznia. | Olyan jelszót állítson be, amely csak számokat tartalmaz.|
| A jelszónak csak alfanumerikus karaktereket kell tartalmaznia. | Számok és betűk kombinációját tartalmazó jelszó beállítása.|
| A jelszónak összetett karaktereket kell tartalmaznia. | Összetett karakterek, például számok, nagybetűk és szimbólumok (például `$`, `%`és `#`) adhatók hozzá. A szervezete több betűt, számot és nem alfanumerikus karaktert is felhasználhat, hogy mások is megnehezítik a jelszó kibecslését.|  
| A jelszó lejárt. | Állítson be egy új jelszót. A szervezete megköveteli, hogy bizonyos számú nap elteltével módosítsa a jelszavát. |
| A jelszó túl nemrég lett használva. | Válassza ki a korábban még nem használt jelszót. A szervezete megköveteli, hogy a jelszó újbóli felhasználása előtt bizonyos mennyiségű időt kell megadnia. |

## <a name="ios-passcode-requirements"></a>iOS-PIN-kódokra vonatkozó követelmények

| Üzenet | A hiba kijavítása |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A PIN-kód megadása kötelező.| Állítson be egy PIN-kódot. A szervezete megköveteli az eszköz zárolásának feloldásához szükséges PIN-kód megadását. |
| A PIN-kód túl egyszerű. |  Győződjön meg arról, hogy a PIN-kód nem tartalmaz szekvenciális vagy ismétlődő számokat, például 1234 vagy 1111. |
| A PIN-kód túl rövid. | Frissítsen vagy állítson be egy több karaktert tartalmazó PIN-kódot. A szervezete megköveteli, hogy a PIN-kód egy bizonyos hosszúságú legyen. A ténylegesen kiválasztott elemek változhatnak, de a szükséges minimális hossz 4 karakter, a maximum pedig 14. A PIN-kód módosításakor előfordulhat, hogy az Apple felszólítja, hogy adjon meg 6 vagy több karaktert. Ez az üzenet egy Apple System-javaslat. Ha a szervezetnek csak 4 vagy 5 karakterből álló PIN-kódot kell megadnia, akkor nem szükséges 6 számjegyű PIN-kódot beírnia.|  
| A PIN-kódnak csak számokat kell tartalmaznia. | Olyan PIN-kódot állítson be, amely csak számokat tartalmaz.|
| A PIN-kódnak csak alfanumerikus karaktereket kell tartalmaznia.| Számok és betűk kombinációját tartalmazó PIN-kód beállítása.|
| A PIN-kódnak nem alfanumerikus karaktereket kell tartalmaznia. | Speciális karakterek (például `&`, `!`, `$`, `%`és `#`) hozzáadása. A szervezete több betűt, számot és nem alfanumerikus karaktert is felhasználhat, hogy mások is megnehezítik a PIN-kód kibecslését.|
| A PIN-kód lejárt. | Állítson be egy új jelszót. A szervezete megköveteli, hogy bizonyos számú nap elteltével módosítsa a jelszavát. |
| A PIN-kódot a közelmúltban használták.| Válassza ki a korábban még nem használt PIN-kódot. A szervezete megköveteli, hogy a PIN-kód újbóli felhasználása előtt egy bizonyos ideig elhaladjon. |
|A Touch ID vagy a Face ID hitelesítés szükséges. | Állítsa be a Touch ID-t vagy a Face ID-t. A szervezete megköveteli, hogy a fenti módszerek egyikével hitelesítse magát, mielőtt a jelszavakat vagy a hitelkártya-adatokat használja. | 

## <a name="macos-password-requirements"></a>macOS-jelszóra vonatkozó követelmények
| Üzenet | A hiba kijavítása |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Kötelező jelszót megadni. | Állítson be egy jelszót. A szervezetnek meg kell adnia egy jelszót az eszköz zárolásának feloldásához. |
| A jelszó túl egyszerű.|  Győződjön meg arról, hogy a jelszó nem tartalmaz szekvenciális vagy ismétlődő számokat, például 1234 vagy 1111. |
| A jelszó túl rövid. | Frissítsen vagy állítson be egy több karakterből álló jelszót. A szervezete megköveteli, hogy a jelszó bizonyos hosszúságú legyen.|
| A jelszónak csak számokat kell tartalmaznia. | Olyan jelszót állítson be, amely csak számokat tartalmaz.|
| A jelszónak csak alfanumerikus karaktereket kell tartalmaznia. | Számok és betűk kombinációját tartalmazó jelszó beállítása.|
| A jelszónak nem alfanumerikus karaktereket kell tartalmaznia. | Speciális karakterek (például `&`, `!`, `$`, `%`és `#`) hozzáadása. A szervezete több betűt, számot és nem alfanumerikus karaktert is felhasználhat, hogy mások is megnehezítik a jelszó kibecslését.|
| A jelszó lejárt. | Állítson be egy új jelszót. A szervezete megköveteli, hogy bizonyos számú nap elteltével módosítsa a jelszavát. |
| A jelszó túl nemrég lett használva. | Válassza ki a korábban még nem használt jelszót. A szervezete megköveteli, hogy a jelszó újbóli felhasználása előtt bizonyos mennyiségű időt kell megadnia. |

## <a name="android-password-requirements"></a>Az Android-jelszóra vonatkozó követelmények
| Üzenet | A hiba kijavítása |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Kötelező jelszót megadni. | Jelszó vagy PIN-kód beállítása. A szervezetnek meg kell adnia egy jelszót az eszköz zárolásának feloldásához. |
| A jelszó túl egyszerű. |  Győződjön meg arról, hogy a jelszó vagy a PIN-kód nem tartalmaz szekvenciális vagy ismétlődő számokat, például 1234 vagy 1111. |
| A jelszó túl rövid. | Frissítsen vagy állítson be egy több karakterből álló jelszót. A szervezete megköveteli, hogy a jelszó bizonyos hosszúságú legyen.|
| A jelszónak számokat kell tartalmaznia. | Számokat tartalmazó jelszó vagy PIN-kód beállítása.|
| A jelszónak betűket kell tartalmaznia. | Olyan jelszót állítson be, amely az ábécéből származó betűket tartalmaz.|
| A jelszónak alfanumerikus karaktereket kell tartalmaznia. | Számok és betűk kombinációját tartalmazó jelszó beállítása.|
| A jelszónak alfanumerikus karaktereket és szimbólumokat kell tartalmaznia. | Olyan jelszót állítson be, amely betűk, számok és speciális karakterek (például `&`, `!`, `$`, `%`és `#`) kombinációját tartalmazza. |
| A jelszónak biometrikus technológiát kell használnia.| Állítsa be az eszközt biometrikus hitelesítés, például ujjlenyomat vagy Arcfelismerés használatára.
| A jelszó lejárt. | Állítson be egy új jelszót. A szervezete megköveteli, hogy bizonyos számú nap elteltével módosítsa a jelszavát. |
| A jelszó túl nemrég lett használva. | Válassza ki a korábban még nem használt jelszót. A szervezete megköveteli, hogy a jelszó újbóli felhasználása előtt bizonyos mennyiségű időt kell megadnia. |

## <a name="next-steps"></a>További lépések

Az eszköz jelszavának, PIN-kódjának vagy PIN-kódjának létrehozásához vagy módosításához tekintse meg a következő cikkeket.  

- [Windows 10-es eszköz jelszavának beállítása](set-or-change-your-password-windows.md)  
- [IOS-eszköz PIN-kódának beállítása](set-or-change-your-passcode-ios.md)  
- [Android-eszköz PIN-kódjának vagy jelszavának beállítása](set-your-pin-or-password-android.md)  

További segítségre van szüksége? Forduljon a támogatási személyhez. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  


