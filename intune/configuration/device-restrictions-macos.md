---
title: macOS-eszközbeállítások a Microsoft Intuneban – Azure | Microsoft Docs
titleSuffix: ''
description: Beállítások hozzáadása, konfigurálása vagy létrehozása macOS-eszközökön a szolgáltatások korlátozása érdekében, beleértve a jelszó megadását, a zárolt képernyő vezérlését, a beépített alkalmazások használatát, a korlátozott vagy jóváhagyott alkalmazások hozzáadását, a Bluetooth-eszközök kezelését, a felhőhöz való kapcsolódást a biztonsági mentéshez és tárterület, a teljes képernyős mód engedélyezése, tartományok hozzáadása és annak szabályozása, hogy a felhasználók hogyan használják a Safari böngészőt Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b2efdc04414d29fc1d8d200525cb3a4a880ec01
ms.sourcegitcommit: e9cf372711ff186ed468b01a9204631a139bd8e5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776895"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS eszközbeállítások az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk a macOS-eszközökön szabályozható különböző beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, beállíthatja a jelszavas szabályokat, engedélyezheti vagy korlátozhatja az egyes alkalmazásokat, és így tovább.

Ezek a beállítások hozzáadódnak az Intune-ban lévő eszköz konfigurációs profiljához, majd a macOS-eszközökhöz vannak rendelve vagy telepítve.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz-korlátozási konfigurációs profilt](../device-restrictions-configure.md).

> [!NOTE]
> Ezek a beállítások a különböző regisztrációs típusokra vonatkoznak. A különböző regisztrációs típusokkal kapcsolatos további információkért lásd: [MacOS-regisztráció](../macos-enroll.md).

## <a name="general"></a>Általános

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése és automatikus eszközök beléptetése

