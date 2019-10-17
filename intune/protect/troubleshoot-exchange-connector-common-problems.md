---
title: Az Intune Exchange Connector gyakori problémáinak elhárítása
titleSuffix: Microsoft Intune
description: A helyszíni Microsoft Intune Exchange Connector gyakori problémáinak elhárítása és megoldása.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9542212e1b75d97c96c024eed20e20e610e2b5d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503648"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Az Intune Exchange Connector gyakori problémáinak elhárítása
 
Ez a cikk segítséget nyújt az Intune-rendszergazdának az Intune Exchange Connector működésével kapcsolatos gyakori problémák megoldásában.  

A hibaelhárítás megkezdése előtt tekintse át az [Intune helyszíni Exchange Connector hibaelhárítása](troubleshoot-exchange-connector.md) című témakört az összekötő alapszintű információinak megtekintéséhez. Tekintse át az összekötő-konfigurációval kapcsolatos gyakori problémákat is. 

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Exchange ActiveSync-eszköz nincs felderítve az Exchange-ből

Ha egy Exchange ActiveSync-eszköz nincs felderítve az Exchange-ből, [figyelje az Exchange Connector tevékenységét](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) , és ellenőrizze, hogy az Exchange Connector szinkronizálva van-e az Exchange-kiszolgálóval. Ha az eszköz csatlakoztatása óta nem történt szinkronizálás, Gyűjtse össze a szinkronizálási naplókat, és csatolja őket egy támogatási kéréshez. Ha a teljes szinkronizálás vagy a gyors szinkronizálás sikeresen befejeződött az eszköz csatlakoztatása óta, ellenőrizze a következő problémákat: 

- Győződjön meg arról, hogy a felhasználók Intune-licenccel rendelkeznek. Ha nem, az Exchange Connector nem észleli az eszközeit.  

- Ha a felhasználó elsődleges SMTP-címe eltér az egyszerű felhasználónévtől (UPN) Azure Active Directory (Azure AD), az Exchange Connector nem észleli az adott felhasználó eszközeit. A probléma megoldásához javítsa ki az elsődleges SMTP-címet.  

- Ha az Exchange 2010 és az Exchange 2013 postaláda-kiszolgáló is van a környezetben, javasoljuk, hogy az Exchange Connectort egy Exchange 2013 ügyfél-hozzáférési kiszolgálóra (CAS) mutasson. Ha az Exchange Connector Exchange 2010 HITELESÍTÉSSZOLGÁLTATÓval való kommunikációra van beállítva, az Exchange Connector nem derít fel semmilyen felhasználói eszközt az Exchange 2013-ben.  

- Az Exchange Online dedikált környezetek esetében az Exchange Connectort az Exchange 2013 CAS (nem Exchange 2010 CAS) elemre kell irányítani a kezdeti beállítás során. Az összekötő csak Exchange 2013 HITELESÍTÉSSZOLGÁLTATÓKkal kommunikál, ha PowerShell-parancsmagokat hajt végre.  


## <a name="problems-with-the-notification-email-message"></a>Az értesítő e-mail-üzenettel kapcsolatos problémák  

Ha a helyszíni postaládák feltételes hozzáférését szeretné támogatni az Android Knox-t nem futtató eszközökön, győződjön meg arról, hogy az Intune-regisztráció az Intune Exchange Connector által küldött "első lépések" e-mail-üzenettel kezdődik. Az üzenet beléptetésének megkezdése biztosítja, hogy az eszköz egyedi ActiveSyncID kapjon az összes platformon (Exchange, Azure AD, Intune).  

Előfordulhat, hogy a felhasználó nem kapja meg az értesítési e-mail üzenetet, mert:  

- Az értesítési fiók beállítása helytelen.
- Az értesítési fiók automatikus észlelése nem sikerült.
- Nem sikerült elküldeni az e-mail üzenetet az Exchange Web Services (EWS) számára.

