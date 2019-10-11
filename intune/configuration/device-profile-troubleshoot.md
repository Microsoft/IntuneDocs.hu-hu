---
title: Az Microsoft Intune-Azure eszköz profiljainak hibakeresése | Microsoft Docs
description: Az eszközökre vonatkozó házirendekkel és profilokkal kapcsolatos gyakori kérdések és válaszok, beleértve a felhasználókra vagy eszközökre nem alkalmazott módosításokat, hogy mennyi ideig tart az új szabályzatok leküldésének eszköze, mely beállításokat alkalmazza a rendszer, ha több házirend van, mi történik, ha a profil törölve vagy eltávolítva, és még több Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8fa8e1940a5b5b9c6938abfdd0813a2b8c537f8
ms.sourcegitcommit: f1bd3b866f3ba62a562d88fdae07eef64ac11cbb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262495"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Gyakori kérdések, problémák és megoldások az eszközök házirendjével és profiljaival Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Választ kaphat a gyakori kérdésekre, amikor az Intune-ban dolgozik az eszközök profiljaival és házirendjeivel. Ez a cikk a beadási időintervallumokat is felsorolja, és több lehetőséget biztosít az ütközések kezelésére.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Miért nem kap új profilt a felhasználónak a jelszó vagy a hozzáférési kód meglévő Wi-Fi-profilban való módosításakor?

Létre kell hoznia egy vállalati Wi-Fi-profilt, telepítenie kell a profilt egy csoportba, módosítania kell a jelszót, és mentenie kell a profilt. Ha a profil megváltozik, előfordulhat, hogy egyes felhasználók nem kapják meg az új profilt.

A probléma megoldásához állítsa be a vendég Wi-Fi-t. Ha a vállalati Wi-Fi meghibásodik, a felhasználók csatlakozhatnak a vendég Wi-Fi-hez. Ügyeljen arra, hogy engedélyezze az automatikus kapcsolódási beállításokat. Telepítse a vendég Wi-Fi-profilt az összes felhasználóra.

Néhány további javaslat:  

- Ha a csatlakoztatni kívánt Wi-Fi-hálózat jelszót vagy hozzáférési kódot használ, győződjön meg arról, hogy közvetlenül tud kapcsolódni a Wi-Fi-útválasztóhoz. Az iOS-eszköz használatával tesztelheti.
- A Wi-Fi-végponthoz (Wi-Fi-útválasztóhoz) való sikeres csatlakozás után jegyezze fel az SSID-t és a használt hitelesítő adatokat (ez az érték a jelszó vagy a hozzáférési kód).
- Adja meg az SSID-t és a hitelesítő adatokat (jelszót vagy jelszót) az előmegosztott kulcs mezőben. 
- Helyezzen üzembe olyan tesztelési csoportba, amely korlátozott számú felhasználót tartalmaz, lehetőleg csak az IT-csapatot. 
- IOS-eszköz szinkronizálása az Intune-nal. Regisztráljon, ha még nem regisztrálta. 
- Ellenőrizze, hogy csatlakozik-e ugyanahhoz a Wi-Fi-végponthoz (az első lépésben említettek szerint).
- Kiindulhat nagyobb csoportokba, és végül a szervezet összes várható felhasználója számára. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Mennyi időt vesz igénybe, hogy az eszközök a hozzájuk rendelt szabályzatot, profilt vagy alkalmazást kapják meg?

Az Intune értesíti az eszközt, hogy jelentkezzen be az Intune szolgáltatásba. Az értesítési időpontok változhatnak, beleértve az azonnal akár néhány órát is. Ezek az értesítési időpontok a platformok között is változnak.

Ha egy eszköz nem ellenőrzi, hogy az első értesítés után beolvassa-e a szabályzatot vagy a profilt, az Intune három további próbálkozást tesz lehetővé. Előfordulhat, hogy egy offline eszköz (például ki van kapcsolva vagy nem csatlakozik a hálózathoz) nem kapja meg az értesítéseket. Ebben az esetben az eszköz az Intune szolgáltatással a következő ütemezett bejelentkezéskor beolvassa a szabályzatot vagy a profilt, amelynek a **becsült** értéke:

| Platform | Frissítési ciklus|
| --- | --- |
| iOS | Körülbelül 8 óránként |
| macOS | Körülbelül 8 óránként |
| Android | Körülbelül 8 óránként |
| Eszközként regisztrált Windows 10 rendszerű számítógépek | Körülbelül 8 óránként |
| Windows Phone | Körülbelül 8 óránként |
| Windows 8.1 | Körülbelül 8 óránként |

Ha az eszköz nemrég lett regisztrálva, a megfelelőség és a konfiguráció ellenőrzése gyakrabban fut, ami **a következő:**

