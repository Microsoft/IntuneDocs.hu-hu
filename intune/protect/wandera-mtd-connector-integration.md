---
title: A Wanderer Mobile Threat Protection-integráció beállítása az Intune-nal
titleSuffix: Intune on Azure
description: A Wanda Mobile Threat Protection-megoldás beállítása a Microsoft Intune a mobileszközök hozzáférésének szabályozásához a vállalati erőforrásokhoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e565f40aac2a2b97f547a5b68a70a887d9e820ae
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207468"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>A Wander Mobile Threat Protection integrálása az Intune-nal  

A Wanda Mobile Threat Defense megoldás az Intune-nal való integrálásához hajtsa végre az alábbi lépéseket.  

> [!NOTE]
> A Mobile Threat Defense gyártója nem regisztrált eszközök esetén nem támogatott.

## <a name="before-you-begin"></a>Előkészületek  

Mielőtt elkezdené a Wanda integrálását az Intune-nal, ellenőrizze, hogy rendelkezik-e az alábbi előfeltételekkel:
- Microsoft Intune-előfizetés  
- Azure Active Directory rendszergazdai hitelesítő adatok a következő engedélyek megadására:  
  - Bejelentkezés és felhasználói profil olvasása  
  - A címtár elérése a bejelentkezett felhasználó nevében  
  - Címtáradatok olvasása  
  - Eszközadatok küldése az Intune-ba  

- Vándor-előfizetés:
  - Egy vagy több olyan bolyongó fiók, amely az 1. kapcsolathoz van licenccel  
  - Egy fiók a Super Administrator jogosultságokkal a Wanda-ben  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>A Wanda Mobile Threat Defense alkalmazás engedélyezése  

A Wanda Mobile Threat Defense alkalmazás engedélyezési folyamata:  
- A Wanda Mobile Threat Defense szolgáltatás lehetővé teszi, hogy az eszköz állapotával kapcsolatos adatokat az Intune-nal továbbítsa.  
- A Wanda szinkronizálja az Azure AD regisztrációs csoportjának tagságát az eszköz adatbázisának feltöltéséhez.  
- Az Azure AD egyszeri bejelentkezés (SSO) használatának engedélyezése a Wanda RADAR felügyeleti portálján.  
- Engedélyezi a Wanda Mobile Threat Defense alkalmazásnak, hogy bejelentkezzen az Azure AD SSO használatával.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>A Wanderer Mobile Threat Defense integrációjának beállítása  
Az a Wanderers-hez való *csatlakozási* művelethez egy egyszeri konfigurációs folyamat szükséges, amelyet az Intune és a Wanda konzolon is végre kell hajtani. A konfigurációs folyamat körülbelül 15 percet vesz igénybe. A konfigurálást a vándor technikai fiókjával vagy a támogatási képviselővel való koordináció nélkül végezheti el.  

