---
title: Eszközprofilok létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Eszköz konfigurációs profiljának hozzáadása vagy konfigurálása Microsoft Intuneban. Válassza ki a platform típusát, konfigurálja a beállításokat, majd adjon hozzá egy hatókör címkét.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0858eefede678615e5b856fa0e40e48a791e4cce
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730799"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Eszközprofil létrehozása a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az eszközök profiljaival beállításokat adhat hozzá és konfigurálhat, majd leküldheti ezeket a beállításokat a szervezet eszközeire. [Az eszközön található szolgáltatások és beállítások alkalmazása az eszközök profiljaival](device-profiles.md) részletesebben, beleértve a teendőket is.

Ez a cikk:

- A profil létrehozásának lépéseit sorolja fel.
- Azt mutatja be, hogyan adhat hozzá hatókör-címkét a profil "filter" eleméhez.
- A Windows 10-es eszközökre vonatkozó alkalmazhatósági szabályokat ismerteti, és bemutatja, hogyan hozhat létre szabályt.
- Felsorolja a bejelentkezések frissítési ciklusának időpontját, amikor az eszközök profilokat és bármely profil-frissítést fogadnak.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

2. Válassza az **Eszközök konfigurálása** lehetőséget. A következő lehetőségek közül választhat:

    - **Áttekintés**: Felsorolja a profilok állapotát, és további részleteket biztosít a felhasználókhoz és eszközökhöz rendelt profilokhoz.
    - **Kezelés**: Hozzon létre eszközöket, töltsön fel egyéni [PowerShell-parancsfájlokat](../apps/intune-management-extension.md) a profilban való futtatáshoz, és adja hozzá az adatterveket az eszközökhöz a [eSIM](esim-device-configuration.md)használatával.
    - **Figyelő**: Tekintse meg a sikeres vagy sikertelen profilok állapotát, és tekintse meg a profilokban lévő naplókat is.
    - **Telepítés**: Vegyen fel egy SCEP-vagy PFX-hitelesítésszolgáltatót, vagy engedélyezze a [távközlési költségek kezelését](telecom-expenses-monitor.md) a profilban.

3. Válassza a **profilok** > **profil létrehozása**lehetőséget. Adja meg a következő tulajdonságokat:

   - **Név**: Adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profil neve például a **WP e-mail-profilja a teljes vállalat számára**.
   - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
   - **Platform**: Válassza ki az eszközök platformját. A választható lehetőségek:  

       - **Android**
       - **Vállalati Android**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 és újabb**
       - **Windows 10 és újabb**

   - **Profil típusa**: Válassza ki a létrehozni kívánt beállítások típusát. A megjelenő lista a választott **platformtól** függ.
   - **Beállítások**: Az alábbi cikkek ismertetik az egyes profiltípusok beállításait:

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
       - [SCEP-tanúsítvány](../protect/certificates-scep-configure.md)
       - [Megbízható tanúsítvány](../protect/certificates-configure.md)
       - [Szabályzatok frissítése](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Információvédelem](../protect/windows-information-protection-configure.md)

     Ha például az **iOS/iPadOS** lehetőséget választja a platformhoz, a profil típusa beállítás a következő profilhoz hasonlóan néz ki:

     ![IOS-profil létrehozása az Intune-ban](./media/device-profile-create/create-device-profile.png)

4. Ha elkészült, kattintson **az OK** > **Létrehozás** gombra a módosítások mentéséhez. Ekkor létrejön a profil, és megjelenik a listában.

## <a name="scope-tags"></a>Hatókörcímkék

A beállítások hozzáadása után hozzáadhat egy hatókör-címkét is a profilhoz. A hatókör-címkék meghatározott csoportokra, például HR-re vagy az összes US-NC-alkalmazottakra vonatkozó házirendeket oszthatnak ki és szűrhetik.

További információ a hatóköri címkékről és a műveletekről: [a RBAC és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Hatókör címke hozzáadása

1. Válassza a **hatókör (címkék)** lehetőséget.
2. Új hatóköri címke létrehozásához válassza a **Hozzáadás** lehetőséget. Vagy válasszon ki egy meglévő hatókör címkét a listából.
3. Válassza ki **OK** a módosítások mentéséhez.

## <a name="applicability-rules"></a>Alkalmazhatósági szabályok

Érintett kiadások:

- Windows 10 és újabb

Az alkalmazhatósági szabályok lehetővé teszik a rendszergazdák számára, hogy egy adott feltételnek megfelelő csoportban célozzák meg az eszközöket. Létrehozhat például egy eszköz-korlátozási profilt, amely a **minden Windows 10 rendszerű eszköz** csoportra vonatkozik. És csak azt szeretné, hogy a profil a Windows 10 Enterprise rendszerű eszközökhöz legyen hozzárendelve.

A feladat elvégzéséhez hozzon létre egy **alkalmazhatósági szabályt**. Ezek a szabályok nagyszerűek a következő esetekben:

- Windows 10 Education (EDU) rendszert használ. A fújtató College-ban minden Windows 10 EDU-eszközt meg kíván célozni a RS3 és a RS4 között.
- Az emberi erőforrások minden felhasználóját meg szeretné célozni a contoso-on, de csak a Windows 10 Professional vagy a Enterprise rendszerű eszközöket szeretné használni.

A forgatókönyvek megközelítéséhez a következőket kell tennie:

- Hozzon létre egy eszközök csoportot, amely tartalmazza az összes eszközt a Harmonikák Főiskoláján. A profilban adjon hozzá egy alkalmazhatósági szabályt, amely akkor érvényes, ha az operációs rendszer `16299` minimális verziója és a maximális `17134`verziószáma. Rendelje hozzá ezt a profilt a fújtató College-eszközök csoportjához.

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

    - **Profil kiosztása, ha**: Olyan felhasználókat vagy csoportokat tartalmaz, amelyek megfelelnek a megadott feltételeknek.
    - **Ne rendeljen profilt, ha**: Azokat a felhasználókat vagy csoportokat zárja ki, amelyek megfelelnek a megadott feltételeknek.

3. A **tulajdonság**mezőben válassza ki a szűrőt. A választható lehetőségek: 

    - **Operációs rendszer verziója**: A listában tekintse meg azokat a Windows 10-es kiadásokat, amelyeket bele szeretne foglalni (vagy ki kell zárni) a szabályba.
    - **Operációs rendszer verziója**: Adja meg a **minimális** és a **maximális** Windows 10-es verziószámot, amelyet fel szeretne venni (vagy ki kell zárni) a szabályba. Mindkét értéket kötelező megadni.

      Megadhatja például `10.0.16299.0` a (RS3 vagy 1709) értéket a minimális verzióhoz `10.0.17134.0` , és (RS4 vagy 1803) a maximális verzióhoz. Vagy részletesebben `10.0.16299.001` is megadhatja a minimális verziót és `10.0.17134.319` a maximális verziót.

4. A módosítások mentéséhez válassza a **Hozzáadás** lehetőséget.

## <a name="refresh-cycle-times"></a>A ciklus idejének frissítése

Az Intune különböző frissítési ciklusokat használ a konfigurációs profilok frissítéseinek kereséséhez. Ha az eszköz nemrég lett regisztrálva, a bejelentkezés gyakrabban fut. A [házirend-és profil-frissítési ciklusok](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) a becsült frissítési időpontokat listázza.

A felhasználók bármikor megnyithatja a Céges portál alkalmazást, és az eszköz szinkronizálásával azonnal megkeresheti a profil frissítéseit.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
