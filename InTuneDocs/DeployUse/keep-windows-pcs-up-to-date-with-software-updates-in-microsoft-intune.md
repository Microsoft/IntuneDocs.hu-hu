---
title: "Szoftverfrissítések Windows rendszerű számítógépekhez | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8c1f4f209c5ec704290882b8f6f71e0b1b01d21c
ms.openlocfilehash: d650eea62be0c00c414b51ed5c49310c5175acd7


---

# Windows rendszerű számítógépek naprakészen tartása szoftverfrissítésekkel a Microsoft Intune-ban
A Microsoft Intune többféle módszerrel könnyíti meg a felügyelt számítógépek védelmét, például a számítógépeket naprakészen tartó szoftverfrissítések kezelésével, amelyek segítenek a legújabb javítások és szoftverfrissítések gyors telepítésében.

Ha még nem telepítette az Intune-ügyfelet a számítógépeken, [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](install-the-windows-pc-client-with-microsoft-intune.md) című témakörben olvashat erről.

Ha új frissítések érhetők el a Microsoft Update-ben, vagy egy külső gyártótól származó frissítést hozott létre, és azok alkalmazhatók a kezelt számítógépekre, megjelenik egy értesítés a **Frissítések** munkaterület **Áttekintés** lapján. Miután ezt az értesítési hivatkozást választotta, különféle műveleteket végezhet el, például megtekintheti a frissítés további adatait, jóváhagyhatja vagy elutasíthatja a frissítést, és megtekintheti, hogy mely számítógépeken lesz telepítve a frissítés, ha jóváhagyja.

> [!IMPORTANT]
> A **Frissítések** munkaterület addig nem jelenik meg a felügyeleti konzolon, amíg nem telepíti az ügyfelet legalább egy számítógépen, és nem kezdi meg sikeresen annak kezelését.

A frissítések jóváhagyása és telepítése során az Intune-konzol **Frissítések** munkaterületén ellenőrizheti, hogy a telepítés sikeres vagy sikertelen volt-e.

A következő szakaszokban leírtakkal naprakészen tarthatja a kezelt számítógépeken lévő szoftvereket.

## Előkészületek
A szoftverfrissítések létrehozásának és jóváhagyásának megkezdése előtt konfiguráljon és alkalmazzon a frissítésének telepítésének idejét és mikéntjét szabályozó házirendeket a számítógépekre.

### Frissítési házirend-beállítások konfigurálása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Házirend** &gt; **Áttekintés** &gt; **Házirend hozzáadása** elemet.

2.  Konfiguráljon és alkalmazzon egy **Microsoft Intune-ügynökbeállítási** házirendet a frissítési beállításokhoz. Használhatja az ajánlott beállításokat, vagy testre is szabhatja a beállításokat. Ha a házirendek létrehozásával és alkalmazásával kapcsolatban további tájékoztatásra van szüksége, [A Windows rendszerű számítógépek a Microsoft Intune számítógépügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) című témakörben olvashat erről bővebben.

