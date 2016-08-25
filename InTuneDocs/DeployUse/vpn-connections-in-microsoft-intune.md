---
title: VPN-kapcsolatok | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
ms.sourcegitcommit: 95abe7b12e68755f3c95f91888efd3e85c057119
ms.openlocfilehash: b55cf263611d6e90805cad9985eb8a5e7ebeb4a0


---

# VPN-kapcsolatok a Microsoft Intune-ban
 A virtuális magánhálózatok (VPN) segítségével biztonságos távoli hozzáférést biztosíthat felhasználóinak a vállalati hálózathoz. A távoli felhasználók úgy dolgozhatnak, mintha eszközük fizikailag kapcsolódna a hálózathoz. Az eszközök egy VPN-csatlakozási profil használatával kezdeményeznek kapcsolatot a VPN-kiszolgálóval. A Microsoft Intune **VPN-profiljainak** beállításával a szervezetében lévő felhasználókra és eszközökre alkalmazhatja a VPN-beállításokat. Ezen beállítások telepítésével lecsökkentheti a vállalati hálózaton lévő erőforrások eléréséhez szükséges végfelhasználói beavatkozást.

Tegyük fel például, hogy minden iOS-eszközön alkalmazni szeretné azokat a beállításokat, amelyek a vállalati hálózaton lévő egyik fájlmegosztáshoz való csatlakozáshoz szükségesek. Ehhez létre kell hoznia egy VPN-profilt, amely tartalmazza a vállalati hálózathoz való csatlakozáshoz szükséges beállításokat, majd ezt a profilt minden, iOS-eszközt használó felhasználóra alkalmaznia kell. A felhasználók látni fogják a VPN-kapcsolatot a rendelkezésre álló hálózatok listájában, és minimális erőfeszítéssel csatlakozhatnak.

VPN-profilokkal a következő típusú eszközök konfigurálhatók:

* Android 4 vagy újabb rendszerű eszközök
* Az iOS 7.1-es vagy újabb rendszerű eszközök
* A Mac OS X 10.9-es vagy újabb rendszerű eszközök
* A Windows 8.1-es vagy újabb verzióját futtató regisztrált eszközök
* A Windows Phone 8.1-es vagy újabb verzióját futtató eszközök
* A Windows 10 asztali és mobil verzióját futtató eszközök

A VPN-profil konfigurációs beállításai a kiválasztott eszköztípustól függően eltérnek.

## VPN-kapcsolat típusai

Az Intune a következő kapcsolattípusokat használó VPN-profilok létrehozását támogatja:




Kapcsolat típusa |iOS és Mac OS X  |Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows 10 asztali és mobil verziója |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Igen |Igen   |Nem    |     Nem    |Nem  |Nem    | Igen (OMA-URI, csak mobil)|     
Pulse Secure|Igen  |Igen |Igen   |Nem  |Igen  |Igen| Igen|        
F5 Edge Client|Igen |Igen |Igen |Nem  |Igen  |   Igen |  Igen|   
Dell SonicWALL Mobile Connect|Igen |Igen |Igen |Nem  |Igen |Igen |Igen|         
CheckPoint Mobile VPN|Igen |Igen |Igen |Igen |Igen|Igen|Igen|
Microsoft SSL (SSTP)|Nem |Nem |Nem |Nem |Nem|Nem|VPNv1 OMA-URI *|
Microsoft Automatic|Nem |Nem |Nem |Nem |Nem|Igen (OMA-URI)|Igen|
IKEv2|iOS-eszközök egyéni profilja|Nem |Nem |Nem |Nem|Igen (OMA-URI)|Igen|
PPTP|iOS-eszközök egyéni profilja|Nem |Nem |Nem |Nem|Nem|Igen|
L2TP|iOS-eszközök egyéni profilja|Nem |Nem |Nem |Nem|Igen (OMA-URI)|Igen|

\* A Windows 10-hez egyébként rendelkezésre álló további beállítások nélkül.

