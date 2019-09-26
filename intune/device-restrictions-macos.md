---
title: macOS-eszközbeállítások a Microsoft Intuneban – Azure | Microsoft Docs
titleSuffix: ''
description: Beállítások hozzáadása, konfigurálása vagy létrehozása macOS-eszközökön a szolgáltatások korlátozása érdekében, beleértve a jelszó megadását, a zárolt képernyő vezérlését, a beépített alkalmazások használatát, a korlátozott vagy jóváhagyott alkalmazások hozzáadását, a Bluetooth-eszközök kezelését, a felhőhöz való kapcsolódást a biztonsági mentéshez és tárterület, a teljes képernyős mód engedélyezése, tartományok hozzáadása és annak szabályozása, hogy a felhasználók hogyan használják a Safari böngészőt Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d32224581c16325f0b060608409aa422cbf49d90
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71302360"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS eszközbeállítások az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk a macOS-eszközökön szabályozható különböző beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, beállíthatja a jelszavas szabályokat, engedélyezheti vagy korlátozhatja az egyes alkalmazásokat, és így tovább.

Ezek a beállítások hozzáadódnak az Intune-ban lévő eszköz konfigurációs profiljához, majd a macOS-eszközökhöz vannak rendelve vagy telepítve.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz-korlátozási konfigurációs profilt](device-restrictions-configure.md).

> [!NOTE]
> Ezek a beállítások a különböző regisztrációs típusokra vonatkoznak. A különböző regisztrációs típusokkal kapcsolatos további információkért lásd: [MacOS-regisztráció](macos-enroll.md).

