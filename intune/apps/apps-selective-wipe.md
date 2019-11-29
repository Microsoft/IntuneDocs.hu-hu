---
title: Csak a céges adatok törlése az alkalmazásokból
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan törölheti az Intune által felügyelt alkalmazásokból származó vállalati adatok szelektív törlését Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c0ca82b434b83937c7962b2676ce3c2a12c1424
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564005"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Csak vállalati adatok törlése az Intune által felügyelt alkalmazásokból

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ha egy eszközt elveszítenek vagy ellopnak, vagy ha a dolgozó elhagyja a vállalatot, fontos eltávolítani a vállalati alkalmazásadatokat az eszközről. Előfordul, hogy a személyes adatokat meg kell őrizni, különösen, ha az eszköz a dolgozó saját tulajdona.

>[!NOTE]
> Az iOS, az Android és a Windows 10 platform az egyetlen olyan platform, amely jelenleg támogatott a vállalati adatok Intune által felügyelt alkalmazásokból való törléséhez. Az Intune által felügyelt alkalmazások olyan alkalmazások, amelyek tartalmazzák az Intune APP SDK-t, és rendelkeznek egy licenccel rendelkező felhasználói fiókkal a szervezet számára. Az alkalmazás-védelmi házirendek telepítése nem szükséges az alkalmazás szelektív törlésének engedélyezéséhez.

A vállalati alkalmazásadatok szelektív törléséhez hozzon létre törlési kérést az ebben a témakörben leírt lépésekkel. A kérelem teljesítése után az alkalmazás a következő futtatásakor az eszközön a vállalati adatok törlődnek az alkalmazásból. Törlési kérelem létrehozásán kívül új műveletként konfigurálható a céges adatok szelektív törlése, ha az alkalmazásvédelmi szabályzatok (APP) hozzáférési beállításai nem teljesülnek. Ez a funkció lehetővé teszi, hogy a céges adatokat automatikusan védje vagy eltávolítsa az előre konfigurált feltételeken alapuló alkalmazásokról.

>[!IMPORTANT]
> Az alkalmazásból a natív címjegyzékbe közvetlenül szinkronizált névjegyeket a rendszer eltávolítja. A natív címjegyzékből egy másik külső forrásba szinkronizált névjegyek nem törölhetők. Ez jelenleg csak a Microsoft Outlook alkalmazásra érvényes.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Felhasználói regisztráció nélkül telepített, folyamatban lévő befejező házirendek
A Windows Information Protection (folyamatban lévő) házirendek telepítése anélkül végezhető el, hogy MDM-felhasználóknak kellene regisztrálniuk Windows 10-es eszközét. Ez a konfiguráció lehetővé teszi, hogy a vállalatok biztosítsák a vállalati dokumentumok védelmét a WIP-konfiguráció alapján, miközben a felhasználó saját maga felügyelheti Windows-eszközeit. Ha a dokumentumok védve vannak WIP-szabályzattal, a védett adatokat az Intune-rendszergazdák szelektív módon törölhetik. Ehhez ki kell választaniuk a felhasználót és az eszközt, majd el kell küldeniük egy adattörlési kérést, amelynek hatására WIP-szabályzat által védett összes adat használhatatlanná válik. A Azure Portal Intune-ban válassza az **ügyfélalkalmazás** > **alkalmazás szelektív törlés**lehetőséget. További információ: [A Windows Információvédelem (WIP) alkalmazásvédelmi szabályzatainak létrehozása és bevezetése az Intune használatával](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Törlési kérés

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **alkalmazás szelektív törlés** > **törlési kérelem létrehozása**lehetőséget.<br>
   Megjelenik a **törlési kérelem létrehozása** panel.
3. Kattintson a **felhasználó kiválasztása**lehetőségre, válassza ki azt a felhasználót, akinek az alkalmazási adatát törölni szeretné, **majd kattintson a Kiválasztás gombra** a **felhasználó kiválasztása** ablaktábla alján.

    ![Képernyőfelvétel a "felhasználó kiválasztása" panelről](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. Kattintson az eszköz **kijelölése**lehetőségre, válassza ki az eszközt, majd az **eszköz kiválasztása** panel alján kattintson a **kiválasztás** elemre.

    ![Képernyőkép a "törlési kérelem létrehozása" panelről, ahol az eszköz ki van választva](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. Kattintson a **Létrehozás** elemre a törlési kérelem elvégzéséhez.

A szolgáltatás külön törlési kéréseket hoz létre az egyes védett alkalmazásokhoz az eszközön és a törlési kéréshez társított felhasználóhoz, és nyomon követi azokat.

   ![Képernyőfelvétel: "Client apps – alkalmazás szelektív törlése" panel](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>A törlési kérelmek figyelése

Elérhető egy összesítő jelentés is, amely a törlési kérelem összesített állapotát jeleníti meg, és tartalmazza a függőben lévő kérések és a hibák számát. Ha további részleteket szeretne megismerni, kövesse az alábbi lépéseket:

1. Az **alkalmazások** > **alkalmazás szelektív törlés** paneljén megtekintheti a kérelmek felhasználók szerint csoportosított listáját. A rendszer minden, az eszközön futó védett alkalmazáshoz külön törlési kérést hoz létre, ezért több kérés jelenhet meg ugyanannál a felhasználónál. Az állapot mutatja, hogy a törlési kérés **függőben van**, **sikertelen**, vagy **sikeres**.

    ![Képernyőkép a törlési kérés állapotáról az Alkalmazások szelektív törlése panelen](./media/apps-selective-wipe/wipe-request-status-1.png)

Ezen kívül látható az eszköz neve és típusa is, ami megkönnyíti a jelentések olvasását.

>[!IMPORTANT]
> A törléshez a felhasználónak meg kell nyitnia az alkalmazást, ami a kéréstől számítva akár 30 percig is eltarthat.

## <a name="delete-a-wipe-request"></a>Törlési kérés törlése

A felfüggesztett állapotú törlés addig lesz megjelenítve, míg manuálisan nem törli. Törlési kérés manuális törléséhez:

1. Nyissa meg az **Ügyfélalkalmazások – Alkalmazás szelektív törlése** panelt.

2. Kattintson a listában a jobb gombbal a törölni kívánt törlési kérésre, és válassza a **Törlési kérés törlése** lehetőséget.

    ![Képernyőkép a törlési kérések listájáról az Alkalmazások szelektív törlése panelen](./media/apps-selective-wipe/delete-wipe-request.png)

3. Ha a rendszer törlési megerősítést kér, válassza az **Igen** vagy a **Nem** lehetőséget, majd kattintson az **OK** gombra.

## <a name="see-also"></a>További információ
[Mi az alkalmazásvédelmi szabályzat?](app-protection-policy.md)

[Mi az alkalmazáskezelés?](app-management.md)
