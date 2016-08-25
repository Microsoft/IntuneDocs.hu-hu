---
title: "Windows 10-es házirend-beállítások | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.sourcegitcommit: 1cccafa5f740bad50779ae36c899fd23ee7dc5f3
ms.openlocfilehash: 70347776f72a3534a4c384957aef01a909767b99


---

# Windows 10-es házirend-beállítások a Microsoft Intune-ban

A jelen témakörben felsorolt házirend-beállításokkal konfigurálhatja a Windows 10 asztali verziót vagy Windows 10 Mobile-t használó regisztrált eszközökön.

## Az általános konfigurációs szabályzat beállításai

A Microsoft Intune Windows 10-eszközökhöz készült **általános konfigurációs szabályzatát** regisztrált asztali Windows 10- és Windows 10 Mobile-eszközökhöz használhatja. Ez a szabályzat nem használható, ha a Windows 10 rendszerű számítógépek kezelése Intune ügyfélszoftverrel történik.


### Jelszó

|Beállítás neve|Részletek|
|----------------|----------------------|
|**Jelszó kérése az eszközzárolás feloldásához**|Jelszó kérése a támogatott eszközökön.|
|**Kötelező jelszótípus**|Meghatározza a megkövetelt jelszótípust, például hogy a jelszó csak számokat, vagy számokat és betűket is tartalmazhat|
|**Kötelező jelszótípus** - **Karakterkészletek minimális száma**|A következő négy karakterkészlet létezik: kisbetűk, nagybetűk, számok és szimbólumok. Ez a beállítás azt határozza meg, hány különböző karakterkészletnek kell szerepelnie a jelszóban.|
|**Jelszó minimális hossza**|Az eszközjelszóban használandó karakterek minimális számát határozza meg.<br>(csak a Windows 10 Mobile)|
|**Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt**|A megadott számú sikertelen bejelentkezési kísérlet után törli az eszközt.|
|**Képernyő kikapcsolása ennyi perc inaktivitás után**|Meghatározza, hogy az eszköznek mennyi ideig kell tétlennek lennie a képernyő zárolása előtt.|
|**Jelszó lejárata (nap)**|Meghatározza, hogy mennyi idő elteltével kell módosítani a jelszót.|
|**Jelszóelőzmények megjegyzése**|Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.|
|**Korábbi jelszavak megjegyzése** - **Korábbi jelszavak újbóli használatának tiltása**|Ez a beállítás a eszköz által megjegyzett korábbi jelszavak számát határozza meg.|
|**Képjelszó és PIN-kód engedélyezése**|Lehetővé teszi egy képen egyszerű kézmozdulatok, vagy egy egyszerű PIN-kód használatát a bejelentkezéshez.<br>(csak a Windows 10 asztali verzió)|
|**Jelszó kérése, amikor az eszköz visszatér inaktív állapotból**|Engedélyezése esetén a felhasználónak meg kell adnia egy jelszót, ha szeretné feloldani az inaktív állapotú eszköz zárolását.<br>(csak a Windows 10 Mobile)|

### Titkosítás

|Beállítás neve|Részletek|
|----------------|----------------------|
|**Mobileszköz titkosításának kötelezővé tétele**|Aktiválja a titkosítást a megcélzott eszközökön.<br>(csak a Windows 10 Mobile)|

### Rendszer

|Beállítás neve|Részletek|
|----------------|----------------------|
|**Képernyőfelvétel-készítés használatának engedélyezése**|Engedélyezése esetén a felhasználó rögzítheti képként a képernyőn látható tartalmat.<br>(csak a Windows 10 Mobile)|
|**Regisztráció manuális törlésének engedélyezése**|Lehetővé teszi a felhasználó számára a munkahelyi fiók manuális törlését az eszközről.|
|**Főtanúsítvány manuális telepítésének engedélyezése**|Meghatározza, hogy a felhasználó telepíthet-e manuálisan főtanúsítványokat.<br>(csak a Windows 10 Mobile)|
|**Diagnosztikai és használati adatok küldésének engedélyezése a Microsoft felé**|Meghatározza, hogy az eszközök mennyi diagnosztikai és használati adatot küldjenek a Microsoftnak.<br><br>**Nem** – Az eszköz nem küld adatokat a Microsoftnak.<br>**Alapszintű** – Az eszköz csak korlátozott mennyiségű információt küld a Microsoftnak.<br>**Bővített** – Az eszköz bővebb diagnosztikai adatokat küld a Microsoftnak.<br>**Teljes (ajánlott)** – A **Bővített** beállítással küldött adatok mellett az eszköz állapotával kapcsolatos információkat is küld.|


### Fiók és szinkronizálás

