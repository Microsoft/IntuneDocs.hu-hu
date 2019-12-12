---
title: Interaktív forgatókönyv – biztonságos Microsoft Office Mobile apps
titleSuffix: Microsoft Intune
description: Ismerkedjen meg a biztonságos Microsoft Office Mobile apps Microsoft 365 Eszközkezelő portálról történő üzembe helyezésének interaktív forgatókönyvével.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd02e2b7f9582308109d1e6986d7e6a8014e5af7
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585892"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Interaktív forgatókönyv – biztonságos Microsoft Office Mobile apps 

Ha ezt az útmutatást az Eszközkezelő portálon követi, az iOS-és Android-eszközökön is engedélyezheti az Intune-alkalmazások alapszintű védelmét.

Az Ön által engedélyezett alkalmazás-védelem a következő műveleteket fogja érvényesíteni: 
- A munkahelyi fájlok titkosítása.
- PIN-kód megkövetelése a munkahelyi fájlokhoz való hozzáféréshez.
- A PIN-kód öt sikertelen kísérlet után történő alaphelyzetbe állításának megkövetelése.
- A munkahelyi fájlok biztonsági mentésének letiltása iTunes-, iCloud-vagy Android-alapú biztonsági mentési szolgáltatásokban.  
- A munkahelyi fájlok csak a OneDrive vagy a SharePointba menthetők.
- A védett alkalmazások nem tudják betölteni a munkahelyi fájlokat a feltört vagy feltört eszközökön.
- A munkahelyi fájlokhoz való hozzáférés letiltása, ha az eszköz 720 percen keresztül offline állapotú.
- A munkahelyi fájlok eltávolítása, ha az eszköz 90 napig offline állapotú. 

## <a name="background"></a>Háttér

Az Office Mobile apps és a Microsoft Edge for Mobile is támogatja a kettős identitást. A kettős identitás lehetővé teszi, hogy az alkalmazások a munkahelyi fájlokat a személyes fájlokból külön kezeljék. 

