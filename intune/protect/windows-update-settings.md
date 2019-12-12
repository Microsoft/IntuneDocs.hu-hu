---
title: A Windows for Business frissítési beállításai Microsoft Intune – Azure | Microsoft Docs
description: Az Intune használatával üzembe helyezhető Windows 10-es eszközök WUfB beállításai.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f3359bc5544b3a353271ea17083c8c3acb49742
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72584467"
---
# <a name="windows-update-settings-for-intune"></a>Windows Update-beállítások az Intune-hoz  

A Microsoft Intune [konfigurálható és felügyelhető](windows-update-for-business-configure.md) Windows 10-es frissítési beállítások megtekintése.  

Ha a Windows 10-es frissítési körök beállításait konfigurálja az Intune-ban, akkor a Windows Update beállításait kell konfigurálnia. Ha egy Windows Update-beállítás Windows 10-es verziótól függ, a rendszer a beállítások részletei között megjegyezi a verzió függőségét.  

## <a name="update-settings"></a>Beállítások frissítése  

A frissítési beállítások vezérlik, hogy az eszköz milyen biteket töltsön le, és mikor. Az egyes beállítások működésével kapcsolatos további információkért tekintse meg a Windows dokumentációját.  

- **Karbantartási csatorna**  
  **Alapértelmezett**: féléves csatorna  
  Windows Update CSP: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  Állítsa be azt a csatornát (ágat), amelyről az eszköz megkapja a Windows-frissítéseket. A frissítések kézbesítése előtt a különböző csatornák eltérő késleltetési időszakokat is használhatnak.  

  Például a féléves *csatorna* egy hat hónapos halasztást tartalmaz. Ha ezt a csatornát a beállítások alól további halasztás nélkül használja, az eszköz a kiadás után hat hónappal telepíti a frissítést.  

  Támogatott frissítési csatornák:  

  - Féléves csatorna  
  - Féléves csatorna (megcélozva)  
  - Windows Insider – gyors  
  - Windows Insider – lassú  
  - A Windows Insider kiadása  

  Ha egy bennfentes csatornát választ, az Intune automatikusan konfigurálja a Windows Update [/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) -beállítást, hogy a belső Build működni fog.  


  > [!IMPORTANT]  
  > A Windows 1903-es verziójától kezdődően a *féléves csatorna (megcélozt)* (SAC-T) használata megszűnik. Ezzel a módosítással a SAC-T egyesítve van a *féléves csatornával*. Ha többet szeretne megtudni erről a változásról, valamint arról, hogy miként befolyásolja a vállalati Windows Update működését, tekintse meg a Windows IT Pro blog post [Windows Update for Business és a SAC-T kivonulását](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523)ismertető témakört.  
 
- **Microsoft-termékek frissítései**  
  **Alapértelmezett**: Engedélyezés  
  Windows Update CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Engedélyezés** *– jelölje be* az alkalmazás frissítéseinek keresése Microsoft Updateról lehetőséget.  
  - **Letiltás** – a Letiltás lehetőség kiválasztásával megakadályozhatja az alkalmazások frissítéseinek vizsgálatát.  

- **Windows-illesztőprogramok**  
  **Alapértelmezett**: Engedélyezés  
  Windows Update CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Engedélyezés** – jelölje be az *Engedélyezés* Windows Update illesztőprogramok felvétele a frissítések során jelölőnégyzetet.  
  - **Letiltás** – a Letiltás beállítás megadásával megakadályozhatja az illesztőprogramok vizsgálatát.  

- **Minőségi frissítés halasztási időtartama (nap)**  
  **Alapértelmezett**: 0  
  Windows Update CSP: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Itt adhatja meg a 0 és 30 közötti napok számát, amelyek esetében a minőségi frissítések késleltetve lettek. Ez az időtartam a kiválasztott szolgáltatási csatorna részét képező halasztási időszakon kívül van. A késleltetési időszak akkor kezdődik, amikor az eszköz megkapja a házirendet.  

  A minőségi frissítések általában javítások és a meglévő Windows-funkciók javításai.  

