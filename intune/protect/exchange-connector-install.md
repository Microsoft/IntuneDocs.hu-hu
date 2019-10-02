---
title: A Microsoft Intune helyszíni Exchange-összekötőjének beállítása
titleSuffix: Microsoft Intune
description: A helyszíni Exchange-összekötővel kezelheti az eszközök az Exchange-postaládákhoz való hozzáférését az Intune-regisztráció és az Exchange Active Sync (EAS) alapján.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26b6b884d2a21b15e2946e4ea591054bd478fa7b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729227"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>A helyszíni Intune Exchange Connector beállítása Microsoft Intune
A cikkben található információk segítségével telepítheti és figyelheti a Exchange Active Sync helyszíni összekötőt az Intune-hoz.  Az Intune helyszíni Exchange Connector és a [feltételes hozzáférési szabályzatok segítségével engedélyezheti vagy letilthatja a helyszíni Exchange-postaládák elérését](conditional-access-exchange-create.md). 

Amikor egy eszköz megpróbál hozzáférni a helyszíni Exchange-hez, az Exchange Connector leképezi a Exchange Active Sync (EAS) rekordokat az Exchange Serverben az Intune-rekordokhoz, hogy keressen az Intune-ban regisztrált eszközökre, és megfeleljen az eszköz megfelelőségi szabályzatának. A feltételes hozzáférési szabályzattól függően az eszköz hozzáférése vagy blokkolása engedélyezett. További információ: [Mi a feltételes hozzáférés használatának gyakori módjai az Intune](conditional-access-intune-common-ways-use.md) -ban?

Az Intune-előfizetések esetében több helyszíni Exchange-összekötő telepítése is támogatott. Ha több helyszíni Exchange-szervezettel rendelkezik, mindegyikhez beállíthat külön összekötőt. Azonban csak egy összekötő telepíthető az egyes Exchange-szervezetek használatához. 

A következő általános lépésekkel állíthatja be az Intune-nal a helyszíni Exchange Serverrel való kommunikációt lehetővé tevő kapcsolatot:

1. Töltse le a helyszíni Intune Exchange Connectort az Intune-portálról.
2. Telepítse és konfigurálja az Exchange-összekötőt a helyszíni Exchange-szervezet egyik számítógépén.
3. Az Exchange-kapcsolat ellenőrzése.
4. Ismételje meg ezeket a lépéseket minden olyan Exchange-szervezet esetében, amelyhez csatlakozni szeretne az Intune-hoz.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Az Intune helyszíni Exchange-összekötő követelményei
Szüksége lesz egy Intune-licenccel rendelkező fiókra, amelyet az összekötő használhat az Exchange-hez való csatlakozáshoz. A fiók az összekötő telepítésekor van megadva.  

A következő táblázat a helyszíni Exchange-összekötő számítógépre vonatkozó követelményeit tartalmazza.  

|  Követelmény  |   További információ     |
|---------------|------------------------|
|  Operációs rendszerek        | Az Intune a helyszíni Exchange-összekötőt olyan számítógépen támogatja, amelyen a Windows Server 2008 SP2 64 bites, a Windows Server 2008 R2, a Windows Server 2012, a Windows Server 2012 R2 vagy a Windows Server 2016 rendszer valamelyik kiadása fut.<br /><br />Az összekötő nem támogatott a Server Core telepítéseken.  |
| Microsoft Exchange          | A helyszíni összekötőhöz a Microsoft Exchange 2010 SP3 vagy újabb verziójára, vagy régi dedikált Exchange Online-ra van szükség. Lépjen kapcsolatba a fiókkezelővel annak megállapításához, hogy a dedikált Exchange Online-környezet <strong>új</strong> vagy <strong>régi</strong> konfigurációval rendelkezik-e. |
| Mobileszköz-kezelő szolgáltató           | [Mobileszköz-kezelő szolgáltatóként a Microsoft Intune-t állítsa be](../fundamentals/mdm-authority-set.md). |
| Hardver              | Azon számítógépnek, amelyre az összekötőt telepíteni kívánja, 1,6 GHz-es processzorral, 2 GB memóriával és legalább 10 GB szabad lemezterülettel kell rendelkeznie. |
|  Active Directory-szinkronizálás             | Mielőtt az Intune-t az összekötő segítségével csatlakoztathatná az Exchange-kiszolgálóhoz, [állítsa be az Active Directory-szinkronizálást](../fundamentals/users-add.md), hogy a helyi felhasználók és biztonsági csoportok szinkronizálva legyenek az Azure Active Directory meglévő példányával. |
| További szoftverek         | Az összekötőt futtató számítógépnek a Microsoft .NET-keretrendszer 4.5-ös és a Windows PowerShell 2.0-s verziójának teljes telepítésével kell rendelkeznie. |
| Network (Hálózat)               | Az összekötő telepítéséhez használt számítógépnek olyan tartományhoz kell tartoznia, amely megbízhatósági kapcsolatban áll az Exchange Server-t üzemeltető tartománnyal.<br /><br />A számítógépet úgy kell beállítani, hogy a 80-as és a 443-as porton, a tűzfalakon és a proxykiszolgálókon keresztül hozzáférjen az Intune szolgáltatáshoz. Az Intune által használt tartományok a következők: manage.microsoft.com, &#42;manage.microsoft.com és &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Exchange-parancsmagokkal kapcsolatos követelmények

