---
# required metadata

title: Az eszközök beállításainak és funkcióinak kezelése házirendek használatával | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 06/14/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával
A Microsoft Intune**-szabályzatok** a mobileszközök és a számítógépek funkcióit szabályozó beállítások csoportjai. A házirendeket ajánlott vagy testreszabott beállításokat tartalmazó sablonok segítségével hozhatja létre, majd telepítheti őket az eszköz- vagy felhasználói csoportok számára.

## Milyen típusú szabályzatok használhatók?

Az Intune-szabályzatok két kategóriába sorolhatók: A használt kategória határozza meg, hogyan hozható létre és hogyan telepíthető a házirend.


- **Konfigurációs szabályzatok:** Ezek általában az eszközök biztonsági beállításainak és szolgáltatásainak kezelésére használhatók. A témakörben található információk alapján megismerheti a szabályzatok létrehozását és telepítését, valamint a rendelkezésre álló beállításokat.
- **Eszközök megfelelőségi szabályzatai:** Ezek határozzák meg az eszközre vonatkozó szabályokat és beállításokat, amelyek ahhoz szükségesek, hogy az eszköz megfeleljen a feltételes hozzáférési szabályzatok előírásainak. A megfelelőségi szabályzatok a feltételes hozzáféréstől függetlenül is megfigyelheti és kijavíthatja az eszközök megfelelőséggel kapcsolatos hibáit.
A részleteket lásd: [Eszközmegfelelőségi szabályzatok a Microsoft Intune-ban](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Feltételes hozzáférési szabályzatok:** Ezekkel a szabályzatokkal a megadott feltételek alapján biztosíthatja a levelezés és más szolgáltatások védelmét.
A részleteket lásd: [Az e-mailek és az O365-szolgáltatások elérésének korlátozása a Microsoft Intune-ban](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Vállalati eszközregisztrációs szabályzatok:** a vállalati eszközregisztrációs szabályzatok létrehozásának részletes ismertetését lásd: [iOS- és Mac-eszközök kezelésének beállítása a Microsoft Intune-ban](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Erőforrás-hozzáférési szabályzatok:** A szabályzatok ezen csoportja együttműködve biztosítja a hozzáférést a felhasználóknak a munkájuk sikeres elvégzéséhez szükséges fájlokhoz és erőforrásokhoz, bárhol legyenek is.
A részleteket lásd: [A vállalati erőforrások hozzáférésének engedélyezése a Microsoft Intune-nal](enable-access-to-company-resources-with-microsoft-intune.md).


Az Intune-szabályzatok teljes listáját lásd: [A Microsoft Intune szabályzatainak ismertetése](microsoft-intune-policy-reference.md).




## Konfigurációs házirend létrehozása

1.  A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Házirend** &gt; **Konfigurációs szabályzatok** &gt; **Hozzáadás** lehetőséget.

2.  Válassza ki a kívánt házirendet, és válassza a hozzá ajánlott beállítások használatát (ha elérhető; a beállítások később módosíthatók), vagy hozzon létre egyéni házirendet a saját beállításaival.

    > [!TIP] A megfelelő szabályzat kiválasztásához [A Microsoft Intune szabályzatainak ismertetése](microsoft-intune-policy-reference.md) témakörben talál segítséget.

3.  Amikor elkészült, válassza a **Házirend létrehozása** lehetőséget.

4.  A **Házirend létrehozása** képernyőn adja meg a házirend nevét, illetve igény szerint a leírását.

5.  Konfigurálja a kívánt házirend-beállításokat, majd válassza a **Házirend mentése** lehetőséget.

    Ha segítségre van szüksége bármelyik házirend-beállítással kapcsolatban, válassza ki a házirendtípust a következő listából:

    - [iOS-eszközbeállítások](ios-policy-settings-in-microsoft-intune.md)
    - [Android-eszközbeállítások](android-policy-settings-in-microsoft-intune.md)
    - [Windows 8 és Windows 8.1 rendszerű eszközök beállításai](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Windows Phone 8.1 rendszerű eszközök beállításai](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Windows 10 rendszerű asztali és mobileszközök beállításai](windows-10-policy-settings-in-microsoft-intune.md)
    - [Windows Team-eszközök beállításai](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [A Windows-kiadás frissítésének beállításai](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Mac OS X-eszközbeállítások](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Az Exchange ActiveSync-beállításai](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [A használati feltételekre vonatkozó házirend beállításai](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Mobileszközök általános beállításai (örökölt)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  A megerősítő párbeszédpanelen válassza az **Igen** lehetőséget a házirend telepítéséhez, vagy a **Nem** lehetőséget, ha telepítés nélkül kívánja azt létrehozni.

Az új házirend megtekintéséhez és szerkesztéséhez keresse meg azt az egyes házirendtípusok szakaszaiban a **Házirend** munkaterületen.

Ha olyan házirendet hoz létre, amely az ajánlott beállításokat alkalmazza, akkor az új házirend neve a sablon nevének, dátumának és időpontjának kombinációjából tevődik össze. Ha szerkeszti a házirendet, a neve módosul a szerkesztés dátumával és időpontjával.

A létrehozott házirendet általában telepíteni kell egy vagy több felhasználó- vagy eszközcsoportra.

> [!TIP]
> Nem minden házirendtípust kell telepíteni. A mobilalkalmazás-kezelési házirend például nem igényel telepítést. Ezt a házirendtípus egy alkalmazáshoz kell társítani, és ezután az alkalmazást kell telepíteni.

## Konfigurációs szabályzat telepítése

1.  A **Házirend** munkaterületen válassza ki a telepíteni kívánt házirendet, majd kattintson a **Központi telepítés kezelése** elemre.

2.  A **Telepítések kezelése** párbeszédpanelen:

    -   **A házirend telepítése** – Válasszon ki egy vagy több olyan csoportot, amelynek telepíteni kívánja a házirendet, majd kattintson a **Hozzáadás** &gt; **OK** gombra.

    -   **A párbeszédpanel bezárása telepítés nélkül** – Kattintson a **Mégse** gombra.

Ha egy már telepített házirendet választ ki, a házirendlista alsó részén további információkat láthat róla.

## A szabályzatok kezelése

1.  A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Házirend** lehetőséget, majd keresse meg és válassza ki a kezelni kívánt házirendet.

2.  Válasszon a következő lehetőségek közül:

- **Szerkesztés** – Megnyitja a kiválasztott szabályzat tulajdonságait, hogy módosíthassa őket.
- **Törlés** – Törli a kiválasztott házirendet.<br>Ha töröl egy házirendet, az minden olyan csoportból törlődik, ahol telepítve volt.
- **Központi telepítés kezelése** – Válassza ki azt a csoportot, amely számára telepíteni kívánja a házirendet, majd válassza a **Hozzáadás** lehetőséget.


## A Microsoft Intune szabályzataival kapcsolatban gyakran felmerülő kérdések

### Mennyi időt vesz igénybe, hogy a mobileszközök megkapják a házirendet vagy az alkalmazásokat a telepítés után?
Egy házirend vagy alkalmazás telepítésekor az Intune megpróbálja értesíteni az eszközt, hogy jelentkezzen be az Intune-ba. Ez általában 5 percnél kevesebb időt vesz igénybe.

Ha az eszköz az első értesítés után nem jelentkezik be, hogy beszerezze a házirendet, a szolgáltatás 3 további kísérletet tesz.  Ha az eszköz kapcsolat nélküli állapotban van (például ki van kapcsolva vagy nem kapcsolódik hálózathoz), előfordulhat, hogy nem kapja meg az értesítéseket.

Ebben az esetben az eszköz az Intune szolgáltatásba való következő ütemezett bejelentkezéskor szerzi be a házirendet a következő módon:

- iOS – 6 óránként
- Android – 8 óránként
- Windows Phone – 8 óránként
- Regisztrált Windows RT-eszközök – 24 óránként
- Eszközként regisztrált Windows 8.1 és Windows 10-számítógépek – 8 óránként

Ha az eszköz nemrég lett regisztrálva, a bejelentkezés gyakoribb lesz, a következőképpen:

- iOS – 6 órán át 15 percenként, majd 6 óránként
- Android – 15 percen át 3 percenként, majd 2 órán át 15 percenként, majd 8 óránként
- Windows Phone – 15 percen át 5 percenként, majd 2 órán át 15 percenként, majd 8 óránként
- Eszközként regisztrált Windows-számítógépek – 30 percen át 3 percenként, majd 24 óránként

A felhasználók emellett a vállalati portál alkalmazás elindításával bármikor jelentkezhetnek a házirend beszerzéséhez.

### Milyen műveletek hatására küld az Intune azonnal értesítést egy eszközre?
Az eszközök akkor jelentkeznek be az Intune-ba, amikor a bejelentkezésre felhívó értesítést kapnak, vagy a fenti táblázatokban látható ütemezett alkalmakkor.  Ha a művelet, például a törlés, a zárolás, a jelszó-visszaállítás, az alkalmazástelepítés, a profiltelepítés (Wi-Fi, VPN, e-mail stb.) vagy a szabályzattelepítés kifejezetten egy eszközre vagy felhasználóra vonatkozik, az Intune azonnal megpróbálja értesíteni az eszközt, hogy be kell jelentkeznie az Intune szolgáltatásba a frissítések fogadásához.

Az egyéb módosítások – például a kapcsolattartási adatok módosítása a vállalati portálon – nem indítják el az azonnali értesítések küldését az eszközök felé.

> [!TIP]
> Amikor beállításokat tartalmazó házirendet telepít egy Android-eszközre, a rendszer megkéri a felhasználót, hogy intézkedjen a házirendnek való megfelelés biztosítása érdekében. Amíg a felhasználók nem intézkednek, illetve az eszköz újraindításáig az új házirend-beállítások nem lépnek érvénybe.

### Ha ugyanazon felhasználó vagy eszköz számára több házirend is települ, honnan tudható, hogy melyik beállítások lesznek érvényben?
Fontos, hogy ha több házirendet telepít ugyanazon felhasználó vagy eszköz számára, az alkalmazni kívánt beállítás értékelése az egyes értékelések szintjén történik.

-   A megfelelőségi házirend-beállítások mindig prioritást élveznek a konfigurációs házirend-beállításokkal szemben

-   Ha egy beállítás több megfelelőségi házirendben is szerepel, akkor a szigorúbb megfelelőségi beállítás lesz érvényes

-   Ha egy beállítás több konfigurációs házirendben is szerepel, akkor a szigorúbb konfigurációs beállítás lesz érvényes

### Mi történik, ha a mobilalkalmazás-kezelési (MAM) házirendek ütköznek egymással? Melyik lesz érvényes az alkalmazásra?
Az ütközési értékek a mobilalkalmazás-kezelési házirendek legkorlátozóbb beállításai a számbeviteli mezők kivételével (ilyen például a PIN-kód beviteli próbálkozások száma az alaphelyzetbe állítás előtt).  A számbeviteli mezők értéke ugyanaz lesz, mintha a konzolban hozna létre egy MAM-házirendet a javasolt beállításokkal.

Akkor történik ütközés, ha két azonos házirend-beállítás van.  Például előfordulhat, hogy a másolás/beillesztés beállításra két megegyező MAM-házirendet konfigurált.  Ebben az esetben a másolás/beillesztés beállítás a legszigorúbb értékre lesz állítva, a többi beállítás pedig a konfiguráltak szerint lesz megadva.

Ha az alkalmazáshoz telepít és érvénybe léptet egy házirendet, majd egy másikat is telepít, akkor az első elsőbbséget élvez és érvényben marad, a második pedig ütközést jelez. Ha azonban egyszerre telepíti őket, tehát nincs első házirend, akkor mindkettő ütközést jelez, és a legszigorúbb beállítás lesz érvényes.

### Mi történik, ha az egyéni iOS-házirendek ütköznek?
Az Intune nem értékeli az Apple konfigurációs fájlok vagy az egyéni OMA-URI házirendek tartalmát, csak kézbesítési módszerként funkcionál.

Ezért ha egyéni házirendet telepít, győződjön meg arról, hogy a konfigurált beállítások nem ütköznek a megfelelőségi, konfigurációs vagy az egyéb egyéni házirendekkel. A beállítási ütközést tartalmazó egyéni házirendekben a beállítások alkalmazásának sorrendje véletlenszerű.

### Mi történik, ha egy szabályzatot törölnek, vagy a szabályzat alkalmazhatatlanná válik?
Amikor töröl egy házirendet, vagy eltávolít egy olyan eszközt a csoportból, amelyen a házirend telepítve volt, akkor a házirend és a beállítások a következő táblázatban összefoglaltak szerint törlődnek az adott eszközről:

#### Regisztrált eszközök

- Wi-Fi, VPN, tanúsítvány és e-mail profilok – Ezek a profilok az összes támogatott regisztrált eszközről el lesznek távolítva.
- Minden egyéb házirendtípus
    - **Windows és Android rendszerű eszközök** – A beállítások nem törlődnek az eszközről.
    - **Windows Phone 8.1 rendszerű eszközök** – A következő beállítások törlődnek:
        - Jelszó szükséges a mobileszközök feloldásához
        - Egyszerű jelszavak engedélyezése
        - Jelszó minimális hossza
        - Kötelező jelszótípus
        - Jelszó lejárata (nap)
        - Jelszóelőzmények megjegyzése
        - Megengedett sikertelen bejelentkezések száma az eszközön tárolt adatok törléséig – Jelszó kérése ennyi perc inaktivitás után – Megkövetelt jelszótípus – Karakterkészletek minimális száma – Kamera engedélyezése – Titkosítás megkövetelése mobileszközökön – Cserélhető tároló engedélyezése – Webböngésző engedélyezése – Alkalmazás-áruház engedélyezése – Képernyőfelvétel-készítés engedélyezése – Földrajzi hely meghatározásának engedélyezése – Microsoft-fiók használatának engedélyezése – Másolás és beillesztés engedélyezése – Wi-Fi alapú internetmegosztás engedélyezése – Ingyenes Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése – Wi-Fi elérési pontok jelentésének engedélyezése – Gyári beállítások visszaállításának engedélyezése – Bluetooth engedélyezése – NFC engedélyezése – Wi-Fi engedélyezése
    
    - **iOS** – Az összes beállítás törlődik, kivéve a következőket:
        - Hangroaming használatának engedélyezése
        - Adatroaming használatának engedélyezése
        - Automatikus szinkronizálás engedélyezése roaming közben

#### Az Intune ügyfélszoftvert futtató Windows rendszerű számítógépek

- **Endpoint Protection-beállítások** – A beállítások visszaállnak az ajánlott értékekre. Az egyetlen kivétel a **Csatlakozás a Microsoft Active Protection Service szolgáltatáshoz** beállítás, amelynek az alapértelmezett értéke **Nem**. A részleteket lásd: [Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Szoftverfrissítések beállításai** – A beállítások az operációs rendszer alapértelmezett állapotára állnak vissza. A részleteket lásd: [Windows rendszerű számítógépek naprakészen tartása szoftverfrissítésekkel a Microsoft Intune-ban](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **A Microsoft Intune Center beállításai** – Minden olyan támogatási kapcsolattartási adat törlődik a számítógépről, amelyet a szabályzat adott meg.
- **A Windows tűzfal beállításai** – A beállítások a számítógép operációs rendszerének alapértelmezett értékeire állnak vissza. A részleteket lásd: [Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).


### A szabályzatok frissítése az eszközökön a naprakész állapot biztosításához (csak az Intune ügyfélszoftvert futtató Windows rendszerű számítógépekre vonatkozik)

1.  Bármely eszközcsoportban válassza ki azokat az eszközöket, amelyeknek a házirendjeit frissíteni kívánja, majd válassza a **Távoli feladatok** &gt; **Házirendek frissítése** lehetőségre.
2.  A feladat állapotának megtekintéséhez válassza az Intune felügyeleti konzoljának jobb alsó sarkában lévő **Távoli feladatok** elemet.

### Hol találhatok segítséget a szabályzatokkal kapcsolatos problémák elhárításához?

Lásd a [Troubleshoot policies in Microsoft Intune](../Troubleshoot/troubleshoot-policies-in-microsoft-intune) (Szabályzatokkal kapcsolatos problémák elhárítása a Microsoft Intune-ban) című témakört.


<!--HONumber=Jun16_HO3-->