- **Szolgáltatási frissítés halasztási időtartama (nap)**  
  **Alapértelmezett**: 0  
  Windows Update CSP: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Itt adhatja meg, hogy hány nap elteltével legyen késleltetve a szolgáltatások frissítései. Ez az időtartam a kiválasztott szolgáltatási csatorna részét képező halasztási időszakon kívül van. A késleltetési időszak akkor kezdődik, amikor az eszköz megkapja a házirendet.  

  Támogatott késleltetési idő:  

  - *Windows 1709-es és újabb* verziók – 0 – 365 nap  
  - *Windows-verzió 1703* – 0 – 180 nap  

  A funkciófrissítések általában új Windows-funkciókat tartalmaznak.  

- **Szolgáltatás frissítésének eltávolítási idejének beállítása (2 – 60 nap)**  
  **Alapértelmezett**: 10  
  Windows Update CSP: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Adja meg azt az időpontot, amely után a szolgáltatás frissítéseit nem lehet eltávolítani.  

  Az időszak lejárta után az előző frissítési bitek törlődnek az eszközről, és a továbbiakban már nem távolíthatók el egy korábbi frissítési verzióra.  

  Tegyük fel például, hogy egy frissítési gyűrű egy 20 napos szolgáltatás-frissítési eltávolítási időszakmal rendelkezik. 25 nap elteltével állítsa vissza a legújabb funkció frissítését, és használja az Eltávolítás lehetőséget.  Azok az eszközök, amelyek több mint 20 nappal ezelőtt telepítették a szolgáltatást, nem tudják eltávolítani, mert a karbantartási folyamat részeként eltávolítottak a szükséges biteket. Azonban azok az eszközök, amelyek csak a 19 napos frissítést telepítették, eltávolíthatják a frissítést, ha sikeresen bejelentkeznek az eltávolítási parancs fogadására, mielőtt meghaladják a 20 napos eltávolítási időszakot.  

## <a name="user-experience-settings"></a>Felhasználói élmény beállításai  

A felhasználói élmény beállításai vezérlik az eszköz újraindítására és emlékeztetőre vonatkozó végfelhasználói élményt. Az egyes beállítások működésével kapcsolatos további információkért tekintse meg a Windows Update CSP dokumentációját.  

- **Az automatikus frissítés viselkedése**  
  **Alapértelmezett**: automatikus telepítés karbantartási időpontban  
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Válassza ki az automatikus frissítések telepítésének módját, és ha szükséges, az eszköz újraindításának idejét.  

  Támogatott beállítások:  

  - **Értesítés letöltése** – a frissítés letöltése előtt értesítse a felhasználót. A felhasználók a frissítések letöltésére és telepítésére is lehetőséget választanak.  

  - **Automatikus telepítés karbantartási időben** – a frissítések automatikusan letöltve, majd az automatikus karbantartás során települnek, ha az eszköz nincs használatban, vagy akkumulátor-áramellátáson fut. Ha újraindításra van szükség, a rendszer legfeljebb hét napig kéri a felhasználók újraindítását, majd az újraindítás kényszerítve lesz.  

    Ez a beállítás automatikusan újraindíthatja az eszközt a frissítés telepítése után. Az **aktív órák** beállításaival határozhatja meg, hogy az automatikus újraindítások milyen időszak alatt legyenek blokkolva:  

    - **Aktív óra kezdése** – megadásával megkezdheti az újraindítások eltávolítását a frissítési telepítések miatt.  
      **Alapértelmezett**: 8  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Aktív órák vége** – Itt adhatja meg a frissítési telepítések miatti újraindítások letiltásának befejezési idejét.  
      **Alapértelmezett**: 5 PM  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Automatikus telepítés és újraindítás karbantartási időben** – a frissítések automatikusan települnek, majd az automatikus karbantartás során települnek, ha az eszköz nincs használatban, vagy akkumulátor-áramellátáson fut. Ha újraindítás szükséges, az eszköz újraindul, ha nincs használatban. (Ez az alapértelmezett a nem felügyelt eszközök esetében.)  

    Ez a beállítás automatikusan újraindíthatja az eszközt a frissítés telepítése után. Az **aktív órák** beállításainak használata nem Windows Update beállításokban van leírva, de az Intune azt használja, hogy az automatikus újraindítások letiltása közben milyen időszakot kell meghatározni:  

    - **Aktív óra kezdése** – megadásával megkezdheti az újraindítások eltávolítását a frissítési telepítések miatt.  
      **Alapértelmezett**: 8  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Aktív órák vége** – Itt adhatja meg a frissítési telepítések miatti újraindítások letiltásának befejezési idejét.  
      **Alapértelmezett**: 5 PM  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Automatikus telepítés és újraindítás ütemezett időpontban** – a telepítési nap és időpont meghatározása. Ha nincs megadva, a telepítés naponta 3 ÓRAKOR fut le, majd egy 15 perces visszaszámlálást indít el az újraindításig. A bejelentkezett alkalmazások késleltetik a visszaszámlálást és az újraindítást.   
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Ez a beállítás támogatja a további beállításokat.  

    - **Automatikus viselkedés gyakorisága** – ezzel a beállítással ütemezhetők, hogy a rendszer mikor telepítse a frissítéseket, beleértve a hetet, a napot és az időt.  
      **Alapértelmezett**: hetente

    - **Ütemezett telepítés napja** – Itt adhatja meg, hogy a hét melyik napján szeretné telepíteni a frissítéseket.  
      **Alapértelmezett**: bármely nap  

    - **Ütemezett telepítési idő** – Itt adhatja meg, hogy mikor szeretné telepíteni a frissítéseket.  
      **Alapértelmezett**: 3  

  - **Automatikus telepítés és újraindítás végfelhasználói vezérlés nélkül** – a frissítések automatikusan le lettek letöltve, majd az automatikus karbantartás során települnek, ha az eszköz nincs használatban, vagy akkumulátorról fut. Ha újraindítás szükséges, az eszköz újraindul, ha nincs használatban. Ez a beállítás a végfelhasználói vezérlő ablaktáblát a csak olvasható értékre állítja be.  

  - **Alaphelyzetbe állítás az alapértelmezett értékre** – az eredeti automatikus frissítési beállítások visszaállítása a 2018-es vagy újabb frissítést futtató Windows 10-es gépeken.  


