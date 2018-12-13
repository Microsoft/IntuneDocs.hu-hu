---
title: Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz
titlesuffix: Microsoft Intune
description: Ez a témakör azt ismerteti, hogyan lehet alkalmazáskonfigurációs szabályzatokkal konfigurációs adatokat szolgáltatni a futó iOS-alkalmazásoknak.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 685803f6ef30994a943969e3642bd8349dcf9f6e
ms.sourcegitcommit: 874d9a00cc4666920069d54f99c6c2e687fa34a6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53324939"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ha iOS-alkalmazáshoz szeretne egyéni konfigurációs beállításokat megadni, használja az alkalmazáskonfigurációs szabályzatokat a Microsoft Intune-ban. Ezek a konfigurációs beállítások lehetővé teszik az alkalmazás testre szabását a szállító igényei szerint. Ezeket a konfigurációs beállításokat (kulcsokat és értékeket) az alkalmazás szállítójától kell beszerezni. Az alkalmazás konfigurálásához a beállításokat kulcs-érték párokban, vagy a kulcsokat és az értékeket tartalmazó XML-fájlként kell megadni. Ezeket a konfigurációs szabályzatokat nem kell közvetlenül felhasználókhoz vagy eszközökhöz rendelni. Ehelyett a konfigurációs szabályzatot egy alkalmazáshoz kell társítani, majd az alkalmazást hozzárendelni a felhasználókhoz vagy eszközökhöz. A konfigurációs szabályzatbeállítások akkor használatosak, amikor egy alkalmazás keresi azokat (általában az első futtatáskor).

Miután hozzáadta az alkalmazáskonfigurálási szabályzatot, beállíthatja az alkalmazáskonfigurálási szabályzat hozzárendeléseit. A szabályzat hozzárendeléseinek beállításakor felvehet vagy kizárhat a szabályzat hatálya alá eső felhasználói csoportokat. Amikor felvesz egy vagy több csoportot, kiválaszthat bizonyos csoportokat, vagy választhat beépített csoportokat. Beépített csoportok a következők: **Minden felhasználó**, **Minden eszköz**, és **Minden felhasználó és minden eszköz**. 

>[!NOTE]
>Az Intune biztosítja az előre létrehozott **Minden felhasználó** és **Minden eszköz** csoportok beépített optimalizálását a felhasználók kényelme érdekében a konzolon. Mindenképpen ajánlott ezeket a csoportokat használni az összes felhasználó és az összes eszköz megcélzására az Ön által létrehozott „Minden felhasználó” vagy „Minden eszköz” csoport helyett.<p></p>
>A Microsoft Intune rendszergazdájaként szabályozhatja, hogy melyik felhasználói fiókok legyenek hozzáadva a Microsoft Office-alkalmazásokhoz a felügyelt eszközökön. A hozzáférést korlátozhatja csak a szervezeti felhasználói fiókokra, és blokkolhatja a személyes fiókok használatát a regisztrált eszközökön. A támogató alkalmazások feldolgozzák az alkalmazáskonfigurációt, majd eltávolítják és letiltják a nem jóváhagyott fiókokat.

Miután kiválasztotta a belefoglalt csoportokat az alkalmazáskonfigurálási szabályzathoz, kiválaszthatja az adott kizárni kívánt csoportokat is. További információ: [Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban](apps-inc-exl-assignments.md).

> [!TIP]
> Ez a szabályzattípus jelenleg csak az iOS 8.0-ás vagy újabb verzióit futtató eszközökön érhető el. A szabályzat az alábbi alkalmazástelepítési módszereket támogatja:
>
> -   **Felügyelt iOS-alkalmazás az App Store-ból**
> -   **Alkalmazáscsomag az iOS számára**
>
> Az alkalmazástelepítés-típusokról bővebben a következő témakörben olvashat: [Alkalmazás felvétele a Microsoft Intune-ba](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Alkalmazáskonfigurációs szabályzat konfigurálása

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).
2. Válassza a **Minden szolgáltatás** > **Intune** lehetőséget. Az Intune a **Figyelés + felügyelet** szakaszban található.
3. Válassza az **Ügyfélalkalmazások** tevékenységprofilt.
4. Válassza az **Alkalmazáskonfigurációs szabályzatok** lehetőséget a **Felügyelet** csoportban, majd a **Hozzáadás** lehetőséget.
5. Adja meg a következő adatokat:
    - **Név** – Az Azure Portalon megjelenítendő profilnév.
    - **Leírás** – Az Azure Portalon megjelenítendő profilleírás.
    - **Eszközregisztráció típusa** – Válassza a **Felügyelt eszközök** lehetőséget.
