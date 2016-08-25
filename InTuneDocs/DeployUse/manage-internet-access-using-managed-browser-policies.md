---
title: "Az internet-hozzáférés felügyelt böngészőszabályzatokkal való kezelése a Microsoft Intune-ban| Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 2df44199ecd904dcfb6774a942244338c1384186
ms.openlocfilehash: c4462af584d54225084159dfa35f5e1d07c36397


---

# Az internet-hozzáférés felügyelt böngészőszabályzatokkal való kezelése a Microsoft Intune-ban
A felügyelt böngésző egy webböngésző-alkalmazás, amelyet a Microsoft Intune használatával helyezhet üzembe a szervezetében. A felügyeltböngésző-szabályzatban megadható egy engedélyezési vagy blokklista, amellyel korlátozhatók a felügyelt böngésző felhasználói által felkereshető webhelyek.

Mivel az alkalmazás felügyelt alkalmazás, mobilalkalmazás-felügyeleti szabályzatokat is alkalmazhat az alkalmazásra, például szabályozhatja a kivágási, másolási és beillesztési műveleteket, megakadályozhatja a képernyőfelvételek készítését, és gondoskodhat arról, hogy azok a tartalmak, amelyek hivatkozásaira a felhasználók kattintanak, csak más felügyelt alkalmazásokban nyílhassanak meg. További részletekért lásd: [Mobilalkalmazás-kezelési házirendek konfigurálása és telepítése a Microsoft Intune-konzolon](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Ha a felhasználók a felügyelt böngészőt az alkalmazásáruházból telepítik és azt nem az Intune felügyeli, az alábbi viselkedés várható: iOS – A felügyelt böngészőalkalmazás alapvető webböngészőként használható, de néhány szolgáltatás nem érhető el, és nem fér hozzá a többi, Intune által felügyelt alkalmazás adataihoz.
Android – A felügyelt böngészőalkalmazás nem használható.
Ha a felhasználók telepítik a felügyelt böngészőt iOS 9-es verziónál régebbi verziójú iOS-eszközre, azt semmilyen Ön által létrehozott házirend nem fogja felügyelni. Annak érdekében, hogy a böngészőt az Intune felügyelje, a felhasználóknak el kell távolítaniuk az alkalmazást, mielőtt azt Ön felügyelt alkalmazásként telepítené a számukra. Ha a felhasználó iOS 9-es vagy újabb rendszeren telepíti a felügyelt böngészőt, a rendszer a felhasználót annak engedélyezésére kéri, hogy ez házirenddel felügyelhető legyen.

Felügyeltböngésző-szabályzatokat a következő eszköztípusok esetében hozhat létre:

-   Android 4 vagy újabb rendszerű eszközök

-   Az iOS 7.1-es vagy újabb rendszerű eszközök

Az Intune Managed Browser támogatja a [Microsoft Intune alkalmazási partnerektől származó](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) webes tartalom megnyitását.

## Felügyeltböngésző-szabályzat létrehozása.

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) kattintson a **Házirend** &gt; **Házirend hozzáadása** elemre.