A következő táblázatban azok az értékek láthatók, melyek beállíthatók a házirendben, továbbá az ajánlott értékek, amelyek alkalmazva lesznek, ha nem szabja testre a házirendet. Ezek a beállítások a **Frissítések** részben találhatók meg.

  |Házirend-beállítás|Részletek|
    |------------------|--------------------|
    |**A frissítések és alkalmazások keresésének gyakorisága (óra)** |Azt adja meg, hogy milyen gyakran (8–22 óra) ellenőrzi az Intune, hogy rendelkezésre állnak-e új frissítések és alkalmazások.<br /><br />Javasolt érték: **8** óra.|
    |**A frissítések és alkalmazások automatikus vagy rákérdezéses telepítése** |Azt határozza meg, hogy a frissítések telepítése automatikusan történik, vagy a rendszer megkérdezi a felhasználót a telepítés előtt. Emellett ezzel a beállítással ütemezheti a frissítések és alkalmazások telepítését.<br /><br />**A frissítések és alkalmazások ütemezés szerinti automatikus telepítése** beállítással a megadott ütemezésnek megfelelően lesznek telepítve a frissítések és az alkalmazások.<br /><br />Függő házirend-beállításként az **Automatikus karbantartás használata a Windows rendszerű számítógépeken**  beállítás azt adja meg, hogy a frissítések és az alkalmazások a Windows automatikus karbantartási időszakában legyenek telepítve.<br /><br />**A felhasználó felszólítása a telepítésre** beállítás esetén a rendszer rákérdez a frissítések telepítésére, amikor készen állnak.<br /><br />Javasolt értékek:<br /><br />A **Frissítések és alkalmazások ütemezés szerinti automatikus telepítése** érték kijelölve<br /><br />**Ütemezett nap: Naponta**<br /><br />**Ütemezett időpont: 3:00**<br /><br />A **Windows rendszerű számítógépek automatikus karbantartása** érték kijelölve|
    |**A Windows működését nem megszakító frissítések azonnali telepítésének engedélyezése** |Az **Engedélyezés** érték esetén a rendszer letöltésük után azonnal telepíti a frissítéseket, kivéve azokat, amelyek megszakítanák a Windows működését, vagy újraindítanák a rendszert. Ezek a frissítések **A frissítések és alkalmazások automatikus vagy rákérdezéses telepítése** beállítás konfigurációjának megfelelően lesznek telepítve.<br /><br />A **Nem engedélyezett** érték esetén a rendszer a **Frissítések automatikus vagy felszólítás utáni telepítése** beállítás konfigurációjának megfelelően telepíti a frissítéseket.<br /><br />Javasolt érték: **Engedélyezett** |
    |**Késleltetés a Windows az ütemezett frissítések és alkalmazások telepítését követő újraindítása előtt (perc)** |A Windows az ütemezett frissítések és alkalmazások telepítését követő újraindítása előtti (1-30 perces) várakozási időt határozza meg.<br /><br />Javasolt érték: **15 perc** |
    |**A kihagyott ütemezett frissítések és alkalmazások a Windows újraindítását követő telepítése megkezdésének késleltetése (perc)** |Azt határozza meg, hogy milyen (1-60 perces) várakozási idő után kezdődjön meg a frissítések és alkalmazások telepítése a Windows újraindítását követően, ha egy ütemezett frissítés kimaradt.<br /><br />Javasolt érték: **5 perc**|
    |**A Windows ütemezett frissítések és alkalmazások telepítését követő újraindítása szabályozásának engedélyezése a bejelentkezett felhasználó számára** |Azt határozza meg, hogy a bejelentkezett felhasználó késleltetheti-e a Windows újraindítását (ha az **Igen** értékre van állítva), vagy értesítést kap a Windows automatikus újraindításáról (ha a **Nem** értékre van állítva). Ha a frissítések és alkalmazások ütemezett telepítésének befejezésekor nincs bejelentkezve felhasználó, a Windows szükség esetén automatikusan újraindul. Ha alapértelmezés szerint a **Nem**értékre van állítva, a Windows újraindítása előtti idő 5 percre van állítva.<br /><br />Javasolt érték: **Igen**|
    |**A felhasználó megkérdezése a Windows újraindításáról az Intune-ügyfélügynök kötelező frissítésekor** |Azt határozza meg, hogy, hogy a rendszer kéri-e a bejelentkezett felhasználót a Windows újraindítására, ha az Intune-ügyfélügynök egy kötelező frissítéséhez a Windows újraindítása szükséges.<br /><br />Javasolt érték: **Igen**|
    |**A Microsoft Intune-ügyfélügynök kötelező frissítései telepítésének ütemezése** |Az ügyfélfrissítések telepítésének ütemezését határozza meg.<br /><br />Javasolt érték: nincs konfigurálva|
    |**Késleltetés a Windows az ütemezett frissítések és alkalmazások telepítését követő újraindításának kérései között (perc)** |Azt határozza meg, hogy a rendszer milyen (1-1440 perc közötti) gyakorisággal kéri a felhasználót, hogy indítsa újra a Windowst, amikor olyan ütemezett frissítés vagy alkalmazás lett telepítve, amelyhez a Windows újraindítása szükséges, és a felhasználó késlelteti az újraindítást.<br /><br />Javasolt érték: **30 perc** |

## Microsoft-szoftverek frissítése
A Microsoft-szoftverek frissítése az Ön részéről nagyon kevés munkát igényel. Ennek megkezdése előtt azonban két dolgot be kell állítania:

