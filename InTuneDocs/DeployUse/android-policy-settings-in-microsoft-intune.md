---
title: "Android- és Samsung KNOX-eszközök konfigurációs házirendjének beállításai | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 62beaec31a0cdc3c28fd3eed820a6771e42ef3e7
ms.openlocfilehash: f4c0eccb0cd30daaba97e8f34eea69e3d0e8e0ad


---

# Android- és Samsung KNOX-eszközök konfigurációs házirendjének beállításai a Microsoft Intune-ban

## Általános konfigurációs szabályzat

A Microsoft Intune **Androidhoz készült általános konfigurációs szabályzatát** a következő beállítások konfigurálásához használhatja:

-   **Mobileszköz-biztonsági beállítások** – előre meghatározott beállítások egy listájából választva számos szolgáltatást és funkciót szabályozhat az eszközökön.

-   **Teljes képernyős mód** (csak Samsung KNOX-eszközök esetén) – zárolhatja az eszközöket, hogy csak bizonyos szolgáltatások működjenek rajtuk. Megadhatja például, hogy az eszköz csak egy meghatározott felügyelt alkalmazás futtatását engedélyezze, vagy letilthatja a hangerő-szabályozó gombok használatát az eszközön. Ezek a beállítások egy eszköz demonstrációs modelljéhez, illetve egy olyan eszközhöz használhatók, amely csak egyetlen funkció végrehajtására van kijelölve (például egy pénztári eszköz).

-   **Megfelelő és nem megfelelő alkalmazások** – egy listában megadhatja a vállalatban megfelelőnek vagy nem megfelelőnek ítélt alkalmazásokat. Android és iOS rendszerű eszközökön a **Nem kompatibilis alkalmazások jelentése** beállítással ellenőrizhető, hogy a listában megadott alkalmazás kompatibilis-e a felhasználók által telepített alkalmazásokkal (az alkalmazás telepítése azonban ténylegesen nem tiltható le).

> [!TIP]
> Beállíthat feltételeket a felhasználók számára, amelyekkel gondoskodhat arról, hogy tudomásul vegyék, hogy az eszközükön lévő alkalmazásokat – beleértve a személyes alkalmazásokat – értékelni fogják, a nem kompatibilis alkalmazások pedig le lesznek tiltva, vagy nem kompatibilisként lesznek jelentve. A felhasználóknak el kell fogadniuk ezeket a feltételeket ahhoz, hogy beléptethessék eszközüket, és a vállalati portál segítségével beszerezhessék az alkalmazásokat. A használati feltételekkel kapcsolatos további információt a [Használati feltételek házirend-beállításai a Microsoft Intune-ban](terms-and-condition-policy-settings-in-microsoft-intune.md) című témakörben találhat.

Ha a keresett beállítás nem jelenik meg ebben a témakörben, valószínűleg létre tudja hozni egy egyéni Android-szabályzattal, amely lehetővé teszi az OMA-URI-beállítások használatát az eszköz vezérlésére. További információkért olvassa el a jelen témakörben alább található **Egyéni szabályzatbeállítások** című részt.

### Jelszóbeállítások

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Jelszó szükséges a mobileszközök feloldásához**|Jelszó kérése a támogatott eszközökön.|Igen|Igen|
|**Jelszó minimális hossza**|A jelszó minimális hossza.|Igen|Igen|
|**Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt**|A megadott számú sikertelen bejelentkezési kísérlet után törli az eszközt.|Igen|Igen|
|**Képernyő kikapcsolása ennyi perc inaktivitás után**|Az eszköz az itt megadott másodperc elteltével automatikusan zárolja magát.|Igen|Igen|
|**Jelszó lejárata (nap)**|Azon napok száma, amely után a jelszót kötelező megváltoztatni.|Igen|Igen|
|**Jelszóelőzmények megjegyzése**|Az eszköz ennyi korábban használt jelszót fog tárolni.|Igen|Igen|
|**Korábbi jelszavak megjegyzése** – **Korábbi jelszavak újbóli használatának tiltása**|Megakadályozza a korábban használt jelszavak használatát.|Igen|Igen|
|**Jelszó minősége**|Válassza ki a jelszó erősségének szintjét, valamint hogy használható-e biometrikus eszköz.|Igen|Igen|
|**Ujjlenyomattal történő zárolásfeloldás engedélyezése**|Az eszköz ujjlenyomattal történő feloldásának engedélyezése.|Nem|Igen|
|**Intelligens zárolás és más megbízhatósági ügynökök engedélyezése**<br>(Android 5 és újabb verziók)|A kompatibilis Android-eszközökön vezérelheti vele az intelligens zárolás funkciót. Ez a „megbízhatósági ügynökök” néven is ismert telefonos funkció lehetővé teszi az eszköz zárolási képernyője jelszavának letiltását vagy megkerülését, ha az eszköz megbízható helyen van, például ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címkéhez van közel. Ezzel a beállítással megakadályozhatja a végfelhasználók számára az intelligens zárolás konfigurálását.|Igen|Nem|

