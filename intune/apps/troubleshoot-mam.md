---
title: Mobilalkalmazás-kezelési hibaelhárítás
titleSuffix: Microsoft Intune
description: Ez a témakör néhány hibaelhárítási tippet ismertet a feltételes hozzáférés központi telepítéséhez.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43fd8207a07f64fd293eb9c90bbfc2a8dadd9157
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72489936"
---
# <a name="troubleshoot-mobile-application-management"></a>Mobilalkalmazás-kezelési hibaelhárítás

Ez a témakör a Intune App Protection (más néven MAM vagy Mobile Application Management) használatakor bekövetkezett gyakori problémák megoldásait ismerteti.

Ha ezekkel az információkkal nem tudja megoldani a problémát, a következő témakörben talál további részleteket a segítségkéréshez: [Hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md).

## <a name="common-it-administrator-issues"></a>A rendszergazdáknál gyakran előforduló problémák

Ezek olyan gyakori problémák, amikor a rendszergazda az Intune app Protection-szabályzatok használata során felmerülhet.

| Probléma | Description | Megoldás |
| -- | -- | -- |
| A Skype Vállalati verzióra nem vonatkozó szabályzat | Az Azure Portalon beállított, eszközregisztráció nélküli alkalmazásvédelmi szabályzat nem lép életbe az iOS- és Android-eszközökön futó Skype Vállalati verzió alkalmazásra vonatkozóan. | A Skype Vállalati verziót a modern hitelesítésre kell beállítani.  Kövesse a [Bérlő engedélyezése modern hitelesítéshez](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) című részben található utasításokat a modern hitelesítés beállításához Skype-hoz. |
| Nem alkalmazott Office-alkalmazás-szabályzat | Az alkalmazásvédelmi szabályzatok egyetlen felhasználónál sem lépnek életbe a [támogatott Office-alkalmazásokra](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) vonatkozóan. | Ellenőrizze, hogy a felhasználók rendelkeznek-e Intune-licenccel, illetve, hogy a használt alkalmazásvédelmi szabályzat megcélozza-e az Office-alkalmazásokat. Az újonnan beállított alkalmazásvédelmi szabályzatok életbe lépéséhez esetenként 8 órának is el kell telnie. |
| A rendszergazda nem tudja beállítani az alkalmazásvédelmi szabályzatot az Azure Portalon | A rendszergazda felhasználó nem tudja konfigurálni az alkalmazás-védelmi szabályzatokat a Azure Portalban. | A következő felhasználói szerepkörök rendelkeznek hozzáféréssel a Azure Portalhoz: <ul><li>Globális rendszergazda, amely beállítható a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com/)</li><li>A tulajdonos, amelyet beállíthat a [Azure Portalban](https://portal.azure.com/).</li><li>Közreműködő, amely beállítható a [Azure Portalban](https://portal.azure.com/).</li></ul> A szerepkörök beállításához tekintse meg a [szerepköralapú adminisztrációs vezérlő (RBAC)](../fundamentals/role-based-access-control.md) című témakört Microsoft Intune segítségével.|
|Az alkalmazásvédelmi szabályzat jelentéseiből hiányzó felhasználói fiókok | A felügyeleti konzol jelentéseiben nem szerepelnek azok a felhasználói fiókok, amelyekre a közelmúltban alkalmazták az alkalmazásvédelmi szabályzatot. | Az alkalmazásvédelmi szabályzattal újonnan megcélzott felhasználók esetében előfordul, hogy 24 órának is el kell telnie, hogy a felhasználó megjelenjen a jelentésekben. |
| Nem működő szabályzatváltozások | Az alkalmazásvédelmi szabályzatokat érintő változások és frissítések életbe lépéséhez akár 8 órára is szükség lehet. | Ha alkalmazandó, a végfelhasználó jelentkezzen ki az alkalmazásból, majd jelentkezzen be újra, ezzel kényszerítve a szinkronizálást a szolgáltatással. |
| Az alkalmazásvédelmi szabályzat nem működik a DEP-pel | Az alkalmazásvédelmi szabályzat nem lép érvénybe az Apple DEP-eszközökön. | Győződjön meg róla, hogy használja-e a Felhasználói affinitás funkciót az Apple Eszközregisztrációs programmal (DEP). Felhasználói affinitásra minden olyan alkalmazás esetében szükség van, amely felhasználói hitelesítést igényel DEP alatt. <br><br>Az iOS DEP-regisztrációval kapcsolatos további információkért tekintse meg az [iOS-eszközök automatikus regisztrálása az Apple Készülékregisztrációs programban](../enrollment/device-enrollment-program-enroll-ios.md) című témakört.|
| Az adatátviteli szabályzat nem működik iOS-szel | A **Más alkalmazásokból való adatátvitel engedélyezése az alkalmazásnak** és a **Más alkalmazásokból való adatfogadás engedélyezése az alkalmazásnak** szabályzatok nem tudják kezelni az adatátvitelt az iOS-ben. | Lásd: az [iOS-alkalmazások közötti adatátvitel kezelése Microsoft Intuneban](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>A végfelhasználóknál előforduló gyakori problémák

A végfelhasználóknál előforduló gyakori problémák a következő kategóriákba sorolhatók:

* **Normál használati forgatókönyvek**: a végfelhasználók az Intune app Protection-szabályzattal rendelkező alkalmazásokban előfordulhatnak ilyen forgatókönyvek. Ezek nem tényleges problémákat, de problémának vagy hibáknak tűnhetnek.

* **Normál használati párbeszédablakok**: ezek a használati párbeszédpanelek a végfelhasználók számára az Intune app Protection-szabályzattal rendelkező alkalmazásokban jelenhetnek meg. Ezeket az üzeneteket és párbeszédpanelek **nem** hibát jeleznek.

* **Hibaüzenetek és párbeszédpanelek**: ezek azok a hibaüzenetek és párbeszédpanelek, amelyekben a végfelhasználók az Intune app Protection-szabályzattal rendelkező alkalmazásokban jelenhetnek meg. Ezek gyakran a rendszergazda által elkövetett hibát jeleznek, vagy az Intune-alkalmazásvédelem hibáját.

### <a name="normal-usage-scenarios"></a>Normál használati forgatókönyvek

Platfésm | Forgatókönyv | Magyarázat |
---| --- | --- |
iOS | A végfelhasználó az iOS megosztási bővítménnyel megnyithatja a munkahelyi vagy az iskolai adatokat a nem felügyelt alkalmazásokban, még akkor is, ha az adatátviteli szabályzat beállítása **Csak felügyelt alkalmazások** vagy **Nincs alkalmazás**. Nem jár ez adatszivárgással? | Az Intune alkalmazásvédelmi szabályzata nem tudja kezelni az iOS megosztási bővítményt az eszköz felügyelete nélkül. Ezért az **Intune titkosítja a „céges” adatokat, mielőtt az alkalmazáson kívül megosztaná**. Ezt úgy ellenőrizheti, hogy megpróbálja megnyitni a „céges” fájlt a felügyelt alkalmazáson kívüli más alkalmazással. A fájlnak titkosítottnak kell lennie, így nem nyitható meg a felügyelt alkalmazáson kívül mással.
iOS | Miért kéri a végfelhasználó **a Microsoft Authenticator alkalmazás telepítését** . | Erre akkor van szükség, ha alkalmazás-alapú feltételes hozzáférés van alkalmazva. lásd: [jóváhagyott ügyfélalkalmazás megkövetelése](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access).
Android: | Miért kell a végfelhasználónak akkor is **telepítenie a Céges portál alkalmazást**, ha MAM-alkalmazásvédelmet használok eszközregisztráció nélkül?  | Androidon a legtöbb alkalmazásvédelmi funkció be van építve a Céges portál alkalmazásba. **Annak ellenére, hogy a Céges portál alkalmazás mindig szükséges, eszközregisztrációra nincs szükség**. A regisztráció nélküli alkalmazásvédelemhez a végfelhasználónak telepítenie kell a Céges portál alkalmazást az eszközre.
iOS/Android | Nem alkalmazták az alkalmazás-védelmi szabályzatot az Outlook alkalmazásban az e-mailek piszkozatára | Mivel az Outlook a vállalati és a személyes kontextust is támogatja, nem kényszeríti ki a MAM-t az e-mailek piszkozatára.
iOS/Android | Az alkalmazás-védelmi szabályzat nem lett alkalmazva az új dokumentumokra a WXP (Word, Excel, PowerPoint) | Mivel a WXP támogatja mind a vállalati, mind a személyes környezetet, nem kényszeríti ki a MAM-t az új dokumentumokra, amíg azokat egy azonosított vállalati helyre nem mentik, mint például a OneDrive.
iOS/Android | Az alkalmazások nem engedélyezik a helyi tárterületre való mentést, ha a házirend engedélyezve van | Ennek a beállításnak az alkalmazási viselkedését az alkalmazás fejlesztője vezérli.
Android: | Az Android több korlátozással rendelkezik, mint az iOS, amit a "natív" alkalmazások hozzáférhetnek a MAM által védett tartalmakhoz | Az Android egy nyílt platform, a "natív" alkalmazás-társítás pedig a végfelhasználó által potenciálisan nem biztonságos alkalmazások számára módosítható. Az [adatátviteli szabályzat kivételeit](app-protection-policies-exception.md) alkalmazza az adott alkalmazások alól.
Android: | A Azure Information Protection (központilag) mentheti PDF-ként, ha a Mentés másként lehetőség meg van akadályozva | Az a (z) a "nyomtatás letiltása" nevű MAM-szabályzat kitüntetése, ha a Mentés PDF-ként elem szerepel.
iOS | A PDF-mellékletek megnyitása az Outlook alkalmazásban meghiúsul "a művelet nem engedélyezett | Ez akkor fordulhat elő, ha a felhasználó nem hitelesítette az Intune-hoz készült Acrobat Readert, vagy az ujjlenyomat használatával hitelesíti a szervezetét. Először nyissa meg az Acrobat Readert, és hitelesítse magát az UPN hitelesítő adataival.


### <a name="normal-usage-dialogs"></a>Normál használati párbeszédpanelek

Platfésm | Üzenet vagy párbeszédpanel | Magyarázat |
--- | --- | --- |
iOS, Android | **Bejelentkezés**: Az adatok védelme érdekében a munkahelyének felügyelnie kell ezt az alkalmazást. A művelet befejezéséhez jelentkezzen be a munkahelyi vagy az iskolai fiókjába. | A végfelhasználónak be kell jelentkeznie a munkahelyi vagy iskolai fiókjával az alkalmazás használatához, amelyhez egy alkalmazás-védelmi szabályzat szükséges. Ahhoz, hogy a szabályzat érvényes legyen, a felhasználónak hitelesítenie kell Azure Active Directory.
iOS, Android |**Újraindítás szükséges**: A munkahelye most már védi az adatait ebben az alkalmazásban. A folytatáshoz újra kell indítania az alkalmazást. | Az alkalmazás nemrég kapott egy Intune app Protection-szabályzatot, és újra kell indítani ahhoz, hogy a szabályzat érvényes legyen.
iOS, Android |**Nem engedélyezett művelet**: A szervezete csak munkahelyi vagy iskolai adatok megnyitását engedélyezi ebben az alkalmazásban. | A rendszergazda a **Más alkalmazásokból való adatfogadás engedélyezése az alkalmazásnak** beállításaként a **Csak felügyelt alkalmazások** lehetőséget adta meg. Ezért a végfelhasználó csak olyan alkalmazásokból vihet át adatátvitelt az alkalmazásba, amelyek rendelkeznek alkalmazás-védelmi házirenddel.
iOS, Android |**Nem engedélyezett művelet**: A munkahelye adatait csak felügyelt alkalmazásokba viheti át. | A rendszergazda **Az alkalmazás átadhat adatokat más alkalmazásoknak** beállításaként a **Csak felügyelt alkalmazások** lehetőséget adta meg. Ezért a végfelhasználó csak az alkalmazásból származó adatok átvitelét végezheti el az alkalmazás-védelmi szabályzattal rendelkező más alkalmazásokba.
iOS, Android |**Törlési riasztás**: A munkahelye törölte az alkalmazáshoz hozzárendelt adatokat. A folytatáshoz indítsa újra az alkalmazást. | A rendszergazda az Intune alkalmazásvédelmi funkciójával kezdeményezte az alkalmazástörlés.
Android: | **Céges portál szükséges**: Csak akkor használhatja a munkahelyi vagy iskolai fiókját ebben az alkalmazásban, ha telepíti az Intune Céges portál alkalmazást. A folytatáshoz kattintson az "Ugrás az áruházba" gombra. | Androidon a legtöbb alkalmazásvédelmi funkció be van építve a Céges portál alkalmazásba. **Annak ellenére, hogy a Céges portál alkalmazás mindig szükséges, eszközregisztrációra nincs szükség**. A regisztráció nélküli alkalmazásvédelemhez a végfelhasználónak telepítenie kell a Céges portál alkalmazást az eszközre.

### <a name="error-messages-and-dialogs-on-ios"></a>Hibaüzenetek és párbeszédpanelek az iOS-ben

Hibaüzenet vagy párbeszédpanel | Ok | Kockázatcsökkentés |
-- | --- | --- |
**Nincs beállítva az alkalmazás**: Ez az alkalmazás nincs beállítva az Ön általi használatra. Segítségért forduljon a rendszergazdához. | Nem sikerült felderíteni az alkalmazáshoz szükséges alkalmazás-védelmi szabályzatot. |Léptessen életbe egy iOS-es alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az alkalmazást.
**Üdvözli Önt az Intune Managed Browser**: Ez az alkalmazás akkor működik optimálisan, ha a Microsoft Intune felügyeli. Bármikor böngészheti vele az internetet. Ha az alkalmazást a Microsoft Intune felügyeli, további adatbiztonsági funkciókat is elérhet. | Nem sikerült felderíteni a Intune Managed Browser alkalmazáshoz szükséges alkalmazás-védelmi szabályzatot. <br><br>A felhasználó ebben az esetben is internetezhet, de az alkalmazást nem az Intune fogja felügyelni. | Léptessen életbe egy iOS-es alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az Intune Managed Browser alkalmazást.
**A bejelentkezés sikertelen**: Nem tudtuk bejelentkeztetni. Próbálkozzon újra később. | Nem sikerült regisztrálni a felhasználót a MAM-szolgáltatásban, miután a felhasználó megpróbált munkahelyi vagy iskolai fiókjával bejelentkezni. | Léptessen életbe egy iOS-es alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az alkalmazást.
**A fiók nincs beállítva**: A szervezete nem állította be a fiókját a munkahelyi vagy iskolai adatok elérésére. Kérjen segítséget a rendszergazdától. | A felhasználói fiókhoz nem tartozik Intune A Direct-licenc. | Ellenőrizze, hogy a felhasználó fiókja rendelkezik-e Intune-licenccel a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com).
**Nem felel meg az eszköz**: Nem használhatja az alkalmazást, mert ez egy feltört eszköz. Segítségért forduljon a rendszergazdához. | Az Intune észlelte, hogy a felhasználó feltört eszközt használ. | Állítsa vissza az eszköz gyári alapbeállításait. Kövesse az Apple támogatói webhelyén található [utasításokat](https://support.apple.com/HT201274).
**Internetkapcsolat szükséges**: Az alkalmazáshasználati jogosultsága ellenőrzéséhez internetkapcsolatra van szükség. | Az eszközön nincs internetkapcsolat. | Csatlakoztassa az eszközt egy Wi-Fi- vagy adathálózathoz.
**Ismeretlen hiba**: Próbálja meg újraindítani az alkalmazást. Ha nem szűnik meg a probléma, kérjen segítséget a rendszergazdától. | Ismeretlen hiba történt. | Próbálkozzon újra egy kis idő elteltével. Ha a hiba továbbra is fennáll, hozzon létre egy [támogatási jegyet](../fundamentals/get-support.md#create-an-online-support-ticket) az Intune-nal.
**Hozzáférés a szervezet adataihoz**: A megadott munkahelyi vagy iskolai fióknak nincs hozzáférése ehhez az alkalmazáshoz. Lehetséges, hogy másik fiókkal kell bejelentkeznie. Segítségért forduljon a rendszergazdához. | Az Intune észlelte, hogy a felhasználó egy második, az eszközön a MAM-mal regisztrált fióktól eltérő munkahelyi vagy iskolai fiókkal próbál bejelentkezni. A MAM egyszerre csak egy munkahelyi vagy iskolai fiókot képes kezelni egy eszközön. | A felhasználó jelentkezzen be azzal a fiókkal, amelynek felhasználóneve megjelenik a bejelentkezési képernyőn. Előfordulhat, hogy [konfigurálnia kell a felhasználói UPN-beállítást az Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)-hoz. <br> <br> Vagy jelentkezzen be az új munkahelyi vagy iskolai fiókkal, és távolítsa el a MAM-mal jelenleg regisztrált fiókot.
**Csatlakozási probléma**: Váratlan csatlakozási probléma lépett fel. Ellenőrizze a kapcsolatot, majd próbálkozzon újra.  |  Váratlan hiba. | Próbálkozzon újra egy kis idő elteltével. Ha a hiba továbbra is fennáll, hozzon létre egy [támogatási jegyet](../fundamentals/get-support.md#create-an-online-support-ticket) az Intune-nal.
**Riasztás**: Ez az alkalmazás már nem használható. További információért forduljon a rendszergazdához. | Nem sikerült ellenőrizni az alkalmazás tanúsítványának érvényességét. | Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Telepítse újra az alkalmazást.
**Hiba**: Az alkalmazás problémát észlelt, ezért leáll. Ha nem szűnik meg a probléma, forduljon a rendszergazdához. | Nem sikerült beolvasni a MAM-alkalmazás PIN kódját az Apple iOS kulcsláncából. | Indítsa újra az eszközt. Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Telepítse újra az alkalmazást.

### <a name="error-messages-and-dialogs-on-android"></a>Hibaüzenetek és párbeszédpanelek az Androidban

Párbeszédpanel/hibaüzenet | Ok | Kockázatcsökkentés |
-- | --- | --- |
**Nincs beállítva az alkalmazás**: Ez az alkalmazás nincs beállítva az Ön általi használatra. Segítségért forduljon a rendszergazdához. | Nem sikerült felderíteni az alkalmazáshoz szükséges alkalmazás-védelmi szabályzatot. |Léptessen életbe egy Andoridos alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az alkalmazást.
**Failed app launch** (Alkalmazás indítása sikertelen): Hiba történt az alkalmazás indításakor. Próbálja meg frissíteni az alkalmazást vagy az Intune Munkahelyi portál alkalmazást. Ha segítségre van szüksége, lépjen kapcsolatba a rendszergazdával. | Az Intune észleli az alkalmazásra vonatkozó érvényes alkalmazásvédelmi szabályzatot, de az alkalmazás összeomlik a MAM inicializálása során. | Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Ellenőrizze, hogy telepítve van-e az eszközön az Intune Munkahelyi portál alkalmazás, és hogy naprakész-e. <br><br> Ha a hiba továbbra is fennáll, használja a Céges portál alkalmazást, hogy naplókat küldjön az Intune-nak, vagy hozzon létre egy [támogatási jegyet](../fundamentals/get-support.md#create-an-online-support-ticket).
**Nem találhatók alkalmazások**: Ezen az eszközön nem található olyan alkalmazás, amellyel munkahelye engedélyezné a tartalom megnyitását. Segítségért forduljon a rendszergazdához. | A felhasználó munkahelyi vagy iskolai adatokat próbált meg megnyitni egy másik alkalmazásban, de az Intune nem talált olyan más felügyelt alkalmazást, amely jogosult az adatok megnyitására. | Állítson be egy androidos alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozzon meg vele legalább egy másik MAM-kompatibilis alkalmazást, amely alkalmas a kérdéses adatok megnyitására.
**A bejelentkezés sikertelen**: Próbáljon meg újra bejelentkezni. Ha nem szűnik meg a probléma, kérje a rendszergazda segítségét. | Nem sikerült hitelesíteni a fiókot, amellyel a felhasználó megpróbál bejelentkezni. | A felhasználó azzal a munkahelyi vagy iskolai fiókkal jelentkezzen be, amely már regisztrálva van az Intune MAM-szolgáltatásában (ez az első munkahelyi vagy iskolai fiók, amellyel sikeresen bejelentkezett ebbe az alkalmazásba). <br><br> Törölje az alkalmazásadatokat. <br><br> Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Ellenőrizze, hogy a Munkahelyi portál alkalmazás naprakész verzióját használja-e.
**Internetkapcsolat szükséges**: Az alkalmazáshasználati jogosultsága ellenőrzéséhez internetkapcsolatra van szükség. | Az eszközön nincs internetkapcsolat. | Csatlakoztassa az eszközt egy Wi-Fi- vagy adathálózathoz.
**Nem felel meg az eszköz**: Nem használhatja az alkalmazást, mert ez egy feltört eszköz. Segítségért forduljon a rendszergazdához. | Az Intune észlelte, hogy a felhasználó feltört eszközt használ. | Állítsa vissza az eszköz gyári alapbeállításait.
**A fiók nincs beállítva**: Ezt az alkalmazást a Microsoft Intune-nak kell kezelnie, de az Ön fiókja még nincs beállítva. Segítségért forduljon a rendszergazdához. | A felhasználói fiókhoz nem tartozik Intune A Direct-licenc. | Ellenőrizze, hogy a felhasználó fiókja rendelkezik-e Intune-licenccel a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com).
**Unable to register the app** (Nem sikerült regisztrálni az alkalmazást): Ezt az alkalmazást a Microsoft Intune-nak kell kezelnie, de ezúttal nem sikerült azt regisztrálni. Segítségért forduljon a rendszergazdához. | Nem sikerült automatikusan regisztrálni az alkalmazást a MAM-szolgáltatásban, pedig alkalmazásvédelmi szabályzatra van szükség. | Törölje az alkalmazásadatokat. <br><br> Naplókat küldhet az Intune-nak a Céges portál alkalmazáson keresztül, vagy egy támogatási jegyet. További információkért lásd: [a Microsoft Intune támogatásának beszerzése](../fundamentals/get-support.md).

## <a name="next-steps"></a>További lépések

- [A mobilalkalmazás-kezelés beállításának ellenőrzése](app-protection-policies-validate.md)
- Ismerje meg, hogyan használhatók a naplófájlok Intune App Protection szabályzattal kapcsolatos hibák megoldásához: [https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372)
- További információt az Intune hibaelhárításáról a [Segítségnyújtás a céges felhasználóknak a hibaelhárítási portál használatával](../fundamentals/help-desk-operators.md) című témakörben talál. 
- Ismertető a Microsoft Intune esetleges ismert problémáiról. További információt [Az Intune ismert problémái](../known-issues.md) című témakörben talál.
- További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md).