![A vállalati adatok és a személyes adatok képe](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

Az [Intune app Protection-házirendek](~/apps/app-protection-policy.md) segítenek a munkahelyi fájlok védelmében az Intune-ban regisztrált eszközökön. Az alkalmazásvédelmi szabályzatokat emellett a munkatársak tulajdonában álló, az Intune-ban felügyeletre nem regisztrált eszközökön is alkalmazhatja. Ebben az esetben annak ellenére, hogy a vállalat nem felügyeli az eszközt, továbbra is meg kell győződnie arról, hogy a munkahelyi fájlok és erőforrások védve vannak.

Az alkalmazás-védelmi házirendek használatával megakadályozhatja, hogy a felhasználók a nem védett helyekről mentsenek munkahelyi fájlokat. Emellett korlátozható a más, alkalmazásvédelmi szabályzatokkal nem védett alkalmazásokba irányuló adattovábbítás. Íme néhány az alkalmazásvédelmi szabályzatok beállításai közül:
- Adatáthelyezési szabályzatok, például a Mentés másként művelet letiltása és a Kivágás, másolás és beillesztés korlátozása.
- Hozzáférési házirend-beállítások az egyszerű PIN-kód megkövetelése a hozzáféréshez, valamint a felügyelt alkalmazások futtatásának letiltása a feltört vagy feltört eszközökön.

Az alkalmazásalapú feltételes hozzáférés és az ügyfélalkalmazás-felügyelet egy további biztonsági réteget jelent, mivel gondoskodik róla, hogy csak az Intune alkalmazásvédelmi szabályzatait támogató mobilalkalmazások férhessenek hozzá az Exchange Online-hoz és más Office 365-szolgáltatásokhoz.

Azzal, hogy csak a Microsoft Outlook alkalmazásnak engedélyezi az Exchange Online elérését, blokkolhatja az iOS és az Android beépített levelezőalkalmazásait. Ezenfelül blokkolhatja az Intune alkalmazásvédelmi szabályzattal el nem látott alkalmazások SharePoint Online-elérését is.

Ebben a példában a rendszergazda alkalmazásvédelmi szabályzatokkal látta el az Outlook alkalmazást, majd egy feltételes hozzáférési szabállyal felvette az Outlookot a céges levelezés elérésére használható jóváhagyott alkalmazások listájára.

![Outlook-alkalmazás feltételes hozzáférésének folyamata](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Előfeltételek

Szüksége lesz az Intune rendszergazdai engedélyeinek követésére:

   - Felügyelt alkalmazások olvasási, létrehozási, törlési és hozzárendelési engedélyek
   - A házirend beállítja az olvasási, létrehozási és hozzárendelési engedélyeket
   - Szervezet olvasási engedélye

## <a name="step-1---introduction"></a>1\. lépés – bevezetés

Az **Intune app Protection** irányított forgatókönyv követésével megakadályozhatja, hogy az adatok a szervezeten kívül is megosszák vagy szivárognak. 

A hozzárendelt iOS-és Android-felhasználóknak minden alkalommal meg kell adniuk egy PIN-kódot, amikor megnyitnak egy Office-alkalmazást. 5 sikertelen PIN-kód próbálkozás után a felhasználóknak vissza kell állítania a PIN-kódját. Ha már megkövetelt egy eszköz PIN-kódját, a rendszer nem érinti a felhasználókat.

### <a name="what-you-will-need-to-continue"></a>A folytatáshoz szükséges művelet

Megkérjük, hogy a felhasználók által igényelt alkalmazásokról és az azokhoz való hozzáférésről mi szükséges. Győződjön meg arról, hogy a következő információk hasznosak:
- A vállalati használatra jóváhagyott Office-alkalmazások listája.
- A jóváhagyott alkalmazások nem felügyelt eszközökön való elindítására vonatkozó PIN-követelmények.

## <a name="step-2---basics"></a>2\. lépés – alapismeretek

Ebben a lépésben meg kell adnia az új alkalmazás-védelmi szabályzat **előtagját** és **leírását** . Az **előtag**hozzáadásakor a rendszer frissíti az interaktív forgatókönyv által létrehozott erőforrásokkal kapcsolatos részleteket. Ezekkel a részletekkel később könnyebben megtalálhatja a szabályzatokat, ha módosítania kell a hozzárendeléseket és a konfigurációt. 

> [!TIP]
> Vegye figyelembe a létrehozandó erőforrásokat, így később is hivatkozhat rájuk.

## <a name="step-3---apps"></a>3\. lépés – alkalmazások

Az első lépésekhez ez az interaktív forgatókönyv az iOS-és Android-eszközökön való védelemhez előre kiválasztja a következő mobil alkalmazásokat:
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

Ez az interaktív forgatókönyv ezeket az alkalmazásokat úgy konfigurálja, hogy a Microsoft Edge-ben nyissa meg a webhivatkozásokat, hogy a munkahelyeket egy védett böngészőben lehessen megnyitni.

Módosítsa a védelemmel ellátni kívánt szabályzat által felügyelt alkalmazások listáját. Alkalmazások hozzáadása vagy eltávolítása a listából. 

Ha kiválasztotta az alkalmazásokat, kattintson a **tovább**gombra.

## <a name="step-4---configuration"></a>4\. lépés – konfiguráció

Ebben a lépésben konfigurálnia kell a vállalati fájlok és e-mailek ezen alkalmazásokban való eléréséhez és megosztásához szükséges követelményeket. Alapértelmezés szerint a felhasználók menthetik az adatait a szervezet OneDrive és SharePoint-fiókjaiba.

| Beállítás | Description | Alapértelmezett érték |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| PIN-kód típusa | A numerikus PIN-kódok az összes számból állnak. A PIN-kódok alfanumerikus karakterekből és speciális karakterekből állnak.  IOS/iPadOS esetén a "PIN-kód" típus konfigurálásához az alkalmazásnak az Intune SDK 7.1.12 vagy újabb verziójára van szüksége. Numerikus típusú kód az Intune SDK bármelyik verziójával használható. | Numerikus |
| PIN-kód minimális hosszának kiválasztása | Meghatározza a számjegyek minimális számát a PIN-kód sorrendjében. | 6 |
| A hozzáférési követelmények ismételt ellenőrzési művelete (perc inaktivitás után) | Ha a házirend által felügyelt alkalmazás a megadott ennyi percnél hosszabb ideig inaktív, az alkalmazás kérni fogja a hozzáférési követelményeket (azaz PIN-kód, feltételes indítási beállítások) az alkalmazás elindítása után az ismételt vizsgálathoz. | 30 |
| Szervezeti adattárolók nyomtatása | Ha le van tiltva, az alkalmazás nem tudja kinyomtatni a védett adatforrásokat. | Letiltás |
| Szabályzat által felügyelt alkalmazások hivatkozásainak megnyitása nem felügyelt böngészőkben | Ha le van tiltva, a szabályzattal felügyelt alkalmazás hivatkozásait felügyelt böngészővel kell megnyitni. | Letiltás |
| Az Adatmásolás nem felügyelt alkalmazásokba | Ha le van tiltva, a felügyelt alkalmazások továbbra is a felügyelt alkalmazásokban maradnak. | Engedélyezés |

## <a name="step-5---assignments"></a>5\. lépés – hozzárendelések

Ebben a lépésben kiválaszthatja azokat a felhasználói csoportokat, amelyeket fel szeretne venni a vállalati adataihoz való hozzáférés biztosításához. Az alkalmazások védelme a felhasználókhoz és nem eszközökhöz van rendelve, így a vállalati adatai biztonságban lesznek, a használt eszköztől és a regisztrációs állapottól függetlenül.

Az alkalmazás-védelmi szabályzatok és a hozzárendelt feltételes hozzáférési beállítások nélküli felhasználók a vállalati profilból személyes alkalmazásokba és nem védett helyi tárhelyre menthetik az adatait a mobileszközökön. Emellett személyes alkalmazásokkal is csatlakozhatnak a vállalati adatszolgáltatásokhoz, például a Microsoft Exchange-hez.

## <a name="step-6---review--create"></a>6\. lépés – felülvizsgálat + létrehozás

Az utolsó lépés lehetővé teszi a konfigurált beállítások összefoglalásának áttekintését. Miután áttekintette a beállításokat, kattintson a **Létrehozás** gombra az interaktív forgatókönyv befejezéséhez. Miután az interaktív forgatókönyv elkészült, megjelenik egy táblázat az erőforrások között. Ezeket az erőforrásokat később is szerkesztheti, azonban ha elhagyja az összegző nézetet, a rendszer nem menti a táblát.

> [!IMPORTANT]
> Az interaktív forgatókönyv befejezését követően megjelenik egy Összegzés. Az összegzésben felsorolt erőforrásokat módosíthatja, azonban a osztályalapú megjelenítő tábla nem lesz mentve.
## <a name="next-steps"></a>További lépések

- A munkahelyi fájlok biztonságának javításához rendeljen hozzá egy alkalmazás-alapú feltételes hozzáférési szabályzatot a felhőalapú szolgáltatások számára a munkahelyi fájlok a nem védett alkalmazások számára történő küldéséhez. További információ: [alkalmazás-alapú feltételes hozzáférési szabályzatok létrehozása az Intune](~/protect/app-based-conditional-access-intune-create.md)-nal.

