---
title: Ügyfélszolgálati hibaelhárítási portál
titleSuffix: Microsoft Intune
description: Az ügyfélszolgálat munkatársai a hibaelhárítási portál segítségével oldják meg a felhasználók műszaki problémáit.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3812d19122cf4dd85edf00a6fa12d9f2b89529aa
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514591"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Segítségnyújtás a céges felhasználóknak a hibaelhárítási portál használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A hibaelhárítási portál segítségével az ügyfélszolgálat munkatársai és az Intune-rendszergazdák felhasználói információkat tekinthetnek meg a felhasználói segítségkérések teljesítéséhez. Az ügyfélszolgálattal rendelkező cégek **Ügyfélszolgálat** jogosultságot oszthatnak ki egy felhasználói csoport részére. Az ügyfélszolgálati szerepkörrel rendelkezők a **Hibaelhárítás** panelt használhatják.

A **Hibaelhárítás** panelen megtalálhatók lesznek a felhasználói regisztrálással kapcsolatos problémák. A hiba adatai és a megoldáshoz javasolt lépések segítséget nyújtanak a rendszergazdának és az ügyfélszolgálati munkatársaknak a hibalehárításban. A rendszer nem jegyez fel minden regisztrálási hibát, és bizonyos hibáknál nem kínál fel megoldási javaslatokat.

Az ügyfélszolgálati szerepkör hozzárendeléséről a [Szerepköralapú hozzáférés-vezérlés (RBAC) az Intune-nal](/intune/role-based-access-control) című témakör nyújt további információt.

Ha egy felhasználó Intune-nal kapcsolatos műszaki problémával fordul az ügyfélszolgálathoz, az ügyfélszolgálat munkatársa megadja a felhasználó nevét. Az Intune hasznos adatokat jelenít meg, amelyek számos 1. szintű probléma megoldásában segíthetnek, mint például:

- Felhasználó állapota
- Hozzárendelések
- Megfelelőségi problémák
- Az eszköz nem válaszol
- Az eszközön nem működnek a VPN- vagy Wi-Fi-beállítások
- Alkalmazástelepítési hiba

## <a name="to-review-troubleshooting-details"></a>A hibaelhárítási adatok ellenőrzése

A hibaelhárítási panelen a **Felhasználó kiválasztása** hivatkozással lehet megnézni a felhasználó adatait. A felhasználói adatok segítséget nyújtanak a felhasználók és eszközeik aktuális állapotának áttekintésében.  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza a **Hibaelhárítás** lehetőséget.
4. A felhasználó kiválasztásához kattintson a **Kijelölés** lehetőségre.
5. Jelöljön ki egy felhasználót a megfelelő név vagy e-mail cím beírásával. Kattintson a **Kiválasztás** lehetőségre. A felhasználóval kapcsolatos hibaelhárítási információ a Hibaelhárítás panelen jelenik meg. Az alábbi táblázat tartalmazza az információk leírását.

> [!Note]  
> A **Hibaelhárítás** panel a böngészőben a [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) címen is elérhető.

## <a name="areas-of-troubleshooting-dashboard"></a>A hibaelhárítási irányítópult területei

A **Hibaelhárítás** panel használatával felhasználói információkat tekinthet meg.

![Hibaelhárítási irányítópult, a következő táblázatban leírt számozott területtel](./media/help-desk-operators/troubleshooting-dash.png)

| Terület | Név | Leírás |
| ---  | ---  | ---         |
| 1.   | Fiók állapota  | Az aktuális Intune-bérlő állapotát jeleníti meg, amely lehet **Aktív** vagy **Inaktív**.       |
| 2.   | Felhasználó kiválasztása  | Az aktuálisan kiválasztott felhasználó neve. Új felhasználó kiválasztásához kattintson a **Felhasználó váltása** lehetőségre.       |
| 3.   | Felhasználó állapota  | Megjeleníti a felhasználó Intune-licencének állapotát, az eszközök számát, az egyes eszközök megfelelőségét, az alkalmazások számát és az alkalmazások megfelelőségét.       |
| 4.   | Felhasználói adatok  | A listából kiválaszthatja a panelen megtekintendő információkat. <br>Az alábbiak közül választhat: <ul><li>Ügyfélalkalmazások<li>Megfelelőségi házirendek<li> Beállítási házirendek<li>Alkalmazásvédelmi szabályzatok <li>Regisztrációs korlátozások</ul>      |
| 5.   | Csoporttagság  | Megjeleníti azokat csoportokat, amelyeknek a kiválasztott felhasználó jelenleg a tagja.       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>Regisztrációs hiba hivatkozása

A Regisztrációs hibák táblázat a sikertelen regisztrációs kísérleteket jeleníti meg. A lenti táblázatban szereplő eszközök esetében előfordulhat, hogy egy újabb próbálkozás során sikerült regisztrálnia. Nem minden sikertelen kísérlet jelenik meg. A kockázatcsökkentési adatok nem érhetők el minden funkcióhoz.

| Táblázatoszlop | Leírás |
|-------------|----------|
| Regisztráció kezdete | A felhasználó első regisztrációjának kezdési időpontja. |
| Operációs rendszer | Az eszköz operációs rendszere. |
| Operációs rendszer verziója | Az eszköz operációs rendszerének verziója. |
| Hiba | A hiba oka. |

