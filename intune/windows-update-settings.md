---
title: A Windows for Business frissítési beállításai Microsoft Intune – Azure | Microsoft Docs
description: Az Intune használatával üzembe helyezhető Windows 10-es eszközök WUfB beállításai.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e9baf3593883cf2fa2402a0b4daec638a336366
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884194"
---
# <a name="windows-update-settings-for-intune"></a>Windows Update-beállítások az Intune-hoz  

A Microsoft Intune [konfigurálható és felügyelhető](windows-update-for-business-configure.md) Windows 10-es frissítési beállítások megtekintése.  

Ha a Windows 10-es frissítési körök beállításait konfigurálja az Intune-ban, akkor a Windows Update beállításait kell konfigurálnia. Ha egy Windows Update-beállítás Windows 10-es verziótól függ, a rendszer a beállítások részletei között megjegyezi a verzió függőségét.  

## <a name="update-settings"></a>Beállítások frissítése  

A frissítési beállítások vezérlik, hogy az eszköz milyen biteket töltsön le, és mikor. Az egyes beállítások működésével kapcsolatos további információkért tekintse meg a Windows dokumentációját.  

### <a name="servicing-channel"></a>Karbantartási csatorna  

- **Alapértelmezett**: Féléves csatorna (megcélozva)  
- **Windows**-referenciák dokumentációja: [Frissítés/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
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
> A Windows 1903-es verziójától kezdődően a *féléves csatorna (megcélozt)* (SAC-T) használata megszűnik. Ezzel a módosítással a SAC-T egyesítve vana féléves csatornával. Ha többet szeretne megtudni erről a változásról, valamint arról, hogy miként befolyásolja a vállalati Windows Update működését, tekintse meg a Windows IT Pro blog post [Windows Update for Business és a SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523)kivonulását ismertető témakört.
 


### <a name="microsoft-product-updates"></a>Microsoft-termékek frissítései  

- **Alapértelmezett**:  Allow
- **Windows**-referenciák dokumentációja: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Válassza az alkalmazás frissítéseinek keresése Microsoft Updateról lehetőséget.    

### <a name="windows-drivers"></a>Windows-illesztőprogramok  

- **Alapértelmezett**:  Allow
- **Windows**-referenciák dokumentációja: [Frissítés/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Válassza az *Engedélyezés lehetőséget* Windows Update illesztőprogramok felvételéhez a frissítések során

### <a name="quality-update-deferral-period-days"></a>Minőségi frissítés halasztási időtartama (nap)  

- **Alapértelmezett**: 0  
- **Windows**-referenciák dokumentációja: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Itt adhatja meg a 0 és 30 közötti napok számát, amelyek esetében a minőségi frissítések késleltetve lettek. Ez az időtartam a kiválasztott szolgáltatási csatorna részét képező halasztási időszakon kívül van. A késleltetési időszak akkor kezdődik, amikor az eszköz megkapja a házirendet.  

A minőségi frissítések általában javítások és a meglévő Windows-funkciók javításai.  

### <a name="feature-update-deferral-period-days"></a>Szolgáltatási frissítés halasztási időtartama (nap)  

- **Alapértelmezett**: 0  
- **Windows**-referenciák dokumentációja: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Itt adhatja meg, hogy hány nap elteltével legyen késleltetve a szolgáltatások frissítései. Ez az időtartam a kiválasztott szolgáltatási csatorna részét képező halasztási időszakon kívül van. A késleltetési időszak akkor kezdődik, amikor az eszköz megkapja a házirendet.  
Támogatott késleltetési idő:  

- *Windows 1709 vagy újabb verzió*: 0 – 365 nap  
- *Windows-verzió 1703*:  0 – 180 nap  

A funkciófrissítések általában új Windows-funkciókat tartalmaznak.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Szolgáltatás frissítésének eltávolítási idejének beállítása (2 – 60 nap)  

- **Alapértelmezett**: 10  
- **Windows**-referenciák dokumentációja:  [Frissítés/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Adja meg azt az időpontot, amely után a szolgáltatás frissítéseit nem lehet eltávolítani.  

Az időszak lejárta után az előző frissítési bitek törlődnek az eszközről, és a továbbiakban már nem távolíthatók el egy korábbi frissítési verzióra.  

Tegyük fel például, hogy egy frissítési gyűrű egy 20 napos szolgáltatás-frissítési eltávolítási időszakmal rendelkezik. 25 nap elteltével állítsa vissza a legújabb funkció frissítését, és használja az Eltávolítás lehetőséget.  Azok az eszközök, amelyek több mint 20 nappal ezelőtt telepítették a szolgáltatást, nem tudják eltávolítani, mert a karbantartási folyamat részeként eltávolítottak a szükséges biteket. Azonban azok az eszközök, amelyek csak a 19 napos frissítést telepítették, eltávolíthatják a frissítést, ha sikeresen bejelentkeznek az eltávolítási parancs fogadására, mielőtt meghaladják a 20 napos eltávolítási időszakot.  


## <a name="user-experience-settings"></a>Felhasználói élmény beállításai  

A felhasználói élmény beállításai vezérlik az eszköz újraindítására és emlékeztetőre vonatkozó végfelhasználói élményt. Az egyes beállítások működésével kapcsolatos további információkért tekintse meg a Windows dokumentációját.  

### <a name="automatic-update-behavior"></a>Automatikus frissítési viselkedés  

- **Alapértelmezett**: Automatikus telepítés és újraindítás ütemezett időpontban  
- **Windows**-referenciák dokumentációja: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Válassza ki az automatikus frissítések telepítését, és ha szükséges, az eszköz újraindításának módját.  

A következő támogatott lehetőségek teljes nyilvánosságra hozataláról a Windows dokumentációjában tájékozódhat:  

- **Értesítés letöltése** – a frissítés letöltése előtt értesítse a felhasználót. A felhasználók a frissítések letöltésére és telepítésére is lehetőséget választanak.  

- **Automatikus telepítés karbantartási időpontban** – a frissítések letöltése automatikusan megtörténik, majd az automatikus karbantartás során települ, amikor az eszköz nincs használatban, vagy akkumulátor-áramellátáson fut. Ha újraindításra van szükség, a rendszer legfeljebb hét napig kéri a felhasználók újraindítását, majd az újraindítás kényszerítve lesz.  

  Ez a beállítás automatikusan újraindíthatja az eszközt a frissítés telepítése után. Az **aktív órák** beállításaival határozhatja meg, hogy az automatikus újraindítások milyen időszak alatt legyenek blokkolva:  

  - **Aktív órák kezdete**: A frissítési telepítések miatti újraindítások letiltásának kezdési idejét határozza meg.  
    **Windows**-referenciák dokumentációja:  [Frissítés/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Alapértelmezett**: 8  
  
  - **Aktív órák vége**: A frissítési telepítések miatt letiltott újraindítások letiltásának befejezési időpontja.  
    **Windows**-referenciák dokumentációja:  [Frissítés/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Alapértelmezett**: 5 ÓRA  

- **Automatikus telepítés és újraindítás karbantartási időben** – a frissítések automatikusan települnek, majd az automatikus karbantartás során települnek, ha az eszköz nincs használatban, vagy akkumulátor-áramellátáson fut. Ha újraindítás szükséges, az eszköz újraindul, ha nincs használatban. (Ez az alapértelmezett a nem felügyelt eszközök esetében.)  

  Ez a beállítás automatikusan újraindíthatja az eszközt a frissítés telepítése után. Az **aktív órák** beállításainak használata nem Windows Update beállításokban van leírva, de az Intune azt használja, hogy az automatikus újraindítások letiltása közben milyen időszakot kell meghatározni:  

  - **Aktív órák kezdete**: A frissítési telepítések miatti újraindítások letiltásának kezdési idejét határozza meg.  
    **Windows**-referenciák dokumentációja:  [Frissítés/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Alapértelmezett**: 8  

  - **Aktív órák vége**: A frissítési telepítések miatt letiltott újraindítások letiltásának befejezési időpontja.  
    **Windows**-referenciák dokumentációja:  [Frissítés/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Alapértelmezett**: 5 ÓRA  

- **Automatikus telepítés és újraindítás ütemezett időpontban** – a telepítési nap és időpont meghatározása. Ha nincs megadva, a telepítés naponta 3 ÓRAKOR fut le, majd egy 15 perces visszaszámlálást indít el az újraindításig. A bejelentkezett alkalmazások késleltetik a visszaszámlálást és az újraindítást.  
  
  Ez a beállítás támogatja a további beállításokat.  
  **Windows**-referenciák dokumentációja:  [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Automatikus viselkedés gyakorisága**: Ezzel a beállítással ütemezheti a frissítésék telepítését, amelyet hét, nap és időpont szerint adhat meg.  
    **Alapértelmezett**: Hetente

  - **Ütemezett telepítés napja**:  Itt adhatja meg, hogy a hét melyik napján szeretné telepíteni a frissítéseket.  
    **Alapértelmezett**: Bármely nap  

  - **Ütemezett telepítés időpontja**:  Itt adhatja meg azt a napszakot, amikor a frissítéseket telepíteni szeretné.  
    **Alapértelmezett**: 3 –  

- **Automatikus telepítés és újraindítás végfelhasználói vezérlés nélkül** – a frissítések letöltése automatikusan megtörténik, majd az automatikus karbantartás során települ, amikor az eszköz nincs használatban, vagy akkumulátorról fut. Ha újraindítás szükséges, az eszköz újraindul, ha nincs használatban. Ez a beállítás a végfelhasználói vezérlő ablaktáblát a csak olvasható értékre állítja be.  

- **Alaphelyzetbe állítás az alapértelmezett értékre** – az eredeti automatikus frissítési beállítások visszaállítása a 2018-es vagy újabb frissítést futtató Windows 10-es gépeken.  


### <a name="restart-checks"></a>Újraindítási ellenőrzések  

- **Alapértelmezett**: Allow  
- **Windows**-referenciák dokumentációja: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

Ez a beállítás a Windows rendszerű eszközök verziójától függően eltérő eredményeket tartalmaz:  

- Windows 1703-es és korábbi verziók: Egy eszköz újraindításakor a rendszer bizonyos ellenőrzéseket végez, például ellenőrzi az aktív felhasználókat, az akkumulátor szintjét, a futó játékokat és más szempontokat. Ha át szeretné ugrani ezeket az ellenőrzéseket az eszközök újraindításakor, válassza a **Kihagyás** lehetőséget.  
- A Windows 1709-es verziójától kezdve: Az aktív órákban a következő folyamatok nem futnak a frissítésekhez: vizsgálat, letöltés, telepítés és újraindítás. Az aktív órák után a frissítési folyamatok futnak, és felébresztik az eszközt az alvó állapotból, a vizsgálatból, a letöltésből, a telepítésből és az újraindításból, feltéve, hogy az akkumulátor-ellenőrzés és a Power checks pass. További információ: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>A Windows-frissítések szüneteltetésének tiltása a felhasználó számára  

- **Alapértelmezett**: Allow  
- **Windows**-referenciák dokumentációja: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Egy adott frissítés telepítésének felfüggesztését engedélyező vagy blokkoló eszköz felhasználója. 

### <a name="block-user-from-scanning-for-windows-updates"></a>A Windows-frissítések keresésének tiltása a felhasználó számára  
- **Alapértelmezett**: Allow
- **Windows**-referenciák dokumentációja: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

Megadja, hogy engedélyezi vagy letiltja a felhasználó hozzáférését a vizsgálat Windows Update. Ha például egy blokkot konfigurál,a felhasználók nem férhetnek hozzá a Windows Update Scan, download és install funkciókhoz.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>A felhasználó jóváhagyásának megkövetelése a munkaidőn kívüli újraindításhoz  

- **Alapértelmezett**: Nincs konfigurálva  
- **Windows**-referenciák dokumentációja: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
A *kötelező* beállítás megadásával megkövetelheti, hogy a felhasználó a munkaidőn kívül is jóváhagyja az eszköz újraindítását.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>A felhasználó emlékeztetője a szükséges automatikus újraindítás előtt a mellőzhető-emlékeztetővel (óra)  

- **Alapértelmezett**: *Ez a beállítás alapértelmezés szerint nincs konfigurálva, és nem jelenik meg emlékeztető a felhasználók számára*.  
- **Windows**-referenciák dokumentációja: [Frissítés/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Itt adhatja meg, hogy az automatikus újraindítás meddig tartson előre egy mellőzhető értesítést az újraindítást kérő eszköz felhasználójának. A **2**, **4**, **8**, **12**vagy **24** óra értékek támogatottak.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>A felhasználó emlékeztetője a szükséges automatikus újraindítás előtt, állandó emlékeztetővel (perc)  

- **Alapértelmezett**: *Ez a beállítás alapértelmezés szerint nincs konfigurálva, és nem jelenik meg emlékeztető a felhasználók számára*.  
- **Windows**-referenciák dokumentációja: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Itt adhatja meg, hogy az automatikus újraindítás meddig tartson előre egy nem mellőzhető figyelmeztetést az eszköz felhasználója számára az újraindítás után. A **15**, **30** vagy **60** perces értékek támogatottak.  

### <a name="windows-update-notification-level"></a>Értesítési szint Windows Update  
- **Alapértelmezett**: Az alapértelmezett Windows Update értesítések használata 
- **Windows**-referenciák dokumentációja: [Frissítés/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)

Határozza meg, hogy a felhasználók milyen mértékben látják a Windows Update értesítéseket. Ez a beállítás nem szabályozza a frissítések letöltésének és telepítésének módját.

### <a name="allow-user-to-restart-engaged-restart"></a>A felhasználó újraindításának engedélyezése (lefolytatott újraindítás)  

- **Alapértelmezett**: Nincs konfigurálva  
- **Windows**-referenciák dokumentációja: *Nem alkalmazható*  
- **Windows-verzió**: Támogatott a Windows 10 1803-es és újabb verzióiban  

  > [!NOTE]  
  > A Windows 10 1809-es verziója további lefolytatott újraindítási beállításokat tartalmaz, amelyek lehetővé teszik, hogy a funkciók és a minőségi frissítések külön beállításokat alkalmazzanak. Az Intune által felügyelt beállítások azonban nem vonatkoznak külön a különböző frissítési típusokra. Ehelyett az Intune ugyanazokat az értékeket alkalmazza a szolgáltatás és a minőségi frissítések esetében is.  

A **kötelező**beállítás megadása esetén engedélyezheti a Windows 10 frissítéseinek kapcsolódó újraindítási lehetőségeinek használatát. Ezekkel a lehetőségekkel az eszköz felhasználója felügyelheti az eszközt, ha olyan frissítést telepít, amely újraindítást igényel.  

A beállítással kapcsolatos további információkért tekintse [Elindult újraindítás](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) meg a Windows 10-es dokumentációjában a frissítések központi telepítésével foglalkozó témakört.  

A következő beállításokkal szabályozhatja, hogy mikor történjen a művelet újraindítása.  

- **A felhasználók automatikus újraindítás utáni újraindítása (nap)**  
  - **Alapértelmezett**:  Alapértelmezés szerint ez a beállítás nincs konfigurálva, de **2** és **30**közötti értéket is támogat.  
  - **Windows**-referenciák dokumentációja: [Frissítés/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Adja meg, hogy mennyi ideig legyenek a frissítés telepítése, amíg az eszköz be nem írja a felvállalt újraindítási viselkedést. A beállított napok száma után a felhasználók az eszköz újraindítására vonatkozó kérést kapnak.  

- **Késleltetett újraindítási emlékeztető (nap)**  
  - **Alapértelmezett**:  Alapértelmezés szerint ez a beállítás nincs konfigurálva, de **1** és **3**közötti értéket támogat.  
  - **Windows**-referenciák dokumentációja: [Frissítés/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Itt adhatja meg, hogy az újraindítási kérések mennyi ideig legyenek késleltetve.  A késleltetési idő után a rendszer újra felajánlja az újraindítási kérést. A felhasználó továbbra is késleltetheti az emlékeztetőt, amíg el nem éri a telepítési határidőt.  

- **Függőben lévő újraindítások határidejének megadása (nap)**  
  - **Alapértelmezett**:  Alapértelmezés szerint ez a beállítás nincs konfigurálva, de támogatja a **2** és **30**közötti értéket.  
  - **Windows**-referenciák dokumentációja: [Frissítés/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Itt adhatja meg, hogy legfeljebb hány nap elteltével induljon el a megkezdett újraindítási viselkedés, mielőtt az eszköz kényszeríti a szükséges újraindítást. Ez az újraindítás arra kéri a felhasználókat, hogy mentse a munkájukat.

### <a name="delivery-optimization-download-mode"></a>Kézbesítési optimalizálás letöltési módja  

A továbbítási optimalizálás már nem a Windows 10-es frissítési kör részeként van konfigurálva a szoftverfrissítések alatt. A kézbesítési optimalizálás már be van állítva az eszköz konfigurációjával. A korábbi konfigurációk azonban továbbra is elérhetők maradnak a konzolon. Ezeket a korábbi konfigurációkat úgy távolíthatja el, hogy *nem konfigurálja*őket, de másképp nem módosítható. 

Az új és a régi házirend közötti ütközések elkerülése érdekében lásd: [váltás meglévő frissítési](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) körökből a kézbesítési optimalizálásba, majd helyezze át a beállításokat egy kézbesítési optimalizálási profilba.
