---
title: SCEP-tanúsítványok használata az Azure-beli Microsoft Intune-nal | Micrososft Docs
description: Az SCEP-tanúsítványok Microsoft Intune-ban való használatához konfigurálja a helyszíni AD-tartományát, hozzon létre hitelesítésszolgáltatót, állítsa be az NDES-kiszolgálót, és telepítse az Intune Tanúsítvány-összekötőt. Ezután hozzon létre egy SCEP-tanúsítványprofilt, és rendelje azt csoportokhoz. Megismerheti továbbá a különböző eseményazonosítókat és azok leírását, valamint az Intune Connector Service diagnosztikai kódjait.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/28/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba7bb3a12e0e634df44bb832f8f35aa166095415
ms.sourcegitcommit: 34ff5ebe6efaa5b3a2a1db274de0a07c14944a6b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67463896"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>SCEP-tanúsítványok konfigurálása és használata az Intune-nal

Ez a cikk bemutatja az infrastruktúra konfigurálását, majd az Egyszerű tanúsítványbeiktatási protokoll (SCEP) tanúsítványprofiljainak ezt követő létrehozását és hozzárendelését az Intune-nal.

## <a name="configure-on-premises-infrastructure"></a>A helyszíni infrastruktúra konfigurálása

- **Active Directory-tartomány**: A jelen szakaszban felsorolt összes kiszolgálónak (a webalkalmazás-proxykiszolgáló kivételével) csatlakoznia kell a szervezet Active Directory-tartományához.

