---
title: "Windowsos szabályzatbeállítások | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a280fcbecf82e6ff27e40d2d53331b3988953ff7
ms.openlocfilehash: aa62528e588b0579669ab8d115766efd72e6f9b2


---

# Windowsos szabályzatbeállítások a Microsoft Intune-ban
A Microsoft Intune **Windows-eszközökhöz készült általános konfigurációs házirendjét (Windows 8.1 és újabb verziók)** regisztrált Windows 8.1- és Windows 8-eszközökhöz használhatja:

## Alkalmazhatósági beállítások

|Beállítás neve|Részletek|
|----------------|----------------------------------|
|**Az összes konfiguráció alkalmazása a Windows 10-re**|Ezzel a beállítással engedélyezheti, hogy a szabályzatban szereplő beállítások a rendszer Windows Phone 8- és 8.1-eszközökön felül a Windows 10-eszközökre is alkalmazza.|

## Biztonsági beállítások

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Kötelező jelszótípus**|A megkövetelt jelszótípust határozza meg, például hogy a jelszó csak számokat, vagy számokat és betűket is tartalmazhat.|Igen|Igen|
|**Megkövetelt jelszótípus – a karakterkészletek minimális száma**|A következő négy karakterkészlet létezik: kisbetűk, nagybetűk, számok és szimbólumok. Ez a beállítás azt határozza meg, hány különböző karakterkészletnek kell szerepelnie a jelszóban. iOS-eszközök esetén azonban azt határozza meg, hány szimbólumnak kell szerepelnie a jelszóban.|Igen|Igen|
|**Jelszó minimális hossza**<sup>1</sup>|Konfigurálja a minimálisan szükséges hossza (karakter) a jelszót az eszközökön.|Igen|Igen|
|**Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt**|Törli az eszközt a megadott számú sikertelen bejelentkezést követően.|Igen|Igen|
|**Képernyő kikapcsolása ennyi perc inaktivitás után**|Adja meg, hogy az eszköz hány perc tétlenség után kérjen jelszót a zárolás feloldásához.| Igen|Igen|
|**Jelszó lejárata (nap)**|Ennyi nap elteltével kell megváltoztatni az eszköz jelszavát.|Igen|Igen|
|**Jelszóelőzmények megjegyzése**|Ez a beállítás azt határozza meg, hogy a felhasználó beállíthat-e általa korábban már használt jelszavakat.|Igen|Igen|
|**Korábbi jelszavak megjegyzése** – **Korábbi jelszavak újbóli használatának tiltása**|Ez a beállítás az eszköz által megjegyzett korábbi jelszavak számát határozza meg.|Igen|Igen|
|**Képjelszó és PIN-kód engedélyezése**|Engedélyezi a képjelszó és a PIN-kód használatát az eszközön. A képjelszó segítségével a felhasználó egy képre rajzolt kézmozdulatokkal jelentkezhet be. A PIN-kód gyors bejelentkezést tesz lehetővé egy négyjegyű kóddal.|Igen|Igen|
<sup>1</sup> Ha Windows RT rendszerű eszközökre beállítja a jelszóhosszúságra vonatkozó házirend alkalmazását, a rendszer a felhasználókat a jelszavuk módosítására kényszeríti, még akkor is, ha az aktuális jelszó megfelel a házirend követelményeinek.

## Titkosítási beállítások

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Titkosítás megkövetelése mobileszközön**<sup>1</sup>|Az eszközön található összes fájlnak titkosítva kell lennie.<br>A Windows Phone 8-telefonokon ezt **Igen**értékre kell állítani.|Igen|Nem|
<sup>1</sup> További információ a Windows 8.1 rendszerű eszközökhöz

-   A Windows 8.1 rendszerű eszközökön a titkosítás kényszerítéséhez minden egyes eszközön telepíteni kell a következőt: [2014. decemberi MDM-ügyfélfrissítés Windows rendszerre](http://support.microsoft.com/kb/3013816) .

-   Ha engedélyezi ezt a beállítást a Windows 8.1 rendszerű eszközökön, az eszköz valamennyi felhasználójának rendelkeznie kell Microsoft-fiókkal.

-   A titkosítás működéséhez az eszköznek teljesítenie kell a Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) hardvertanúsítvány követelményeit.

-   Amikor kényszeríti az eszközön a titkosítást, a Microsoft-fiókkal rendelkező felhasználók részéről a helyreállítási kulcs csak a OneDrive-fiókjukból érhető el. Ez a kulcs nem állítható vissza egy felhasználó nevében.

## Kártevőkre vonatkozó beállítások

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Hálózati tűzfal megléte szükséges**|Előírja a Windows tűzfal bekapcsolását.|Igen|Nem|
|**SmartScreen engedélyezése**|Kötelezővé teszi a Windows SmartScreen használatát az eszközökön.|Igen|Nem|

