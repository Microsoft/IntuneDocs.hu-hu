---
title: "A Mac OS X-házirendek beállításai | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8c1f4f209c5ec704290882b8f6f71e0b1b01d21c
ms.openlocfilehash: bbbb666fdc34a82d247d760d156d48c5ac72374c


---

# A Mac OS X-konfigurációs házirendek beállításai a Microsoft Intune-ban

## Az általános konfigurációs szabályzat beállításai

A Microsoft Intune **Mac OS X-hez készült általános konfigurációs szabályzatát** a következő beállítások konfigurálásához használhatja:

-   **Eszközbiztonsági beállítások** – az előre meghatározott beállítások listájából választva számos szolgáltatást és funkciót szabályozhat az eszközökön.

-   **Megfelelő és nem megfelelő alkalmazások** – egy listában megadhatja a vállalatban megfelelőnek vagy nem megfelelőnek ítélt alkalmazásokat. A Jelentés a szabályzatnak nem megfelelő alkalmazásokról beállítással ellenőrizhető, hogy a listában megadott alkalmazás kompatibilis-e a felhasználók által telepített alkalmazásokkal (az alkalmazás telepítése azonban nem tiltható le).

Ha ez a lista nem tartalmazza a keresett beállítást, próbálja meg létrehozni egy egyéni Mac OS X-házirenddel, amely lehetővé teszi az Apple Configurator eszközzel létrehozott beállítások importálását. További információkért olvassa el a jelen témakörben alább található **Egyéni szabályzatbeállítások** című részt.

### Jelszóbeállítások

|Beállítás neve|Részletek|
|----------------|---------------|
|**Jelszó kérése az eszközzárolás feloldásához**|Itt adhatja meg, hogy a felhasználónak kell-e jelszót használnia Mac-számítógépe eléréséhez. **Fontos:** Az IOS-eszközöktől eltérően a Mac OS X-eszközökön a felhasználó nem azonnal kap jelszófrissítési értesítést a beállításnak való megfelelés érdekében.|
|**Kötelező jelszótípus**|Annak megadása, hogy a jelszó csak numerikus lehet-e, illetve hogy **alfanumerikusnak** kell-e lennie (betűket és számokat is tartalmaznia kell). **Fontos:** Ezt a beállítást csak a Mac OS X 10.10.3-as és újabb verziói támogatják.|
|**Jelszó speciális karaktereinek minimális száma**|A jelszóban használandó speciális karakterek minimális számának (**0** - **4**) megadása.<br /><br />A speciális karakterek szimbólumok, mint például a kérdőjel (**?**)|
|**Jelszó minimális hossza**|A jelszó minimális hosszának ( **4** – **14** karakter) megadása.|
|**Egyszerű jelszavak engedélyezése**|Az egyszerű jelszavak (például a**0000**vagy az**1234**) használatának engedélyezése.|
|**Tétlen percek száma, mielőtt az eszköz újból kéri a jelszót**|Annak megadása, hogy mennyi ideig legyen a számítógép inaktív ahhoz, hogy bekapcsoljon a jelszavas zárolás.|
|**Jelszó lejárata (nap)**|Itt adhatja meg, hogy mennyi idő telhet el a kötelező jelszómódosításig (**1** - **255** nap).|
|**Jelszóelőzmények megjegyzése**|Ezzel a beállítással megakadályozhatja, hogy a felhasználó a korábban használt jelszavakat használja. Ha engedélyezi ezt a beállítást, a **Korábbi jelszavak újbóli használatának tiltása** beállítással megadhatja, hogy hány korábban használt jelszó ne legyen újra felhasználható (**1** - **24**).|
|**Képernyőkímélő bekapcsolása ennyi perc inaktivitás után**|Annak megadása, hogy a számítógépnek mennyi ideig kell inaktívnak lennie a képernyőkímélő aktiválásához.|

