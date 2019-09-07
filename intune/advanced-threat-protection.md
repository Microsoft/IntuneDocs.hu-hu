---
title: A Microsoft Defender ATP használata a Microsoft Intune-Azure-ban | Microsoft Docs
description: A Microsoft Defender komplex veszélyforrások elleni védelem (Microsoft Defender ATP) használata az Intune-nal, beleértve a telepítést és a konfigurálást, az Intune-eszközök előkészítését az ATP használatával, majd az Intune-nal való megfelelőség és a feltételes feltételek alapján hozzáférési szabályzatok a hálózati erőforrások megóvásához.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d9fe180e81c9e661954dd0986f05ac3b5e749ed
ms.sourcegitcommit: e477e399cba673a2a9e1fa342e8303ed993801eb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739187"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>A Microsoft Defender ATP megfelelőségének betartatása feltételes hozzáféréssel az Intune-ban  

A Microsoft Defender komplex veszélyforrások elleni védelem (Microsoft Defender ATP Microsoft Intune) integrálható a mobil veszélyforrások elleni védelem megoldásával, így megelőzheti a biztonsági réseket, és korlátozhatja a szervezeten belüli szabálysértések hatását. A Microsoft Defender ATP a Windows 10 vagy újabb rendszert futtató eszközökön működik.

A sikeres végrehajtáshoz használja a következő konfigurációkat a koncerten:
- **Szolgáltatások közötti kapcsolat létesítése az Intune és a Microsoft DEFENDER ATP között**. Ez a szolgáltatás lehetővé teszi, hogy a Microsoft Defender ATP adatokat gyűjtsön a számítógép kockázatáról az Intune-nal felügyelt Windows 10-es eszközökről.  
- **Eszköz-konfigurációs profil használata az eszközök bevezetéséhez a Microsoft DEFENDER ATP használatával**. A Microsoft Defender ATP szolgáltatással való kommunikációhoz és a kockázati szint felmérését segítő információk biztosításához az eszközök bevezetésével konfigurálhatja azokat.  
 - **Az eszköz megfelelőségi szabályzatával állíthatja be az engedélyezni kívánt kockázati szintet**. A kockázati szinteket a Microsoft Defender ATP szolgáltatja.  Azok az eszközök, amelyek túllépik az engedélyezett kockázati szintet, nem megfelelőként vannak azonosítva.  
- **Feltételes hozzáférési szabályzattal** megakadályozhatja, hogy a felhasználók hozzáférjenek a vállalati erőforrásokhoz a nem megfelelő eszközökről.  

Emellett az Intune-nak a Microsoft Defender ATP-vel való integrálásával kihasználhatja a ATPs veszélyforrások elleni & sebezhetőségek felügyeletét (TVM), és az Intune használatával javíthatja a [TVM által azonosított végponti gyengeséget](atp-manage-vulnerabilities.md).

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>Példa a Microsoft Defender ATP használatára az Intune-nal  

A következő példa segít megmagyarázni, hogyan működnek együtt a megoldások a szervezet védelmének elősegítése érdekében. Ebben a példában a Microsoft Defender ATP és az Intune már integrálva van.  

Vegye fontolóra egy olyan eseményt, amelyben valaki beágyazott kártékony kóddal rendelkező Word-mellékletet küld a szervezeten belüli felhasználó számára.  
- A felhasználó megnyitja a mellékletet, és engedélyezi annak tartalmát.  
- Megemelt jogosultsági szintű támadás kezdődik, és a támadó egy távoli számítógépről rendszergazdai jogosultságot szerez az áldozat eszközén.  
- A támadó ezután távolról hozzáfér a felhasználó többi eszközéhez is. A biztonsági incidens a teljes vállalatot is érintheti.  

A Microsoft Defender ATP segítséget nyújt az ilyen forgatókönyvhöz hasonló biztonsági események megoldásához.  
- A példánkban a Microsoft Defender ATP azt észleli, hogy az eszköz rendellenes kódot hajtott végre, a folyamat jogosultság-eszkalációját, a rosszindulatú kód beadását és a gyanús távoli rendszerhéj kiosztását.  
- Az eszközről érkező műveletek alapján a Microsoft Defender ATP [magas kockázatnak minősíti az eszközt](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity) , és részletes jelentést készít a gyanús tevékenységekről a Microsoft Defender Security Center portálon.  