## Rendszerbeállítások

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Automatikus frissítés szükséges**|Az automatikus frissítési beállítás aktiválása az eszközökön.|Igen|Nem|
|**Automatikus frissítés szükséges – Az automatikusan telepített frissítések legalacsonyabb besorolása**|Válassza ki az automatikus telepítésű frissítések besorolását:<br /><br />-   **Fontos** – Minden fontosként megjelölt frissítést telepít.<br />-   **Ajánlott** – Minden fontosként vagy ajánlottként megjelölt frissítést telepít.|Igen|Nem|
|**Felhasználói fiókok felügyelete**|Kötelezővé teszi a felhasználói fiókok felügyeletének használatát az eszközökön.|Igen|Nem|
|**Diagnosztikai adatok küldésének engedélyezése**|Engedélyezése esetén az eszköz diagnosztikai adatokat küld a Microsoftnak.|Igen|Nem|


## Felhőbeállítások – dokumentumok és adatok

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Munkahelyi mappák URL-címe**|Beállítja a munkahelyi mappa URL-címét, hogy lehetővé tegye a dokumentumok az eszközök közötti szinkronizálását.|Igen|Nem|

## E-mail beállítások

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**A Microsoft-fiók opcionálissá tétele a Windows Mail alkalmazásban**|Microsoft-fiók nélkül is hozzáférhetővé teszi a Windows Posta alkalmazást.|Igen|Nem|

## Alkalmazásbeállítások – böngésző

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Automatikus kitöltés engedélyezése**|A felhasználók módosíthatják a böngésző automatikus kiegészítési funkciójának beállításait.|Igen|Nem|
|**Előugróablak-blokkoló engedélyezése**|A böngésző előugróablak-blokkolójának engedélyezése vagy letiltása.|Igen|Nem|
|**Beépülő modulok engedélyezése**|A felhasználók hozzáadhatnak beépülő modulokat az Internet Explorerhez.|Igen|Nem|
|**Active Scripting engedélyezése**|A böngésző futtathat parancsfájlokat (pl. Active X-parancsfájlok).|Igen|Nem|
|**Csalás elleni figyelmeztetés engedélyezése**|A potenciálisan rosszindulatú webhelyekről szóló figyelmeztetések engedélyezése vagy letiltása.|Igen|Nem|
|**Intranetes hely engedélyezése egyetlen szó beírásakor**|Engedélyezi, hogy egyetlen szó, például a „Bing” használatával az Internet Explorert webhelyekre lehessen irányítani.|Igen|Nem|
|**Intranet hálózat automatikus észlelésének engedélyezése**|Segít az intranetes webhelyek biztonságának konfigurálásában az Internet Explorerben.|Igen|Nem|
|**Internet zóna biztonsági szintje**|Az Internet Explorer internetes webhelyekre vonatkozó biztonsági szintjének beállítása.|Igen|Nem|
|**Intranet zóna biztonsági szintje**|Az Internet Explorer intranetes webhelyekre vonatkozó biztonsági szintjének beállítása.|Igen|Nem|
|**Megbízható helyek zóna biztonsági szintje**|Beállíthatja a megbízható helyek zóna biztonsági szintjét.|Igen|Nem|
|**Tiltott helyek zóna biztonsági szintje**|Beállíthatja a tiltott helyek zóna biztonsági szintjét.|Igen|Nem|
|**Do Not Track (Nyomkövetés tiltása) fejléc küldése**|A nyomkövetést tiltó fejléc küldése az Internet Explorerben a felkeresett webhelyeknek.|Igen|Nem|
|**Vállalati üzemmód menü elérések engedélyezése**|Lehetővé teszi, hogy a felhasználók férhetnek hozzá a vállalati üzemmód menü beállítások Internet Explorer programból.<br>Engedélyezése esetén meghatározhatja a **Naplózási jelentés helyét** is, ahol megtalálható annak a jelentésnek az URL-címe, amely megjeleníti azokat a webhelyeket, amelyekhez a felhasználók bekapcsolták a vállalati üzemmódot.|Igen|Nem|
|**Vállalati üzemmód webhelylistájának helye**|Megadhatja azon webhelyek listájának helyét, amelyek a Vállalati üzemmódot használják, ha az aktív.|Igen|Nem|

## Eszközképességek beállításai – mobilhálózat

|Beállítás neve|Részletek|Windows 8.1 és Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Adatroaming használatának engedélyezése**|Adatroaming használatának engedélyezése, ha az eszköz mobilhálózathoz csatlakozik.|Igen|Nem|



### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