-   **Termékkategóriák és frissítési besorolások** – a frissítések a számítógépeken elérhetővé tenni kívánt kategóriáit és besorolásait határozza meg. Dönthet például úgy, hogy a Microsoft Office-nak csak a kritikus frissítéseit szeretné telepíteni.

-   **Automatikus jóváhagyási szabályok** – ezekkel a szabályokkal a frissítések meghatározott típusai automatikusan jóváhagyhatók, így csökkentheti a felügyelettel járó többletterhelést. Dönthet például úgy, hogy az összes kritikus frissítést automatikusan jóvá kívánja hagyni.

Az alábbi két eljárással készülhet fel a szoftverfrissítések alkalmazására:

### A kezelt számítógépek számára elérhetővé tenni kívánt termékkategóriák és frissítési besorolások beállítása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Felügyelet** &gt; **Frissítések** elemet.

2.  A **Szolgáltatás beállításai: Frissítések** oldal **Termékkategória** listájából válassza ki a számítógépek számára elérhetővé tenni kívánt frissítési kategóriákat. Fontos megjegyezni, hogy a leggyakoribb frissítések alapértelmezés szerint be vannak jelölve.

    > [!IMPORTANT]
    > Annak biztosítása érdekében, hogy a számítógépek megkapják a rendszergazda által jóváhagyott frissítéseket, a Windows Server Update Services (WSUS) **Adja meg az intraneten található Microsoft frissítési szolgáltatás helyét** csoportházirend-beállítását ne alkalmazza az Intune-ban regisztrált számítógépekre.

3.  A **Frissítési besorolás** listából válassza ki a frissítések a kezelt számítógépek számára elérhetővé tenni kívánt osztályait. A leggyakoribb beállítások itt is alapértelmezés szerint be vannak jelölve.

4.  A beállítások tárolásához válassza a **Mentés** lehetőséget.

### A szoftverfrissítések automatikus jóváhagyási szabályainak konfigurálása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Felügyelet** &gt; **Frissítések** elemet.

2.  Az **Automatikus jóváhagyási szabályok** részben, a **Kiszolgálóbeállítások: Frissítések** oldalon válassza az **Új** lehetőséget.

3.  Az Automatikus jóváhagyási szabály létrehozása varázsló **Általános** lapján adjon meg egy nevet, illetve megadhat egy leírást a szabályhoz.

4.  A **Termékkategóriák** lapon válassza ki a termékeket, amelyekhez automatikusan szeretné engedélyezni a frissítéseket.

5.  A **Frissítési besorolások** lapon adja meg az automatikusan jóváhagyni kívánt frissítési besorolásokat.

6.  Az **Alkalmazás** lapon tegye a következőket:

    -   Válassza ki a számítógépcsoportokat, melyekre alkalmazni kívánja az új szabályt, majd válassza a **Hozzáadás** lehetőséget.

    -   A frissítésekhez a **Telepítési határidő érvényesítése ezekre a frissítésekre** jelölőnégyzet bejelölésével, majd a **Telepítési határidő** listából a telepítési határidő kiválasztásával megadhat egy telepítési határidőt.

        > [!NOTE]
        > Ha megad egy telepítési határidőt, előfordulhat, hogy a kezelt számítógépeken a határidő lejárta után egy vagy több újraindításra lesz szükség.

    -   Ha elkészült, válassza a **Tovább** elemet.

7.  Az **Összesítés** lapon tekintse át az új szabály beállításait, majd válassza a **Befejezés** lehetőséget.

Az új szabály az **Automatikus jóváhagyási szabályok** részben jelenik meg, a következő helyen: **Kiszolgálóbeállítások: Frissítések** oldal.

> [!NOTE]
> A létrehozott automatikus jóváhagyási szabályok csak a jövőbeli frissítéseket hagyják jóvá, az Intune-ban korábban meglévő frissítéseket nem hagyják jóvá automatikusan. Ezen frissítések jóváhagyásához futtatnia kell az automatikus jóváhagyási szabályt.


### Automatikusan jóváhagyott frissítésekre vonatkozó szabályok szerkesztése, futtatása vagy törlése

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Felügyelet** &gt; **Frissítések** elemet.

