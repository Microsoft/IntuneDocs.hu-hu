---
title: Microsoft Intune app SDK Androidhoz – tesztelési útmutató
description: Az Androidhoz készült Microsoft Intune app SDK tesztelési útmutatója segítségével tesztelheti az Intune által felügyelt Android-alkalmazást.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9eada01f2b1e876d6d3b47140c671e3ff7eeab02
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503507"
---
# <a name="microsoft-intune-app-sdk-for-android-testing-guide"></a>Microsoft Intune app SDK Androidhoz – tesztelési útmutató

Ez az útmutató segít a fejlesztőknek az Intune által felügyelt Android-alkalmazások tesztelésében.  

## <a name="prerequisite-test-accounts"></a>Előfeltétel-ellenőrzési fiókok
Létrehozhat új fiókokat előre generált adattal vagy anélkül is. Új fiók létrehozása:
1. Nyissa meg a [Microsoft bemutatók](https://demos.microsoft.com/environments/create/tenant) webhelyét. 
2. [Állítsa be az Intune](../fundamentals/setup-steps.md) -t a mobileszköz-kezelés (Mdm) engedélyezéséhez.
3. [Hozzon létre felhasználókat](../fundamentals/users-add.md).
4. [Csoportok létrehozása](../fundamentals/groups-add.md).
5. A teszteléshez szükség szerint [rendeljen licenceket](../fundamentals/licenses-assign.md) .


## <a name="azure-portal-policy-configuration"></a>Azure Portal házirend-konfiguráció
[Hozzon létre és rendeljen alkalmazás-védelmi szabályzatokat](../apps/app-protection-policies.md) a [Azure Portal Intune](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)-paneljén. Az [alkalmazás konfigurációs szabályzatát](../apps/app-configuration-policies-overview.md) az Intune panelen is létrehozhatja és hozzárendelheti.

> [!NOTE]
> Ha az alkalmazás nincs felsorolva a Azure Portalban, a **További alkalmazások** lehetőség kiválasztásával, majd a csomag nevének a szövegmezőben való megadásával megcélozhatja a szabályzatot.

## <a name="test-cases"></a>Tesztelési esetek

A következő tesztelési esetekben konfigurációs és megerősítési lépéseket kell megadnia. Ez az útmutató segítséget nyújt az Intune által felügyelt Android-alkalmazások hibáinak elhárításához.

### <a name="required-pin-and-corporate-credentials"></a>Szükséges PIN-kód és vállalati hitelesítő adatok

PIN-kód megkövetelése a vállalati erőforrások eléréséhez. Emellett a vállalati hitelesítés is kikényszeríthető, mielőtt a felhasználók használhatják a felügyelt alkalmazásokat. Ezt a következőképpen teheti meg:

1. A **PIN-kód megkövetelése a hozzáféréshez** és a **vállalati hitelesítő adatok megkövetelése** a hozzáféréshez **Igen**. További információ: [az Android-alkalmazások védelmi házirendjének beállításai a Microsoft Intuneban](../apps/app-protection-policy-settings-android.md#access-requirements).
2. Erősítse meg a következő feltételeket:
    - Az alkalmazás elindítása előtt szerepelnie kell egy, a PIN-kód bevitelére vonatkozó kérésnek, vagy a Céges portál való regisztráció során használt üzemi felhasználónak.
    - Az érvényes bejelentkezési Rákérdezés oka az lehet, hogy egy nem megfelelően konfigurált Android-jegyzékfájl, pontosabban a Azure Active Directory Authentication Library (ADAL) integráció (SkipBroker, ClientID és Authority) értékeit okozza.
    - A promptot nem sikerült bemutatni, mert egy helytelenül integrált `MAMActivity` érték lehet. További információ a `MAMActivity`ről: [Microsoft Intune app SDK for Android fejlesztői útmutató](app-sdk-android.md).

> [!NOTE] 
> Ha az előző teszt nem működik, az alábbi tesztek valószínűleg sikertelenek lesznek. Az [SDK](app-sdk-android.md##sdk-integration) és a [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) integráció áttekintése.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Az adatátviteli és-fogadási művelet korlátozása más alkalmazásokkal
A vállalat által felügyelt alkalmazások közötti adatátvitel a következőképpen szabályozható:

1. Állítsa be az **alkalmazás átviheti az adatátvitelt más alkalmazásokba** a **szabályzattal felügyelt alkalmazásokba**.
2. Állítsa be az alkalmazás más alkalmazásokból az **összes alkalmazásba**való **fogadásának engedélyezése lehetőséget** . Ezek a szabályzatok a szándékok és a tartalomszolgáltatók használatát érintik.
3. Erősítse meg a következő feltételeket:
    - A nem felügyelt alkalmazásokból való megnyitás megfelelően működik.
    - A tartalom megosztása a felügyelt alkalmazások között engedélyezett.
    - A felügyelt alkalmazások és a nem felügyelt alkalmazások (például a Chrome) megosztása le van tiltva.

### <a name="restrict-cut-copy-and-paste"></a>Kivágási, másolási és beillesztési műveletek korlátozása
A következő módon korlátozhatja a rendszervágólapot a felügyelt alkalmazásokra:

1. A **kivágási, másolási és beillesztési műveletek korlátozása más alkalmazásokkal** a **szabályzatba való beillesztéssel felügyelt**csoportba.
2. Erősítse meg a következő feltételeket:
    - Az alkalmazásból származó szöveg másolása nem felügyelt alkalmazásba (például üzenetek) le van tiltva.

### <a name="prevent-save"></a>Mentés megakadályozása
A **Mentés másként** funkciót a következőképpen szabályozhatja:

1. Ha az alkalmazáshoz [integrált mentési vezérlőre](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)van szükség, állítsa a **"Mentés másként"** beállítást **Igen**értékre.
2. Erősítse meg a következő feltételeket:
    - A mentés csak a megfelelő felügyelt helyekre korlátozódik.

### <a name="file-encryption"></a>Fájl titkosítása
Az eszközön tárolt adatai a következőképpen titkosíthatók:

1. Állítsa az **alkalmazásadatok titkosítása** **Igen**értékre.
2. Erősítse meg a következő feltételeket:
    - Nem érinti a normál alkalmazás viselkedését.

### <a name="prevent-android-backups"></a>Az androidos biztonsági mentések tiltása
Az alkalmazások biztonsági mentését az alábbiak szerint vezérelheti:

1. Ha [beépített biztonsági mentési korlátozásokat](app-sdk-android.md#protecting-backup-data)állított be, az **androidos biztonsági mentések letiltása** **Igen**értékre.
2. Erősítse meg a következő feltételeket:
    - A biztonsági mentések korlátozottak.

### <a name="unenrollment"></a>Törlésének
Távolról törölheti a felügyelt alkalmazásokat a vállalati e-mailek és dokumentumok használatával, és a rendszer visszafejti a személyes adatait, ha már nem felügyelt. Ezt a következőképpen teheti meg:

1. A Azure Portal [kiadja a törlést](../apps/apps-selective-wipe.md).
2. Ha az alkalmazás nem regisztrálja az összes törlési kezelőt, erősítse meg a következő feltételeket:
    - Az alkalmazás teljes törlése történik.
3. Ha az alkalmazás regisztrálva van `WIPE_USER_DATA` vagy `WIPE_USER_AUXILARY_DATA`, erősítse meg a következő feltételeket:
    - A felügyelt tartalom el lesz távolítva az alkalmazásból. További információ: [az Androidhoz készült Intune app SDK Fejlesztői útmutatója – szelektív törlés](app-sdk-android.md#selective-wipe).

### <a name="multi-identity-support"></a>Többszörös identitás támogatása
A [többszörös identitás támogatásának](app-sdk-android.md#multi-identity-optional) integrálása magas kockázatú változás, amelyet alaposan meg kell vizsgálni. A leggyakoribb problémák az identitás (a környezet és a veszélyforrások szintjének) és a fájlok nyomon követése (`MAMFileProtectionManager`) helytelen beállítása miatt fordulnak elő.

Minimálisan ellenőrizze, hogy:

- A **Mentés másként** házirend megfelelően működik a felügyelt identitások esetében.
- A másolási és beillesztési korlátozásokat a rendszer megfelelően kikényszeríti a felügyelt személyes adatokkal.
- Csak a felügyelt identitáshoz tartozó adatok titkosítva vannak, és a személyes fájlok nem módosulnak.
- A regisztráció törlése során a szelektív törlés csak a felügyelt identitások adatait távolítja el.
- A rendszer feltételes indítást kér a felhasználótól, ha nem felügyelt fiókra történő módosítást végez (csak első alkalommal).

### <a name="app-configuration-optional"></a>Alkalmazás konfigurációja (nem kötelező)
Megadhatja a felügyelt alkalmazások viselkedését. Ha az alkalmazás az alkalmazások konfigurációs beállításait használja, tesztelje, hogy az alkalmazás megfelelően kezeli-e az összes olyan értéket, amelyet Ön (rendszergazdaként) be tud állítani. [Alkalmazás-konfigurációs szabályzatokat](../apps/app-configuration-policies-overview.md) az Intune-ban hozhat létre és rendelhet hozzá.

## <a name="next-steps"></a>További lépések

- [Androidos üzletági alkalmazás hozzáadása Microsoft Intune](../apps/lob-apps-android.md)
