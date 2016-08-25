---
title: "Mobileszközök biztonsági házirendjének beállításai | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: 8b7dac0bef8505567a9d0485fe6e952a3f6aa305


---

# Mobileszközök biztonsági házirendjének beállításai a Microsoft Intune-nal
> [!IMPORTANT]
> A Microsoft Intune már külön konfigurációs szabályzatokat tartalmaz minden eszközplatformhoz, és ezek a szabályzatok a legfrissebb használható beállításokat tartalmazzák. Továbbra is használja a mobileszköz-biztonsági házirendet, és a meglévő telepítések továbbra is működni fognak. Mindazonáltal meg kell terveznie a mielőbbi áttérést az új konfigurációs szabályokra, mivel a jövőben eltávolításra kerül a mobileszköz-biztonsági házirend.

Az Intune mobileszköz-biztonsági szabályzatainak használatával konfigurálhatja azokat a beállításokat, amelyeket a vállalat felügyelt eszközein kíván érvénybe léptetni. Ezek a beállítások az eszközök működésének és biztonsági funkcióinak szabályozására szolgálnak.

Mobileszköz-biztonsági szabályzatokat a következő eszköztípusok esetében hozhat létre és léptethet érvénybe:

-   Windows RT 8.1- és regisztrált Windows 8.1-eszközök

-   Windows RT

-   Windows Phone 8 és Windows Phone 8.1

-   iOS

-   Android és Samsung KNOX

> [!NOTE]
> Egyes beállítások csak bizonyos eszközökre alkalmazhatók. A konfigurálható beállítások teljes listáját lásd az alábbi táblázatban.

## Biztonsági beállítások

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Jelszó szükséges a mobileszközök feloldásához**|Nem|Nem|Igen|Igen|Igen|
|**Kötelező jelszótípus**<br /><br />(a megkövetelt jelszótípust határozza meg, például hogy a jelszó csak számokat, vagy számokat és betűket is tartalmazhat)|Igen|Igen|Igen|Igen|Nem|
|**Megkövetelt jelszótípus – a karakterkészletek minimális száma**<br /><br />A következő négy karakterkészlet létezik: kisbetűk, nagybetűk, számok és szimbólumok. Ez a beállítás azt határozza meg, hány különböző karakterkészletnek kell szerepelnie a jelszóban). iOS-eszközök esetén azonban azt határozza meg, hány szimbólumnak kell szerepelnie a jelszóban)|Igen|Igen|Igen|Igen|Nem|
|**Jelszó minimális hossza**|Igen|Igen|Igen|Igen|Igen|
|**Egyszerű jelszavak engedélyezése**<br /><br />Egyszerű jelszó például a „0000” és az „1234”|Nem|Nem|Igen|Igen|Nem|
|**Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt**|Igen|Igen|Igen|Igen|Igen|
|**Képernyő kikapcsolása ennyi perc inaktivitás után**<sup>1</sup>|Igen|Igen|Igen|Igen|Igen|
|**Jelszó lejárata (nap)**|Igen|Igen|Igen|Igen|Igen|
|**Jelszóelőzmények megjegyzése**|Igen|Igen|Igen|Igen|Igen|
|**Korábbi jelszavak megjegyzése** – **Korábbi jelszavak újbóli használatának tiltása**|Igen|Igen|Igen|Igen|Igen|
|**Jelszó minősége**|Nem|Nem|Nem|Nem|Igen|
|**Képjelszó és PIN-kód engedélyezése**|Igen|Igen|Nem|Nem|Nem|
|**Tétlen percek száma, mielőtt az eszköz újból kéri a jelszót**|Nem|Nem|Nem|Igen|Nem|
|**Ujjlenyomattal történő zárolásfeloldás engedélyezése**|Nem|Nem|Nem|iOS 7 és újabb verziók|Nem|
Ha a **Képernyő kikapcsolása ennyi perc inaktivitás után** és a **Jelszó kérése ennyi perc inaktivitás után** beállítást is konfigurálja iOS-eszközökön, akkor egymás után lesznek alkalmazva. Ha például mindkét beállítást az **5** perc értékre állítja be, a képernyő 5 perc után automatikusan ki fog kapcsolni, és az eszköz további 5 perc után lesz zárolva. Ha azonban a felhasználó manuálisan kapcsolja ki a képernyőt, azonnal a második beállítás lesz alkalmazva. Ugyanebben a példában az eszköz 5 perccel azután lesz zárolva, hogy a felhasználó kikapcsolta a képernyőt.

Ha Windows RT rendszerű eszközökre beállítja a jelszóhosszúságra vonatkozó házirend alkalmazását, a rendszer a felhasználókat a jelszavuk módosítására kényszeríti, még akkor is, ha az aktuális jelszó megfelel a házirend követelményeinek.