Az értesítő e-mailek problémáinak elhárításához tekintse át a következő szakaszt.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>Nézze meg az értesítési fiókot, amely az automatikus észlelési beállításokat kéri le
1. Győződjön meg arról, hogy az automatikus észlelési szolgáltatás és a EWS konfigurálva van az Exchange ügyfél-hozzáférési szolgáltatásokban. További információ: az [ügyfél-hozzáférési szolgáltatások](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) és [az automatikus észlelési szolgáltatás az Exchange Serveren](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).


2. Ellenőrizze, hogy az értesítési fiókja megfelel-e a következő követelményeknek:

   - A fiók egy aktív postaládával rendelkezik, amelyet a helyszíni Exchange-kiszolgáló üzemeltet.  

   - A fiók UPN-je megegyezik az SMTP-címnek.

3. Az automatikus észleléshez olyan DNS-kiszolgáló szükséges, amely DNS-rekordot tartalmaz a **autodiscover.SMTPdomain.com** (például autodiscover.contoso.com), amely az Exchange-ügyfél elérési kiszolgálójára mutat. A rekord kereséséhez adja meg a teljes tartománynevet a *autodiscover.SMTPdomain.com* helyett, és kövesse az alábbi lépéseket:

   1. A parancssorba írja be az *nslookup*parancsot.  

   2. Adja meg a *autodiscover.SMTPdomain.com*. A kimenetnek az alábbi képhez hasonlónak kell lennie:  
      @no__t 0Nslookup-eredmények @ no__t-1

   Az automatikus észlelési szolgáltatást az internetről is tesztelheti https://testconnectivity.microsoft.com címen. Vagy tesztelje egy helyi tartományból a Microsoft connectivity Analyzer eszköz használatával. További információ: [Microsoft connectivity Analyzer eszköz](https://docs.microsoft.com/en-us/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)). Ha szükséges, [töltse le a Microsoft connectivity Analyzer eszközt](https://go.microsoft.com/fwlink/?LinkID=313782).


### <a name="check-autodiscovery"></a>Automatikus észlelés keresése  

Ha az automatikus észlelés sikertelen, próbálkozzon a következő lépésekkel:
1. [Konfiguráljon egy érvényes automatikus észlelési DNS-rekordot](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)). 

2. Az Intune Exchange Connector konfigurációs fájljában a EWS URL-címének kódolása:

   1. Határozza meg a EWS URL-címét. Az Exchange alapértelmezett EWS URL-címe @no__t – 0, de az URL-cím eltérő lehet. Forduljon az Exchange-rendszergazdához, és ellenőrizze a környezetének megfelelő URL-címet.

   2. Szerkessze a *OnPremisesExchangeConnectorServiceConfiguration. XML* fájlt. Alapértelmezés szerint a fájl a *%ProgramData%\Microsoft\Windows Intune Exchange connectorban* található az Exchange Connectort futtató számítógépen. Nyissa meg a fájlt egy szövegszerkesztőben, majd módosítsa a következő sort a környezet EWS URL-címének megjelenítéséhez: `<ExchangeWebServiceURL> https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`
    

3. Mentse a fájlt, majd indítsa újra a számítógépet, vagy indítsa újra a Microsoft Intune Exchange Connector szolgáltatást.

>[!NOTE]
> Ebben a konfigurációban az Intune Exchange Connector leáll az automatikus észlelés használatával, és ehelyett közvetlenül a EWS URL-címhez csatlakozik.

## <a name="next-steps"></a>További lépések  

Az adott hibákkal kapcsolatos segítségért próbálkozzon [az Intune Exchange Connector gyakori hibáinak megoldásával](troubleshoot-exchange-connector-common-errors.md).

Támogatást kaphat, vagy segítséget kérhet az Intune-Közösségtől:
- A probléma megoldásához, illetve a Microsofttal kapcsolatos támogatási eset megnyitásához tekintse meg a [támogatás kérése](../fundamentals/get-support.md) az Intune-konzollal való használatát ismertető témakört. 
- A probléma közzététele a [Microsoft Intune fórumokon](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
