---
title: Eszközprofilok létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Eszköz konfigurációs profiljának hozzáadása vagy konfigurálása Microsoft Intuneban. Válassza ki a platform típusát, konfigurálja a beállításokat, majd adjon hozzá egy hatókör címkét.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 694e2ae67ef2bf7795dcf63a03480fdaed8cfbc4
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74261642"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Eszközprofil létrehozása a Microsoft Intune-ban

Az eszközök profiljaival beállításokat adhat hozzá és konfigurálhat, majd leküldheti ezeket a beállításokat a szervezet eszközeire. [Az eszközön található szolgáltatások és beállítások alkalmazása az eszközök profiljaival](device-profiles.md) részletesebben, beleértve a teendőket is.

Ez a cikk:

- A profil létrehozásának lépéseit sorolja fel.
- Azt mutatja be, hogyan adhat hozzá hatókör-címkét a profil "filter" eleméhez.
- A Windows 10-es eszközökre vonatkozó alkalmazhatósági szabályokat ismerteti, és bemutatja, hogyan hozhat létre szabályt.
- Felsorolja a bejelentkezések frissítési ciklusának időpontját, amikor az eszközök profilokat és bármely profil-frissítést fogadnak.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profilok**lehetőséget. A következő lehetőségek közül választhat:

    - **Áttekintés**: felsorolja a profilok állapotát, és további részleteket biztosít a felhasználókhoz és eszközökhöz rendelt profilokhoz.
    - **Kezelés**: eszközbeállítások létrehozása, egyéni PowerShell- [szkriptek](../apps/intune-management-extension.md) feltöltése a profilba való futtatáshoz, valamint adattervek hozzáadása az eszközökhöz a [eSIM](esim-device-configuration.md)használatával.
    - **Figyelő**: Ellenőrizze a profil állapotát a sikerhez vagy a meghibásodáshoz, és tekintse meg a profilok naplóit is.
    - **Telepítő**: adjon hozzá egy SCEP-vagy pfx-hitelesítésszolgáltatót, vagy engedélyezze a [távközlési költségek kezelését](telecom-expenses-monitor.md) a profilban.

3. Válassza a **profil létrehozása**lehetőséget. Adja meg a következő tulajdonságokat:

   - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profil neve például a **WP e-mail-profilja a teljes vállalat számára**.
   - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
   - **Platform**: válassza ki az eszközök platformját. A választható lehetőségek:  

       - **Android**
       - **Vállalati Android**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 és újabb verziók**
       - **Windows 10 és újabb**

   - **Profil típusa**: válassza ki a létrehozni kívánt beállítások típusát. A megjelenő lista a választott **platformtól** függ.
   - **Beállítások**: az alábbi cikkek az egyes profilok típusának beállításait írják le:

       - [Felügyeleti sablonok](administrative-templates-windows.md)
       - [Egyéni](../custom-settings-configure.md)
       - [Kézbesítési optimalizálás](../delivery-optimization-windows.md)
       - [Eszközfunkciók](../device-features-configure.md)
       - [Eszközkorlátozások](device-restrictions-configure.md)
       - [Kiadás verziófrissítése és üzemmód kapcsolója](edition-upgrade-configure-windows-10.md)
       - [Oktatás](education-settings-configure.md)
       - [E-mail](email-settings-configure.md)
       - [Endpoint Protection](../protect/endpoint-protection-configure.md)
       - [Identity protection](../protect/identity-protection-configure.md)  
       - [Kioszkmód](kiosk-settings.md)
       - [PKCS-tanúsítvány](../protect/certficates-pfx-configure.md)
       - [PKCS importált tanúsítvány](../protect/certificates-imported-pfx-configure.md)
       - [SCEP-tanúsítvány](../protect/certificates-scep-configure.md)
       - [Megbízható tanúsítvány](../protect/certificates-configure.md)
       - [Szabályzatok frissítése](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Információvédelem](../protect/windows-information-protection-configure.md)

     Ha például az **iOS/iPadOS** lehetőséget választja a platformhoz, a profil típusa beállítás a következő profilhoz hasonlóan néz ki:

     ![IOS-profil létrehozása az Intune-ban](./media/device-profile-create/create-device-profile.png)

4. Ha elkészült, válassza **az OK** > **Létrehozás** lehetőséget a módosítások mentéséhez. Ekkor létrejön a profil, és megjelenik a listában.

## <a name="scope-tags"></a>Hatókörcímkék

