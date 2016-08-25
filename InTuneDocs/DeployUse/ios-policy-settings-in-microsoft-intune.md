---
title: "Az iOS szabályzatbeállításai | Microsoft Intune"
description: "Szabályzatok létrehozása Intune-ban felügyelt iOS-eszközök beállításainak és funkcióinak felügyeletére."
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f9a492a16605130743b943f6aa49d1d633eb97d4
ms.openlocfilehash: 3292df922eeb53108f2b34d4113b0b6c5a114564


---

# iOS-szabályzatbeállítások a Microsoft Intune-ban

Az Intune számos olyan beépített általános beállítást tartalmaz, amelyekkel konfigurálhatja iOS-eszközeit. Ezen kívül használhatja az Apple Configurator eszközt is olyan egyéni beállítások létrehozására, amelyek nem érhetők el az Intune-ban.

## Az általános konfigurációs szabályzat beállításai

A Microsoft Intune **iOS-hoz készült általános konfigurációs szabályzatát** a következő beállítások konfigurálásához használhatja:

-   **Általános eszköz- és biztonsági beállítások** – előre meghatározott beállítások egy listájából választva számos szolgáltatást és funkciót szabályozhat az eszközön.

-   **Teljes képernyős mód** – zárolhatja az eszközöket, hogy csak bizonyos szolgáltatások működjenek rajtuk. Megadhatja például, hogy az eszköz csak egy meghatározott felügyelt alkalmazás futtatását engedélyezze, vagy letilthatja a hangerő-szabályozó gombok használatát az eszközön. Ezek a beállítások egy eszköz demonstrációs modelljéhez, illetve egy olyan eszközhöz használhatók, amely csak egyetlen funkció végrehajtására van kijelölve (például egy pénztári eszköz).

-   **Megfelelő és nem megfelelő alkalmazások** – egy listában megadhatja a vállalatban megfelelőnek vagy nem megfelelőnek ítélt alkalmazásokat. Android és iOS rendszerű eszközökön a **Nem kompatibilis alkalmazások jelentése** beállítással ellenőrizhető, hogy a listában megadott alkalmazás kompatibilis-e a felhasználók által telepített alkalmazásokkal (az alkalmazás telepítése azonban ténylegesen nem tiltható le).

> [!TIP]
> Beállíthat feltételeket a felhasználók számára, amelyekkel gondoskodhat arról, hogy tudomásul vegyék, hogy az eszközükön lévő alkalmazásokat – beleértve a személyes alkalmazásokat – értékelni fogják, a nem kompatibilis alkalmazások pedig le lesznek tiltva, vagy nem kompatibilisként lesznek jelentve. A felhasználóknak el kell fogadniuk ezeket a feltételeket ahhoz, hogy beléptethessék eszközüket, és a vállalati portál segítségével beszerezhessék az alkalmazásokat. A használati feltételekkel kapcsolatos további információkért lásd: [Használati feltételek szabályzatbeállításai a Microsoft Intune-ban](terms-and-condition-policy-settings-in-microsoft-intune.md).

Ha a keresett beállítás nem jelenik meg ebben a témakörben, valószínűleg létre tudja hozni egy egyéni iOS-szabályzattal, mellyel az [Apple Configurator eszközzel](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) létrehozott beállításokat importálhatja. További információkért olvassa el a jelen témakörben alább található **Egyéni szabályzatbeállítások** című részt.

