---
title: Eszközkorlátozásokra vonatkozó beállítások a Microsoft Intune-ban Windows 8.1 rendszerű eszközök esetén
titleSuffix: ''
description: Az Intune azon beállításainak ismertetése, amelyekkel szabályozhatók az eszközbeállítások, illetve a funkciók köre a Windows 8.1 rendszerű eszközökön.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0df55e79dbc54926c0507889620f2667d7b8bd7b
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72489833"
---
# <a name="microsoft-intune-windows-81-and-later-device-restriction-settings"></a>A Windows 8.1-es és újabb verzióinak eszközkorlátozásokra vonatkozó beállításai a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikk bemutatja a Microsoft Intune olyan eszközkorlátozásokra vonatkozó beállításait, melyek konfigurálhatók Windows 8.1 és újabb rendszerű eszközökhöz.


## <a name="general"></a>Általános

- **Diagnosztikai adatok beküldése** – Engedélyezése esetén az eszköz diagnosztikai adatokat küld a Microsoftnak.
- **Tűzfal** – Előírja a Windows tűzfal bekapcsolását.
- **Felhasználói fiókok felügyelete** – Kötelezővé teszi a felhasználói fiókok felügyeletének használatát az eszközökön.

## <a name="password"></a>Jelszó
- **Kötelező jelszó típusa** – Megköveteli a végfelhasználótól, hogy jelszót adjon meg az eszköz eléréséhez.
- **Jelszó minimális hossza** – Konfigurálja a jelszó minimális hosszát (karakterszámát).
- **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat** – Törli az eszközön lévő adatokat a megadott számú sikertelen bejelentkezési kísérlet után.
- **Képernyőzárolás legfeljebb ennyi perc inaktivitás után** – Azt állítja be, hogy az eszköz hány perc tétlenség után kérjen jelszót a zárolás feloldásához.
- **Jelszó érvényessége (napokban)** – Meghatározza, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát.
- **Korábbi jelszavak újbóli használatának tiltása** – Meghatározza, hogy a felhasználó beállíthat-e általa korábban már használt jelszavakat.
- **Képjelszó és PIN-kód** – Engedélyezi a képjelszó és a PIN-kód használatát. A képjelszó segítségével a felhasználó egy képre rajzolt kézmozdulatokkal jelentkezhet be. A PIN-kód gyors bejelentkezést tesz lehetővé egy négyjegyű kóddal.
- **Titkosítás** – Megköveteli, hogy az eszközön minden fájl titkosítva legyen.<br>A Windows 8.1 rendszerű eszközökön a titkosítás kényszerítéséhez minden egyes eszközön telepíteni kell a következőt: [2014. decemberi MDM-ügyfélfrissítés Windows rendszerre](https://support.microsoft.com/kb/3013816) .
Ha engedélyezi ezt a beállítást a Windows 8.1 rendszerű eszközökön, az eszköz valamennyi felhasználójának rendelkeznie kell Microsoft-fiókkal.
A titkosítás működéséhez az eszköznek teljesítenie kell a [Microsoft InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97) hardvertanúsítvány követelményeit.
Amikor kényszeríti az eszközön a titkosítást, a helyreállítási kulcs csak a felhasználó OneDrive-fiókon keresztül elérhető Microsoft-fiókjából érhető el. Ez a kulcs nem állítható vissza egy felhasználó nevében. 



## <a name="browser"></a>Böngésző
- **Automatikus kitöltés** – Engedélyezi a felhasználók számára a böngésző automatikus kiegészítési funkciója beállításainak módosítását.
- **Csalással kapcsolatos figyelmeztetések** – Engedélyezi vagy letiltja a potenciálisan rosszindulatú webhelyekről szóló figyelmeztetéseket.
- **SmartScreen** – Engedélyezi vagy letiltja a potenciálisan rosszindulatú webhelyekről szóló figyelmeztetéseket.
- **JavaScript** – Engedélyezi, hogy a böngésző szkripteket (például Java-szkripteket) futtasson.
- **Előugró ablakok** – Engedélyezi vagy letiltja a böngésző előugróablak-blokkolóját.
- **Nyomkövetést tiltó fejlécek küldése** – A nyomkövetést tiltó fejlécet küld az Internet Explorerben a felkeresett webhelyeknek.
- **Beépülő modulok** – Engedélyezi a felhasználók számára, hogy beépülő modulokat adjanak hozzá az Internet Explorerhez.
- **Egyszavas navigálás intranetes webhelyre** – Engedélyezi, hogy egyetlen szó, például a „Bing” használatával az Internet Explorert webhelyekre lehessen irányítani.
- **Intranetes webhelyek automatikus észlelése** – Segít az intranetes webhelyek biztonságának konfigurálásában az Internet Explorerben.
- **Internetes biztonsági szint** – Az Internet Explorer internetes webhelyekre vonatkozó biztonsági szintjét állítja be.
- **Intranetes biztonsági szint** – Az Internet Explorer intranetes webhelyekre vonatkozó biztonsági szintjét állítja be.
- **Megbízható webhelyek biztonsági szintje** – A megbízható helyek zóna biztonsági szintjét állítja be.
- **Magas biztonsági szint korlátozott webhelyek esetén** – A tiltott helyek zóna biztonsági szintjét állítja be.
- **Vállalati üzemmód menüpont használata** – Engedélyezi a felhasználók számára a Vállalati üzemmód menü használatát.
Engedélyezése esetén meghatározhatja a **Naplózási jelentés helyét** is, ahol megtalálható annak a jelentésnek az URL-címe, amely megjeleníti azokat a webhelyeket, amelyekhez a felhasználók bekapcsolták a vállalati üzemmódot.
- **Vállalati üzemmód webhelylistájának helye** – Megadja azon webhelyek listáját, amelyek használják a vállalati üzemmódot, ha az aktív.

## <a name="cellular"></a>Mobil
- **Adatroaming** – Engedélyezi adatroaming használatát arra az esetre, ha az eszköz mobilhálózathoz csatlakozik.

## <a name="cloud-and-storage"></a>Felhő és tárolás
- **Munkamappák URL-címe** – Megadja a munkahelyi mappa URL-címét, hogy lehetővé tegye a dokumentumok szinkronizálását az eszközök között.
- **Windows Posta alkalmazás elérése Microsoft-fiók nélkül** – Microsoft-fiók nélkül is hozzáférhetővé teszi a Windows Posta alkalmazást.
