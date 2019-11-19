---
title: Microsoft Intune Exchange Connector beállítása
titleSuffix: Microsoft Intune
description: A helyszíni Intune Exchange Connector használatával kezelheti az Exchange-postaládákhoz való hozzáférést az Intune-regisztráció és az Exchange ActiveSync (EAS) alapján.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62db99fc2e47bdfa1a767db3bb2916649dedc074
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164690"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>A helyszíni Intune Exchange Connector beállítása
Az Exchange-hez való hozzáférés védelmének elősegítése érdekében az Intune a Microsoft Intune Exchange Connector néven ismert helyszíni összetevőre támaszkodik. Ezt az összekötőt a helyszíni *Exchange ActiveSync-összekötőnek* is nevezik az Intune-konzol egyes helyein. 

A cikkben található információk segítségével telepítheti és figyelheti az Intune Exchange Connectort. Az összekötőt a [feltételes hozzáférési szabályzatok](conditional-access-exchange-create.md) segítségével engedélyezheti vagy letilthatja a helyszíni Exchange-postaládák elérését. 

Az összekötő telepítve van, és a helyszíni hardveren fut. Felfedi az Exchange-hez csatlakozó eszközöket, és az eszköz adatait az Intune szolgáltatással kommunikálja. Az összekötő lehetővé teszi, hogy az eszközök regisztrálása és megfelelősége alapján engedélyezi vagy blokkolja az eszközöket. Ezek a kommunikáció a HTTPS protokollt használják.

Amikor egy eszköz megpróbál hozzáférni a helyszíni Exchange-kiszolgálóhoz, az Exchange Connector Maps Exchange ActiveSync-(EAS-) rekordokat hoz az Exchange Server Intune-rekordjaihoz, így biztosítva, hogy az eszköz regisztrálva legyen az Intune-ban, és megfelel az eszköz szabályzatának. A feltételes hozzáférési szabályzattól függően az eszköz engedélyezhető vagy letiltható. További információ: [Mi a feltételes hozzáférés használatának gyakori módjai az Intune](conditional-access-intune-common-ways-use.md) -ban?

A *felderítési* és az *engedélyezési és a blokkolási* műveletek is szabványos Exchange PowerShell-parancsmagokkal hajthatók végre. Ezek a műveletek az Exchange Connector első telepítésekor megadott szolgáltatásfiókot használják. 

Az Intune-előfizetések esetében több Intune Exchange-összekötő telepítése is támogatott. Ha több helyszíni Exchange-szervezettel rendelkezik, mindegyikhez beállíthat külön összekötőt. Az egyes Exchange-szervezetekhez azonban csak egy összekötő telepíthető.  

Kövesse az alábbi általános lépéseket egy olyan kapcsolat beállításához, amely lehetővé teszi az Intune számára a helyszíni Exchange Serverrel való kommunikációt:

1. Töltse le a helyszíni összekötőt az Intune-portálról.
2. Telepítse és konfigurálja az Exchange-összekötőt a helyszíni Exchange-szervezet egyik számítógépén.
3. Az Exchange-kapcsolat ellenőrzése.
4. Ismételje meg ezeket a lépéseket minden olyan Exchange-szervezet esetében, amelyhez csatlakozni szeretne az Intune-hoz.

## <a name="intune-exchange-connector-requirements"></a>Az Intune Exchange Connector követelményei

Az Exchange-hez való csatlakozáshoz szüksége van egy olyan fiókra, amely rendelkezik az összekötő által használható Intune-licenccel. A fiókot az összekötő telepítésekor kell megadnia.  

A következő táblázat felsorolja azon számítógép követelményeit, amelyre az Intune Exchange Connectort telepíti.  

