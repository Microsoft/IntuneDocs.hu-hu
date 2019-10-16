---
title: Alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt Android Enterprise-eszközökhöz
titleSuffix: Microsoft Intune
description: A Microsoft Intune alkalmazás-konfigurációs házirendjeivel megadhatja a beállításokat, amikor a felhasználók felügyelt Google Play-alkalmazást futtatnak.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d31126a259274a2c75f933428632e274d8710aa6
ms.sourcegitcommit: b8127c7a62d9ac4d0f768980fa1424567bb58733
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350026"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt Android Enterprise-eszközökhöz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazás-konfigurációs szabályzatok a Microsoft Intune a Google Play-alkalmazások felügyelt Android Enterprise-eszközökön való felügyeletének beállításait. Az alkalmazás fejlesztője az Android által felügyelt alkalmazások konfigurációs beállításait teszi elérhetővé. Az Intune ezeket a megjelenő beállításokat használva lehetővé teszi, hogy a rendszergazda konfigurálja az alkalmazás funkcióit. Az alkalmazás konfigurációs házirendje hozzá van rendelve a felhasználói csoportokhoz. A házirend-beállítások akkor használatosak, amikor az alkalmazás ellenőrzi őket, általában az alkalmazás első futtatásakor.

> [!NOTE]  
> Az alkalmazáskonfigurációt nem minden alkalmazás támogatja. Ellenőrizze, hogy az alkalmazás támogatja-e az alkalmazás-konfigurációs házirendeket az alkalmazás fejlesztőivel kapcsolatban.

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ban válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** >  **Hozzáadás**lehetőséget.
2. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. A helyes szabályzat neve például az **Android Enterprise Nine Work app Policy a teljes vállalat**számára.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Eszköz beléptetésének típusa**: válassza a **felügyelt eszközök**elemet.
    - **Platform**: válassza az **Android**lehetőséget.