- **Újraindítási ellenőrzések**  
  **Alapértelmezett**: Engedélyezés  
  Windows Update CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  Ha át szeretné ugrani ezeket az ellenőrzéseket az eszközök újraindításakor, válassza a **Kihagyás** lehetőséget. 
  
  Ez a beállítás a Windows rendszerű eszközök verziójától függően eltérő eredményeket tartalmaz:  
 
  - *Windows 1703-es és korábbi* verziók – az eszköz újraindításakor bizonyos ellenőrzések történnek, beleértve az aktív felhasználók, az akkumulátor szintjeinek, a játékok futtatásának és egyéb szolgáltatásoknak a ellenőrzését.  
  
  - A *Windows 1709-es és újabb* verziói – az aktív órák alatt a következő folyamatok nem futnak a frissítésekhez: vizsgálat, letöltés, telepítés és újraindítás. Az aktív órák után a frissítési folyamatok futnak, és felébresztik az eszközt az alvó állapotból, a vizsgálatból, a letöltésből, a telepítésből és az újraindításból, feltéve, hogy az akkumulátor-ellenőrzés és a Power checks pass. 

- **A Windows-frissítések szüneteltetésének tiltása a felhasználó számára**  
  **Alapértelmezett**: Engedélyezés  
  Windows Update CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Engedélyezés** – engedélyezi az eszköz felhasználóinak, hogy szüneteltetik a frissítés telepítését.  
  - **Letiltás** – megakadályozza, hogy az eszköz felhasználói szüneteltesse a frissítés telepítését.  

- **A Windows-frissítések keresésének tiltása a felhasználó számára**  
  **Alapértelmezett**: Engedélyezés  
  Windows Update CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Engedélyezés** – engedélyezi az eszköz felhasználóinak, hogy a frissítések kereséséhez és letöltéséhez Windows Update vizsgálatot használjanak, és telepítsenek szolgáltatásokat.
  - **Letiltás** – megakadályozza, hogy az eszköz felhasználói hozzáférhessenek a Windows Update vizsgálathoz, a frissítések letöltéséhez és a funkciók telepítéséhez.  