### A szabályzatnak megfelelő és nem megfelelő alkalmazásokra vonatkozó beállítások
A **Szabályzatnak megfelelő &amp; nem megfelelő alkalmazások Mac OS X-es eszközökhöz** listában engedélyezze az **Eszközök felügyelt beállításai** beállítást, majd adja meg a kompatibilis vagy nem kompatibilis alkalmazások listáját az alábbi információk alapján:

> [!NOTE]
> Egy házirendben csak egy, kompatibilis vagy nem kompatibilis alkalmazásokat tartalmazó lista szerepelhet. Mindkét típusú lista nem adható meg ugyanabban a házirendben.
> 
> Az Intune lehetővé teszi, hogy jelentést készítsen a nem megfelelő alkalmazásokat futtató eszközökről. Ezzel nem tiltja le a nem megfelelő alkalmazások telepítését, és nem is távolítja el azokat.

|Beállítás neve|Részletek|
|----------------|---------------|
|**Meg nem felelésről szóló jelentés küldése, ha a felhasználók telepítik a listán szereplő alkalmazások valamelyikét**|Azon alkalmazások felsorolása, amelyek telepítésére a felhasználók nem jogosultak. Ha a felhasználók ezen alkalmazások bármelyikét telepítik, szerepelni fognak a **szabályzatoknak nem megfelelő alkalmazásokról készült jelentésekben**.|
|**Meg nem felelésről szóló jelentés küldése, ha a felhasználók a listán nem szereplő alkalmazásokat telepítenek**|Azon Mac OS X-alkalmazások felsorolása, amelyek telepítésére a felhasználók jogosultak. Ha a felhasználók bármilyen más alkalmazást telepítenek, szerepelni fognak a **szabályzatoknak nem megfelelő alkalmazásokról készült jelentésekben**.|
|**Hozzáadás**|Hozzáadhat egy alkalmazást a kijelölt listához. Meg kell adnia egy szabadon választott nevet, valamint tetszés szerint megadhatja az alkalmazás kiadóját, valamint az alkalmazás csomagazonosítóját. **Tipp:** Az alkalmazás csomagazonosítóját az alábbi lépésekkel keresheti meg a telepített alkalmazást futtató Mac számítógépen:<ol><li>Nyissa meg az alkalmazás telepítési mappáját (például **/Applications**)</li><li>Jelölje ki az *&lt;alkalmazásnév&gt;***.app** csomagot, és válassza a **Show Package Contents** (Csomag tartalmának megjelenítése) lehetőséget.</li><li>Nyissa meg az **Info.plist** fájl</li><li>Ellenőrizze a **CFBundleIdentifier**kulcshoz hozzárendelt értéket</li></ol>A csomagazonosító formátuma: **com.contoso.alkalmazásnév**|
|**Alkalmazások importálása**|Importálhatja azokat az alkalmazásokat, amelyeket egy vesszővel tagolt fájlban megadott. Használja a fájlban megadott formátumot, alkalmazásnevet, kiadót és alkalmazáscsomag-azonosítót.|
|**Szerkesztés**|A kiválasztott alkalmazás nevének, kiadójának és alkalmazáscsomag-azonosítójának szerkesztése.|
|**Törlés**|Törölheti a kijelölt alkalmazást a listából.|
> [!TIP]
> Az Intune-jelentésekkel kapcsolatos további információkért lásd: [A Microsoft Intune-műveletek értelmezése jelentések segítségével](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Ha egy Mac OS X-eszköz készenléti állapotban van, a házirendek és profilok nem kézbesíthetők, és nem naplózhatók. Ennek következtében előfordulhat, hogy az Intune konzolján ideiglenesen a **Hibás házirend-beállítások** állapotüzenet jelenik meg, amíg az eszköz fel nem ébred a készenléti üzemmódból.

### A szabályzatnak megfelelő és nem megfelelő alkalmazások figyelése
A **szabályzatnak nem megfelelő alkalmazásokról készült jelentésben** megtekintheti a megadott alkalmazások megfelelőségét.

#### A jelentés futtatása

1.  A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com) kattintson a **Jelentések** &gt; **Szabályzatoknak nem megfelelő alkalmazások – jelentések** elemre.

