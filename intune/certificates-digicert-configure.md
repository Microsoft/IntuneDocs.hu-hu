---
title: DigiCert PKCS-tanúsítványok kiállítása Microsoft Intune
titleSuffix: Microsoft Intune
description: Telepítse és konfigurálja az Intune tanúsítvány-összekötőt, hogy PKCS-tanúsítványokat bocsásson ki az DigiCert PKI platformról az Intune által felügyelt eszközökre.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c68e8bafda1ca171df043adacb31ea05254903ff
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/30/2019
ms.locfileid: "71305231"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Az Intune tanúsítvány-összekötő beállítása a DigiCert PKI platformhoz  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az Intune Certificate Connector használatával PKCS-tanúsítványokat adhat ki az DigiCert PKI platformról az Intune által felügyelt eszközökre. Az összekötőt csak DigiCert hitelesítésszolgáltatóval (CA), vagy DigiCert-HITELESÍTÉSSZOLGÁLTATÓval és Microsoft-HITELESÍTÉSSZOLGÁLTATÓval is használhatja.  
> [!TIP]  
> A DigiCert megszerezte a Symantec webhelyének biztonsági és kapcsolódó PKI-megoldásait. A módosítással kapcsolatos további információkért tekintse meg a [Symantec technikai támogatásáról szóló cikket](https://support.symantec.com/en_US/article.INFO4722.html).

Ha már használja az Intune tanúsítvány-összekötőt a Microsoft HITELESÍTÉSSZOLGÁLTATÓTÓL származó tanúsítványok kiállításához a PKCS vagy a System Center Endpoint Protection használatával, ugyanezt az összekötőt használhatja egy DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL származó PKCS-tanúsítványok konfigurálásához és kiállításához. Miután elvégezte a konfigurálást a DigiCert CA támogatásához, az Intune Certificate Connector a következő tanúsítványokat tudja kiállítani:

* PKCS-tanúsítványok a Microsoft HITELESÍTÉSSZOLGÁLTATÓTÓL
* DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL származó PKCS-tanúsítványok
* Tanúsítványok Endpoint Protection Microsoft HITELESÍTÉSSZOLGÁLTATÓTÓL

Ha még nem telepítette az összekötőt, de azt tervezi, hogy a Microsoft HITELESÍTÉSSZOLGÁLTATÓI és DigiCert is használja, először hajtsa végre a Microsoft HITELESÍTÉSSZOLGÁLTATÓ összekötő-konfigurációját. Ezután térjen vissza ehhez a cikkhez annak konfigurálásához, hogy a DigiCert is támogassa. A tanúsítvány-profilokkal és az összekötővel kapcsolatos további információkért tekintse [meg az eszközökhöz tartozó tanúsítvány profiljának konfigurálása Microsoft Intuneban](certificates-configure.md)című témakört.  

Ha az összekötőt csak a DigiCert HITELESÍTÉSSZOLGÁLTATÓval fogja használni, a cikk utasításait követve telepítheti és konfigurálhatja az összekötőt. 

## <a name="prerequisites"></a>Előfeltételek  
- **Aktív előfizetés a DIGICERT CA**-ban: Az előfizetés szükséges ahhoz, hogy beszerezze a regisztrációs szolgáltató (RA) tanúsítványát a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL.

## <a name="install-the-digicert-ra-certificate"></a>A DigiCert RA-tanúsítvány telepítése  
 
1. Mentse a következő kódrészletet a **CertReq. ini** nevű fájlba, és frissítse a szükséges módon (például: *A tulajdonos neve CN formátumban*).
 
        [Version] 
        Signature="$Windows NT$" 
        
        [NewRequest] 
        ;Change to your,country code, company name and common name 
        Subject = "Subject Name in CN format"
        
        KeySpec = 1 
        KeyLength = 2048 
        Exportable = TRUE 
        MachineKeySet = TRUE 
        SMIME = False 
        PrivateKeyArchive = FALSE 
        UserProtected = FALSE 
        UseExistingKeySet = FALSE 
        ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
        ProviderType = 12 
        RequestType = PKCS10 
        KeyUsage = 0xa0 
        
        [EnhancedKeyUsageExtension] 
        OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication
        
        ;----------------------------------------------- 

2. Nyisson meg egy rendszergazda jogú parancssort, és hozzon elő egy tanúsítvány-aláírási kérelmet (CSR) a következő parancs használatával:

   `Certreq.exe -new certreq.ini request.csr`

3. Nyissa meg a Request. CSR fájlt a Jegyzettömbben, és másolja a CSR-tartalmat a következő formátumban:


        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Jelentkezzen be a DigiCert HITELESÍTÉSSZOLGÁLTATÓba, és tallózással keresse meg az **ra-tanúsítványt** a feladatokból.

   a. A szövegmezőbe írja be a CSR-tartalmat a 3. lépésben. 

   b. Adja meg a tanúsítvány rövid nevét.

   c. Válassza a **Folytatás**lehetőséget. 

   d. A megadott hivatkozás használatával töltse le az RA-tanúsítványt a helyi számítógépre.

5. Importálja az RA-tanúsítványt a Windows tanúsítványtárolóba:

   a. Nyisson meg egy MMC konzolt.

   b. Válassza a **fájl** > **beépülő modulok** > hozzáadása vagy eltávolítása**tanúsítvány** > **hozzáadása**lehetőséget. 

   c. Válassza a **számítógépfiók** > **tovább**lehetőséget.

   d. Válassza a **helyi számítógép** > **befejezése**lehetőséget. 

   e. Kattintson az **OK gombra** a **beépülő modul hozzáadása/eltávolítása** ablakban. Bontsa ki a **tanúsítványok (helyi számítógép)**  > **személyes** > **tanúsítványok**csomópontot.

   f. A jobb egérgombbal kattintson a **Tanúsítványok** csomópontra, és válassza a **Minden feladat** > **Importálás** lehetőséget.  

   g. Válassza ki a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL letöltött RA-tanúsítvány helyét, majd kattintson a **tovább**gombra.

   h. Válassza a **személyes tanúsítványtároló** > **következő**lehetőséget. 

   i. Válassza a **Befejezés** lehetőséget az ra tanúsítvány és annak titkos kulcsának a **helyi gép személyes** tárolójába való importálásához.  

6. A titkos kulcsú tanúsítvány exportálása és importálása: 

   a. Bontsa ki a **Tanúsítványok (Helyi számítógép)**  > **Személyes** > **Tanúsítványok** csomópontot.

   b. Válassza ki az előző lépésben importált tanúsítványt.

   c. Kattintson a jobb gombbal a tanúsítványra, és válassza a **minden feladat** > **Exportálás**lehetőséget.

   d. Válassza a **tovább**lehetőséget, majd adja meg a jelszót.

   e. Válassza ki az exportálandó helyet, majd kattintson a **Befejezés gombra**.

   f. Az 5. lépésben leírt eljárást követve importálja a titkos kulcs tanúsítványát a **helyi számítógép személyes** tárolójába.

   g. Rögzítsen egy másolatot az RA-tanúsítvány ujjlenyomatának szóközök nélkül. Az alábbi példa az ujjlenyomatot szemlélteti: 

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
    
    > [!NOTE]
    > Az RA-tanúsítvány DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL való beszerzésével kapcsolatos segítségért forduljon a [DigiCert ügyfélszolgálatához](mailto:enterprise-pkisupport@digicert.com).  

## <a name="prepare-to-install-intune-certificate-connector"></a>A Microsoft Intune Tanúsítvány-összekötő telepítésének előkészítése
> [!TIP]  
> Ez a szakasz akkor érvényes, ha az Intune Certificate Connectort csak DigiCert HITELESÍTÉSSZOLGÁLTATÓval fogja használni. Ha Intune Certificate Connectort használ egy Microsoft HITELESÍTÉSSZOLGÁLTATÓval, és hozzá kívánja adni a DigiCert CA-támogatását, ugorjon előre az [összekötő konfigurálásához a DigiCert támogatásához](#configure-the-connector-to-support-digicert).  

1. A következő listából válassza ki a Windows operációsrendszer-verzióinak egyikét, és telepítse azt egy számítógépre:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Hozzon létre egy rendszergazdai jogosultságokkal rendelkező felhasználót, és végezze el az alábbi lépéseket.

3. Keresse meg a legújabb Windows-frissítéseket, és telepítse őket, ha vannak ilyenek. A Windows-frissítések telepítése után indítsa újra a számítógépet.

4. Telepítse a .NET keretrendszer 3.5-ös verzióját:

   a. Nyissa meg a Vezérlőpult**programok és szolgáltatások** >  **felületét** > **a Windows-szolgáltatások be-és kikapcsolása**lehetőségre.

   b. Válassza ki **.NET-keretrendszer 3.5** elemet, és telepítése azt.  

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Az Intune tanúsítvány-összekötő telepítése a DigiCert való használathoz  

> [!TIP]  
> Ha az Intune Certificate Connectort Microsoft HITELESÍTÉSSZOLGÁLTATÓval szeretné felvenni, és hozzá kívánja adni a DigiCert HITELESÍTÉSSZOLGÁLTATÓI támogatást, ugorjon előre az [összekötő konfigurálásához a DigiCert támogatásához](#configure-the-connector-to-support-digicert).  

Töltse le az Intune tanúsítvány-összekötő legújabb verzióját az Intune felügyeleti portálján, és kövesse az alábbi utasításokat.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.  

2. Válassza az **eszköz konfigurációs** > **tanúsítvány összekötők** >  **+ Hozzáadás**lehetőséget.  

3. Válassza **a tanúsítvány-összekötő szoftver letöltése**lehetőséget. Mentse a szoftvert olyan helyre, ahol hozzá tud férni a-kiszolgálóról, ahová telepíteni fogja.  

   ![Az összekötő szoftver letöltése](./media/certificates-digicert-configure/connector-download.png)
   
4. Azon a kiszolgálón, amelyre telepíteni kívánja az összekötőt, futtassa a **NDESConnectorSetup. exe fájlt** emelt szintű jogosultságokkal. 

5. A **telepítési beállítások** lapon válassza a **pfx-eloszlás**lehetőséget.  
   
   ![PFX-eloszlás kiválasztása](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Ha az Intune Certificate Connector használatával szeretne tanúsítványokat kibocsátani egy Microsoft HITELESÍTÉSSZOLGÁLTATÓTÓL és egy DigiCert-HITELESÍTÉSSZOLGÁLTATÓTÓL, válassza a **SCEP és a pfx-profilok eloszlása**lehetőséget. 

6. Az összekötő beállításának befejezéséhez használja az alapértelmezett beállításokat.

## <a name="configure-the-connector-to-support-digicert"></a>Az összekötő konfigurálása a DigiCert támogatásához

Alapértelmezés szerint az Intune Certificate Connector telepítve van a **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**.

1. A **NDESConnectorSvc** mappában Nyissa meg a **NDESConnector. exe. config** fájlt a Jegyzettömbben.

   a. Frissítse a `RACertThumbprint` kulcs értékét az előző szakaszban másolt tanúsítvány ujjlenyomatának értékével. Példa:

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   
   b. Mentse és zárja be a fájlt.

2. Nyissa meg a **Services. msc fájlt**:

   a. Válassza ki az **Intune Connector Service** lehetőséget.

   b. Állítsa le, majd indítsa el újra a szolgáltatást.

   c. A szolgáltatás ablakának bezárásához.

## <a name="set-up-the-intune-administrator-account"></a>Az Intune-beli rendszergazdai fiók beállítása  

> [!TIP]  
> Ha Intune Certificate Connectort használ egy Microsoft HITELESÍTÉSSZOLGÁLTATÓval, és hozzá kívánja adni a DigiCert CA-támogatását, ugorjon a [megbízható tanúsítvány profiljának létrehozásához](#create-a-trusted-certificate-profile).   
 
1. Nyissa meg a NDES-összekötő felhasználói felületét az **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.  

2. A **beléptetés** lapon válassza a **Bejelentkezés**lehetőséget.

3. Adja meg az Intune-bérlői rendszergazdai hitelesítő adatait.

4. Válassza a **Bejelentkezés**lehetőséget, majd kattintson **az OK** gombra a sikeres regisztráció megerősítéséhez. Ezután lezárhatja az NDES-összekötő felhasználói felületét.
   
   ![NDES-összekötő felülete a "sikeresen regisztrált" üzenettel](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)



## <a name="create-a-trusted-certificate-profile"></a>Megbízható tanúsítványprofil létrehozása

Az Intune által felügyelt eszközökhöz telepítendő PKCS-tanúsítványokat megbízható főtanúsítvánnyal kell láncba helyezni. A lánc létrehozásához hozzon létre egy Intune-beli megbízható tanúsítványsablont a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL származó főtanúsítvánnyal.

1. Megbízható legfelső szintű tanúsítvány beszerzése az DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL:

    a. Jelentkezzen be a DigiCert HITELESÍTÉSSZOLGÁLTATÓI felügyeleti portálra.

    b. Válassza a **hitelesítésszolgáltatók kezelése** a **feladatokból**lehetőséget. 

    c. Válassza ki a megfelelő HITELESÍTÉSSZOLGÁLTATÓT a listából.  

    d. A megbízható főtanúsítvány letöltéséhez válassza a **Főtanúsítvány letöltése** lehetőséget.

2. Megbízható tanúsítvány profiljának létrehozása az Intune-portálon:

   a. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

   b. Válassza az **Eszközkonfiguráció** > **Kezelés** > **Profilok** > **Profil létrehozása** lehetőséget.

   c. Adja meg a megbízható tanúsítvány profiljához tartozó **név** és **Leírás** adatait.

   d. Válassza ki a megbízható tanúsítvány eszközplatformját a **Platform** legördülő listából.

   e. A **Profil típusa** legördülő listában válassza a **megbízható tanúsítvány**lehetőséget.

   f. Keresse meg az előző lépésben a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL beszerzett megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓ. cer fájlt, majd kattintson **az OK gombra**.

   g. Csak Windows 8,1 és Windows 10 rendszerű eszközök esetén válassza ki a megbízható tanúsítvány célját tárolót a következő helyről:    
      - **Számítógép tanúsítványtárolója – fő**  
      - **Számítógép tanúsítványtárolója – köztes**  
      - **Felhasználói tanúsítványtároló – köztes** 

   h. Ha elkészült, válassza az **OK** gombot, lépjen vissza a **Profil létrehozása** panelre, és válassza a **Létrehozás** gombot.  
 
A profil megjelenik a profilok listájában az **eszköz konfigurációja – profilok** ablaktáblán, és a **megbízható tanúsítvány**profiljának típusa jelenik meg.  Ügyeljen arra, hogy ezt a profilt a tanúsítványokat fogadó eszközökhöz rendelje. A profil csoportokhoz rendeléséhez lásd: [eszközbeállítások társítása](device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>A tanúsítvány-profil OID beszerzése  

A DigiCert CA-ban található tanúsítványfájl-sablonnal társítva van az OID-profil. A PKCS-tanúsítvány profiljának az Intune-ban való létrehozásához a tanúsítványsablon nevének a DigiCert HITELESÍTÉSSZOLGÁLTATÓI tanúsítvány-sablonhoz társított tanúsítvány-profil OID formátumúnak kell lennie.

1. Jelentkezzen be a DigiCert HITELESÍTÉSSZOLGÁLTATÓI felügyeleti portálra.
2. Válassza a **tanúsítvány-profilok kezelése**lehetőséget.
3. Válassza ki a használni kívánt tanúsítványsablont.
4. Másolja a tanúsítvány-profil OID-t. Az objektumazonosító a következő példához hasonlóan néz ki:

 
       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
 

> [!NOTE]
> Ha segítségre van szüksége a tanúsítvány-profil OID beszerzéséhez, forduljon a [DigiCert ügyfélszolgálatához](mailto:enterprise-pkisupport@digicert.com).

## <a name="create-a-pkcs-certificate-profile"></a>PKCS-tanúsítványprofil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.  

2. Nyissa meg az **eszköz konfigurációs** >  **profiljait**, és válassza a **profil létrehozása**lehetőséget.

3. Adja meg a PKCS-tanúsítvány profiljának **nevét** és **leírását** .  

4. A **platform** legördülő listából válassza ki a támogatott eszköz platformot.

5. A **Profil típusa** legördülő listában válassza a PKCS- **tanúsítvány**lehetőséget.
 
6. A **PKCS-tanúsítvány** ablaktáblán konfigurálja a paramétereket az alábbi táblázat értékeivel. Ezek az értékek szükségesek egy DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL származó PKCS-tanúsítványok kiállításához az Intune Certificate Connector használatával. 

   |PKCS-tanúsítvány paramétere | Value | Leírás |
   | --- | --- | --- |
   | Hitelesítésszolgáltató | pki-ws.symauth.com | Ennek az értéknek a DigiCert CA alapszolgáltatásának teljes tartományneve, záró perjel nélkül kell lennie. Ha nem biztos abban, hogy ez a DigiCert CA-előfizetés megfelelő alapszolgáltatásának teljes tartományneve, forduljon a DigiCert ügyfélszolgálatához. <br><br>*A Symantec és a DigiCert közötti váltás esetén ez az URL-cím változatlan marad*. <br><br> Ha ez a teljes tartománynév helytelen, az Intune tanúsítvány-összekötő nem tudja kiállítani a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL származó PKCS-tanúsítványokat.| 
   | Hitelesítésszolgáltató neve | Symantec | Ennek az értéknek a **Symantec** sztringnek kell lennie. <br><br> Ha ez az érték módosul, az Intune tanúsítvány-összekötő nem tudja kiállítani a PKCS-tanúsítványokat a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL.|
   | Tanúsítványsablon neve | A DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL származó OBJEKTUMAZONOSÍTÓ. Példa: **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Ennek az értéknek egy, az előző szakaszban a DigiCert HITELESÍTÉSSZOLGÁLTATÓI tanúsítvány profilja sablonból [beszerzett objektumazonosító-](#get-the-certificate-profile-oid) profilnak kell lennie. <br><br> Ha az Intune Certificate Connector nem talál ehhez a DigiCert HITELESÍTÉSSZOLGÁLTATÓhoz társított tanúsítványsablont, a rendszer nem ad ki PKCS-tanúsítványokat a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL.|  

   ![HITELESÍTÉSSZOLGÁLTATÓ és tanúsítványsablon kijelölése](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)  

   > [!NOTE]
   > A Windows platformokhoz készült PKCS-tanúsítvány profiljának nem kell megbízható tanúsítvány-profillal társítva lennie. Nem Windows platformú profilok (pl. Android profilok) esetén azonban szükséges a hozzárendelés.
7. Fejezze be a profil konfigurálását az üzleti igények kielégítéséhez, majd kattintson az **OK** gombra a profil mentéséhez. 

8. Válassza a **hozzárendelések** lehetőséget, és állítson be egy megfelelő csoportot, amely ezt a profilt fogja kapni. A hozzárendelt csoport legalább egy felhasználót vagy eszközt kell, hogy tartalmazzon.
 
Az előző lépések elvégzése után az Intune Certificate Connector PKCS-tanúsítványokat ad ki a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL a hozzárendelt csoportban lévő Intune által felügyelt eszközökre. Ezek a tanúsítványok az Intune által felügyelt eszköz **aktuális felhasználói** tanúsítványtárolójának **személyes** tárolójában lesznek elérhetők.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>A PKCS-tanúsítvány profiljának támogatott attribútumai

|Attribútum | Az Intune által támogatott formátumok | A DigiCert Cloud CA által támogatott formátumok | Eredmény |
| --- | --- | --- | --- |
| Tulajdonos neve |Az Intune az alábbi három formátumban támogatja a tulajdonos nevének megadását: <br><br> 1. Köznapi név <br> 2. E-mail címet tartalmazó köznapi név <br> 3. Köznapi név e-mailben <br><br> Példa: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | A DigiCert CA több attribútumot is támogat.  Ha további attribútumokat szeretne kijelölni, akkor azokat rögzített értékekkel kell definiálni az DigiCert-tanúsítvány profilja sablonban.| A PKCS tanúsítványkérelem köznapi nevét vagy e-mail-címét használja. <br><br> Az Intune-tanúsítvány profilja és a DigiCert sablonja közötti eltérés nem egyezik az DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL kiállított tanúsítványokkal.|
| Tulajdonos alternatív neve (SAN) | Az Intune a következő SAN-mezőértékeket támogatja: <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (kódolt érték) | A DigiCert Cloud CA ezeket a paramétereket is támogatja. Ha további attribútumokat szeretne kijelölni, akkor azokat rögzített értékekkel kell definiálni az DigiCert-tanúsítvány profilja sablonban. <br><br> **AltNameTypeEmail**: Ha ez a típus nem található a SAN-ben, az Intune Certificate Connector a **AltNameTypeUpn**értéket használja.  Ha a **AltNameTypeUpn** nem található meg a San-ben, akkor az Intune tanúsítvány-összekötő a tulajdonos nevében lévő értéket használja, ha az e-mail-formátuma.  Ha a típus még nem található, az Intune tanúsítvány-összekötő nem tudja kiállítani a tanúsítványokat. <br><br> Például: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: Ha ez a típus nem található meg a SAN-ban, az Intune Certificate Connector a **AltNameTypeEmail**értéket használja. Ha a **AltNameTypeEmail** nem található meg a San-ben, akkor az Intune tanúsítvány-összekötő a tulajdonos neve mező értékét használja, ha az e-mail formátuma. Ha a típus még nem található, az Intune tanúsítvány-összekötő nem tudja kiállítani a tanúsítványokat.  <br><br> Például: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: Ha ez a típus nem található a SAN-ben, az Intune tanúsítvány-összekötő nem tudja kiállítani a tanúsítványokat. <br><br> Például: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  Vegye figyelembe, hogy a mező értéke csak kódolt formátumban (hexadecimális érték) támogatott a DigiCert CA által. Ebben a mezőben bármely értéknél az Intune tanúsítvány-összekötő Base64-kódolásra konvertálja, mielőtt elküldi a tanúsítványkérelmet. *Az Intune Tanúsítvány-összekötő nem ellenőrzi, hogy az érték már kódolva van-e.* | Nincsenek |

## <a name="troubleshooting"></a>Hibaelhárítás

Az Intune Certificate Connector szolgáltatás naplói a NDES-összekötő számítógép **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** érhetők el. Nyissa meg a naplókat a [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) , és keressen kivételeket vagy hibaüzeneteket.

| Probléma/hibaüzenet | A megoldás lépései |
| --- | --- |
| Nem lehet bejelentkezni az Intune-bérlői rendszergazdai fiókkal a NDES-összekötő felhasználói felületén. | Ez akkor fordulhat elő, ha a helyszíni tanúsítvány-összekötő nincs engedélyezve az Intune felügyeleti portálján. A probléma megoldásához használja az alábbi eljárások egyikét: <br><br> A Silverlight felhasználói felületéről: <br> 1. Jelentkezzen be az [Intune felügyeleti portálra](https://admin.manage.microsoft.com). <br> 2. Válassza a **rendszergazda**elemet. <br> 3. Válassza a **mobileszköz-kezelő** > **tanúsítvány-összekötő**lehetőséget. <br> 4. Válassza **a helyszíni tanúsítvány-összekötő konfigurálása**lehetőséget. <br> 5. Jelölje be a **tanúsítvány-összekötő engedélyezése** jelölőnégyzetet. <br> 6. Kattintson az **OK** gombra. <br><br> Az Azure Portal felhasználói felületén: <br> 1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com). <br> 2. Lépjen Microsoft Intune. <br> 3. Válassza az **eszköz konfigurációja** > **hitelesítésszolgáltató**lehetőséget. <br> 4. Válassza ki **engedélyezése**. <br><br> Miután elvégezte az előző lépéseket a Silverlight felhasználói felületéről vagy a Azure Portalból, próbáljon meg ugyanazzal az Intune-bérlői rendszergazdai fiókkal bejelentkezni az NDES-összekötő felhasználói felületén. |
| Az NDES-összekötő tanúsítványa nem található. <br><br> System.ArgumentNullException: Az érték nem lehet null. | Az Intune Tanúsítvány-összekötő akkor jeleníti meg ezt a hibát, ha az Intune-bérlői rendszergazdai fiókkal még sosem jelentkeztek be az NDES-összekötő felhasználói felületére. <br><br> Ha a hiba továbbra is fennáll, indítsa újra az Intune szolgáltatás-összekötőt. <br><br> 1. Nyissa meg a **Services. msc fájlt**. <br> 2. Válassza ki az **Intune Connector Service** lehetőséget. <br> 3. Kattintson rá a jobb egérgombbal, majd válassza az **Újraindítás** lehetőséget.|
| NDES Connector - IssuePfx -Generic Exception: (NDES-összekötő - IssuePfx - Általános kivétel:) <br> System.NullReferenceException: Az objektum hivatkozása nem az objektum egy példányára van beállítva. | Ez a hiba átmeneti. Indítsa újra az Intune szolgáltatás-összekötőt. <br><br> 1. Nyissa meg a **Services. msc fájlt**. <br> 2. Válassza ki az **Intune Connector Service** lehetőséget. <br> 3. Kattintson rá a jobb egérgombbal, majd válassza az **Újraindítás** lehetőséget. |
| DigiCert-szolgáltató – nem sikerült beolvasni a DigiCert házirendet. <br><br>"A művelet túllépte az időkorlátot." | Az Intune tanúsítvány-összekötő művelet időtúllépési hibát kapott a DigiCert HITELESÍTÉSSZOLGÁLTATÓval való kommunikáció során. Ha a hiba továbbra is fennáll, növelje a kapcsolódás időtúllépési értékét, és próbálkozzon újra. <br><br> A kapcsolódás időkorlátjának növeléséhez: <br> 1. Nyissa meg az NDES-összekötőt futtató számítógépet. <br>2. Nyissa meg a **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** fájlt a Jegyzettömbben. <br> 3. Növelje a következő paraméter időtúllépési értékét: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Indítsa újra az Intune Certificate Connector szolgáltatást. <br><br> Ha a probléma továbbra is fennáll, forduljon a DigiCert ügyfélszolgálatához. |
| DigiCert-szolgáltató – nem sikerült beolvasni az ügyféltanúsítványt. | Az Intune tanúsítvány-összekötő nem tudta beolvasni az erőforrás-engedélyezési tanúsítványt a helyi számítógép személyes tanúsítványtárolójában. A probléma megoldásához telepítse az erőforrás-engedélyezési tanúsítványt a helyi számítógép személyes tanúsítványtárolójában a titkos kulcsával együtt. <br><br> Az erőforrás-engedélyezési tanúsítványt a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL kell beszerezni. További részletekért forduljon a DigiCert ügyfélszolgálatához. | 
| DigiCert-szolgáltató – nem sikerült beolvasni a DigiCert házirendet. <br><br>"A kérelem megszakadt: Nem hozható létre SSL/TLS biztonságos csatorna. " | Ez a hiba a következő esetekben jelentkezhet: <br><br> 1. Az Intune Certificate Connector szolgáltatás nem rendelkezik engedéllyel az erőforrás-engedélyezési tanúsítvány és a titkos kulcs beolvasásához a helyi számítógép személyes tanúsítványtárolójában. A probléma megoldásához keresse meg az összekötő szolgáltatás futó környezeti fiókját a Services. msc-ben. Az összekötő szolgáltatásnak az NT AUTHORITY\SYSTEM környezetben kell futnia. <br><br> 2. Előfordulhat, hogy az Intune felügyeleti portál PKCS-tanúsítvány profilja érvénytelen alapszolgáltatási FQDN-vel van konfigurálva a DigiCert HITELESÍTÉSSZOLGÁLTATÓhoz. A teljes tartománynév a **PKI-ws.symauth.com**hasonló. A probléma megoldásához forduljon a DigiCert ügyfélszolgálatához, hogy az URL-cím helyes-e az előfizetéséhez. <br><br> 3. Az Intune tanúsítvány-összekötő nem tud hitelesíteni a DigiCert HITELESÍTÉSSZOLGÁLTATÓval az erőforrás-engedélyezési tanúsítványon keresztül, mert nem tudja beolvasni a titkos kulcsot. A probléma megoldásához telepítse az erőforrás-engedélyezési tanúsítványt és annak titkos kulcsát a helyi számítógép személyes tanúsítványtárolójában. <br><br> Ha a probléma továbbra is fennáll, forduljon a DigiCert ügyfélszolgálatához. |
| DigiCert-szolgáltató – nem sikerült beolvasni a DigiCert házirendet. <br><br>"A kérelem elem nem értelmezhető." | Az Intune tanúsítvány-összekötő nem tudta lekérni az DigiCert-sablon sablonját, mert az OBJEKTUMAZONOSÍTÓ nem felel meg az Intune-tanúsítvány profiljának. Egy másik esetben az Intune tanúsítvány-összekötő nem találja a DigiCert CA-ban található ügyfél-profil OID-hez társított tanúsítványsablont. <br><br> A probléma megoldásához szerezze be a megfelelő ügyféloldali profilt OID-t a DigiCert HITELESÍTÉSSZOLGÁLTATÓ DigiCert-tanúsítvány sablonjában. Ezután frissítse a PKCS-tanúsítvány profilját az Intune felügyeleti portálján. <br><br> Szerezze be az ügyfél-profil OID-t a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL: <br> 1. Jelentkezzen be a DigiCert HITELESÍTÉSSZOLGÁLTATÓI felügyeleti portálra. <br> 2. Válassza a **tanúsítvány-profilok kezelése**lehetőséget. <br> 3. Válassza ki a használni kívánt tanúsítványsablont. <br> 4. A tanúsítvány-profil OID beszerzése. Az objektumazonosító a következő példához hasonlóan néz ki: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> A PKCS-tanúsítvány profiljának frissítése a megfelelő tanúsítványfájl OID-vel: <br>1. Jelentkezzen be az Intune felügyeleti portálra. <br> 2. Nyissa meg a PKCS-tanúsítvány profilját, és válassza a **Szerkesztés**lehetőséget. <br> 3. Frissítse a tanúsítvány-profil OID-t a tanúsítványsablon neve mezőben. <br> 4. Mentse a PKCS-tanúsítvány profilját. |
| DigiCert-szolgáltató – a házirend ellenőrzése nem sikerült. <br><br> Az attribútum nem tartozik a DigiCert által támogatott tanúsítványsablon-attribútumok listához. | Az DigiCert CA ezt az üzenetet jeleníti meg, ha eltérés van a DigiCert-tanúsítvány profilja és az Intune-tanúsítvány profilja között. Ez a probléma valószínűleg azért történt, mert az attribútum nem egyezik a **SubjectName** vagy a **SubjectAltName**. <br><br> A probléma megoldásához válassza az Intune által támogatott attribútumok elemet a **SubjectName** és a **SubjectAltName** az DigiCert-tanúsítvány profilja sablonban. További információ: az Intune által támogatott attribútumok a **tanúsítvány paramétereinek** szakaszában. |
| Egyes felhasználói eszközök nem kapnak PKCS-tanúsítványokat a DigiCert HITELESÍTÉSSZOLGÁLTATÓTÓL. | Ez a probléma akkor fordul elő, ha a felhasználó UPN-je speciális karaktereket tartalmaz `global_admin@intune.onmicrosoft.com`(például:). <br><br> A DigiCert HITELESÍTÉSSZOLGÁLTATÓ nem támogatja a speciális karaktereket a **mail_firstname** és a **mail_lastname**. <br><br> A problémát az alábbi lépésekkel oldhatja meg: <br><br> 1. Jelentkezzen be a DigiCert HITELESÍTÉSSZOLGÁLTATÓI felügyeleti portálra. <br> 2. Nyissa meg a **tanúsítvány-profilok kezelése lapot**. <br> 3. Válassza ki az Intune-hoz használt tanúsítványsablont. <br> 4. Válassza a **testreszabási beállítások** hivatkozást. <br> 5. Kattintson a **Speciális beállítások** gombra. <br> 6. A **tanúsítvány mezői – tulajdonos DN**területen adjon hozzá egy **KÖZNAPI nevet (CN)** , és törölje a meglévő **köznapi név (CN)** mezőt. A hozzáadási és törlési műveleteket együtt kell végrehajtani. <br> 7. Kattintson a **Mentés** gombra. <br><br> Az előző módosítással a DigiCert-tanúsítvány profilja a **"CN<upn>="** értéket kéri a **mail_firstname** és a **mail_lastname**helyett. |
| A felhasználó manuálisan törölt egy már telepített tanúsítványt az eszközéről. | Az Intune a következő bejelentkezéskor és a szabályzatok betartatásakor újra üzembe helyezi ugyanazt a tanúsítványt. Ebben az esetben a NDES-összekötő nem kap PKCS-tanúsítványkérelmet. |

## <a name="next-steps"></a>További lépések

A jelen cikkben található információk mellett a [mi Microsoft Intune-eszköz profilokkal](device-profiles.md) kapcsolatos információk is szerepelnek? a szervezet eszközeinek és a hozzájuk tartozó tanúsítványok kezeléséhez.