2.  Az **Automatikus jóváhagyási szabályok** részben jelöljön ki egy szabályt, majd hajtsa végre a következők egyikét:

    -   A szabály szerkesztéséhez válassza a **Szerkesztés** lehetőséget, majd az **Automatikus jóváhagyási szabály frissítése varázslóban** módosítsa a szabály paramétereit.

    -   A szabály futtatásához válassza **A kijelölt futtatása** lehetőséget.

    -   A szabály törléséhez válassza a **Törlés** lehetőséget.

        > [!NOTE]
        > Egy szabály törlése nem befolyásolja a törölt szabály által jóváhagyott korábbi frissítéseket.

## A nem a Microsoft által készített szoftverek frissítése
Telepítheti nem a Microsoft által készített szoftverek frissítéseit is. Ezt úgy teheti meg, hogy a **Frissítés feltöltése** varázslóval feltölti a frissítést a felhőbeli tárolóhelyre, ami után ugyanúgy jóváhagyhatja vagy elutasíthatja a frissítést, mint a Microsoft-szoftverek esetében.

### Külső gyártótól származó frissítés feltöltése és konfigurálása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Frissítések** &gt; **Áttekintés** &gt; **Feltöltés** elemre.

2.  A **Frissítésfájlok** lapon a **Tallózás** lehetőséget választva jelölje ki a telepítési fájlokat, amelyek szükségesek a frissítés telepítéséhez. A fájl lehet Windows Installer (.msi) fájl, Windows Installer javítófájl (.msp) vagy .exe programfájl. Emellett a telepítési fájllal megegyező mappában lévő tetszőleges további fájlokat vagy mappákat is hozzáadhat.

    A rendszer megjeleníti a feltöltéséhez kijelölt fájlok teljes méretét. Fontos megjegyezni, hogy ez a méret nem tartalmazza a telepítési fájlok tömörítetlen vagy kibontott méretét.

3.  A telepítési fájlok megadása után a **Frissítés leírása** lapon megjelenik az Intune által a szoftvertelepítési fájlokból kinyert szoftverinformációkhoz tartozó név, leírás és besorolás. A telepíteni kívánt frissítés típusának megjelölésére választhat egy besorolást (Frissítések, Fontos frissítések, Biztonsági frissítések, Kumulatív frissítések vagy Szervizcsomagok). Ha elkészült, válassza a **Tovább** lehetőséget.

4.  A varázsló **Követelmények** lapján válassza ki a kezelt számítógépek architektúráját (32 bites, 64 bites vagy mindkettő) és operációs rendszerét, amelyeken alkalmazható lesz a frissítés.

5.  Az **Észlelési szabályok** lapon adja meg, hogy az Intune hogyan határozza meg, hogy egy frissítés már telepítve van-e a kezelt számítógépeken. Az alapértelmezett beállítás (**Az alapértelmezett észlelési szabályok használata**) beállítás esetén az Intune mindig minden célként megadott számítógépre telepíti egyszer a frissítéseket.

    > [!NOTE]
    > Ha a megadott frissítéstelepítési fájl egy Windows Installer vagy .msp-fájl, a varázsló **Észlelési szabályok** lapja nem jelenik meg. Ennek az az oka, hogy a Windows Installer és a .msp-fájlok tartalmazzák a saját, a korábbi frissítéstelepítések észlelésére vonatkozó utasításaikat.

    A következő szabályok közül egy vagy több alkalmazásával határozhatja meg, hogy az adott frissítés már telepítve van-e a kezelt számítógépeken:

    -   **A fájl létezik**

    -   **Az MSI-termékkód létezik**

    -   **A beállításkulcs létezik**

6.  Adja meg az észlelési szabály beállításához esetleg szükséges további információkat, például egy fájl elérési útját és nevét, egy Windows Installer-termékkódot vagy egy beállításkulcsot, majd válassza a **Tovább** lehetőséget.

7.  A varázsló **Előfeltételek** lapján olyan szoftvereket adhat meg, melyeknek már telepítve kell lennie ahhoz, hogy telepíteni lehessen a frissítést. Itt megadhatja a **Nincs** értéket, kiválaszthat egy az Intune-ba már felvett és azzal kezelt szoftvercsomagot, vagy az alábbi szabályok egyikének megadásával írhatja le a szoftvereket:

    -   **A fájl létezik**

    -   **Az MSI-termékkód létezik**

    -   **A beállításkulcs létezik**

8.  Adja meg az észlelési szabály beállításához esetleg szükséges további információkat, például egy fájl elérési útját és nevét, egy Windows Installer-termékkódot vagy egy beállításkulcsot, majd válassza a **Tovább** lehetőséget.

