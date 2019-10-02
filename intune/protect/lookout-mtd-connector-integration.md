---
title: A Lookout-integráció beállítása a Microsoft Intune-ban
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan integrálhatja az Intune-t a mobil végpontok biztonságával, a mobil veszélyforrások elleni védelem megoldásával a mobileszközök a vállalati erőforrásokhoz való hozzáférésének szabályozására.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729235"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>A mobil végpontok biztonsági integrációjának beállítása az Intune-nal
Az [előfeltételeknek](lookout-mobile-threat-defense-connector.md#prerequisites)megfelelő környezettel integrálhatja az Intune-nal a kilátó mobil végpontok biztonságát. A cikkben található információk végigvezetik az integráció beállításában és a fontos beállítások konfigurálásában az Intune-nal való használathoz.  

> [!IMPORTANT]
> Egy olyan létező Lookout Mobility Endpoint Security-bérlő, amely még nincs társítva az Azure AD-bérlőjéhez, nem használható fel az Azure AD-val és az Intune-nal való integrációhoz. Új Lookout Mobility Endpoint Security-bérlő létrehozásához lépjen kapcsolatba a Lookout támogatási csapatával. Azure AD-felhasználói számára használja az új bérlőt.

## <a name="collect-azure-ad-information"></a>Azure AD-információk gyűjtése  
Az Intune-nal való integrációhoz a kilátó mobilitási végpont biztonsági bérlőjét a Azure Active Directory (AD) előfizetésével társíthatja.

Ahhoz, hogy a Kitekintő mobil Endpoint Security-előfizetés integrálása az Intune-nal történjen, a következő információkat kell megadnia a támogatás kitekintéséhez (enterprisesupport@lookout.com):  

- **Azure AD-bérlői címtár azonosítója**  

- Az **Azure ad Group objektum azonosítója** a **teljes** kilátó Mobile Endpoint Security (MES) konzolhoz való hozzáféréssel rendelkező csoport számára.  
  Ezt a felhasználói csoportot az Azure AD-ben hozza létre, hogy tartalmazza azokat a felhasználókat, akik *teljes hozzáféréssel* rendelkeznek a **kilátó konzolba**való bejelentkezéshez. A felhasználóknak a csoport tagjának kell lenniük, vagy a választható *korlátozott hozzáférési* csoportnak a kilátó konzolra való bejelentkezéshez. 

- Az **Azure ad Group objektum azonosítója** a **korlátozott** kilátói hozzáférés-konzolt *(opcionális csoport)* tartalmazó csoport számára. 
  Ezt a választható felhasználói csoportot az Azure AD-ben úgy hozza létre, hogy tartalmazza azokat a felhasználókat, akiknek nincs hozzáférésük a kilátó konzol több konfigurációs és regisztrációval kapcsolatos moduljához. Ezek a felhasználók ehelyett csak olvasási hozzáféréssel rendelkeznek a kilátó konzol **Security Policy** moduljához. A felhasználóknak ennek a választható csoportnak vagy a szükséges *teljes hozzáférési* csoportnak a tagjainak kell lenniük a kilátó konzolba való bejelentkezéshez.

 > [!TIP] 
 > Az engedélyekről további információt talál a Lookout-webhelyen, [ebben a cikkben](https://personal.support.lookout.com/hc/articles/114094105653).

### <a name="collect-information-from-azure-ad"></a>Adatgyűjtés az Azure AD-ből 

1. Jelentkezzen be a [Azure Portal](https://portal.azure.com) globális rendszergazdai fiókkal.

2. Nyissa meg a **Azure Active Directory** > **tulajdonságokat** , és keresse meg a **címtár-azonosítót**. A *Másolás* gombbal másolja a CÍMTÁR-azonosítót, majd mentse egy szövegfájlba.

   ![Azure AD-tulajdonságok](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Ezután keresse meg az Azure ad-csoport AZONOSÍTÓját azon fiókok esetében, amelyeket az Azure AD-felhasználók számára a kilátó konzolhoz való hozzáférés biztosításához használ. Egy csoport a *teljes hozzáféréshez*, a második pedig a *korlátozott hozzáféréshez* nem kötelező. Az *objektumazonosító*beszerzése az egyes fiókokhoz:  
   1. A *csoportok – minden csoport* ablaktábla megnyitásához lépjen **Azure Active Directory** > **csoportok** elemre.  

   2. Válassza ki a *teljes hozzáféréshez* létrehozott csoportot az *Áttekintés* panel megnyitásához.  

   3. Másolja a *Másolás* gombot az objektumazonosító másolásához, majd mentse egy szövegfájlba.  

   4. Ha ezt a csoportot használja, ismételje meg a *korlátozott hozzáférési* csoport folyamatát.  

      ![Azure AD-csoport objektumának azonosítója](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Az információk összegyűjtése után lépjen kapcsolatba a kilátó támogatási szolgálatával (e-mail: enterprisesupport@lookout.com). A megtekintő támogatás az elsődleges kapcsolattartóval együttműködve előkészíti az előfizetést, és létrehozza a kilátó vállalati fiókot az Ön által megadott információk alapján.  

## <a name="configure-your-lookout-subscription"></a>A kilátó előfizetés konfigurálása  
Miután a kinézeti támogatás létrehozza a kilátó vállalati fiókot, a kisegítő támogatás e-mailt küld a vállalat elsődleges kapcsolattartójának, amely a bejelentkezési URL-címre mutat: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Kezdeti bejelentkezés  
A megjelenítői MES-konzolra való első bejelentkezéskor megjelenik egy beleegyező lap (https://aad.lookout.com/les?action=consent). Az Azure AD globális rendszergazdája csak bejelentkezik, és **fogadja el**. A következő bejelentkezéshez nem szükséges, hogy a felhasználó ezen szintű Azure AD-jogosultsággal rendelkezzen. 

 Egy hozzájárulást kérő lap jelenik meg. A regisztráció befejezéséhez válassza az **elfogad** lehetőséget. 
   @no__t – a 0screenshot első bejelentkezési oldalának a @ no__t-1

Ha elfogadja és beleegyezik, a rendszer átirányítja a kilátó konzolra.

A kezdeti bejelentkezés és a belefoglalt engedély befejezése után a https://aad.lookout.com webhelyről bejelentkező felhasználók átirányítva lesznek a MES-konzolra. Ha a beleegyezikés még nem lett megadva, az összes bejelentkezési kísérlet helytelen bejelentkezési hibát eredményez.

### <a name="configure-the-intune-connector"></a>Az Intune-összekötő konfigurálása  
Az alábbi eljárás azt feltételezi, hogy korábban létrehozott egy felhasználói csoportot az Azure AD-ben a kilátó üzembe helyezésének teszteléséhez. Az ajánlott eljárás a felhasználók egy kis csoportja, hogy a kilátó és az Intune-rendszergazdák megismerjék a termék integrációját. Miután ismerősek voltak, kiterjesztheti a beléptetést a felhasználók további csoportjaira.

1. Jelentkezzen be a [kilátó MES-konzolra](https://aad.lookout.com) , és nyissa meg a **System** > **összekötőket**, majd válassza az **összekötő hozzáadása**elemet.  Válassza az **Intune**lehetőséget.

   ![A kilátó konzoljának képe az Intune lehetőséggel az összekötők lapon](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. A *Microsoft Intune* ablaktáblán válassza a **kapcsolatbeállítások** lehetőséget, és adja meg a **szívverés gyakoriságát** percben. 

   ![A kapcsolatbiztonsági beállítások lap és a beállított szívverési gyakoriság képe](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Válassza a **beléptetések kezelése**lehetőséget, és **a következő Azure ad biztonsági csoportok használatával azonosítsa a Lookout for Workban regisztrálni kívánt eszközöket**, adja meg a kilátóhoz használni kívánt Azure ad-csoport *nevét* , majd kattintson a Save (Mentés) gombra.  **változások**.

    ![képernyőkép az Intune-összekötő regisztrálási oldaláról](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **Tudnivalók a használt csoportokról**:
   - Az ajánlott eljárás az, ha egy Azure AD-beli biztonsági csoporttal rendelkezik, amely kis számú felhasználót tartalmaz a kilátó integráció teszteléséhez.
   - A **csoport neve** megkülönbözteti a kis-és nagybetűket a Azure Portal biztonsági csoportjának **tulajdonságaiban** látható módon.  
   - A **beléptetési felügyelethez** megadott csoportok határozzák meg azokat a felhasználókat, akiknek az eszközei regisztrálva lesznek a figyeléssel. Ha egy felhasználó beléptetési csoportban van, az Azure AD-beli eszközei regisztrálva lesznek, és jogosultak az aktiválásra a MES-ben. Amikor a felhasználó először nyitja meg a *Lookout for Work* alkalmazást egy támogatott eszközön, a rendszer felszólítja az aktiválásra.

4. Válassza az **állapot-szinkronizálás** lehetőséget, és győződjön meg arról, hogy az *eszköz állapota* és **a** *veszélyforrás állapota* beállítás értéke be.  Mindkettő szükséges ahhoz, hogy a kilátó Intune-integráció megfelelően működjön.  

5. Válassza a **hibakezelés**lehetőséget, adja meg azt az e-mail-címet, amelyen a hibajelentések érkeznek, majd kattintson a **módosítások mentése**gombra.
 
   ![képernyőkép az Intune-összekötő hibakezelési oldaláról](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Az összekötő konfigurálásának befejezéséhez válassza az **összekötő létrehozása** lehetőséget. Később, amikor elégedett az eredménnyel, kiterjesztheti a regisztrációt további felhasználói csoportokra.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Az Intune konfigurálása Mobile Threat Defense-szolgáltatóként való kilátó használatára
Miután konfigurálta a MES-t, be kell állítania egy kapcsolódást az Intune-beli figyeléshez.  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

2. Lépjen az **eszköz megfelelősége** > **Mobile Threat Defense** elemre, és válassza a **Hozzáadás**lehetőséget.

3. Az *összekötő hozzáadása* ablaktáblán használja a legördülő listát, és válassza a **Lookout for Work**lehetőséget.  

4. Kattintson a **Létrehozás** gombra. Miután az összekötő kapcsolatot létesít a MES-vel, az *összekötő beállításai* elérhetővé válnak.

5. Állítsa **be az** **alkalmazások szinkronizálásának engedélyezése iOS-eszközökön** beállítását. 

6. A konfiguráció befejezéséhez válassza a **Mentés** lehetőséget.  Az Intune és a megjelenő MES már integrálva van, és használatra kész.


## <a name="additional-settings-in-the-lookout-mes-console"></a>További beállítások a kilátó MES-konzolon
A következő további beállítások konfigurálhatók a kilátó MES-konzolon.  

### <a name="configure-enrollment-settings"></a>Regisztrációs beállítások konfigurálása
A kilátó MES-konzolon válassza a **System** >  a**Beléptetés** > **regisztrációs beállítások**kezelése lehetőséget.  

- A leválasztott **állapot**mezőben határozza meg, hogy hány nap elteltével legyen leválasztva a nem csatlakoztatott eszköz.  

  A leválasztott eszközöket nem megfelelőnek tekinti a program, és az Intune-beli feltételes hozzáférésre vonatkozó szabályzatok alapján törli a munkahelyi alkalmazásokhoz való hozzáférésüket. 1 és 90 nap közötti időtartam adható meg.

  ![Beléptetési beállítások a rendszermodulon](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>E-mail-értesítések konfigurálása
Ha e-mailben szeretne riasztásokat kapni a fenyegetésekről, jelentkezzen be a [kilátói MES-konzolra](https://aad.lookout.com) azzal a felhasználói fiókkal, amelyről értesítést szeretne kapni  

- Lépjen a **Beállítások** elemre, majd állítsa be az értesítéseket, **amelyeken**fogadni kíván, majd **mentse** a módosításokat.  

- Ha már nem szeretne e-mail-értesítéseket kapni, állítsa be az értesítéseket a **kikapcsoláshoz** , és mentse a módosításokat.

  ![képernyőkép a beállítások lapról a megjelenő felhasználói fiókkal](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>A veszélyforrások besorolásának konfigurálása  
A mobil végpontok biztonsági kilátója a különböző típusú mobil fenyegetéseket osztályozza. A kilátó veszélyforrások besorolásának alapértelmezett kockázati szintjei vannak társítva. A kockázati szintek bármikor módosíthatók a vállalat igényeinek megfelelően.

A veszélyforrások szintjének besorolásával és a hozzájuk társított kockázati szintek kezelésével kapcsolatos információkért lásd: a [veszélyforrások Kilátójának áttekintése](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> A kockázati szintek a mobil végpontok biztonságának fontos aspektusa, mert az Intune-integráció az eszköz megfelelőségét a kockázati szintek alapján számítja ki futásidőben.  
> 
> Az Intune-rendszergazda állítja be a szabályzatban, hogy egy eszköz akkor nem megfelelő, ha egy olyan aktív fenyegetés található rajta, amelynek a szintje: **Magas**, **Közepes** vagy **Alacsony**. Az eszköz megfelelőségi besorolása közvetlenül az Intune-ban vezérli a veszélyforrások besorolási szabályzatát.  

## <a name="monitor-enrollment"></a>Regisztráció figyelése
A telepítés befejezése után a Mobile Endpoint Security megkezdi az Azure AD lekérdezését azon eszközök esetében, amelyek megfelelnek a megadott regisztrációs csoportoknak.  A beléptetett eszközökre vonatkozó információkat a kilátó MES-konzolon elérhető **eszközök** pontban találja.  
- Az eszközök kezdeti állapota *függőben*van.  
- Az eszköz állapotának frissítései a *Lookout for Work* alkalmazás telepítése, megnyitása és aktiválása után az eszközön.

Az eszközre telepített *Lookout for Work* alkalmazás beszerzésével kapcsolatos további információkért lásd: [figyelés a Work-alkalmazások hozzáadásához az Intune](mtd-apps-ios-app-configuration-policy-add-assign.md)-nal.

## <a name="next-steps"></a>További lépések

[Lookout-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)
