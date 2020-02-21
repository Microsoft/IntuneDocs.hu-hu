---
title: Eszközprofilok hibaelhárítása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az eszközökre vonatkozó házirendekkel és profilokkal kapcsolatos gyakori kérdések és válaszok, beleértve a felhasználókra vagy eszközökre nem alkalmazott módosításokat, hogy mennyi ideig tart az új szabályzatok leküldésének eszköze, mely beállításokat alkalmazza a rendszer, ha több házirend van, mi történik, ha a profil törölve vagy eltávolítva, és még több Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21497716f17ced83bdcc1952cb952151f993bb7b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511327"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Gyakori kérdések, problémák és megoldások az eszközök házirendjével és profiljaival Microsoft Intune

Választ kaphat a gyakori kérdésekre, amikor az Intune-ban dolgozik az eszközök profiljaival és házirendjeivel. Ez a cikk a beadási időintervallumokat is felsorolja, és több lehetőséget biztosít az ütközések kezelésére.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Miért nem kap a felhasználó új profilt, amikor megváltoztatja a jelszót vagy a hozzáférési kódot egy létező Wi-Fi-profilban?

Ön létrehoz egy vállalati Wi-Fi-profilt, hozzárendeli egy csoporthoz, megváltoztatja a jelszót, és menti a profilt. A profil megváltoztatásakor egyes felhasználók esetleg nem kapják meg az új profilt.

A probléma következményei vendég Wi-Fi beállításával mérsékelhetők. A vállalati Wi-Fi kiesése esetén a felhasználók a vendég Wi-Fi-hez kapcsolódhatnak. Gondoskodjon az automatikus csatlakozás beállításáról. A vendég Wi-Fi profilt rendelje hozzá minden felhasználóhoz.

Néhány további javaslat:  

- Ha a csatlakoztatni kívánt Wi-Fi-hálózat jelszót vagy hozzáférési kódot használ, győződjön meg arról, hogy közvetlenül tud kapcsolódni a Wi-Fi-útválasztóhoz. A teszteléshez iOS/iPadOS eszközt használhat.
- A Wi-Fi-végponthoz (Wi-Fi-útválasztóhoz) való sikeres kapcsolódás után jegyezze fel az SSID-t és a használt hitelesítő adatokat (ez a jelszó vagy a hitelesítő kód).
- Adja meg az SSID-t és a hitelesítő adatokat (jelszót vagy hitelesítő kódot) az Előmegosztott kulcs mezőben. 
- Alkalmazza egy tesztcsoportra, amelynek csak néhány tagja van, lehetőleg a rendszergazdák közül. 
- Az iOS/iPadOS eszköz szinkronizálása az Intune-nal. Regisztráljon, ha ezt még nem tette meg. 
- Próbáljon meg újból kapcsolódni ugyanahhoz a Wi-Fi-végponthoz (az első lépésben leírtak szerint).
- Bővítse ki a kört nagyobb csoportokra és végül mindenkire, aki a szervezetben várhatóan felhasználó lesz. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Mennyi időt vesz igénybe, hogy az eszközök a hozzájuk rendelt szabályzatot, profilt vagy alkalmazást kapják meg?

Az Intune értesíti az eszközt, hogy jelentkezzen be az Intune szolgáltatásba. Az értesítési időpontok változhatnak, beleértve az azonnal akár néhány órát is. Ezek az értesítési időpontok a platformok között is változnak.

Ha egy eszköz nem ellenőrzi, hogy az első értesítés után beolvassa-e a szabályzatot vagy a profilt, az Intune három további próbálkozást tesz lehetővé. Előfordulhat, hogy egy offline eszköz (például ki van kapcsolva vagy nem csatlakozik a hálózathoz) nem kapja meg az értesítéseket. Ebben az esetben az eszköz megkapja a házirendet vagy a profilt a következő ütemezett bejelentkezéskor az Intune szolgáltatással. Ugyanez vonatkozik a meg nem felelés ellenőrzésére is, beleértve azokat az eszközöket is, amelyek a megfelelőségtől a nem megfelelő állapotba vannak áthelyezve.

**Becsült** gyakoriságok:

| Platform | Frissítési ciklus|
| --- | --- |
| iOS/iPadOS | Körülbelül 8 óránként |
| macOS | Körülbelül 8 óránként |
| Android: | Körülbelül 8 óránként |
| Eszközként regisztrált Windows 10 számítógépek | Körülbelül 8 óránként |
| Windows Phone | Körülbelül 8 óránként |
| Windows 8.1 | Körülbelül 8 óránként |

Ha az eszköz nemrég lett regisztrálva, a megfelelőség, a nem megfelelőség és a konfiguráció-ellenőrzés gyakrabban fut le, ami a **következő:**

