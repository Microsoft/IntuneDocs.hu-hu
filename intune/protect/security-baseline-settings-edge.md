---
title: Az Intune biztonsági alapkonfigurációinak beállításai a Microsoft Edge-hez
titleSuffix: Microsoft Intune
description: Az Intune által támogatott biztonsági alapbeállítások a Microsoft Edge böngésző kezeléséhez
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f4e56340d871ea5e0bcec7e541a418c32d021d0
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415553"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>A Microsoft Edge alapkonfigurációjának beállításai az Intune-hoz

Tekintse meg a Microsoft Edge webböngésző alapkonfigurációjának beállításait, amelyeket a Microsoft Intune támogat. A Microsoft Edge alapértékek a Microsoft Edge böngészők ajánlott konfigurációját jelentik, és előfordulhat, hogy nem egyeznek meg a többi biztonsági alapkonfiguráció alapértelmezett értékeivel.

> [!NOTE]
> A Microsoft Edge alapterve nyilvános előzetes verzióban érhető el. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **A Microsoft Defender SmartScreen-kérések megkerülésének megakadályozása a webhelyeken**  
  **Alapértelmezett**: engedélyezve  
  Microsoft Edge CSP: [böngésző/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  Ezzel a házirend-beállítással eldöntheti, hogy a felhasználók felülírhatják-e a Microsoft Defender SmartScreen-figyelmeztetéseit a potenciálisan rosszindulatú webhelyekről. 
  - Ha engedélyezi ezt a beállítást, a felhasználók nem hagyhatják figyelmen kívül a Microsoft Defender SmartScreen-figyelmeztetéseit, és a rendszer letiltja a webhelyet. 
  - Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználók figyelmen kívül hagyhatják a Microsoft Defender SmartScreen figyelmeztetéseit, és folytatják a webhelyet.

- **Az SSL minimálisan engedélyezett verziója**  
  **Alapértelmezett**: engedélyezve  

  Az SSL minimális támogatott verziójának beállítása. Ha úgy állítja be ezt a házirendet, hogy *nincs konfigurálva*, a Microsoft Edge a *TLS 1,0*alapértelmezett minimális verzióját használja. Ha az Engedélyezve értékre *van*állítva, a következő értékek közül választhat minimális verziót:

  - TLS 1,0
  - TLS 1,1
  - TLS 1,2

  - **Az SSL minimálisan engedélyezett verziója**  
    **Alapértelmezett**: TLS 1,2

- **A Microsoft Defender SmartScreen-figyelmeztetések megkerülésének megakadályozása a letöltésekkel kapcsolatban**  
  **Alapértelmezett**: engedélyezve  
  Microsoft Edge CSP: [böngésző/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  Ezzel a szabályzattal meghatározhatja, hogy a felhasználók felülírhatják-e a Microsoft Defender SmartScreen-figyelmeztetéseit a nem ellenőrzött letöltésekkel kapcsolatban.
  - Ha engedélyezi ezt a házirendet, a szervezet felhasználói nem hagyhatják figyelmen kívül a Microsoft Defender SmartScreen-figyelmeztetéseit, és nem tudják befejezni a nem ellenőrzött letöltéseket.
  - Ha letiltja vagy nem konfigurálja ezt a házirendet, a felhasználók figyelmen kívül hagyhatják a Microsoft Defender SmartScreen-figyelmeztetéseit, és nem ellenőrzött letöltéseket végezhetnek el.

- **Az SSL-figyelmeztetés oldalának engedélyezése a felhasználók számára**  
  **Alapértelmezett**: letiltva  
  Microsoft Edge CSP: [böngésző/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  A Microsoft Edge egy figyelmeztető oldalt jelenít meg, amikor a felhasználók SSL-hibákat tartalmazó helyeket látogatnak meg. Ha ezt a házirendet *engedélyezve* vagy *nincs konfigurálva*értékre állítja, a felhasználók a következő figyelmeztető lapokon keresztül is rákattintanak. Ha a szabályzat *le van tiltva*, a felhasználók nem kattintanak a figyelmeztetési oldalon. 

- **Alapértelmezett Adobe Flash-beállítás**  
  **Alapértelmezett**: engedélyezve  
  Microsoft Edge CSP: [böngésző/AllowFlash](https://docs.microsoft.coms/windows/client-management/mdm/policy-csp-browser#browser-allowflash), és [böngésző/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  Meghatározza, hogy az "PluginsAllowedForUrls" vagy a "PluginsBlockedForUrls" által nem jelzett webhelyek automatikusan futtatják-e az Adobe Flash beépülő modult. 

  - A "BlockPlugins" lehetőség kiválasztásával letilthatja az Adobe Flasht az összes webhelyen
  - Válassza a "ClickToPlay" lehetőséget, hogy az Adobe Flash fusson, de a felhasználónak a helyőrzőre kattintva elindíthatja azt.
  
   A "PluginsAllowedForUrls" és a "PluginsBlockedForUrls" szabályzatok minden esetben elsőbbséget élveznek a "DefaultPluginsSetting" szemben. Az automatikus lejátszás csak az "PluginsAllowedForUrls" szabályzatban explicit módon felsorolt tartományok esetében engedélyezett. 
   Ha engedélyezni szeretné az Automatikus lejátszást az összes helyhez, vegye fel a http://* és a https://*-t a listára. 
   
   - Ha úgy állítja be ezt a házirendet, hogy *ne legyen konfigurálva*, a felhasználó manuálisan is módosíthatja ezt a beállítást. * 2 = letilthatja az Adobe Flash beépülő modult * 3 = kattintson a korábbi "1" beállításhalmaz engedélyezése-all értékre, de ezt a funkciót már csak az "PluginsAllowedForUrls" házirend kezeli. Az "1"-et használó meglévő házirendek a Click-to-Play módban fognak működni.  
 
  - **Alapértelmezett Adobe Flash-beállítás**  
    **Alapértelmezett**: az Adobe Flash beépülő modul letiltása

- **Hely elkülönítésének engedélyezése minden helyhez**  
  **Alapértelmezett**: engedélyezve  

  Az "SitePerProcess" házirend segítségével megakadályozható, hogy a felhasználók elhagyják az összes hely elkülönítésének alapértelmezett viselkedését. A IsolateOrigins házirend segítségével elkülönítheti a további, finomabb szempontokat is.

  - Ha a házirend *engedélyezve*van, a felhasználók nem tilthatják le az alapértelmezett viselkedést, ahol az egyes helyek a saját folyamataiban futnak. 
  - Ha a *letiltott* vagy a *nincs konfigurálva*beállítást használja, a felhasználók eldönthetik a helyek elkülönítését. (Például a "hely elkülönítésének tiltása" bejegyzés használatával a edge://flags.) Ha letiltja a házirendet, vagy nem konfigurálja a házirendet, nem kapcsolja ki a hely elkülönítését.

- **Támogatott hitelesítési sémák**  
  **Alapértelmezett**: engedélyezve  

  Meghatározza, hogy mely HTTP-hitelesítési sémák támogatottak. A szabályzatot a következő értékek használatával állíthatja be: alapszintű, kivonatoló, NTLM és egyeztetés. Több értéket vesszővel válassza el egymástól. Ha nem konfigurálja ezt a házirendet, a rendszer mind a négy sémát használja.
 
  - **Támogatott hitelesítési sémák**  
    Válasszon a következő lehetőségek közül: 
    - Alapvető
    - Digest
    - NTLM *(alapértelmezés szerint kiválasztva)*
    - Egyeztetés *(alapértelmezés szerint kiválasztva)*

- **Jelszavak mentésének engedélyezése a Password Managerben**  
  **Alapértelmezett**: letiltva  
  Microsoft Edge CSP: [böngésző/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Felhasználói jelszavak mentésének engedélyezése a Microsoft Edge-nek. 
  - Ha engedélyezi ezt a házirendet, a felhasználók elmenthetik a jelszavukat a Microsoft Edge-ben. Amikor legközelebb meglátogatják a webhelyet, a Microsoft Edge automatikusan megadja a jelszót. 
  - Ha letiltja ezt a házirendet, a felhasználók nem menthetik az új jelszavakat, de továbbra is használhatják a korábban mentett jelszavakat. 
  
  Ha *engedélyezi* vagy *letiltja*ezt a házirendet, a felhasználók nem változtathatják meg és nem bírálják felül ezt a szabályzatot a Microsoft Edge-ben. 
  
  Ha a beállítás *nincs konfigurálva*, a felhasználók menthetik a jelszavakat, és kikapcsolhatják ezt a funkciót.

- **Annak szabályozása, hogy mely bővítmények nem telepíthetők**  
  **Alapértelmezett**: engedélyezve  

  Azokat a bővítményeket sorolja fel, amelyeket a felhasználók nem telepíthetnek a Microsoft Edge-ben. Ha telepíti ezt a házirendet, a listán szereplő összes bővítmény le van tiltva, és a felhasználó nem fogja tudni engedélyezni azokat. Ha eltávolít egy elemet a letiltott bővítmények listájáról, a bővítményt a rendszer automatikusan újra engedélyezi, ha korábban már telepítették.
  
  A **\*** használatával blokkolhatja az összes olyan bővítményt, amely nem szerepel explicit módon az engedélyezési listán. Ha a házirend nincs *konfigurálva*, a felhasználók bármelyik bővítményt telepíthetnek a Microsoft Edge-ben. 
  
  Példa értéke: extension_id1 extension_id2.  
  <br>
  - **Bővítmény-azonosítók a felhasználónak meg kell akadályoznia a telepítést (vagy * az összes)**  
    Válassza a **Hozzáadás** lehetőséget, és adjon meg további bővítményeket. a **\*** alapértelmezés szerint ki van választva.

- **A Microsoft Defender SmartScreen konfigurálása**  
  **Alapértelmezett**: engedélyezve  
  Microsoft Edge CSP: [böngésző/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  Ezzel a házirend-beállítással beállíthatja, hogy be legyen-e kapcsolva a Microsoft Defender SmartScreen szolgáltatás. A Microsoft Defender SmartScreen figyelmeztető üzeneteket biztosít a felhasználók számára az esetleges adatlopó csalások és kártevő szoftverek elleni védelem érdekében. 
  
  - Alapértelmezés szerint a Microsoft Defender SmartScreen be van kapcsolva. Ha engedélyezi ezt a beállítást, a Microsoft Defender SmartScreen be van kapcsolva, és a felhasználók nem kapcsolhatják ki.
  - Ha letiltja ezt a beállítást, a Microsoft Defender SmartScreen ki van kapcsolva, és a felhasználók nem kapcsolhatják be. 
  - Ha a *nincs konfigurálva*értékre van állítva, a felhasználók eldönthetik, hogy a Microsoft Defender smartscreent használják-e. 
  
  Ez a szabályzat csak olyan Windows-példányokon érhető el, amelyek Microsoft Active Directory-tartományhoz csatlakoznak, vagy Windows 10 Pro-vagy Enterprise-példányokon, amelyek az eszközök felügyeletére vannak regisztrálva.

- **Felhasználói szintű natív üzenetküldési gazdagépek engedélyezése (rendszergazdai engedélyek nélkül telepítve)**  
  **Alapértelmezett**: letiltva  

  A natív üzenetküldési gazdagépek felhasználói szintű telepítésének engedélyezése. 
  - Ha letiltja ezt a házirendet, a Microsoft Edge csak a rendszerszinten telepített natív üzenetküldési gazdagépeket fogja használni. Ha nem konfigurálja ezt a házirendet, alapértelmezés szerint a Microsoft Edge lehetővé teszi a felhasználói szintű natív üzenetküldési gazdagépek használatát.

## <a name="next-steps"></a>További lépések

[Biztonsági alaptervek használata az Intune-ban](security-baselines.md)