| Platform | Frequency |
| --- | --- |
| iOS | 1 órán át 15 percenként, majd 8 óránként |  
| macOS | 1 órán át 15 percenként, majd 8 óránként | 
| Android | 15 percen át 3 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 
| Eszközként regisztrált Windows 10 rendszerű számítógépek | 15 percen át 3 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 
| Windows Phone | 15 percen át 5 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 
| Windows 8.1 | 15 percen át 5 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 

A felhasználók bármikor megnyithatja a Céges portál alkalmazást, és az eszköz szinkronizálásával azonnal megkeresheti a házirend-vagy profil-frissítéseket.

A felhasználói affinitás nélküli eszközök esetén a szinkronizálás gyakorisága a regisztrációt követően azonnal változhat óra és nap között. Az Intune a kérelmeket különféle időközönként küldi el az Intune-ba való bejelentkezéshez. Azonban továbbra is az eszköznek kell bejelentkeznie. A kezdeti regisztráció után a bejelentkezés befejezéséhez szükséges idő előre nem látható. Emellett az eszközök regisztrálásának típusától, valamint az eszközhöz rendelt szabályzatok és profiloktól is függ. Az eszköz regisztrálása és az összes kezdeti házirend és profil alkalmazása után az eszköz az Intune-ban regisztrált idő alapján megkeresi az új szabályzatokat és profilokat az 6-8 óránként.

Ajánlott eljárásként győződjön meg arról, hogy az eszközök legalább nyolc óra elteltével online állapotban vannak a legjobb eredmények elérése érdekében.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Milyen műveletek okozzák az Intune-nak, hogy azonnal értesítést küldjön egy eszköznek?

A rendszer különböző műveleteket indít el, például ha egy házirend, profil vagy alkalmazás hozzá van rendelve (vagy ki van osztva), frissítve, törölve és így tovább. Ezek a műveleti idők a platformok között változnak.

Az eszközök akkor jelentkeznek be az Intune-ba, amikor értesítést kapnak a bejelentkezéshez, vagy az ütemezett bejelentkezés során. Ha egy művelettel rendelkező eszközt vagy felhasználót céloz meg, például a zárolás, a jelszó alaphelyzetbe állítása, az alkalmazás, a profil vagy a házirend-hozzárendelés, akkor az Intune azonnal értesíti az eszközt, hogy bejelentkezzen a frissítések fogadásához.

Más módosítások, például a kapcsolattartási adatok módosítása a Céges portál alkalmazásban, nem okoz azonnali értesítést az eszközöknek.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Ha ugyanahhoz a felhasználóhoz vagy eszközhöz több szabályzat is hozzá van rendelve, honnan tudható, hogy mely beállítások lesznek alkalmazva?

Ha ugyanahhoz a felhasználóhoz vagy eszközhöz két vagy több házirend van hozzárendelve, akkor a rendszer az egyes beállítások szintjén alkalmazza a beállításokat:

- A megfelelőségi szabályzat beállításai mindig elsőbbséget élveznek a konfigurációs profil beállításaival szemben.

- Ha egy megfelelőségi szabályzat egy másik megfelelőségi szabályzatban megjelenő beállítással van kiértékelve, akkor a legszigorúbb megfelelőségi házirend-beállítás érvényes.

- Ha egy konfigurációs házirend beállítása ütközik egy másik konfigurációs házirend beállításával, ez az ütközés az Intune-ban jelenik meg. Az ütközések manuális feloldása.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Mi történik, ha az alkalmazás-védelmi házirendek ütköznek egymással? Melyiket alkalmazza az alkalmazásra?

Az ütközési értékek az alkalmazás védelmi házirendjében elérhető legszigorúbb beállítások, *kivéve* a számok beviteli mezőit, például a PIN-kód kísérleteit az Alaphelyzetbe állítás előtt. A szám típusú beviteli mezők ugyanazok, mint az értékek, ahogy a MAM-szabályzatot az ajánlott beállítások lehetőséggel hozta létre.

Ütközések történnek, ha két Profilbeállítások azonosak. Például két olyan MAM-szabályzatot konfigurált, amely azonos a másolási/beillesztési beállítás kivételével. Ebben az esetben a másolás/beillesztés beállítás a legszigorúbb értékre van állítva, a többi beállítás pedig konfiguráltként van alkalmazva.

Egy házirend települ az alkalmazásba, és érvénybe lép. A rendszer egy második szabályzatot helyez üzembe. Ebben az esetben az első házirend elsőbbséget élvez, és alkalmazva marad. A második szabályzat ütközést jelez. Ha mindkettő egyszerre van alkalmazva, ami azt jelenti, hogy nincs korábbi házirend, akkor mindkettő ütközést jelez. Minden ütköző beállítás a legszigorúbb értékre van állítva.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Mi történik, ha az egyéni iOS-házirendek ütköznek?

Az Intune nem értékeli az Apple konfigurációs fájlok vagy az egyéni Open Mobile Alliance Uniform Resource Identifier (OMA-URI) szabályzatok tartalmát. Csupán kézbesítési mechanizmusként szolgál.