## Titkosítási beállítások

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Titkosítás megkövetelése mobileszközön**<sup>1</sup><br /><br />A Windows Phone 8-telefonokon ezt **Igen**értékre kell állítani.<br /><br />Az iOS-eszközök titkosításának engedélyezéséhez **A mobileszközök zárolásának feloldásához jelszó szükséges**beállítást engedélyezni kell.|Igen|Nem|Igen|Nem|Igen|
|**Titkosítás megkövetelése tárolókártyákon**<br /><br />Az Exchange ActiveSync által kezelt eszközökre is vonatkozik.|nem áll rendelkezésre|nem áll rendelkezésre|n/a (az alkalmazások és a vonatkozó adatok titkosítása automatikusan megtörténik)|nem áll rendelkezésre|Igen|
További információk a Windows 8.1 rendszerű eszközökhöz

-   A Windows 8.1 rendszerű eszközökön a titkosítás kényszerítéséhez minden egyes eszközön telepíteni kell a következőt: [2014. decemberi MDM-ügyfélfrissítés Windows rendszerre](http://support.microsoft.com/kb/3013816) .

-   Ha engedélyezi ezt a beállítást a Windows 8.1 rendszerű eszközökön, az eszköz valamennyi felhasználójának rendelkeznie kell Microsoft-fiókkal.

-   A titkosítás működéséhez az eszköznek teljesítenie kell a Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) hardvertanúsítvány követelményeit.

-   Amikor kényszeríti az eszközön a titkosítást, a Microsoft-fiókkal rendelkező felhasználók részéről a helyreállítási kulcs csak a OneDrive-fiókjukból érhető el. Ez a kulcs nem állítható vissza egy felhasználó nevében.

## Kártevőkre vonatkozó beállítások

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Hálózati tűzfal megléte szükséges**|Igen|Nem|Nem|Nem|Nem|
|**SmartScreen engedélyezése**|Igen|Nem|Nem|Nem|Nem|

## Rendszerbeállítások

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Automatikus frissítés szükséges**|Igen|Nem|Nem|Nem|Nem|
|**Automatikus frissítés szükséges – Az automatikusan telepített frissítések legalacsonyabb besorolása**<br /><br />Válassza ki az automatikus telepítésű frissítések besorolását:<br /><br />**Fontos** – Minden fontosként megjelölt frissítést telepít.<br /><br />**Ajánlott** – Minden fontosként vagy ajánlottként megjelölt frissítést telepít.|Igen|Nem|Nem|Nem|Nem|
|**Képernyőfelvétel-készítés használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Vezérlőközpont engedélyezése a zárolási képernyőn**|Nem|Nem|Nem|iOS 7 és újabb verziók|Nem|
|**Értesítési nézet engedélyezése a zárolási képernyőn**|Nem|Nem|Nem|iOS 7 és újabb verziók|Nem|
|**Ma nézet engedélyezése a zárolási képernyőn**|Nem|Nem|Nem|iOS 7 és újabb verziók|Nem|
|**Felhasználói fiókok felügyelete**|Igen|Nem|Nem|Nem|Nem|
|**Diagnosztikai adatok küldésének engedélyezése**|Igen|Nem|Csak Windows Phone 8.1 esetén|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Nem megbízható TLS tanúsítványok engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Személyespénztárca-szoftver zárolt állapotban**|Nem|Nem|Nem|Igen|Nem|
|**Gyári beállítások visszaállításának engedélyezése**|Nem|Nem|Nem|Nem|Igen (kizárólag Samsung KNOX esetében)|


## Felhőbeállítások – dokumentumok és adatok

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**iCloudba történő biztonsági mentés engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Dokumentum iCloudba szinkronizálásának engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Fényképadatfolyamok iCloudba szinkronizálásának engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Biztonsági másolat titkosításának engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Munkahelyi mappák URL-címe**<br /><br />(beállítja a munkahelyi mappa URL-címét, hogy lehetővé tegye a dokumentumok az eszközök közötti szinkronizálását)|Igen|Nem|Nem|Nem|Nem|
|**Google biztonsági mentés engedélyezése**|Nem|Nem|Nem|Nem|Igen (kizárólag Samsung KNOX esetében)|

## Felhőbeállítások – fiókok és szinkronizálás

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Microsoft-fiók használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Nem|
|**Google-fiók automatikus szinkronizálásának engedélyezése**|Nem|Nem|Nem|Nem|Igen (kizárólag Samsung KNOX esetében)|

## E-mail beállítások

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**E-mail mellékletek letöltésének engedélyezése a felhasználók számára**<sup>1</sup>|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|
|**E-mail szinkronizálási időtartam** Az Exchange ActiveSync által kezelt eszközökre is vonatkozik.|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|
|**Engedélyezze a beállításokat nem teljes mértékben támogató eszközök szinkronizálását az Exchange-kiszolgálóval (Exchange ActiveSync)** Az Exchange ActiveSync által kezelt eszközökre is vonatkozik.|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|nem áll rendelkezésre|
|**A Microsoft-fiók opcionálissá tétele a Windows Mail alkalmazásban**|Igen|Nem|Nem|Nem|Nem|
|**Egyéni e-mail fiókok engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Nem|