- **A felhasználó jóváhagyásának megkövetelése a munkaidőn kívüli újraindításhoz**  
  **Alapértelmezett**: nincs konfigurálva  
  Windows Update CSP: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **Nincs konfigurálva**  
  - **Kötelező** – megkövetelheti, hogy a felhasználó a munkaidőn kívül is jóváhagyja az eszköz újraindítását.  
   
- **A felhasználó emlékeztetője a szükséges automatikus újraindítás előtt a mellőzhető-emlékeztetővel (óra)**  
  **Alapértelmezett**: 4  
  Windows Update CSP: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  Itt adhatja meg, hogy az automatikus újraindítás meddig tartson előre egy mellőzhető értesítést az újraindítást kérő eszköz felhasználójának. A **2**, **4**, **8**, **12**vagy **24** óra értékek támogatottak.  
  
  Ha törli az alapértelmezett értéket, a beállítás nem lesz *konfigurálva*.  

- **A felhasználó emlékeztetője a szükséges automatikus újraindítás előtt, állandó emlékeztetővel (perc)**  
  **Alapértelmezett**: 15  
  Windows Update CSP: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Itt adhatja meg, hogy az automatikus újraindítás meddig tartson előre egy nem mellőzhető figyelmeztetést az eszköz felhasználója számára az újraindítás után. A **15**, **30** vagy **60** perces értékek támogatottak.  

  Ha törli az alapértelmezett értéket, a beállítás nem lesz *konfigurálva*.  

- **Frissítési értesítési szint módosítása**  
  **Alapértelmezett**: az alapértelmezett Windows Update értesítések használata  
  Windows Update CSP: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Határozza meg, hogy a felhasználók milyen mértékben látják a Windows Update értesítéseket. Ez a beállítás nem szabályozza a frissítések letöltésének és telepítésének módját.  

  Támogatott beállítások:
  - **Nincs konfigurálva**
  - **Az alapértelmezett Windows Update értesítések használata**
  - **Az összes értesítés kikapcsolása, kivéve az újraindítási figyelmeztetéseket**
  - **Az összes értesítés kikapcsolása, beleértve az újraindítási figyelmeztetéseket is**  

- **Használati határidő beállításai**  
  **Alapértelmezett**: nincs konfigurálva  
 
  Lehetővé teszi a felhasználó számára a határidő-beállítások használatát.  

  - **Nincs konfigurálva**
  - **Engedélyezés**

  Az *Engedélyezés*beállításnál a következő beállításokat állíthatja be a határidőkhöz:

  - **A szolgáltatások frissítéseinek határideje**  
    **Alapértelmezett**: *nincs konfigurálva*  
    Windows Update CSP: [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Azt adja meg, hogy hány nap elteltével telepítse automatikusan a rendszer a szolgáltatás frissítéseit az eszközön (2-30).

  - **Minőségi frissítések határideje**  
    **Alapértelmezett**: *nincs konfigurálva*  
    Windows Update CSP: [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Azt adja meg, hogy hány nap elteltével kell a felhasználó automatikusan telepíteni a minőségi frissítéseket az eszközökre (2-30).

  - **Türelmi időszak**  
    **Alapértelmezett**: *nincs konfigurálva* Windows Update CSP: [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Azt határozza meg, hogy a határidő lejárta után hány nap elteltével induljon el automatikusan a rendszer (2-7).

  - **Automatikus újraindítás a határidő lejárta előtt**  
    **Alapértelmezett**: igen Windows Update CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Meghatározza, hogy az eszköz automatikusan újrainduljon-e a határidő lejárta előtt.
    - **Igen**
    - **Nem**

### <a name="delivery-optimization-download-mode"></a>Kézbesítési optimalizálás letöltési módja  

A továbbítási optimalizálás már nem a Windows 10-es frissítési kör részeként van konfigurálva a szoftverfrissítések alatt. A kézbesítési optimalizálás már be van állítva az eszköz konfigurációjával. A korábbi konfigurációk azonban továbbra is elérhetők maradnak a konzolon. Ezeket a korábbi konfigurációkat úgy távolíthatja el, hogy *nem konfigurálja*őket, de másképp nem módosítható. 

Az új és a régi házirend közötti ütközések elkerülése érdekében lásd: [váltás meglévő frissítési körökből a kézbesítési optimalizálásba](../configuration/delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) , majd helyezze át a beállításokat egy kézbesítési optimalizálási profilba.