|Beállítás neve|Részletek|
|----------------|----------------------|---------------------|
|**Microsoft-fiók használatának engedélyezése**|Lehetővé teszi, hogy a felhasználó Microsoft-fiókot társítson az eszközhöz.|
|**Nem Microsoft-fiókok manuális felvételének engedélyezése**|Lehetővé teszi, hogy a felhasználó olyan e-mail fiókokat vegyen fel az eszközön, amelyek nincsenek Microsoft-fiókhoz társítva.|
|**Beállítások szinkronizálásának engedélyezése Microsoft-fiók esetén**|Lehetővé teszi a Microsoft-fiókhoz kapcsolódó eszköz- és alkalmazásbeállítások szinkronizálását az eszközök között.|

### E-mail beállítások

|Beállítás neve|Részletek|
|----------------|----------------------|---------------------|
|**A Microsoft-fiók opcionálissá tétele a Windows Mail alkalmazásban**|A beállítás engedélyezése esetén nem kötelező Microsoft-fiókot használni a Windows Posta alkalmazásban.<br>Csak a Windows 10 asztali verzió|



### Microsoft Edge

|Beállítás neve|Részletek|
|----------------|----------------------|
|**Webböngésző használatának engedélyezése**|Engedélyezi az Edge webböngésző használatát az eszközön.<br>(csak a Windows 10 Mobile)|
|**Keresési javaslatok engedélyezése a címsorban**|Lehetővé teszi, hogy a keresőmotor webhelyeket javasoljon a keresőkifejezések beírása közben.|
|**Intranetes adatforgalom küldésének engedélyezése az Internet Explorerbe**|Engedélyezi a felhasználók számára az intranetes webhelyek megnyitását az Internet Explorerben.<br>(csak a Windows 10 asztali verzió)|
|**Követés letiltásának engedélyezése**|Lehetővé teszi az Edge böngésző számára a Do Not Track (Követés letiltása) fejlécek küldését a felhasználók által meglátogatott webhelyeknek.|
|**SmartScreen engedélyezése**|Aktiválja a SmartScreen böngészőbeállítást az eszközökön.|
|**Active Scripting engedélyezése**|A parancsprogramok, például a JavaScriptek futtatásának engedélyezése az Edge böngészőben.|
|**Előugró ablakok engedélyezése**|A böngésző előugróablak-blokkolójának engedélyezése vagy letiltása.<br>(csak a Windows 10 asztali verzió)|
|**Cookie-k engedélyezése**|A cookie-k engedélyezésére vagy letiltására szolgál.|
|**Automatikus kitöltés engedélyezése**|Engedélyezi a felhasználók számára a böngésző automatikus kiegészítési funkciója beállításainak módosítását.<br>(csak a Windows 10 asztali verzió)|
|**Jelszókezelő engedélyezése**|Az Edge böngésző Jelszókezelő szolgáltatásának engedélyezése vagy letiltása.|
|**Vállalati üzemmód webhelylistájának helye**|Megadja, hogy hol található a Vállalati üzemmódban megnyitott webhelyek listája. Ezt a listát a felhasználók nem szerkeszthetik.<br>(csak a Windows 10 asztali verzió)|

### Alkalmazások

|Beállítás neve|Részletek|
|----------------|----------------------|---------------------|
|**Alkalmazástároló használatának engedélyezése**|Az alkalmazás-áruház használatának engedélyezése az eszközön.<br>(csak a Windows 10 Mobile)|



### Mobil

|Beállítás neve|Részletek|
|----------------|----------------------|---------------------|
|**Adatroaming használatának engedélyezése**|Hálózatok közötti barangolás engedélyezése adatok elérése közben.|
|**VPN engedélyezése mobilhálózaton**|Azt szabályozza, hogy az eszköz létesíthet-e VPN-kapcsolatot mobilhálózat használata esetén.|
|**VPN engedélyezése mobilhálózati roaming esetén**|Azt szabályozza, hogy az eszköz létesíthet-e VPN-kapcsolatot mobilhálózati roaming esetén.|

### Hardver

