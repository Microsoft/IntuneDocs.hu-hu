---
# required metadata

title: Wi-Fi-kapcsolatok | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Wi-Fi-kapcsolatok a Microsoft Intune-ban
A Microsoft Intune Wi-Fi profiljaival vezeték nélküli hálózati beállításokat adhat meg a szervezet felhasználói és eszközei számára. A beállításokkal a felhasználók egyszerűbben csatlakozhatnak a vezeték nélküli hálózatokhoz.

Tegyük fel például, hogy egy új, **Contoso Wi-Fi** nevű vezeték nélküli hálózatot helyezett üzembe, és szeretné beállítani, hogy az összes iOS-eszköz kapcsolódjon ehhez a hálózathoz. Ennek folyamata a következő:

1.   Hozza létre a **Contoso Wi-Fi** vezeték nélküli hálózathoz való csatlakozás beállításait tartalmazó Wi-Fi profilt.

2. Telepítse a profilt az iOS-eszközzel rendelkező felhasználók csoportjában.

3.   A felhasználók megtalálják az új **Contoso Wi-Fi** hálózatot a vezeték nélküli hálózatok között, és könnyedén csatlakoznak hozzá.

A Wi-Fi-profilok a következő platformokon telepíthetők:

-   Android 4.0 és újabb verziók

-   iOS 7.1-es és újabb verziók

-   Mac OS X 10.9 és újabb verziók

A Windows 8.1 vagy újabb rendszert futtató eszközökre importálhatja az előzőleg fájlba exportált Wi-Fi konfigurációs profilt. Részletekért lásd a jelen témakör „Wi-Fi profil importálása” című szakaszát.

## Wi-Fi profil létrehozása

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) kattintson a **Házirend** &gt; **Házirend hozzáadása** elemre.

2.  Válassza ki a következő házirendtípusok egyikét, majd kattintson a **Házirend létrehozása**lehetőségre:

    -   **Wi-Fi profil (Android 4 és újabb)**

    -   **Wi-Fi profil (iOS 7.1 és újabb)**

    -   **Wi-Fi-profil (Mac OS X 10.9 és újabb verziók)**

    Ehhez a házirendtípushoz nincsenek ajánlott beállítások, Egyéni házirendet kell létrehoznia.

3.  Adja meg a profil nevét és leírását.

4. Adja meg a **Hálózati kapcsolatok** beállítás értékeit:

  |Beállítás|További információk| |-----------|--------------------|
|**Hálózatnév**|Adjon meg egy leíró nevet a vezeték nélküli hálózathoz. Ez a név fog megjelenni a felhasználó eszközén a vezeték nélküli hálózat kiválasztásakor.| |**SSID (Service Set Identifier, szolgáltatáskészlet-azonosító)**|Adja meg azon vezeték nélküli hálózat SSID azonosítóját, amelyhez csatlakozni kíván. Az SSID azonosító megkülönbözteti a kis- és nagybetűket, és a felhasználók számára nem jelenik meg.| |**Automatikus csatlakozás, ha a hálózat hatótávolságon belül van**|Kapcsolja be ezt a funkciót, ha szeretné, hogy az eszközök automatikusan csatlakozzanak a vezeték nélküli hálózathoz, amikor annak hatótávolságán belül vannak.| |**Csatlakozás akkor is, ha a hálózat nem közli a nevét (SSID azonosítóját)**|Kapcsolja be ezt a funkciót, ha szeretné engedélyezni, hogy az eszközök akkor is csatlakozzanak a hálózathoz, amikor az nem látható a hálózatlistában (mivel rejtett, vagy nem közli a nevét).|

5. Konfigurálja a kijelölt platform **Biztonsági beállításait** . A rendelkezésre álló beállítások a választott biztonsági típusoktól függnek.

  #### Android eszközök esetén

  |Beállítás neve|További információk|Használat:| |----------------|--------------------|-------------|
