---
title: Az Intune Exchange Connector gyakori problémáinak elhárítása
titleSuffix: Microsoft Intune
description: A helyszíni Microsoft Intune Exchange Connector gyakori problémáinak elhárítása és megoldása
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4219d9d4f7d7e8c56acc218d16d8277ed2cf3821
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817536"
---
# <a name="resolve-common-problems-for-the-intune-exchange-connector"></a>Az Intune Exchange Connector gyakori problémáinak elhárítása
 
Ez a cikk segítséget nyújt az Intune-rendszergazdának az Intune Exchange Connector működésével kapcsolatos gyakori problémák megoldásában.  

A továbblépés előtt tekintse át az Intune helyszíni Exchange Connector hibaelhárítása az összekötővel kapcsolatos alapvető információkhoz című témakört a hibaelhárítás megkezdése előtt, valamint az összekötő konfigurálásával kapcsolatos gyakori problémákat. 

## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Az Exchange ActiveSync-eszköz nem deríthető fel az Exchange-ből

[Az Exchange Connector tevékenységének figyelésével](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) ellenőrizze, hogy az Exchange Connector szinkronizál-e az Exchange-kiszolgálóval. Ha az eszköz csatlakozása óta sikeresen lezajlott egy teljes vagy gyors szinkronizálás, akkor megvizsgálhatja a további, alább felsorolt hibalehetőségeket. Ha nem került sor a szinkronizálásra, gyűjtse össze a szinkronizálási naplókat, és csatolja őket egy támogatási kérelemhez.  

- Ellenőrizze, hogy a felhasználók rendelkeznek-e Intune-licenccel, ellenkező esetben az Exchange Connector nem észleli az eszközeit.  

- Ha egy felhasználó elsődleges SMTP-címe különbözik az Azure Active Directoryban (Azure AD) szereplő egyszerű felhasználónevétől, az Exchange Connector nem észleli az adott felhasználó eszközeit. A probléma megoldásához javítsa ki az elsődleges SMTP-címet.  

- Ha az Exchange 2010 és az Exchange 2013 postaláda-kiszolgáló is van a környezetben, javasoljuk, hogy az Exchange Connectort egy Exchange 2013 ügyfél-hozzáférési kiszolgálóra (CAS) mutasson. Ellenkező esetben, ha az Exchange Connector úgy van beállítva, hogy az Exchange 2010 HITELESÍTÉSSZOLGÁLTATÓval kommunikáljon, az Exchange Connector nem észleli az Exchange 2013 felhasználói eszközeit.  

- Az Exchange Online dedikált környezetek esetében az Exchange Connectort egy Exchange 2013 CAS (nem Exchange 2010 CAS) értékűre kell irányítani a kezdeti beállítás során, mivel az összekötő csak az ezzel a HITELESÍTÉSSZOLGÁLTATÓval kommunikálni fog a végrehajtás során PowerShell-parancsmagok.  


## <a name="problems-with-the-notification-email-message"></a>Az értesítő e-mail-üzenettel kapcsolatos problémák  

A nem Knox Android-eszközök helyszíni postaládákhoz való feltételes hozzáférésének támogatásához az Intune-regisztrációnak az Intune Exchange Connector által küldött "első lépések" e-mail-üzenettel kell kezdődnie. Az üzenet beléptetésének megkezdése biztosítja, hogy az eszköz egyedi ActiveSyncID kapjon az összes platformon (Exchange, Azure AD, Intune).  

Több oka is van annak, hogy a felhasználók miért nem kapják meg az értesítő e-mail-üzenetet:  

- Az értesítési fiók nincs megfelelően beállítva.
- Az automatikus észlelés meghiúsul az értesítési fióknál.
- Az e-mail-üzenet elküldésére vonatkozó EWS-kérelem sikertelen.

Az e-mailes értesítési problémák elhárításához használja az alábbi lépéseket.