Mivel az Intune-eszköz megfelelőségi szabályzata olyan eszközöket tartalmaz, amelyek *közepes* vagy *magas* szintű kockázatot jelentenek nem megfelelőként, a feltört eszköz nem megfelelőnek minősül. Ez a besorolás lehetővé teszi, hogy a feltételes hozzáférési szabályzata beindítson és letiltsa az eszközről a vállalati erőforrásokhoz való hozzáférést.  

## <a name="prerequisites"></a>Előfeltételek

Ha a Microsoft Defender ATP-t az Intune-nal szeretné használni, győződjön meg róla, hogy a következő konfigurálva van, és készen áll a használatra:

- Licenccel rendelkező bérlő az Enterprise Mobility + Security E3 és Windows E5 (vagy Microsoft 365 Enterprise E5) csomaghoz
- Microsoft Intune környezet az [Intune-nal felügyelt](windows-enroll.md) Windows 10-es eszközökhöz, amelyek az Azure AD-ba is be vannak léptetve
- [Microsoft DEFENDER ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) és hozzáférés a microsoft Defender Security Centerhoz (ATP-portál)

## <a name="enable-microsoft-defender-atp-in-intune"></a>A Microsoft Defender ATP engedélyezése az Intune-ban

Az első lépés a szolgáltatás és a szolgáltatás közötti kapcsolat beállítása az Intune és a Microsoft Defender ATP között. Ehhez rendszergazdai hozzáférésre van szükség a Microsoft Defender Security Centerhoz és az Intune-hoz.  