### Titkosítási beállítások

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Mobileszköz titkosításának kötelezővé tétele**|A mobileszközön található összes fájlnak titkosítva kell lennie.|Igen|Igen|
|**Titkosítás megkövetelése tárolókártyákon**|Ez a beállítás határozza meg, hogy kötelező legyen-e az eszköz tárolókártyájának titkosítása.|Nem|Igen|

### Rendszerbeállítások

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Képernyőfelvétel-készítés használatának engedélyezése**|Engedélyezése esetén a felhasználó rögzítheti képként a képernyőn látható tartalmat.|Nem|Igen|
|**Diagnosztikai adatok küldésének engedélyezése**|Engedélyezése esetén az eszköz diagnosztikai adatokat küld a Google-nak.|Nem|Igen|
|**Gyári beállítások visszaállításának engedélyezése**|A gyári beállítások visszaállításának engedélyezése az eszközön.|Nem|Igen|

### Felhőbeállítások – dokumentumok és adatok

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------------------|----------------|
|**Google biztonsági mentés engedélyezése**|Google-biztonsági mentés engedélyezése.|Nem|Igen|

### Felhőbeállítások – fiókok és szinkronizálás

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Google-fiók automatikus szinkronizálásának engedélyezése**|Google-fiókbeállítások automatikus szinkronizálásának engedélyezése.|Nem|Igen|

### Alkalmazásbeállítások – böngésző

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Webböngésző használatának engedélyezése**|Az eszközön található böngésző használatának engedélyezése.|Nem|Igen|
|**Automatikus kitöltés engedélyezése**|A böngésző Automatikus kitöltés funkciójának engedélyezése.|Nem|Igen|
|**Előugróablak-blokkoló engedélyezése**|A böngésző előugróablak-blokkoló funkciójának engedélyezése.|Nem|Igen|
|**Cookie-k engedélyezése**|Az eszközön található böngésző cookie-használatának engedélyezése.|Nem|Igen|
|**Active Scripting engedélyezése**|Az eszközön található böngésző Active Scripting funkciójának engedélyezése.|Nem|Igen|

### Alkalmazásbeállítások – alkalmazások

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Google Play áruház engedélyezése**|A Google Play Áruház használatának engedélyezése az eszközön.|Nem|Igen|

### Eszközképességek beállításai – hardver

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Kamera használatának engedélyezése**|Engedélyezi az eszköz kamerájának használatát.|Igen|Igen|
|**Cserélhető tároló használatának engedélyezése**|Cserélhető tárolók (például SD-kártya) használatának engedélyezése az eszközön.|Nem|Igen|
|**Wi-Fi használatának engedélyezése**|Az eszköz Wi-Fi-funkciójának engedélyezése.|Nem|Igen|
|**Wi-Fi alapú internetmegosztás használatának engedélyezése**|Az eszköz Wi-Fi-alapú internetmegosztási funkciójának engedélyezése.|Nem|Igen|
|**Földrajzi hely meghatározásának engedélyezése**|Engedélyezi az eszköz számára a helyadatok használatát.|Nem|Igen|
|**NFC használatának engedélyezése**|A kis hatótávolságú kommunikációt használó műveletek engedélyezése (ha az eszköz támogatja ezt a funkciót).|Nem|Igen|
|**Bluetooth használatának engedélyezése**|Az eszköz Bluetooth-funkciójának engedélyezése.|Nem|Igen|
|**Kikapcsolás engedélyezése**|Az eszköz felhasználó általi kikapcsolásának engedélyezése.<br /><br />Ha ez a beállítás le van tiltva, a **Megengedett sikertelen bejelentkezések száma az eszközön tárolt adatok törléséig** beállítás Samsung KNOX-eszközökön nem működik.|Nem|Igen|

### Eszközképességek beállításai – mobilhálózat

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Hangroaming használatának engedélyezése**|Hangroaming használatának engedélyezése, ha az eszköz mobilhálózathoz csatlakozik.|Nem|Igen|
|**Adatroaming használatának engedélyezése**|Adatroaming használatának engedélyezése, ha az eszköz mobilhálózathoz csatlakozik.|Nem|Igen|
|**SMS-/MMS-üzenetküldés engedélyezése**|SMS- és MMS-üzenetek engedélyezése az eszközön.|Nem|Igen|

### Eszközképességek beállításai – szolgáltatások