| Platform | Gyakoriság |
| --- | --- |
| iOS/iPadOS | 1 órán át 15 percenként, majd 8 óránként |  
| macOS | 1 órán át 15 percenként, majd 8 óránként | 
| Android: | 15 percen át 3 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 
| Eszközként regisztrált Windows 10 számítógépek | 15 percen át 3 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 
| Windows Phone | 15 percen át 5 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 
| Windows 8.1 | 15 percen át 5 percenként, majd 2 órán át 15 percenként, majd körülbelül 8 óránként | 

A felhasználók bármikor megnyithatja a Céges portál alkalmazást, a **beállítások** > a **szinkronizálás** segítségével azonnal megkeresheti a házirend-vagy profil-frissítéseket.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Milyen műveletek hatására küld az Intune azonnal értesítést egy eszközre?

A rendszer különböző műveleteket indít el, például ha egy házirend, profil vagy alkalmazás hozzá van rendelve (vagy ki van osztva), frissítve, törölve és így tovább. Ezek a műveleti idők a platformok között változnak.

Az eszközök akkor jelentkeznek be az Intune-ba, amikor értesítést kapnak a bejelentkezéshez, vagy az ütemezett bejelentkezés során. Ha egy művelettel rendelkező eszközt vagy felhasználót céloz meg, például a zárolás, a jelszó alaphelyzetbe állítása, az alkalmazás, a profil vagy a házirend-hozzárendelés, akkor az Intune azonnal értesíti az eszközt, hogy bejelentkezzen a frissítések fogadásához.

Más módosítások, például a kapcsolattartási adatok módosítása a Céges portál alkalmazásban, nem okoz azonnali értesítést az eszközöknek.