|  Követelmény  |   További információ     |
|---------------|------------------------|
|  Operating systems        | Az Intune támogatja az Intune Exchange Connectort olyan számítógépen, amelyen a Windows Server 2008 SP2 64-bit, a Windows Server 2008 R2, a Windows Server 2012, a Windows Server 2012 R2 vagy a Windows Server 2016 bármely kiadása fut.<br /><br />Az összekötő nem támogatott a Server Core telepítéseken.  |
| Microsoft Exchange          | A helyszíni összekötőhöz a Microsoft Exchange 2010 SP3 vagy újabb verziójára, vagy régi dedikált Exchange Online-ra van szükség. Lépjen kapcsolatba a fiókkezelővel annak megállapításához, hogy a dedikált Exchange Online-környezet *új* vagy *régi* konfigurációval rendelkezik-e. |
| Mobileszköz-kezelő szolgáltató           | [Mobileszköz-kezelő szolgáltatóként a Microsoft Intune-t állítsa be](../fundamentals/mdm-authority-set.md). |
| Hardver              | Azon számítógépnek, amelyre az összekötőt telepíteni kívánja, 1,6 GHz-es processzorral, 2 GB memóriával és legalább 10 GB szabad lemezterülettel kell rendelkeznie. |
|  Active Directory-szinkronizálás             | Mielőtt a-összekötővel csatlakoztatja az Intune-t az Exchange-kiszolgálóhoz, [állítsa be Active Directory szinkronizálást](../fundamentals/users-add.md). A helyi felhasználókat és biztonsági csoportokat szinkronizálni kell a Azure Active Directory-példányával. |
| További szoftverek         | Az összekötőt futtató számítógépnek a Microsoft .NET Framework 4,5 és a Windows PowerShell 2,0 teljes telepítése szükséges. |
| Hálózat               | Az összekötő telepítéséhez használt számítógépnek olyan tartományhoz kell tartoznia, amely megbízhatósági kapcsolatban áll az Exchange Servert futtató tartománnyal.<br /><br />Konfigurálja úgy a számítógépet, hogy az a 80-es és a 443-es portokon keresztül a tűzfalakon és a proxy kiszolgálókon keresztül hozzáférjen az Intune szolgáltatáshoz. Az Intune ezeket a tartományokat használja: <br> – manage.microsoft.com <br> - \*manage.microsoft.com<br> - \*. manage.microsoft.com <br><br> Az Intune Exchange Connector a következő szolgáltatásokkal kommunikál: <br> -Intune szolgáltatás: HTTPS-port 443 <br> – Exchange ügyfél-hozzáférési kiszolgáló (CAS): WinRM Service port 443<br> – Exchange automatikus észlelés 443<br> -Exchange Web Services (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Exchange-parancsmagokkal kapcsolatos követelmények

Hozzon létre egy Active Directory felhasználói fiókot az Intune Exchange connectorhoz. A fióknak engedéllyel kell rendelkeznie a következő Windows PowerShell Exchange-parancsmagok futtatásához:  

- `Get-ActiveSyncOrganizationSettings`, `Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`, `Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`, `Set-ActiveSyncMailboxPolicy`, `New-ActiveSyncMailboxPolicy`, `Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`, `Set-ActiveSyncDeviceAccessRule`, `New-ActiveSyncDeviceAccessRule`, `Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`, `Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>Telepítőcsomag letöltése

Az Intune Exchange Connectort támogató Windows Serveren:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).  Olyan fiókot használjon, amely rendszergazda a helyszíni Exchange-kiszolgálón, és amely rendelkezik az Exchange Server használatára szolgáló licenccel.

2. Válassza a **bérlői felügyelet** > **Exchange-hozzáférés**lehetőséget.  

3. A **telepítés**területen válassza az **Exchange ActiveSync helyszíni összekötő** lehetőséget, majd válassza a **Hozzáadás**lehetőséget.

4. Az **összekötő hozzáadása** lapon válassza a helyszíni **összekötő letöltése**lehetőséget. Az Intune Exchange Connector egy tömörített (. zip) mappában található, amely megnyitható vagy menthető. A **Fájl letöltése** párbeszédpanelen kattintson a **Mentés** gombra a tömörített mappa biztonságos helyen való tárolásához.

## <a name="install-and-configure-the-intune-exchange-connector"></a>Az Intune Exchange Connector telepítése és konfigurálása

Az Intune Exchange Connector telepítéséhez kövesse az alábbi lépéseket. Ha több Exchange-szervezettel rendelkezik, ismételje meg az összes beállítani kívánt Exchange-összekötő lépéseit.

1. Az Intune Exchange Connector támogatott operációs rendszerén bontsa ki a **Exchange_Connector_Setup. zip** fájlban található fájlokat egy biztonságos helyre.
   > [!IMPORTANT]
   > Ne nevezze át és ne helyezze át a *Exchange_Connector_Setup* mappában található fájlokat. Ezek a módosítások az összekötő telepítésének sikertelenségét okozzák.

2. A fájlok kibontása után nyissa meg a kibontott mappát, majd kattintson duplán a **Exchange_Connector_Setup. exe** fájlra az összekötő telepítéséhez.

   > [!IMPORTANT]
   > Ha a célmappa nem biztonságos hely, törölje a *MicrosoftIntune. accountcert* nevű tanúsítványt a helyszíni összekötők telepítésének befejezésekor.

3. A **Microsoft Intune Exchange Connector** párbeszédpanelen válassza ki a **Helyszíni Microsoft Exchange Server** vagy **Üzemeltetett Microsoft Exchange Server** lehetőségek egyikét.

   ![Kép az Exchange-kiszolgáló típusának kiválasztási helyéről](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Helyszíni Exchange-kiszolgáló esetén adja meg az **Ügyfél-hozzáférési kiszolgáló** szerepkört futtató Exchange-kiszolgáló nevét vagy teljes tartománynevét.

   Üzemeltetett Exchange-kiszolgáló esetén adja meg az Exchange-kiszolgáló címét. Az üzemeltetett Exchange-kiszolgáló URL-címének megkeresése:

   1. Nyissa meg az Office 365 Outlookot.

   2. Kattintson a **?** ikonra a bal felső sarokban, majd válassza **a névjegy**elemet.

   3. Keresse meg a **POP külső kiszolgáló** értéket.

   4. Kattintson a **Proxykiszolgáló** elemre az üzemeltetett Exchange proxykiszolgáló-beállításainak megadásához.

       1. Válassza a **Proxykiszolgáló használata mobileszköz-információk szinkronizálásakor**lehetőséget.

       1. Adja meg a **proxykiszolgáló nevét** és **portszámát** a kiszolgálóhoz való hozzáféréshez.

       1. Ha a proxykiszolgáló eléréséhez felhasználói hitelesítő adatok szükségesek, válassza a **hitelesítő adatok használata a proxykiszolgálóhoz való csatlakozáshoz**lehetőséget. Ezután adja meg a **tartomány\felhasználó** és a **jelszó** értékét.

       1. Válassza az **OK** gombot.

4. A **felhasználó (tartomány \ Felhasználónév)** és a **jelszó** mezőkben adja meg az Exchange-kiszolgálóhoz való kapcsolódáshoz szükséges hitelesítő adatokat. A megadott fióknak rendelkeznie kell egy, az Intune használatához szükséges licenccel. 

5. Adja meg a hitelesítő adatokat az értesítések egy felhasználó Exchange Server-postaládába való küldéséhez. Ezt a felhasználót dedikálhatja kizárólag az értékesítésekre. Az értesítések felhasználónak Exchange-postaládára van szüksége az értesítések e-mailben való elküldéséhez. Ezeket az értesítéseket feltételes hozzáférési szabályzatok használatával konfigurálhatja az Intune-ban.  

   Győződjön meg arról, hogy az automatikus észlelés szolgáltatás és az Exchange-webszolgáltatások konfigurálva vannak az Exchange HITELESÍTÉSSZOLGÁLTATÓKon. Az ezzel kapcsolatos további információkért lásd: [Ügyfélelérési kiszolgáló](https://technet.microsoft.com/library/dd298114.aspx).

6. A **jelszó** mezőben adja meg a fiók jelszavát, hogy az Intune hozzáférjen az Exchange-kiszolgálóhoz.

   > [!NOTE]
   > A bérlőbe való bejelentkezéshez használt fióknak legalább Intune szolgáltatás-rendszergazdának kell lennie. A rendszergazdai fiók nélkül sikertelenül fog csatlakozni a következő hibával: "a távoli kiszolgáló hibát adott vissza: (400) hibás kérés".

7. Válassza a **Csatlakozás** elemet.

   > [!NOTE]
   > A kapcsolódás beállítása néhány percet is igénybe vehet.

A konfigurálás során az Exchange Connector tárolja a proxybeállításokat az Internet elérésének engedélyezéséhez. Ha a proxybeállítások módosulnak, konfigurálja újra az Exchange Connectort, hogy alkalmazza a frissített proxybeállításokat az Exchange connectorra.

Miután az Exchange Connector létrehozta a csatlakozást, a rendszer automatikusan szinkronizálja és hozzáadja az Exchange-összekötőt az Exchange által felügyelt felhasználókhoz társított mobileszközök számára. Ez a szinkronizálás hosszabb időt is igénybe vehet.

> [!NOTE]
> Ha telepíti az Intune Exchange Connectort, és később törölnie kell az Exchange-csatlakozást, el kell távolítania az összekötőt arról a számítógépről, amelyre telepítették.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Összekötők telepítése több Exchange-szervezethez

Az Intune-előfizetések esetében több Intune Exchange-összekötőt is támogat. Több Exchange-szervezettel rendelkező bérlő esetében csak egy összekötőt állíthat be minden Exchange-szervezethez. 

Ha az összekötőket több Exchange-szervezethez való csatlakozásra szeretné telepíteni, töltse le egyszer a. zip mappát. Ugyanezt a letöltést használja az egyes telepített összekötők esetében. Minden további összekötő esetében kövesse az előző szakaszban leírt lépéseket a telepítőprogram kinyeréséhez és futtatásához az Exchange-szervezeten belüli kiszolgálón.

Az Intune-hoz csatlakozó összes Exchange-szervezet támogatja a magas rendelkezésre állást, a figyelést és a manuális szinkronizálást. A következő szakaszok ismertetik ezeket a funkciókat.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>Helyszíni Intune Exchange Connector – magas rendelkezésre állás támogatása  

A helyszíni összekötő esetében a magas rendelkezésre állás azt jelenti, hogy ha az összekötő által használt Exchange CAS elérhetetlenné válik, az összekötő átválthat az adott Exchange-szervezethez tartozó más HITELESÍTÉSSZOLGÁLTATÓKra. Az Exchange Connector maga nem támogatja a magas rendelkezésre állást. Ha az összekötő meghibásodik, nincs automatikus feladatátvétel. A sikertelen összekötő cseréjéhez [telepítenie kell egy új összekötőt](#reinstall-the-intune-exchange-connector) .

A feladatátvételhez az összekötő a megadott HITELESÍTÉSSZOLGÁLTATÓK használatával hozza létre az Exchange-hez való sikeres kapcsolódást. Ezután felfedi a további CASst az adott Exchange-szervezet számára. Ez a felderítés lehetővé teszi, hogy az összekötő átadja a feladatátvételt egy másik CAS számára, ha van ilyen, amíg az elsődleges CAS elérhetővé nem válik.

Alapértelmezés szerint a további CASs felderítése engedélyezve van. Ha ki kell kapcsolnia a feladatátvételt:

1. A kiszolgálón, amelyen az Exchange Connector telepítve van, keresse fel **%*ProgramData*% \ Microsoft\Windows Intune Exchange Connectort**.

2. Nyissa meg egy szövegszerkesztőben az **OnPremisesExchangeConnectorServiceConfiguration.xml** fájlt.

3. Módosítsa **\<IsCasFailoverEnabled >*true*\</IsCasFailoverEnabled >** **\<IsCasFailoverEnabled >*false*\</IsCasFailoverEnabled >** .

## <a name="performance-tune-the-exchange-connector-optional"></a>Teljesítmény – az Exchange Connector hangolása (nem kötelező)

Ha az Exchange ActiveSync 5 000 vagy több eszközt támogat, konfigurálhat egy opcionális beállítást az összekötő teljesítményének növelése érdekében. A teljesítmény javítása érdekében lehetővé teszi, hogy az Exchange a PowerShell-parancs futtatási helyének több példányát használja.

A módosítás előtt győződjön meg arról, hogy az Exchange Connector futtatásához használt fiók nem használatos más Exchange-felügyeleti célokra. Az Exchange-fiók korlátozott számú futtatási területtel rendelkezik, és az összekötő a legtöbbet fogja használni.

A teljesítmény finomhangolása nem alkalmas régebbi vagy lassabb hardveren futó összekötők esetén.

Az Exchange Connector teljesítményének növelése:

1. Nyissa meg az összekötő telepítési könyvtárát azon a kiszolgálón, amelyen az összekötő telepítve van.  Az alapértelmezett hely a *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*.

2. Szerkessze a *OnPremisesExchangeConnectorServiceConfiguration. XML*fájlt.

3. Keresse meg a **EnableParallelCommandSupport** , és állítsa az **igaz**értéket:

   \<EnableParallelCommandSupport > True\</EnableParallelCommandSupport >

4. Mentse a fájlt, majd indítsa újra a Microsoft Intune Exchange Connector szolgáltatást.

## <a name="reinstall-the-intune-exchange-connector"></a>Telepítse újra az Intune Exchange Connectort

Előfordulhat, hogy újra kell telepítenie az Intune Exchange Connectort. Mivel csak egyetlen összekötő tud csatlakozni az egyes Exchange-szervezetekhez, ha egy második összekötőt telepít a szervezet számára, a telepített új összekötő lecseréli az eredeti összekötőt.

1. Az új összekötő telepítéséhez kövesse az [Exchange Connector telepítése és konfigurálása](#install-and-configure-the-intune-exchange-connector) című szakasz lépéseit.

2. Ha a rendszer kéri, válassza a **replace (csere** ) lehetőséget az új összekötő telepítéséhez.
   ![konfigurációs figyelmeztetés az összekötő cseréjéhez](./media/exchange-connector-install/prompt-to-replace.png)

3. Folytassa az [Intune Exchange Connector telepítése és konfigurálása](#install-and-configure-the-intune-exchange-connector) című szakasz lépéseit, majd jelentkezzen be újra az Intune-ba.

4. A végső ablakban kattintson a **Bezárás** gombra a telepítés befejezéséhez.
   ![a telepítő befejezése](./media/exchange-connector-install/successful-reinstall.png)

## <a name="monitor-an-exchange-connector"></a>Exchange-összekötő figyelése

Miután sikeresen konfigurálta az Exchange Connectort, megtekintheti a kapcsolatok állapotát és a legutóbbi sikeres szinkronizálási kísérletet.

Az Exchange Connector-kapcsolatok ellenőrzése:

1. Az Intune irányítópultján válassza az **Exchange-hozzáférés**lehetőséget.

2. Válassza a **helyszíni Exchange-hozzáférés** lehetőséget az egyes Exchange-összekötők kapcsolati állapotának ellenőrzéséhez.

Ellenőrizheti a legutóbbi sikeres szinkronizálási kísérlet dátumát és időpontját is.

Az Intune 1710-as verziótól kezdődően az [Exchange Connector és az intune System Center Operations Manager felügyeleti csomagja](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)is használható. A felügyeleti csomag különböző módokon figyeli az Exchange Connectort, amikor problémákba ütközik.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Gyors szinkronizálás vagy teljes szinkronizálás manuális kényszerítése

Az Intune Exchange Connector rendszeresen szinkronizálja az EAS-és az Intune-eszközök rekordjait. Ha egy eszköz megfelelőségi állapota megváltozik, az automatikus szinkronizálási folyamat rendszeresen frissíti a rekordokat, hogy az eszköz hozzáférése le legyen tiltva vagy engedélyezve legyen.

- A **gyors szinkronizálás** rendszeresen, naponta többször történik. A gyors szinkronizálás beolvassa az Intune-licenccel rendelkező és a helyszíni Exchange-felhasználók számára a feltételes hozzáférésre irányuló és a legutóbbi szinkronizálás óta megváltoztatott eszközök adatait.

- Alapértelmezés szerint naponta egyszer **teljes szinkronizálás** történik. A teljes szinkronizálás lekéri az összes Intune-licenccel rendelkező és helyszíni Exchange-felhasználó eszköz-információit, amelyek feltételes hozzáférést céloznak meg. A teljes szinkronizálás lekéri az Exchange Server adatait is, és biztosítja, hogy az Intune által a Azure Portalban megadott konfiguráció frissítve legyen az Exchange-kiszolgálón.

Az Intune-irányítópulton a **gyors szinkronizálás** vagy a **teljes szinkronizálás** lehetőség használatával kényszerítheti az összekötők szinkronizálásának futtatását:

   1. Az Intune irányítópultján válassza az **Exchange-hozzáférés**lehetőséget.

   2. Válassza **a helyszíni Exchange-hozzáférés**lehetőséget.

   3. Válassza a szinkronizálni kívánt összekötőt, majd válassza a **Gyors szinkronizálás** vagy a **Teljes szinkronizálás** lehetőséget.

## <a name="next-steps"></a>További lépések

[Feltételes hozzáférési szabályzat létrehozása a helyszíni Exchange-kiszolgálókhoz](conditional-access-exchange-create.md).