|Beállítás neve|Részletek|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Hangsegéd engedélyezése**|Hangsegéd szoftverek használatának engedélyezése az eszközön.|Nem|Igen|
|**Hangtárcsázás engedélyezése**|A hangtárcsázási funkció engedélyezése vagy letiltása az eszközön.|Nem|Igen|
|**Másolás és beillesztés használatának engedélyezése**|Az eszköz másolás és beillesztés funkcióinak engedélyezése.|Nem|Igen|
|**Vágólap alkalmazások közötti megosztásának engedélyezése**|Az alkalmazások közötti másoláshoz használja a vágólapot.|Nem|Igen|
|**A YouTube használatának engedélyezése**|A YouTube használatának engedélyezése az eszközön.|Nem|Igen|

### A szabályzatnak megfelelő és nem megfelelő alkalmazásokra vonatkozó beállítások
A **Szabályzatnak megfelelő és nem megfelelő alkalmazások** listában adja meg a kompatibilis vagy nem kompatibilis eszközök listáját az alábbi információk alapján:

> [!NOTE]
> Egy házirendben csak egy, kompatibilis vagy nem kompatibilis alkalmazásokat tartalmazó lista szerepelhet. Mindkét típusú lista nem adható meg ugyanabban a házirendben.

|Beállítás neve|Részletek|
|----------------|--------------------|
|**Meg nem felelésről szóló jelentés küldése, ha a felhasználók telepítik a listán szereplő alkalmazások valamelyikét**|Azokat a nem az Intune által kezelt alkalmazásokat tartalmazza, amelyeket a felhasználók nem telepíthetnek és futtathatnak. Ha a felhasználók ezen alkalmazások egyikét telepítik, szerepelni fog a szabályzatoknak nem megfelelő alkalmazásokról készült jelentésben.|
|**Meg nem felelés jelentésének mellőzése, ha a felhasználók telepítik a listán szereplő alkalmazások valamelyikét**|Azokat az alkalmazásokat tartalmazza, amelyek használatát engedélyezi a vállalatnál. A megfelelőség biztosítása érdekében a felhasználók nem telepíthetnek olyan alkalmazásokat, amelyek nem szerepelnek a listán. Az Intune által kezelt alkalmazások automatikusan engedélyezettek.|
|**Hozzáadás**|Hozzáadhat egy alkalmazást a kijelölt listához. Meg kell adnia egy szabadon választott nevet, valamint tetszés szerint megadhatja az alkalmazás kiadóját, valamint az alkalmazás alkalmazás-áruházbeli URL-címét.<br /><br />További segítségért olvassa el az ebben a témakörben alább található Alkalmazás-áruházak URL-címének megadása című részt.|
|**Alkalmazások importálása**|Importálhatja azokat az alkalmazásokat, amelyeket egy vesszővel tagolt fájlban megadott. Használja a fájlban megadott formátumot, alkalmazásnevet, kiadót és URL-címet.|
|**Szerkesztés**|Segítségével szerkesztheti a kijelölt alkalmazás nevét, kiadóját és URL-címét.|
|**Törlés**|Törölheti a kijelölt alkalmazást a listából.|

### Teljes képernyős mód beállításai
Adja meg a következő értékeket a **Samsung KNOX**-eszközök beállításhoz:

|Beállítás neve|Részletek|
|----------------|--------------------|
|**Az eszköz Kioszk módjában futtatható kezelt alkalmazás kiválasztása**|Válassza a **Tallózás** elemet, majd válassza ki a felügyelt alkalmazást, amelynek engedélyezni szeretné, hogy az eszköz kioszkmódban is futtassa (az áruházra mutató hivatkozásként megadott alkalmazások jelenleg nem támogatottak). Az itt megadotton kívül más alkalmazás nem futtatható az eszközön.|
|**Hangerőszabályzó gombok engedélyezése**|Engedélyezheti vagy letilthatja a hangerőszabályzó gombok használatát az eszközön.|
|**Képernyő ébresztőgombjának engedélyezése**|Engedélyezheti vagy letilthatja a képernyő ébresztőgombját az eszközön.|

### A szabályzatnak megfelelő és nem megfelelő alkalmazások referenciaadatai

#### A szabályzatnak megfelelő és nem megfelelő alkalmazások figyelése
A **Nem kompatibilis alkalmazások jelentése** beállítás használatával megtekintheti az engedélyezett és letiltott alkalmazások kompatibilitását.

###### A nem kompatibilis alkalmazások jelentésének futtatása