- **Definíciók keresése**: a **blokk** megakadályozza, hogy a felhasználó kiemelje a szót, majd megkeresse a definícióját az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hozzáférését a definíciós keresési szolgáltatáshoz.
- **Diktálás**: a **Letiltás** megakadályozza, hogy a felhasználó hangbevitelt használjon szöveg megadásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a diktálási bevitel használatát.
- **Tartalom gyorsítótárazása**: válassza a **nincs konfigurálva** (alapértelmezett) lehetőséget a tartalom gyorsítótárazásának engedélyezéséhez. A tartalom-gyorsítótárazás az alkalmazásadatok, a webböngésző-adatokat, a letöltéseket és a helyileg tárolt adatokat az eszközön tárolja. A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy az adatok a gyorsítótárban legyenek tárolva.

  A macOS-tartalom gyorsítótárazásával kapcsolatos további információkért lásd: a [tartalom gyorsítótárazásának kezelése Mac gépen](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (egy másik webhely megnyitása).

  Ez a funkció az alábbiakra vonatkozik:  
  - macOS 10,13 és újabb verziók

- **Szoftverfrissítések késleltetése**: Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a szoftverfrissítések az eszközön jelennek meg, ahogy az Apple felszabadítja őket. Ha például egy macOS-frissítést az Apple adott időpontban szabadít fel, akkor ez a frissítés természetesen az eszközön jelenik meg a kiadási dátum körül. A magok létrehozási frissítései késedelem nélkül engedélyezettek.

  Az **Engedélyezés** beállítás megadásával késleltetheti, hogy a szoftverfrissítések mikor jelenjenek meg az eszközökön, 0-90 nap múlva. Ez a beállítás nem szabályozza, hogy a frissítések Mikor vagy nincsenek telepítve. 

  - **Szoftverfrissítések láthatóságának késleltetése**: adjon meg egy 0-90 napos értéket. Ha a késleltetés lejár, a felhasználók értesítést kapnak, hogy az operációs rendszer legkorábbi verziójára frissítsen a késleltetés elindításakor.

    Ha például egy macOS-es frissítés **január 1-jén**érhető el, és a **láthatóság késleltetése** **5 nap**, akkor a frissítés nem jelenik meg elérhető frissítésként. A kiadást követő **hatodik napon** a frissítés elérhető lesz, és a végfelhasználók is telepíthetik azt.

    Ez a funkció az alábbiakra vonatkozik:  
    - macOS 10.13.4 és újabb verziók

- **Képernyőképek**: az eszközt regisztrálni kell az Apple automatikus eszközök regisztrációjában (DEP). Ha a **blokkolás**értékre van állítva, a felhasználók nem menthetnek egy képernyőképet a kijelzőről. Emellett megakadályozza, hogy az osztályterem alkalmazás megfigyelje a távoli képernyőket. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a képernyőképek rögzítését, és lehetővé teszi, hogy az osztályterem alkalmazás megtekintse a távoli képernyőket.

### <a name="settings-apply-to-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése

- A **távoli képernyő megfigyelése az osztályterem alkalmazáson keresztül**: a **Letiltás** megakadályozza, hogy a tanárok az osztályterem alkalmazás használatával lássák a tanulók képernyőjét. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a tanárok számára, hogy megtekintsék a tanulók képernyőjét.

  Ha ezt a beállítást szeretné használni, állítsa be a **képernyőképek** beállítást úgy, hogy **ne legyen konfigurálva** (a képernyőképek engedélyezve vannak).

- Nem megjelenő **képernyő-megfigyelés az osztályterem alkalmazásban**: **lehetővé** teszi, hogy a tanárok a tanulók számára is megállapodjanak a diákok képernyőjén **Nincs konfigurálva** (alapértelmezett) a tanulónak meg kell egyeznie ahhoz, hogy a tanár láthassa a képernyőket.

  Ha ezt a beállítást szeretné használni, állítsa be a **képernyőképek** beállítást úgy, hogy **ne legyen konfigurálva** (a képernyőképek engedélyezve vannak).

- A **tanulóknak engedélyt kell kérniük a tantermi osztály elhagyására**: a nem felügyelt tantermi tanfolyamot **igénylő** tanulók számára a tanfolyam elhagyása érdekében be kell szereznie a tanárok jóváhagyását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a tanulók számára, hogy minden alkalommal elhagyják a tanfolyamot, amikor a tanuló választ.

- **A tanárok automatikusan zárolják az eszközöket és az alkalmazásokat az osztályterem alkalmazásban**: lehetővé teszi, **hogy** a tanárok a tanulók jóváhagyása nélkül zárolják a tanuló eszközét vagy alkalmazását. **Nincs konfigurálva** (alapértelmezett) a tanulónak meg kell egyeznie ahhoz, hogy a tanár zárolni tudja az eszközt vagy alkalmazást.

- A **tanulók automatikusan csatlakozhatnak az osztályterem osztályhoz**: lehetővé teszi, **hogy** a tanulók a tanár megkérdezése nélkül csatlakozzanak egy osztályhoz. **Nincs konfigurálva** (alapértelmezés) a tanári jóváhagyást igényel egy osztályhoz való csatlakozáshoz.

## <a name="password"></a>Jelszó

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése és automatikus eszközök beléptetése

- **Password (jelszó**): **megköveteli** a végfelhasználótól, hogy jelszót adjon meg az eszköz eléréséhez. **Nincs konfigurálva** (az alapértelmezett) nem igényel jelszót. Emellett nem kényszerít semmilyen korlátozást, mint például az egyszerű jelszavak blokkolása vagy a minimális hossz beállítása.
  - **Kötelező jelszó típusa**: adja meg, hogy a jelszó csak numerikus lehet-e, vagy alfanumerikusnak kell lennie (betűket és számokat is tartalmaznia kell).

    Ez a funkció az alábbiakra vonatkozik:  
    - macOS 10.10.3 és újabb verziók

  - **Nem alfanumerikus karakterek száma a jelszóban**: Itt adhatja meg, hogy hány összetett karakter szükséges a jelszóban (**0** – **4**).<br>A speciális karakterek olyan szimbólumok, mint például a „ **?** ”.
  - **Jelszó minimális hossza**: Itt adhatja meg a felhasználó által konfigurálandó jelszó minimális hosszát ( **4** és **16** karakter között).
  - **Egyszerű jelszavak**: az egyszerű jelszavak (például a **0000** vagy a **1234**) használatának engedélyezése.
  - Jelszó kérése a **Képernyő zárolása után legfeljebb perccel**: azt határozza meg, hogy mennyi ideig kell a számítógépnek inaktívnak lennie, mielőtt jelszó szükséges a zárolás feloldásához.
  - Ennyi **perc inaktivitás**után: megadhatja, hogy a számítógépnek mennyi ideig kell tétlennek lennie a képernyő zárolása előtt.
  - **Jelszó érvényessége (nap)** : Itt adhatja meg, hogy hány nap elteltével kell módosítani a felhasználónak a jelszót (**1** – **255** nap).
  - **Korábbi jelszavak újbóli használatának tiltása**: Itt adhatja meg, hogy a korábban használt jelszavak száma **1** és **24**között legyen.

- A **PIN-kód módosításának tiltása a felhasználó**számára: válassza a **Letiltás** lehetőséget a PIN-kód módosításának, hozzáadásának vagy eltávolításának leállításához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a PIN-kódok hozzáadását, módosítását vagy eltávolítását.
- **Ujjlenyomat zárolásának feloldása**: válassza a **Letiltás** lehetőséget, hogy ne használjon ujjlenyomatot az eszköz zárolásának feloldásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára az eszköz zárolásának feloldását ujjlenyomat használatával.

- **Jelszó automatikus**kitöltésének tiltása: a **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a MacOS-en az automatikus kitöltés jelszavai A **blokk** kiválasztása a következő hatással is van:

  - A felhasználók nem kérik a mentett jelszavak használatát a Safariban vagy bármely alkalmazásban.
  - Az automatikus erős jelszavak le vannak tiltva, és az erős jelszavakat nem javasoljuk a felhasználók számára.

  **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a funkciókat.

- **Jelszó-közelségi kérelmek letiltása**: válassza a **Letiltás** lehetőséget, hogy a felhasználó eszköze ne kérjen jelszavakat a közeli eszközökről. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a jelszavakat.

- **Jelszó-megosztás letiltása**: a **blokk** megakadályozza a jelszavak megosztását az eszközök között a AirDrop használatával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszavak megosztását.

## <a name="built-in-apps"></a>Beépített alkalmazások

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése és automatikus eszközök beléptetése

- **Safari automatikus**kitöltésének letiltása: a **Letiltás** letiltja az eszközön található Safari automatikus kitöltés szolgáltatását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a webböngésző automatikus kiegészítési beállításainak módosítását.
- **Kamera letiltása**: válassza a **Letiltás** lehetőséget az eszközön található kamerához való hozzáférés megakadályozása érdekében. **Nincs konfigurálva** (alapértelmezés) engedélyezi az eszköz kamerájának elérését.
- **Apple Music letiltása**: a **blokk** a Music alkalmazást klasszikus módra vált, és letiltja a Music szolgáltatást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Apple Music alkalmazás használatát.
- **Reflektorfény internetes keresési eredményeinek letiltása**: a **blokk** leállítja a reflektorfényből az internetes keresésből származó találatok visszaadását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Spotlight-keresés kapcsolódását az internethez a keresési eredmények biztosítása érdekében.
- **Fájlátvitel letiltása az iTunes használatával: a** **Letiltás** letiltja az alkalmazás fájlmegosztó szolgáltatásait. **Nincs konfigurálva** (alapértelmezés) engedélyezi az Application file Sharing Services szolgáltatást.

  Ez a funkció az alábbiakra vonatkozik:  
  - macOS 10,13 és újabb verziók

## <a name="restricted-apps"></a>Korlátozott alkalmazások

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése és automatikus eszközök beléptetése

- **A korlátozott alkalmazások listájának típusa**: hozza létre azon alkalmazások listáját, amelyeket a felhasználók nem telepíthetnek és nem használhatnak. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): nincsenek korlátozások az Intune-ban. A felhasználók hozzáférhetnek a hozzárendelt alkalmazásokhoz és a beépített alkalmazásokhoz.
  - **Tiltott alkalmazások**: az Intune által nem felügyelt alkalmazások, amelyeket nem kíván telepíteni az eszközre. A felhasználók nem akadályozzák meg a tiltott alkalmazások telepítését. Ha azonban a felhasználó a listából telepít egy alkalmazást, az az Intune-ban szerepel.
  - **Jóváhagyott alkalmazások**: azok az alkalmazások, amelyeket a felhasználók telepíthetnek. A felhasználók nem telepíthetnek olyan alkalmazásokat, amelyek nem szerepelnek a felsorolásban. Az Intune által kezelt alkalmazások automatikusan engedélyezettek. A felhasználók nem akadályozzák meg a jóváhagyott listán nem szereplő alkalmazások telepítését. De ha igen, az Intune-ban jelentett jelentés.