A házirend vagy profil beállításait minden bejelentkezéskor alkalmazza a rendszer. Előfordulhat, hogy a [Windows 10 Mdm házirend frissítése](https://www.petervanderwoude.nl/post/windows-10-mdm-policy-refresh/) jó erőforrás.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Ha ugyanazon felhasználóhoz vagy eszközhöz több szabályzat is hozzá van rendelve, honnan tudható, hogy mely beállítások lesznek alkalmazva?

Ha ugyanahhoz a felhasználóhoz vagy eszközhöz két vagy több házirend van hozzárendelve, akkor a rendszer az egyes beállítások szintjén alkalmazza a beállításokat:

- A megfelelőségi szabályzat beállításai mindig elsőbbséget élveznek a konfigurációs profil beállításaival szemben.

- Ha egy megfelelőségi szabályzat egy másik megfelelőségi szabályzatban megjelenő beállítással van kiértékelve, akkor a legszigorúbb megfelelőségi házirend-beállítás érvényes.

- Ha egy konfigurációs házirend beállítása ütközik egy másik konfigurációs házirend beállításával, ez az ütközés az Intune-ban jelenik meg. Ezeket az ütközéseket manuálisan kell feloldani.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Mi történik, ha ütközés van két alkalmazásvédelmi szabályzat között? Melyik érvényes az alkalmazásra?

Az ütközési értékek az alkalmazás védelmi házirendjében elérhető legszigorúbb beállítások, *kivéve* a számok beviteli mezőit, például a PIN-kód kísérleteit az Alaphelyzetbe állítás előtt. A szám típusú beviteli mezők ugyanazok, mint az értékek, ahogy a MAM-szabályzatot az ajánlott beállítások lehetőséggel hozta létre.

Ütközések történnek, ha két Profilbeállítások azonosak. Például előfordulhat, hogy a másolás/beillesztés beállításra két megegyező MAM-házirendet konfigurált. Ebben az esetben a másolás/beillesztés a legszigorúbb értékre lesz beállítva, a többi beállítás pedig a konfiguráltak szerint lesz alkalmazva.

Egy házirend települ az alkalmazásba, és érvénybe lép. A rendszer egy második szabályzatot helyez üzembe. Ebben az esetben az első házirend elsőbbséget élvez, és alkalmazva marad. A második szabályzat ütközést jelez. Ha mindkettő egyszerre van alkalmazva, ami azt jelenti, hogy nincs korábbi házirend, akkor mindkettő ütközést jelez. Minden ütközésnél a legszigorúbb beállítás lesz érvényes.

## <a name="what-happens-when-iosipados-custom-policies-conflict"></a>Mi történik, ha az iOS/iPadOS egyéni házirendek ütköznek?

Az Intune nem értékeli a konfigurációs Apple-fájlok vagy az Open Mobile Alliance egységes erőforrás-azonosítóra (OMA-URI) vonatkozó egyéni szabályzatainak tartalmát. Csak kézbesítési mechanizmusként funkcionál.

Ha egyéni szabályzatot rendel hozzá, győződjön meg arról, hogy a konfigurált beállítások nem ütköznek a megfelelőséggel, a konfigurációval vagy az egyéb egyéni házirendekkel. Ha egy egyéni házirend és a beállításai ütköznek, a rendszer véletlenszerűen alkalmazza a beállításokat.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Mi történik, ha egy profilt törölnek, vagy az már nem érvényes?

Amikor töröl egy profilt, vagy eltávolít egy olyan eszközt a csoportból, amely a profilt tartalmaz, a profil és a beállítások el lesznek távolítva az eszközről a következő módon:

- Wi-Fi, VPN, tanúsítvány és e-mail profilok: Ezek a profilok az összes támogatott regisztrált eszközről el lesznek távolítva.
- Minden más profiltípus esetén:  

  - **Windows és Android rendszerű eszközök**: a beállítások nem törlődnek az eszközről
  - **Windows Phone 8.1 rendszerű eszközök**: A következő beállítások törlődnek:  
  
    - Jelszó szükséges a mobileszközök feloldásához
    - Egyszerű jelszavak engedélyezése
    - Jelszó minimális hossza
    - Kötelező jelszótípus
    - Jelszó lejárata (nap)
    - Jelszóelőzmények megjegyzése
    - Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt
    - Tétlen percek száma, mielőtt az eszköz újból kéri a jelszót
    - Kötelező jelszótípus – megadandó karakterek minimális száma
    - Kamera használatának engedélyezése
    - Mobileszköz titkosításának kötelezővé tétele
    - Cserélhető tároló használatának engedélyezése
    - Webböngésző használatának engedélyezése
    - Alkalmazástároló használatának engedélyezése
    - Képernyőfelvétel-készítés használatának engedélyezése
    - Földrajzi hely meghatározásának engedélyezése
    - Microsoft-fiók használatának engedélyezése
    - Másolás és beillesztés használatának engedélyezése
    - Wi-Fi alapú internetmegosztás használatának engedélyezése
    - Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése
    - Wi-Fi elérési pontok jelentéskészítésének engedélyezése
    - Összes adat törlésének engedélyezése
    - Bluetooth használatának engedélyezése
    - NFC használatának engedélyezése
    - Wi-Fi használatának engedélyezése

  - **iOS/iPadOS**: az összes beállítás törlődik, kivéve a következőket:
  
    - Hangroaming engedélyezése
    - Adatroaming engedélyezése
    - Automatikus szinkronizálás engedélyezése roaming közben

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Módosítottam egy eszközkorlátozási profilt, de a módosítások még nem léptek érvénybe

A beállítás után Windows Phone-telefon eszközök nem teszik lehetővé a MDM vagy EAS használatával beállított biztonsági házirendek használatát a biztonság csökkentése érdekében. Például beállíthatja, hogy a **jelszó minimális száma** 8 legyen. Megpróbálja csökkenteni 4-re. A szigorúbb profil már alkalmazva van az eszközre.

Ha a profilt kevésbé biztonságos értékre szeretné módosítani, állítsa vissza a biztonsági házirendeket. Például a Windows 8,1 operációs rendszer asztalán, a jobb > válassza a **beállítások** > **Vezérlőpult**lehetőséget. Válassza a **Felhasználói fiókok** kisalkalmazást. A bal oldali navigációs menüben található a **biztonsági házirendek alaphelyzetbe állítása** hivatkozás (az alsó felé). Válassza ki ezt, majd a **Szabályzatok alaphelyzetbe állítása** lehetőséget.

Előfordulhat, hogy más MDM-eszközöket (például Android, Windows Phone-telefon 8,1 vagy újabb), iOS/iPadOS és Windows 10 rendszert kell kivonni, majd újból regisztrálnia kell az Intune-ba egy kevésbé korlátozó profil alkalmazásához.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>A Windows 10-es profil egyes beállításai "nem alkalmazható" értéket adnak vissza

A Windows 10-es eszközök egyes beállításai "nem alkalmazható"-ként jelenhetnek meg. Ha ez történik, az adott beállítás nem támogatott az eszközön futó Windows-verzió vagy-kiadás esetében. Ez az üzenet a következő okok miatt fordulhat elő:

- A beállítás csak a Windows újabb verzióiban érhető el, és nem a jelenlegi operációs rendszer (OS) verziója az eszközön.
- A beállítás csak adott Windows-kiadások vagy adott SKU-ra, például a Home, a Professional, a Enterprise és az Education szolgáltatáshoz érhető el.

Ha többet szeretne megtudni a különböző beállításokhoz tartozó verzióról és SKU-ra vonatkozó követelményekről, tekintse meg a [konfigurációs szolgáltató (CSP) dokumentációját](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>További lépések

További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md).