|Beállítás neve|Részletek|
|----------------|----------------------|
|**Kamera használatának engedélyezése**|A beállítás meghatározza, hogy használható-e az eszközön a kamera.|
|**Cserélhető tároló használatának engedélyezése**|Meghatározza, hogy az eszközzel használható-e külső tárolóeszköz, például SD-kártya.|
|**Wi-Fi használatának engedélyezése**|Az eszköz Wi-Fi funkciójának engedélyezése.<br>(csak a Windows 10 Mobile)|
|**Internetmegosztás engedélyezése**|Az internetmegosztás engedélyezése az eszközön.|
|**Manuális Wi-Fi konfiguráció engedélyezése**|Azt szabályozza, hogy a felhasználó konfigurálhat-e saját Wi-Fi kapcsolatokat, vagy csak a Wi-Fi profillal konfigurált kapcsolatokat használhatja.<br>(csak a Windows 10 Mobile)|
|**Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése**|Az ingyenes Wi-Fi elérési pontokhoz történő automatikus csatlakozás és a kapcsolódáshoz szükséges használati feltételek automatikus elfogadásának engedélyezése az eszközön.|
|**Földrajzi hely meghatározásának engedélyezése**|Meghatározza, hogy az eszköz használhatja-e a helyalapú szolgáltatások adatait.|
|**NFC használatának engedélyezése**|Engedélyezi az eszköz kis hatótávolságú kommunikációs (NFC) funkciójának használatát.|
|**Bluetooth használatának engedélyezése**|Engedélyezi a Bluetooth-képességek használatát az eszközön.|
|**Bluetooth-észlelhetőség engedélyezése**|Észlelhetővé teszi az eszközt más Bluetooth-kompatibilis eszközök által.|
|**Bluetooth-hirdetés engedélyezése**|Engedélyezi, hogy az eszközök hirdetéseket fogadjanak Bluetooth-on keresztül.|
|**Bluetooth-csatlakozási üzemmód engedélyezése**|**Fontos:** ez a beállítás a Windows 10 rendszerben már nem támogatott, és a jövőben meg fog szűnni.|
|**Telefon alaphelyzetbe állításának engedélyezése**|Azt szabályozza, hogy a felhasználó visszaállíthatja-e az eszköz gyári beállításait.|
|**USB-kapcsolat engedélyezése**|Azt szabályozza, hogy az eszközök elérhetnek-e külső tárolóeszközöket USB-kapcsolaton keresztül.|
|**Lopásgátló üzemmód engedélyezése**|Annak beállítása, hogy engedélyezve van-e a Windows lopásgátló üzemmódja.|

### Jellemzők

|Beállítás neve|Részletek|
|----------------|----------------------|---------------------|
|**Másolás és beillesztés használatának engedélyezése**|A másolás és beillesztés engedélyezése vagy letiltása az eszközön.<br>(csak a Windows 10 Mobile)|
|**Hangrögzítés engedélyezése**|Az eszköz hangrögzítési funkciói használatának engedélyezése vagy letiltása.<br>(csak a Windows 10 Mobile)|
|**A Cortana engedélyezése**|A Cortana beszédfelismerési asszisztens engedélyezése vagy letiltása.|
|**Műveletközponti értesítések engedélyezése**|Műveletközponti értesítések engedélyezése vagy letiltása az eszköz zárolási képernyőjén.<br>(csak a Windows 10 Mobile)|

### Defender

Ezek a beállítások csak a Windows 10 asztali verziójában érvényesek.