## Alkalmazásbeállítások – böngésző

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Webböngésző használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Automatikus kitöltés engedélyezése**|Igen|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Előugróablak-blokkoló engedélyezése**|Igen|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Cookie-k engedélyezése**|Nem|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Beépülő modulok engedélyezése**|Igen|Nem|Nem|Nem|Nem|
|**Active Scripting engedélyezése**|Igen|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Csalás elleni figyelmeztetés engedélyezése**|Igen|Nem|Nem|Igen|Nem|
|**Intranetes hely engedélyezése egyetlen szó beírásakor**<br /><br />(engedélyezi, hogy egyetlen szó, például a „Bing” használatával az Internet Explorert webhelyekre lehessen irányítani)|Igen|Nem|Nem|Nem|Nem|
|**Intranet hálózat automatikus észlelésének engedélyezése**|Igen|Nem|Nem|Nem|Nem|
|**Internet zóna biztonsági szintje**|Igen|Nem|Nem|Nem|Nem|
|**Intranet zóna biztonsági szintje**|Igen|Nem|Nem|Nem|Nem|
|**Megbízható helyek zóna biztonsági szintje**|Igen|Nem|Nem|Nem|Nem|
|**Tiltott helyek zóna biztonsági szintje**|Igen|Nem|Nem|Nem|Nem|
|**Do Not Track (Nyomkövetés tiltása) fejléc küldése**|Igen|Nem|Nem|Nem|Nem|
|**Vállalati üzemmód menü elérések engedélyezése**|Igen|Nem|Nem|Nem|Nem|
|**Vállalati üzemmód webhelylistájának helye**|Igen|Nem|Nem|Nem|Nem|

## Alkalmazásbeállítások – alkalmazások

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Alkalmazástároló használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Jelszó megkövetelése az alkalmazástórolóhoz való hozzáféréshez**|Nem|Nem|Nem|Igen|Nem|
|**Alkalmazáson belüli vásárlás engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Felügyelt dokumentumok engedélyezése egyéb, nem felügyelt alkalmazásokban**|Nem|Nem|Nem|iOS 7 és újabb verziók|Nem|
|**Nem felügyelt dokumentumok engedélyezése egyéb, felügyelt alkalmazásokban**|Nem|Nem|Nem|iOS 7 és újabb verziók|Nem|
|**Videokonferenciák engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Felnőtt tartalom engedélyezése a médiatárban**|Nem|Nem|Nem|Igen|Nem|
|**Alkalmazástelepítés engedélyezése**|Nem|Nem|Nem|iOS 6 és újabb verziók|Nem|

## Alkalmazásbeállítások – játékok

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Game Centerbeli ismerősök engedélyezése**|Nem|Nem|Nem|Igen|Nem|
|**Több résztvevős játék engedélyezése**|Nem|Nem|Nem|Igen|Nem|

## Eszközképességek beállításai – hardver

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kamera használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Igen|Igen|
|**Cserélhető tároló használatának engedélyezése**|Nem|Nem|Igen|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**Wi-Fi használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**Wi-Fi alapú internetmegosztás használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Nem|
|**Wi-Fi elérési pontok jelentéskészítésének engedélyezése**<br /><br />(információt küld a Wi-Fi kapcsolatokról a közeli kapcsolatok felderítésének elősegítése érdekében)|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Nem|
|**Földrajzi hely meghatározásának engedélyezése**<br /><br />(engedélyezi az eszköz számára a helyadatok használatát)|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**NFC használatának engedélyezése**<br /><br />(engedélyezi a kis hatótávolságú kommunikációt használó műveleteket)|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**Bluetooth használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**Kikapcsolás engedélyezése**<br>Ha ez a beállítás le van tiltva, a **Megengedett sikertelen bejelentkezések száma az eszközön tárolt adatok törléséig** beállítás Samsung KNOX-eszközökön nem működik.|Nem|Nem|Nem|Nem|Igen (kizárólag Samsung KNOX esetében)|

## Eszközképességek beállításai – mobilhálózat

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Hangroaming használatának engedélyezése**|Nem|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Adatroaming használatának engedélyezése**|Igen|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Automatikus szinkronizálás engedélyezése roaming közben**|Nem|Nem|Nem|Igen|Nem|
|**SMS-/MMS-üzenetküldés engedélyezése**|Nem|Nem|Nem|Nem|Igen (kizárólag Samsung KNOX esetében)|

## Eszközképességek beállításai – szolgáltatások

|Beállítás neve|Windows 8.1 és Windows RT 8.1|Windows RT|Windows Phone 8 és Windows Phone 8.1|iOS|Android és Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Hangsegéd engedélyezése**|Nem|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Hangsegéd engedélyezése, amíg az eszköz zárolva van**|Nem|Nem|Nem|Igen|Nem|
|**Hangtárcsázás engedélyezése**|Nem|Nem|Nem|Igen|Igen (kizárólag Samsung KNOX esetében)|
|**Másolás és beillesztés használatának engedélyezése**|Nem|Nem|Csak Windows Phone 8.1 esetén|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**Vágólap alkalmazások közötti megosztásának engedélyezése**|Nem|Nem|Nem|Nem|Igen (kizárólag Samsung KNOX esetében)|
|**A YouTube használatának engedélyezése**|Nem|Nem|Nem|Nem|Igen (kizárólag Samsung KNOX esetében)|

### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával.md](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


