---
# required metadata

title: Az ügyfél beállításának hibaelhárítása | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Az ügyfél a Microsoft Intune-ban való beállításának hibaelhárítása
A következő szakaszokban található információk segítséget nyújtanak az ügyfelek beállításával kapcsolatban gyakran előforduló problémák elhárításában. Ha ezekkel az információkkal nem tudja megoldani a problémát, a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben talál további részleteket a segítségkéréshez.

## Nem sikerül az ügyfél telepítése

-   Ha a [Microsoft Intune felügyeleti konzol](https://manage.microsoft.com/) felületén nem jelennek meg az ügyfélszoftverek telepítési riasztásai, ellenőrizze a számítógép internetkapcsolatát és a proxy konfigurációját, továbbá ellenőrizze, hogy a számítógép tud-e kommunikálni a szolgáltatás URL-címével, amely a következő: [https://manage.microsoft.com](https://manage.microsoft.com/). Ezután próbálja meg újból az ügyfélszoftver telepítését.

-   Ügyfélszoftver-telepítési hibával kapcsolatos riasztás esetén e-mailt küldhet a kiválasztott címzetteknek, ha konfigurál egy értesítési szabályt a **Felügyelet** munkaterületen. További információért lásd: [Értesítések a Microsoft Intune riasztásaival](/intune/deploy-use/get-notified-by-microsoft-intune-alerts).

-   Az Intune az **Ügyfélszoftver telepítése sikertelen** kritikus riasztást jeleníti meg, ha az ügyfélszoftver telepítése nem sikerült. Ez az üzenet a [Microsoft Intune felügyeleti konzol](https://manage.microsoft.com/) **Rendszer áttekintése** és **Riasztások** lapjain jelenik meg. Így ellenőrizheti, hogy vannak-e riasztások:

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com/) kattintson a **Riasztások** &gt; **Áttekintés** elemre.

2.  A **Riasztások áttekintése** lapon a következő információkat tekintheti át:

    -   A három legfontosabb riasztást, amelyek dátum, kategória vagy súlyosság szerint rendezhetők

    -   Az aktív riasztások teljes számát

3.  Válassza az **Összes riasztás** lehetőséget a következő információk **Riasztások** lapon való megjelenítéséhez. Először a kritikus riasztások jelennek meg:

    -   **Név** – Annak a riasztástípusnak a neve, amely a riasztást előidézte.

    -   **Forrás** – Hivatkozás a riasztás forrására.  Ha a riasztástípus megjelenítési küszöbértéke **Összes**, akkor ez a hivatkozás egyetlen érintett eszközt jelenít meg.  Ha a riasztástípus megjelenítési küszöbértéke valamilyen értékre van beállítva, akkor ez a hivatkozás a riasztás által érintett összes eszközt megjeleníti.

    -   **Utolsó frissítés** – A riasztás legutóbbi módosításának időpontja. Ha egy riasztás le van zárva, akkor a lezárás időpontja jelenik meg.

    -   **Súlyosság** – A riasztás súlyossága

## Nem sikerül letölteni a számítógép-regisztrációs csomagot
**Probléma:** számítógép regisztrálása során a következőt tapasztalja:
-  Nem sikerül letölteni a regisztrációs csomagot 
-  Megjelenik a letöltési párbeszédablak, de időtúllépés tapasztalható

**Megoldás:** ellenőrizze, hogy a letöltéshez használt böngészőben a letöltés ideje alatt engedélyezve vannak-e a letöltések, valamint, hogy a rendszer engedélyezi-e a titkosított fájlok helyi lemezre mentését.

## Az ügyfél telepítése a következő hibakóddal lefagy: 0x80040154
**A probléma leírása:**
 
-  A regisztráció során lefagy az ügyfél telepítése

-  Nem sikerül regisztrálni az eszközt 

-  A WindowsUpdate.log a következő hibaszámot tartalmazza: 0x80040154

Ezt a problémát az okozhatja, hogy a számítógépről kritikus szoftverfrissítések hiányoznak.

**Megoldás:** gondoskodjon róla, hogy a szoftverfrissítési szabályzat engedélyezze a kritikus frissítések telepítését, ennek menetéért lásd: [Windows rendszerű számítógépek naprakészen tartása szoftverfrissítésekkel a Microsoft Intune-ban](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune) 


## Microsoft Intune-házirendekkel kapcsolatos hibák a policyplatform.log fájlban
Nem mobileszköz-felügyelet alá tartozó Windows-eszközök esetén a policyplatform.log fájlban lévő házirendhibák az eszközön lévő Windows Felhasználói fiókok felügyelete (UAC) nem alapértelmezett beállításainak eredményei lehetnek. Néhány nem alapértelmezett UAC-beállítás hatással lehet a Microsoft Intune ügyféltelepítéseire és a házirendek érvénybe léptetésére.

### Az UAC-problémák megoldása

1.  Vonja ki a számítógépet az [Adatok és eszközök kivonása a Microsoft Intune-nal való felügyelet alól](/intune/deploy-use/retire-devices-from-microsoft-intune-management) szakaszban leírtak szerint.

2.  Várjon 20 percet az ügyfélszoftver eltávolításáig.

    > [!NOTE] Ne próbálja meg eltávolítani az ügyfelet a Programok és szolgáltatások területről.

3.  A Start menüben írja be az **UAC** kifejezést a Felhasználói fiókok felügyelete beállításainak megnyitásához.

4.  Mozgassa az értesítési csúszkát az alapértelmezett beállításhoz.

## Mi a teendő, ha az ügyfelet nem lehet eltávolítani a Microsoft Intune felügyeleti konzolról?

### Az ügyfélszoftver eltávolítása a Microsoft Intune parancssori eszközzel

1.  Nyisson meg egy parancssort rendszergazdai módban.

2.  Nyissa meg a *%programfiles%\Microsoft\OnlineManagement\Common* mappát.

3.  Futtassa a következő parancsot: ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## Ügyfél-telepítési hibakódok
A következő táblázat azokat a hibakódokat ismerteti, amelyek megjelenhetnek a **Riasztások** között, ha az ügyfélszoftver telepítése sikertelen. Továbbá javaslatokat is tartalmaz a hibakódok által jelölt problémák megoldására.

|Hibakód|Lehetséges probléma|Javasolt megoldás|
|--------------|--------------------|------------------------|
|**0x80CF0437**|Az ügyfélszámítógép órája nem a helyes időre van beállítva.|Győződjön meg róla, hogy az ügyfélszámítógép órája és időzónája a helyes értékre van beállítva.|
|**0x80240438**, **0x80CF0438**, **0x80CF401B**|Nem lehet kapcsolódni az Intune szolgáltatáshoz. Ellenőrizze az ügyfél proxybeállításait.|Ellenőrizze, hogy az Intune támogatja-e az ügyfélszámítógép proxybeállításait, és hogy az ügyfélszámítógépnek van-e internetkapcsolata. A támogatott proxybeállításokkal kapcsolatos további információkért lásd: [Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80CF402C**|Nem lehet kapcsolódni az Intune szolgáltatáshoz. Ellenőrizze a hálózati kapcsolatot.|Ellenőrizze, hogy a számítógépnek van-e hálózati kapcsolata. Gondoskodjon róla, hogy a hálózati kábel csatlakoztatva, a vezeték nélküli hálózat pedig engedélyezve legyen.|
|**0x80240438, 0x80CF0438**|Az Internet Explorer és a helyi rendszer proxybeállításai nincsenek konfigurálva.|Ellenőrizze az ügyfél proxybeállításait, és győződjön meg arról, hogy az Intune támogatja őket, illetve hogy az ügyfélszámítógépnek van internetkapcsolata. A támogatott proxybeállításokkal kapcsolatos további információkért lásd: [Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80043001**|A beléptetési csomag elavult.|Töltse le és telepítse az aktuális ügyfélszoftver-csomagot a **Felügyelet** munkaterületen. Útmutatásért lásd [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune) című témakört.|
|**0x80043004**|Az előfizetés nem létezik vagy le van tiltva.|Ellenőrizze, hogy az Intune-fiókja és -előfizetése aktív-e. A fiókbeállítások megtekintéséhez jelentkezzen be a fiókjába az [Office 365 Felügyeleti központban](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043002**|A fiók karbantartási módban van.|Nem tud új ügyfélszámítógépeket beléptetni, ha a fiók karbantartási módban van. A fiókbeállítások megtekintéséhez jelentkezzen be a fiókjába az [Office 365 Felügyeleti központban](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043003**|A fiókot törölték.|Ellenőrizze, hogy az Intune-fiókja és -előfizetése aktív-e. A fiókbeállítások megtekintéséhez jelentkezzen be a fiókba.|
|**0x80043005**|Az ügyfélszámítógépet eltávolították.|Várjon néhány órát, távolítsa el az ügyfélszoftver minden régebbi verzióját a számítógépről, majd próbálja meg újból telepíteni az ügyfélszoftvert. Útmutatásért lásd fent: **Mi a teendő, ha az ügyfelet nem lehet eltávolítani a Microsoft Intune felügyeleti konzolról?**.|
|**0x80043006**|Elérte a fiókhoz engedélyezett munkaállomások maximális számát.|A szervezetnek további munkaállomásokat kell vásárolnia, mielőtt további ügyfélszámítógépeket léptethet be a szolgáltatásba.|
|**0x80043007**|A tanúsítványfájl nem található abban a mappában, amelyben a telepítőprogram van.|A telepítés kezdete előtt az összes fájlt csomagolja ki. Ne nevezze át és ne helyezze át a kicsomagolt fájlokat: az összes fájlnak ugyanabban a mappában kell lennie, különben a telepítés sikertelen lesz. További információkért lásd: [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x8024D015**, **0x00240005**, **0x80070BC2**, **0x80070BC9**, **0x80CFD015**|A szoftvert nem lehet telepíteni, mert függőben van az ügyfélszámítógép újraindítása.|Indítsa újra a számítógépet, majd próbálja meg újból az ügyfélszoftver telepítését.|
|**0x80070032**|Az ügyfélszámítógép nem felel meg az ügyfélszoftver telepítéséhez szükséges egy vagy több előfeltételnek.|Gondoskodjon róla, hogy minden szükséges frissítés telepítve legyen az ügyfélszámítógépen, majd próbálja meg újból az ügyfélszoftver telepítését. Az ügyfélszoftver telepítésének előfeltételeivel kapcsolatos további információkért lásd: [A Microsoft Intune hálózati infrastruktúrával kapcsolatos követelményei](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0x80043008**|A Microsoft Online Management Updates szolgáltatás nem indítható el.|Lépjen kapcsolatba a Terméktámogatással a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című szakaszban leírtak szerint.|
|**0x80043009**|Az ügyfélszámítógép már be van léptetve a szolgáltatásba.|Az ügyfélszámítógépet el kell távolítania, mielőtt újból beléptetheti a szolgáltatásba. Útmutatásért lásd az [Eszközök kivonása a Microsoft Intune-nal való felügyelet alól](/intune/deploy-use/retire-devices-from-microsoft-intune-management) című témakört.|
|**0x8004300B**|Az ügyfélszoftver telepítési csomagja nem futtatható, mert az ügyfélen futó Windows-verzió nem támogatott.|Az Intune nem támogatja az ügyfélszámítógépen futó Windows-verziót. A támogatott operációs rendszerek listájáért lásd: [A Microsoft Intune hálózati infrastruktúrával kapcsolatos követelményei](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0xAB2**|A Windows Installer nem tud hozzáférni a VBScript futtatókörnyezethez egy egyéni művelet végrehajtásához.|A hibát egy egyéni művelet okozza, amely dinamikus kötésű kódtárakon (DLL-eken) alapul. Előfordulhat, hogy a DLL hibaelhárításához a következő témakörben ismertetett eszközöket kell használnia: [Microsoft Support KB198038: Useful Tools for Package and Deployment Issues](http://go.microsoft.com/fwlink/?LinkID=234255).|
|**0x8004300f**|A szoftver nem telepíthető, mert a System Center Configuration Manager-ügyfél már telepítve van.|Távolítsa el a Configuration Manager-ügyfelet, majd próbálja meg újból az ügyfélszoftver telepítését.|
|**0x80043010**|A szoftver nem telepíthető, mert az Open Mobile Alliance Device Management- (OMADM-) ügyfél már telepítve van.|Léptesse ki az OMADM-ügyfelet, majd próbálja meg újból az ügyfélszoftver telepítését.|
Ha a telepítéssel kapcsolatos problémák továbbra is fennállnak, forduljon az támogatási szolgálathoz a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című szakaszban leírtak szerint. Tegye elérhetővé az ügyfélszámítógép beléptetési naplóját (%*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log és %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log) és a Windows Update naplóját (%*windir*%\windowsupdate.log) a támogatási szakemberek számára.

### További lépések
Ha ezek a hibaelhárítási információk nem oldották meg a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben leírtak szerint.


<!--HONumber=Jun16_HO1-->