### Biztonsági beállítások

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Jelszó szükséges a mobileszközök feloldásához**|Ez a beállítás azt határozza meg, hogy a felhasználóknak kell-e jelszót megadniuk az eszközükhöz való hozzáféréshez.|Igen|
|**Kötelező jelszótípus**|A megkövetelt jelszótípust határozza meg, például hogy a jelszó csak számokat, vagy számokat és betűket is tartalmazhat.|Igen|
|**Megkövetelt jelszótípus – a karakterkészletek minimális száma**|Azt határozza meg, hogy hány szimbólumnak (például **#** vagy **@**) kell szerepelnie a jelszóban.|Igen|
|**Jelszó minimális hossza**|A jelszóban használandó karakterek minimális számát határozza meg.|Igen|
|**Egyszerű jelszavak engedélyezése**|Egyszerű jelszavak, például „0000” vagy „1234” engedélyezése.|Igen|
|**Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt**|A megadott számú sikertelen bejelentkezési kísérlet után törli az eszközt.|Igen|
|**Képernyő kikapcsolása ennyi perc inaktivitás után**<sup>1</sup>|Ennyi perc elteltével kapcsol ki a kijelző.|Igen|
|**Jelszó lejárata (nap)**|Ennyi nap elteltével kell megváltoztatni az eszköz jelszavát.|Igen|
|**Jelszóelőzmények megjegyzése**|Ez a beállítás azt határozza meg, hogy a felhasználó használhatja-e az általa korábban használt jelszavakat.|Igen|
|**Korábbi jelszavak megjegyzése** – **Korábbi jelszavak újbóli használatának tiltása**|Ez a beállítás az eszköz által megjegyzett korábbi jelszavak számát határozza meg.|Igen|
|**Tétlen percek száma, mielőtt az eszköz újból kéri a jelszót**<sup>1</sup>|Ez a beállítás azt határozza meg, hogy az eszköz mennyi időt tölthet üresjáratban, mielőtt a felhasználónak újra be kell írnia a jelszavát.|Igen|
|**Ujjlenyomattal történő zárolásfeloldás engedélyezése**|Az eszközzárolás ujjlenyomattal történő feloldásának engedélyezése.|iOS 7.1-es és újabb verziók|
<sup>1</sup> Ha a **Képernyő kikapcsolása ennyi perc inaktivitás után** és a **Jelszó kérése ennyi perc inaktivitás után** beállítást is konfigurálja iOS-eszközökön, azok egymás után lesznek alkalmazva. Ha például mindkét beállítást az **5** perc értékre állítja be, a képernyő 5 perc után automatikusan ki fog kapcsolni, és az eszköz további 5 perc után lesz zárolva. Ha azonban a felhasználó manuálisan kapcsolja ki a képernyőt, azonnal a második beállítás lesz alkalmazva. Ugyanebben a példában az eszköz 5 perccel azután lesz zárolva, hogy a felhasználó kikapcsolta a képernyőt.

### Rendszerbeállítások

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Képernyőkép-készítés engedélyezése**|Engedélyezi a felhasználó számára, hogy képként rögzítse a képernyő tartalmát.|Igen|
|**Vezérlőközpont engedélyezése a zárolási képernyőn**|Itt adható meg, hogy a Vezérlőközpont alkalmazás elérhető legyen-e, amikor az eszköz zárolva van.|iOS 7.1-es és újabb verziók|
|**Értesítési nézet engedélyezése a zárolási képernyőn**|Engedélyezi a felhasználó számára, hogy az eszköz zárolásának feloldása nélkül is hozzáférhessen az értesítések nézetéhez.|iOS 7.1-es és újabb verziók|
|**Ma nézet engedélyezése a zárolási képernyőn**|Itt adható meg, hogy megtekinthetők-e az értesítések, amikor az eszköz zárolva van.|iOS 7.1-es és újabb verziók|
|**Diagnosztikai adatok küldésének engedélyezése**|Engedélyezi vagy letiltja, hogy az eszköz diagnosztikai adatokat küldjön az Apple számára.|Igen|
|**Nem megbízható TLS tanúsítványok engedélyezése**|Engedélyezi nem megbízható TLS-tanúsítványok használatát az eszközön.|Igen|
|**Passbook zárolt állapotban való használatának engedélyezése**|Engedélyezi a felhasználó számára a Passbook alkalmazás eszközzárolás alatti elérését.|Igen|

### Felhőbeállítások – dokumentumok és adatok

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**iCloudba történő biztonsági mentés engedélyezése**|Engedélyezi a felhasználó számára, hogy biztonsági mentést készítsen az iCloudba az eszközről.|Igen|
|**Dokumentum iCloudba szinkronizálásának engedélyezése**|Engedélyezi a dokumentumok és kulcsértékek szinkronizálását az iCloud tárhelyére.|Igen|
|**Fényképadatfolyamok iCloudba szinkronizálásának engedélyezése**|Engedélyezi az eszközön lévő fényképek szinkronizálását az iCloudba.|Igen|
|**Biztonsági másolat titkosításának engedélyezése**|Megköveteli az eszköz minden biztonsági másolatának titkosítását.|Igen|

### Alkalmazásbeállítások – böngésző

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Safari engedélyezése**|Ez a beállítás azt határozza meg, hogy a Safari böngésző használható-e az eszközön.|Igen|
|**Automatikus kitöltés engedélyezése**|A felhasználók módosíthatják a böngésző automatikus kiegészítési funkciójának beállításait.|Igen|
|**Előugróablak-blokkoló engedélyezése**|Engedélyezi vagy letiltja a böngésző előugróablak-blokkolóját.|Igen|
|**Cookie-k engedélyezése**|Engedélyezi Cookie-k használatát az eszköz webböngészője számára.|Igen|
|**JavaScript engedélyezése**|Java-parancsfájlok böngészőben történő futtatásának engedélyezése.|Igen|
|**Csalás elleni figyelmeztetés engedélyezése**|Csalás elleni figyelmeztetés engedélyezése az eszköz böngészőjében.|Igen|

### Alkalmazásbeállítások – alkalmazások

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Alkalmazástároló használatának engedélyezése**|Az alkalmazás-áruház elérésének engedélyezése az eszköz számára.|Igen|
|**Jelszó megkövetelése az alkalmazástárolóhoz való hozzáféréshez**|A felhasználókat jelszó beírására kötelezi az alkalmazás-áruházhoz való hozzáféréshez.|Igen|
|**Alkalmazáson belüli vásárlás engedélyezése**|A futó alkalmazásokból történő áruházi vásárlások engedélyezése.|Igen|
|**Felügyelt dokumentumok engedélyezése egyéb, nem felügyelt alkalmazásokban**|A vállalati dokumentumok bármely alkalmazásban való megtekintésének engedélyezése.<br>**Példa:** Szeretné megakadályozni, hogy a felhasználók fájlokat mentsenek a OneDrive alkalmazásból a Dropbox alkalmazásba. Állítsa be ezt a beállítást „Nem” értékre. Miután az eszköz megkapja a házirendet (például újraindítás után), nem engedélyezi többé a mentést.|iOS 7.1-es és újabb verziók|
|**Nem felügyelt dokumentumok engedélyezése egyéb, felügyelt alkalmazásokban**|Bármely dokumentum felügyelt vállalati alkalmazásokban való megtekintésének engedélyezése.|iOS 7.1-es és újabb verziók|
|**Videokonferenciák engedélyezése**|Videokonferencia-alkalmazások, például a Facetime engedélyezése az eszközön.|Igen|
|**Felnőtt tartalom engedélyezése a médiatárban**|Felnőttnek minősített áruházi tartalom elérésének engedélyezése az eszköz számára.|Igen|

### Alkalmazásbeállítások – játékok

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Game Centerbeli ismerősök felvételének engedélyezése**|Barátok hozzáadásának engedélyezése a Game Center alkalmazásban a felhasználó számára.|Igen|
|**Több résztvevős játék engedélyezése**|Engedélyezi a felhasználó számára, hogy többszereplős játékokat játsszon az eszközön.|Igen|

### Eszközképességek beállításai – hardver

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Kamera használatának engedélyezése**|A beállítás meghatározza, hogy használható-e az eszközön a kamera.|Igen|

### Eszközképességek beállításai – mobilhálózat

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Hangroaming használatának engedélyezése**|Hangroaming használatának engedélyezése, ha az eszköz mobilhálózathoz csatlakozik.|Igen|
|**Adatroaming használatának engedélyezése**|Adatroaming használatának engedélyezése, ha az eszköz mobilhálózathoz csatlakozik.|Igen|
|**Roamingolás közbeni globális, háttérbeli adatbeolvasás engedélyezése**|Mobilhálózati roaming közben történő adatlehívás, például e-mail engedélyezése az eszköz számára.|Igen|

### Eszközképességek beállításai – szolgáltatások

|Beállítás neve|Részletek|iOS|
|----------------|-------|
|**Siri engedélyezése**|A Siri beszédfelismerési asszisztens használatának engedélyezése az eszközön.|Igen|
|**Siri zárolt eszközön való használatának engedélyezése**|A Siri beszédfelismerési asszisztens eszközzárolás alatti használatának engedélyezése az eszközön.|Igen|
|**Hangtárcsázás engedélyezése**|A hangtárcsázási funkció engedélyezése az eszközön.|Igen|


### A szabályzatnak megfelelő és nem megfelelő alkalmazásokra vonatkozó beállítások
A **Szabályzatnak megfelelő és nem megfelelő alkalmazások** listában adja meg a kompatibilis vagy nem kompatibilis eszközök listáját az alábbi információk alapján:

> [!NOTE]
> Egy házirendben csak egy, kompatibilis vagy nem kompatibilis alkalmazásokat tartalmazó lista szerepelhet. Mindkét típusú lista nem adható meg ugyanabban a házirendben.

|Beállítás neve|Részletek|
|----------------|--------------------|
|**Meg nem felelésről szóló jelentés küldése, ha a felhasználók telepítik a listán szereplő alkalmazások valamelyikét**|Azokat a nem az Intune által kezelt alkalmazásokat tartalmazza, amelyek telepítése és futtatása nem engedélyezett a felhasználóknak.|
|**Meg nem felelés jelentésének mellőzése, ha a felhasználók telepítik a listán szereplő alkalmazások valamelyikét**|Azokat az alkalmazásokat tartalmazza, amelyeket a felhasználók telepíthetnek. A megfelelőség biztosítása érdekében a felhasználók nem telepíthetnek olyan alkalmazásokat, amelyek nem szerepelnek a listán. Az Intune által kezelt alkalmazások automatikusan engedélyezettek.|
|**Hozzáadás**|Hozzáadhat egy alkalmazást a kijelölt listához. Meg kell adnia egy szabadon választott nevet, valamint tetszés szerint megadhatja az alkalmazás kiadóját, valamint az alkalmazás alkalmazás-áruházbeli URL-címét. További segítségért olvassa el az ebben a témakörben alább található **Alkalmazás-áruházak URL-címének megadása** című részt.|
|**Alkalmazások importálása**|Importálhatja azokat az alkalmazásokat, amelyeket egy vesszővel tagolt fájlban megadott. Használja a fájlban megadott formátumot, alkalmazásnevet, kiadót és URL-címet.|
|**Szerkesztés**|Segítségével szerkesztheti a kijelölt alkalmazás nevét, kiadóját és URL-címét.|
|**Törlés**|Törölheti a kijelölt alkalmazást a listából.|

### Teljes képernyős mód beállításai

|Beállítás neve|Részletek|
|----------------|--------------------|
|**Az eszköz Kioszk módjában futtatható kezelt alkalmazás kiválasztása**|Válassza a **Tallózás** elemet, majd adja meg azt a kezelt alkalmazást, illetve áruházbeli alkalmazást, amelynek engedélyezni szeretné a futtatását, amikor az eszköz kioszkmódban van. Más alkalmazás nem lesz futtatható az eszközön. További segítségért olvassa el az ebben a témakörben alább található **Alkalmazás-áruházak URL-címének megadása** című részt.|
|**Érintés engedélyezése**|Engedélyezheti vagy letilthatja az érintőképernyőt az eszközön.|
|**Képernyő elforgatásának engedélyezése**|Engedélyezheti vagy letilthatja a képernyő tájolásának módosítását az eszköz elforgatásakor.|
|**Hangerőszabályzó gombok engedélyezése**|Engedélyezheti vagy letilthatja a hangerőszabályzó gombok használatát az eszközön.|
|**Csengetőkapcsoló engedélyezése**|Engedélyezheti vagy letilthatja a csengető- (némító-) kapcsolót az eszközön.|
|**Képernyő ébresztőgombjának engedélyezése**|Engedélyezheti vagy letilthatja a képernyő ébresztőgombját az eszközön.|
|**Automatikus zárolás engedélyezése**|Engedélyezheti vagy letilthatja az eszköz automatikus zárolását.|
|**Monó hang engedélyezése**|Engedélyezheti vagy letilthatja a **Monó hang**kisegítő beállítást.|
|**Hangalámondás engedélyezése**|Engedélyezheti vagy letilthatja a **VoiceOver** kisegítő beállítást, amely hangosan felolvassa az eszköz képernyőjén megjelenő szöveget.|
|**A hangalámondás módosításának engedélyezése**|Engedélyezheti vagy letilthatja a VoiceOver funkció módosítását (például hogy milyen gyorsan történjen a képernyőn látható szöveg felolvasása).|
|**Nagyítás engedélyezése**|Engedélyezheti vagy letilthatja a **Nagyítás** kisegítő beállítást, amellyel érintéssel nagyíthatja az eszköz képernyőjén megjelenő tartalmat.|
|**Nagyítás módosításának engedélyezése**|Engedélyezheti vagy letilthatja a nagyítási funkció módosítását.|
|**Színek invertálásának engedélyezése**|Engedélyezheti vagy letilthatja a **Színek invertálása** kisegítő beállítást, amellyel módosíthatja a képernyőt a látásukban korlátozott felhasználók számára.|
|**Színinvertálás módosításának engedélyezése**|Engedélyezheti vagy letilthatja a színinvertálási funkció módosítását.|
|**Kisegítő érintés engedélyezése**|Engedélyezheti vagy letilthatja a **Kisegítő érintés** kisegítő beállítást, amely segít a nehézségekkel küszködő felhasználóknak a képernyőn elvégezhető kézmozdulatok végrehajtásában.|
|**Kisegítő érintés módosításának engedélyezése**|Engedélyezheti vagy letilthatja a Kisegítő érintés funkció módosítását.|
|**Beszéd kiválasztásának engedélyezése**|Engedélyezheti vagy letilthatja a **Beszéd kiválasztása** kisegítő beállítást, amellyel felolvastatható az Ön által kijelölt szöveg.|
> [!NOTE]
> Az alábbi megjegyzések az iOS-eszközök Kioszk módjának beállításaira vonatkoznak:
> 
> -   Az iOS-eszközök a teljes képernyős módra való konfigurálása előtt felügyelt módra kell állítania az eszközt az [Apple Configurator eszközzel](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) vagy az eszközregisztráció-kezelővel. Az Apple Configurator eszközzel kapcsolatos további információkat az Apple dokumentációjában talál.
> -   Ha a megadott iOS-alkalmazás a konfigurációs házirend alkalmazása után települ, az eszköz mindaddig nem lép Kioszk módba, amíg újra nem indítják.

### A szabályzatnak megfelelő és nem megfelelő alkalmazások referenciaadatai

#### A szabályzatnak megfelelő és nem megfelelő alkalmazások figyelése
A **Nem kompatibilis alkalmazások jelentése** beállítás használatával megtekintheti az engedélyezett és letiltott alkalmazások kompatibilitását.

##### A nem kompatibilis alkalmazások jelentésének futtatása

1.  A [Microsoft Intune felügyeleti konzolban](https://manage.microsoft.com) válassza a **Jelentések** &gt; **Jelentés a szabályzatnak nem megfelelő alkalmazásokról** elemet.

2.  Jelölje ki az ellenőrizni kívánt eszközcsoportokat, adja meg, hogy a kompatibilis vagy a nem kompatibilis alkalmazásokat szeretné-e ellenőrizni, illetve mindkettőt, majd válassza a **Jelentés megtekintése**elemet.

#### Alkalmazás-áruházak URL-címének megadása
Ha meg szeretné adni egy alkalmazás URL-címét a szabályzatnak megfelelő és nem megfelelő alkalmazások listájában, illetve **Az eszköz kioszkmódjában futtatandó felügyelt alkalmazás kiválasztása** beállításban (csak iOS rendszerben), használja a következő formátumot:

Egy keresőmotor segítségével keresse meg az iTunes alkalmazás-áruházban használni kívánt alkalmazást, és nyissa meg az alkalmazás lapját.

Másolja a vágólapra a lap URL-címét, és használja ezt az URL-címet a kompatibilis és nem kompatibilis alkalmazások listájának, illetve a Kioszk módban futtatni kívánt alkalmazásnak a konfigurálásához.

**Például:** Keressen rá az **iPad Microsoft Word**kifejezésre. Ebben az esetben a következő URL-t használja: **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Az iTunes szoftverrel is megkeresheti az alkalmazást, majd a **Hivatkozás másolása** parancs használatával beszerezheti az alkalmazás URL-címét.


## Egyéni szabályzatbeállítások

A Microsoft Intune **egyéni iOS-szabályzat** használatával az [Apple Configurator eszközzel](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) létrehozott beállítások iOS-alapú eszközökre telepíthetők. Ezzel az eszközzel számos olyan beállítást készíthet, amelyek ezen eszközök működését vezérlik, és egy konfigurációs profilba exportálhatja őket. Ezt a konfigurációs profilt később Intune iOS-szabályzatokba importálhatók, és a beállítások telepíthetők a szervezetben lévő felhasználók és eszközök számára.

Ezzel a funkcióval olyan iOS-beállításokat léptethet érvénybe, amelyek nem konfigurálhatók az Intune általános konfigurációs szabályzatával.

### Előfeltételek
Mielőtt elkezdené, telepítenie kell az Apple Configurator eszközt, és létre kell hoznia a felhasználók vagy eszközök számára telepíteni kívánt beállításokat tartalmazó konfigurációs fájlt. Az Apple Configurator eszköz letöltése és az azzal kapcsolatos információk a [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)áruházban érhetők el

> [!NOTE]
> Az Intune nem készít jelentést az egyéni iOS-házirendek egyes beállításainak betartásáról. a teljes házirend betartásáról azonban igen.

### Általános beállítások

|Beállítás neve|Részletek|
    |----------------|--------------------|
    |**Név**|Adjon meg egy egyedi nevet az egyéni iOS-házirend számára, hogy az azonosítható legyen az Intune konzolján.|
    |**Leírás**|Adjon meg egy leírást, amely áttekintést nyújt az iOS egyéni szabályzatáról, és olyan releváns információkat tartalmaz, amelyek megkönnyítik a keresését.|

### Egyéni beállítások

|Beállítás neve|Részletek|
    |----------------|--------------------|
|**Egyéni konfigurációs profil neve (megjelenik a felhasználók számára)**|Nevezze el a szabályzatot. Ez a név jelenik majd meg az eszközön és az Intune szabályzatjelentéseiben.|
|**Konfigurációs profilfájl**|Válassza az **Importálás** elemet, majd keresse meg az Apple Configurator eszközzel létrehozott konfigurációs profilt. **Megjegyzés:** Ellenőrizze, hogy az Apple Configurator eszközből exportált beállítások kompatibilisek-e azon eszközök iOS-verziójával, amelyekre az egyéni iOS-házirendet telepíti. A nem kompatibilis beállításokból fakadó problémák megoldásával kapcsolatos információkat az [Apple Developer](https://developer.apple.com/) webhelyről letölthető **Configuration Profile Reference** és **Mobile Device Management Protocol Reference** című (angol nyelvű) útmutatóban talál.|
    |**Konfigurációs profil részletei**|Megjeleníti az importált konfigurációs profil xml-kódját.|

### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


