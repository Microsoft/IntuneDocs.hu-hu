---
title: Microsoft Intune app SDK Androidon – fejlesztői tesztelési útmutató
description: Az Androidhoz készült Microsoft Intune app SDK tesztelési útmutatója segítségével tesztelheti az Intune által felügyelt Android-alkalmazást.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1484567721283ddb91f3ecebbc448e7356ceaf5a
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830535"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Microsoft Intune app SDK Android-fejlesztőknek – tesztelési útmutató

Az Android rendszerhez készült Microsoft Intune app SDK tesztelési útmutatója segítségével tesztelheti az Intune által felügyelt Android-alkalmazást.  

## <a name="prerequisite-test-accounts"></a>Előfeltétel-ellenőrzési fiókok
Új fiókok hozhatók létre előre generált adattal és anélkül. Új fiók létrehozása:
1. Navigáljon a [Microsoft bemutatók](https://demos.microsoft.com/environments/create/tenant) webhelyére. 
2. [Állítsa be az Intune](../fundamentals/setup-steps.md) -t a mobileszköz-kezelés (Mdm) engedélyezéséhez.
3. [Hozzon létre felhasználókat](../fundamentals/users-add.md).
4. [Csoportok létrehozása](../fundamentals/groups-add.md).
5. A teszteléshez szükség szerint [rendeljen licenceket](../fundamentals/licenses-assign.md) .


## <a name="azure-portal-policy-configuration"></a>Azure Portal házirend-konfiguráció
[Hozzon létre és rendeljen alkalmazás-védelmi szabályzatokat](../apps/app-protection-policies.md) a [Azure Portal Intune](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)-paneljén. Az [alkalmazás-konfigurációs szabályzat](../apps/app-configuration-policies-overview.md) az Intune panelen is létrehozható és hozzárendelhető.

> [!NOTE]
> Ha az alkalmazás nem szerepel a Azure Portalban, a **További alkalmazások** lehetőség kiválasztásával és a csomag nevének a szövegmezőben való megadásával megcélozhatja a szabályzatot.

## <a name="test-cases"></a>Tesztelési esetek

A következő tesztelési esetekben konfigurációs és megerősítési lépéseket kell megadnia. Ez az útmutató segítséget nyújt az Intune által felügyelt Android-alkalmazások hibáinak elhárításához.

### <a name="required-pin-and-corporate-credentials"></a>Szükséges PIN-kód és vállalati hitelesítő adatok

PIN-kód megkövetelése a vállalati erőforrások eléréséhez. Emellett a vállalati hitelesítés is kikényszeríthető, mielőtt a felhasználók használhatják a felügyelt alkalmazásokat. A következő lépésekkel állíthatja be ezeket a követelményeket:

1. Adja meg **a PIN-kód megkövetelése a hozzáféréshez** és a **vállalati hitelesítő adatok megkövetelése az** **Igen**lehetőséget. További információ: [az Android-alkalmazások védelmi házirendjének beállításai a Microsoft Intuneban](../apps/app-protection-policy-settings-android.md#access-requirements).
2. Erősítse meg a következő feltételeket:
    - Az alkalmazás elindítása előtt szerepelnie kell a PIN-kód beírásának/beállításának és/vagy a Céges portál való regisztráció során használt üzemi felhasználónak.
    - Az érvényes bejelentkezési Rákérdezés oka lehet egy nem megfelelően konfigurált Android-jegyzékfájl, különösen a ADAL-integráció (SkipBroker, ClientID és Authority) értékei.
    - Nem sikerült bemutatni az esetleges kéréseket egy helytelenül `MAMActivity` integrált érték miatt. További információ `MAMActivity`: [Microsoft Intune app SDK for Android fejlesztői útmutató](app-sdk-android.md).

> [!NOTE] 
> Ha a fenti teszt nem működik, az alábbi tesztek valószínűleg sikertelenek lesznek. Az [SDK](app-sdk-android.md##sdk-integration) és a [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) integráció áttekintése.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Az adatátviteli és-fogadási művelet korlátozása más alkalmazásokkal
A vállalat által felügyelt alkalmazások közötti adatátvitel a következőképpen szabályozható:

1. Állítsa be az **alkalmazás átviheti az adatátvitelt más alkalmazásokba** a **szabályzattal felügyelt alkalmazásokba**.
2. Állítsa be az alkalmazás más alkalmazásokból az **összes alkalmazásba**való **fogadásának engedélyezése lehetőséget** . Ezen szabályzatok hatással lesznek a szándékok és a tartalomszolgáltatók használatára.
3. Erősítse meg a következő feltételeket:
    - A nem felügyelt alkalmazásokból való megnyitás megfelelően működik.
    - A tartalom megosztása a felügyelt alkalmazások között engedélyezett.
    - A felügyelt alkalmazások és a nem felügyelt alkalmazások (például a Chrome) megosztása le van tiltva.

### <a name="restrict-cut-copy-and-paste"></a>Kivágási, másolási és beillesztési műveletek korlátozása
A következő módon korlátozhatja a rendszervágólapot a felügyelt alkalmazásokra:

1. A **kivágási, másolási és beillesztési műveletek korlátozása más alkalmazásokkal** a **szabályzatba való beillesztéssel felügyelt**csoportba.
2. Erősítse meg a következő feltételeket:
    - Az alkalmazásból származó szöveg másolása felügyelt, nem felügyelt alkalmazásba (például üzenetek) le van tiltva.

### <a name="prevent-save-as"></a>**A Mentés másként** művelet letiltása
A **Mentés másként** funkció a következőképpen szabályozható:

1. Ha az alkalmazáshoz [integrált "Mentés másként" vezérlők](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)szükségesek, állítsa a **"Mentés másként"** beállítást **Igen**értékre.
2. Erősítse meg a következő feltételeket:
    - A mentés csak a megfelelő felügyelt helyekre korlátozódik.

### <a name="file-encryption"></a>Fájl titkosítása
Az eszközön tárolt adatai a következőképpen titkosíthatók:

1. Állítsa az **alkalmazásadatok titkosítása** **Igen**értékre.
2. Erősítse meg a következő feltételeket:
    - A normál alkalmazás viselkedése nincs hatással.

### <a name="prevent-android-backups"></a>Androidos biztonsági mentések tiltása
Az alkalmazások biztonsági mentését az alábbiak szerint vezérelheti:

1. Ha [integrált biztonsági mentési korlátozásokat](app-sdk-android.md#protecting-backup-data)állított be, az **androidos biztonsági mentések letiltása** **Igen**értékre állítható.
2. Erősítse meg a következő feltételeket:
    - A biztonsági mentések korlátozottak.

### <a name="unenrollment"></a>Törlésének
Távolról törölheti a vállalati e-maileket és dokumentumokat tartalmazó felügyelt alkalmazásokat, és a rendszer visszafejti a személyes adatait, ha az már nem az alábbiak szerint van kezelve:

1. A Azure Portal [kiadja a törlést](../apps/apps-selective-wipe.md).
2. Ha az alkalmazás nem regisztrálja az összes törlési kezelőt, erősítse meg a következő feltételeket:
    - Az alkalmazás teljes törlése történik.
3. Ha az alkalmazás regisztrálva van `WIPE_USER_DATA` a `WIPE_USER_AUXILARY_DATA`(z) vagy rendszerhez, ellenőrizze a következő feltételeket:
    - A felügyelt tartalom el lesz távolítva az alkalmazásból. További információ: [az Androidhoz készült Intune app SDK Fejlesztői útmutatója – szelektív törlés](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Többszörös identitás
A [többszörös identitás támogatásának](app-sdk-android.md#multi-identity-optional) integrálása magas kockázatú változás, amelyet alaposan meg kell vizsgálni. A leggyakoribb problémák az identitás helytelen beállítása (a környezeti és a veszélyforrások szintjén), valamint a fájlok (`MAMFileProtectionManager`) követése miatt is.

A többszörös identitásra vonatkozó következő forgatókönyvek minimálisra kell, hogy legyenek újra érvényesítve:

- A **Mentés másként** házirend megfelelően működik a felügyelt identitások esetében.
- A másolási beillesztési korlátozásokat a rendszer megfelelően kikényszeríti a személyes felügyeletre.
- Csak a felügyelt identitáshoz tartozó adatok titkosítottak, és a személyes fájlok nem módosulnak.
- A regisztráció törlése során a szelektív törlés csak a felügyelt identitások adatait távolítja el.
- A végfelhasználót a rendszer feltételes indításra kéri a nem felügyelt fiókra történő váltáskor (csak első alkalommal).

### <a name="app-configuration-optional"></a>Alkalmazás konfigurációja (nem kötelező)
A felügyelt alkalmazások viselkedését az alábbiak szerint állíthatja be:

1. Ha az alkalmazás az alkalmazások konfigurációs beállításait használja, tesztelje, hogy az alkalmazás megfelelően kezeli-e az összes olyan értéket, amelyet Ön (rendszergazdaként) be tud állítani. Az [alkalmazás-konfigurációs házirendek](../apps/app-configuration-policies-overview.md) létrehozhatók és hozzárendelhetők az Intune használatával.

## <a name="next-steps"></a>További lépések

- [Microsoft Intunehez adjon hozzá egy androidos üzletági alkalmazást](../apps/lob-apps-android.md).
