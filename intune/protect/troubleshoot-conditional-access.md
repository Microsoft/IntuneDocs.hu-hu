---
title: A feltételes hozzáférés hibaelhárítása
titleSuffix: Microsoft Intune
description: Mi a teendő, ha a felhasználók nem tudnak hozzáférni az erőforrásokhoz az Intune feltételes hozzáférésével.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4a1d0575ce4c46c56fd1b3d2a7526a18a076fcf
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576127"
---
# <a name="troubleshoot-conditional-access"></a>A feltételes hozzáférés hibaelhárítása
Ez a cikk azt ismerteti, mi a teendő, ha a felhasználók nem férhetnek hozzá a feltételes hozzáféréssel védett erőforrásokhoz, vagy ha a felhasználók hozzáférhetnek a védett erőforrásokhoz, de le kell tiltani őket.

Az Intune-nal és a feltételes hozzáféréssel a következő szolgáltatásokhoz férhet hozzá:
- Office 365-szolgáltatások, mint például az Exchange Online, a SharePoint Online és a Skype vállalati online verzió
- Helyszíni Exchange
- Különböző egyéb szolgáltatások

Ezzel a funkcióval biztos lehet abban, hogy csak az Intune-ban regisztrált és az Intune felügyeleti konzolján beállított feltételes hozzáférési szabályoknak megfelelő, illetve Azure Active Directory hozzáférnek a vállalati erőforrásokhoz. 

## <a name="requirements-for-conditional-access"></a>A feltételes hozzáférésre vonatkozó követelmények

A feltételes hozzáférés működéséhez az alábbi követelményeknek kell teljesülniük:

- Az eszközt regisztrálni kell a MDM-be, és az Intune-nak kell kezelnie.

- A felhasználónak és az eszköznek is meg kell felelnie az Intune-ban hozzájuk rendelt megfelelőségi szabályzatoknak.

- Alapértelmezés szerint lennie kell egy, a felhasználóhoz hozzárendelt eszközmegfelelőségi szabályzatnak. Ez a beállítás attól függ, hogy az eszközök az Intune felügyeleti portálon az **eszköz megfelelősége** > **megfelelőségi** szabályzata beállításnál megadott **megfelelőségi házirend nélkül legyenek megjelölve** .

- Az eszközön aktiválni kell az Exchange ActiveSync protokollt, ha a felhasználó nem az Outlookot, hanem az eszköz natív levelezőprogramját használja. Ez automatikusan megtörténik iOS/iPadOS, Windows Phone-telefon és Android Knox rendszerű eszközök esetén.

- Helyszíni Exchange esetén az Intune Exchange-összekötőt megfelelően kell konfigurálni. További információ: [az Exchange Connector hibaelhárítása Microsoft Intuneban](troubleshoot-exchange-connector.md).

- Helyszíni Skype esetén be kell állítania a hibrid modern hitelesítést. Lásd: [hibrid modern hitelesítés – áttekintés](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview).

Az egyes eszközökre vonatkozó feltételek megtekinthetők az Azure Portalon, valamint a Mobileszközkészlet-jelentésben.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Az eszközök megfelelőként jelennek meg, de a felhasználók továbbra is le vannak tiltva

- Győződjön meg arról, hogy a felhasználó rendelkezik Intune-licenccel a megfelelő megfelelőség kiértékeléséhez.

- A nem Knox Android-eszközök nem kapnak hozzáférést, amíg a felhasználó az első **lépések** hivatkozásra kattint a kapott karanténba helyezett e-mailben. Ez akkor is érvényes, ha a felhasználó már regisztrálva van az Intune-ban. Ha a felhasználó nem kapja meg az e-mailt a telefonon található hivatkozással, akkor a számítógép használatával hozzáférhet az e-mailekhez, és továbbíthatja azt az eszközön lévő e-mail-fiókba.

- Az eszköz első regisztrálásakor a megfelelőségi adatok rögzítése az eszközhöz időbe telhet. Várjon néhány percet, és próbálkozzon újra.

