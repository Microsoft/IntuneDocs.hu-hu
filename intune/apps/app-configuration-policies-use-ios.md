---
title: Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz
titleSuffix: Microsoft Intune
description: Ez a témakör azt ismerteti, hogyan lehet alkalmazáskonfigurációs szabályzatokkal konfigurációs adatokat szolgáltatni a futó iOS-alkalmazásoknak.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c388e632f545b48a18ef6ed7b76132c290f16a9e
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813454"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ha iOS-alkalmazáshoz szeretne egyéni konfigurációs beállításokat megadni, használja az alkalmazáskonfigurációs szabályzatokat a Microsoft Intune-ban. Ezek a konfigurációs beállítások lehetővé teszik, hogy az alkalmazások testreszabhatók legyenek az alkalmazás-szállítók iránya alapján. Ezeket a konfigurációs beállításokat (kulcsokat és értékeket) az alkalmazás szállítójától kell beszerezni. Az alkalmazás konfigurálásához a beállításokat kulcs-érték párokban, vagy a kulcsokat és az értékeket tartalmazó XML-fájlként kell megadni.

A Microsoft Intune rendszergazdájaként szabályozhatja, hogy melyik felhasználói fiókok legyenek hozzáadva a Microsoft Office-alkalmazásokhoz a felügyelt eszközökön. A hozzáférést korlátozhatja csak a szervezeti felhasználói fiókokra, és blokkolhatja a személyes fiókok használatát a regisztrált eszközökön. A támogató alkalmazások feldolgozzák az alkalmazáskonfigurációt, majd eltávolítják és letiltják a nem jóváhagyott fiókokat. A konfigurációs szabályzatbeállítások akkor használatosak, amikor egy alkalmazás keresi azokat (általában az első futtatáskor).

Miután hozzáadta az alkalmazáskonfigurálási szabályzatot, beállíthatja az alkalmazáskonfigurálási szabályzat hozzárendeléseit. A szabályzat hozzárendeléseinek beállításakor felvehet vagy kizárhat a szabályzat hatálya alá eső felhasználói csoportokat. Amikor felvesz egy vagy több csoportot, kiválaszthat bizonyos csoportokat, vagy választhat beépített csoportokat. Beépített csoportok a következők: **Minden felhasználó**, **Minden eszköz**, és **Minden felhasználó és minden eszköz**. 

> [!NOTE]
> Az Intune biztosítja az előre létrehozott **Minden felhasználó** és **Minden eszköz** csoportok beépített optimalizálását a felhasználók kényelme érdekében a konzolon. Mindenképpen ajánlott ezeket a csoportokat használni az összes felhasználó és az összes eszköz megcélzására az Ön által létrehozott „Minden felhasználó” vagy „Minden eszköz” csoport helyett.

Miután kiválasztotta a belefoglalt csoportokat az alkalmazáskonfigurálási szabályzathoz, kiválaszthatja az adott kizárni kívánt csoportokat is. További információ: [Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban](apps-inc-exl-assignments.md).