- Alkalmazáscsomag- **azonosító**: adja meg a kívánt alkalmazás ALKALMAZÁSCSOMAG- [azonosítóját](bundle-ids-built-in-ios-apps.md) . Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Alkalmazás neve**: adja meg a kívánt alkalmazás nevét. Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Kiadó**: adja meg a kívánt alkalmazás közzétevőjét.

Ha alkalmazásokat szeretne hozzáadni a listához, a következőket teheti:

- **Hozzáadás**: válassza a lehetőséget az alkalmazások listájának létrehozásához.
- **Importáljon** egy CSV-fájlt az alkalmazás részleteivel, beleértve az URL-címet is. Használja a következő formátumot: `<app bundle ID>, <app name>, <app publisher>`. Vagy az **Exportálás** gombra kattintva hozza létre a hozzáadott alkalmazások listáját ugyanabban a formátumban.

## <a name="connected-devices"></a>Csatlakoztatott eszközök

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése és automatikus eszközök beléptetése

- **AirDrop letiltása**: a **blokk** megakadályozza a AirDrop használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirDrop funkció használatát a tartalmak a közeli eszközökkel való cseréjéhez.
- Az **Apple Watch automatikus feloldásának letiltása**: a **blokk** megakadályozza, hogy a felhasználók a MacOS-eszközeik zárolását az Apple Watch szolgáltatással oldják fel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy a MacOS-eszközét az Apple Watch használatával oldják fel.