|Beállítás neve|Részletek|
|-|-|
|**Valós idejű figyelés engedélyezése**|Engedélyezi a kártevők, kémprogramok és más nemkívánatos szoftverek valós idejű vizsgálatát.|
|**Viselkedésfigyelés engedélyezése**|Engedélyezi, hogy a Defender gyanús tevékenységekre utaló ismert mintákat keressen az eszközökön.|
|**Hálózatfelügyeleti rendszer engedélyezése**|A hálózatvizsgáló rendszer (NIS) a Microsoft Endpoint Protection-központtól származó ismert biztonsági rések aláírásai alapján észleli és blokkolja a kártékony hálózati forgalmat, ezáltal segíti az eszközök védelmét a hálózati támadásokkal szemben.|
|**Minden letöltött fájl vizsgálata**|Meghatározza, hogy a Defender az internetről letöltött összes fájlt megvizsgálja-e.|
|**Szkriptek ellenőrzésének engedélyezése**|Engedélyezi a Defender számára az Internet Explorer által használt parancsfájlok vizsgálatát.|
|**A fájl- és programtevékenység figyelése**|Engedélyezése esetén a Defender megfigyelheti a fájl- és programtevékenységet az eszközökön.|
|**Ártalmatlanított kártevő szoftverek követése (nap)**|A megadott számú napig engedélyezi a Defender számára az ártalmatlanított kártevők további követését a korábban érintett eszközök manuális ellenőrzése céljából. Ha a napok számát **0**-ra állítja, a kártevő a karanténban marad, és a rendszer nem távolítja el automatikusan. |
|**Ügyfél-kezelőfelület elérésének engedélyezése**|Azt szabályozza, hogy a Windows Defender kezelőfelülete rejtett legyen-e a végfelhasználók számára.<br>Módosítás esetén a beállítás a végfelhasználó számítógépének következő újraindításakor lép érvénybe.|
|**Napi gyors vizsgálat ütemezése**|Minden nap a választott időben végzett gyorsvizsgálat beütemezését teszi lehetővé.|
|**Rendszervizsgálat ütemezése**|A választott napokon és időpontban rendszeresen végzett teljes vagy gyors rendszervizsgálat beütemezését teszi lehetővé.|
|**CPU-használatát korlátozása a vizsgálatok alatt**|Lehetővé teszi a vizsgálatok processzorhasználatának korlátozását (**1**%-tól **100**%-ig).|
|**Archív fájlok vizsgálata**|Engedélyezi a Defender számára az archív fájlok – például ZIP- vagy CAB-fájlok – vizsgálatát.|
|**E-mail üzenetek vizsgálata**|Engedélyezi a Defender számára az eszközre érkező e-mailek azonnal vizsgálatát.|
|**Cserélhető adathordozók vizsgálata**|Engedélyezi a Defender számára a cserélhető meghajtók, például a pendrive-ok vizsgálatát.|
|**Csatlakoztatott hálózati meghajtók vizsgálata**|Engedélyezi a Defender számára a csatlakoztatott hálózati meghajtókon tárolt fájlok vizsgálatát.<br>Ha a meghajtón található fájlok írásvédettek, a Defender nem képes eltávolítani a bennük talált kártevőket.|
|**Hálózati megosztott mappákból megnyitott fájlok vizsgálata**|Engedélyezi a Defender számára a megosztott hálózati meghajtókon található (például az UNC elérési útvonalon megnyitott) fájlok vizsgálatát.<br>Ha a meghajtón található fájlok írásvédettek, a Defender nem képes eltávolítani a bennük talált kártevőket.|
|**Aláírás-frissítési időköz**|Meghatározza, hogy a Defender milyen időközönként keressen új aláírásfájlokat.|
|**Felhővédelem engedélyezése**|Engedélyezi vagy letiltja, hogy a rendszer adatokat küldjön a Microsoft Active Protection Service számára a felügyelt eszközökön észlelt kártevőkről. Ezek az adatok a szolgáltatás további fejlesztésére szolgálnak.|
|**Minták küldésének kérése a felhasználóktól**|Azt szabályozza, hogy a rendszer automatikusan elküldje a Microsoftnak azokat a fájlokat, amelyeken további vizsgálat szükséges annak megállapításához, hogy kártékonyak-e.|
|**Vélhetően nem kívánatos alkalmazások észlelése**|Ezzel a beállítással biztosíthatja a regisztrált Windows rendszerű asztali számítógépek védelmét a Windows Defender által a vélhetően nemkívánatos osztályba sorolt szoftverek futtatása ellen. Biztosíthatja a védelmet ezen alkalmazások futtatása ellen, vagy a vizsgálati üzemmóddal jelentést készíthet a vélhetően nemkívánatos alkalmazások telepítéséről.|
|**A vizsgálatok futtatásakor vagy a valós idejű védelem használatakor kizárandó fájlok és mappák**|Vegye fel a kívánt fájlokat és mappákat – például **C:\Elérési_út** vagy **%ProgramFiles%\Elérési_út\fájlnév.exe** – a kivételek listájára. A rendszer a valós idejű és ütemezett vizsgálatok során nem vizsgálja ezeket a fájlokat és mappákat.|
|**A vizsgálatok futtatásakor vagy a valós idejű védelem használatakor kizárandó fájlkiterjesztések**|Vegye fel a kívánt fájlkiterjesztéseket – például **jpg** vagy **txt** – a kivételek listájára. A rendszer a valós idejű és ütemezett vizsgálatok során nem vizsgálja az ilyen kiterjesztésű fájlokat.|
|**A vizsgálatok futtatásakor vagy a valós idejű védelem használatakor kizárandó folyamatok**|Vegye fel a kívánt típusú folyamatokat – **.exe**, **.com** vagy **.scr** – a kivételek listájára. A rendszer a valós idejű és ütemezett vizsgálatok során nem vizsgálja ezeket a folyamatokat.| 


### Frissítések beállításai

|Beállítás neve|Részletek|
|----------------|---------------|
|**Automatikus frissítések engedélyezése**|A beállítás engedélyezésével engedélyezheti az automatikus frissítéseket. Ezt követően a következő lehetőségek egyikének beállításával szabályozhatja a frissítések működését:<br /><br />**Értesítést kérek a letöltésről**<br /><br />**Automatikus telepítés karbantartási időpontban**<br /><br />**Automatikus telepítés és újraindítás karbantartási időpontban**<br /><br />**Automatikus telepítés és újraindítás ütemezett időpontban** **Megjegyzés:** Kiválasztása esetén a következő beállítások konfigurálása is lehetővé válik: **Végfelhasználói értesítések letiltása**, illetve **Adja meg az ütemezett frissítések telepítésének napját**.<br>(csak a Windows 10 asztali verzió)|