## <a name="general"></a>Általános

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **Definíciók keresése**: A **Letiltás** megakadályozza, hogy a felhasználó kiemelje a szót, majd megkeresse a definícióját az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hozzáférést a definíciós keresési szolgáltatáshoz.
- **Diktálás**: A **Letiltás** leállítja a felhasználótól a hangbemenet használatát szöveg megadásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a diktálási bevitel használatát.
- **Tartalom gyorsítótárazása**: Válassza a **nincs konfigurálva** (alapértelmezett) lehetőséget a tartalom gyorsítótárazásának engedélyezéséhez. A tartalom-gyorsítótárazás az alkalmazásadatok, a webböngésző-adatokat, a letöltéseket és a helyileg tárolt adatokat az eszközön tárolja. A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy az adatok a gyorsítótárban legyenek tárolva.

  A macOS-tartalom gyorsítótárazásával kapcsolatos további információkért lásd: a [tartalom gyorsítótárazásának kezelése Mac gépen](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (egy másik webhely megnyitása).

  Ez a funkció az alábbiakra vonatkozik:  
  - macOS 10,13 és újabb verziók

- **Szoftverfrissítések késleltetése**: Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a szoftverfrissítések az eszközön jelennek meg, ahogy az Apple kiadják őket. Ha például egy macOS-frissítést az Apple adott időpontban szabadít fel, akkor ez a frissítés természetesen az eszközön jelenik meg a kiadási dátum körül. A magok létrehozási frissítései késedelem nélkül engedélyezettek.

  Az **Engedélyezés** beállítás megadásával késleltetheti, hogy a szoftverfrissítések mikor jelenjenek meg az eszközökön, 0-90 nap múlva. Ez a beállítás nem szabályozza, hogy a frissítések Mikor vagy nincsenek telepítve. 

  - **Szoftverfrissítések láthatóságának késleltetése**: 0-90 napos értéket adjon meg. Ha a késleltetés lejár, a felhasználók értesítést kapnak, hogy az operációs rendszer legkorábbi verziójára frissítsen a késleltetés elindításakor.

    Ha például egy macOS-es frissítés **január 1-jén**érhető el, és a **láthatóság késleltetése** **5 nap**, akkor a frissítés nem jelenik meg elérhető frissítésként. A kiadást követő **hatodik napon** a frissítés elérhető lesz, és a végfelhasználók is telepíthetik azt.

    Ez a funkció az alábbiakra vonatkozik:  
    - macOS 10.13.4 és újabb verziók

- **Képernyőképek**: Az eszközt regisztrálni kell az Apple automatikus eszköz-regisztrációjában (DEP). Ha a **blokkolás**értékre van állítva, a felhasználók nem menthetnek egy képernyőképet a kijelzőről. Emellett megakadályozza, hogy az osztályterem alkalmazás megfigyelje a távoli képernyőket. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a képernyőképek rögzítését, és lehetővé teszi, hogy az osztályterem alkalmazás megtekintse a távoli képernyőket.

### <a name="settings-apply-to-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése

- **A távoli képernyő megfigyelése az osztályterem alkalmazáson keresztül**: A **Letiltás** beállítás megadásával megakadályozhatja, hogy a tanárok az osztályterem alkalmazás használatával lássák a tanulók képernyőjét. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a tanárok számára, hogy megtekintsék a tanulók képernyőjét.

  Ha ezt a beállítást szeretné használni, állítsa be a **képernyőképek** beállítást úgy, hogy **ne legyen konfigurálva** (a képernyőképek engedélyezve vannak).

- Nem megjelenő **képernyő-megfigyelés az osztályterem alkalmazásban**: Az **Engedélyezés** lehetővé teszi a tanárok számára, hogy a tanulók számára ne kelljen elfogadniuk a tanulók képernyőjét. **Nincs konfigurálva** (alapértelmezés szerint) a tanulónak meg kell egyeznie ahhoz, hogy a tanár láthassa a képernyőket.

  Ha ezt a beállítást szeretné használni, állítsa be a **képernyőképek** beállítást úgy, hogy **ne legyen konfigurálva** (a képernyőképek engedélyezve vannak).

- **A tanulóknak engedélyt kell kérniük az osztályterem osztály elhagyására**: **Megkövetelheti** , hogy a tanulók a tanfolyam elhagyása érdekében egy nem felügyelt osztályteremben regisztrálják a tanári jóváhagyást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a tanulók számára, hogy a tanuló által választott időben elhagyják a tanfolyamot.

- **A tanárok automatikusan le tudják zárni az eszközöket és az alkalmazásokat az osztályterem alkalmazásban**: **Lehetővé** teszi, hogy a tanárok a tanulók jóváhagyása nélkül zárolják a tanuló eszközét vagy alkalmazását. **Nincs konfigurálva** (alapértelmezés szerint) a tanulónak meg kell egyeznie ahhoz, hogy a tanár zárolni tudja az eszközt vagy alkalmazást.

- A **tanulók automatikusan csatlakozhatnak az osztályterem osztályhoz**: **Lehetővé** teszi, hogy a tanulók a tanár megkérdezése nélkül csatlakozzanak egy osztályhoz. **Nincs konfigurálva** (alapértelmezés) a tanárok jóváhagyását igényli egy osztályhoz való csatlakozáshoz.

## <a name="password"></a>Windows 10

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **Jelszó**: **Kérje** meg a végfelhasználót, hogy adjon meg egy jelszót az eszköz eléréséhez. **Nincs konfigurálva** (alapértelmezés) nem igényel jelszót. Emellett nem kényszerít semmilyen korlátozást, mint például az egyszerű jelszavak blokkolása vagy a minimális hossz beállítása.
  - **Szükséges jelszó típusa**: Annak megadása, hogy a jelszó csak numerikus lehet-e, vagy Alfanumerikusnak kell lennie (betűket és számokat is tartalmaznia kell).

    Ez a funkció az alábbiakra vonatkozik:  
    - macOS 10.10.3 és újabb verziók

  - **Nem alfanumerikus karakterek száma a jelszóban**: Adja meg a jelszóban használandó speciális karakterek minimális számát (**0** - **4**).<br>A speciális karakterek olyan szimbólumok, mint például a „ **?** ”.
  - **Jelszó minimális hossza**: Adja meg a jelszó minimális hosszát, amelyet a felhasználónak be kell állítania ( **4** és **16** karakter között).
  - **Egyszerű jelszavak**: Az egyszerű jelszavak (például a **0000**vagy az**1234**) használatának engedélyezése.
  - **A jelszó megadása után legfeljebb ennyi perccel a képernyő zárolása után**: Adja meg, hogy mennyi ideig legyen a számítógép inaktív ahhoz, hogy bekapcsoljon a jelszavas zárolás.
  - **A képernyőfelvételek legfeljebb ennyi perc inaktivitás**után: Itt adhatja meg, hogy a számítógépnek mennyi ideig kell tétlennek lennie a képernyő zárolása előtt.
  - **Jelszó érvényessége (napokban)** : Adja meg, hogy hány nap telhet el a kötelező jelszómódosításig (**1** **255** nap).
  - **Korábbi jelszavak újbóli használatának tiltása**: Adja meg a korábban nem használható jelszavak számát **1** és **24**között.

- **A PIN-kód módosításának tiltása a felhasználó**számára: Válassza a **Letiltás** lehetőséget a jelszó módosításának, hozzáadásának vagy eltávolításának leállításához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a PIN-kódok hozzáadását, módosítását vagy eltávolítását.
- **Ujjlenyomat feloldásának tiltása**: Válassza a **Letiltás** lehetőséget, hogy ne használjon ujjlenyomatot az eszköz zárolásának feloldásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára az eszköz zárolásának feloldását ujjlenyomat használatával.

- **Jelszó automatikus**kitöltésének tiltása: A **Letiltás** lehetőség kiválasztásával megakadályozhatja a MacOS-en a jelszavak automatikus kitöltését funkció használatát. A **blokk** kiválasztása a következő hatással is van:

  - A felhasználók nem kérik a mentett jelszavak használatát a Safariban vagy bármely alkalmazásban.
  - Az automatikus erős jelszavak le vannak tiltva, és az erős jelszavakat nem javasoljuk a felhasználók számára.

  **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a funkciókat.

- **Jelszó-közelségi kérelmek letiltása**: Válassza a **Letiltás** lehetőséget, hogy a felhasználó eszköze ne kérjen jelszavakat a közeli eszközökről. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a jelszavakra vonatkozó kérelmeket.

- **Jelszó megosztásának letiltása**: A **Letiltás** megakadályozza a jelszavak megosztását az eszközök között a AirDrop használatával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszavak megosztását.

## <a name="built-in-apps"></a>Beépített alkalmazások

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **Safari automatikus**kitöltésének tiltása: A **Letiltás** letiltja az eszközön a Safari automatikus kitöltés szolgáltatását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a webböngésző automatikus kiegészítési beállításainak módosítását.
- **Kamera letiltása**: Válassza a **Letiltás** lehetőséget a kamera elérésének megakadályozásához az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi az eszköz kamerájának elérését.
- **Apple Music blokkolása**: A **Block** a Music alkalmazást klasszikus módra vált, és letiltja a Music szolgáltatást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az Apple Music alkalmazás használatát.
- **Reflektorfény internetes keresési eredményeinek letiltása**: A **Letiltás** megszakítja a reflektorfényben az internetes keresésből származó eredmények visszaadását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Spotlight-keresés kapcsolódását az internethez a keresési eredmények biztosítása érdekében.
- **Fájlátvitel letiltása az iTunes használatával**: A **Letiltás** letiltja az alkalmazás fájlmegosztó szolgáltatásait. **Nincs konfigurálva** (alapértelmezés) engedélyezi az Application file Sharing Services szolgáltatást.

  Ez a funkció az alábbiakra vonatkozik:  
  - macOS 10,13 és újabb verziók

## <a name="restricted-apps"></a>Korlátozott alkalmazások

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **A korlátozott alkalmazások listájának típusa**: Hozza létre azon alkalmazások listáját, amelyeket a felhasználók nem telepíthetnek és nem használhatnak. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): Az Intune-ban nincsenek korlátozások. A felhasználók hozzáférhetnek a hozzárendelt alkalmazásokhoz és a beépített alkalmazásokhoz.
  - **Tiltott alkalmazások**: Az Intune által nem felügyelt alkalmazásokat, amelyeket nem szeretne telepíteni az eszközre. A felhasználók nem akadályozzák meg a tiltott alkalmazások telepítését. Ha azonban a felhasználó a listából telepít egy alkalmazást, az az Intune-ban szerepel.
  - **Jóváhagyott alkalmazások**: Azok az alkalmazások, amelyeket a felhasználók telepíthetnek. A felhasználók nem telepíthetnek olyan alkalmazásokat, amelyek nem szerepelnek a felsorolásban. Az Intune által kezelt alkalmazások automatikusan engedélyezettek. A felhasználók nem akadályozzák meg a jóváhagyott listán nem szereplő alkalmazások telepítését. De ha igen, az Intune-ban jelentett jelentés.
