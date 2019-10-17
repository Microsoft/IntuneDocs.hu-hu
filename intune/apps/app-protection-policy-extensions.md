---
title: Alkalmazás-védelmi szabályzatok bővítményekhez
titleSuffix: Microsoft Intune
description: Ez a témakör a bővítmények alkalmazás-védelmi szabályzatát (alkalmazást) ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a94f3d175fe5c036c5e90635a66467263b23122
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499115"
---
# <a name="protecting-application-extensions"></a>Az alkalmazások bővítményeinek védelme

Ez a cikk a Microsoft Intune bővítmények alkalmazás-védelmi házirendjeit ismerteti.

## <a name="add-ins-for-outlook-app"></a>Bővítmények az Outlook alkalmazáshoz

Az Outlook-bővítmények lehetővé teszik a népszerű alkalmazások integrálását az e-mail-ügyfélprogrammal. Az Outlook-bővítmények a web, a Windows, a Mac és az Outlook alkalmazásban érhetők el az Android és az iOS rendszerhez. Az Intune APP SDK és az Intune app Protection-szabályzatok nem támogatják a bővítmények Outlookhoz való felügyeletének támogatását, de a használatuk korlátozásának más módjai is vannak. Mivel a bővítmények felügyelete a Microsoft Exchange-en keresztül történik, a felhasználók megoszthatnak adatokat és üzeneteket az Outlook és a nem felügyelt bővítményalkalmazások között, kivéve ha az adott felhasználónál ki vannak kapcsolva a bővítmények az Exchange-ben.

Ha szeretné beszüntetni a végfelhasználók számára az Outlook-bővítmények elérését és telepítését (ez hatással van az összes Outlook-ügyfélre), az Exchange felügyeleti központban végezze el a következő szerepkör-módosításokat:

- Az Office Áruház bővítményeinek telepítését úgy gátolhatja meg, hogy a felhasználóktól megvonja a My Marketplace (Saját piactér) szerepkört.
- A bővítményeinek közvetlen telepítését úgy gátolhatja meg, hogy a felhasználóktól megvonja a My Custom Apps (Saját egyéni alkalmazások) szerepkört.
- Amennyiben az összes bővítmény telepítését meg szeretné akadályozni a felhasználók számára, mind a Saját egyéni alkalmazások, mind a Saját piactér szerepkört távolítsa el.

Ezek az utasítások az Office 365, az Exchange 2016, az Exchange 2013 alkalmazásra vonatkoznak a web, a Windows, a Mac és a Mobile rendszeren.