> [!IMPORTANT] Az eszközökre alkalmazott VPN-profilok használatához telepítenie kell a megfelelő VPN-alkalmazást a profilhoz. A megfelelő alkalmazás Intune-nal történő telepítéséhez a következő dokumentumban talál segítséget: [Alkalmazások telepítése a Microsoft Intune-ban](deploy-apps-in-microsoft-intune.md).  

 Az [Egyéni konfigurációk VPN-profilokhoz](custom-configurations-for-vpn-profiles.md) szakaszban tájékozódhat arról, hogy hogyan hozhat létre egyéni VPN-profilokat URI-beállításokkal.     

## A VPN-profilok védelmének biztosítása

A VPN-profilok számos különböző kapcsolattípust és különféle gyártóktól származó protokollt használhatnak. E kapcsolatok védelmét általában az alábbi két módszer egyikével biztosítják:

### Tanúsítványok

A VPN-profil létrehozásakor ki kell választania egy SCEP-vagy .PFX-tanúsítványprofilt, amelyet korábban az Intune-ban hozott létre.

Ez identitástanúsítványként is ismert, és segítségével hajtja végre a rendszer a hitelesítést egy olyan megbízható tanúsítványprofillal (vagy főtanúsítvánnyal), amelyet Ön annak érdekében hozott létre, hogy engedélyezze a felhasználó eszközének a csatlakozást. A megbízható tanúsítványt a rendszer a VPN-kapcsolatot hitelesítő számítógépre alkalmazza, amely általában a VPN-kiszolgáló.

A tanúsítványprofilok Intune-ban történő létrehozásáról és használatáról a következő dokumentumban olvashat bővebben: [Az erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md).

### Felhasználónév és jelszó

A felhasználó a VPN-kiszolgálón felhasználónév és jelszó megadásával végzi el a hitelesítést.

## VPN-profil létrehozása