### <a name="to-enable-defender-atp"></a>A Defender ATP engedélyezése  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **eszköz megfelelősége** > **Microsoft Defender ATP**lehetőséget, majd az *összekötő beállításai*alatt válassza **a Microsoft Defender Security Center megnyitása**lehetőséget.

    ![Válassza ki a Microsoft Defender Security Center megnyitásához](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. A **Microsoft Defender Security Centerban**:
    1. Válassza a **Beállítások** > **Speciális funkciók** lehetőséget.
    2. A **Microsoft Intune kapcsolathoz** válassza a **Be** lehetőséget:

        ![Az Intune-hoz való kapcsolódás engedélyezése](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Válassza a **Beállítások mentése** lehetőséget.

4. Lépjen vissza az Intune-ba, a**Microsoft Defender ATP** **eszköz megfelelősége** > . Állítsa be a **Windows-eszközök csatlakoztatása 10.0.15063 és újabb verzióját a Microsoft DEFENDER ATP** -be **a**következőre:.
5. Kattintson a **Mentés** gombra.

Ezt a feladatot általában egyszer kell elvégezni. Miután engedélyezte a Microsoft Defender ATP-t az Intune-bérlőhöz, nem kell újra végrehajtania.

> [!TIP]  
> Amikor új alkalmazást integrál az Intune Mobile Threat Defense-be, és engedélyezi az Intune-nal való kapcsolatot, az Intune egy klasszikus feltételes hozzáférési szabályzatot hoz létre Azure Active Directoryban. Minden olyan MTD-alkalmazás, amelyet integrál, beleértve a [DEFENDER ATP](advanced-threat-protection.md) -t vagy bármely további [MTD-partnert](mobile-threat-defense.md#mobile-threat-defense-partners), új klasszikus feltételes hozzáférési szabályzatot hoz létre. Ezek a szabályzatok figyelmen kívül hagyhatók, de nem szerkeszthetők, nem törölhetők és nem tilthatók le.
> 
> Klasszikus feltételes hozzáférési szabályzatok a MTD-alkalmazásokhoz: 
> 
> - Az Intune-MTD arra használják, hogy az eszközök regisztrálva legyenek az Azure AD-ben, hogy a MTD-partnerekkel való kommunikáció előtt rendelkezzenek az eszköz azonosítójával. Az azonosító megadása kötelező, hogy az eszközök és az állapotuk sikeresen jelentse az Intune-nak.  
> - Semmilyen más felhőalapú alkalmazásra vagy erőforrásra nincs hatással.  
> - Nem különböznek a MTD kezeléséhez esetlegesen létrehozott feltételes hozzáférési házirendektől.
> - Alapértelmezés szerint a kiértékeléshez használt egyéb feltételes hozzáférési szabályzatok nem működnek együtt.  
> 
> A klasszikus feltételes hozzáférési szabályzatok megjelenítéséhez [Az Azure](https://portal.azure.com/#home)-ban lépjen **Azure Active Directory** > a**feltételes hozzáférés** > **klasszikus házirendjei**elemre.

## <a name="onboard-devices-by-using-a-configuration-profile"></a>Eszközök előkészítése konfigurációs profil használatával

Miután létrehozta a szolgáltatások közötti kapcsolatot az Intune és a Microsoft Defender ATP között, az Intune által felügyelt eszközöket az ATP-be irányítja, így a kockázati szintjére vonatkozó adatokat összegyűjtheti és felhasználhatja. Az eszközök előkészítéséhez a Microsoft Defender ATP eszköz konfigurációs profilját használhatja.  

A Microsoft Defender ATP-vel létesített kapcsolatok létrehozásakor az Intune a Microsoft Defender ATP bevezetési konfigurációs csomagját kapta. Ez a csomag az eszköz konfigurációs profiljával rendelkező eszközökre van telepítve. A konfigurációs csomag úgy konfigurálja az eszközöket, hogy a [Microsoft DEFENDER ATP-szolgáltatásokkal](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) kommunikáljanak a fájlok vizsgálatához, a fenyegetések észleléséhez, és jelentse a kockázatot a Microsoft Defender ATP-nek.  

Miután bevezet egy eszközt a konfigurációs csomag használatával, nem kell újra végrehajtania. Eszközöket [csoportszabályzat vagy a System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) használatával is bevonhat.


### <a name="create-the-device-configuration-profile"></a>Az eszköz konfigurációs profiljának létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adjon meg **Nevet** és **Leírást**.
4. A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.
5. A **Profil típusa**beállításnál válassza a **Microsoft Defender ATP (Windows 10 asztali verzió)** lehetőséget.
6. A beállítások konfigurálása:

   - **Microsoft DEFENDER ATP-ügyfél konfigurációs csomagjának típusa**: Válassza **a** bevezetést, hogy hozzáadja a konfigurációs csomagot a profilhoz. A **Regisztráció megszüntetése** lehetőséget választva eltávolíthatja profilból a konfigurációs csomagot.
  
     > [!NOTE]  
     > Ha megfelelően létesített egy, a Microsoft Defender ATP-sel létesített kapcsolatokat **, az Intune automatikusan** előkészíti a konfigurációs profilt, és a **Microsoft Defender ATP-ügyfél konfigurációs csomagjának típusa** beállítás nem lesz elérhető.
  
    - **Minta megosztása az összes fájlhoz**: A **lehetővé teszi a** minták gyűjtését és a Microsoft Defender ATP-vel való megosztását. Ha például egy gyanús fájlt lát, beküldheti azt a Microsoft Defender ATP-be a Deep Analysis használatával. **Nincs konfigurálva, nem** oszt meg egyetlen mintát sem a Microsoft Defender ATP-ben.
    - A **telemetria-jelentéskészítés gyakoriságának gyorsítása**: A magas kockázatú eszközök esetében **engedélyezze** ezt a beállítást, hogy az a Microsoft Defender ATP szolgáltatásnak gyakrabban telemetria jelentést.

    A [Windows 10-es gépek System Center Configuration Manager használatával történő](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) előkészítése további részleteket tartalmaz ezekről a Microsoft Defender ATP-beállításokról.

7. Válassza az **OK**, majd a **Létrehozás** lehetőséget a változások mentéséhez. Ezzel létrejön a profil.
8. [Rendelje hozzá az eszköz konfigurációs profilját](device-profile-assign.md) a Microsoft Defender ATP-vel felmérni kívánt eszközökhöz.  


## <a name="create-and-assign-the-compliance-policy"></a>A megfelelőségi szabályzat létrehozása és kiosztása  

A megfelelőségi szabályzat meghatározza, hogy milyen kockázati szintet kell figyelembe venni az eszköz számára.

### <a name="create-the-compliance-policy"></a>A megfelelőségi szabályzat létrehozása  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
3. Adjon meg **Nevet** és **Leírást**.
4. A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.
5. A **Microsoft DEFENDER ATP** -beállítások részen állítsa be, hogy **az eszköz a gép kockázati pontszáma alatt vagy alatt legyen** az előnyben részesített szint. 
   
   A fenyegetések szintjének besorolását a [Microsoft DEFENDER ATP határozza meg](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Törlés**: Ez a szint a legbiztonságosabb. Az eszközön nem lehetnek meglévő fenyegetések, és továbbra is hozzáférhetnek a vállalati erőforrásokhoz. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül. (A Microsoft Defender ATP-felhasználók a *biztonságos értéket biztosítják*.)
   - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. A közepes vagy magas veszélyforrású eszközök nem megfelelőek.
   - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt fenyegetések alacsony vagy közepes méretűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.
   - **Magas**: Ez a szint a legkevésbé biztonságos, és lehetővé teszi az összes veszélyforrás szintjét. A magas, közepes vagy alacsony veszélyforrású eszközök megfelelőnek minősülnek.

6. Válassza az **OK**, majd a **Létrehozás** lehetőséget a változások mentéséhez (ezzel létrejön a szabályzat).  
7. [Rendelje hozzá az eszköz megfelelőségi szabályzatát](create-compliance-policy.md#assign-user-groups) a megfelelő csoportokhoz.



## <a name="create-a-conditional-access-policy"></a>Feltételes hozzáférési szabályzat létrehozása  

A feltételes hozzáférési szabályzat blokkolja a megfelelőségi szabályzatban beállított fenyegetési szintet túllépő eszközök erőforrásokhoz való hozzáférését. Letilthatja az eszköz hozzáférését a vállalati erőforrásokhoz, például a SharePointhoz vagy az Exchange Online-hoz.  

> [!TIP]  
> A feltételes hozzáférés az Azure Active Directory (Azure AD) technológiája. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza a **feltételes hozzáférés** > **új szabályzat**lehetőséget.
2. Adjon meg **Nevet** a szabályzathoz és válassza a **Felhasználók és csoportok** lehetőséget. A befoglalási vagy kizárási lehetőségek használatával jelölje ki a szabályzathoz rendelendő csoportokat majd válassza a **Kész** lehetőséget.
3. Válassza a **Felhőalkalmazások** lehetőséget, és válassza ki a védeni kívánt alkalmazásokat. Az **Alkalmazások kijelölése** alatt választhatja például az **Office 365 SharePoint Online** és az **Office 365 Exchange Online** elemeket.

    A módosítások mentéséhez válassza a **Kész** gombot.

4. A **Feltételek** > **Ügyfélalkalmazások** választásával a szabályzat alkalmazásokra és böngészőkre is érvényesíthető. Választhatja például az **Igen**, majd a **Böngésző** és a **Mobilalkalmazások és asztali ügyfelek** lehetőségeket.

    A módosítások mentéséhez válassza a **Kész** gombot.

5. Válassza az **Engedélyezés** lehetőséget, ha feltételes hozzáférést szeretne alkalmazni az eszköz megfelelősége alapján. Választhatja például a **Hozzáférés engedélyezése** > **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget.

    A módosítások mentéséhez válassza az **Választ** gombot.

6. A módosítások mentéséhez válassza a **Szabályzat engedélyezése** majd a **Létrehozás** lehetőséget.



## <a name="monitor-device-compliance"></a>Az eszközmegfelelőség figyelése  

Ezután figyelje a Microsoft Defender ATP-megfelelőségi szabályzattal rendelkező eszközök állapotát.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközmegfelelőség** > **Megfelelés a szabályzatoknak** lehetőséget.
3. Keresse meg a Microsoft Defender ATP-szabályzatot a listában, és tekintse meg, hogy mely eszközök megfelelőek vagy nem megfelelőek.

## <a name="view-onboarding-status"></a>Bevezetési állapot megtekintése
Az Intune által felügyelt Windows 10-es eszközök bevezetési állapotának megtekintéséhez nyissa meg az **eszköz megfelelősége** > **Microsoft Defender ATP**-t. Ezen a lapon egy eszköz konfigurációs profiljának létrehozását is kezdeményezheti, amellyel több eszközt helyezhet üzembe a Microsoft Defender ATP-ben.

## <a name="next-steps"></a>További lépések  

[Microsoft Defender ATP feltételes hozzáférés](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)   
[A Microsoft Defender ATP kockázati irányítópultja](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  
Az [eszközökön felmerülő problémák megoldásához használjon biztonsági feladatokat a ATPs sebezhetőségi kezelésével](atp-manage-vulnerabilities.md).  
[Eszközmegfelelőségi szabályzatok – első lépések](device-compliance-get-started.md)  
 