- IOS-/iPadOS-eszközök esetén a meglévő e-mail-profil letilthatja az Intune-rendszergazda által létrehozott e-mail-profil üzembe helyezését, így az eszköz nem megfelelőnek bizonyulhat. Ebben az esetben a Céges portál alkalmazás értesíti a felhasználót, hogy a manuálisan konfigurált e-mail-profil miatt nem felel meg a felhasználónak, és felszólítja a felhasználót, hogy távolítsa el a profilt. Miután a felhasználó eltávolította a meglévő e-mail-profilt, az Intune e-mail-profilja sikeresen üzembe helyezhető. A probléma megelőzése érdekében kérje meg a felhasználókat, hogy regisztráció előtt távolítsanak el minden meglévő e-mail-profilt az eszközről.

- Előfordulhat, hogy az eszköz egy ellenőrzési megfelelőségi állapotba kerül, és megakadályozza, hogy a felhasználó másik bejelentkezést indítson el. Ha ebben az állapotban van egy eszköz:
  - Győződjön meg róla, hogy az eszköz a Céges portál alkalmazás legújabb verzióját használja.
  - Indítsa újra az eszközt.
  - Ellenőrizze, hogy a probléma a különböző hálózatokon (például mobil, Wi-Fi stb.) továbbra is fennáll-e.

  Ha a probléma nem szűnik meg, lépjen kapcsolatba a Microsoft ügyfélszolgálatával a [támogatás kérése a Microsoft Intune-hoz](../fundamentals/get-support.md) szakaszban leírtak szerint.

- Előfordulhat, hogy bizonyos Android-eszközök titkosítva vannak, azonban a Céges portál alkalmazás nem titkosítottként ismeri fel ezeket az eszközöket, és nem megfelelőként jelöli meg őket. Ebben a forgatókönyvben a felhasználó számára a Céges portál alkalmazás értesítést jelenít meg, kérve egy indítási PIN-kód beállítását az eszközhöz. Koppintson az értesítésre, és a meglévő PIN-kód vagy a jelszó ellenőrzése után válassza a **Require PIN to start device** (PIN-kód kérése az eszköz indításához) beállítást a **Secure start-up** (Biztonságos indítás) képernyőn, majd koppintson a Céges portál alkalmazásban a **Megfelelőség ellenőrzése** gombra az eszköznél. Az eszközt ettől kezdve titkosítottként kell, hogy észlelje a program. 

  > [!NOTE]
  > Egyes eszközök gyártói a felhasználó által beállított PIN-kód helyett az alapértelmezett PIN-kód használatával titkosítják az eszközeiket. Az Intune-nézetek titkosítása alapértelmezett PIN-kódot használ, és nem megfelelőként jelöli meg ezeket az eszközöket, amíg a felhasználó nem hoz létre új, nem alapértelmezett PIN-kódot.

- A regisztrált és megfelelő Android-eszközök továbbra is blokkolva lehetnek, és a vállalati erőforrásokhoz való első próbálkozáskor karanténra vonatkozó értesítést kapnak. Ha ez történik, győződjön meg arról, hogy a Céges portál alkalmazás nem fut, majd válassza az **első lépések** hivatkozást a karanténba helyezett e-mailben a kiértékelés elindításához. Ezt csak akkor kell elvégezni, amikor először engedélyezi a feltételes hozzáférést.

- Egy regisztrált Android-eszköz felkérheti a felhasználót, hogy "nem található tanúsítvány", és nem kap hozzáférést a O365-erőforrásokhoz. A felhasználónak engedélyeznie kell a *böngészőalapú hozzáférés engedélyezése* beállítást a regisztrált eszközön a következőképpen:
  1. Nyissa meg a Vállalati portál alkalmazást.
  2. Nyissa meg a beállítások lapot a három pont (...) vagy a hardver menü gombján.
  3. Válassza a *böngésző hozzáférésének engedélyezése* gombot.
  4. A Chrome böngészőben jelentkezzen ki az Office 365-ből, majd indítsa újra a Chrome-ot.  


## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Az eszközök le vannak tiltva, és nem érkezett karanténba helyezési e-mail

- Ellenőrizze, hogy az eszköz az Intune felügyeleti konzolján Exchange ActiveSync-eszközként jelenik-e meg. Ha nem, akkor valószínű, hogy az eszköz felderítése sikertelen, feltehetően egy Exchange Connectorral kapcsolatos probléma miatt. További információ: [az Intune helyszíni Exchange Connector hibáinak megoldása](troubleshoot-exchange-connector.md).

