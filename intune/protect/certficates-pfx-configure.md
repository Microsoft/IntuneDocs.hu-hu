---
title: Magán-és nyilvános kulcsú tanúsítványok használata a Microsoft Intune-Azure-ban | Microsoft Docs
description: A nyilvános kulcsú titkosítási szabványok (PKCS) tanúsítványai a Microsoft Intune, a főtanúsítványok és tanúsítványsablonok használata, az Intune Certificate Connector (NDES) telepítése, valamint a PKCS-tanúsítványhoz tartozó eszköz-konfigurációs profilok használata.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d35d7470508b610f850ca7f9f394e0d26bec677
ms.sourcegitcommit: 576b9528629981e87e775fac146932e502f07a74
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258096"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>PKCS-tanúsítványok konfigurálása és használata az Intune-nal

Az Intune támogatja a magán-és nyilvános kulcspár-(PKCS-) tanúsítványok használatát. Ez a cikk segítséget nyújt a szükséges infrastruktúra, például a helyszíni tanúsítvány-összekötők konfigurálásához, a PKCS-tanúsítvány exportálásához, majd a tanúsítvány hozzáadásához az Intune-eszköz konfigurációs profiljához.

A Microsoft Intune beépített beállításokat tartalmaz a PKCS-tanúsítványok használatára a szervezet erőforrásaihoz való hozzáféréshez és hitelesítéshez. A tanúsítványok hitelesítése és biztonságos hozzáférés a vállalati erőforrásokhoz, például VPN-hez vagy WiFi-hálózathoz. Ezeket a beállításokat az Intune-ban az eszköz konfigurációs profiljait használó eszközökre kell telepíteni.