> [!TIP]
> Ez a szabályzattípus jelenleg csak az iOS 8.0-ás vagy újabb verzióit futtató eszközökön érhető el. A szabályzat az alábbi alkalmazástelepítési módszereket támogatja:
>
> - **Felügyelt iOS-alkalmazás az App Store-ból**
> - **Alkalmazáscsomag az iOS számára**
>
> Az alkalmazástelepítés-típusokról bővebben a következő témakörben olvashat: [Alkalmazás felvétele a Microsoft Intune-ba](apps-add.md). További információ az alkalmazások konfigurációjának a. ipa-alkalmazáscsomag a felügyelt eszközökhöz való beépítéséről: felügyelt alkalmazások konfigurálása az [iOS fejlesztői dokumentációjában](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Alkalmazáskonfigurációs szabályzat konfigurálása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **Ügyfélalkalmazások** területet.
4. Válassza az **Alkalmazáskonfigurációs szabályzatok** lehetőséget a **Felügyelet** csoportban, majd a **Hozzáadás** lehetőséget.
5. Adja meg a következő adatokat:
    - **Név** – Az Azure Portalon megjelenítendő profilnév.
    - **Leírás** – Az Azure Portalon megjelenítendő profilleírás.
    - **Eszköz beléptetése** – válassza a **felügyelt eszközök** lehetőséget az Intune-ban regisztrált eszközökhöz.
6. A **Platform** beállításban válassza az **iOS** lehetőséget.
7. Válassza a **Társított alkalmazás** lehetőséget. A **Társított alkalmazás** panelen jelölje ki azt a felügyelt alkalmazást, amelyre a konfigurációt alkalmazni szeretné, majd nyomja meg az **OK** gombot.
8. A **Konfigurációs szabályzat hozzáadása** panelen válassza a **Konfigurációs beállítások** lehetőséget.
9. Válassza a **Konfigurációs beállítások formátuma** lehetőséget. Konfigurációs adatok hozzáadásához válassza az alábbi módszerek egyikét:
    - **Konfigurációtervező használata**
    - **XML-adatok megadása**<br><br>
    A konfigurációtervező használatáról a [Konfigurációtervező használatát](#use-configuration-designer) ismertető cikkben talál bővebb információt. Az XML-adatok megadásáról az [XML-adatok megadása](#enter-xml-data) című cikkben talál útmutatást. 
10. Miután hozzáadta a konfigurációs adatokat, kattintson **az OK gombra**, majd válassza a **Hozzáadás** lehetőséget a konfigurációs szabályzat hozzáadásához. Ekkor megjelenik a konfigurációs szabályzat áttekintő panelje.
11. Válassza a **Hozzárendelések** lehetőséget a belefoglalási és kizárási beállítások megjelenítéséhez. 

    ![Képernyőkép a szabályzat-hozzárendelések Belefoglalás lapjáról](./media/app-configuration-policies-use-ios/app-config-policy01.png)
12. Válassza a **Minden felhasználó** lehetőséget a **Belefoglalás** lapon.

    ![Képernyőkép a szabályzat-hozzárendelések legördülő listájának Minden felhasználó lehetőségéről](./media/app-configuration-policies-use-ios/app-config-policy02.png)
13. Válassza a **Kizárás** lapot. 
14. Kattintson a **Válassza ki a kizárandó csoportokat** lehetőségre a kapcsolódó panel megjelenítéséhez.

    ![Képernyőkép a szabályzat-hozzárendelések Válassza ki a kizárandó csoportokat paneljéről](./media/app-configuration-policies-use-ios/app-config-policy03.png)
15. Válassza ki azokat a csoportokat, amelyeket ki szeretne zárni, majd kattintson a **Kijelölés** lehetőségre.

    >[!NOTE]
    >Csoportok hozzáadásakor, ha bármely más csoport már bele lett foglalva egy adott hozzárendelés-típus esetében, az előre ki van jelölve, és nem módosítható más belefoglalási hozzárendelés-típusok esetében. Ezért az adott csoport használatba lett véve, és így nem használható kizárt csoportként.
16. Kattintson a **Mentés**gombra.

## <a name="use-configuration-designer"></a>A configuration designer használata

A Microsoft Intune olyan konfigurációs beállításokat tesz elérhetővé, amelyek egy-egy alkalmazásra érvényesek. A konfigurációtervezőt olyan eszközökön található alkalmazásokhoz használhatja, amelyek regisztrálva vannak vagy nincsenek regisztrálva a Microsoft Intune-ban. A tervezővel konkrét konfigurációs kulcsokat és értékeket konfigurálhat, amelyekkel létrehozhatja az alapul szolgáló XML-fájl. Az értékekhez az adattípust is meg kell adnia. Az alkalmazás telepítésének idején ezek a beállítások automatikusan érvénybe lépnek az adott alkalmazáson.

### <a name="add-a-setting"></a>Beállítás hozzáadása

1. A konfiguráció minden kulcsához és értékéhez állítsa be az alábbiakat:
   - **Konfigurációs kulcs** - Az adott beállításkonfigurációhoz egyedi azonosítóként szolgáló kulcs.
   - **Értéktípus** - A konfigurációs érték adattípusa. A típus az alábbiak egyike: egész szám, valós szám, sztring vagy logikai.
   - **Konfigurációs érték** - A konfiguráció értéke.
2. A konfigurációs beállítások megadásához válassza az **OK** gombot.

### <a name="delete-a-setting"></a>Beállítás törlése

1. Válassza a beállítás melletti három pontot ( **...** ).
2. Válassza a **Törlés** elemet.

A \{\{ és \}\} karaktereket csak a tokentípusok használják, ezek más célokra nem használhatók.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Csak a konfigurált szervezeti fiókok engedélyezése a többidentitásos alkalmazásokban 

IOS-eszközök esetén használja a következő kulcs/érték párokat:

| **Kulcs** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Értékek** | <ul><li>**Enabled** (Engedélyezve): Csak az [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) kulcs által meghatározott felügyelt felhasználói fiók használata engedélyezett.</li><li>**Disabled** (Letiltva) (vagy az **Enabled** értéktől eltérő bármilyen érték, a kis- és nagybetűket nem megkülönböztetve): Bármely fiók használata engedélyezett.</li></ul> |.

   > [!NOTE]
   > Az iOS 10,34-es vagy újabb verziójának OneDrive kell használnia, az iOS 2.99.0 vagy újabb verziójára, illetve az iOS 44.8.7 vagy későbbi verziójára készült Outlook alkalmazást, és az alkalmazásnak az [Intune app Protection-szabályzatokkal](app-protection-policy.md) kell rendelkeznie, ha csak a konfigurált, többszörös identitású szervezeti fiókok engedélyezése

## <a name="enter-xml-data"></a>XML-adatok megadása

Beírhat vagy beilleszthet egy XML-tulajdonságlistát, amelyben a kívánt alkalmazáskonfigurációs beállítások szerepelnek (Intune-ban regisztrált eszközök esetén adható meg). Az XML-tulajdonságlista formátuma a konfigurálni kívánt alkalmazás függvényében eltérő. A használandó formátummal kapcsolatban forduljon az alkalmazás szállítójához.

Az Intune ellenőrzi az XML-formátumot, azt azonban nem, hogy az XML-tulajdonságlista (PList) működik-e a célalkalmazással.

További információ az XML-tulajdonságlistákról:

- Tekintse meg az [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Az XML-tulajdonságlisták ismertetése) című témakört az iOS Developer Libraryben.

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

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>A Céges portál alkalmazás konfigurálása az iOS DEP-eszközök támogatásához

A DEP (Apple Készülékregisztrációs program) regisztrációi nem kompatibilisek a Céges portál alkalmazás App Store-verziójával. A következő lépésekkel azonban konfigurálhatja a Céges portál alkalmazást az iOS DEP-eszközök támogatásához.

1. A Azure Portal Intune-ban:
    - Szükség esetén adja hozzá a Intune Céges portált az **Intune** > **Client apps** > **apps** > **hozzáadásához**.
    - A Céges portál alkalmazáshoz tartozó alkalmazás-konfigurációs szabályzat létrehozásához nyissa meg az **ügyfélalkalmazások** > **alkalmazás-konfigurációs**házirendeket.
2. Hozzon létre egy alkalmazás-konfigurációs szabályzatot az alábbi XML-sel. Az alkalmazás-konfigurációs házirend létrehozásával és az XML-adatok megadásával kapcsolatos további információkért tekintse meg az [alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt iOS-eszközökhöz](app-configuration-policies-use-ios.md) vagy a hibrid Mdm, [Beállítások alkalmazása iOS-alkalmazásokra a System Center alkalmazás konfigurációs házirendjeivel című témakört. Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-ios-apps-with-app-configuration-policies).

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. Telepítse a Céges portált az eszközökre az alkalmazás-konfigurációs házirenddel megcélozva a kívánt csoportokra. Ügyeljen arra, hogy csak olyan eszközök csoportjaira telepítse a szabályzatot, amelyeken már van regisztrálva a DEP.
4. Kérje meg a végfelhasználókat, hogy jelentkezzenek be a Céges portál alkalmazásba, amikor az automatikusan települ.

## <a name="monitor-ios--app-configuration-status-per-device"></a>Az iOS-alkalmazáskonfigurációk figyelése minden egyes eszközön 
Konfigurációs szabályzat hozzárendelése után figyelheti az iOS-alkalmazások konfigurációs állapotát az egyes felügyelt eszközökön. Az Azure Portal **Microsoft Intune** oldalán kattintson az **Eszközök** > **Minden eszköz** lehetőségre. A felügyelt eszközök listáján az egyik eszközre kattintva nyissa meg a hozzá tartozó panelt. Az eszköz paneljén kattintson az **Alkalmazáskonfiguráció** elemre.  

## <a name="additional-information"></a>További információ

- [Az Outlook telepítése az iOS-és Android-alkalmazásokhoz – konfigurációs beállítások](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>További lépések

Ezt követően gondoskodhat az alkalmazás valamely csoporthoz történő [hozzárendeléséről](apps-deploy.md) és [figyeléséről](apps-monitor.md).