## <a name="cloud-and-storage"></a>Felhő és tárolás

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése és automatikus eszközök beléptetése

- **ICloud-kulcstartó szinkronizálásának**letiltása: válassza a **Letiltás** lehetőséget a kulcstartóban tárolt hitelesítő adatok icloudba való szinkronizálásának letiltásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy szinkronizálják ezeket a hitelesítő adatokat.
- **ICloud-dokumentumok szinkronizálásának letiltása**: a **Letiltás** megakadályozza az iCloud számára a dokumentumok és adatok szinkronizálását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a dokumentumok és a kulcs-érték szinkronizálását az iCloud tárhelyére.
- **ICloud levelek biztonsági mentésének letiltása**: a **blokk** megakadályozza, hogy az iCloud szinkronizálja a MacOS-es levelező alkalmazást. **Nincs konfigurálva** (alapértelmezés) engedélyezi a levelezés szinkronizálását az icloudba.
- **ICloud-kapcsolattartó biztonsági mentésének letiltása**: a **blokk** megakadályozza, hogy az iCloud szinkronizálja az eszközök névjegyeit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a kapcsolattartást az iCloud használatával.
- **ICloud naptár biztonsági mentésének letiltása**: a **blokk** megakadályozza, hogy az iCloud szinkronizáljon a MacOS Calendar alkalmazásba. **Nincs konfigurálva** (alapértelmezés) engedélyezi a naptár szinkronizálását az icloudba.
- **ICloud-emlékeztető biztonsági mentésének letiltása**: a **blokk** megakadályozza, hogy az iCloud szinkronizáljon a MacOS-emlékeztetők alkalmazásba. **Nincs konfigurálva** (alapértelmezés) engedélyezi az emlékeztetők szinkronizálását az icloudba.
- **ICloud könyvjelző biztonsági mentésének letiltása**: a **blokk** megakadályozza, hogy az iCloud szinkronizálja az eszközök könyvjelzőit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a könyvjelzők szinkronizálását az icloudba.
- **ICloud-jegyzetek biztonsági mentésének letiltása**: a **blokk** megakadályozza, hogy az iCloud szinkronizálja az eszközök megjegyzéseit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jegyzetek szinkronizálását az icloudba.
- Az **iCloud Photo Library**letiltása: a **blokk** letiltja az iCloud fényképgyűjteményt, és megakadályozza, hogy az iCloud szinkronizálja az eszközök fényképeit. Az iCloud fényképgyűjteményből nem teljes mértékben letöltött fényképek el lesznek távolítva az eszköz helyi tárolójából. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi fényképek szinkronizálását az eszköz és az ICloud Photo Library között.
- **Handoff**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy megkezdjék a munkát egy MacOS-eszközön, majd folytassa az elindított munkát egy másik iOS-vagy MacOS-eszközön. A **Letiltás** megakadályozza a handoff funkciót az eszközön. 

  Ez a funkció az alábbiakra vonatkozik:  
  - macOS 10,15 és újabb verziók

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése és automatikus eszközök beléptetése

- **E-mail-tartomány URL-címe**: **adjon hozzá** egy vagy több URL-címet a listához. Ha a felhasználók a konfigurálttól eltérő tartományból kapnak e-mailt, az e-mail-cím nem megbízhatóként van megjelölve a macOS posta alkalmazásban.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](../device-profile-monitor.md).

Az eszköz funkcióit és beállításait [iOS](../device-restrictions-ios.md) -eszközökön is korlátozhatja.
