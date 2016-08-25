---
title: "PFX-tanúsítványinfrastruktúra konfigurálása | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 05/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6edb37708d26033358af30c47e955b20caedb6fd
ms.openlocfilehash: 51def9dc80043bbf5a71578fb44cae9259fd48b1



---
# Tanúsítványinfrastruktúra konfigurálása
Ez a témakör a tanúsítványprofilok létrehozásával és telepítésével kapcsolatos tudnivalókat ismerteti.

Ha bármilyen tanúsítványalapú hitelesítést szeretne végrehajtani a szervezetben, szüksége lesz egy vállalati hitelesítésszolgáltatóra.

A PFX-tanúsítványprofilok használatához a vállalati hitelesítésszolgáltatón kívül a következőkre is szüksége lesz:

-   Egy számítógép, amely képes kommunikálni a hitelesítésszolgáltatóval. Alternatív megoldásként használhatja magát a hitelesítésszolgáltató számítógépet is.

 -  A hitelesítésszolgáltatóval kommunikálni képes számítógépen futó Intune Certificate Connector.

## A helyszíni infrastruktúra leírása


-    **Active Directory-tartomány**: A jelen szakaszban felsorolt összes kiszolgálónak (a webalkalmazás-proxykiszolgáló kivételével) csatlakoznia kell a szervezet Active Directory-tartományához.