1.  A [Microsoft Intune felügyeleti konzolban](https://manage.microsoft.com) válassza a **Jelentések** &gt; **Jelentés a szabályzatnak nem megfelelő alkalmazásokról** elemet.

2.  Jelölje ki az ellenőrizni kívánt eszközcsoportokat, adja meg, hogy a kompatibilis vagy a nem kompatibilis alkalmazásokat szeretné-e ellenőrizni, illetve mindkettőt, majd válassza a **Jelentés megtekintése**elemet.

#### Alkalmazás-áruházak URL-címének megadása
Ha meg szeretné adni egy alkalmazás URL-címét a szabályzatnak megfelelő és nem megfelelő alkalmazások listájában, használja a következő formátumot:

A [Google Play Alkalmazások szakaszában](https://play.google.com/store/apps) keresse meg a használni kívánt alkalmazást.

Nyissa meg az alkalmazás telepítési lapját, és másolja az URL-címet a vágólapra. Most ezt a címet felhasználhatja URL-címként a kompatibilis vagy a nem kompatibilis alkalmazások listájában.

**Például:** Keressen rá a Google Play-ben a Microsoft Office Mobile kifejezésre. A használt URL-cím a következő: **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## Egyéni szabályzatbeállítások
A Microsoft Intune **Android egyéni konfigurációs házirenddel** OMA-URI-beállításokat telepíthet, melyekkel vezérelhetők az Android-eszközökön elérhető szolgáltatások. Ezek szabványos beállítások, amelyeket számos mobileszköz-gyártó alkalmaz az eszközök szolgáltatásainak vezérlésére.

Ezzel a képességgel olyan Android-beállításokat telepíthet, amelyek nem konfigurálhatók Intune-szabályzatokkal.

> [!NOTE]
> Jelenleg az egyéni Android-házirendek csak az előmegosztott kulcsot tartalmazó Android-eszközök Wi-Fi beállításainak konfigurálását támogatják.

### Általános beállítások

|Beállítás neve|Részletek|
    |----------------|--------------------|
    |**Név**|Adjon egyedi nevet az egyéni Android-szabályzatnak, hogy az azonosítható legyen az Intune konzolján.|
    |**Leírás**|Adjon meg egy leírást, amely áttekintést nyújt az Android egyéni szabályzatáról, és olyan releváns információkat tartalmaz, amelyek megkönnyítik a keresését.|

### OMA-URI-beállítások

   |Beállítás neve|Részletek|
    |--------|--------------------|
    |**Beállítás neve**|Adjon meg egy egyedi nevet az OMA-URI beállítás számára, amellyel az egyszerűen azonosítható a beállítások listájában.|
    |**Beállítás leírása**|Adjon meg egy olyan leírást, amely áttekintést nyújt az adott beállításról, valamint más olyan releváns információkat tartalmaz, amelyek segítenek a megkeresésében.|
    |**Adattípus**|Válassza ki a dátumtípust, amelyben meg szeretné adni ezt az OMA-URI beállítást. Válassza a **Karakterlánc, Karakterlánc (XML), Dátum és időpont, Egész szám, Lebegőpontos szám** vagy **Logikai** lehetőséget.|
    |**OMA-URI (megkülönbözteti a kis- és nagybetűket)**|Adja meg az OMA-URI azonosítót, amelyhez beállítást kíván megadni.|
    |**Érték**|Adja meg a korábban megadott OMA-URI azonosítóhoz társítandó értéket.|

### Példa: Egyéni Wi-Fi profil konfigurálása előmegosztott kulccsal
Bár az Intune támogatja az Android-eszközök Wi-Fi-profiljait, ez a szolgáltatás jelenleg nem támogatja az előmegosztott kulcs használatát a konfigurációban. Ebből a példából megtudhatja, hogyan hozhat létre előmegosztott kulcsot használó Wi-Fi profilt létrehozó egyéni Android-házirendet az Android-eszközön.

#### Wi-Fi profil létrehozása előmegosztott kulccsal

1.  Győződjön meg arról, hogy a felhasználók az Android rendszerhez készült [Intune Vállalati portál alkalmazás](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) legújabb verzióját használják.

2.  Hozzon létre egy egyéni Android-házirendet, és vegye fel a következő beállításokat:

|Beállítás neve|Részletek|
|----------------|--------------------|
|**Beállítás neve**|Adja meg a beállítás kívánt nevét.|
|**Beállítás leírása**|Adja meg a jelentés leírását.|
|**Adattípus**|Válassza a **Karakterlánc (XML)** lehetőséget.|
|**OMA-URI**|Írja be a következőket: ./Vendor/MSFT/WiFi/Profile/*&lt;a Wi-Fi profilja&gt;*/Settings|

3.  Az **Érték** mezőbe másolja és illessze be a következő XML-kódot:

    ```
    <!--
    WEP Wifi Profile
                    <Name of wifi profile> = Name of profile 
                    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
                    <WEP password> = Password to connect to the network
    -->
    <WLANProfile 
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <name><SSID of wifi profile></name>
        </SSID>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <MSM>
        <security>
          <authEncryption>
            <authentication>open</authentication>
            <encryption>WEP</encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial><WEP password></keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>
    ```

4.  Amikor végzett, mentse a házirendet, és telepítse azt a szükséges Android-eszközökre. Az új Wi-Fi profil megjelenik a kapcsolatok listájában az eszközön.

### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