1. A [Microsoft Intune felügyeleti konzolban](https://manage.microsoft.com) válassza a **Házirend > Házirend hozzáadása** elemet.
2. Válasszon sablont az új szabályzathoz a megfelelő eszköztípus kibontásával, majd válasszon VPN-profilt az eszköznek:
    * **VPN-profil (Android 4 és újabb)**
    * **VPN-profil (iOS 7.1 és újabb)**
    * **VPN-profil (Mac OS X 10.9 és újabb verziók)**
    * **VPN-profil (Windows 8.1 és újabb verziók)**
    * **VPN-profil (Windows Phone 8.1 és újabb)**
    * **VPN-profil (Windows 10 és újabb asztali és mobil verzió)**

    Csak egyéni házirendet hozhat létre és alkalmazhat a VPN-profilhoz. Ajánlott beállítások nem állnak rendelkezésre.

3. Az alábbi táblázat segítséget nyújt a VPN-profil beállításainak konfigurálásában:

Beállítás neve  |További információ  
---------|---------
**Név**     |Adjon meg egy egyedi nevet a VPN-profilhoz, amellyel az egyszerűen azonosítható az Intune konzoljában.         
**Leírás**     |Adjon meg egy olyan leírást, amely áttekintést nyújt a VPN-profilról, valamint más olyan releváns információkat tartalmaz, amelyek segítenek a profil helyének meghatározásában.         
**VPN-kapcsolat (felhasználóknál megjelenő) neve**     |Adja meg a VPN-profil nevét. Ez az a név, amelyet a felhasználók látni fognak a rendelkezésre álló VPN-kapcsolatok listájában az eszközükön.         
**Kapcsolat típusa**     |  Válasszon egyet a következő kapcsolattípusok közül a VPN-profilban való használathoz: **Cisco AnyConnect** (nem érhető el a Windows 8.1 vagy Windows Phone 8.1 rendszerhez), **Pulse Secure**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect**, **CheckPoint Mobile VPN**
**VPN-kiszolgáló leírása**     | Adjon meg egy leírást ahhoz a VPN-kiszolgálóhoz, amelyhez az eszközök csatlakozni fognak. **Például:** Contoso VPN-kiszolgáló. Ha a kapcsolat típusa **F5 Edge Client**, a **Kiszolgálólista** mezőben adja meg a kiszolgálóleírások és IP-címek listáját.
**A kiszolgáló IP-címe vagy teljesen minősített tartományneve**    |Adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljesen minősített tartománynevét, amelyhez az eszközök csatlakozni fognak. **Példák:** 192.168.1.1, vpn.contoso.com.  Ha a kapcsolat típusa **F5 Edge Client**, a **Kiszolgálólista** mezőben adja meg a kiszolgálóleírások és IP-címek listáját.         |         
**Kiszolgálólista**     |A **Hozzáadás** elemre kattintva felvehet egy új VPN-kiszolgálót, amelyet aztán alkalmazhat a VPN-kapcsolat kialakításához. Azt is megadhatja, hogy melyik kiszolgáló legyen az alapértelmezett a kapcsolathoz. Ez a beállítás csak akkor látható, ha a kapcsolat típusa **F5 Edge Client**.         
**Az összes hálózati forgalom elküldése a VPN-kapcsolaton keresztül**     |Ha ezt a lehetőséget választja, azzal minden hálózati forgalmat a VPN-kapcsolaton keresztül küld el. Ha nem ezt a lehetőséget választja, az ügyfélprogram dinamikusan egyezteti a vegyes alagútkezelés útvonalait a külső VPN-kiszolgálóhoz való csatlakozáskor. Csak a vállalati hálózat kapcsolatainak küldése történik VPN-alagúton keresztül. Az interneten megtalálható erőforrásokhoz való csatlakozás esetén a program nem használ VPN-alagutat.
**Hitelesítési módszer**| Válassza ki a VPN-kapcsolat által használandó hitelesítési módszert: **Tanúsítványok** vagy **Felhasználónév és jelszó**. A Felhasználónév és jelszó beállítás nem érhető el, ha a kapcsolat típusa Cisco AnyConnect. A **Hitelesítési módszer** beállítás Windows 8.1 esetén nem áll rendelkezésre.
**A felhasználói hitelesítő adatok megjegyzése minden egyes bejelentkezéskor**|Ezzel a beállítással gondoskodhat arról, hogy a rendszer megjegyezze a felhasználó hitelesítő adatait, így a felhasználónak nem kell megadnia őket minden egyes alkalommal, amikor kapcsolatot létesít.
**Ügyféltanúsítvány kiválasztása ügyfél-hitelesítéshez (identitástanúsítvány)**|Válassza ki azt a korábban az ügyfélprogramhoz létrehozott SCEP tanúsítványt, amelyet a VPN-kapcsolat hitelesítéséhez szeretne használni. A tanúsítványprofilok Intune-ban történő használatáról a következő dokumentumban olvashat bővebben: [Az erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md). Ez a beállítás csak akkor látható, ha a hitelesítési módszer a **Tanúsítványok**.
**Szerepkör**| Adja meg annak a felhasználói szerepkörnek a nevét, amely hozzáfér ehhez a kapcsolathoz. A felhasználói szerepkörök személyes beállításokat definiálnak, és engedélyeznek vagy letiltanak bizonyos hozzáférési funkciókat. Ez a beállítás csak akkor látható, ha a kapcsolat **Pulse Secure** típusú.
**Tartomány**|Adja meg a használni kívánt hitelesítési tartomány nevét. A hitelesítési tartomány a Pulse Secure kapcsolattípus által használt hitelesítési erőforrások csoportosítása. Ez a beállítás csak akkor látható, ha a kapcsolat **Pulse Secure** típusú.
**Bejelentkezési csoport vagy tartomány**|Adja meg annak a bejelentkezési csoportnak vagy tartománynak a nevét, amelyhez csatlakozni szeretne. Ez a beállítás csak akkor látható, ha a kapcsolat típusa **Dell SonicWALL Mobile Connect**.
**Ujjlenyomat**|Adjon meg egy karakterláncot (például „Contoso ujjlenyomatkód”), amelyet a rendszer a VPN-kiszolgáló megbízhatóságának ellenőrzésére fog használni. Az ujjlenyomatok: elküldhetők az ügyfélprogramnak, így az tudni fogja, hogy megbízhat-e az azonos ujjlenyomattal rendelkező kiszolgálókban a csatlakozáskor. Ha az eszköz még nem rendelkezik ujjlenyomattal, akkor arra fogja kérni a felhasználót, hogy bízzon meg a VPN-kiszolgálóban, amelyhez csatlakozik, miközben megjeleníti az ujjlenyomatot (a felhasználó manuálisan ellenőrizheti az ujjlenyomatot, majd a **Megbízom benne** elemet választva csatlakozhat). Ez a beállítás csak akkor látható, ha a kapcsolat típusa **CheckPoint Mobile VPN**.
**Alkalmazásonkénti VPN**|Ha a VPN-kapcsolatot egy iOS- vagy Mac OS X-alkalmazással társítaná, válassza ezt a lehetőséget. A rendszer ezt a kapcsolatot fogja megnyitni az alkalmazás futtatásakor. A VPN-profilt a szoftver telepítésekor társíthatja egy alkalmazással. További információ: [Alkalmazások központi telepítése a Microsoft Intune-ban)](deploy-apps-in-microsoft-intune.md)
**Proxybeállítások automatikus észlelése** (csak iOS, Mac OS X, Windows 8.1 és Windows Phone 8.1 esetén)|Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, adja meg, hogy szeretné-e, ha az eszközök automatikusan észlelnék a kapcsolatbeállításokat. További információt a Windows Server dokumentációjában talál.
**Automatikus konfigurációs parancsfájl használata** (csak iOS, Mac OS X, Windows 8.1 és Windows Phone 8.1 esetén)|Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, adja meg, hogy szeretné-e egy automatikus konfigurációs parancsfájllal definiálni a beállításokat, majd adja meg a beállításokat tartalmazó fájl URL-címét. További információt a Windows Server dokumentációjában talál.
**Proxykiszolgáló használata** (csak iOS, Mac OS X, Windows 8.1 és Windows Phone 8.1 esetén)|Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, válassza ezt a beállítást, majd adja meg a proxykiszolgáló címét és portszámát. További információt a Windows Server dokumentációjában talál.
**Proxybeállítások megkerülése helyi címek esetén** (csak iOS, Mac OS X, Windows 8.1 és Windows Phone 8.1 esetén)|Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, válassza ezt a beállítást, ha az Ön által megadott helyi címekhez nem szeretné használni a proxykiszolgálót. További információt a Windows Server dokumentációjában talál.
**Egyéni XML** (csak Windows 8.1-es és újabb, illetve Windows Phone 8.1-es és újabb verziók esetén)|Segítségével a VPN-kapcsolatot konfiguráló egyéni XML-parancsokat adhat meg. Példák. **Pulse Secure** esetén: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. **CheckPoint Mobile VPN** esetén: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" /&gt;. **Dell SonicWALL Mobile Connect** esetén: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. **F5 Edge Client** esetén: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Az egyéni XML-parancsok írásával kapcsolatban további információt az egyes gyártók VPN-dokumentációjában talál.
**DNS-utótagok keresési listája** (csak Windows Phone 8.1 esetén)|Minden egyes sorban adjon meg egy DNS-utótagot. Minden egyes megadott DNS-utótagra rákeres a rendszer, amikor egy rövid nevet használó webhelyhez csatlakozik. Adja meg például a **domain1.contoso.com** és **domain2.contoso.com** DNS-utótagokat, majd látogasson el a **http://sajatwebhely** URL-címre. Ekkor a **http://sajatwebhely.domain1.contoso.com** és **http://sajatwebhely.domain2.contoso.com** URL-címekre fog keresni.
**A VPN megkerülése a vállalati Wi-Fi hálózathoz való csatlakozáskor** (csak Windows Phone 8.1 esetén)|Azt adja meg, hogy a VPN-kapcsolat nem lesz használatban, amikor az eszköz a vállalati Wi-Fi hálózathoz csatlakozik.
**A VPN megkerülése otthoni Wi-Fi hálózathoz való csatlakozáskor** (csak Windows Phone 8.1 esetén)|Azt adja meg, hogy a VPN-kapcsolat nem lesz használatban, amikor az eszköz egy otthoni Wi-Fi hálózathoz csatlakozik.