## Egyéni szabályzatbeállítások
A Microsoft Intune Windows 10-hez és a Windows 10 Mobile-hoz készült **egyéni konfigurációs házirendjeivel** OMA-URI beállítások telepíthetők, amelyek a Windows 10- és Windows 10 Mobile-eszközökön elérhető szolgáltatások vezérlésére használhatók. Ezek szabványos beállítások, amelyeket számos mobileszköz-gyártó alkalmaz az eszközök szolgáltatásainak vezérlésére.

E funkció révén olyan Windows 10-beállításokat léptethet érvénybe, amelyek nem konfigurálhatók az Intune általános konfigurációs házirendjével.



### Egyéni házirendek általános beállításai

|Beállítás neve|Részletek|
    |----------------|--------------------|
    |**Név**|Adjon meg egy egyedi nevet a házirend számára, hogy azonosítható legyen az Intune konzolján.|
    |**Leírás**|Adjon meg egy olyan leírást, amely áttekintést nyújt a szabályzatról, valamint más olyan releváns információkat tartalmaz, amelyek segítenek megkeresésében.|

### Egyéni házirendek OMA-URI-beállításai

|Beállítás neve|Részletek|
    |--------|--------------------|
    |**Beállítás neve**|Adjon meg egy egyedi nevet az OMA-URI beállítás számára, amellyel az egyszerűen azonosítható a beállítások listájában.|
    |**Beállítás leírása**|Adjon meg egy olyan leírást, amely áttekintést nyújt az adott beállításról, valamint más olyan releváns információkat tartalmaz, amelyek segítenek a megkeresésében.|
    |**Adattípus**|Válassza ki a dátumtípust, amelyben meg szeretné adni ezt az OMA-URI beállítást. A következő lehetőségek közül választhat:<br /><br />-   **Karakterlánc**<br />-   **Karakterlánc (XML)**<br />-   **Dátum és időpont**<br />-   **Egész szám**<br />-   **Lebegőpontos szám**<br />-   **Logikai**|
    |**OMA-URI (megkülönbözteti a kis- és nagybetűket)**|Adja meg az OMA-URI azonosítót, amelyhez beállítást kíván megadni.|
    |**Érték**|Adja meg a korábban megadott OMA-URI azonosítóhoz társítandó értéket.|


## Windows 10-eszközök egyéni URI-beállításai
Ez a témakör a Microsoft Intune **egyéni Windows 10-házirendjeiben** konfigurálható beállításokat sorolja fel Windows 10- és Windows 10 Mobile-eszközökhöz.

Az összes eszköznek regisztrálva kell lennie az Intune-ban, ha használni kívánja az egyéni Windows URI-házirendet.

### Házirendek URI-beállításai