- Alkalmazáscsomag **azonosítója**: Adja meg a kívánt alkalmazás alkalmazáscsomag- [azonosítóját](bundle-ids-built-in-ios-apps.md) . Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Alkalmazás neve**: Adja meg a kívánt alkalmazás nevét. Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Közzétevő**: Adja meg a kívánt alkalmazás közzétevőjét.

Ha alkalmazásokat szeretne hozzáadni a listához, a következőket teheti:

- **Hozzáadás**: Válassza a lehetőséget az alkalmazások listájának létrehozásához.
- **Importáljon** egy CSV-fájlt az alkalmazás részleteivel, beleértve az URL-címet is. Használja a következő formátumot: `<app bundle ID>, <app name>, <app publisher>`. Vagy az **Exportálás** gombra kattintva hozza létre a hozzáadott alkalmazások listáját ugyanabban a formátumban.

## <a name="connected-devices"></a>Csatlakoztatott eszközök

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **AirDrop letiltása**: A **blokk** megakadályozza a AirDrop használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirDrop funkció használatát a tartalmak a közeli eszközökhöz való cseréjéhez.
- Az **Apple Watch automatikus feloldásának letiltása**: A Letiltás megakadályozza, hogy a felhasználók **leoldják** a MacOS-eszközét az Apple Watch szolgáltatással. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak a macOS-eszközük zárolását az Apple Watch használatával.