9. A varázsló **Parancssori argumentumok** lapján a telepítési parancssorhoz a telepítőfájl működésének módosítása céljából esetlegesen szükséges telepítési tulajdonságokat adhat hozzá. Egyes szoftverek például támogatják a **/q** tulajdonság használatát a csendes telepítés engedélyezéséhez. Az adott szoftvercsomag dokumentációját áttekintve tájékozódhat az esetlegesen támogatott parancssori argumentumokról. Adja meg a szükséges parancssori argumentumokat, ha vannak ilyenek, majd válassza a **Tovább** lehetőséget.

    > [!NOTE]
    > Ha a frissítés nem támogatja a csendes telepítést, a frissítés nem telepíthető az Intune használatával.

10. A varázsló **Visszatérési kódok** lapján megadhatja, hogyan legyenek értelmezve a frissítés telepítésének visszatérési kódjai. Az Intune alapértelmezés szerint az iparági szabványoknak megfelelő visszatérési kódok alapján ad jelentést a frissítések sikertelen vagy sikeres telepítéséről. A megadott visszatérési kódok a következők:

|Visszatérési kód|Részletek|
|---------------|------------------|
|**0**|Siker|
|**3010**|Siker, újraindítással|

11. Bármely itt nem szereplő visszatérési kód sikertelennek van tekintve.
Néhány frissítés a visszatérési kódok nem szabványos értelmezéseit alkalmazza. Ebben az esetben megadhat saját értelmezéseket a visszatérési kódokhoz.

12. Adja meg vagy szerkessze a szükséges visszatérési kódokat, majd válassza a **Tovább** lehetőséget.

13. A varázsló **Összegzés** lapján tekintse át a végrehajtandó műveleteket, majd válassza a **Feltöltés** lehetőséget a varázsló befejezéséhez.

A feltöltött frissítést az Ön Intune felhőalapú tárolóhelyén tárolja a rendszer. Ha nincs elegendő szabad terület a frissítéscsomag feltöltéséhez, erről a feltöltési folyamat során értesítést kap. Az Intune a frissítés feltöltésének a megkezdéséig nem tudja megállapítani, hogy ahhoz mekkora szabad tárhely szükséges, mert a tömörített telepítőfájlok több helyet foglalnak a kitömörítésük után.

Az Intune-ba való feltöltésük után a külső gyártótól származó frissítések a **Minden frissítés** ablaktábla **Frissítések** munkaterületén jelennek meg. Ekkor jóváhagyhatja és telepítheti a frissítést. További információért olvassa el a következő „Frissítések jóváhagyása és visszautasítása” című részt.

## Frissítések jóváhagyása és visszautasítása
Ha vannak a telepítésre készen álló frissítések, egy üzenet jelenik meg a **Frissítések** munkaterület **Frissítések – áttekintés** lapján, a **Frissítés állapota**részben. Ezt az üzenetet választva megnyithatja a **Minden frissítés** lapot, melyen megtekintheti, hogy mely frissítések állnak készen a jóváhagyásra.

A **Szűrők** lista használatával könnyebben megtalálhatja a frissítéseket. Megjelenítheti például csak a sikertelen vagy csak a felülírt frissítéseket.

Amikor kiválaszt egy frissítést a listáról, az alábbi táblázatban szereplő további parancsok is elérhetők, melyekkel kezelheti a frissítéseket:

