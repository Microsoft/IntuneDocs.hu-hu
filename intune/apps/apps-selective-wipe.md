---
title: Csak a céges adatok törlése az alkalmazásokból
titleSuffix: Microsoft Intune
description: Learn how to selectively wipe only corporate data from Intune-managed apps with Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2019
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
ms.openlocfilehash: 0fafe7c17c698a5eb4e5ad6825bee0ae3fe874c2
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199234"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Csak vállalati adatok törlése az Intune által felügyelt alkalmazásokból

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ha egy eszközt elveszítenek vagy ellopnak, vagy ha a dolgozó elhagyja a vállalatot, fontos eltávolítani a vállalati alkalmazásadatokat az eszközről. Előfordul, hogy a személyes adatokat meg kell őrizni, különösen, ha az eszköz a dolgozó saját tulajdona.

>[!NOTE]
> The iOS, Android, and Windows 10 platforms are the only platforms currently supported for wiping corporate data from Intune managed apps. Intune managed apps are applications that include the Intune APP SDK and have a licensed user account for your organization. Deployment of Application Protection Policies are not required to enable app selective wipe.

A vállalati alkalmazásadatok szelektív törléséhez hozzon létre törlési kérést az ebben a témakörben leírt lépésekkel. A kérelem teljesítése után az alkalmazás a következő futtatásakor az eszközön a vállalati adatok törlődnek az alkalmazásból. Törlési kérelem létrehozásán kívül új műveletként konfigurálható a céges adatok szelektív törlése, ha az alkalmazásvédelmi szabályzatok (APP) hozzáférési beállításai nem teljesülnek. Ez a funkció lehetővé teszi, hogy a céges adatokat automatikusan védje vagy eltávolítsa az előre konfigurált feltételeken alapuló alkalmazásokról.

>[!IMPORTANT]
> Az alkalmazásból a natív címjegyzékbe közvetlenül szinkronizált névjegyeket a rendszer eltávolítja. A natív címjegyzékből egy másik külső forrásba szinkronizált névjegyek nem törölhetők. Ez jelenleg csak a Microsoft Outlook alkalmazásra érvényes.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Deployed WIP policies without user enrollment
Windows Information Protection (WIP) policies can be deployed without requiring MDM users to enroll their Windows 10 device. Ez a konfiguráció lehetővé teszi, hogy a vállalatok biztosítsák a vállalati dokumentumok védelmét a WIP-konfiguráció alapján, miközben a felhasználó saját maga felügyelheti Windows-eszközeit. Ha a dokumentumok védve vannak WIP-szabályzattal, a védett adatokat az Intune-rendszergazdák szelektív módon törölhetik. Ehhez ki kell választaniuk a felhasználót és az eszközt, majd el kell küldeniük egy adattörlési kérést, amelynek hatására WIP-szabályzat által védett összes adat használhatatlanná válik. From the Intune in the Azure portal, select **Client app** > **App selective wipe**. További információ: [A Windows Információvédelem (WIP) alkalmazásvédelmi szabályzatainak létrehozása és bevezetése az Intune használatával](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Törlési kérés

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. In the Intune pane, select **Client apps** > **App selective wipe** > **Create wipe request**.<br>
   The **Create wipe request** pane is displayed.
3. Click **Select the user**, choose the user whose app data you want to wipe, and click **Select** at the bottom of the **User** pane.
4. Click **Select the device**, choose the device, and click **Select** at the bottom of the **Select Device** pane.
5. Click **Create** to make a wipe request.

A szolgáltatás külön törlési kéréseket hoz létre az egyes védett alkalmazásokhoz az eszközön és a törlési kéréshez társított felhasználóhoz, és nyomon követi azokat.

## <a name="monitor-your-wipe-requests"></a>A törlési kérelmek figyelése

Elérhető egy összesítő jelentés is, amely a törlési kérelem összesített állapotát jeleníti meg, és tartalmazza a függőben lévő kérések és a hibák számát. Ha további részleteket szeretne megismerni, kövesse az alábbi lépéseket:

1. Az **Ügyfélalkalmazások – Alkalmazás szelektív törlése** panelen felhasználók szerint csoportosítva látható a kérések listája. A rendszer minden, az eszközön futó védett alkalmazáshoz külön törlési kérést hoz létre, ezért több kérés jelenhet meg ugyanannál a felhasználónál. Az állapot mutatja, hogy a törlési kérés **függőben van**, **sikertelen**, vagy **sikeres**.

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