6. A **Platform** beállításban válassza az **iOS** lehetőséget.
7.  Válassza a **Társított alkalmazás** lehetőséget. A **Társított alkalmazás** panelen jelölje ki azt a felügyelt alkalmazást, amelyre a konfigurációt alkalmazni szeretné, majd nyomja meg az **OK** gombot.
8.  A **Konfigurációs szabályzat hozzáadása** panelen válassza a **Konfigurációs beállítások** lehetőséget.
9. Válassza a **Konfigurációs beállítások formátuma** lehetőséget. XML-információk hozzáadásához válassza az alábbiak egyikét:
    - **Konfigurációtervező használata**
    - **XML-adatok megadása**<br><br>
    A konfigurációtervező használatáról a [Konfigurációtervező használatát](#use-configuration-designer) ismertető cikkben talál bővebb információt. Az XML-adatok megadásáról az [XML-adatok megadása](#enter-xml-data) című cikkben talál útmutatást. 
10. XML-adatainak hozzáadását követően használja az **OK**, majd a **Hozzáadás** gombot a konfigurációs szabályzat hozzáadásához. Ekkor megjelenik a konfigurációs szabályzat áttekintő panelje.
11. Válassza a **Hozzárendelések** lehetőséget a belefoglalási és kizárási beállítások megjelenítéséhez. 

    ![Képernyőkép a szabályzat-hozzárendelések Belefoglalás lapjáról](./media/app-config-policy01.png)
12. Válassza a **Minden felhasználó** lehetőséget a **Belefoglalás** lapon.

    ![Képernyőkép a szabályzat-hozzárendelések legördülő listájának Minden felhasználó lehetőségéről](./media/app-config-policy02.png)
13. Válassza a **Kizárás** lapot. 
14. Kattintson a **Válassza ki a kizárandó csoportokat** lehetőségre a kapcsolódó panel megjelenítéséhez.

    ![Képernyőkép a szabályzat-hozzárendelések Válassza ki a kizárandó csoportokat paneljéről](./media/app-config-policy03.png)
15. Válassza ki azokat a csoportokat, amelyeket ki szeretne zárni, majd kattintson a **Kijelölés** lehetőségre.

    >[!NOTE]
    >Csoportok hozzáadásakor, ha bármely más csoport már bele lett foglalva egy adott hozzárendelés-típus esetében, az előre ki van jelölve, és nem módosítható más belefoglalási hozzárendelés-típusok esetében. Ezért az adott csoport használatba lett véve, és így nem használható kizárt csoportként.
16. Kattintson a **Save** (Mentés) gombra.

## <a name="use-configuration-designer"></a>A configuration designer használata

A Microsoft Intune olyan konfigurációs beállításokat tesz elérhetővé, amelyek egy-egy alkalmazásra érvényesek. A konfigurációtervezőt olyan eszközökön található alkalmazásokhoz használhatja, amelyek regisztrálva vannak vagy nincsenek regisztrálva a Microsoft Intune-ban. A tervezővel konkrét konfigurációs kulcsokat és értékeket konfigurálhat, amelyekkel létrehozhatja az alapul szolgáló XML-fájl. Az értékekhez az adattípust is meg kell adnia. Az alkalmazás telepítésének idején ezek a beállítások automatikusan érvénybe lépnek az adott alkalmazáson.

### <a name="add-a-setting"></a>Beállítás hozzáadása

1. A konfiguráció minden kulcsához és értékéhez állítsa be az alábbiakat:
   - **Konfigurációs kulcs** - Az adott beállításkonfigurációhoz egyedi azonosítóként szolgáló kulcs.
   - **Értéktípus** - A konfigurációs érték adattípusa. A típus az alábbiak egyike: egész szám, valós szám, sztring vagy logikai.
   - **Konfigurációs érték** - A konfiguráció értéke.
2. A konfigurációs beállítások megadásához válassza az **OK** gombot.

### <a name="delete-a-setting"></a>Beállítás törlése

1. Válassza a beállítás melletti három pontot (**...**).
2. Válassza a **Törlés** elemet.

A \{\{ és \}\} karaktereket csak a tokentípusok használják, ezek más célokra nem használhatók.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Csak a konfigurált szervezeti fiókok engedélyezése a többidentitásos alkalmazásokban 

IOS-eszközök esetén használja az alábbi kulcs-érték párok:

| **Kulcs** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Értékek** | <ul><li>**Engedélyezett**: Az egyetlen fiók által meghatározott felügyelt felhasználói fióknak a [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) kulcsot.</li><li>**Letiltott** (vagy bármilyen érték, amely nem különbözteti meg a megfelelő **engedélyezve**): Minden olyan fiók használata engedélyezett.</li></ul> |.

   > [!NOTE]
   > Kell használnia a OneDrive vállalati verzió iOS 10.34 vagy újabb verzió és az Outlook iOS 2.99.0-es vagy újabb és az alkalmazás verziókkal kell működnie [az Intune alkalmazásvédelmi szabályzatai](app-protection-policy.md) amikor így csak konfigurált szervezeti fiókok a többszörös identitást.

## <a name="enter-xml-data"></a>XML-adatok megadása

Beírhat vagy beilleszthet egy XML-tulajdonságlistát, amelyben a kívánt alkalmazáskonfigurációs beállítások szerepelnek (Intune-ban regisztrált eszközök esetén adható meg). Az XML-tulajdonságlista formátuma a konfigurálni kívánt alkalmazás függvényében eltérő. A használandó formátummal kapcsolatban forduljon az alkalmazás szállítójához.

Az Intune ellenőrzi az XML-formátumot, azt azonban nem, hogy az XML-tulajdonságlista (PList) működik-e a célalkalmazással.

További információ az XML-tulajdonságlistákról:

  -  Tekintse meg az [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Az XML-tulajdonságlisták ismertetése) című témakört az iOS Developer Libraryben.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Alkalmazáskonfigurációs XML-fájl példaformátuma

Alkalmazáskonfigurációs fájl létrehozásakor a következő értékeket adhatja meg ebben a formátumban:

```xml
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
</dict>
```
### <a name="supported-xml-plist-data-types"></a>Támogatott XML PList-adattípusok

Az Intune a következő adattípusokat támogatja a tulajdonságlistákban:

- &lt;integer&gt; (egész szám)
- &lt;real&gt; (valós szám)
- &lt;string&gt;
- &lt;array&gt; (tömb)
- &lt;dict&gt; (szótár)
- &lt;true /&gt; (igaz) vagy &lt;false /&gt; (hamis)

### <a name="tokens-used-in-the-property-list"></a>A tulajdonságlistában használt tokenek

Ezenkívül az Intune a következő tokentípusokat támogatja a tulajdonságlistában:
- \{\{userprincipalname\}\} — például **John@contoso.com**
- \{\{mail\}\} — például **John@contoso.com**
- \{\{partialupn\}\} — például **János**
- \{\{accountid\}\} — például **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} — például **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} — például **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} — például **Szabó János**
- \{\{serialnumber\}\} — például **F4KN99ZUG5V2** (iOS-eszközök esetén)
- \{\{serialnumberlast4digits\}\} — például **G5V2** (iOS-eszközök esetén)
- \{\{aaddeviceid\}\}– például **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="monitor-ios--app-configuration-status-per-device"></a>Az iOS-alkalmazáskonfigurációk figyelése minden egyes eszközön 
Konfigurációs szabályzat hozzárendelése után figyelheti az iOS-alkalmazások konfigurációs állapotát az egyes felügyelt eszközökön. Az Azure Portal **Microsoft Intune** oldalán kattintson az **Eszközök** > **Minden eszköz** lehetőségre. A felügyelt eszközök listáján az egyik eszközre kattintva nyissa meg a hozzá tartozó panelt. Az eszköz paneljén kattintson az **Alkalmazáskonfiguráció** elemre.  

## <a name="next-steps"></a>További lépések

Ezt követően gondoskodhat az alkalmazás valamely csoporthoz történő [hozzárendeléséről](apps-deploy.md) és [figyeléséről](apps-monitor.md).