- További információ [az Outlook bővítményeiről](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- További információ arról, [hogyan lehet kijelölni azokat a rendszergazdákat és felhasználókat, akik Outlook-bővítményeket telepíthetnek és kezelhetnek](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

## <a name="linkedin-account-connections-for-microsoft-apps"></a>LinkedIn-fiókkapcsolatok Microsoft-alkalmazásokban

A LinkedIn-fiókkapcsolatok lehetővé teszik a felhasználóknak a nyilvános LinkedIn-profiladatok megtekintését bizonyos Microsoft-alkalmazásokban. Alapértelmezés szerint a felhasználók dönthetnek úgy, hogy összekötik a LinkedIn-fiókjukat a munkahelyi vagy iskolai Microsoft-fiókjukkal további LinkedIn-profiladatok eléréséhez. 

> [!NOTE]
> A LinkedIn-integráció jelenleg nem érhető el az egyesült államokbeli ügyfeleknek, illetve azon szervezeteknek, amelyek Exchange Online-postaládái a következő országokban üzemelnek: Ausztrália, Kanada, Kína, Franciaország, Németország, India, Dél-Korea, Egyesült Királyság, Japán és Dél-Afrika.

Az Intune App SDK és az Intune alkalmazásvédelmi szabályzatai nem támogatják a LinkedIn-fiókkapcsolatok kezelését, más módon azonban lehetséges kezelni őket. Letilthatja a LinkedIn-fiókkapcsolatokat a teljes szervezete számára, vagy engedélyezheti a LinkedIn-fiókkapcsolatokat kizárólag a szervezete bizonyos felhasználói csoportjainak. Ezek a beállítások az összes Office 365-alkalmazásban és minden platformon (böngészőben, mobileszközön és asztali gépen is) érvényesek a LinkedIn-kapcsolatokra. A következőket teheti:

- Engedélyezheti vagy letilthatja a LinkedIn-fiókkapcsolatokat a bérlőjében az Azure Portalon keresztül. 
- Engedélyezheti vagy letilthatja a LinkedIn-fiókkapcsolatokat a szervezete Office 2016-alkalmazásaiban csoportházirend használatával.

Ha a LinkedIn-integráció engedélyezve van a bérlőjében, akkor a LinkedIn-fiókjukat a munkahelyi vagy iskolai Microsoft-fiókjukkal összekötő szervezeti felhasználók két lehetőség közül választhatnak: 

- Engedélyezhetik az adatok két fiók közötti kétirányú megosztását. Ez azt jelenti, hogy engedélyezik a LinkedIn-fiókjuknak, hogy adatokat osszon meg a munkahelyi vagy iskolai Microsoft-fiókjukkal, illetve a munkahelyi vagy iskolai Microsoft-fiókjuknak, hogy adatokat osszon meg a LinkedIn-fiókjukkal. A LinkedIn szolgáltatással megosztott adatok elhagyják az online szolgáltatásokat. 
- Engedélyezhetik az adatok egyirányú megosztását, a LinkedIn-fiókjukból a munkahelyi vagy iskolai Microsoft-fiókjukba

Ha egy felhasználó hozzájárul az adatok fiókok közötti megosztásához, akkor a LinkedIn-integráció – az Office-bővítményekhez hasonlóan – a meglévő Microsoft Graph API-kat használja. A LinkedIn-integráció az Office-bővítmények számára elérhető API-knak csak egy részhalmazát használja, és támogatja a különféle kizárásokat.


|Microsoft Graph-engedélyek  |Description  |
|---------|---------|
|[Személyek](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions) olvasásának engedélyezése     |Engedélyezi az alkalmazásnak a bejelentkezett felhasználó számára releváns személyek pontozott listájának olvasását. A lista tartalmazhat helyi kapcsolatokat, közösségi hálózati kapcsolatokat, szervezeti címjegyzékbeli kapcsolatokat, illetve olyan személyeket, akikkel a felhasználó nemrég kommunikált (például e-mailben vagy Skype-on).         |
|[Naptárak](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions) olvasásának engedélyezése     |Engedélyezi az alkalmazásnak a felhasználó naptáraiban lévő események olvasását. Ideértve például a bejelentkezett felhasználó naptárában lévő értekezleteket, azok időpontjával, helyével és résztvevőivel együtt.         |
|[Felhasználói profilok](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions) olvasásának engedélyezése     |Engedélyezi a felhasználóknak az alkalmazásba való bejelentkezést, és engedélyezi az alkalmazásnak a bejelentkezett felhasználók profiljának olvasását. Emellett engedélyezi az alkalmazásnak a bejelentkezett felhasználók alapvető vállalati adatainak olvasását is.         |
|Subscriptions     |Ez a hatókör jelenleg nem érhető el, és nincs használatban. Ide tartoznak a felhasználó szervezete által nyújtott előfizetések a különféle Microsoft-alkalmazásokra és -szolgáltatásokra, ideértve például az Office 365-öt is.         |
|Insights     |Ez a hatókör jelenleg nem érhető el, és nincs használatban. Ide tartoznak a bejelentkezett felhasználói fiókhoz kapcsolódó érdeklődési körök, melyek a Microsoft-szolgáltatások használati adatain alapulnak.         |

### <a name="learn-more"></a>További információ

- Tudjon meg többet a [Microsoft-alkalmazásokban használható LinkedIn-adatokról és -funkciókról](https://go.microsoft.com/fwlink/?linkid=850740).
- Ismerje meg a LinkedIn-fiókkapcsolatok megjelenésének részleteit az [Office 365 fejlesztési ütemtervének lapján](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc). 
- Tudja meg, hogyan [konfigurálhatja a LinkedIn-fiókkapcsolatokat](https://docs.microsoft.com/azure/active-directory/linkedin-integration).
- A felhasználók LinkedIn-fiókja és munkahelyi vagy iskolai Microsoft-fiókja közötti adatmegosztásról bővebben a következő témakörben olvashat: [LinkedIn használata munkahelyi vagy iskolai Microsoft-alkalmazásokban ](https://www.linkedin.com/help/linkedin/answer/84077).