3. Válassza a **társított alkalmazás**lehetőséget. Válassza ki azt az alkalmazást, amelyben meg szeretné határozni az alkalmazás konfigurációs szabályzatát. Válassza ki a felügyelt Google Play-alkalmazások listáját, amelyeket jóváhagyott és szinkronizált az Intune-nal.
4. Válassza az **Engedélyek** lehetőséget. A konfigurációkat a következőkkel adhatja meg:

    - [A konfigurációtervező](#use-the-configuration-designer)
    - [A JSON-szerkesztő](#enter-the-json-editor)

5. Válassza **az OK** > **Hozzáadás**lehetőséget.

## <a name="use-the-configuration-designer"></a>A konfigurációtervező használata

A felügyelt Google Play-alkalmazások konfigurációs tervezőjét akkor használhatja, ha az alkalmazást a konfigurációs beállítások támogatására tervezték. A konfiguráció az Intune-ban regisztrált eszközökre vonatkozik. A tervezővel konkrét konfigurációs értékeket konfigurálhat az alkalmazás által elérhető beállításokhoz.

1. Válassza a **Hozzáadás** elemet. Válassza ki az alkalmazáshoz megadni kívánt konfigurációs beállítások listáját.

    Ha az e-mail-alkalmazáshoz Gmailt vagy kilenc munkát használ, tekintse meg az e [-mailek konfigurálásával kapcsolatos további információkért lásd az androidos vállalati eszközök beállításait](../email-settings-android-enterprise.md) .

2. A konfiguráció minden kulcsához és értékéhez állítsa be az alábbiakat:

    - **Value Type (értéktípus**): a konfigurációs érték adattípusa. Sztring értéktípusok esetében igény szerint megadhat egy változót vagy tanúsítványprofilt értéktípusnak.
    - **Konfigurációs érték**: a konfiguráció értéke. Ha a változó vagy a tanúsítvány lehetőséget választja az **érték típushoz**, válassza a változók vagy a tanúsítványok profiljainak listáját. Ha kijelöl egy tanúsítványt, akkor az eszközre központilag telepített tanúsítvány aliasa futásidőben van feltöltve.

### <a name="supported-variables-for-configuration-values"></a>A konfigurációs értékek támogatott változói

Ha változót szeretne megadni értéktípusnak, az alábbi lehetőségek közül választhat:

| Beállítás | Példa |
|----|----|
| Mail | john@contoso.com |
| Egyszerű Felhasználónév | john@contoso.com |
| Részleges UPN | John |
| Domain | Contoso.com |
| Felhasználónév | John Doe |
| Fiókazonosító | fc0dc142-71d8-4B12-bbea-bae2a8514c81 |
| Felhasználói azonosító | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Eszköz azonosítója | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Csak a konfigurált szervezeti fiókok engedélyezése a többidentitásos alkalmazásokban 

Android-eszközök esetén használja az alábbi kulcs/érték párokat:

| **Kulcs** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Értékek** | <ul><li>Egy vagy több <code>;</code> karakterrel elválasztott egyszerű felhasználónév (UPN).</li><li>Csak az ezzel a kulccsal meghatározott, felügyelt felhasználói fiók(ok) engedélyezett(ek).</li><li> Az Intune-ban regisztrált eszközökhöz a <code>{{userprincipalname}}</code> token használható a regisztrált felhasználói fiók helyettesítésére.</li></ul> |

   > [!NOTE]
   > Az Outlookot az Android 2.2.222 és újabb verziójához, a Word, az Excel, a PowerPoint for Android 16.0.9327.1000 és újabb verziójához, vagy a OneDrive for Android 5,28 és újabb verzióhoz kell használnia, ha csak a konfigurált, többszörös identitású szervezeti fiókok engedélyezése<p></p>
   > Microsoft Intune rendszergazdaként beállíthatja, hogy mely felhasználói fiókok legyenek hozzáadva Microsoft Office alkalmazásokhoz a felügyelt eszközökön. A hozzáférést korlátozhatja csak a szervezeti felhasználói fiókokra, és blokkolhatja a személyes fiókok használatát a regisztrált eszközökön. A támogató alkalmazások feldolgozzák az alkalmazáskonfigurációt, majd eltávolítják és letiltják a nem jóváhagyott fiókokat.<p></p>

## <a name="enter-the-json-editor"></a>A JSON-szerkesztő megnyitása

Az alkalmazások bizonyos konfigurációs beállításai (például a köteg típusú alkalmazások) nem konfigurálhatók a Configuration designerrel. Ezekhez az értékekhez használja a JSON-szerkesztőt. A beállítások megadása ezen alkalmazások számára az alkalmazás telepítésekor automatikusan történik.

1. A **Konfigurációs beállítások formátuma** beállításban válassza a **Belépés a JSON-szerkesztőbe** lehetőséget.
2. A szerkesztőben definiálhatja konfigurációs beállítások JSON-értékeit. Választhatja a **JSON-sablon letöltése** lehetőséget a mintafájl letöltéséhez, amelyet ezután konfigurálhat.
3. Válassza az **OK**, majd a **Hozzáadás** gombot.

Ekkor létrejön a szabályzat, és megjelenik a listában.

Amikor valamelyik eszközön sor kerül az alkalmazáskonfigurációs szabályzathoz rendelt alkalmazás futtatására, akkor a rendszer a szabályzatban szereplő beállításoknak megfelelően fogja futtatni azt.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Az engedélyek engedélyezési állapotának előzetes konfigurálása az alkalmazásokhoz

Az Android-eszközök funkcióinak eléréséhez előre konfigurálhatja az alkalmazás engedélyeit is. Alapértelmezés szerint az olyan Android-alkalmazások, amelyek az eszközre vonatkozó engedélyeket igényelnek, például a tartózkodási helyhez vagy az eszköz kamerához való hozzáférés megadását kérik a felhasználóknak az engedélyek elfogadásához

Egy alkalmazás például az eszköz mikrofonját használja. A rendszer felszólítja a felhasználót, hogy engedélyezze az alkalmazás számára a mikrofon használatára vonatkozó engedélyt.

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ban válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** >  **Hozzáadás**lehetőséget.
2. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. Például egy jó szabályzat neve az **Android Enterprise prompt engedélyek alkalmazás-házirend a teljes vállalat**számára.
    - **Leírás**. Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Eszköz beléptetésének típusa**: válassza a **felügyelt eszközök**elemet.
    - **Platform**: válassza az **Android**lehetőséget.

3. Válassza a **társított alkalmazás**lehetőséget. Válassza ki azt az alkalmazást, amelynek meg szeretné határozni a konfigurációs szabályzatát. Válassza ki az androidos munkahelyi profil által jóváhagyott és az Intune-nal szinkronizált alkalmazások listájából.
4. Válassza az **engedélyek** > **Hozzáadás**lehetőséget. A listából válassza ki a rendelkezésre álló alkalmazások engedélyeit > **OK gombra**.
5. Válasszon beállítást az ehhez a szabályzathoz megadandó egyes engedélyekhez:
    - **Rákérdezés**. A felhasználó elfogadásra vagy elutasításra való felszólítása.
    - **Automatikus engedélyezés**. Automatikus jóváhagyás a felhasználó értesítése nélkül.
    - **Automatikus elutasítás**. Automatikus elutasítás a felhasználó értesítése nélkül.
6. Az alkalmazás-konfigurációs házirend hozzárendeléséhez válassza ki az alkalmazás-konfigurációs házirendet > **hozzárendelés** > **csoport kiválasztása lehetőséget**. Válassza ki a hozzárendelni kívánt felhasználói csoportokat > **válassza a lehetőséget**.
7. A szabályzat hozzárendeléséhez kattintson a **Mentés** gombra.

## <a name="additional-information"></a>További információ

- [Felügyelt Google Play-alkalmazás kiosztása androidos vállalati eszközökhöz](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Az Outlook telepítése az iOS-és Android-alkalmazásokhoz – konfigurációs beállítások](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>További lépések

Ezt követően gondoskodhat az alkalmazás valamely csoporthoz történő [hozzárendeléséről](apps-deploy.md) és [figyeléséről](apps-monitor.md).