A beállítások hozzáadása után hozzáadhat egy hatókör-címkét is a profilhoz. A hatókör-címkék meghatározott csoportokra, például HR-re vagy az összes US-NC-alkalmazottakra vonatkozó házirendeket oszthatnak ki és szűrhetik.

További információ a hatóköri címkékről és a műveletekről: [a RBAC és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Hatókör címke hozzáadása

1. Válassza a **hatókör (címkék)** lehetőséget.
2. Új hatóköri címke létrehozásához válassza a **Hozzáadás** lehetőséget. Vagy válasszon ki egy meglévő hatókör címkét a listából.
3. A módosítások mentéséhez kattintson az **OK** gombra.

## <a name="applicability-rules"></a>Alkalmazhatósági szabályok

Érintett kiadások:

- Windows 10 és újabb

Az alkalmazhatósági szabályok lehetővé teszik a rendszergazdák számára, hogy egy adott feltételnek megfelelő csoportban célozzák meg az eszközöket. Létrehozhat például egy eszköz-korlátozási profilt, amely a **minden Windows 10 rendszerű eszköz** csoportra vonatkozik. És csak azt szeretné, hogy a profil a Windows 10 Enterprise rendszerű eszközökhöz legyen hozzárendelve.

A feladat elvégzéséhez hozzon létre egy **alkalmazhatósági szabályt**. Ezek a szabályok nagyszerűek a következő esetekben:

- Windows 10 Education (EDU) rendszert használ. A fújtató College-ban minden Windows 10 EDU-eszközt meg kíván célozni a RS3 és a RS4 között.
- Az emberi erőforrások minden felhasználóját meg szeretné célozni a contoso-on, de csak a Windows 10 Professional vagy a Enterprise rendszerű eszközöket szeretné használni.

A forgatókönyvek megközelítéséhez a következőket kell tennie:

- Hozzon létre egy eszközök csoportot, amely tartalmazza az összes eszközt a Harmonikák Főiskoláján. A profilban adjon hozzá egy alkalmazhatósági szabályt, amely akkor érvényes, ha az operációs rendszer minimális verziója `16299`, és a maximális verziószám `17134`. Rendelje hozzá ezt a profilt a fújtató College-eszközök csoportjához.

  A hozzárendelés után a profil a megadott minimális és maximális verziók közötti eszközökre vonatkozik. Azon eszközök esetében, amelyek nem az Ön által megadott minimális és maximális verziók közé tartoztak, az állapotuk **nem alkalmazhatóként**jelenik meg.

- Hozzon létre egy felhasználói csoportot, amely tartalmazza az emberi erőforrások (HR) összes felhasználóját a contoso-on. A profilban adjon hozzá egy alkalmazhatósági szabályt, hogy a Windows 10 Professional vagy Enterprise rendszert futtató eszközökre vonatkozzon. Rendelje hozzá ezt a profilt a HR-felhasználók csoportjához.

  A hozzárendelés után a profil a Windows 10 Professional vagy Enterprise rendszert futtató eszközökre vonatkozik. Azon eszközök esetében, amelyek nem futtatják ezeket a kiadásokat, az állapotuk **nem alkalmazhatóként**jelenik meg.

- Ha két profil pontosan ugyanazokkal a beállításokkal rendelkezik, akkor a rendszer az alkalmazhatósági szabály nélkül alkalmazza a profilt. 

  Például a Microsoft Windows 10-es eszközök csoportjának célja a BitLocker engedélyezése, és nem rendelkezik alkalmazhatósági szabállyal. A ProfileB ugyanazt a Windows 10-es eszközök csoportot célozza meg, lehetővé teszi a BitLocker használatát, és az alkalmazhatósági szabállyal csak a profilt alkalmazza a Windows 10 Enterprise rendszerre.

  Ha mindkét profil hozzá van rendelve, a rendszer alkalmazza a profilt, mert nem rendelkezik alkalmazhatósági szabállyal. 

Amikor hozzárendeli a profilt a csoportokhoz, az alkalmazhatósági szabályok szűrőként működnek, és csak azokat az eszközöket célozzák meg, amelyek megfelelnek a feltételeknek.

### <a name="add-a-rule"></a>Szabály hozzáadása

1. Válassza ki az **alkalmazhatósági szabályokat**. Megadhatja a **szabályt**, a **tulajdonságot**és az **operációs rendszer kiadását**:

    ![Alkalmazhatósági szabály hozzáadása az eszköz konfigurációs profiljához Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. A **szabály**mezőben válassza ki, hogy szeretne-e felhasználókat vagy csoportokat bevonni vagy kizárni. A választható lehetőségek:

    - **Rendeljen hozzá profilt, ha**: olyan felhasználókat vagy csoportokat tartalmaz, amelyek megfelelnek a megadott feltételeknek.
    - **Ne rendeljen profilt, ha**: kizárja azokat a felhasználókat vagy csoportokat, amelyek megfelelnek a megadott feltételeknek.

3. A **tulajdonság**mezőben válassza ki a szűrőt. A választható lehetőségek: 

    - **Operációs rendszer kiadása**: a listában tekintse meg azokat a Windows 10-es kiadásokat, amelyeket bele szeretne foglalni (vagy ki kell zárni) a szabályba.
    - **Operációs rendszer verziója**: adja meg a szabályban a **minimális** és a **maximális** Windows 10-es verziószámot, amelyet fel szeretne venni (vagy kizár). Mindkét értéket kötelező megadni.

      Megadhatja például `10.0.16299.0` (RS3 vagy 1709) a minimális verzióhoz, és `10.0.17134.0` (RS4 vagy 1803) a maximális verzióhoz. Vagy részletesebben is megadhatja, és megadhatja `10.0.16299.001` a minimális verzióhoz, és `10.0.17134.319` a maximális verzióhoz.

4. A módosítások mentéséhez válassza a **Hozzáadás** lehetőséget.

## <a name="refresh-cycle-times"></a>A ciklus idejének frissítése

Az Intune különböző frissítési ciklusokat használ a konfigurációs profilok frissítéseinek kereséséhez. Ha az eszköz nemrég lett regisztrálva, a bejelentkezés gyakrabban fut. A [házirend-és profil-frissítési ciklusok](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) a becsült frissítési időpontokat listázza.

A felhasználók bármikor megnyithatja a Céges portál alkalmazást, és az eszköz szinkronizálásával azonnal megkeresheti a profil frissítéseit.

## <a name="recommendations"></a>Javaslatok

Profilok létrehozásakor vegye figyelembe az alábbi javaslatokat:

- Nevezze el a szabályzatokat, hogy tudja, mit, és mit csinálnak. A [megfelelőségi szabályzatok](../protect/create-compliance-policy.md) és a [konfigurációs profilok](../configuration/device-profile-create.md) nem kötelező **leírási** tulajdonsággal rendelkeznek. A **leírásban**adjon meg konkrét információkat, és adja meg, hogy mások is tudják, mi a házirend.

  Néhány konfigurációs profil például az alábbiakat tartalmazza:

  **Profilnév**: felügyeleti sablon – OneDrive konfigurációs profil az összes Windows 10 felhasználóhoz  
  **Profil leírása**: a OneDrive felügyeleti sablon profilja, amely tartalmazza a minimális és alapbeállításokat minden Windows 10 felhasználóhoz. A user@contoso.com hozta létre, hogy megakadályozza a felhasználók számára a szervezeti adatok személyes OneDrive-fiókokhoz való megosztását.

  **Profil neve**: VPN-profil az összes iOS-felhasználóhoz  
  **Profil leírása**: VPN-profil, amely tartalmazza az iOS-felhasználók minimális és alapszintű beállításait a contoso VPN-hez való csatlakozáshoz. Létrehozta user@contoso.com így a felhasználók automatikusan hitelesítik magukat a VPN-en ahelyett, hogy a felhasználók felhasználónevét és jelszavát kérik.

- Hozza létre a profilt a feladatával, például a Microsoft Edge beállításainak konfigurálása, a Microsoft Defender víruskereső beállításainak engedélyezése, az iOS-es jailbroken-eszközök letiltása stb.

- Olyan profilok hozhatók létre, amelyek adott csoportokra, például marketingre, értékesítésre, rendszergazdákra vagy hely vagy iskolai rendszerre vonatkoznak.

- Különálló felhasználói szabályzatok az eszközök házirendjéből.

  Például [Felügyeleti sablonok az Intune-ban](administrative-templates-windows.md) több száz ADMX-beállítás van. A sablon azt mutatja, hogy a beállítások a felhasználókra vagy az eszközökre vonatkoznak-e. Felügyeleti sablonok létrehozásakor rendelje hozzá a felhasználók beállításait egy felhasználói csoporthoz, és rendelje hozzá az eszköz beállításait az eszközök csoportjához.

  Az alábbi képen egy olyan beállítás látható, amely a felhasználókra és/vagy az eszközökre alkalmazható:

  ![A felhasználóra és az eszközökre vonatkozó Intune felügyeleti sablon](./media/device-profile-create/setting-applies-to-user-and-device.png)

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