További információ az importált PKCS-tanúsítványok használatáról: [importált pfx-tanúsítványok](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Követelmények

A PKCS-tanúsítványok Intune-nal való használatához a következő infrastruktúrára lesz szüksége:

- **Active Directory tartomány**:  
  Az ebben a szakaszban felsorolt összes kiszolgálónak csatlakoznia kell a Active Directory tartományhoz.

  A Active Directory tartományi szolgáltatások (AD DS) telepítésével és konfigurálásával kapcsolatos további információkért lásd: [AD DS tervezés és tervezés](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Hitelesítésszolgáltató**:  
   Vállalati hitelesítésszolgáltató (CA).

  A Active Directory tanúsítványszolgáltatások (AD CS) telepítésével és konfigurálásával kapcsolatos információkért tekintse meg a következő témakört: [Active Directory tanúsítványszolgáltatások lépésenkénti útmutatója](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > Az Intune követelményei szerint az AD CS-t vállalati hitelesítésszolgáltatóval, és nem önálló hitelesítésszolgáltatóval kell futtatni.

- **Ügyfél**:  
  A vállalati HITELESÍTÉSSZOLGÁLTATÓhoz való kapcsolódáshoz.

- **Főtanúsítvány**:  
  Vállalati hitelesítésszolgáltatótól származó főtanúsítvány exportált másolata.

- **Microsoft Intune tanúsítvány-összekötő** (más néven az *NDES Certificate Connector*):  
  Az Intune-portálon válassza az **eszköz konfigurációja** > **tanúsítvány-összekötők** > **Hozzáadás**lehetőséget, és kövesse a *lépéseket az összekötő PKCS #12 telepítéséhez*. Az **NDESConnectorSetup. exe**tanúsítvány-összekötő telepítőjének letöltéséhez használja a portál letöltési hivatkozását.  

  Az Intune legfeljebb 100 példányt támogat a bérlők számára. A összekötő minden példányának külön Windows-kiszolgálón kell lennie. Az összekötő egy példányát telepítheti ugyanarra a kiszolgálóra, mint a PFX tanúsítvány-összekötő példánya Microsoft Intune. Több összekötő használata esetén az összekötő-infrastruktúra támogatja a magas rendelkezésre állást és a terheléselosztást, mivel bármely elérhető összekötő-példány feldolgozhatja a PKCS-tanúsítványkérelmek kérelmeit. 

  Ez az összekötő a hitelesítéshez vagy az S/MIME e-mailek aláírásához használt PKCS-tanúsítványkérelmek feldolgozását végzi.

  A Microsoft Intune Tanúsítvány-összekötő támogatja a Federal Information Processing standard (FIPS) üzemmódot is. A FIPS nem szükséges, de ha engedélyezve van, akkor lehetőség van tanúsítványok kibocsátására és visszavonására.

- **Pfx tanúsítvány-összekötő a Microsoft Intunehoz**:  
  Ha az S/MIME e-mailek titkosítását tervezi használni, az Intune-portálon töltheti le a pfx-tanúsítványok importálását támogató *pfx tanúsítvány-összekötőt* .  Nyissa meg az **eszköz konfigurációja** > **tanúsítvány-összekötők** > **Hozzáadás**lehetőséget, majd kövesse a *lépéseket az importált pfx-tanúsítványokhoz tartozó összekötő telepítéséhez*. Az **PfxCertificateConnectorBootstrapper. exe**telepítőjének letöltéséhez használja a portál letöltési hivatkozását. 

  Minden Intune-bérlő támogatja az összekötő egyetlen példányát. Ezt az összekötőt telepítheti ugyanarra a kiszolgálóra, mint az Microsoft Intune Certificate Connector példánya.

  Ez az összekötő kezeli az Intune-ba importált PFX-fájlok kéréseit egy adott felhasználó számára az S/MIME e-mail-titkosításhoz.  

  Ez az összekötő automatikusan képes frissíteni magát, ha új verziók válnak elérhetővé. A frissítési képesség használatához a következőket kell tennie:
  - Telepítse a PFX tanúsítvány-összekötőt Microsoft Intune a kiszolgálón.  
  - A fontos frissítések automatikus fogadásához győződjön meg arról, hogy a tűzfalak nyitva vannak, amelyek lehetővé teszik, hogy az összekötő kapcsolatba lépjen a **443**-es port **AutoUpdate.msappproxy.net** .   

  További információ: [Microsoft Intune hálózati végpontok és az](../fundamentals/intune-endpoints.md) [Intune hálózati konfigurációs követelményei és sávszélessége](../fundamentals/network-bandwidth-use.md).

- **Windows Server**:  
  Windows-kiszolgálót használ a gazdagéphez:

  - Microsoft Intune Tanúsítvány-összekötő – hitelesítéshez és S/MIME e-mail aláírási forgatókönyvekhez
  - PFX tanúsítvány-összekötő a Microsoft Intunehoz – S/MIME e-mail titkosítási forgatókönyvek esetén.

  Az Intune támogatja a *pfx tanúsítvány-összekötő* telepítését ugyanarra a kiszolgálóra, mint a *Microsoft Intune tanúsítvány-összekötő*.
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Főtanúsítvány exportálása a vállalati hitelesítésszolgáltatótól

VPN-, WiFi-vagy más erőforrásokkal rendelkező eszköz hitelesítéséhez az eszköznek szüksége van egy gyökérszintű vagy köztes HITELESÍTÉSSZOLGÁLTATÓI tanúsítványra. Az alábbi lépések ismertetik a szükséges tanúsítvány beszerzését a vállalati hitelesítésszolgáltatótól.

**Parancssor használata**:  
1. Jelentkezzen be a legfelső szintű hitelesítésszolgáltató kiszolgálóra rendszergazdai fiókkal.
 
2. Lépjen a **Start** > **Futtatás**elemre, majd írja be a **cmd** parancsot a parancssor megnyitásához. 
    
3. A legfelső szintű tanúsítvány *ca_name. cer*nevű fájlként való exportálásához a **Certutil-ca. CERT ca_name. cer** fájlt kell megadnia.



## <a name="configure-certificate-templates-on-the-ca"></a>Tanúsítványsablonok konfigurálása a HITELESÍTÉSSZOLGÁLTATÓN

1. Jelentkezzen be a vállalati hitelesítésszolgáltatóhoz egy rendszergazdai jogosultságokkal rendelkező fiókkal.
2. Nyissa meg a **Hitelesítésszolgáltató** konzolt, majd kattintson a jobb gombbal a **Tanúsítványsablonok** elemre, és válassza a **Kezelés** lehetőséget.
3. Keresse meg a **felhasználói** tanúsítványsablont, kattintson rá a jobb gombbal, majd válassza a **sablon megkettőzése** lehetőséget az **új sablon tulajdonságainak**megnyitásához.

    > [!NOTE]
    > S/MIME e-mail-aláírás és titkosítás esetén sok rendszergazda külön tanúsítványt használ az aláíráshoz és a titkosításhoz. Ha a Microsoft Active Directory Tanúsítványszolgáltatást használja, akkor használhatja az **Exchange Signature Only** (csak Exchange-aláírás) sablont S/MIME e-mail-aláírási tanúsítványokhoz, és az **Exchange User** (Exchange felhasználó) sablont S/MIME titkosítási tanúsítványokhoz.  Ha harmadik féltől származó hitelesítésszolgáltatót használ, javasoljuk, hogy tekintse át az aláírási és titkosítási sablonok beállításához szükséges útmutatást.

4. A **Kompatibilitás** lapon:

    - Állítsa a **Hitelesítésszolgáltató** beállítást **Windows Server 2008 R2** értékre.
    - Állítsa a **Tanúsítvány kezdeményezettje** beállítást **Windows 7 / Server 2008 R2** értékre.

5. Állítsa be az **Általános** lapon a **Sablon megjelenítendő neve** beállítást egy aktuális névre.

    > [!WARNING]
    > A **Sablon neve** alapértelmezés szerint ugyanaz, mint a **Sablon megjelenítendő neve**, *szóköz nélkül*. Jegyezze fel a sablon nevét, mert később szüksége lesz rá.

6. A **Kérelmek kezelése** lapon válassza **A titkos kulcs exportálható** beállítást.
7. A **Titkosítás** lapon ellenőrizze, hogy a **Minimális kulcshossz** értéke 2048.
8. A **Tulajdonos neve** lapon válassza a **Kérelemben megadva** lehetőséget.
9. A **Bővítmények** lapon ellenőrizze, hogy az **Alkalmazásszabályzatok** területen láthatók-e a következő elemek: Titkosított fájlrendszer, Biztonságos e-mail, Ügyfél-hitelesítés.

    > [!IMPORTANT]
    > iOS-tanúsítványsablonok esetén a **Kiterjesztések** lapon frissítse a **Kulcshasználat** beállítást, és ügyeljen rá, hogy **Az aláírás igazolja az eredetet** jelölőnégyzet ne legyen bejelölve.

10. A **Biztonság** lapon vegye fel annak a kiszolgálónak a fiókját, amelyen telepíti a Microsoft Intune Tanúsítvány-összekötőt. Adja meg a fiók számára az **Olvasás** és **Beléptetés** engedélyeket.
11. A tanúsítvány mentéséhez válassza ki az **Alkalmaz** > **OK** elemet. Zárja be a **Tanúsítvány-sablonok konzolt**.
12. A **Hitelesítésszolgáltató** konzolon kattintson a jobb gombbal a **Tanúsítványsablonok** > **Új** > **Kiállítandó tanúsítványsablon** elemre. Válassza ki az iménti lépésekben létrehozott sablont. Válassza az **OK** gombot.
13. Ahhoz, hogy a kiszolgáló kezelhesse a regisztrált eszközök és felhasználók tanúsítványait, kövesse az alábbi lépéseket:

    1. Kattintson a jobb gombbal a hitelesítésszolgáltatóra, majd kattintson a **Tulajdonságok** elemre.
    2. A biztonság lapon vegye fel annak a kiszolgálónak a fiókját, amelyen az összekötőket (**Microsoft Intune Tanúsítvány-összekötő** vagy **Microsoft Intune-hoz készült PFX tanúsítvány-összekötő**) futtatja. 
    3. A fiók számára adja meg a **Tanúsítványok kiadása és kezelése** és a **Tanúsítványkérés** engedélyeket.

14. Jelentkezzen ki a vállalati hitelesítésszolgáltatóból.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>A Microsoft Intune Tanúsítvány-összekötő letöltése, telepítése és konfigurálása

> [!IMPORTANT]  
> A Microsoft Intune Tanúsítvány-összekötő nem telepíthető a kiállító hitelesítésszolgáltatóra (CA), hanem külön Windows Serverre kell telepíteni.  

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** > **tanúsítvány-összekötők** >  **+ Hozzáadás**lehetőséget.

3. Kattintson a *tanúsítvány-összekötő szoftver letöltése* a PKCS #12-összekötőhöz elemre, és mentse a fájlt egy olyan helyre, amely az összekötő telepítéséhez használt kiszolgálóról érhető el.

   ![Microsoft Intune Tanúsítvány-összekötő Letöltés](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. A letöltés befejezése után jelentkezzen be a kiszolgálóra. Ha ez megvan:

    1. Győződjön meg róla, hogy telepítve van-e a .NET keretrendszer 4.5 vagy újabb verziója, mivel arra szüksége van az NDES tanúsítvány-összekötőjének. A .NET 4.5-keretrendszer automatikusan részen a Windows Server 2012 R2 és újabb verzióknak.
    2. Futtassa a telepítőprogramot (NDESConnectorSetup.exe), és fogadja el az alapértelmezett helyet. A telepítő az összekötőt a `\Program Files\Microsoft Intune\NDESConnectorUI` helyen telepíti. A Telepítőbeállítás oldalon válassza a **PFX terjesztése**, lehetőséget. Folytassa és fejezze be a telepítést.
    3. Az összekötő-szolgáltatás alapértelmezés szerint a helyi rendszerfiók alatt fut. Ha az Internet eléréséhez proxy szükséges, akkor győződjön meg arról, hogy a helyi szolgáltatásfiók hozzáfér a proxy-beállításokhoz a kiszolgálón.

5. A Microsoft Intune Tanúsítvány-összekötő megnyitja a **beléptetés** lapot. Az Intune-nal való kapcsolódás engedélyezéséhez **Jelentkezzen**be, és adjon meg egy globális rendszergazdai jogosultságokkal rendelkező fiókot.
6. Javasoljuk, hogy a **Speciális** lapon hagyja kijelölve az **E számítógép SYSTEM fiókjának a használata (alapértelmezett)** beállítást.
7. **Alkalmaz** > **Bezárás**
8. Lépjen vissza az Intune-portálra (**intune** > **eszköz konfigurációja** > **tanúsítási összekötők**). Néhány pillanat múlva megjelenik egy zöld pipa jel, és a **kapcsolatok állapota** **aktív**. Az összekötő kiszolgáló mostantól kapcsolatba tud lépni az Intune-nal.
9. Ha a hálózati környezetben van webproxyja, további konfigurációkra lehet szükség az összekötő működésének engedélyezéséhez. További információ: a [meglévő helyszíni proxykiszolgálók használata](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) az Azure Active Directory dokumentációjában.
<ul><li>Android Enterprise (*munkahelyi profil*)</li><li>iOS</li><li>macOS</li><li>A Windows 10 és újabb > a Microsoft Intune Tanúsítvány-összekötő támogatja a TLS 1,2-t. Ha a TLS 1,2 telepítve van az összekötőt futtató kiszolgálón, az összekötő a TLS 1,2-et használja. Ellenkező esetben a TLS 1,1 használatos. Az eszközök és a kiszolgáló közötti hitelesítéshez jelenleg a TLS 1.1 van használatban.

## <a name="create-a-trusted-certificate-profile"></a>Megbízható tanúsítványprofil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

   ![Navigáljon az Intune-hoz, és hozzon létre egy új profilt egy megbízható tanúsítványhoz](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Adja meg a következő tulajdonságokat:

    - **Név** a profil számára
    - Igény szerint hozzáadhat egy leírást
    - **Platform**, amelyen telepíteni kell a profilt
    - A **Profiltípust** állítsa **Megbízható tanúsítványra**

4. Válassza a **Beállítások**lehetőséget, majd adja meg a korábban exportált. cer fájl legfelső szintű hitelesítésszolgáltatói tanúsítványát.

   > [!NOTE]
   > A **2. lépésben**kiválasztott platformtól függően előfordulhat, hogy nem rendelkezik a tanúsítvány **célhelyének** kiválasztására szolgáló lehetőséggel.

   ![Profil létrehozása és megbízható tanúsítvány feltöltése](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. A profil mentéséhez kattintson az **OK** > **Létrehozás** gombra.

6. Az új profil egy vagy több eszközhöz történő hozzárendeléséhez lásd: [Microsoft Intune-eszközprofilok hozzárendelése](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>PKCS-tanúsítványprofil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza ki, majd lépjen az **eszközök** > **konfigurációs profilok** lehetőségre, > **hozzon létre profilt**.

3. Adja meg a következő tulajdonságokat:

    - **Név** a profil számára
    - Igény szerint hozzáadhat egy leírást
    - **Platform**, amelyen telepíteni kell a profilt
    - A **Profiltípust** állítsa **PKCS-tanúsítványra**

4. Válassza a **Beállítások**lehetőséget, és konfigurálja a kiválasztott platformra vonatkozó tulajdonságokat:
   
   |Beállítás     | Platform     | Részletek   |
   |------------|------------|------------|
   |**Megújítási küszöb (%)**        |<ul><li>Összes         |Ajánlott érték 20%  | 
   |**Tanúsítvány érvényességi időtartama**  |<ul><li>Összes         |Ha nem módosította a tanúsítványsablont, akkor ez a beállítás egy évig állítható be. |
   |**Kulcstároló-szolgáltató (KSP)**   |<ul><li>Windows 10  | Windows esetén válassza ki a kulcsok tárolásának helyét az eszközön. |
   |**Hitelesítésszolgáltató**      |<ul><li>Összes         |Megjeleníti a vállalati HITELESÍTÉSSZOLGÁLTATÓ belső teljes tartománynevét (FQDN).  |
   |**Hitelesítésszolgáltató neve** |<ul><li>Összes         |Felsorolja a vállalati HITELESÍTÉSSZOLGÁLTATÓ nevét, például a "contoso hitelesítésszolgáltató" nevet. |
   |**Tanúsítvány típusa**             |<ul><li>Android Enterprise (*munkahelyi profil*)</li><li>iOS</li><li>macOS</li><li>Windows 10 és újabb|Válasszon egy típust: <ul><li> A **felhasználói** tanúsítványok a tulajdonos és a tanúsítvány Tárolóhálózati felhasználói és eszköz attribútumait is tartalmazhatják. </il><li>Az **eszközök** tanúsítványainak csak a tulajdonos és a tanúsítvány Tárolóhálózati attribútumait tartalmazhatják. Eszköz használata olyan forgatókönyvekhez, mint a felhasználó nélküli eszközök, például kioszkok vagy más megosztott eszközök.  <br><br> Ez a beállítás hatással van a tulajdonos nevének formátumára. |
   |**Tulajdonos nevének formátuma**          |<ul><li>Összes         |A legtöbb platform esetében állítsa ezt a beállítást a **köznapi névre** , hacsak másként nem kötelező.<br><br>A következő platformokon a tulajdonos nevének formátumát a tanúsítvány típusa határozza meg: <ul><li>Android Enterprise (*munkahelyi profil*)</li><li>iOS</li><li>macOS</li><li>Windows 10 és újabb</li></ul>  <p> A cikk későbbi részében lásd a [tulajdonos nevének formátumát](#subject-name-format) . |
   |**Tulajdonos alternatív neve**     |<ul><li>Összes         |Ha ez a beállítás nem kötelező, adja meg az egyszerű felhasználónév **(UPN)** beállítást. |
   |**Kibővített kulcshasználat**           |<ul><li> Android-eszköz rendszergazdája </li><li>Android Enterprise (*eszköz tulajdonosa*, *munkahelyi profil*) </li><li>Windows 10 |A tanúsítványokhoz általában szükség van az *ügyfél-hitelesítésre* , hogy a felhasználó vagy az eszköz hitelesíthető legyen egy kiszolgálóval. |
   |**Minden alkalmazás titkos kulcshoz való hozzáférésének engedélyezése** |<ul><li>macOS  |Az **Engedélyezés** beállítás megadásával biztosíthatja, hogy a rendszer a társított Mac-eszközhöz a PKCS-tanúsítvány titkos kulcsához konfigurált alkalmazásokat adjon. <br><br> A beállítással kapcsolatos további információkért tekintse meg a [konfigurációs profil referenciájának](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) *AllowAllAppsAccess* című szakaszt az Apple fejlesztői dokumentációjában. |
   |**Főtanúsítvány**             |<ul><li>Android-eszköz rendszergazdája </li><li>Android Enterprise (*eszköz tulajdonosa*, *munkahelyi profil*) |Válasszon ki egy korábban hozzárendelt legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítvány-profilt. |

5. A profil mentéséhez kattintson az **OK** > **Létrehozás** gombra.

6. Az új profil egy vagy több eszközhöz történő hozzárendeléséhez lásd: [Microsoft Intune-eszközprofilok hozzárendelése](../configuration/device-profile-assign.md).

   > [!NOTE]
   > Az androidos vállalati profillal rendelkező eszközökön a PKCS-tanúsítvány profil használatával telepített tanúsítványok nem láthatók az eszközön. A tanúsítvány sikeres központi telepítésének megerősítéséhez ellenőrizze a profil állapotát az Intune-konzolon.

### <a name="subject-name-format"></a>Tulajdonos nevének formátuma

Ha PKCS-tanúsítványsablont hoz létre a következő platformokhoz, a tulajdonos nevének formátuma a kiválasztott tanúsítvány típusától függ, amely a **felhasználó** vagy az **eszköz**.  

Platformok

- Android Enterprise (*munkahelyi profil*)
- iOS
- macOS
- Windows 10 és újabb

> [!NOTE]
> Létezik egy ismert probléma a PKCS használatával olyan tanúsítványok beszerzéséhez, [amelyek ugyanaz a probléma, mint a SCEP esetében,](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters) ha az eredményül kapott tanúsítvány-aláírási kérelemben szereplő tulajdonos neve (CSR) a következő karakterek egyikét tartalmazza Escape-karakterként (fordított perjel \\):
> - \+
> - ;
> - ,
> - =

- **Felhasználói tanúsítványtípus**  
  A *tulajdonos nevének formátuma* a következő két változót tartalmazza: **KÖZNAPI név (CN)** és **e-mail (E)** . Az **Egyszerű név (CN)** az alábbi változók bármelyikére beállítható:

  - **CN = {{username}}** : a felhasználó egyszerű felhasználóneve, például janedoe@contoso.com.
  - **CN={{AAD_Device_ID}}** : Egy Azure Active Directoryban való eszközregisztrációkor társított azonosító. Ez az azonosító jellemzően az Azure AD-ben való hitelesítéshez használatos.
  - **CN = {{SERIALNUMBER}}** : az egyedi sorozatszám (Sn) általában a gyártó által az eszköz azonosítására használatos.
  - **CN = {{IMEINumber}}** : a mobil telefon azonosítására szolgáló nemzetközi mobileszköz-identitás (IMEI) egyedi szám.
  - **CN = {{OnPrem_Distinguished_Name}}** : relatív megkülönböztető nevek sorozata vesszővel elválasztva, például *CN = JANE DOE, OU = UserAccounts, DC = Corp, DC = contoso, DC = com*.

    A *{{OnPrem_Distinguished_Name}}* változó használatához ne felejtse el szinkronizálni a *onpremisesdistinguishedname* User ATTRIBÚTUMot az Azure AD-vel való [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) használatával.

  - **CN = {{onPremisesSamAccountName}}** : a rendszergazdák a sAMAccountName attribútumot az Azure ad-vel a *onPremisesSamAccountName*nevű attribútumba szinkronizálva Active Directoryról az Azure ad-be. Az Intune a tanúsítvány kiállításának részeként helyettesítheti be ezt a változót. A samAccountName attribútum a Windows korábbi verziójából származó ügyfelek és kiszolgálók támogatásához használt felhasználói bejelentkezési név (pre-Windows 2000). A felhasználói bejelentkezési név formátuma: *DomainName\testUser*, vagy csak *tesztfelhasználó*.

    A ( *onPremisesSamAccountName* ) *{{onPremisesSamAccountName}}* változó használatához az Azure AD-vel a [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) használatával kell szinkronizálnia a felhasználói attribútumot.

  Egy vagy több változó és statikus sztringek együttes használatával létrehozhat egyéni tulajdonosnév-formátumokat, például a következőhöz hasonlót:  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  Ez a példa egy tulajdonos nevének formátumát tartalmazza, amely a CN és az E változókat, valamint a szervezeti egység, szervezet, hely, állam és ország értékek karakterláncait használja. A függvény leírását és a támogatott sztringeket a [CertStrToName függvény](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) című cikkben találhatja meg.

- **Eszköz tanúsítványtípus**  
  A tulajdonos nevének formátumára vonatkozó beállítások a következő változókat tartalmazzák: 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** *(csak Windows és tartományhoz csatlakoztatott eszközök esetén alkalmazható)*
  - **{{MEID}}**

  Megadhatja ezeket a változókat, majd a változó szövegét a szövegmezőben. Egy *Device1* nevű eszköz köznapi neve például a következő lehet: **CN = {{DeviceName}} Device1**.

  > [!IMPORTANT]  
  > - Ha változót ad meg, a hiba elkerüléséhez tegye a változó nevét kapcsos zárójelben ({}) a példában látható módon.  
  > - Az eszköz *tulajdonosának* vagy *San* -tanúsítványának (például **IMEI**, **serialnumber**és **FullyQualifiedDomainName**) használt tulajdonságai olyan tulajdonságok, amelyek az eszközhöz hozzáféréssel rendelkező személy által meghamisítható.
  > - Egy eszköznek támogatnia kell az adott profilhoz tartozó tanúsítvány-profilban megadott összes változót az adott eszközre való telepítéshez.  Ha például a **{{IMEI}}** egy SCEP-profil tulajdonos nevében van használatban, és olyan eszközhöz van rendelve, amely nem rendelkezik IMEI-számmal, akkor a profilt nem lehet telepíteni.  
 


## <a name="whats-new-for-connectors"></a>Az összekötők újdonságai

A két tanúsítvány-összekötő frissítései rendszeresen jelennek meg. Amikor frissítünk egy összekötőt, itt olvashat a változásokról.

Az *Microsoft Intune pfx tanúsítvány-összekötője* [támogatja az automatikus frissítéseket](#requirements), az *Intune tanúsítvány-összekötő* pedig manuálisan frissül.

### <a name="may-17-2019"></a>Május 17., 2019

- **PFX tanúsítvány-összekötő a Microsoft Intune-Version 6.1905.0.404**  
  Változások ebben a kiadásban:  
  - Kijavítva a probléma, hogy a meglévő PFX-tanúsítványok továbbra is újra fel lesznek dolgozva, ami miatt az összekötő leállítja az új kérések feldolgozását. 

### <a name="may-6-2019"></a>2019. május 6.

- **PFX tanúsítvány-összekötő a Microsoft Intune-Version 6.1905.0.402**  
  Változások ebben a kiadásban:  
  - Az összekötő lekérdezési időköze 5 perctől 30 másodpercre van csökkentve.
 
### <a name="april-2-2019"></a>2019. április 2.

- **Intune tanúsítvány-összekötő – verzió 6.1904.1.0**  
  Változások ebben a kiadásban:  
  - Kijavított egy hibát, amely miatt előfordulhat, hogy az összekötő nem tud regisztrálni az Intune-ba, miután bejelentkezett az összekötőbe egy globális rendszergazdai fiókkal.  
  - A tanúsítvány visszavonására vonatkozó megbízhatósági javításokat tartalmaz.  
  - Teljesítménnyel kapcsolatos javításokat tartalmaz, amelyekkel növelheti a PKCS-tanúsítványkérelmek feldolgozásának gyors módját.  

- **PFX tanúsítvány-összekötő a Microsoft Intune-Version 6.1904.0.401**
  > [!NOTE]  
  > A PFX-összekötő ezen verziójának automatikus frissítése 2019 április 11-én nem érhető el.  

  Változások ebben a kiadásban:  
  - Kijavított egy hibát, amely miatt előfordulhat, hogy az összekötő nem tud regisztrálni az Intune-ba, miután bejelentkezett az összekötőbe egy globális rendszergazdai fiókkal.  


## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../configuration/device-profile-assign.md) , és [Figyelje annak állapotát](../configuration/device-profile-monitor.md).

[SCEP használata tanúsítványokhoz](certificates-scep-configure.md)vagy [PKCS-tanúsítványok kiállítása a Symantec PKI Manager webszolgáltatásból](certificates-digicert-configure.md).