Az alábbi további beállítások érhetők el a Windows 10-es asztali és mobileszközökhöz

Beállítás neve  |További információ  
---------|---------
**Hálózati forgalomra vonatkozó szabályok**| Beállíthatja, hogy a VPN-kapcsolatnál mely protokollok, helyi és távoli portok és címtartományok lesznek engedélyezve. Ha nem hoz létre hálózati forgalmi szabályt, minden protokoll, port és címtartomány engedélyezve lesz. Ha létrehoz egy szabályt, a VPN-kapcsolat csakis az általa vagy a további szabályok által engedélyezett protokollokat, portokat és címtartományokat fogja használni.
**Útvonalak**|Azok az útvonalak, amelyeket a VPN-kapcsolat használni fog.
**DNS-kiszolgálók**| Azok a DNS-kiszolgálók, amelyeket a VPN-kapcsolat használni fog, mihelyt kiépült a kapcsolat.         
**Társított alkalmazások**     | Megadhatja a VPN-kapcsolatot automatikusan használó alkalmazások listáját. Az alkalmazás típusa határozza meg az alkalmazás azonosítóját. Univerzális alkalmazások esetén – adja meg a Csomagcsalád nevét, valamint asztali alkalmazások esetén – adja meg az alkalmazás fájlútvonalát.          


