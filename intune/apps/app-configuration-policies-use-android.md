---
title: Alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt Android Enterprise-eszközökhöz
titleSuffix: Microsoft Intune
description: A Microsoft Intune alkalmazás-konfigurációs házirendjeivel megadhatja a beállításokat, amikor a felhasználók felügyelt Google Play-alkalmazást futtatnak.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7650230e419a639adfe02cd6c01f6170a4eb878b
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369158"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt Android Enterprise-eszközökhöz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazás-konfigurációs szabályzatok a Microsoft Intune a Google Play-alkalmazások felügyelt Android Enterprise-eszközökön való felügyeletének beállításait. Az alkalmazás fejlesztője az Android által felügyelt alkalmazások konfigurációs beállításait teszi elérhetővé. Az Intune ezeket a megjelenő beállításokat használva lehetővé teszi, hogy a rendszergazda konfigurálja az alkalmazás funkcióit. Az alkalmazás konfigurációs házirendje hozzá van rendelve a felhasználói csoportokhoz. A házirend-beállítások akkor használatosak, amikor az alkalmazás ellenőrzi őket, általában az alkalmazás első futtatásakor.

> [!NOTE]  
> Az alkalmazáskonfigurációt nem minden alkalmazás támogatja. Ellenőrizze, hogy az alkalmazás támogatja-e az alkalmazás-konfigurációs házirendeket az alkalmazás fejlesztőivel kapcsolatban.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza ki az **alkalmazások** > **alkalmazás-konfigurációs szabályzatok** >  > **felügyelt eszközök** **hozzáadása** elemet. Vegye figyelembe, hogy a **felügyelt eszközök** és a **felügyelt alkalmazások**közül választhat. További információ: az [alkalmazás konfigurációját támogató alkalmazások](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. Az **alapvető beállítások** lapon adja meg a következő adatokat:
    - **Név** – Az Azure Portalon megjelenítendő profilnév.
    - **Leírás** – Az Azure Portalon megjelenítendő profilleírás.
    - **Eszköz beléptetésének típusa** – ez a beállítás **felügyelt eszközökre**van beállítva.
4. Válassza az **Android Enterprise** lehetőséget **platformként**.
5. Kattintson a célcsoport **kiválasztása** elemre a **célként megadott alkalmazás**mellett. Megjelenik a **társított alkalmazás** panel. 
6. A **társított alkalmazás** panelen válassza ki a konfigurációs házirendhez társítandó felügyelt alkalmazást, majd kattintson **az OK**gombra.
7. A **Beállítások** lap megjelenítéséhez kattintson a **tovább** gombra.
8. Kattintson a **Hozzáadás** gombra az **engedélyek hozzáadása** panel megjelenítéséhez.
9. Kattintson a felülbírálni kívánt engedélyekre. A megadott engedélyek felülbírálják az "alapértelmezett alkalmazás engedélyei" házirendet a kiválasztott alkalmazásokhoz.
10. Az **engedélyek állapotának** beállítása az egyes engedélyekhez. A **parancssorból**, az **automatikus engedélyezésből**vagy az **automatikus megtagadás**lehetőség közül választhat. Az engedélyekkel kapcsolatos további információkért tekintse [meg az androidos vállalati beállítások az eszközök megfelelőként való megjelölését az Intune használatával](~/protect/compliance-policy-create-android-for-work.md)című témakört.
11. A legördülő listából válassza ki a **konfigurációs beállítások formátumát**. Konfigurációs adatok hozzáadásához válassza az alábbi módszerek egyikét:
    - **Konfigurációtervező használata**
    - **JSON-adatbevitel**<br><br>
    A konfigurációtervező használatáról a [Konfigurációtervező használatát](#use-the-configuration-designer) ismertető cikkben talál bővebb információt. Az XML-adatok bevitelével kapcsolatos részletekért lásd: [JSON-adatok megadása](#enter-json-data). 
12. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.
13. A **hozzárendelés**a következőhöz elem melletti legördülő listában válassza ki a **kiválasztott csoportokat**, az **összes felhasználót**, **az összes eszközt**, vagy az **összes felhasználót és az összes levies** elemet az alkalmazás konfigurációs házirendjének hozzárendeléséhez.

    ![Képernyőkép a szabályzat-hozzárendelések Belefoglalás lapjáról](./media/app-configuration-policies-use-ios/app-config-policy01.png)

14. A legördülő listában válassza az **összes felhasználó** lehetőséget.

    ![Képernyőkép a szabályzat-hozzárendelések legördülő listájának Minden felhasználó lehetőségéről](./media/app-configuration-policies-use-ios/app-config-policy02.png)

15. Kattintson a **Válassza ki a kizárandó csoportokat** lehetőségre a kapcsolódó panel megjelenítéséhez.

    ![Képernyőkép a szabályzat-hozzárendelésekről – válassza ki a kizárni kívánt csoportokat](./media/app-configuration-policies-use-ios/app-config-policy03.png)

16. Válassza ki azokat a csoportokat, amelyeket ki szeretne zárni, majd kattintson a **Kijelölés** lehetőségre.

    >[!NOTE]
    >Csoportok hozzáadásakor, ha bármely más csoport már bele lett foglalva egy adott hozzárendelés-típus esetében, az előre ki van jelölve, és nem módosítható más belefoglalási hozzárendelés-típusok esetében. Ezért az adott csoport használatba lett véve, és így nem használható kizárt csoportként.

17. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez.
18. A **Létrehozás** gombra kattintva adja hozzá az alkalmazás konfigurációs szabályzatát az Intune-hoz.

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
| HRE-eszköz azonosítója | dc0dc142-11d8-4b12-bfea-cae2a8514c82 |
| Fiókazonosító | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| Intune-eszközazonosító | b9841cd9-9843-405f-be28-b2265c59ef97 |
| Domain | contoso.com |
| Mail | john@contoso.com |
| Részleges UPN | John |
| Felhasználó azonosítója | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Felhasználónév | John Doe |
| Egyszerű felhasználónév | john@contoso.com |


### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Csak a konfigurált szervezeti fiókok engedélyezése a többidentitásos alkalmazásokban 

Android-eszközök esetén használja az alábbi kulcs/érték párokat:

| **Kulcs** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Értékek** | <ul><li>Egy vagy több <code>;</code> karakterrel elválasztott egyszerű felhasználónév (UPN).</li><li>Csak az ezzel a kulccsal meghatározott, felügyelt felhasználói fiók(ok) engedélyezett(ek).</li><li> Az Intune-ban regisztrált eszközökhöz a <code>{{userprincipalname}}</code> token használható a regisztrált felhasználói fiók helyettesítésére.</li></ul> |

   > [!NOTE]
   > Az Outlookot az Android 2.2.222 és újabb verziójához, a Word, az Excel, a PowerPoint for Android 16.0.9327.1000 és újabb verziójához, vagy a OneDrive for Android 5,28 és újabb verzióhoz kell használnia, ha csak a konfigurált, többszörös identitású szervezeti fiókok engedélyezése<p></p>
   > Microsoft Intune rendszergazdaként beállíthatja, hogy mely felhasználói fiókok legyenek hozzáadva Microsoft Office alkalmazásokhoz a felügyelt eszközökön. A hozzáférést korlátozhatja csak a szervezeti felhasználói fiókokra, és blokkolhatja a személyes fiókok használatát a regisztrált eszközökön. A támogató alkalmazások feldolgozzák az alkalmazáskonfigurációt, majd eltávolítják és letiltják a nem jóváhagyott fiókokat.<p></p>

## <a name="enter-json-data"></a>JSON-adatbevitel

Az alkalmazások bizonyos konfigurációs beállításai (például a köteg típusú alkalmazások) nem konfigurálhatók a Configuration designerrel. Ezekhez az értékekhez használja a JSON-szerkesztőt. A beállítások megadása ezen alkalmazások számára az alkalmazás telepítésekor automatikusan történik.

1. A **Konfigurációs beállítások formátuma** beállításban válassza a **Belépés a JSON-szerkesztőbe** lehetőséget.
2. A szerkesztőben definiálhatja konfigurációs beállítások JSON-értékeit. Választhatja a **JSON-sablon letöltése** lehetőséget a mintafájl letöltéséhez, amelyet ezután konfigurálhat.
3. Válassza az **OK**, majd a **Hozzáadás** gombot.

Ekkor létrejön a szabályzat, és megjelenik a listában.

Amikor valamelyik eszközön sor kerül az alkalmazáskonfigurációs szabályzathoz rendelt alkalmazás futtatására, akkor a rendszer a szabályzatban szereplő beállításoknak megfelelően fogja futtatni azt.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Az engedélyek engedélyezési állapotának előzetes konfigurálása az alkalmazásokhoz

Az Android-eszközök funkcióinak eléréséhez előre konfigurálhatja az alkalmazás engedélyeit is. Alapértelmezés szerint az olyan Android-alkalmazások, amelyek az eszközre vonatkozó engedélyeket igényelnek, például a tartózkodási helyhez vagy az eszköz kamerához való hozzáférés megadását kérik a felhasználóknak az engedélyek elfogadásához

Egy alkalmazás például az eszköz mikrofonját használja. A rendszer felszólítja a felhasználót, hogy engedélyezze az alkalmazás számára a mikrofon használatára vonatkozó engedélyt.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **alkalmazások** > **alkalmazás-konfigurációs házirendek** >   > **felügyelt eszközök** **hozzáadása** lehetőséget.
2. Adja hozzá a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. Például egy jó szabályzat neve az **Android Enterprise prompt engedélyek alkalmazás-házirend a teljes vállalat**számára.
    - **Leírás**. Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Eszköz beléptetésének típusa**: Ez a beállítás **felügyelt eszközökre**van beállítva.
    - **Platform**: válassza az **Android**lehetőséget.

3. Válassza a **társított alkalmazás**lehetőséget. Válassza ki azt az alkalmazást, amelynek meg szeretné határozni a konfigurációs szabályzatát. Válassza ki az androidos munkahelyi profil által jóváhagyott és az Intune-nal szinkronizált alkalmazások listájából.
4. Válassza az **engedélyek** > **Hozzáadás**lehetőséget. A listából válassza ki a rendelkezésre álló alkalmazások engedélyeit > **OK gombra**.
5. Válasszon beállítást az ehhez a szabályzathoz megadandó egyes engedélyekhez:
    - **Rákérdezés**. A felhasználó elfogadásra vagy elutasításra való felszólítása.
    - **Automatikus engedélyezés**. Automatikus jóváhagyás a felhasználó értesítése nélkül.
    - **Automatikus elutasítás**. Automatikus elutasítás a felhasználó értesítése nélkül.
6. Az alkalmazás-konfigurációs házirend hozzárendeléséhez válassza ki az alkalmazás-konfigurációs házirendet > **hozzárendelés** > **válassza a csoportok lehetőséget**. Válassza ki a hozzárendelni kívánt felhasználói csoportokat > **válassza a lehetőséget**.
7. A szabályzat hozzárendeléséhez kattintson a **Mentés** gombra.

## <a name="additional-information"></a>További információ

- [Felügyelt Google Play-alkalmazás kiosztása androidos vállalati eszközökhöz](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Az Outlook telepítése iOS-/iPadOS-és Android-alkalmazás konfigurációs beállításaihoz](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>További lépések

Ezt követően gondoskodhat az alkalmazás valamely csoporthoz történő [hozzárendeléséről](apps-deploy.md) és [figyeléséről](apps-monitor.md).