## <a name="cloud-and-storage"></a>Felhő és tárolás

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **ICloud-kulcstartó szinkronizálásának letiltása**: Válassza a **Letiltás** lehetőséget, ha le szeretné tiltani a kulcstartóban tárolt hitelesítő adatok icloudba való szinkronizálását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy szinkronizálják ezeket a hitelesítő adatokat.
- **ICloud-dokumentumok szinkronizálásának letiltása**: A **blokk** megakadályozza, hogy az iCloud szinkronizálja a dokumentumokat és az adatokkal. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a dokumentumok és a kulcs-érték szinkronizálását az iCloud tárhelyére.
- **ICloud levelek biztonsági mentésének letiltása**: A **Letiltás** megakadályozza, hogy az iCloud szinkronizáljon a MacOS mail alkalmazásba. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a levelezés szinkronizálását az iCloudba.
- **ICloud-kapcsolattartó biztonsági mentésének letiltása**: A **blokk** megakadályozza, hogy az iCloud szinkronizálja az eszközök névjegyeit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a kapcsolattartási szinkronizálást az iCloud használatával.
- **ICloud naptár biztonsági mentésének letiltása**: A **Letiltás** megakadályozza, hogy az iCloud szinkronizáljon a MacOS Calendar alkalmazásba. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a naptár szinkronizálását az iCloudba.
- **ICloud-emlékeztető biztonsági mentésének letiltása**: A **Letiltás** megakadályozza, hogy az iCloud szinkronizáljon a MacOS-emlékeztetők alkalmazásba. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az emlékeztetők szinkronizálását az iCloudba.
- **ICloud könyvjelző biztonsági mentésének letiltása**: A **blokk** megakadályozza, hogy az iCloud szinkronizálja az eszközök könyvjelzőit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a könyvjelzők szinkronizálását az iCloudba.
- **ICloud-megjegyzések biztonsági mentésének letiltása**: A **blokk** megakadályozza, hogy az iCloud szinkronizálja az eszközök megjegyzéseit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jegyzetek szinkronizálását az iCloudba.
- **ICloud Photo Library letiltása**: A **Letiltás** letiltja az iCloud fényképgyűjteményt, és megakadályozza, hogy az iCloud szinkronizálja az eszközök fényképeit. Az iCloud fényképgyűjteményből nem teljes mértékben letöltött fényképek el lesznek távolítva az eszköz helyi tárolójából. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi fényképek szinkronizálását az eszköz és az iCloud Photo Library között.
- **Handoff**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy egy macOS-eszközön kezdjenek munkát, majd folytassa az elindított munkát egy másik iOS-vagy macOS-eszközön. A **Letiltás** megakadályozza a handoff funkciót az eszközön. 

  Ez a funkció az alábbiakra vonatkozik:  
  - macOS 10,15 és újabb verziók

## <a name="domains"></a>Tartományok

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **E-mail-tartomány URL-címe**: **Adjon hozzá** egy vagy több URL-címet a listához. Ha a felhasználók a konfigurálttól eltérő tartományból kapnak e-mailt, az e-mail-cím nem megbízhatóként van megjelölve a macOS posta alkalmazásban.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az eszköz funkcióit és beállításait [iOS](device-restrictions-ios.md) -eszközökön is korlátozhatja.