Hozzon létre egy Active Directory felhasználói fiókot, amelyet a helyszíni Exchange Connector fog használni. A fióknak engedéllyel kell rendelkeznie az alábbi szükséges Windows PowerShell Exchange-parancsmagok futtatásához:


- Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
- Get-CasMailbox, Set-CasMailbox
- Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
- Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
- Get-ActiveSyncDeviceStatistics
- Get-ActiveSyncDevice
- Get-ExchangeServer
- Get-ActiveSyncDeviceClass
- Get-Recipient
- Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
- Set-ADServerSettings
- Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>A helyszíni Exchange-összekötő szoftver telepítőcsomagjának letöltése

1. Egy, a helyszíni Exchange-összekötőt támogató Windows Server rendszerben nyissa meg az [Azure Portalt](https://portal.azure.com), és jelentkezzen be egy olyan felhasználói fiókkal, amely rendszergazda a helyszíni Exchange Serveren, és rendelkezik licenccel az Exchange Server használatához.

2. Ugrás az **Intune** > **Exchange** -hozzáférésre  

3. A **telepítés**területen válassza **az Exchange ActiveSync helyszíni összekötő**lehetőséget, majd kattintson a **Hozzáadás**gombra.

4. Az **összekötő hozzáadása** lapon válassza a helyszíni **összekötő letöltése**lehetőséget. A helyszíni Exchange Connector egy tömörített (. zip) mappában található, amely megnyitható vagy menthető. A **Fájl letöltése** párbeszédpanelen kattintson a **Mentés** parancsra a tömörített mappa biztonságos helyre való mentéséhez.

    > [!IMPORTANT]
    > Ne nevezze és ne helyezze át a helyszíni Exchange-összekötő mappájában levő fájlokat. A mappa tartalmának áthelyezése vagy átnevezése az Exchange-összekötő sikertelen telepítését eredményezi.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>A helyszíni Intune Exchange-összekötő telepítése és konfigurálása
A helyszíni Intune Exchange-összekötő telepítéséhez hajtsa végre az alábbi lépéseket. Ha több Exchange-szervezettel rendelkezik, ismételje meg ezeket a lépéseket az összes további beállítandó Exchange-összekötő esetében.

1. Egy, a helyszíni Exchange-összekötő által támogatott operációs rendszerben bontsa ki az **Exchange_Connector_Setup.zip** fájl tartalmát egy biztonságos helyre.

2. A fájlok kibontása után nyissa meg a kibontott mappát, majd kattintson duplán az **Exchange_Connector_Setup.exe** fájlra a helyszíni Exchange-összekötő telepítéséhez.

   > [!IMPORTANT]
   > Ha a célmappa nem biztonságos hely, akkor a helyszíni összekötők telepítése után törölje a **MicrosoftIntune.accountcert** tanúsítványfájlt.

3. A **Microsoft Intune Exchange Connector** párbeszédpanelen válassza ki a **Helyszíni Microsoft Exchange Server** vagy **Üzemeltetett Microsoft Exchange Server** lehetőségek egyikét.

   ![Kép az Exchange-kiszolgáló típusának kiválasztási helyéről](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Helyszíni Exchange-kiszolgáló esetén adja meg az **Ügyfél-hozzáférési kiszolgáló** szerepkört futtató Exchange-kiszolgáló nevét vagy teljes tartománynevét.

   Üzemeltetett Exchange-kiszolgáló esetén adja meg az Exchange-kiszolgáló címét. Az üzemeltetett Exchange-kiszolgáló URL-címének megkeresése:

   1. Nyissa meg az Office 365-ös Webes Outlookot.

   2. Kattintson a **?** ikonra baloldalt felül, majd válassza a **Névjegy** lehetőséget.

   3. Keresse meg a **POP külső kiszolgáló** értéket.

   4. Kattintson a **Proxykiszolgáló** elemre az üzemeltetett Exchange proxykiszolgáló-beállításainak megadásához.
       1. Válassza a **Proxykiszolgáló használata mobileszköz-információk szinkronizálásakor**lehetőséget.

       2. Adja meg a **proxykiszolgáló nevét** és **portszámát** a kiszolgálóhoz való hozzáféréshez.

       3. Ha a proxykiszolgálóhoz való csatlakozáshoz hitelesítő adatok megadása szükséges, válassza a **Hitelesítő adatok használata a proxykiszolgálóhoz való csatlakozáshoz** lehetőséget. Ezután adja meg a **tartomány\felhasználó** és a **jelszó** értékét.

       4. Válassza az **OK** gombot.

4. A **Felhasználó (Tartomány\felhasználó)** és **Jelszó** mezőknél adja meg az Exchange-kiszolgálóhoz való csatlakozáshoz szükséges hitelesítő adatokat. A megadott fióknak rendelkeznie kell egy, az Intune használatához szükséges licenccel. 

5. Adja meg azokat a hitelesítő adatokat, amelyek szükségesek ahhoz, hogy az értesítéseket egy felhasználó Exchange Server-postaládájába küldhesse a rendszer. Ezt a felhasználót dedikálhatja kizárólag az értékesítésekre. Az értesítések felhasználónak Exchange-postaládára van szüksége az értesítések e-mailben való elküldéséhez. Ezeket az értesítéseket a feltételes hozzáférési szabályzatokon keresztül konfigurálhatja az Intune-ban.  

   Győződjön meg arról, hogy az Automatikus észlelés szolgáltatás és az Exchange-webszolgáltatások konfigurálva vannak az Exchange ügyfélelérési kiszolgálón. Az ezzel kapcsolatos további információkért lásd: [Ügyfélelérési kiszolgáló](https://technet.microsoft.com/library/dd298114.aspx).

6. A **Jelszó** mezőben adja meg a fiók jelszavát, hogy az Intune hozzáférhessen az Exchange-kiszolgálóhoz.

   > [!NOTE]
   > Ahhoz, hogy a kapcsolódás sikeres legyen, a bérlőhöz való bejelentkezéshez használt fióknak legalább Intune szolgáltatás-rendszergazdának kell lennie. Enélkül sikertelen lesz a hiba: "A távoli kiszolgáló hibát adott vissza: (400) helytelen kérelem ".

7. Válassza a **Csatlakozás** elemet.

   > [!NOTE]
   > A kapcsolat konfigurálása néhány percig is eltarthat.

A konfiguráció során az Exchange-összekötő tárolja a proxybeállításait, hogy lehetővé tegye a kapcsolódást az internethez. Ha a proxybeállítások módosulnak, akkor újra kell konfigurálnia az Exchange Connectort, hogy alkalmazza a frissített proxybeállításokat az Exchange connectorra.

Miután az Exchange-összekötő létrehozta a kapcsolatot, azokat a mobileszközöket, amelyek az Exchange-ben felügyelt felhasználókhoz vannak társítva, a rendszer automatikusan szinkronizálja és hozzáadja az Exchange-összekötőhöz. Ez a szinkronizálás eltarthat egy ideig.

> [!NOTE]
> Ha telepítette a helyszíni Exchange-összekötőt, de később törli az Exchange-kapcsolatot, akkor el kell távolítania a helyszíni Exchange-összekötőt is arról a számítógépről, amelyre telepítette.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Összekötők telepítése több Exchange-szervezethez
Az Intune egy előfizetésben több helyszíni Exchange-összekötőt is támogat. Több Exchange-szervezettel rendelkező bérlő esetében beállíthat egy összekötőt minden egyes Exchange-szervezethez, de csak egyetlen összekötőt egyetlen szervezet számára. 

Ha az összekötőket több Exchange-szervezethez való csatlakozásra telepíti, töltse le egyszer a. zip mappát, majd használja újra ugyanezt a letöltést minden egyes telepített összekötőhöz. Minden további összekötő esetében kövesse az előző szakaszban leírt lépéseket a telepítőprogram kinyeréséhez és futtatásához az Exchange-szervezeten belüli kiszolgálón.

Az Intune-hoz csatlakozó összes Exchange-szervezet esetében a következő szakaszokban ismertetett magas rendelkezésre állási, figyelési és manuális szinkronizálási funkciók támogatottak.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Magas rendelkezésre állású helyszíni Exchange Connector támogatása 
A helyszíni Exchange Connector magas rendelkezésre állása azt jelenti, hogy az összekötő által használt Exchange ügyfél-hozzáférési kiszolgáló (CAS) nem lesz elérhető, az összekötő átválthat az adott Exchange-szervezethez tartozó más HITELESÍTÉSSZOLGÁLTATÓK használatára. Maga az Exchange Connector nem támogatja a magas rendelkezésre állást. Ha az összekötő meghibásodik, nincs automatikus feladatátvétel, és az összekötőt [új összekötő telepítésével](#reinstall-the-on-premises-exchange-connector)kell lecserélnie. 

A feladatátvétel végrehajtásához, miután az összekötő sikeresen létrehozta az Exchange-hez való csatlakozást a megadott HITELESÍTÉSSZOLGÁLTATÓK használatával, az összekötő felfedi a további CASst az adott Exchange-szervezet számára. A további CASs ismerete lehetővé teszi, hogy az összekötő feladatátvételt hajtson végre egy másik CAS számára, ha elérhető, amíg az elsődleges HITELESÍTÉSSZOLGÁLTATÓK elérhetővé nem válnak. Alapértelmezés szerint a további CASs felderítése engedélyezve van. A feladatátvételt a következő eljárással kapcsolhatja ki:  
1. A kiszolgálón, amelyen az Exchange Connector telepítve van, lépjen a következőre:%*ProgramData*% \ Microsoft\Windows Intune Exchange Connector. 
2. Nyissa meg egy szövegszerkesztőben az **OnPremisesExchangeConnectorServiceConfiguration.xml** fájlt.
3. Módosítsa az &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; értéket az &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; értékre a funkció letiltásához.  
 
## <a name="optional-performance-tuning-for-the-exchange-connector"></a>Opcionális teljesítmény-hangolás az Exchange connectorhoz  

Ha az Exchange ActiveSync használatával 5 000 vagy több eszközt támogat, konfigurálhat egy opcionális beállítást az összekötő teljesítményének növelése érdekében. Nagyobb teljesítmény érhető el azáltal, hogy lehetővé teszi, hogy az Exchange a PowerShell-parancsok több példányát használja a futtatáshoz. 

A módosítás előtt győződjön meg arról, hogy az Exchange Connector futtatásához használt fiók nem használatos más Exchange-felügyeleti célokra. Ennek az az oka, hogy az Exchange-fiók korlátozott számú futtatási tárhelyet tartalmaz, amelyek többségét az összekötő fogja használni. 

Ez a teljesítmény-változás nem alkalmas a régebbi vagy lassabb hardveren futó összekötők esetében.  

1. Nyissa meg az összekötők telepítési könyvtárát azon a kiszolgálón, amelyen az összekötő telepítve van.  Az alapértelmezett hely a *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Szerkessze a *OnPremisesExchangeConnectorServiceConfiguration. XML*fájlt.
3. Keresse meg a **EnableParallelCommandSupport** , és állítsa az **igaz**értéket:  
     
   \<EnableParallelCommandSupport > True\</EnableParallelCommandSupport >
4. Mentse a fájlt, majd indítsa újra a Microsoft Intune Exchange Connector szolgáltatást.

## <a name="reinstall-the-on-premises-exchange-connector"></a>A helyszíni Exchange Connector újratelepítése
Előfordulhat, hogy újra kell telepítenie az Exchange Connectort. Mivel a rendszer egyetlen összekötőt támogat az egyes Exchange-szervezetekhez való csatlakozáshoz, ha egy második összekötőt telepít egy szervezet számára, a telepített új összekötő lecseréli az eredeti összekötőt.

1. Az új összekötő telepítésének megkezdéséhez kövesse az [Intune helyszíni Exchange Connector telepítése és konfigurálása](#install-and-configure-the-intune-on-premises-exchange-connector) című témakör lépéseit. 
2. Ha a rendszer kéri, válassza a Replace ( **Csere** ) lehetőséget az új összekötő telepítéséhez.  
   ![Az összekötő cseréjére szolgáló konfigurációs kérés](./media/exchange-connector-install/prompt-to-replace.png)

3. Folytassa az előző eljárás lépéseit, majd jelentkezzen be újra az Intune-ba.
4. Ha a végső képernyő jelenik meg, a **Bezárás** gombra kattintva fejezze be a telepítést.  
   ![Telepítés befejezése](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Az Exchange Connector tevékenységének figyelése

Miután sikeresen konfigurálta az Exchange Connectort, megtekintheti a kapcsolatok állapotát és a legutóbbi sikeres szinkronizálási kísérletet. Az Exchange Connector-kapcsolatok ellenőrzése:

1. Az Intune irányítópultján válassza az **Exchange-hozzáférés**lehetőséget.
2. Válassza a **helyszíni Exchange-hozzáférés** lehetőséget az egyes Exchange-összekötők kapcsolati állapotának ellenőrzéséhez.

Ellenőrizheti a legutóbbi sikeres szinkronizálási kísérlet dátumát és időpontját is.
--> 

### <a name="system-center-operations-manager-management-pack"></a>System Center Operations Manager felügyeleti csomag

Az Intune 1710-as verziótól kezdődően az [Exchange Connector és az intune Operations Manager felügyeleti csomagja](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)is használható. A felügyeleti csomag használatával különböző módokon figyelheti az Exchange Connectort, amikor problémákba ütközik.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Gyors szinkronizálás vagy teljes szinkronizálás manuális kényszerítése
A helyszíni Exchange Connector rendszeresen szinkronizálja az EAS-és az Intune-eszközök rekordjait. Ha egy eszköz megfelelőségi állapota megváltozik, az automatikus szinkronizálási folyamat rendszeresen frissíti a rekordokat, hogy az eszköz hozzáférése le legyen tiltva vagy engedélyezve legyen.

- **Gyors szinkronizálás** rendszeresen történik, naponta többször. A gyors szinkronizálás beolvassa az Intune-licenccel rendelkező és a helyszíni Exchange feltételes hozzáférésre irányuló, a legutóbbi szinkronizálás óta megváltoztatott felhasználók adatait.

- **Teljes szinkronizálás** naponta egyszer történik alapértelmezés szerint. A teljes szinkronizálás lekéri az összes Intune-licenccel rendelkező és a helyszíni Exchange feltételes hozzáférés-megcélzó felhasználójának eszköz-információit. A teljes szinkronizálás emellett beolvassa az Exchange kiszolgálói adatait is, és biztosítja, hogy az Intune által az Azure Portalon megadott konfiguráció frissüljön az Exchange-kiszolgálón. 


Kényszerítheti a szinkronizálás futtatását egy összekötőn, ha a **Gyors szinkronizálás** vagy a **Teljes szinkronizálás** lehetőséget választja az Intune-irányítópulton. Ehhez kövesse az alábbi lépéseket:

   1. Az Intune irányítópultján válassza az **Exchange-hozzáférés**lehetőséget.
   2. Válassza **a helyszíni Exchange-hozzáférés**lehetőséget.
   3. Válassza a szinkronizálni kívánt összekötőt, majd válassza a **Gyors szinkronizálás** vagy a **Teljes szinkronizálás** lehetőséget.

## <a name="next-steps"></a>További lépések
[Feltételes hozzáférési szabályzat létrehozása a helyszíni Exchange-hez](conditional-access-exchange-create.md)