### <a name="review-the-notification-account-thats-used-to-retrieve-autodiscover-settings"></a>Tekintse át az automatikus észlelési beállítások lekéréséhez használt értesítési fiókot
1. Győződjön meg arról, hogy az automatikus észlelési szolgáltatás és az Exchange-webszolgáltatások konfigurálva vannak az Exchange ügyfél-hozzáférési szolgáltatásokban. További információ: ügyfél- [hozzáférési szolgáltatások](https://docs.microsoft.com/Exchange/architecture/client-access/client-access).

   További információ: [az automatikus észlelés szolgáltatás az Exchange Serveren](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).


2. Ellenőrizze, hogy az értesítési fiókja megfelel-e a következő követelményeknek:

   - A fiók egy aktív postaládával rendelkezik, amelyet a helyszíni Exchange-kiszolgáló üzemeltet.  

   - A fiók UPN-je megegyezik az SMTP-címnek.

3. Ahhoz, hogy az automatikus észlelés működjön, a DNS-kiszolgálónak rendelkeznie kell egy DNS-rekorddal a **autodiscover.SMTPdomain.com** (például autodiscover.contoso.com), amely az Exchange-ügyfél elérési kiszolgálójára mutat. Ha szeretné megtekinteni, hogy a rekord megtalálható-e, tegye a következőket, miközben a teljes tartománynevet adja meg a *autodiscover.SMTPdomain.com*helyett:

   1. A parancssorba írja be az **nslookup**parancsot, majd nyomja le az ENTER billentyűt.  

   2. Írja be a **autodiscover.SMTPdomain.com**, majd nyomja le az ENTER billentyűt.

      A kimenetnek az alábbi képhez hasonlónak kell lennie:  
      ![Nslookup-eredmények](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
)

   Az automatikus észlelési szolgáltatást az internetről is tesztelheti https://testconnectivity.microsoft.com/ vagy egy helyi tartományból a Microsoft connectivity Analyzer eszköz használatával. További információ: [Microsoft connectivity Analyzer eszköz](https://docs.microsoft.com/en-us/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)). Töltse le a [Microsoft connectivity Analyzer eszközt](http://go.microsoft.com/fwlink/?LinkID=313782).


### <a name="review-autodisocvery"></a>Autodisocvery áttekintése  

Ha az automatikus észlelés sikertelen, próbálkozzon a következő lépésekkel:
1. [Konfiguráljon egy érvényes automatikus észlelési DNS-rekordot](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)). 

2. A EWS URL-címe az Intune Exchange Connector konfigurációs fájljában a következőképpen történik:

   1. Határozza meg a EWS URL-címét. Az Exchange alapértelmezett EWS URL-címe **https://<mailServerFQDN>/EWS/Exchange. asmx**, bár a tiéd eltérő lehet. Forduljon az Exchange-rendszergazdához, és ellenőrizze a környezetének megfelelő URL-címet.

   2. Szerkessze a **OnPremisesExchangeConnectorServiceConfiguration. XML** fájlt. Alapértelmezés szerint a fájl a **%ProgramData%\Microsoft\Windows Intune Exchange connectorban** található az Exchange Connectort futtató számítógépen. Nyissa meg a fájlt egy szövegszerkesztő használatával, majd módosítsa a következő sort a környezet EWS URL-címének megjelenítéséhez: `<ExchangeWebServiceURL> https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`
    

3. Mentse a fájlt, majd indítsa újra a számítógépet, vagy indítsa újra a Microsoft Intune Exchange Connector szolgáltatást.

>[!NOTE]
> Ebben a konfigurációban az Intune Exchange Connector leáll az automatikus észlelés használatával, és ehelyett közvetlenül a EWS URL-címhez csatlakozik.

## <a name="next-steps"></a>További lépések  

A következő cikk az adott hibák megoldásához nyújt segítséget:
- [Az Intune Exchange Connector gyakori hibáinak elhárítása](troubleshoot-exchange-connector-common-errors.md).

Kérjen segítséget a támogatási szolgálattól vagy az Intune-Közösségtől.
- A probléma megoldásához, illetve a Microsoft támogatási esetének megnyitásához tekintse meg a [támogatás kérése](../fundamentals/get-support.md) az Intune-konzollal való használatát ismertető témakört. 
- A probléma közzététele a [Microsoft Intune fórumokon](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
