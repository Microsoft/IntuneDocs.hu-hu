---
title: Csak a céges adatok törlése az alkalmazásokból
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan törölheti az Intune által felügyelt alkalmazásokból származó vállalati adatok szelektív törlését Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f444288e46a933576606429f170753217182e78
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/19/2019
ms.locfileid: "71305314"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Csak vállalati adatok törlése az Intune által felügyelt alkalmazásokból

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ha egy eszközt elveszítenek vagy ellopnak, vagy ha a dolgozó elhagyja a vállalatot, fontos eltávolítani a vállalati alkalmazásadatokat az eszközről. Előfordul, hogy a személyes adatokat meg kell őrizni, különösen, ha az eszköz a dolgozó saját tulajdona.

>[!NOTE]
> Az iOS, az Android és a Windows 10 platform az egyetlen olyan platform, amely jelenleg támogatott a vállalati adatok Intune által felügyelt alkalmazásokból való törléséhez. Az Intune által felügyelt alkalmazások olyan alkalmazások, amelyek tartalmazzák az Intune APP SDK-t, és rendelkeznek egy licenccel rendelkező felhasználói fiókkal a szervezet számára. Az alkalmazás-védelmi házirendek telepítése nem szükséges az alkalmazás szelektív törlésének engedélyezéséhez.

A vállalati alkalmazásadatok szelektív törléséhez hozzon létre törlési kérést az ebben a témakörben leírt lépésekkel. A kérelem teljesítése után az alkalmazás a következő futtatásakor az eszközön a vállalati adatok törlődnek az alkalmazásból. Törlési kérelem létrehozásán kívül új műveletként konfigurálható a céges adatok szelektív törlése, ha az alkalmazásvédelmi szabályzatok (APP) hozzáférési beállításai nem teljesülnek. Ez a funkció lehetővé teszi, hogy a céges adatokat automatikusan védje vagy eltávolítsa az előre konfigurált feltételeken alapuló alkalmazásokról.

>[!IMPORTANT]
> Az alkalmazásból a natív címjegyzékbe közvetlenül szinkronizált névjegyeket a rendszer eltávolítja. A natív címjegyzékből egy másik külső forrásba szinkronizált névjegyek nem törölhetők. Ez jelenleg csak a Microsoft Outlook alkalmazásra érvényes.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Felhasználói regisztráció nélkül telepített, folyamatban lévő befejező házirendek
A Windows Information Protection (folyamatban lévő) házirendek telepítése anélkül végezhető el, hogy MDM-felhasználóknak kellene regisztrálniuk Windows 10-es eszközét. Ez a konfiguráció lehetővé teszi, hogy a vállalatok biztosítsák a vállalati dokumentumok védelmét a WIP-konfiguráció alapján, miközben a felhasználó saját maga felügyelheti Windows-eszközeit. Ha a dokumentumok védve vannak WIP-szabályzattal, a védett adatokat az Intune-rendszergazdák szelektív módon törölhetik. Ehhez ki kell választaniuk a felhasználót és az eszközt, majd el kell küldeniük egy adattörlési kérést, amelynek hatására WIP-szabályzat által védett összes adat használhatatlanná válik. A Azure Portal Intune-ban válassza az **ügyfél** > -alkalmazás**szelektív törlés**lehetőséget. További információ: [A Windows Információvédelem (WIP) alkalmazásvédelmi szabályzatainak létrehozása és bevezetése az Intune használatával](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Törlési kérés

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).

2. Válassza a **Minden szolgáltatás** lehetőséget, a szűrési szövegmezőbe írja be az **Intune** szót, majd válassza az **Intune** elemet. Amikor megjelenik az Intune panel, válassza az **Ügyfélalkalmazások** panelt.

    ![A Microsoft Intune panel képernyőképe](./media/apps-selective-wipe01.png)

3. Az **Ügyfélalkalmazások panelen** válassza az **Alkalmazás szelektív törlése** lehetőséget.

4. Kattintson az **Új törlési kérés** lehetőségre. Ennek hatására megnyílik az **Új törlési kérés** panel.

    ![Képernyőfelvétel: Az Új törlési kérés panel](./media/AzurePortal_MAM_NewWipeRequest.png)

5. Válasszon egy felhasználót, majd válassza a **Kijelölés** lehetőséget annak a felhasználónak a megadásához, akinek az alkalmazásadatait törölni kívánja.

6. Ezután válassza az **Eszköz** lehetőséget az **Új törlési kérés** panelen. Ekkor megnyílik az **Eszköz kiválasztása** panel, amelyen látható a választott felhasználóhoz társított összes eszköz listája, valamint két oszlop is: az eszköznév, amely az eszköz felhasználó által definiált rövid neve, és az eszköztípus, amely az eszközplatformot mutatja. Válassza ki a törölni kívánt eszközt.

7. Ekkor ismét az **Új törlési kérés** panel jelenik meg. A törlési kérés elindításához kattintson az **OK** gombra.

A szolgáltatás külön törlési kéréseket hoz létre az egyes védett alkalmazásokhoz az eszközön és a törlési kéréshez társított felhasználóhoz, és nyomon követi azokat.

## <a name="monitor-your-wipe-requests"></a>A törlési kérelmek figyelése

Elérhető egy összesítő jelentés is, amely a törlési kérelem összesített állapotát jeleníti meg, és tartalmazza a függőben lévő kérések és a hibák számát. Ha további részleteket szeretne megismerni, kövesse az alábbi lépéseket:

1. Az **Ügyfélalkalmazások – Alkalmazás szelektív törlése** panelen felhasználók szerint csoportosítva látható a kérések listája. A rendszer minden, az eszközön futó védett alkalmazáshoz külön törlési kérést hoz létre, ezért több kérés jelenhet meg ugyanannál a felhasználónál. Az állapot mutatja, hogy a törlési kérés **függőben van**, **sikertelen**, vagy **sikeres**.

    ![Képernyőkép a törlési kérés állapotáról az Alkalmazások szelektív törlése panelen](./media/wipe-request-status-1.png)

Ezen kívül látható az eszköz neve és típusa is, ami megkönnyíti a jelentések olvasását.

>[!IMPORTANT]
> A törléshez a felhasználónak meg kell nyitnia az alkalmazást, ami a kéréstől számítva akár 30 percig is eltarthat.

## <a name="delete-a-wipe-request"></a>Törlési kérés törlése

A felfüggesztett állapotú törlés addig lesz megjelenítve, míg manuálisan nem törli. Törlési kérés manuális törléséhez:

1. Nyissa meg az **Ügyfélalkalmazások – Alkalmazás szelektív törlése** panelt.

2. Kattintson a listában a jobb gombbal a törölni kívánt törlési kérésre, és válassza a **Törlési kérés törlése** lehetőséget.

    ![Képernyőkép a törlési kérések listájáról az Alkalmazások szelektív törlése panelen](./media/delete-wipe-request.png)

3. Ha a rendszer törlési megerősítést kér, válassza az **Igen** vagy a **Nem** lehetőséget, majd kattintson az **OK** gombra.

## <a name="see-also"></a>Lásd még:
[Mi az alkalmazásvédelmi szabályzat?](app-protection-policy.md)

[Mi az alkalmazáskezelés?](app-management.md)
