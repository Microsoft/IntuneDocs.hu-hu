---
title: "Általános hibaelhárítási tippek | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 6b2d1d5eecb543e45fca5fbb8aa1854c88ec4f9c


---

# Általános hibaelhárítási tippek a Microsoft Intune-hoz
Előfordulhat, hogy a Microsoft Intune telepítése után problémák merülnek fel a konfigurációval vagy az ügyfelekkel kapcsolatban. Az alábbi források megkönnyíthetik a probléma okának kiderítését.

> [!NOTE]
> Ha támogatási kérelmet szeretne létrehozni, vagy egy meglévő kérelmet kíván megtekinteni, [nyissa meg az Office 365 felügyeleti központját](https://portal.office.com/admin/default.aspx). A támogatási lehetőségekről a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben találhat további információkat.
## A probléma meghatározása

-   Milyen viselkedés tapasztalható?

-   Ki és milyen platformokon és eszközökön tapasztalja ezt a viselkedést?

-   Korábban megfelelően működött az eszköz?

-   Milyen módosításokat végzett az Intune vagy az eszköz konfigurációján?

-   Vizsgálja meg, hogy a konfigurációs módosításokon kívül történtek-e egyéb módosítások a működési környezetben.

-   Milyen gyakran fordul elő ez a probléma? Időszakosan vagy állandóan jelentkezik?

-   Tapasztal-e a felhasználó hitelesítési problémát? Ha lehetséges, ellenőrizze, hogy a felhasználó be tud-e jelentkezni az Azure Active Directoryt használó egyéb szolgáltatásokba. Azt is ellenőrizze, hogy a felhasználó be tud-e jelentkezni egy másik eszközről.

-   Ellenőrizte a szolgáltatás állapotát? Az [Office 365 felügyeleti portálon](https://portal.office.com/Admin/Default.aspx) az Intune szolgáltatás állapota is figyelemmel követhető. Válassza a bal oldali panel **Szolgáltatás állapota** elemét.

## Rendelkezésre álló adatok összegyűjtése

-   Eszköznaplók. Az eszköznaplók begyűjtésére vonatkozóan az alábbi témakörökből tájékozódhat:
  - [Az Android diagnosztikai adatait tartalmazó naplófájlok elküldése USB-kábelen keresztül a rendszergazdának](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Az Android diagnosztikai adatait tartalmazó naplófájlok elküldése e-mailben a rendszergazdának](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Az Android regisztrálási hibáinak elküldése a rendszergazdának](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [Az iOS regisztrálási hibáinak elküldése a rendszergazdának](/intune/enduser/send-errors-to-your-it-admin-ios)

-   A felügyeleti konzol adatai. A szabályzatok megvalósítási problémái esetén például meg kell vizsgálni az érintett szabályzatot, illetve annak állapotát a [Csoportok használata felhasználók és eszközök kezelésére a Microsoft Intune-nal](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune) című témakörben leírtak szerint.

## Megoldás keresése

-   Keressen megoldást az interneten. Ha például a 0x80073CF0 hibakódot kapja, rákereshet az interneten a **technet intune 0x80073cf0** kifejezésre, és elolvashatja az [Alkalmazástelepítéssel kapcsolatos problémák elhárítása a Microsoft Intune-ban](troubleshoot-app-deployment-problems-in-microsoft-intune.md) című témakört, amely javaslatokat kínál a probléma megoldásához.

-   Kérdéseire az [Intune TechNet fórumon](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod) is megkeresheti a választ.  Ha a kérdés korábban még nem merült fel, tegye fel azt, hátha a közösség hasznos javaslatokkal tud szolgálni.

-   Azt is megteheti, hogy támogatáskérést nyit. Az Intune támogatási szolgálata nagyobb segítséget tud nyújtani a probléma megoldásához, ha meghatározza a problémát, és összegyűjti az elérhető adatokat.

    Ha támogatási kérelmet szeretne létrehozni, nyissa meg az [Office 365 felügyeleti központját](https://portal.office.com/admin/default.aspx). A támogatási lehetőségekről a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben találhat további információkat.

## Közösségi erőforrások
A következő közösségi erőforrásokban találhat további hasznos információkat:

-   A [Microsoft Intune Survival Guide](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) (A Microsoft Intune túlélési útmutatója) számos olyan forrás hivatkozását tartalmazza, melyek segíthetnek az Intune konfigurálásában, karbantartásában és hibáinak elhárításában.

-   [Az Intune blogja](http://blogs.technet.com/b/windowsintune/)

-   [Kövesse Twitteren az Intune-t](https://twitter.com/MSIntune)

-   [Az Intune fórumai](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### További lépések
Az alább felsorolt témakörök konkrét problémák elhárításához nyújtanak segítséget. Ha ezek az információk nem segítettek megoldani a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben leírtak szerint.

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Munkahelyi erőforrás-hozzáférési problémák megoldása a Microsoft Intune-nal](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Alkalmazástelepítéssel kapcsolatos problémák elhárítása a Microsoft Intune-ban](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Eszközök regisztrálásával kapcsolatos problémák elhárítása az Intune-ban](troubleshoot-device-enrollment-in-intune.md)

[Szabályzatokkal kapcsolatos problémák elhárítása a Microsoft Intune-ban](troubleshoot-policies-in-microsoft-intune.md)

[Az ügyfél a Microsoft Intune-ban való beállításának hibaelhárítása](troubleshoot-client-setup-in-microsoft-intune.md)

[A Microsoft Intune szoftverfrissítéseinek hibaelhárítása](troubleshoot-software-updates-in-microsoft-intune.md)



<!--HONumber=Jul16_HO1-->