2.  Konfigurálja a **Szoftverek** kategória alábbi házirend-típusainak egyikét:

    -   **Felügyelt böngésző házirendje (Android 4 és újabb)**

    -   **Managed Browser-szabályzat (iOS 7.1 és újabb verziók)**

    Részletesebb tájékoztatás a szabályzatok használatáról és telepítéséről: [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Az alábbi táblázat a felügyeltböngésző-szabályzat beállításainak konfigurálásához nyújt segítséget:

|Beállítás neve|Részletek|
    |----------------|--------------------|
    |**Név**|Egyedi nevet adjon a felügyelt böngészőnek, hogy könnyen azonosíthassa az Intune konzolon.|
    |**Leírás**|Adjon meg egy leírást, amely áttekintést nyújt a felügyeltböngésző-szabályzatról, és olyan releváns információkat tartalmaz, amelyek megkönnyítik a böngésző megkeresését.|
    |**Engedélyezési vagy ltiltólista beállítása azon URL-címek korlátozásához, amelyeket a Managed Browser (felügyelt böngésző) megnyithat**|Válasszon az alábbi lehetőségek közül:<br /><br />**A Managed Browser csak a lenti URL-címeket nyithatja meg** – Azon URL-címek listájának megadása, amelyeket a felügyelt böngésző megnyithat.<br /><br />**A Managed Browser nem nyithatja meg a lenti URL-címeket** – Azon URL-címek listájának megadása, amelyeket a felügyelt böngésző nem nyithat meg. **Megjegyzés:** Ugyanabban a felügyeltböngésző-szabályzatban nem adhat meg egyszerre engedélyezett és tiltott URL-címeket is.<br />Az URL-címek megadható formátumáról további informácót a jelen témakör **Engedélyezett és blokkolt URL-címek URL-formátuma** című szakasza tartalmaz.|

4.  Ha elkészült, kattintson a **Házirend mentése**gombra.

Az új szabályzat a **Házirend** munkaterület **Konfigurációs szabályzatok** csomópontjában jelenik meg.

## A felügyelt böngészőalkalmazás telepítésének létrehozása
Miután létrehozta a felügyeltböngésző-szabályzatot, létrehozhatja a felügyelt böngészőalkalmazás szoftvertelepítését, és hozzárendelheti a létrehozott felügyeltböngésző-szabályzathoz.

> [!IMPORTANT]
> A felügyeltböngésző-szabályzatokat az Intune egyéb szabályzataitól eltérő módon kell telepíteni. Ezt a szabályzattípust hozzá kell rendelni a felügyelt böngésző szoftvercsomagjához.

Telepítse az alkalmazást, és ügyeljen arra, hogy a **Mobilalkalmazások kezelései** lapon a felügyeltböngésző-szabályzat kiválasztásával hozzá kell rendelnie a szabályzatot az alkalmazáshoz.

Az alkalmazások telepítésével kapcsolatos részletekért lásd: [Alkalmazások telepítése Microsoft Intune-ban](deploy-apps-in-microsoft-intune.md).

## Felügyelt böngésző – biztonság és adatvédelem

-   Az IOS-eszközökön nem nyithatók meg azok a felhasználók által felkeresett webhelyek, amelyek lejárt vagy nem megbízható tanúsítvánnyal rendelkeznek.

-   A felügyelt böngésző nem használja a felhasználók eszközein futó beépített böngésző beállításait. Ennek az az oka, hogy a felügyelt böngésző nem fér hozzá ezekhez a beállításokhoz.

-   Ha engedélyezi az **Egyszerű PIN-kód megkövetelése a hozzáféréshez** vagy a **Vállalati hitelesítő adatok megkövetelése a hozzáféréshez** beállítást a felügyelt böngészőhöz hozzárendelt mobilalkalmazás-felügyeleti szabályzatban, és a felhasználó a hitelesítési lapon a súgóhivatkozásra kattint, bármely internetes webhelyet elérhet, függetlenül attól, hogy azok lettek-e adva a felügyeltböngésző-szabályzat blokklistájához.

-   A felügyelt böngésző csak akkor képes blokkolni a hozzáférést a webhelyekhez, ha azokat közvetlenül érik el. Nem képes blokkolni a hozzáférést, ha a felhasználó köztes szolgáltatások (például egy fordítási szolgáltatás) használatával éri el a webhelyet.

-   A hitelesítés lehetővé tétele és az Intune-dokumentáció elérése érdekében a **&#42;.microsoft.com** mentesül az engedélyezési és blokkolási beállítások alól, és mindig engedélyezve van.

### A használatra vonatkozó adatok kikapcsolása
A Microsoft termék- és szolgáltatásfejlesztési célból automatikusan névtelen adatokat gyűjt a felügyelt böngésző teljesítményéről és használatáról, de a felhasználók bármikor kikapcsolhatják az adatok gyűjtését eszközük **Használati adatok** beállításával. Nem tudja befolyásolni ezen adatok gyűjtését.

## Kapcsolódó információk

### Az engedélyezett és a blokkolt URL-címek URL-formátuma
Az alábbi táblázat azokat az engedélyezett formátumokat és helyettesítő karaktereket ismerteti, amelyek az URL-címek engedélyezési és blokklistákban való megadásakor használhatók.

-   A csillag („**&#42;**”) helyettesítő karakter es szimbólum a megengedett minták alábbi listájának szabályai szerint használható.

-   Az URL-címek listába történő bevitelekor ellenőrizze, hogy az URL-címet a **http** vagy a **https** előtaggal adta-e meg.

-   A címben portszámokat is megadhat. Ha nem ad meg portszámot, a rendszer a következő értékeket használja:

    -   HTTP – 80-as port

    -   HTTPS – 443-as port

    A portszám helyettesítő karakterrel való megadása nem támogatott. Például: **http&colon;//www&period;contoso&period;com:*; ** és **http&colon;//www&period;contoso&period;com: /*;**

-   Az alábbi táblázat az URL-címek megadásakor használható mintákat ismerteti:

|URL-cím|Részletek|Egyezik|Nem egyezik|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Egyetlen lapnak felel meg|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|Egyetlen lapnak felel meg|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Az összes www.contoso.com karakterlánccal kezdődő URL-cím|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|A contoso.com összes altartománya|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|Egyetlen mappa|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|Egyetlen lap, amely portszámot használ|http://www.contoso.com:80||
    |https://www.contoso.com|Egyetlen biztonságos lap|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|Egyetlen mappa és annak összes almappája|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Az alábbi példák nem engedélyezett beviteleket szemléltetnek:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   IP-címek

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

### Az engedélyezési lista és a blokklista közötti ütközések feloldása
Ha egy eszközön több felügyeltböngésző-szabályzatot léptet érvénybe, és ezek beállításai ütköznek, a rendszer mind a módot (engedélyezés vagy letiltás), mind az URL-listákat kiértékeli. Ütközés esetén a következőképpen viselkedik:

-   Ha a módok mindegyik szabályzatban azonosak, de az URL-listák eltérőek, az URL-címek használatát nem kényszeríti ki az eszközön.

-   Ha a módok mindegyik szabályzatban eltérőek, de az URL-listák azonosak, az URL-címek használatát nem kényszeríti ki az eszközön.

-   Ha az eszközön első alkalommal léptet érvénybe felügyeltböngésző-szabályzatot, és két szabályzat ütközik, a rendszer nem kényszeríti ki az URL-cím használatát az eszközön. A konfliktusokat a **Házirend** munkaterület **Házirendütközések** csomópontjában tekintheti meg.

-   Ha egy eszközön már érvénybe léptetett felügyeltböngésző-szabályzatot, és egy második érvénybe léptetett szabályzat ütköző beállításokat tartalmaz, az eredeti beállítások nem módosulnak az eszközön. A konfliktusokat a **Házirend** munkaterület **Házirendütközések** csomópontjában tekintheti meg.



<!--HONumber=Jun16_HO4-->