### <a name="enable-support-for-wandera-in-intune"></a>A Bolyongás támogatásának engedélyezése az Intune-ban

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** > **Mobile Threat Defense** > **Hozzáadás**lehetőséget.
3. Az **összekötő hozzáadása** lapon használja a legördülő menüt, és válassza a **Bolyongás**lehetőséget. Majd válassza a **Létrehozás**lehetőséget.  
4. A Mobile Threat Defense panelen válassza a **Wanda** MTD-összekötőt az összekötők listájáról az *összekötő szerkesztése* ablaktábla megnyitásához. Válassza **a Bolyongás felügyeleti konzol megnyitása** lehetőséget a [radar](https://radar.wandera.com/login), a Wanda felügyeleti konzol megnyitásához és a bejelentkezéshez. 
5. A Wanda-konzolon lépjen a **beállítások** > **az** *Microsoft Intune*a következőre:, és **válassza a (** **

   ![Intune kiválasztása](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

6. Válassza az **engedélyek megadása** lehetőséget az Intune-portálhoz való kapcsolódás megnyitásához. Jelentkezzen be az Intune rendszergazdai hitelesítő adataival, jelölje be a jelölőnégyzetet, majd **fogadja el** az engedélyek kérését.  

   ![Engedélyek elfogadása](./media/wandera-mtd-connector-integration/permissions.png) 

7. A Wanda befejezi a kapcsolódást, és visszaadja a RADAR felügyeleti konzoljának. Szükség szerint ismételje meg a folyamatot a további konfigurációk elérésének **megadásához** .  

   ![Integrációk és engedélyek](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

8. A RADAR-konzolon másolja az **SyncOnly** csoport nevét, amely megjelenik az **** Ezt a nevet fogja használni az Intune-ban a Bolyongás szinkronizálására szolgáló csoport konfigurálásához.

   ![Szinkronizálási csoport](./media/wandera-mtd-connector-integration/sync-group-name.png) 

9. Térjen vissza az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -konzolra, és szerkessze a WANDa MTD-összekötőt. Állítsa be az elérhető kapcsolókat **a be**értékre, majd a konfiguráció **mentése** lehetőséget.  

   ![Bolyongás engedélyezése](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Az Intune és a Wanda most már csatlakoztatva van.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>A Wander-alkalmazások és a szinkronizálási csoport konfigurálása  
A Bolyongás üzembe helyezéséhez hozzá kell adnia a Wanda Mobile Apps szolgáltatást a használt platformokhoz (iOS és Android) az Intune-hoz, és hozzá kell rendelnie őket egy adott csoporthoz a szinkronizáláshoz; a *SyncOnly* csoport. 

A következő fejezetek és eljárások végigvezetik a folyamaton.

További információ erről a folyamatról: Wanda, bejelentkezés a Wanda [radarba](https://radar.wandera.com/login). Nyissa meg a **beállítások** > a következőt:, majd válassza az **alkalmazás leküldése** **lapot, majd**a **Microsoft Intune**lehetőséget. Az alkalmazás leküldéses lapja az Intune-ra vonatkozó utasításokkal frissül.  

### <a name="add-the-wandera-apps"></a>A Wanda-alkalmazások hozzáadása  
Ügyfélalkalmazások létrehozása az Intune-ban a vándor alkalmazás üzembe helyezéséhez Android és iOS rendszerű eszközökön. Lásd: [MTD-alkalmazások hozzáadása](mtd-apps-ios-app-configuration-policy-add-assign.md) a bolyongó alkalmazásokhoz tartozó eljárásokhoz és egyéni részletekhez.  

Az alkalmazások létrehozása után térjen vissza ide a szinkronizálási csoport létrehozásához és az alkalmazások hozzárendeléséhez.

### <a name="create-the-synchronization-group-and-assign-the-apps"></a>A szinkronizálási csoport létrehozása és az alkalmazások kiosztása

1. Szerezze be annak a **SyncOnly** -csoportnak a nevét, amely **az, hogy** a Wanda radar-konzolján megjelenik az alábbi, az a. Előfordulhat, hogy a 7. lépés során mentette ezt a nevet, miközben [engedélyezi a Wanderers használatát az Intune-ban](#enable-support-for-wandera-in-intune). Ezt a nevet használja az Intune-beli csoport neveként a Bolyongás szinkronizálásához.  

2. A Endpoint Manager felügyeleti központban lépjen a **csoportok** elemre, és válassza az **új csoport**lehetőséget. A következő beállítás megadásával konfigurálhatja a szinkronizálási csoportot a Bolyongás általi használatra:
   - **Csoport típusa**: **Biztonság**
   - **Csoport neve**: adja meg a **SyncOnly** nevét, amelyet a Wanda radar felügyeleti konzolról kapott le.

   ![a szinkronizálási csoport konfigurálása](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Válassza ki a **tagokat** , és rendeljen hozzá olyan csoportokat, amelyek tartalmazzák a Bolyongás használatával használni kívánt Android-és iOS-eszközöket.

4. A csoport mentéséhez válassza a **Létrehozás** lehetőséget.

További információ: [alkalmazások telepítése](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>A bolyongó alkalmazások kiosztása a szinkronizálási csoportnak  
Ismételje meg az alábbi eljárást az iOS-hez és Androidhoz létrehozott Wanda-alkalmazáshoz.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** lehetőséget, és válassza ki a vándor alkalmazást.
3. Válassza a **hozzárendelések** , majd a **Csoport hozzáadása**lehetőséget.  
4. A *Csoport hozzáadása* panelen a *hozzárendelés típusa* beállításnál válassza a **kötelező**lehetőséget.
5. Válassza a **befoglalt csoportok**lehetőséget, majd **válassza ki a felvenni kívánt csoportokat**. Adja meg a Wanda-szinkronizáláshoz létrehozott csoportot, majd kattintson **az OK** **gombra >  > OK gombra.** **** Válassza a **Mentés** lehetőséget a csoport hozzárendelésének befejezéséhez. 

## <a name="next-steps"></a>További lépések  
Most, hogy konfigurálta az integrációt, megkezdheti a házirendek konfigurálását, a speciális feltételes hozzáférés beállítását és a jelentések megtekintését a Wanda felügyeleti konzolon. A Bolyongás kezelésével és konfigurálásával kapcsolatos további tudnivalókért tekintse meg a következő témakört: [támogatási központ első lépések útmutató](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) a Wanda dokumentációjában. 