|Házirend neve|Részletek|
|---------------|------------|-----------|
|**​Automatikus frissítés engedélyezése**<br>(csak asztali verziók)|**URI teljes elérési útja**: ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** - **5** (alapértelmezés: **1**)|
|**Telepítés napjának ütemezése**<br>(csak mobil)|**URI teljes elérési útja**: ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – minden nap (alapértelmezés)<br>**1** – vasárnap<br>**2** – hétfő<br>**3** – kedd<br>**4** – szerda<br>**5** – csütörtök<br>**6** – péntek<br>**7** – szombat|
|**Telepítés időpontjának ütemezése**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja**: ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – **23** óra (**0**: éjfél) (alapértelmezés: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>(csak mobil)|**URI teljes elérési útja**: ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – a felhasználó nem állíthatja be a jelszó türelmi idejének időzítőjét, és az érték „minden alkalommal” lesz<br>**1** – a felhasználó beállíthatja a jelszó türelmi idejének időzítőjét (alapértelmezés)|
|**WiFi/AllowWiFi**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nem engedélyezi a **Wi-Fi kapcsolat használatát**.<br>**1** – **Engedélyezi a Wi-Fi kapcsolat használatát** (alapértelmezés).|
|**WiFi/AllowInternetSharing**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nem engedélyezi az Internetmegosztást.<br>**1** – Engedélyezi az internetmegosztást (alapértelmezés).|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**WiFi/AllowManualWiFiConfiguration**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Az MDM által kiépítettektől eltérő Wi-Fi kapcsolatok nem engedélyezettek.<br>**1** – Az MDM által kiépítettektől eltérő hálózati SSID-k hozzáadása engedélyezett (alapértelmezés).|
|**System/AllowLocation**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**System/AllowTelemetry**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nem engedélyezett (csak Enterprise rendszerekre vonatkozó beállítás)<br>**1** – Korlátozott<br>**2** – Teljes (alapértelmezés)<br>**3** – Teljes és diagnosztikai információk|
|**System/AllowExperimentation**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nem engedélyezett<br>**1** – Csak beállítások (alapértelmezés)<br>**2** – Beállítások és kísérletezés|
|**Security/AntiTheftMode**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Lopásgátló üzemmód tiltása<br>**1** – Felhasználói beállítás szerint (alapértelmezés)|
|**Connectivity/AllowUSBConnection**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**System/AllowUserToResetPhone**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Connectivity/AllowCellularDataRoaming**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Connectivity/AllowVPNOverCellular**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – VPN tiltása mobileszközökön<br>**1** – A VPN bármilyen kapcsolatot használhat, beleértve a mobilkapcsolatot is (alapértelmezés)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Connectivity/AllowBluetooth**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nem engedélyezi a felhasználónak a Bluetooth aktiválását.<br>**1** – Fenntartva. A Bluetooth bekapcsolásának és konfigurálásának engedélyezése a felhasználónak (nem támogatott Windows Phone 8.1 MDM, EAS, a Windows 10 asztali verziója és Windows 10 Mobile esetén).<br>**2** – Engedélyezett. A Bluetooth bekapcsolásának és konfigurálásának engedélyezése a felhasználónak (alapértelmezés)|
|**Experience/AllowScreenCapture**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Experience/AllowTaskSwitcher**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Experience/AllowVoiceRecording**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Experience/AllowSyncMySettings**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Roaming tiltása<br>**1** – Roaming engedélyezése (alapértelmezés)|
|**Experience/AllowManualMDMUnenrollment**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Accounts/AllowMicrosoftAccountConnection**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Security/AllowManualRootCertificateInstallation**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Security/AllowAddProvisioningPackages**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Search/DisableBackoff**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** (alapértelmezés)<br>**1**|
|**Search/PreventRemoteQueries**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**<br>**1** (alapértelmezés)|
|**Search/AllowUsingDiacritics**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br> **0** (alapértelmezés)<br>**1**|
|**Search/AlwaysUseAutoLangDetection**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** (alapértelmezés)<br>**1**|
|**Search/DisableRemovableDriveIndexing**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** (alapértelmezés)<br>**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**<br>**1** (alapértelmezés)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** (alapértelmezés)<br>**1**|
|**Security/AllowRemoveProvisioningPackage**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Security/RequireProvisioningPackageSignature**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** (alapértelmezés)<br>**1**|
|**AboveLock/AllowActionCenterNotifications**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**TextInput/AllowIMENetworkAccess**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nem engedélyezett<br>A nyílt kiterjesztett szótár ki van kapcsolva.<br>A felhasználók nem tehetik a következőket:<br>Új nyílt kiterjesztett szótár felvétele<br /><br />Új keresésintegrációs konfigurációs fájl felvétele<br>A felhőben való használatra jelölt szolgáltatás használata<br>Felhasználó által regisztrált szó küldése<br>Egyéb rendelkezések:<br>A házirend-beállítás engedélyezése előtt felvett nyílt kiterjesztett szótárak nem lesznek felhasználva az átalakításhoz.<br>A házirend jóváhagyása előtt telepített keresésintegrációs konfigurációs fájl nincs használatban.<br>**1** – Engedélyezés<br>A nyílt kiterjesztett könyvtár alapértelmezés szerint felvehető és használható. A keresésintegráció funkció is alapértelmezés szerint használható.<br>A felhasználó a következőket teheti:<br>A felhőben való használatra jelölt szolgáltatás használata<br>Felhasználó által regisztrált szó küldése.|
|**TextInput/AllowIMELogging**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – A helytelen átalakítások naplózása ki van kapcsolva. Az automatikusan beállított és a bemeneti előzményadatok nincsenek fájlba mentve.<br>**1** – A helytelen átalakítások naplózása be van kapcsolva. Az automatikusan beállított és a bemeneti előzményadatok fájlba mentése (alapértelmezés)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**TextInput/AllowJapaneseIVSCharacters**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**TextInput/AllowJapaneseUserDictionary**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Egyetlen karakter sincs szűrve (alapértelmezés)<br>**1** – A Shift JIS-karakterek kivételével minden karaktert szűr a rendszer|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br /><br />**0** – Egyetlen karakter sincs szűrve (alapértelmezés)<br>**1** – A JIS0208-karakterek kivételével minden karaktert szűr a rendszer|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Egyetlen karakter sincs szűrve (alapértelmezés)<br>**1** – A JIS0208- és az EUDC-karakterek kivételével minden karaktert szűr a rendszer|
|**TextInput/AllowInputPanel**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Bluetooth/AllowDiscoverableMode**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Bluetooth/AllowAdvertising**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowDataSense**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowVPN**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowWorkplace**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowDateTime**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowLanguage**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowRegion**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowSignInOptions**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowYourAccount**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowPowerSleep**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Settings/AllowAutoPlay**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Experience/AllowCortana**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Search/SafeSearchPermissions**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Felnőtt tartalom szigorú, legmagasabb fokú szűrése<br>**1** – Felnőtt tartalom mérsékelt, közepes szintű szűrése (az érvényes keresési eredményeket nem szűri a rendszer – alapértelmezés)|
|**Experience/AllowCopyPaste**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**Kezdőméret kényszerítése**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – méretmódosítás engedélyezése a felhasználó számára (alapértelmezés)<br>**1** – nem teljes képernyő kényszerítése<br>**2** – teljes képernyő kényszerítése|
|**Update/RequireDeferUpgrade**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**: A frissítés késleltetésének mellőzése (maradás az aktuális fejlesztési ágban (CB) – alapértelmezés)<br>**1**: A frissítések késleltetésének engedélyezése (az eszköz az aktuális üzleti ág (CBB) szabályait követi)<br /><br />További információkért lásd:<br>[Bevezetés a Windows 10 karbantartásába](https://technet.microsoft.com/library/mt598226.aspx)<br>[Felkészülés a Windows 10 központi telepítésére](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>(az asztali és mobilos verzióknál egyaránt)|**Leírás:** A szoftverfrissítéseket 4 héttel késleltető házirend.<br /><br />**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br> **0**: A frissítések azonnali alkalmazása (alapértelmezett)<br>**1**-**4**: a rendszer ennyi héttel késlelteti a szoftverfrissítéseket.<br /><br />További információkért lásd:<br>[Bevezetés a Windows 10 karbantartásába](https://technet.microsoft.com/library/mt598226.aspx)<br>[Felkészülés a Windows 10 központi telepítésére](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>(az asztali és mobilos verzióknál egyaránt)|**Leírás:** A funkciófrissítéseket 8 hónappal késleltető házirend.<br /><br />**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**: A frissítések azonnali alkalmazása (alapértelmezett)<br>**1**-**8**: a rendszer ennyi hónappal késlelteti a funkciófrissítéseket.<br /><br />További információkért lásd:<br>[Bevezetés a Windows 10 karbantartásába](https://technet.microsoft.com/library/mt598226.aspx)<br>[Felkészülés a Windows 10 központi telepítésére](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>(az asztali és mobilos verzióknál egyaránt)|**Leírás:** Lehetővé teszi a CBB-gépeknek a frissítések letöltésének leállítását 5 hétre. Ezt akkor kell használni, ha probléma van a frissítéssel.<br /><br />**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**: A frissítések azonnali alkalmazása (alapértelmezett)<br>**1**: A frissítések és verziófrissítések szüneteltetése (5 hét után lejár)|

### A Windows Defender URI-beállításai

|Házirend neve|Részletek|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**AllowBehaviorMonitoring**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**AllowIntrusionPreventionSystem**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**AllowIOAVProtection**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**AllowScriptScanning**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**AllowOnAccessProtection**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**RealTimeScanDirection**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Minden fájl figyelése (kétirányú – alapértelmezés)<br>**1** – Bejövő fájlok figyelése<br>**2** – Kimenő fájlok figyelése|
|**DaysToRetainCleanedMalware**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** - **90** – Megadja, hogy a kártevő szoftvereket mennyi ideig őrizze a rendszer<br>**Alapértelmezett érték:** **0** – Végleg a karantén mappában tartja, automatikusan nem távolítja el|
|**AllowUserUIAccess**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**ScanParameter**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**1** – Gyorsvizsgálat (alapértelmezés)<br>**2** – Teljes vizsgálat|
|**ScheduleScanDay**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Mindennap (alapértelmezés)<br>**1** – hétfő<br>**2** – kedd<br>**3** – szerda<br>**4** – csütörtök<br>**5** – péntek<br>**6** – szombat<br>**7** – vasárnap<br>**8** – Nincs ütemezett vizsgálat|
|**ScheduleScanTime**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – 00:00<br>**60** – 1:00<br>**120** – 2:00 (alapértelmezés)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1381** – Karbantartási időszak|
|**ScheduleQuickScanTime**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br>**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – 00:00<br>**60** – 1:00<br>**120** – 2:00 (alapértelmezés)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1380** – 23:00|
|**AVGCPULoadFactor**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek: 0** - **100** (alapértelmezés: **50**)|
|**AllowArchiveScanning**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**AllowEmailScanning**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Adattípus:** Egész szám<br>**Megengedett értékek:**<br>**0** – nem engedélyezett (alapértelmezés)<br>**1** – engedélyezett|
|**AllowFullScanRemovableDriveScanning**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett (alapértelmezés)<br>**1** – engedélyezett|
|**AllowFullScanOnMappedNetworkDrives**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**AllowScanningNetworkFiles**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés) – Ha az engedélyezett értéket állítja be, akkor is fut, amikor az RTP be van kapcsolva|
|**SignatureUpdateInterval**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Aláírások időközönkénti ellenőrzése kikapcsolva<br>**1** – Aláírások ellenőrzése óránként<br>**2** – Aláírások ellenőrzése 2 óránként stb.<br>**24** – Aláírások ellenőrzése naponta<br>**Alapértelmezett érték:** 8 – Aláírások ellenőrzése 8 óránként|
|**AllowCloudProtection**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – nem engedélyezett<br>**1** – engedélyezett (alapértelmezés)|
|**SubmitSamplesConsent**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Mindig kérdezzen rá (alapértelmezés)<br>**1** – Biztonságos minták automatikus küldése<br>**2** – Soha ne küldjön<br>**3** – Az összes minta automatikus küldése|
|**ExcludedExtensions**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Adattípus:** Karakterlánc<br /><br />**Megengedett értékek:**<br>*&lt;a kiterjesztések listája, pontosvesszővel elválasztva&gt;* Például: **obj;lib**<br>**Alapértelmezés:** a bővítmények nincsenek kizárva|
|**ExcludedPaths**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Adattípus:** Karakterlánc<br /><br />**Megengedett értékek:**<br /><br />*&lt;az elérési utak listája pontosvesszővel elválasztva&gt;*<br /><br />Például: **c:\test;c:\test1.exe**<br /><br />**Alapértelmezett érték:** Nincsenek elérési utak kizárva|
|**ExcludedProcesses**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Adattípus:** Karakterlánc<br /><br />**Megengedett értékek:**<br>*&lt;az elérési utak listája pontosvesszővel elválasztva&gt;*<br>Például: **c:\test.exe;c:\test1.exe**<br>**Alapértelmezett érték:** Nincs kizárt eljárás|

### Edge böngésző URI-beállításai

|Házirend neve|Részletek|
|---------------|------------|-----------|
|**Böngésző engedélyezése**<br>(csak mobil)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**: a böngészés ki van kapcsolva<br>**1**: a böngészés be van kapcsolva (alapértelmezés)|
|**AllowSearchSuggestionsinAddressBar**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**: a keresési javaslatok megjelenítésének mellőzése<br>**1**: a keresési javaslatok megjelenítése (alapértelmezés)|
|**SendIntranetTraffictoInternetExplorer**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0**: letiltva (az intranetes helyek megnyitása az Edge böngészőben – alapértelmezés)<br>**1** – Engedélyezve (az intranetes helyek megnyitása az Internet Explorerben).|
|**Követés letiltásának engedélyezése**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Letiltva (DNT küldésének mellőzése – alapértelmezés)<br>**1** – Engedélyezve (DNT küldése)|
|**SmartScreen konfigurálása**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nem engedélyezett<br>**1** – Engedélyezett (alapértelmezés)|
|**Előugró ablakok engedélyezése**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Előugró ablakok letiltása (alapértelmezés)<br>**1** – Előugró ablakok engedélyezése|
|**Cookie-k engedélyezése**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Nincs blokkolás. Cookie-k engedélyezése az összes webhelyről (alapértelmezés)<br>**1** – Csak a harmadik felektől származó cookie-k letiltása<br>**2** – Az összes cookie letiltása|
|**Jelszó mentésének engedélyezése**<br>(az asztali és mobilos verzióknál egyaránt)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Jelszókezelő letiltva <br>**1** – Jelszókezelő engedélyezve (alapértelmezés)|
|**Automatikus kitöltés engedélyezése**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Adattípus:** Egész szám<br /><br />**Megengedett értékek:**<br>**0** – Letiltva (alapértelmezés)<br>**1** – Engedélyezve|
|**Vállalati webhelylista konfigurálása**<br>(csak asztali verziók)|**URI teljes elérési útja:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Adattípus:** Karakterlánc<br /><br />**Engedélyezett értékek:<br>0** – Nincs konfigurálva<br>**1** – Az Internet Explorer vállalati módú webhelylistájának használata, ha azt konfigurálták (alapértelmezés)<br>**2** – A vállalati webhelylista helyének megadása|

### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO3-->