2.  Jelölje ki az ellenőrizni kívánt eszközcsoportokat, adja meg, hogy a kompatibilis vagy a nem kompatibilis alkalmazásokat szeretné-e ellenőrizni, illetve mindkettőt, majd kattintson a **Jelentés megtekintése**elemre.

## Egyéni Mac OS X-házirendbeállítások a Microsoft Intune-ban
A Microsoft Intune **egyéni Mac OS X-konfigurációs szabályzatával** léptetheti érvénybe az [Apple Configurator eszközzel](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) létrehozott beállításokat a Mac OS X-eszközökön. Ezzel az eszközzel számos olyan beállítást készíthet, amelyek ezen eszközök működését vezérlik, és egy konfigurációs profilba exportálhatja őket. Ezt a konfigurációs profilt később egy Intune-beli egyéni Mac OS X-szabályzatba importálhatja, és a beállításokat telepítheti a szervezetben lévő felhasználók és eszközök számára.

E funkció révén olyan Mac OS X-beállításokat léptethet érvénybe, amelyek nem konfigurálhatók az Intune általános Mac OS X-konfigurációs szabályzatával.

### Előfeltételek
Mielőtt elkezdené, telepítenie kell az Apple Configurator eszközt, és létre kell hoznia a felhasználók vagy eszközök számára telepíteni kívánt beállításokat tartalmazó konfigurációs fájlt. Az Apple Configurator eszköz letöltése és az azzal kapcsolatos információk a [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) áruházban érhetők el.

> [!NOTE]
> Az Intune nem készít jelentést az egyéni Mac OS X-szabályzatok egyes beállításainak betartásáról, a teljes házirend betartásáról azonban igen.

### Általános beállítások

|Beállítás neve|Részletek|
    |----------------|--------------------|
    |**Név**|Az egyéni Mac OS X-szabályzatnak egyéni nevet adjon, hogy könnyebben azonosíthassa az Intune konzolján.|
    |**Leírás**|Adjon meg egy leírást, amely áttekintést nyújt az egyéni Mac OS X-házirendről, és olyan releváns információkat tartalmaz, amelyek megkönnyítik a keresését.|


### Egyéni beállítások

|Beállítás neve|Részletek|
    |----------------|--------------------|
    |**Egyéni konfigurációs profil neve (megjelenik a felhasználók számára)**|Nevezze el a szabályzatot. Ez a név jelenik majd meg az eszközön és az Intune szabályzatjelentéseiben.|
    |**Konfigurációs profilfájl**|Kattintson az **Importálás**lehetőségre, majd keresse meg az Apple Configurator eszközzel létrehozott konfigurációs profilt. **Tipp:** A **Konfigurációs profilfájl létrehozása** című témakörben talál segítséget a konfigurációs profil létrehozásához.|
    |**Konfigurációs profil részletei**|Megjeleníti az importált konfigurációs profil xml-kódját.|



### Konfigurációs profilfájl létrehozása
Az egyéni házirend által használt konfigurációs profilfájlt kétféleképpen hozhatja létre:

-   A fájl Apple Configurator eszközből történő exportálásával ( **.mobileconfig**kiterjesztéssel).

-   A fájlt Ön is létrehozhatja, ha az [Apple konfigurációs profilok készítésére szolgáló útmutatójának](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html)megfelelő sémáját használja.


> [!IMPORTANT]
> Ha egy Mac OS X-eszköz készenléti állapotban van, a házirendek és profilok nem kézbesíthetők, és nem naplózhatók. Ennek következtében előfordulhat, hogy az Intune konzolján ideiglenesen a **Hibás házirend-beállítások** állapotüzenet jelenik meg, amíg az eszköz fel nem ébred a készenléti üzemmódból.

### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