-  **Hitelesítésszolgáltató** (CA): Olyan vállalati hitelesítésszolgáltató (CA), amely a Windows Server 2008 R2 vagy újabb rendszer vállalati verzióján fut. Az önálló hitelesítésszolgáltató nem támogatott. A hitelesítésszolgáltató konfigurálásáról lásd: [Hitelesítésszolgáltató telepítése](http://technet.microsoft.com/library/jj125375.aspx).
    Ha a hitelesítésszolgáltatója Windows Server 2008 R2 rendszeren fut, [telepítenie kell a KB2483564 jelű gyorsjavítást](http://support.microsoft.com/kb/2483564/).

 -  **Egy számítógép, amely képes kommunikálni a hitelesítésszolgáltatóval**: Másik megoldásként használhatja magát a hitelesítésszolgáltató számítógépet is.
-  **Microsoft Intune Certificate Connector**: Az Intune felügyeleti konzollal töltse le a **Certificate Connector** (Tanúsítvány-összekötő) telepítőjét (**ndesconnectorssetup.exe**). Ezután futtassa az **ndesconnectorssetup.exe** fájlt azon a számítógépen, amelyre telepíteni szeretné az tanúsítvány-összekötőt. A . PFX-tanúsítványprofilok esetében a hitelesítésszolgáltatóval kommunikáló számítógépre telepítse a tanúsítvány-összekötőt.
-  **Webalkalmazás-proxykiszolgáló** (nem kötelező): Webalkalmazás-proxykiszolgálóként (WAP) használhat olyan kiszolgálót, amelyen a Windows Server 2012 R2 vagy újabb verziójú rendszer fut. Ez a konfiguráció:
    -  Lehetővé teszi, hogy az eszközök az interneten keresztül fogadjanak tanúsítványokat.
    -  Biztonsági ajánlás olyan környezetekben, ahol az eszközök az interneten keresztül csatlakozva kapnak és újítanak meg tanúsítványokat.

 > [!NOTE]           
> -    A WAP-ot futtató kiszolgálón [telepíteni kell egy frissítést](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ahhoz, hogy az támogassa az NDES által használt hosszú URL-eket. Ez a frissítés megtalálható a [2014. decemberi kumulatív frissítésben](http://support.microsoft.com/kb/3013769), illetve önállóan a [KB3011135-as jelű frissítésként](http://support.microsoft.com/kb/3011135).
>-  Ezenkívül a WAP-ot futtató kiszolgálónak rendelkeznie kell egy SSL-tanúsítvánnyal, amely a külső ügyfeleknek közzétett nevet egyezteti, valamint meg kell bíznia az NDES-kiszolgálón használt SSL-tanúsítványban. E tanúsítványok segítségével a WAP-kiszolgáló képes megszakítani az ügyfelek SSL-kapcsolatát, illetve új SSL-kapcsolatot létrehozni az NDES-kiszolgálóval.
    A WAP-hoz szükséges tanúsítványokkal kapcsolatos további tudnivalókért olvassa el a **Tanúsítványok megtervezése** című szakaszt a [Felkészülés az alkalmazások webalkalmazás-proxyval való közzétételére](https://technet.microsoft.com/library/dn383650.aspx) című cikkben. A WAP-kiszolgálókkal kapcsolatos általános információkért tekintse meg [A webalkalmazás-proxy használata](http://technet.microsoft.com/library/dn584113.aspx) című témakört.|


### Tanúsítványok és sablonok

|Objektum|Részletek|
|----------|-----------|
|**Tanúsítványsablon**|Ezt a sablont a vállalati hitelesítésszolgáltatón tudja konfigurálni.|
|**Megbízható legfelső szintű hitelesítésszolgáltató tanúsítványa**|Ezt a tanúsítványt **.cer** fájlként kell exportálnia a vállalati hitelesítésszolgáltatótól vagy bármely olyan eszközről, amely megbízik a vállalati hitelesítésszolgáltatóban, majd központilag telepítenie kell az eszközökre a megbízható hitelesítésszolgáltatói tanúsítványprofillal.<br /><br />Operációsrendszer-platformonként egy darab megbízható legfelső szintű hitelesítésszolgáltatói tanúsítványt használjon, és társítsa azt az egyes létrehozott megbízható főtanúsítvány-profilokkal.<br /><br />Szükség esetén további megbízható legfelső szintű hitelesítésszolgáltatói tanúsítványokat is használhat. Ezzel például bizalmi kapcsolatot alakíthat ki egy hitelesítésszolgáltatónak, mely aláírja a kiszolgálói hitelesítési tanúsítványokat a szervezet Wi-Fi hozzáférési pontjai számára.|


## Az infrastruktúra konfigurálása
A tanúsítványprofilok konfigurálása előtt végre kell hajtania az alábbi feladatokat, melyekhez a Windows Server 2012 R2 rendszerhez és az Active Directory tanúsítványszolgáltatásokhoz (ADCS) kapcsolódó ismeretek szükségesek:

**1. feladat** – Tanúsítványsablonok konfigurálása a hitelesítésszolgáltatón **2. feladat** – Az Intune tanúsítvány-összekötő engedélyezése, telepítése és konfigurálása

### 1. feladat – Tanúsítványsablonok konfigurálása a hitelesítésszolgáltatónál
Ebben a feladatban teszi közzé a tanúsítványsablont.

##### A hitelesítésszolgáltató konfigurálásához

1.  A vállalati hitelesítésszolgáltatónál a Tanúsítványsablonok beépülő modullal hozzon létre egy új egyéni sablont (vagy másoljon és szerkesszen egy meglévő sablont, például a Felhasználó sablont) a .pFX szolgáltatással való használatra.

    A sablonnak az alábbi beállításokkal kell rendelkeznie:

    -   Adjon meg egy leíró nevet a sablonnak a **Sablon megjelenítendő neve** mezőben.

    -   A **Tulajdonos neve** lapon válassza **A kérelem fogja tartalmazni**lehetőséget. (A biztonságot az Intune NDES-házirendmodulja fogja érvényesíteni.)

    -   A **Kiterjesztések** lapon győződjön meg róla, hogy az **Alkalmazás-házirendek leírása** lista tartalmazza az **Ügyfél-hitelesítés**elemet.

        > [!IMPORTANT]
        > iOS- és Mac OS X-tanúsítványsablonok esetében a **Kiterjesztések** lapon szerkessze a **Kulcshasználat** beállítást, és győződjön meg arról, hogy **Az aláírás az eredet igazolása** lehetőség nincs kiválasztva.


3.  Ellenőrizze az **Érvényesség időtartama** beállítást a sablon **Általános** lapján. Alapértelmezés szerint az Intune a sablonban konfigurált értéket használja. Lehetősége van azonban arra is, hogy a hitelesítésszolgáltató konfigurálásával engedélyezze a kérelmezőnek egy másik érték megadását, amelyet aztán az Intune felügyeleti konzoljából tud megadni. Ha azt szeretné, hogy mindig a sablonban lévő érték legyen használva, hagyja ki ennek a lépésnek a hátralévő részét.

    > [!IMPORTANT]
    > Az iOS és a Mac OS X platform mindig a sablonban beállított értéket használja, minden más konfigurációs beállítástól függetlenül.

    Ha a hitelesítésszolgáltató konfigurálásával lehetővé kívánja tenni a kérelmezőnek az érvényességi időszak megadását, futtassa az alábbi parancsokat a hitelesítésszolgáltatón:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  Tegye közzé a Hitelesítésszolgáltató beépülő modullal a tanúsítványsablont a vállalati hitelesítésszolgáltatón.

    1.  Válassza a **Tanúsítványsablonok** csomópontot, kattintson a **Művelet**-&gt; **Új** &gt; **Kiállítandó tanúsítványsablon** lehetőségre, majd válassza ki a 2. lépésben létrehozott sablont.

    2.  Ellenőrizze a **Tanúsítványsablonok** mappában, hogy a sablon közzététele sikerült-e.

5.  A hitelesítésszolgáltató számítógépen győződjön meg róla, hogy az Intune tanúsítvány-összekötő gazdagépe rendelkezik-e regisztrálási engedéllyel, hogy hozzáférhessen a .PFX-profil létrehozásakor használt sablonhoz. Állítsa be az engedélyt a hitelesítésszolgáltató számítógép tulajdonságainak **Biztonság** lapján.

### 2. feladat – Az Intune tanúsítvány-összekötő engedélyezése, telepítése és konfigurálása
A feladat tartalma:

A tanúsítvány-összekötő letöltése, telepítése és konfigurálása

##### A tanúsítvány-összekötő támogatásának engedélyezéséhez

1.  Nyissa meg az [Intune felügyeleti konzolját](https://manage.microsoft.com), és válassza a **Felügyelet** &gt; **Tanúsítvány-összekötő** lehetőséget.

2.  Kattintson a **Helyszíni tanúsítvány-összekötő konfigurálása** elemre.

3.  Válassza az **Enable Certificate Connector**(Certificate Connector engedélyezése) lehetőséget, és kattintson az **OK**gombra.

##### A tanúsítvány-összekötő letöltéséhez, telepítéséhez és konfigurálásához

1.  Nyissa meg az [Intune felügyeleti konzolját](https://manage.microsoft.com), és kattintson a **Felügyelet** &gt; **Mobileszköz-kezelés** &gt; **Tanúsítvány-összekötő** &gt; **Tanúsítvány-összekötő letöltése** lehetőségre.

2.  A letöltés befejezése után futtassa a letöltött telepítőt (**ndesconnectorssetup.exe**):

  Futtassa a telepítőt azon a számítógépen, amely kapcsolódni tud a hitelesítésszolgáltatóhoz. Válassza a .PFX típusú tanúsítványt terjesztő beállítást, és kattintson a Telepítés elemre. A telepítés befejezése után következő lépésként hozzon létre egy tanúsítványprofilt a [Tanúsítványprofilok konfigurálása](configure-intune-certificate-profiles.md) témakörben leírtaknak megfelelően.

   <!-- Not sure about step 3 below -->

3.  Ha a rendszer kéri az ügyféltanúsítványt a tanúsítvány-összekötőhöz, kattintson a **Kijelölés** lehetőségre, és válassza ki a 3. feladatban telepített **ügyfél-hitelesítő** tanúsítványt.

    Miután kiválasztotta az ügyfél-hitelesítési tanúsítványt, a rendszer visszairányítja az **Client Certificate for Microsoft Intune Certificate Connector** (Ügyféltanúsítvány a Microsoft Intune Certificate Connectorhoz) felületre. Bár a választott tanúsítvány nem látható, kattintson a **Tovább** gombra a tanúsítvány tulajdonságainak megtekintéséhez. Ezután kattintson ismét a **Tovább**gombra, majd a **Telepítés**gombra.

4.  Ha a varázsló befejeződött, még mielőtt bezárná, kattintson **Launch the Certificate Connector UI**(Certificate Connector felhasználói felületének indítása) lehetőségre.

    > [!TIP]
    > Ha bezárná a varázslót a tanúsítvány-összekötő felhasználói felületének megnyitása előtt, akkor az alábbi parancs futtatásával nyithatja meg:
    >
    > **&lt;telepítési_útvonal&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  A **Certificate Connector** (Tanúsítvány-összekötő) felhasználói felületén:

    Kattintson a **Bejelentkezés** gombra, és írja be az Intune szolgáltatás rendszergazdai hitelesítő adatait, vagy egy bérlői rendszergazda globális felügyeleti engedéllyel rendelkező hitelesítő adatait.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    Váltson a **Speciális** lapra, adja meg egy olyan fiók hitelesítő adatait, amely rendelkezik **Tanúsítványok kiállítása és kezelése** engedéllyel a vállalati hitelesítésszolgáltatónál, majd kattintson az **Alkalmaz**gombra.

    Bezárhatja a tanúsítvány-összekötő felhasználói felületét.

6.  Nyisson meg egy parancssort, írja be a **services.msc** fájlnevet, nyomja meg az **Enter** billentyűt, kattintson a jobb gombbal az **Intune-összekötő szolgáltatás** elemre, és válassza az **Újraindítás** parancsot.

A szolgáltatás futásának ellenőrzéséhez nyisson meg egy böngészőt, és írja be az alábbi URL-t, melynek egy **403-as** hibát kell visszaadnia:

**http:// &lt;NDES-kiszolgáló_teljes_tartományneve&gt;/certsrv/mscep/mscep.dll**

### További lépések
Ezzel készen áll a tanúsítványprofilok konfigurálására, amelyről a következő témakörben olvashat: [Tanúsítványprofilok konfigurálása](Configure-Intune-certificate-profiles.md).



<!--HONumber=Jun16_HO4-->