> [!IMPORTANT] Javasoljuk, hogy az alkalmazásonkénti VPN-konfigurációban való használat céljából összeállított alkalmazáslistákat mindig helyezze biztonságba. Ha a listát esetleg arra nem jogosult felhasználó módosítja, és Ön így importálja azt az alkalmazásonkénti VPN-alkalmazáslistába, azzal olyan alkalmazásoknak is VPN-elérést biztosíthat, amelyeknek eredetileg nem szeretett volna. Az alkalmazáslisták biztonságba helyezésének módja lehet a hozzáférés-vezérlési lista (ACL) létrehozása.

Többek között a következő esetben lehet érdemes vállalati határbeállításokat használni. Ha a VPN-t csak távoli asztalokhoz szeretné engedélyezni, akkor létre kell hoznia például egy olyan hálózati forgalmi szabályt, amely engedélyezi a 27-es számú protokollhoz tartozó forgalmat a 3996-os külső porton. A VPN-t csak ez a típusú forgalom fogja használni.

Akkor lehet hasznos útvonalakat megadni a vállalati határokban, ha a VPN-kapcsolat típusa nem engedélyezi annak meghatározását, hogy a rendszer hogyan kezelje a forgalmat vegyes alagútkezelés esetén. Ilyenkor használja az **Útvonalak** elemet a VPN-t használó útvonalak felsorolásához.

Egy egyéni OMA-URI beállítás létrehozásával a Windows 10-es eszközök VPN-használatát adott alkalmazásokra korlátozhatja.

Az új szabályzat a **Házirend** munkaterület **Konfigurációs szabályzatok** csomópontjában jelenik meg.

## A szabályzat telepítése

1.  A **Házirend** munkaterületen válassza ki a telepíteni kívánt házirendet, majd kattintson a **Központi telepítés kezelése** elemre.

2.  A **Telepítések kezelése** párbeszédpanelen:

    -   **A házirend telepítése** – Válasszon ki egy vagy több olyan csoportot, amely számára telepíteni kívánja a házirendet, majd kattintson a **Hozzáadás** &gt; **OK** gombra.

    -   **A párbeszédpanel bezárása telepítés nélkül** – Kattintson a **Mégse** gombra.


A sikeres alkalmazást követően a felhasználók látni fogják a VPN-kapcsolat Ön által megadott nevét a VPN-kapcsolatok listájában az eszközükön.

A **Házirend** munkaterület **Áttekintés** lapján található állapotösszegzés és riasztások segítségével azonosíthatók a szabályzattal kapcsolatos, figyelmet igénylő problémák. Ezen felül egy állapotösszegzés megjelenik az Irányítópult munkaterületen is.

### További információ
[VPN-profilokhoz alkalmazható egyéni konfigurációk](Custom-configurations-for-VPN-profiles.md)
[Alkalmazásonkénti VPN az Android Pulse Secure használatával](per-app-vpn-for-android-pulse-secure.md)



<!--HONumber=Jun16_HO4-->