|**Biztonság típusa**|Válassza ki a vezeték nélküli hálózat biztonsági protokollját:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Nincs hitelesítés (nyílt)**, ha a hálózat nem biztonságos.|Mindig| |**EAP típusa**|Válassza ki az EAP protokoll biztonságos vezeték nélküli kapcsolatok hitelesítéséhez használni kívánt típusát:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Ön a **WPA-Enterprise/WPA2-Enterprise** biztonsági típust választotta.| |**Kiszolgálói érvényesítéshez használandó főtanúsítványok**|Kattintson a **Kiválasztás** elemre, majd válassza ki a kapcsolat hitelesítéséhez használt megbízható főtanúsítvány-profilt. **Fontos:** Megbízható főtanúsítvány-profil létrehozásához lásd: [Erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md).|Az **EAP típusa** bármelyik lehet.| |**Hitelesítési módszer**|Válassza ki a kapcsolat esetében használni kívánt hitelesítési módszert:<br /><br />-   **Tanúsítványok** , ha meg kell adni az ügyféltanúsítványt<br />-   **Felhasználónév és jelszó**, ha más hitelesítési módszert szeretne megadni|Az **EAP típusa** beállítás értéke **PEAP** vagy **EAP-TTLS**.| |**Hitelesítéshez használandó nem EAP-módszer (belső identitás)**|Adja meg, hogy hogyan szeretné hitelesíteni a kapcsolatot:<br /><br />-   **Nincsenek**<br />-   **Titkosítatlan jelszó (PAP)**<br />-   **Challenge Handshake Authentication Protocol (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP 2-es verzió (MS-CHAPV2)**<br /><br />Az elérhető lehetőségek köre a kiválasztott EAP-típustól függ.|A **Hitelesítési módszer** a **Felhasználónév és jelszó**.| |**Identitásadatok védelmének engedélyezése (külső identitás)**|Adja meg az EAP-identáskérésekre válaszul küldendő szöveget. Ez a szöveg tetszőleges érték lehet. A hitelesítés során a rendszer először ezt a név nélküli identitást küldi el, ezt követi a valódi identitás, amelyet egy biztonságos alagúton keresztül továbbít a rendszer.|Az **EAP típusa** beállítás értéke **PEAP** vagy **EAP-TTLS**.| |**Válasszon ki egy, az ügyfél-hitelesítéshez használandó ügyféltanúsítványt (identitástanúsítványt)**|Kattintson a **Kiválasztás** elemre, majd válassza ki a kapcsolat hitelesítéséhez használni kívánt SCEP-tanúsítványprofilt. **Fontos:** SCEP-tanúsítványprofil létrehozásához lásd: [Erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md).|A biztonság típusa **WPA-Enterprise/WPA2-Enterprise**, az **EAP típusa** pedig bármelyik lehet.|

  #### iOS- és Mac OS X-eszközök esetén

  |Beállítás neve|További információk|Használat:| |----------------|--------------------|-------------|
|**Biztonság típusa**|Válassza ki a vezeték nélküli biztonsági protokollt:<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Nincs hitelesítés (nyílt)**, ha a hálózat nem biztonságos.|Mindig| |**EAP típusa**|Válassza ki az EAP protokoll biztonságos vezeték nélküli kapcsolatok hitelesítéséhez használni kívánt típusát:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|A **WPA-Enterprise/WPA2-Enterprise** biztonsági típust választotta.| |**Megbízható kiszolgálók tanúsítványainak nevei**|Válassza ki a kapcsolat hitelesítéséhez használt megbízható főtanúsítvány-profilt. **Fontos:** A megbízható főtanúsítvány létrehozásával kapcsolatban lásd: [Erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md).|A következő EAP-típusok valamelyikét választotta: **EAP-TLS**, **PEAP**, **EAP-TTLS** vagy **EAP-FAST**.| |**PAC használata**|Válassza ezt a lehetőséget, ha védett hozzáférési hitelesítő adatok segítségével szeretné létrehozni a hitelesített alagutat az ügyfél és a hitelesítési kiszolgáló között. A rendszer az esetlegesen rendelkezésre álló PAC-fájlokat használja.|Az **EAP típusa** beállítás értéke a következő: **EAP-FAST**.| |**PAC kiépítése**|A PAC-fájl kiosztása az eszközök számára.<br /><br />Használatakor a **PAC anonim kiépítése** lehetőséget is bejelölheti, ha a PAC-fájlt a kiszolgáló hitelesítése nélkül szeretné kiosztani.|A **PAC használata** beállítás ki van választva.||**Hitelesítési módszer**|Adja meg a kapcsolatnál használni kívánt hitelesítési módszert:<br /><br /><ul><li>**Tanúsítványok** , ha meg kell adni az ügyféltanúsítványt</li><li>**Felhasználónév és jelszó**, ha meg kell adni a következő nem EAP-alapú módszerek egyikét a hitelesítéshez (más néven Belső identitás):<br /><br /><ul><li>**Nincsenek**</li><li>**Titkosítatlan jelszó (PAP)**</li><li>**Challenge Handshake Authentication Protocol (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP 2-es verzió (MS-CHAPV2)**</li><li>**EAP-TLS**</li></ul></li></ul>|Az **EAP típusa** beállítás értéke **PEAP** vagy **EAP-TTLS**.| |**Válasszon ki egy, az ügyfél-hitelesítéshez használandó ügyféltanúsítványt (identitástanúsítványt)**|Válassza ki a kapcsolat hitelesítéséhez használandó SCEP-tanúsítványprofilt. **Fontos:** SCEP-tanúsítványprofil létrehozásához lásd: [Erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md).|Ha a biztonság típusa **WPA-Enterprise/WPA2-Enterprise**, az **EAP típusa** pedig **EAP-TLS**, **PEAP** vagy **EAP-TTLS**.| |**Identitásvédelem engedélyezése (Külső identitás)**|Adja meg az EAP-identitáskérésre válaszul küldendő szöveget. Ez a szöveg tetszőleges érték lehet.<br /><br />A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.|Ha az **EAP típusa** **PEAP**, **EAP-TTLS** vagy **EAP-FAST**.|

6. **Proxybeállítások** konfigurálása (csak iOS és MAC OS X)

    |Beállítás neve|További információ|A következő esetekben használja:|
    |----------------|-------------------|-------------|
    |**Proxybeállítások a Wi-Fi kapcsolathoz**|Válassza ki a proxybeállítások típusát:<br /><br />-   **Nincs** (alapértelmezett)<br />-   **Kézi** – Manuálisan adja meg a proxykiszolgáló URL-címét és portszámát.<br />-   **Automatikus** – A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja.|Mindig|
    |**Proxykiszolgáló címe** és **Portszám**|Adja meg a proxykiszolgáló URL-címét és portszámát.|**A Wi-Fi kapcsolat proxybeállításai** beállítás értéke **Kézi**|
    |**Proxykiszolgáló URL-címe**|Adja meg a proxykiszolgáló beállításait tartalmazó fájl URL-címét.|**A Wi-Fi kapcsolat proxybeállításai** beállítás értéke **Automatikus**|

7.  A Wi-Fi profil mentése

Az új szabályzat a **Házirend** munkaterület **Konfigurációs szabályzatok** csomópontjában jelenik meg. A profil hatályba léptetésével kapcsolatos tudnivalókat lásd: **További lépések**.

## Wi-Fi konfigurációs profil exportálása importálása (csak Windows 8.1 vagy újabb verzió esetén)

### Wi-Fi-profil exportálása
A Windows rendszerben a **netsh wlan** segédprogrammal az Intune által is olvasható XML-fájlba exportálhat egy meglévő Wi-Fi profilt. A szükséges Wi-Fi profillal már rendelkező Windows-számítógépen kövesse az alábbi eljárást.

1.  Hozzon létre egy helyi mappát az exportált W-Fi-profilokhoz, például a c:\WiFi mappát

2.  Nyisson meg egy parancssort rendszergazdaként.

3.  Futtassa a `netsh wlan show profiles` parancsot, és jegyezze fel az exportálni kívánt profil nevét.  Ebben a példában a profil neve: *WiFiName*.

4.  Futtassa ezt a parancsot: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Ezzel létrehozza a „Wi-Fi-WiFiName.xml” nevű Wi-Fi-profilfájlt a célmappában.

## Wi-Fi-profil importálása
A **Windows Wi-Fi házirend importálása** lehetőséggel importáljon egy Wi-FI beállításkészletet, amelyet ezután hozzárendelhet a megfelelő felhasználói vagy eszközcsoportokhoz. A Wi-Fi-profil exportálásának eljárásáról a következő szakaszban olvashat:

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) kattintson a **Házirend** &gt; **Házirend hozzáadása** elemre.

2.  Konfiguráljon egy **Windows** &gt; **Windows Wi-Fi házirend importálása** típusú házirendet.

    Csak egyéni Windows Wi-Fi importált házirendet hozhat létre és rendelhet hozzá. Ajánlott beállítások nem állnak rendelkezésre.

3.  Adja meg az alábbi általános értékeket a Windows Wi-Fi importált házirendhez:

    |Beállítás neve|További információ|
    |----------------|--------------------|
    |**Név**|Adjon meg egy egyedi nevet a Wi-Fi profilhoz, hogy a profil könnyebben azonosítható legyen az Intune konzolon.|
    |**Leírás**|Adja meg a Wi-Fi profil rövid leírását és egyéb kapcsolódó információkat, amelyek alapján a profil könnyen megtalálható lesz.|

4.  Az **Egyéni Wi-Fi profil** fejléc alatt adja meg a következő értékeket:

    |Beállítás neve|További információ|
    |----------------|--------------------|
    |**Konfigurációs profilfájl**|Az **Importálás** elemre kattintva válassza ki azt az XML-fájlt, amely az Intune-ba importálni kívánt Wi-Fi profilbeállításokat tartalmazza.|
    |**Egyéni konfigurációs profil neve (megjelenik a felhasználók számára)**|A Wi-Fi konfigurációs profil nevének megjelenítése abban a formában, ahogy a felhasználók eszközén is megjelenik majd.|
    |**Konfigurációs profil részletei**|Megjeleníti a kiválasztott konfigurációs profil XML-kódját.|

5.  Ha elkészült, kattintson a **Házirend mentése**gombra.

6.  Az új szabályzat a **Házirend** munkaterület **Konfigurációs szabályzatok** csomópontjában jelenik meg.

## A szabályzat telepítése

1.  A **Házirend** munkaterületen válassza ki a telepíteni kívánt házirendet, majd kattintson a **Központi telepítés kezelése**lehetőségre.

2.  A **Telepítések kezelése** párbeszédpanelen:

    -   **A házirend telepítése** – Válasszon ki egy vagy több olyan csoportot, amelynek telepíteni kívánja a szabályzatot, majd kattintson a **Hozzáadás** &gt; **OK** gombra.

    -   **A párbeszédpanel bezárása telepítés nélkül** – Kattintson a **Mégse** gombra.


A **Házirend** munkaterület **Áttekintés** lapján található állapotösszegzés és riasztások segítségével azonosíthatók a szabályzattal kapcsolatos, figyelmet igénylő problémák. Ezen felül egy állapotösszegzés megjelenik az Irányítópult munkaterületen is.

### További információ
Ismerje meg, hogyan hozhat létre Wi-Fi-profilt egy előmegosztott kulccsal: [Wi-Fi-profil létrehozása előmegosztott kulccsal](pre-shared-key-wi-fi-profile.md)


<!--HONumber=Jun16_HO1-->