### <a name="failure-details"></a>Hiba részletei

Egy hibasort kijelölve további adatokat jeleníthet meg.

| Section | Leírás |
|-------------|----------|
| Hiba részletei | A hiba részletes leírása. |
| Lehetséges megoldások | Javasolt lépések a hiba megoldásához. Bizonyos hibákat nem lehet javítani. |
| Erőforrások (nem kötelező) | További hivatkozások a portál témaköreihez és területeihez. |

### <a name="enrollment-errors"></a>Regisztrációs hibák

| Hiba | Részletek |
|-------------|----------|
| iOS/iPadOS időtúllépés vagy hiba | Időtúllépés az eszköz és az Intune között a felhasználó regisztrációs folyamatának elhúzódása miatt. |
| Felhasználó nem található vagy nincs licence | A felhasználó nem rendelkezik licenccel, vagy eltávolították a szolgáltatásból. |
| Már regisztrált eszköz | Valaki regisztrálni próbált egy eszközt a Céges portállal egy olyan eszközön, amelyet egy másik felhasználó már regisztrált. |
| Nincs előkészítve az Intune-ban | Valaki úgy próbált regisztrálni, hogy előtte nem konfigurálta az Intune mobileszköz-kezelési (MDM-) szolgáltatót. |
| Sikertelen regisztrációs hitelesítés | Valaki a Céges portál régi verziójával próbált regisztrálni. |
| Nem támogatott eszköz | Az eszköz nem felel meg az Intune-regisztráció minimális követelményeinek. |
| Regisztrációs korlátozások miatt letiltva | A regisztráció le lett tiltva egy rendszergazda által konfigurált regisztrációs korlátozás miatt. |
| Az eszköz verziószáma túl alacsony | A rendszergazda olyan regisztrációs korlátozást konfigurált, amely nagyobb eszköz verzióját igényli. |
| Az eszköz verziószáma túl magas | A rendszergazda olyan regisztrációs korlátozást konfigurált, amely az eszköz alacsonyabb verzióját igényli. |
| Az eszköz nem regisztrálható személyesként | A rendszergazda beléptetési korlátozást konfigurált a személyes regisztrációk blokkolására, és a hibás eszköz nem a vállalati módon van definiálva. |
| Az eszköz platformja blokkolva | A rendszergazda olyan regisztrációs korlátozást konfigurált, amely letiltja az eszköz platformját. |
| Tömeges jogkivonat lejárt | A kiépítési csomagban lévő tömeges jogkivonat lejárt. |
| Az Autopilot-eszköz vagy a részletek nem találhatók | Az Autopilot-eszköz nem található a regisztrálási kísérlet során. |
| Az Autopilot-profil nem található vagy nincs hozzárendelve | Az eszközön nincs aktív Autopilot-profil. |
| Az Autopilot beléptetési metódusa váratlan | Az eszköz nem engedélyezett módszer használatával próbált regisztrálni. |
| Robotpilóta-eszköz eltávolítva | A regisztrálni próbált eszköz el lett távolítva az Autopilot-ből ehhez a fiókhoz. |
| Eszközök maximális száma elérve | A regisztráció le lett tiltva egy rendszergazda által konfigurált eszközkorlátozás miatt. |
| Apple-bevezetés | Az iOS/iPadOS-eszközök jelenleg nem regisztrálhatók az Intune-ban lévő hiányzó vagy lejárt Apple MDM push-tanúsítvány miatt. |
| Az eszköz nincs előzetesen regisztrálva | Az eszközt nem regisztrálták előre, mert annak céges és személyes regisztrációját egy rendszergazda letiltotta. |
| Nem támogatott funkció | A felhasználó valószínűleg egy, az Intune-konfigurációval nem kompatibilis módon próbált regisztrálni. |

## <a name="collect-available-data-from-mobile-device"></a>Rendelkezésre álló adatok gyűjtése mobileszközön

A következő erőforrásokkal eszközadatokat gyűjthet a felhasználói eszközök hibáinak elhárításakor:
- [IOS/iPadOS-regisztrálási hibák elküldése a rendszergazdának](/intune-user-help/send-errors-to-your-it-admin-ios)
- [A cég informatikai támogatási szolgálatának segítése az eszközproblémák megoldásában részletes naplózással](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
- [Android-naplók elküldése a cég informatikai támogatási szolgálatának USB-kábelen keresztül](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
- [Az Android diagnosztikai adatait tartalmazó naplófájlok elküldése e-mailben a rendszergazdának](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
- [Az Android regisztrálási hibáinak elküldése a rendszergazdának](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>További lépések

Megismerkedhet a szerepköralapú adminisztrációval (RBAC), és hogy az miként használható szerepkörök definiálására a szervezet eszközein, a mobileszköz-kezelésben és az adatvédelmi feladatokban. További információt a [Szerepköralapú hozzáférés-vezérlés (RBAC) az Intune-nal](/intune/role-based-access-control) című témakörben talál.

Ismertető a Microsoft Intune esetleges ismert problémáiról. További információt [Az Intune ismert problémái](/intune/known-issues) című témakörben talál.

Megtudhatja, hogyan hozhat létre támogatási jegyeket, és hogyan kérhet segítséget, ha szüksége van rá. [Támogatás kérése](/intune/get-support).