|Feladat|Részletek|
|--------|--------------------|
|**Tulajdonságok megtekintése**|A frissítés részletes adatainak megtekintése, beleértve azon számítógépek darabszámát, melyeken alkalmazható.|
|**Szerkesztés**|Csak a nem a Microsoft által készített frissítésekhez használható. A frissítések tulajdonságainak szerkesztését teszi lehetővé.|
|**Jóváhagyás**|A kijelölt frissítés jóváhagyása, mely lehetővé teszi a csoportok beállítását, amelyekre telepítve lesz. További tudnivalókat a jelen témakör **Frissítések jóváhagyása** című eljárásában találhat.|
|**Elutasítás**|Eltávolítja a frissítés esetleges korábbi jóváhagyásait, és az alapértelmezett nézetekből elrejti a frissítést. A rendszer emellett a frissítésre vonatkozó esetleges jelentésadatokat is eltávolítja.<br /><br />Ha később meg szeretne keresni egy elutasított frissítést, a **Minden frissítés** lap szűrőjét állítsa be az **Elutasítva**értékre. Ezután szükség szerint jóváhagyhatja a frissítést.<br /><br />Ha egy frissítés azért lett elutasítva, mert elévült a Microsoft Update szolgáltatásban, ez a frissítés nem hagyható jóvá a Intune felügyeleti konzolon.<br /><br />Ha töröl bármely, a számítógépekre alkalmazott frissítési házirendet, ezen frissítési házirendek beállításai a számítógépeken telepített operációs rendszernek megfelelő alapértelmezett állapotra állnak vissza.|
|**Törlés**|Csak a nem a Microsoft által készített frissítésekhez használható. A kijelölt frissítés törlése.|
|**Feltöltés**|A **Frissítés feltöltése** varázsló elindítása, amellyel feltölthetők a telepíteni kívánt, nem a Microsoft által készített frissítések.|

### Frissítések jóváhagyása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Frissítések** &gt; **Áttekintés** &gt; **Jóváhagyásra váró új frissítések** elemre.

    A **Frissítések** munkaterületen válassza az **Áttekintés** &gt; **Jóváhagyásra váró új frissítések** lehetőséget.

    > [!NOTE]
    > Az **Új jóváhagyandó frissítések** hivatkozás csak akkor jelenik meg a **Frissítések állapota** területen, ha legalább egy kezelt számítógép számára jóvá kell hagyni egy frissítést.

2.  Válasszon ki egy frissítést, a lap alján áttekintve a frissítés tulajdonságait győződjön meg arról, hogy jóvá kívánja-e azt hagyni, majd válassza a **Jóváhagyás** lehetőséget. Ha az egyes elemek kijelölésekor lenyomva tartja a **CTRL** billentyűt, egyszerre több frissítést is kijelölhet.

3.  A **Csoportok kiválasztása** lapon válasszon ki egy csoportot, melyben telepíteni szeretné a frissítéseket, majd válassza a **Hozzáadás** lehetőséget. A csoportok megadása után válassza a **Tovább** lehetőséget.

4.  A **Telepítési művelet** lapon a listán szereplő valamennyi csoport esetén tegye a következőket:

    -   Válassza ki a következők egyikét a **Jóváhagyás** listából:

        -   **Kötelező telepítés** – a frissítés telepítése a megadott csoportban lévő számítógépekre.

        -   **Telepítés mellőzése** – a rendszer csak jelzi, hogy a telepítés alkalmazható, de nem telepíti.

        -   **Telepíthető** – a felhasználó igény szerint telepítheti az alkalmazást a Vállalati portálról.

        -   **Eltávolítás** – frissítések eltávolítása a célcsoportban lévő számítógépekről.

            > [!IMPORTANT]
            > A rendszer akkor is eltávolítja a frissítéseket, ha azok nem az Intune szolgáltatással lettek telepítve.

    -   Válassza ki a következők egyikét a **Határidő** listából:

        -   **Nincs** – azt jelzi, hogy a frissítés telepítésének nincs határideje, és a felhasználók folyamatosan elutasíthatják a frissítést.

        -   **Amint lehetséges** – a frissítés telepítése a célzott számítógépekre az első adandó alkalommal.

        -   **Egyéni** – dátum és idő meghatározása a jóváhagyott frissítések telepítéséhez.

        -   **Egy hét**, **Két hét**, **Egy hónap** – a frissítés telepítése a megadott időn belül.

5.  Válassza a **Befejezés** lehetőséget a beállítások mentéséhez, vagy a **Mégse** lehetőséget a beállítások elvetéséhez és a frissítések listájához való visszatéréshez.

    > [!IMPORTANT]
    > A szülőcsoportokhoz beállított műveleteket valamennyi gyermekük örökli, kivéve ha egy gyermekcsoporthoz explicit módon a **Telepítés mellőzése**, a **Kötelező telepítés**vagy az **Eltávolítás** művelet lett konfigurálva.

6.  A **Minden frissítés** lap alján, a részletek ablaktábláján ellenőrizheti, hogy vannak-e a frissítéssel kapcsolatos emlékeztető üzenetek.


### További információ
[Szabályzatok a Windows rendszerű számítógépek védelméhez](policies-to-protect-windows-pcs-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