- Mielőtt az Exchange Connector zárolná az eszközt, aktiválási (karantén) e-mailt küld. Ha az eszköz offline állapotban van, előfordulhat, hogy nem kapja meg az aktiválási e-mailt. 

- Ellenőrizze, hogy az eszköz levelező alkalmazásában az e-mailek fogadásának beállításaként a **Leküldéses** van-e megadva a **Lekérdezéses** helyett. Ha igen, ez okozhatja, hogy a felhasználó nem kapja meg az e-mailt. Váltson **Lekérdezéses** módra, és ellenőrizze, hogy az eszköz megkapja-e az e-mailt.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Az eszközök nem megfelelőek, de a felhasználók nincsenek letiltva

- Windows rendszerű számítógépek esetén a feltételes hozzáférés csak a natív e-mail-alkalmazást, az Office 2013-et és a modern hitelesítést, vagy az Office 2016 blokkolja. Az Outlook korábbi verzióinak, illetve a Windows rendszerű számítógépeken futó összes levelezési alkalmazásnak az HRE és a Active Directory összevonási szolgáltatások (AD FS) (AD FS) konfigurációkat kell megkövetelni a [SharePoint Online és az Exchange Online Azure Active Directory feltételes hozzáférés beállításakor](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication).

- Ha egy kiválasztott eszköz összes adatát törli vagy kivonja azt az Intune felügyelete alól, a kivonást követően még több órán keresztül rendelkezhet hozzáféréssel. Ennek az az oka, hogy az Exchange hat órán keresztül gyorsítótárazza a hozzáférési jogosultságokat. Ebben az esetben érdemes más adatvédelmi megoldást keresnie a kivont eszközökre.

- A Surface Hub, a tömegesen regisztrált és a DEM-ben regisztrált Windows-eszközök támogatják a feltételes hozzáférést, ha az Intune-licenccel rendelkező felhasználó be van jelentkezve. A megfelelőségi szabályzatot azonban az eszközök csoportjaira (nem felhasználói csoportokra) kell telepíteni a megfelelő kiértékeléshez.

- Ellenőrizze a megfelelőségi szabályzatok és a feltételes hozzáférési szabályzatok hozzárendeléseit. Ha a felhasználó nincs abban a csoportban, amely a szabályzatokhoz van rendelve, vagy egy kizárt csoport tagja, a felhasználó nincs letiltva. A rendszer csak a hozzárendelt csoportban lévő felhasználók eszközeinek megfelelőségét ellenőrzi.

## <a name="noncompliant-device-is-not-blocked"></a>A nem megfelelő eszköz nincs letiltva

Ha egy eszköz nem megfelelő, de továbbra is rendelkezik hozzáféréssel, végezze el a következő műveleteket.

- Tekintse át a cél- és kizárási csoportokat. Ha a felhasználó nem szerepel a megfelelő cél- vagy kizárási csoportban, akkor nem tiltható le. A rendszer csak a célcsoportban lévő felhasználók eszközeinek megfelelőségét ellenőrzi.

- Gondoskodjon az eszköz felderítéséről. Az Exchange Connector egy Exchange 2010-es CAS-kiszolgálóra mutat, a felhasználó pedig egy Exchange 2013-kiszolgálón van? Ebben az esetben, ha az alapértelmezett Exchange-szabály az Engedélyezés, az Intune nem észleli az eszköz kapcsolatát az Exchange szolgáltatással, még akkor sem, ha a felhasználó a célcsoportban van.

- Ellenőrizze az eszköz meglétét/hozzáférési állapotát az Exchange-ben:
  - Ezzel a PowerShell-parancsmaggal lekérheti a következő postaláda összes mobileszköz-listáját: "Get-ActiveSyncDeviceStatistics-Mailbox MBX". Ha az eszköz nem szerepel a listán, akkor nem fér hozzá az Exchange-hez.
  
  - Ha az eszköz szerepel a felsorolásban, használja a "Get-CASmailbox-Identity:" UPN-t "| a FL parancsmaggal részletes információkat kaphat a hozzáférési állapotáról, és megadhatja a Microsoft ügyfélszolgálata.

## <a name="next-steps"></a>További lépések
Ha ezek az információk nem segítettek, akkor [Támogatást kérhet a Microsoft Intune-hoz](../fundamentals/get-support.md).