- **Hitelesítésszolgáltató** (CA): A Microsoft vállalati hitelesítésszolgáltató (CA), amely a Windows Server 2008 R2 vagy újabb rendszer Enterprise kiadása fut kell lennie. Az önálló hitelesítésszolgáltató nem támogatott. További útmutatás a [Hitelesítésszolgáltató telepítése](http://technet.microsoft.com/library/jj125375.aspx) témakörben található.
    Ha a hitelesítésszolgáltatója Windows Server 2008 R2 rendszeren fut, [telepítenie kell a KB2483564 jelű gyorsjavítást](http://support.microsoft.com/kb/2483564/).

- **NDES-kiszolgáló**: A Windows Server 2012 R2 vagy újabb állítsa be a hálózati eszközök tanúsítványigénylési szolgáltatás (NDES) kiszolgálói szerepkör. Az Intune nem támogatja az NDES használatát olyan kiszolgálón, amelyen az Enterprise CA is fut. Az [Útmutató a hálózati eszközök tanúsítványigénylési szolgáltatásához](http://technet.microsoft.com/library/hh831498.aspx) című cikkből tájékozódhat arról, hogyan kell konfigurálnia a Windows Server 2012 R2 rendszert az NDES futtatására.
Az NDES-kiszolgálónak egy olyan tartományhoz kell csatlakoznia, amely a vállalati CA-val egy erdőben található. További információ az NDES-kiszolgáló különálló erdőben, elszigetelt hálózaton vagy belső tartományon való telepítéséről: [Házirendmodul használata a Hálózati eszközök tanúsítványigénylési szolgáltatásával](https://technet.microsoft.com/library/dn473016.aspx). Már nem NDES-kiszolgálóra, amely már használatban van egy másik MDM-használata

- **A Microsoft Intune tanúsítvány-összekötő**: Az Intune-portálon lépjen a **eszközkonfiguráció** > **tanúsítvány-összekötőt** > **Hozzáadás**, és kövesse a *lépések SCEP-összekötő telepítésének*. A portálon a letöltési hivatkozás segítségével indítsa el a tanúsítvány-összekötő telepítő letöltési **NDESConnectorSetup.exe**.  Ezt a telepítőt kell futtatnia az NDES-szerepkörrel rendelkező kiszolgálón.  

Az NDES tanúsítvány-összekötő a Federal Information Processing Standard (FIPS) módot is támogatja. A FIPS nem szükséges, de ha engedélyezve van, akkor lehetőség van tanúsítványok kibocsátására és visszavonására.

- **Webalkalmazás-proxykiszolgáló** (nem kötelező): Használjon olyan kiszolgálót, amelyen Windows Server 2012 R2 vagy újabb, mint a webalkalmazás-proxykiszolgálóként (WAP) kiszolgáló. Ez a konfiguráció:
  - Lehetővé teszi, hogy az eszközök az interneten keresztül fogadjanak tanúsítványokat.
  - Biztonsági ajánlás olyan környezetekben, ahol az eszközök az interneten keresztül csatlakozva kapnak és újítanak meg tanúsítványokat.
  
- **Az Azure AD-alkalmazásproxy** (nem kötelező): Az Azure AD-alkalmazásproxy közzététele az NDES-kiszolgálón az Internet helyett egy dedikált webalkalmazás-proxykiszolgálóként (WAP) kiszolgáló is használható. További információért lásd: [Helyszíni alkalmazások biztonságos távoli elérése](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="additional"></a>Továbbiak

- A WAP-ot futtató kiszolgálón [telepíteni kell egy frissítést](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ahhoz, hogy az támogassa az NDES által használt hosszú URL-eket. Ez a frissítés megtalálható a [2014. decemberi kumulatív frissítésben](http://support.microsoft.com/kb/3013769), illetve önállóan a [KB3011135-as jelű frissítésként](http://support.microsoft.com/kb/3011135).
- A WAP-kiszolgálónak rendelkeznie kell egy SSL-tanúsítvánnyal, amely a külső ügyfeleknek közzétett nevet egyezteti, valamint meg kell bíznia az NDES-kiszolgálón használt SSL-tanúsítványban. E tanúsítványok segítségével a WAP-kiszolgáló képes megszakítani az ügyfelek SSL-kapcsolatát, illetve új SSL-kapcsolatot létrehozni az NDES-kiszolgálóval.

További információ: [Tanúsítványok tervezése a WAP-hoz](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) és [Általános adatok a WAP-kiszolgálókról](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>A hálózatra vonatkozó követelmények

Ha nem használ fordított proxyt (például WAP-t vagy az Azure AD alkalmazásproxyját), engedélyezze a TCP-forgalmat a 443-as porton minden gazdagépről/IP-címről az NDES-kiszolgálóra.

Engedélyezzen minden portot és protokollt, amely szükséges az NDES-kiszolgáló és a támogató infrastruktúra közötti működéshez. Az NDES-kiszolgálónak például kommunikálnia kell a CA-val, a DNS-kiszolgálókkal, a Configuration Manager-kiszolgálókkal, a tartományvezérlőkkel, és potenciálisan más szolgáltatásokkal is a környezeten belül.

Az NDES-kiszolgálót egy fordított proxyn keresztül, például az [Azure AD-alkalmazásproxyn](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), a [webalkalmazás-proxyn](https://technet.microsoft.com/library/dn584107.aspx) vagy egy külső proxyn érdemes közzétenni.

### <a name="certificates-and-templates"></a>Tanúsítványok és sablonok  

|Object|Részletek|
|----------|-----------|
|**Tanúsítványsablon**|Ez a sablon a vállalati hitelesítésszolgáltatón konfigurálható.|
|**Ügyfél-hitelesítési tanúsítvány**|A vállalati vagy nyilvános hitelesítésszolgáltatótól lekért tanúsítvány, melyet az NDES-kiszolgálóra kell telepítenie.|
|**Kiszolgálói hitelesítési tanúsítvány**|A vállalati vagy nyilvános hitelesítésszolgáltatótól lekért tanúsítvány. Ezt az SSL-tanúsítványt az NDES-kiszolgálón futó IIS-be kell telepítenie, majd kötést kell létrehoznia. Ha a tanúsítványban be van állítva az ügyfél- és kiszolgálóhitelesítési kulcshasználat (**Kibővített kulcshasználat**), akkor használhatja ugyanazon tanúsítványt.|
|**Megbízható legfelső szintű hitelesítésszolgáltató tanúsítványa**|Exportálja ezeket a tanúsítványokat **.cer** kiterjesztésű fájlként a legfelső szintű hitelesítésszolgáltatóról vagy azokról az eszközökről, amelyek megbízhatónak tartják a legfelső szintű hitelesítésszolgáltatót. Ezután rendelje hozzá a felhasználók, eszközök vagy mindkét használatával a megbízható Hitelesítésszolgáltatói tanúsítványprofillal.<br /> **Megjegyzés:<br />ha SCEP-tanúsítványprofil hozzá van rendelve, ügyeljen arra, hogy rendelje hozzá a *megbízható főtanúsítvány-profil* hivatkozik az SCEP-tanúsítványprofil ugyanazon felhasználó vagy eszköz csoporthoz.  Ez a profil létrehozásához lásd: [hozzon létre egy megbízható tanúsítványprofilt](certficates-pfx-configure.md#create-a-trusted-certificate-profile), amely a cikk a PKCS-tanúsítványprofilok szerződését.** <br/><br />Operációsrendszer-platformonként egy megbízható legfelső szintű Hitelesítésszolgáltatói tanúsítványt használjon, és társíthatja azt minden egyes létrehozott megbízható főtanúsítvány-profilt. <br /><br />Szükség esetén további megbízható legfelső szintű hitelesítésszolgáltatói tanúsítványokat is használhat. Ezzel például bizalmi kapcsolatot alakíthat ki egy hitelesítésszolgáltatónak, mely aláírja a kiszolgálói hitelesítési tanúsítványokat a szervezet Wi-Fi hozzáférési pontjai számára.|

### <a name="accounts"></a>Fiókok

|Name (Név)|Részletek|
|--------|-----------|
|**NDES szolgáltatásfiók**|Adjon meg egy tartományfelhasználói fiókot, melyet NDES szolgáltatásfiókként fog használni. |

## <a name="configure-your-infrastructure"></a>Az infrastruktúra konfigurálása
A tanúsítványprofilok konfigurálása előtt kövesse a következő lépéseket. Ezekhez szükség van a Windows Server 2012 R2 vagy újabb verzió és az Active Directory tanúsítványszolgáltatások (ADCS) ismeretére:

#### <a name="step-1---create-an-ndes-service-account"></a>1\. lépés – NDES szolgáltatásfiók létrehozása

Hozzon létre egy tartományfelhasználói fiókot, melyet NDES szolgáltatásfiókként fog használni. Ezt a fiókot kell megadnia a sablonok vállalati hitelesítésszolgáltatónál való konfigurálásakor, még mielőtt telepítené és konfigurálná az NDES-t. Gondoskodjon arról, hogy a felhasználó rendelkezzen az alapértelmezett jogokkal, valamint a következő jogokkal: **Helyi bejelentkezés engedélyezése**, **Bejelentkezés szolgáltatásként** és **Bejelentkezés kötegfájlfolyamatként**. Egyes szervezeteknél olyan korlátozási szabályzatok lehetnek érvényben, amelyek letiltják ezeket a jogokat.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>2\. lépés – Tanúsítványsablonok konfigurálása a hitelesítésszolgáltatónál
Ebben a lépésben a következőket fogja elvégezni:

- Tanúsítványsablon konfigurálása az NDES számára
- Tanúsítványsablon közzététele az NDES számára

##### <a name="configure-the-certification-authority"></a>A hitelesítésszolgáltató konfigurálása

1. Jelentkezzen be vállalati rendszergazdaként.

2. Hozzon létre egy új sablont a Tanúsítványsablonok beépülő modullal a vállalati hitelesítésszolgáltatón. Vagy másik lehetőségként másoljon egy meglévő sablont, és frissítse a meglévő sablont (például a Felhasználói sablont) az NDES-sel való használathoz.

   >[!NOTE]
   > Az NDES tanúsítványsablonnak v2 tanúsítványsablonon kell alapulnia (Windows 2003-kompatibilitással).

   A sablonnak az alábbi beállításokkal kell rendelkeznie:

   - **Általában**:
   
       - Győződjön meg arról, hogy **A tanúsítvány közzététele az Active Directoryban** tulajdonság **nincs** bejelölve.
       - Adjon meg egy leíró nevet a sablonnak a **Sablon megjelenítendő neve** mezőben.

   - A **Tulajdonos neve** lapon válassza a **Kérelemben megadva** lehetőséget. (A biztonságot az Intune NDES-házirendmodulja fogja érvényesíteni.)

   - A **Kiterjesztések** területen győződjön meg róla, hogy az **Alkalmazás-házirendek leírása** lista tartalmazza az **Ügyfél-hitelesítés** elemet.

     > [!IMPORTANT]
     > iOS- és macOS-tanúsítványsablonok esetében a **Kiterjesztések** lapon módosítsa a **Kulcshasználat** beállítást, és ügyeljen rá, hogy **Az aláírás az eredet igazolása** jelölőnégyzet ne legyen bejelölve.

   - A **Biztonság** területen adja hozzá az NDES szolgáltatásfiókot, és adjon meg hozzá **Regisztrálás** engedélyt a sablonhoz. Az SCEP-profilokat létrehozó Intune-rendszergazdáknak **olvasási** jogokkal kell rendelkezniük, hogy az SCEP-profilok létrehozása során megnyithassák a sablont.

     > [!NOTE]
     > Tanúsítványok visszavonásához az NDES szolgáltatásfiókot kell *tanúsítványok kiállítása és kezelése* jogok a hitelesítésszolgáltatón. Ez az engedély delegálása, nyissa meg a hitelesítésszolgáltató felügyeleti konzolt, és kattintson a jobb gombbal a hitelesítésszolgáltató nevére. Ezután a biztonság lapon adja hozzá, vagy válassza ki a fiókot, és ezután jelölje be a **tanúsítványok kiállítása és kezelése**.


3. Ellenőrizze az **Érvényesség időtartama** beállítást a sablon **Általános** lapján. Alapértelmezés szerint az Intune a sablonban konfigurált értéket használja. A hitelesítésszolgáltató konfigurálásával azonban engedélyezheti, hogy a kérelmező ettől eltérő értéket adjon meg, amelyet aztán az Intune-rendszergazdai konzolról állíthat be. Ha később mindig ezt az értéket akarja használni a sablonban, akkor hagyja ki e lépés további részeit.

   > [!IMPORTANT]
   > Az iOS és a macOS mindig a sablonban beállított értéket használja, minden más konfigurációs beállítástól függetlenül.

Példa a sablonkonfigurációra:

![Sablon, a kérelmek kezelésére szolgáló lap](./media/scep_ndes_request_handling.png)

![Sablon, a tulajdonos nevének megadására szolgáló lap](./media/scep_ndes_subject_name.jpg)

![Sablon, a biztonsági beállításokat tartalmazó lap](./media/scep_ndes_security.jpg)

![Sablon, a bővítményeket tartalmazó lap](./media/scep_ndes_extensions.jpg)

![Sablon, a tanúsítvány kiállításának feltételeit tartalmazó lap](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> Az Alkalmazás-házirendek beállításnál csak azokat az alkalmazás-házirendeket adja hozzá, amelyekre valóban szüksége van. A kiválasztott elemekkel kapcsolatban kérje ki a biztonsági rendszergazda véleményét is.

Konfigurálja a hitelesítésszolgáltatót úgy, hogy engedélyezze a kérelmezőnek az érvényességi időszak megadását:

1. Futtassa a hitelesítésszolgáltatón a következő parancsokat:
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. Tegye közzé a Hitelesítésszolgáltató beépülő modullal a tanúsítványsablont a vállalati hitelesítésszolgáltatón.
   Válassza a **Tanúsítványsablonok** csomópontot, válassza a **Művelet** > **Új** > **Kiállítandó tanúsítványsablon** lehetőséget, és válassza ki a 2. lépésben létrehozott sablont.

3. Ellenőrizze a **Tanúsítványsablonok** mappában, hogy a sablon közzététele sikerült-e.

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>3\. lépés – Előfeltételek konfigurálása az NDES-kiszolgálón
Ebben a lépésben a következőket fogja elvégezni:

- Az NDES hozzáadása egy Windows Server-kiszolgálóhoz, és az IIS konfigurálása az NDES támogatására
- Az NDES szolgáltatásfiók hozzáadása a IIS_IUSR csoporthoz
- Egyszerű szolgáltatásnév (SPN) beállítása az NDES-szolgáltatásfiók számára

1. Jelentkezzen be az NDES szolgáltatásnak helyt adó kiszolgálón **Vállalati rendszergazdaként**, és telepítse az NDES-t a [Szerepkörök és szolgáltatások hozzáadása varázslóval](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)):

   1. A varázslóban válassza az **Active Directory tanúsítványszolgáltatások** lehetőséget az AD CS szerepkör-szolgáltatások eléréséhez. Válassza a **Hálózati eszközök tanúsítványigénylési szolgáltatása**lehetőséget, törölje a jelet a **Hitelesítésszolgáltató**jelölőnégyzetből, és fejezze be a varázslót.

      > [!TIP]
      > A **Telepítési folyamat** lehetőségnél ne jelölje be a **Bezárás** jelölőnégyzetet. Ehelyett válassza **Az Active Directory tanúsítványszolgáltatások beállítása a célkiszolgálón** hivatkozást. Ekkor megnyílik **Az Active Directory tanúsítványszolgáltatások beállítása** varázsló, amelyet a következő lépésben kell használnia. Ha megnyílt Az Active Directory tanúsítványszolgáltatások beállítása varázsló, bezárhatja a Szerepkörök és szolgáltatások hozzáadása varázslót.

   2. Az NDES kiszolgálóhoz való hozzáadásakor a varázsló az IIS-t is telepíti. Ellenőrizze, hogy az IIS így van konfigurálva:

       - **Webkiszolgáló** > **Biztonság** > **Kérelemszűrés**

       - **Webkiszolgáló** > **Alkalmazásfejlesztés** > **ASP.NET 3.5** 

            Az ASP.NET 3.5 telepítése telepíti a .NET-keretrendszer 3.5-öt is. A .NET-keretrendszer 3.5 telepítésekor a **.NET-keretrendszer 3.5** alapszolgáltatásai mellett telepítse a **HTTP-aktiválás**szolgáltatást is.

       - **Webkiszolgáló** > **Alkalmazásfejlesztés** > **ASP.NET 4.5** 

            Az ASP.NET 4.5 telepítése telepíti a .NET-keretrendszer 4.5-öt is. A .NET-keretrendszer 4.5 telepítésekor a **.NET-keretrendszer 4.5** alapszolgáltatásai mellett telepítse az **ASP.NET 4.5** és a **WCF-szolgáltatások** > **HTTP-aktiválás** szolgáltatást is.

       - **Felügyeleti eszközök** > **Kompatibilitás az IIS 6 kezelésével** > **Kompatibilitás az IIS 6 metabázisával**

       - **Felügyeleti eszközök** > **Kompatibilitás az IIS 6 kezelésével** > **IIS 6 WMI kompatibilitási mód**

       - Vegye fel a kiszolgálón az NDES szolgáltatásfiókot a helyi **IIS_IUSR** csoport tagjaként.

2. Futtassa egy emelt jogosultságszintű parancssorból az alábbi parancsot az NDES szolgáltatásfiók egyszerű szolgáltatásnevének beállításához:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Ha például az NDES kiszolgáló neve **Kiszolgalo01**, a tartomány **Contoso.com**és a szolgáltatásfiók **NDESSzolgaltatas**, akkor az alábbi parancsot kell használnia:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>4\. lépés – Az NDES Intune-nal való használatának konfigurálása
Ebben a lépésben a következőket fogja elvégezni:

- Az NDES konfigurálása a vállalati hitelesítésszolgáltatóval való használatra
- SSL-tanúsítvány kötésének létrehozása az IIS-ben
- Kérelemszűrés konfigurálása az IIS-ben

1. Nyissa meg az NDES-kiszolgálón Az Active Directory tanúsítványszolgáltatások beállítása varázslót, és végezze el az alábbi módosításokat:

    > [!TIP]
    > Ha az előző lépésben a hivatkozásra kattintott, akkor ez a varázsló már meg van nyitva. Ellenkező esetben nyissa meg a Kiszolgálókezelőt az Active Directory tanúsítványszolgáltatások telepítés utáni konfigurációjának eléréséhez.

   - A **Szerepkör-szolgáltatások** területen válassza a **Hálózati eszközök tanúsítványigénylési szolgáltatása** lehetőséget.
   - A **Hálózati eszközök tanúsítványigénylési szolgáltatásának szolgáltatásfiókja** területen adja meg az NDES szolgáltatásfiókot.
   - A **Hitelesítésszolgáltató a Hálózati eszközök tanúsítványigénylési szolgáltatásához** területen kattintson a **Kijelölés** lehetőségre, és válassza ki azt a vállalati hitelesítésszolgáltatót, amelyen a tanúsítványsablont konfigurálta.
   - A **Titkosítás a Hálózati eszközök tanúsítványigénylési szolgáltatása esetén** területen adja meg a kulcshosszt a vállalati követelményeknek megfelelően.
   - A **Megerősítés** területen válassza a **Konfigurálás** lehetőséget a varázsló befejezéséhez.

2. Miután a varázsló befejeződött, frissítse az NDES-kiszolgálón az alábbi beállításkulcsot:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    A kulcs frissítéséhez azonosítsa a tanúsítványsablon **célját**, melyet a **Kérelmek kezelése** lapon találhat meg. Ezután frissítse a beállításjegyzék megfelelő bejegyzését úgy, hogy lecseréli a meglévő adatokat a tanúsítványsablon nevére (nem a sablon megjelenő nevére), amelyet a 2. lépésben adott meg. A következő táblázat a tanúsítványsablon-céloknak megfelelő beállításjegyzék-értékeket mutatja:

    |Tanúsítványsablon célja (a Kérelmek kezelése lapon)|Szerkesztendő beállításazonosító|Az SCEP-profil Intune felügyeleti konzolban látható értéke|
    |---|---|---|
    |Aláírás|SignatureTemplate|Digitális aláírás|
    |Encryption|EncryptionTemplate|Kulcstitkosítás|
    |Aláírás és titkosítás|GeneralPurposeTemplate|Kulcstitkosítás<br/>Digitális aláírás|

    Ha például a tanúsítványsablon célja **Titkosítás**, akkor az **EncryptionTemplate** azonosító értékét kell a tanúsítványsablon nevére cserélnie.

3. Az NDES-kiszolgálóra rendkívül hosszú URL-címek (lekérdezések) érkeznek, melyekhez két beállításjegyzékbeli bejegyzést kell felvennie:


   |                        Location                        |      Value      | Type  |      Data       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (decimális) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (decimális) |

4. Az IIS-kezelőben válassza az **Alapértelmezett webhely** > **Kérésszűrés** > **Szolgáltatás beállításainak szerkesztése** lehetőséget. Módosítsa az **URL-cím maximális hossza** és a **Lekérdezési sztring maximális hossza** beállítás értékét a következőre: *65534*, ahogy az a képen is látható:

    ![Maximális URL-hossz és lekérdezéshossz az IIS-ben](./media/SCEP_IIS_max_URL.png)

5. Indítsa újra a kiszolgálót. Ne használja az **iisreset** parancsot, ez ugyanis nem véglegesíti az elvégzett módosításokat.
6. Nyissa meg a `http://*FQDN*/certsrv/mscep/mscep.dll` címet. Az alábbihoz hasonló NDES-lapnak kell megjelennie:

    ![NDES teszt](./media/SCEP_NDES_URL.png)

    Ha **503 – A szolgáltatás nem érhető el** hibát kap, tekintse meg az eseménymegjelenítőt. Valószínű, hogy az alkalmazáskészlet azért állt le, mert az NDES-felhasználó nem rendelkezik valamelyik szükséges joggal. A szükséges jogokat az 1. lépés ismerteti.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Tanúsítványok NDES-kiszolgálón való telepítése és kötése

1. Kérelmezzen a belső vagy a nyilvános hitelesítésszolgáltatótól egy **kiszolgálóhitelesítő** tanúsítványt, és telepítse az NDES-kiszolgálón. Ezután létre kell hoznia az SSL-tanúsítvány kötését az IIS-ben.

    > [!TIP]
    > Miután létrehozta az SSL-tanúsítvány kötését az IIS-ben, telepítenie kell egy ügyfél-hitelesítési tanúsítványt. Ezt a tanúsítványt bármely olyan hitelesítésszolgáltató kibocsáthatja, amelyben az NDES-kiszolgáló megbízik. Ha a tanúsítványban be van állítva az ügyfél- és kiszolgálóhitelesítési kulcshasználat (**Kibővített kulcshasználat**), akkor használhatja ugyanazon tanúsítványt. Ezekről a hitelesítési tanúsítványokról az alábbi lépésekből kaphat további információt.

   1. Miután beszerezte a kiszolgálói hitelesítési tanúsítványt, nyissa meg az **IIS-kezelőt**, és válassza az **Alapértelmezett webhely** lehetőséget. Válassza a **Műveletek** panelen található **Kötések** elemet.

   2. Válassza a **Hozzáadás** lehetőséget, adja meg a **Típus** beállításnál a **https**értéket, és győződjön meg róla, hogy a port **443** értékre van állítva. A különálló Intune csak a 443-as portot támogatja.

   3. Az **SSL-tanúsítvány** beállításnál adja meg a kiszolgálói hitelesítési tanúsítványt.

      > [!NOTE]
      > Ha az NDES-kiszolgáló egyetlen hálózati címhez külső és belső nevet is használ, akkor a kiszolgálói hitelesítési tanúsítványnak tartalmaznia kell az alábbiakat:
      > - **Tulajdonos neve** – a külső, nyilvános kiszolgálónév
      > - **Tulajdonos alternatív neve** – a belső kiszolgálónév

2. Kérelmezzen a belső vagy a nyilvános hitelesítésszolgáltatótól egy **ügyfél-hitelesítő** tanúsítványt, és telepítse az NDES-kiszolgálón. Ez a tanúsítvány megegyezhet a kiszolgálóhitelesítési tanúsítvánnyal, ha ez a tanúsítvány mindkét funkcióval rendelkezik.

    Az ügyfél-hitelesítő tanúsítványnak az alábbi tulajdonságokkal kell rendelkeznie:

    - **Kibővített kulcshasználat**: Ennek az értéknek tartalmaznia kell **ügyfél-hitelesítés**

    - **Tulajdonos neve**: Az értéket meg kell egyeznie a DNS-nevével, a kiszolgáló, amelyen telepíti a tanúsítványt (az NDES-kiszolgáló)

##### <a name="configure-iis-request-filtering"></a>Kérelmek szűrésének konfigurálása az IIS-ben

1. Nyissa meg az NDES-kiszolgálón az **IIS-kezelőt**, válassza az **Alapértelmezett webhely** lehetőséget a **Kapcsolatok** panelen, és nyissa meg a **Kérelmek szűrése** beállítást.

2. Válassza a **Szolgáltatás beállításainak szerkesztése** lehetőséget, és adja meg a következő értékeket:

    - **lekérdezési sztring hossza (bájt)**  = **65534**
    - **URL-cím maximális hossza (bájt)**  = **65534**

3. Tekintse át a következő beállításkulcsot:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Győződjön meg róla, hogy az alábbi értékek vannak beállítva Duplaszó típusú bejegyzésként:

    - Név: **MaxFieldLength**, a decimális **65534**
    - Név: **MaxRequestBytes**, a decimális **65534**

4. Indítsa újra az NDES-kiszolgálót. A kiszolgáló mostantól készen áll az tanúsítvány-összekötő támogatására.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>5\. lépés – Az Intune Certificate Connector engedélyezése, telepítése és konfigurálása
Ebben a lépésben a következőket fogja elvégezni:

- Az NDES támogatásának engedélyezése az Intune-ban.
- A Tanúsítvány-összekötő letöltése, telepítése és konfigurálása a hálózati eszközök tanúsítványigénylési szolgáltatás (NDES) szerepkört üzemeltető kiszolgálón a saját környezetben. Annak érdekében, hogy méretezhető lehessen az NDES-kiépítés a cégen belül, több NDES-kiszolgáló is telepíthető úgy, hogy mindegyikhez tartozik egy-egy Microsoft Intune Tanúsítvány-összekötő.

##### <a name="download-install-and-configure-the-certificate-connector"></a>A tanúsítvány-összekötő letöltése, telepítése és konfigurálása

> [!IMPORTANT] 
> A Microsoft Intune Tanúsítvány-összekötőt külön Windows-kiszolgálóra **kell** telepíteni. A vállalati hitelesítésszolgáltatóra (CA) nem telepíthető. Emellett ugyanarra a kiszolgálóra **kell** telepíteni, mint amelyikre a Hálózati eszközök tanúsítványigénylési szolgáltatása (NDES) szerepkör is telepítve lett.

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza ki **eszközkonfiguráció** > **összekötők minősítési** > **Hozzáadás**.
3. Töltse le és mentse az összekötőt SCEP-fájl. Mentse egy olyan helyre a fogjuk, ha az összekötő telepítéséhez az NDES-kiszolgálón.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)


4. A letöltés befejezése után nyissa meg az NDES-kiszolgálón, amelyen a hálózati eszközök tanúsítványigénylési szolgáltatás (NDES). Ha ez megvan:

    1. Győződjön meg róla, hogy telepítve van-e a .NET 4.5-keretrendszer, mivel arra szüksége van az NDES tanúsítvány-összekötőjének. A .NET 4.5-keretrendszer automatikusan részen a Windows Server 2012 R2 és újabb verzióknak.
    2. A kiszolgáló rendszergazdai jogosultságokkal rendelkező fiók használatára a telepítő futtatásához (**NDESConnectorSetup.exe**). A telepítés során az NDES házirendmodulja és a CRP (tanúsítványregisztrációs pont) webszolgáltatás is települ. A CRP webszolgáltatás, melynek neve CertificateRegistrationSvc, alkalmazásként fut az IIS-ben.

    > [!NOTE]
    > Ha önálló Intune-hoz telepíti az NDES-t, akkor a CRP szolgáltatás automatikusan települ a tanúsítvány-összekötővel együtt. Az Intune szolgáltatásnak a Configuration Managerrel való használatakor a tanúsítványregisztrációs pontot különálló helyrendszerszerepkörként telepíti.

5. Ha a rendszer kéri az ügyféltanúsítványt a tanúsítvány-összekötőhöz, válassza a **Kijelölés** lehetőséget, majd válassza ki az **ügyfél-hitelesítési** tanúsítványt, amelyet a 4. lépésben telepített az NDES-kiszolgálóra.

    Miután kiválasztotta az ügyfél-hitelesítési tanúsítványt, a rendszer visszairányítja az **Client Certificate for Microsoft Intune Certificate Connector** (Ügyféltanúsítvány a Microsoft Intune Certificate Connectorhoz) felületre. Bár a választott tanúsítvány nem látható, válassza a **Tovább** gombot a tanúsítvány tulajdonságainak megtekintéséhez. Válassza a **Tovább**, majd a **Telepítés** lehetőséget.

    > [!IMPORTANT]
    > Az Internet Explorer fokozott biztonsági beállításait [le kell tiltani az NDES-kiszolgálón](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx), amelyen az Intune Tanúsítvány-összekötő található.

6. Ha a varázsló befejeződött, még mielőtt bezárná, válassza a **Launch the Certificate Connector UI** (Certificate Connector felhasználói felületének indítása) lehetőséget.

    > [!TIP]
    > Ha bezárná a varázslót a tanúsítvány-összekötő felhasználói felületének megnyitása előtt, akkor az alábbi parancs futtatásával nyithatja meg:
    >
    > < install_Path > \NDESConnectorUI\NDESConnectorUI.exe

7. A **Certificate Connector** (Tanúsítvány-összekötő) felhasználói felületén:

    Válassza a **Bejelentkezés** gombot, és írja be az Intune szolgáltatás rendszergazdai hitelesítő adatait, vagy egy bérlői rendszergazda globális felügyeleti engedéllyel rendelkező hitelesítő adatait. A bejelentkezés után az Intune Tanúsítvány-összekötő letölt egy tanúsítványt az Intune-ról. Ezzel történik az összekötő és az Intune közti hitelesítés.

    > [!IMPORTANT]
    > A felhasználói fiókot egy érvényes Intune-licenchez kell hozzárendelni. Ha a felhasználói fiók nem rendelkezik érvényes Intune-licenccel, az NDESConnectorUI.exe sikertelenül fut.

    Ha munkahelye proxykiszolgálót használ, és a proxy használata szükséges ahhoz, hogy az NDES-kiszolgáló hozzáférjen az internethez, válassza a **Proxykiszolgáló használata** lehetőséget. Ezután a csatlakozáshoz adja meg a proxykiszolgáló nevét, portját és a fiókhoz tartozó hitelesítő adatokat.

    Váltson a **Speciális** lapra, majd adja meg egy olyan fiók hitelesítő adatait, amely rendelkezik **Tanúsítványok kiállítása és kezelése** engedéllyel a vállalati hitelesítésszolgáltatónál. Válassza az **Alkalmaz** gombot a módosítások alkalmazásához. Ha ez az engedély delegálta az NDES szolgáltatásfiókot, ha [a hitelesítésszolgáltató konfigurálásával](#configure-the-certification-authority), adja meg a használt fiókot. 

    Bezárhatja a tanúsítvány-összekötő felhasználói felületét.

8. Nyisson meg egy parancssort, írja be a **services.msc** nevet, majd nyomja le az **Enter** billentyűt. Kattintson jobb egérgombbal az **Intune Connector Service** > **Újraindítás** lehetőségre.

A szolgáltatás futásának ellenőrzéséhez nyisson meg egy böngészőt, és írja be az alábbi URL-t. Ennek egy **403-as** hibát kell visszaadnia:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Az NDES tanúsítvány-összekötő tartalmazza a TLS 1.2 támogatását. Ha tehát a kiszolgáló, amelyen az NDES tanúsítvány-összekötő telepítve van, támogatja a TLS 1.2-t, akkor a TLS 1.2 lesz használva. Amennyiben a kiszolgáló nem támogatja a TLS 1.2 verziót, a TLS 1.1 lesz használva. Az eszközök és a kiszolgáló közötti hitelesítéshez jelenleg a TLS 1.1 van használatban.

## <a name="create-a-scep-certificate-profile"></a>SCEP-tanúsítványprofil létrehozása

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg az SCEP-tanúsítványprofil **nevét** és **leírását**.
4. Válassza ki az SCEP-tanúsítvány eszközplatformját a **Platform** legördülő listából. Jelenleg az alábbi platformokra vonatkozóan lehet eszközkorlátozási beállításokat megadni:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 és újabb**
   - **Windows 10 és újabb**
5. A **Profil típusa** legördülő listában válassza az **SCEP-tanúsítvány** lehetőséget.
6. Adja meg a következő beállításokat:

   - **Tanúsítvány típusa**: Válasszon **felhasználói** felhasználói tanúsítványok esetében. A **felhasználói** tanúsítványt a tulajdonos és a SAN tanúsítvány felhasználói és eszköz attribútumok tartalmazhat.  Válasszon **eszköz** forgatókönyvek például a felhasználó nélküli eszközök, például kioszkok, vagy a Windows-eszközök esetén a tanúsítvány elhelyezése a helyi számítógép tanúsítványtárolójában. **Eszköz** tanúsítványok tartalmazhat a tulajdonos és a SAN tanúsítvány eszközattribútumokat.  **Eszköztanúsítványok** a következő platformokhoz érhetők el:  
     - Android Enterprise - munkahelyi profil
     - iOS
     - macOS
     - Windows 8.1 és újabb
     - Windows 10 és újabb


   - **Tulajdonos nevének formátuma**: Válassza ki, hogyan Intune-ban hozza létre automatikusan a tulajdonos nevét a tanúsítványkérelemben. A beállítások eltérőek a **Felhasználói** és az **Eszköz** tanúsítványtípus kiválasztásakor. 

        **Felhasználói tanúsítványtípus**  

        A tulajdonos nevében a felhasználó e-mail-címét is feltüntetheti. A következő lehetőségek közül választhat:

        - **Nincs konfigurálva**
        - **Köznapi név**
        - **Köznapi név (e-mail is)**
        - **Köznapi név mint e-mail cím**
        - **IMEI (Nemzetközi mobilkészülék-azonosító)**
        - **Sorozatszám**
        - **Egyéni**: Ezt a beállítást, ha egy **egyéni** szövegmező is megjelenik. Ezt a mezőt egyéni tulajdonosnév-formátumok megadásához használhatja, beleértve a változókat is. Egyéni formátum két változót támogat: **Köznapi név (CN)** és **E-mail (E)** . Az **Egyszerű név (CN)** az alábbi változók bármelyikére beállítható:

            - **CN = {{UserName}}** : Az egyszerű felhasználónév a felhasználó például janedoe@contoso.com
            - **CN={{AAD_Device_ID}}** : Amikor regisztrál egy eszközt az Azure Active Directory (AD) hozzárendelt azonosító. Ez az azonosító jellemzően az Azure AD-ben való hitelesítéshez használatos.
            - **CN={{SERIALNUMBER}}** : Az egyedi sorozatszám (Sorozatszám) jellemzően a gyártó által használt eszköz azonosításához
            - **CN={{IMEINumber}}** : Az International Mobile Equipment azonosító (IMEI) egy mobiltelefonok azonosítására szolgáló egyedi szám
            - **CN={{OnPrem_Distinguished_Name}}** : Relatív megkülönböztető nevek vesszővel elválasztva. például egy feladatütemezési `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

                A(z) `{{OnPrem_Distinguished_Name}}` változó használatához ügyeljen rá, hogy a(z) `onpremisesdistingishedname` felhasználói attribútumot szinkronizálja az Azure AD-vel az [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) segítségével.

            - **CN={{onPremisesSamAccountName}}** : Rendszergazdák szinkronizálhatók a samAccountName attribútumot használva az Active Directoryból az Azure AD-bA az Azure AD connect nevű attribútum be `onPremisesSamAccountName`. Az Intune helyettesítheti ezt a változót egy SCEP-tanúsítványhoz tartozó tanúsítványkiadási kérelem részeként.  A samAccountName attribútum az a bejelentkezési név, amely a Windows előző verzióját (A Windows 2000-nél korábbi verziókat) használó ügyfelek és kiszolgálók támogatására szolgált. A bejelentkezési név formátuma: `DomainName\testUser`, vagy csak `testUser`.

                A(z) `{{onPremisesSamAccountName}}` változó használatához ügyeljen rá, hogy a(z) `onPremisesSamAccountName` felhasználói attribútumot szinkronizálja az Azure AD-vel az [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) segítségével.

            Egy vagy több változó és statikus sztringek együttes használatával létrehozhat egyéni tulajdonosnév-formátumokat, például a következőhöz hasonlót:  

            **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

            Ez a példa egy olyan tulajdonosnév-formátumot hoz létre, amely a CN és az E változó mellett a Szervezeti Egység (OU), a Szervezet (O), a Hely (L) és az Ország/régió (C) értékek sztringjét is alkalmazza. A függvény leírását és a támogatott sztringeket a [CertStrToName függvény](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) című cikkben találhatja meg.

        **Eszköz tanúsítványtípus**  

        Az **Eszköz** tanúsítványtípus használatakor a következő eszköztanúsítvány-változókat is használhatja az értékhez:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Ezek a változók statikus szöveggel adhatók meg egy egyéni szövegmezőben. Például a köznapi nevek a következő formátumban adhatók meg: `CN = {{DeviceName}}text`.

        > [!IMPORTANT]
        >  - A tulajdonosnév statikus szövegében hibát okoznak a kapcsos zárójelek **{ }** , ha nem egy változót fognak közre. 
        >  - Az eszköztanúsítvány-változók használatakor a változót tegye kapcsos zárójelek **{ }** közé.
        >  - A `{{FullyQualifiedDomainName}}` csak a Windows rendszerű és tartományhoz csatlakoztatott eszközök esetén működik. 
        >  -  Ha a tulajdonosnévben megad olyan eszköztulajdonságokat, mint az IMEI, a sorozatszám vagy a teljes tartománynév, vagy az eszköztanúsítványban megadja a SAN-azonosítót, vegye figyelembe, hogy ezeket a tulajdonságokat az eszközhöz hozzáféréssel rendelkező személyek meghamisíthatják.
        >  - A profil nem lesz telepítve az eszközön, ha az eszköz megadott változói nem támogatottak. Például ha megad egy {{IMEI}} változót egy IMEI-számmal nem rendelkező eszközhöz rendelt SCEP profil tulajdonosnevében, a profil telepítése sikertelen lesz. 


   - **Tulajdonos alternatív nevének**: Adja meg, hogyan Intune-ban hozza létre automatikusan a tulajdonos alternatív neve (SAN) értékeit a tanúsítványkérelemben. A beállítások eltérőek a **Felhasználói** és az **Eszköz** tanúsítványtípus kiválasztásakor. 

        **Felhasználói tanúsítványtípus**  

        A következő attribútumok állnak rendelkezésre:

        - E-mail-cím
        - Egyszerű felhasználónév (UPN)

            Ha felhasználói tanúsítványtípust választott ki, akkor például az egyszerű felhasználónevet (UPN) is használhatja a tulajdonos alternatív neveként. Ha az ügyféltanúsítványt egy hálózati házirend-kiszolgálón történő hitelesítésre használja, a tulajdonos alternatív neveként az egyszerű felhasználónevet (UPN) állítsa be. 

        **Eszköz tanúsítványtípus**  

        Egy testreszabható, tábla formátumú szövegmező. A következő attribútumok állnak rendelkezésre:

        - DNS

        Az **Eszköz** tanúsítványtípusnál a következő eszköztanúsítvány-változókat használhatja az értékhez:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Ezek a változók statikus szöveggel adhatók meg az egyéni szövegmezőben. Például a DNS-attribútumok a következő formátumban adhatók meg: `DNS name = {{AzureADDeviceId}}.domain.com`.

        > [!IMPORTANT]
        >  - A tulajdonosnév statikus szövegében nem használhatók kapcsos zárójelek **{ }** , függőleges vonalak **|** és pontosvesszők **;** . 
        >  - Az eszköztanúsítvány-változók használatakor a változót tegye kapcsos zárójelek **{ }** közé.
        >  - A `{{FullyQualifiedDomainName}}` csak a Windows rendszerű és tartományhoz csatlakoztatott eszközök esetén működik. 
        >  -  Ha a tulajdonosnévben megad olyan eszköztulajdonságokat, mint az IMEI, a sorozatszám vagy a teljes tartománynév, vagy az eszköztanúsítványban megadja a SAN-azonosítót, vegye figyelembe, hogy ezeket a tulajdonságokat az eszközhöz hozzáféréssel rendelkező személyek meghamisíthatják.
        >  - A profil nem lesz telepítve az eszközön, ha az eszköz megadott változói nem támogatottak. Például ha megad egy {{IMEI}} változót egy IMEI-számmal nem rendelkező eszközhöz rendelt SCEP profil alternatív tulajdonosnevében, a profil telepítése sikertelen lesz.  

   - **Tanúsítvány érvényességi időtartama**: Ha futtatta a `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` parancsot a kiállító hitelesítésszolgáltató, amely lehetővé teszi az egyéni érvényességi időtartamot, megadhatja a tanúsítvány lejáratáig hátralévő időt mennyisége.<br>A tanúsítványsablonban megadott érvényességi időtartamnál rövidebb értéket is beállíthat, hosszabbat azonban nem. Ha például a tanúsítványsablonban két év van meghatározva a tanúsítvány érvényességi idejeként, akkor egy évet állíthat be értékként, öt évet azonban nem. Az értéknek emellett a kiállító hitelesítésszolgáltató tanúsítványának hátralévő érvényességi időszakánál is kevesebbnek kell lennie. 
   - **Kulcstároló-szolgáltató (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): Adja meg a tanúsítvány a kulcs tárolására. Az alábbi értékek közül választhat:
     - **Regisztrálás a platformmegbízhatósági modul kulcstároló-szolgáltatójába (ha van ilyen), máskülönben regisztrálás a szoftverkulcstároló-szolgáltatóba**
     - **Regisztrálás a platformmegbízhatósági modul kulcstároló-szolgáltatójába, máskülönben a művelet sikertelen**
     - **Regisztrálás a Passportba, máskülönben a művelet sikertelen (Windows 10 és újabb verzió)**
     - **Regisztrálás szoftverkulcstároló-szolgáltatóba**

   - **Kulcshasználat**: Adja meg a tanúsítvány kulcshasználati beállításait. A választható lehetőségek:
     - **Kulcstitkosítás**: Engedélyezi a kulcscserét, ha a kulcs titkosítva van
     - **Digitális aláírás**: Engedélyezi a kulcscserét, ha a kulcs védelmét digitális aláírás segíti
   - **Kulcsméret (bit)** : Válassza ki, hány bitet tartalmazzon a kulcs
   - **Kivonatoló algoritmus** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): Jelölje ki a tanúsítvánnyal használni kívánt kivonatoló algoritmust a rendelkezésre álló típusok közül. Válassza a kapcsolódó eszközöknél használható legerősebb biztonsági szintet.
   - **Legfelső szintű tanúsítvány**: Válasszon egy [megbízható főtanúsítvány-profil](certficates-pfx-configure.md#create-a-trusted-certificate-profile) , hogy előzőleg létre, és a felhasználói és/vagy az eszközhöz rendelt. Ennek a hitelesítésszolgáltatói tanúsítványnak a legfelső szintű tanúsítványnak kell lennie az adott tanúsítványprofilban konfigurált tanúsítványt kiállító hitelesítésszolgáltatónál. Győződjön meg arról, ugyanabba a csoportba hozzárendelve az SCEP-tanúsítványprofilt a megbízható főtanúsítvány-profil hozzárendelése.
   - **Kibővített kulcshasználat**: **Adjon hozzá** értékeket a tanúsítvány felhasználási célja. A legtöbb esetben a tanúsítványnál szükséges az **Ügyfél-hitelesítés**, hogy a felhasználó vagy az eszköz hitelesíthető legyen egy kiszolgálóval. Szükség szerint azonban tetszőleges más kulcshasználatot is felvehet.
   - **Regisztrációs beállítások**
     - **Megújítási küszöb (%)** : Adja meg, hogy a tanúsítvány eszköz idejénél igényelje a tanúsítvány élettartamának hány százalékos hátralévő.
     - **SCEP-kiszolgáló URL-címe**: Adja meg az NDES-kiszolgáló, amely SCEP-tanúsítványokat bocsát ki egy vagy több URL-címeket. Írja be például hasonló `https://ndes.contoso.com/certsrv/mscep/mscep.dll`.
     - A profil létrehozásához válassza az **OK**, majd a **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a profilok listáját tartalmazó panelen.

## <a name="assign-the-certificate-profile"></a>A tanúsítványprofil eszközökhöz rendelése

Mielőtt csoportokhoz rendeli a tanúsítványprofilokat, vegye figyelembe a következőket:

- Amikor csoportokhoz rendeli a tanúsítványprofilokat, a megbízható hitelesítésszolgáltatói tanúsítványprofilból származó tanúsítványfájl települ az eszközre. Az eszköz az SCEP-tanúsítványprofilt használja tanúsítványkérelem létrehozására.
- A tanúsítványprofilok csak a profil létrehozásakor használt platformot futtató eszközökre települnek.
- Tanúsítványprofilokat rendelhet felhasználógyűjteményekhez és eszközgyűjteményekhez is.
- Ha azt szeretné, hogy a tanúsítványok gyorsan megjelenjenek az eszközökön a regisztráció után, a tanúsítványprofilt felhasználócsoporthoz és ne eszközcsoporthoz rendelje hozzá. Ha eszközcsoporthoz rendel hozzá, akkor teljes eszközregisztráció szükséges, mielőtt az eszköz megkaphatná a szabályzatokat.
- Jóllehet az egyes profilokat külön-külön rendeli hozzá, a legfelső szintű hitelesítésszolgáltató és az SCEP- vagy PKCS-profil hozzárendelésére is szükség van. Ellenkező esetben az SCEP- vagy PKCS-tanúsítványszabályzat hibát fog jelezni.

    > [!NOTE]
    > Az iOS-eszközökön, ha SCEP-tanúsítványprofil profilhoz társítva egy további, például egy Wi-Fi vagy VPN-profilt, az eszköz megkaphatná a tanúsítvány minden további profilokhoz. Az eredmény az iOS-eszköz az SCEP-tanúsítvány kérelem által kínált több tanúsítványt kellene.  

- Ha használhat megosztott kezelés Intune-ban és a Configuration Manager, a Configuration Manager s[et a számítási feladatok csúszka](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads) a *erőforrás-hozzáférési házirend* való **Intune** vagy  **Az Intune próbacsapat**. Ez a beállítás lehetővé teszi, hogy a Windows 10-ügyfelek, a tanúsítvány igénylése a folyamat elindításához.  

Az profilok hozzárendeléséről az [Eszközprofilok hozzárendelése](device-profile-assign.md) című cikk nyújt tájékoztatást.

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Intune-összekötő beállításának ellenőrzése és hibaelhárítás

Problémák elhárításához és az Intune-összekötő telepítésének ellenőrzéséhez lásd: [Hitelesítésszolgáltató szkriptmintái](https://aka.ms/intuneconnectorverificationscript)

## <a name="intune-connector-events-and-diagnostic-codes"></a>Intune Connector-események és diagnosztikai kódok

A 6.1806.x.x verziótól kezdődően az Intune Connector Service naplózza az eseményeket az **Eseménynaplóban** (**Alkalmazás- és szolgáltatásnaplók** > **Microsoft Intune Connector**). Ezek az események segíthetnek elhárítani az Intune Connector konfigurációjával kapcsolatos esetleges problémákat. A naplózott eseményrekordokban megtalálhatja, hogy a művelet sikeres vagy sikertelen volt-e, illetve a rekordok diagnosztikai kódokat és üzeneteket is tartalmaznak, melyek segítenek a rendszergazdának a probléma elhárításában.

### <a name="event-ids-and-descriptions"></a>Eseményazonosítók és -leírások

> [!NOTE]
> Az egyes események vonatkozó diagnosztikai kódjairól bővebben a jelen cikk **Diagnosztikai kódok** című táblázatában tájékozódhat.

| Eseményazonosító      | Esemény neve    | Esemény leírása | Vonatkozó diagnosztikai kódok |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Az összekötő szolgáltatás elindult | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Az összekötőszolgáltatás leállt | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Az összekötő beléptetési tanúsítványa sikeresen megújult | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Az összekötő beléptetési tanúsítványának megújítása nem sikerült. Telepítse újra az összekötőt. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Nem sikerült beolvasni az összekötő beléptetési tanúsítványát a beállításjegyzékből. Ellenőrizze az eseményhez tartozó tanúsítvány-ujjlenyomatot. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Ellenőrizze az esemény diagnosztikai adatait. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Sikeresen ki lett bocsátva egy PKCS-tanúsítvány. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet, tanúsítványsablon-nevet és tanúsítvány-ujjlenyomatot. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Egy PKCS-tanúsítvány kibocsátása nem sikerült. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet, tanúsítványsablon-nevet és tanúsítvány-ujjlenyomatot. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Sikeresen vissza lett vonva a tanúsítvány. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet és tanúsítvány-sorozatszámot. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Nem sikerült a tanúsítvány visszavonása. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet és tanúsítvány-sorozatszámot. További információért tekintse át az NDES SVC-naplófájlokat.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Sikeresen fel lett töltve a tanúsítvány kérelme vagy visszavonási adata. A feltöltés részleteit megtalálhatja az esemény adataiban. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Nem sikerült feltölteni a tanúsítvány kérelmét vagy visszavonási adatait. Ellenőrizze az esemény adatai között megtalálható feltöltési állapotot a hiba helyének megállapításához.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Sikeresen le lett töltve egy kérelem egy tanúsítvány aláírására, egy ügyféltanúsítvány letöltésére vagy egy tanúsítvány visszavonására. A letöltés részleteit megtalálhatja az esemény adataiban.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Nem sikerült letölteni egy kérelmet egy tanúsítvány aláírására, egy ügyféltanúsítvány letöltésére vagy egy tanúsítvány visszavonására. A letöltés részleteit megtalálhatja az esemény adataiban. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | A tanúsítványregisztrációs pont sikeresen ellenőrzött egy ügyfélkérdést | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | A tanúsítványregisztrációs pont végzett, de elutasította a kérelmet. További részletekért ellenőrizze a diagnosztikai kódot és üzenetet. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | A tanúsítványregisztrációs pont nem tudott ellenőrizni egy ügyfélkérést. További részletekért ellenőrizze a diagnosztikai kódot és üzenetet. Az eseményüzenet adataiban megtalálhatja a kérdéshez tartozó eszközazonosítót. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | A tanúsítványregisztrációs pont sikeresen befejezte az értesítési folyamatot, és elküldte a tanúsítványt az ügyféleszköznek. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | A tanúsítványregisztrációs pont nem tudta befejezni az értesítési folyamatot. Az eseményüzenet adataiban megtalálhatja a kérelem részleteit. Ellenőrizze az NDES-kiszolgáló és a hitelesítésszolgáltató közötti kapcsolatot. | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>Diagnosztikai kódok

| Diagnosztikai kód | Diagnosztikai név | Diagnosztikai üzenet |
| -------------   | -------------   | -------------      |
| 0x00000000 | Siker  | Siker |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | A hitelesítésszolgáltató érvénytelen vagy elérhetetlen. Győződjön meg róla, hogy a hitelesítésszolgáltató elérhető, és hogy a kiszolgálója tud kommunikálni vele. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | A Symantec Client Auth tanúsítvány nem található meg a helyi tanúsítványtárban. Tekintse meg a cikket [Intune tanúsítvány-összekötő beállítása a DigiCert PKI Platform](https://docs.microsoft.com/intune/certificates-digicert-configure#troubleshooting) további információt.  |
| 0x00000402 | RevokeCert_AccessDenied  | A megadott fióknak nincs engedélye hitelesítésszolgáltatói tanúsítvány visszavonására. A kibocsátó hitelesítésszolgáltató nevét megtalálhatja a Hitelesítésszolgáltató neve mezőben.  |
| 0x00000403 | CertThumbprint_NotFound  | Nem található a bemenetnek megfelelő tanúsítvány. Regisztrálja a tanúsítvány-összekötőt, és próbálkozzon ismét. |
| 0x00000404 | Certificate_NotFound  | Nem található a megadott bemenetnek megfelelő tanúsítvány. Regisztrálja ismét a tanúsítvány-összekötőt, és próbálkozzon újra. |
| 0x00000405 | Certificate_Expired  | Egy tanúsítvány lejárt. Regisztrálja ismét a tanúsítvány-összekötőt a tanúsítvány megújításához, majd próbálkozzon újra. |
| 0x00000408 | CRPSCEPCert_NotFound  | Az CRP-titkosítás tanúsítványa nem található. Győződjön meg róla, hogy az NDES és az Intune-összekötő helyesen van beállítva. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Nem sikerült beolvasni az aláíró tanúsítványt. Győződjön meg róla, hogy az Intune Connector Service megfelelően van konfigurálva, és hogy az Intune Connector Service fut. Ellenőrizze emellett azt is, hogy a tanúsítvány letöltési eseményei sikeresen voltak-e. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Nem sikerült az SCEP-kérelem deszerializálása. Győződjön meg róla, hogy az NDES és az Intune-összekötő helyesen van beállítva. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Kérelem megtagadva lejárt tanúsítványkérdés miatt. Az ügyféleszköz megpróbálhatja ismét végrehajtani a műveletet, miután igényelt egy új kérdést a felügyeleti kiszolgálótól. |
| 0x0FFFFFFFF | Unknown_Error  | Nem tudtuk teljesíteni a kérelmét egy kiszolgálóoldali hiba miatt. Kérjük, próbálkozzon újból. |

## <a name="next-steps"></a>További lépések

- [PKCS-tanúsítványok használata](certficates-pfx-configure.md), vagy [kiállítani a Symantec PKI manager webes szolgáltatás PKCS-tanúsítványok](certificates-symantec-configure.md)
- [Adja hozzá a 3. fél hitelesítésszolgáltató SCEP használata az Intune-nal](certificate-authority-add-scep-overview.md)
- További segítségért használja a következő útmutatókat:
  - [Hibaelhárítási SCEP tanúsítványprofilok azon központi telepítését a Microsoft Intune-ban](https://support.microsoft.com/help/4457481)
  - [A Microsoft Intune tanúsítványprofiljai segítségével használható hibaelhárítási NDES-konfiguráció](https://support.microsoft.com/help/4459540)