Ha egyéni szabályzatot rendel hozzá, győződjön meg arról, hogy a konfigurált beállítások nem ütköznek a megfelelőséggel, a konfigurációval vagy az egyéb egyéni házirendekkel. Ha egy egyéni házirend és a beállításai ütköznek, a rendszer véletlenszerűen alkalmazza a beállításokat.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Mi történik, ha a profil törölve van vagy már nem alkalmazható?

Amikor töröl egy profilt, vagy eltávolít egy olyan eszközt a csoportból, amely a profilt tartalmaz, a profil és a beállítások el lesznek távolítva az eszközről a következő módon:

- Wi-Fi, VPN, tanúsítvány és e-mail profilok: a rendszer eltávolítja ezeket a profilokat az összes támogatott regisztrált eszközről.
- Minden más profil típusa:  

  - **Windows és Android rendszerű eszközök**: a beállítások nem törlődnek az eszközről
  - **Windows Phone-telefon 8,1-eszközök**: a következő beállítások törlődnek:  
  
    - Jelszó megkövetelése a mobileszközök zárolásának feloldásához
    - Egyszerű jelszavak engedélyezése
    - Jelszó minimális hossza
    - Kötelező jelszó típusa
    - Jelszó érvényessége (nap)
    - Korábbi jelszavak megjegyzése
    - Ismétlődő sikertelen bejelentkezések száma az eszköz törlése előtt
    - Jelszó kérése ennyi perc inaktivitás után
    - Kötelező jelszó típusa – a karakterkészletek minimális száma
    - Kamera engedélyezése
    - Titkosítás megkövetelése mobileszközön
    - Cserélhető tároló engedélyezése
    - Webböngésző engedélyezése
    - Alkalmazás-áruház engedélyezése
    - Képernyőfelvétel-készítés engedélyezése
    - Földrajzi hely meghatározásának engedélyezése
    - Microsoft-fiók engedélyezése
    - Másolás és beillesztés engedélyezése
    - Wi-Fi-kötés engedélyezése
    - Ingyenes Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése
    - Wi-Fi elérési pontok jelentéskészítésének engedélyezése
    - Törlés engedélyezése
    - Bluetooth engedélyezése
    - NFC engedélyezése
    - Wi-Fi engedélyezése

  - **iOS**: az összes beállítás törlődik, kivéve a következőket:
  
    - Hangroaming engedélyezése
    - Adatroaming engedélyezése
    - Automatikus szinkronizálás engedélyezése barangolás közben

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Módosítottam egy eszköz korlátozási profilját, de a módosítások nem lépnek érvénybe

A beállítás után Windows Phone-telefon eszközök nem teszik lehetővé a MDM vagy EAS használatával beállított biztonsági házirendek használatát a biztonság csökkentése érdekében. Például beállíthatja, hogy a **jelszó minimális száma** 8 legyen. Megpróbálja csökkenteni 4-re. A szigorúbb profil már alkalmazva van az eszközre.

Ha a profilt kevésbé biztonságos értékre szeretné módosítani, állítsa vissza a biztonsági házirendeket. Például a Windows 8,1-ben az asztalon, a jobb > válassza a **beállítások** > **Vezérlőpult**lehetőséget. Válassza ki a **felhasználói fiókok** kisalkalmazást. A bal oldali navigációs menüben található a **biztonsági házirendek alaphelyzetbe állítása** hivatkozás (az alsó felé). Jelölje ki, majd válassza a **házirendek alaphelyzetbe állítása**lehetőséget.

Előfordulhat, hogy más MDM-eszközöket (például Android, Windows Phone-telefon 8,1 vagy újabb, iOS és Windows 10) ki kell vonni, majd újból regisztrálni kell az Intune-ba egy kevésbé korlátozó profil alkalmazásához.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>A Windows 10-es profil egyes beállításai "nem alkalmazható" értéket adnak vissza

A Windows 10-es eszközök egyes beállításai "nem alkalmazható"-ként jelenhetnek meg. Ha ez történik, az adott beállítás nem támogatott az eszközön futó Windows-verzió vagy-kiadás esetében. Ez az üzenet a következő okok miatt fordulhat elő:

- A beállítás csak a Windows újabb verzióiban érhető el, és nem a jelenlegi operációs rendszer (OS) verziója az eszközön.
- A beállítás csak adott Windows-kiadások vagy adott SKU-ra, például a Home, a Professional, a Enterprise és az Education szolgáltatáshoz érhető el.

Ha többet szeretne megtudni a különböző beállításokhoz tartozó verzióról és SKU-ra vonatkozó követelményekről, tekintse meg a [konfigurációs szolgáltató (CSP) dokumentációját](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Következő lépések

További segítségre van szüksége? Lásd: [Microsoft Intune támogatásának beszerzése](../fundamentals/get-support.md).
